## 30. Docker'da Dev ve Prod Ayrimi

Ayni uygulama icin `dev` (gelistirme) ve `prod` (canli) ortamlari ayirmak, hem gelistirme hizini hem de canli sistem guvenligini korumak icin yapilir.

### Neden ayiriyoruz

- Gelistirme ve canli ortamin hedefleri farklidir.
- `dev` ortaminda hizli degisiklik ve debug onceliklidir.
- `prod` ortaminda performans, stabilite ve guvenlik onceliklidir.
- Tek bir image/compose ayariyla iki hedefi ayni anda iyi karsilamak zordur.

### Ne icin ayiriyoruz

`dev` ortami:
- Kod degisikligini hizli denemek (`hot reload`, debug, test araclari)
- Kaynak kodu volume ile baglayip aninda etkisini gormek
- Daha ayrintili log ve gelistirme odakli ayarlar

`prod` ortami:
- Daha kucuk ve temiz image
- Sadece calisma zamaninda gereken bagimliliklar
- Debug araclarini ve gereksiz paketleri disarida birakmak
- Tutarli ve tekrar edilebilir deployment

### Nasil yapilir

En yaygin yontem:
1. Dockerfile'da ayri target/stage kullanmak (`development`, `production`)
2. Compose dosyalarini ayirmak (base + dev override + prod override)
3. Ortam degiskenlerini ayirmak (`.env.dev`, `.env.prod`)

### Ornek 1: Tek Dockerfile, iki target

```dockerfile
FROM node:20-alpine AS base
WORKDIR /app
COPY package*.json ./

FROM base AS development
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "run", "dev"]

FROM base AS production
RUN npm ci --omit=dev
COPY . .
RUN npm run build
EXPOSE 3000
CMD ["npm", "start"]
```

Bu yapida:
- `development` asamasi gelistirme araclarini da yukler.
- `production` asamasi sadece gerekli paketlerle daha hafif image uretir.

### Ornek 2: Compose ile dev/prod ayirma

`docker-compose.yml` (ortak):

```yaml
services:
  app:
    build:
      context: .
    ports:
      - "3000:3000"
```

`docker-compose.dev.yml`:

```yaml
services:
  app:
    build:
      target: development
    volumes:
      - .:/app
    environment:
      - NODE_ENV=development
```

`docker-compose.prod.yml`:

```yaml
services:
  app:
    build:
      target: production
    environment:
      - NODE_ENV=production
    restart: unless-stopped
```

Calistirma:

```bash
# Dev
docker compose -f docker-compose.yml -f docker-compose.dev.yml up --build

# Prod
docker compose -f docker-compose.yml -f docker-compose.prod.yml up -d --build
```

### Kisa ozet

- `dev` = hizli gelistirme ve debug kolayligi
- `prod` = guvenlik, performans, kararlilik
- Dockerfile stage + Compose override yaklasimi, en pratik ve okunabilir cozumlerden biridir.
