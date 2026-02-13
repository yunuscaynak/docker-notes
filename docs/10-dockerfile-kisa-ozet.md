## 10. Dockerfile (kisa ozet)

Dockerfile, image'in nasil olusacagini anlatan tarif dosyasidir.

Bu sayfa yeni baslayanlar icin "ilk Dockerfile" + temel komut referansi odagindadir.

### 4 adimda mantik

1. Temel image sec (`FROM`)
2. Uygulama dosyalarini kopyala (`COPY`)
3. Gerekli kurulum komutlarini calistir (`RUN`)
4. Baslangic komutunu belirle (`CMD`)

### Ilk Dockerfile ornegi

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
EXPOSE 3001
CMD ["node", "app.js"]
```

### Ilk build komutu

```bash
docker build -t my-app:latest .
```

### Sonra ne yaparsin

```bash
docker run -d --name my-app -p 3001:3001 my-app:latest
```

## 10.1 Dockerfile komut sozlugu

- `FROM`: baslangic image'i secer.
  Ornek: `FROM node:18-alpine`
- `WORKDIR`: sonraki komutlarin calisacagi klasoru ayarlar.
  Ornek: `WORKDIR /app`
- `COPY`: dosyalari image'e kopyalar.
  Ornek: `COPY package*.json ./`
- `RUN`: build asamasinda komut calistirir.
  Ornek: `RUN npm ci`
- `ENV`: ortam degiskeni tanimlar.
  Ornek: `ENV NODE_ENV=production`
- `ARG`: sadece build sirasinda kullanilan degisken.
  Ornek: `ARG APP_VERSION=1.0.0`
- `EXPOSE`: container'in dinledigi portu belirtir.
  Ornek: `EXPOSE 3001`
- `CMD`: container acildiginda varsayilan komut.
  Ornek: `CMD ["node", "app.js"]`
- `ENTRYPOINT`: sabit calisma komutu; `CMD` arguman olabilir.
  Ornek: `ENTRYPOINT ["node", "app.js"]`
- `USER`: container icindeki calisan kullaniciyi degistirir.
  Ornek: `USER node`
- `HEALTHCHECK`: uygulama saglik kontrolu tanimlar.
  Ornek: `HEALTHCHECK CMD curl -f http://localhost:3001/ || exit 1`

## 10.2 Sik karistirilanlar

- `RUN` vs `CMD`
  `RUN` image olusurken calisir, `CMD` container baslayinca calisir.
- `CMD` vs `ENTRYPOINT`
  `CMD` kolay override edilir, `ENTRYPOINT` ana komut gibi davranir.

## 10.3 Build cache ile hizli build

Kural: SIK degisen dosyalari (`COPY . .`) sona birak, AZ degisen dosyalari (`package*.json`) once kopyala.

Docker her satiri bir "katman" (layer) olarak build eder ve cache'ler.
Bir katman degisirse, ondan sonraki katmanlar da tekrar build olur.

Yanlis siralama (yavas):

```dockerfile
COPY . .
RUN npm install
```

Bu siralamada kodda en ufak degisiklik bile `COPY . .` katmanini degistirir.
`COPY . .` degistigi icin alttaki `RUN npm install` da yeniden calisir.

Dogru siralama (hizli):

```dockerfile
COPY package*.json ./
RUN npm install
COPY . .
```

Bu siralamada:
- Sadece kod (`app.js`, `src/*`) degisirse:
  `COPY package*.json` ve `RUN npm install` cache'den gelir, sadece son `COPY . .` yenilenir.
- `package-lock.json` veya `package.json` degisirse:
  `npm install` tekrar calisir (zaten dogru davranis budur, cunku bagimlilik degisti).

Kisa ozet:
- Kod degisimi -> hizli rebuild
- Bagimlilik degisimi -> gerekli rebuild

Ek not: `.dockerignore` kullanarak `node_modules`, `.git`, log dosyalari gibi gereksiz dosyalari build context disinda birakirsan cache daha stabil ve build daha hizli olur.
