## 10. Dockerfile (kisa ozet)

Dockerfile, image'in nasil olusacagini anlatan tarif dosyasidir.

### Basit bir akis

- `FROM`: hangi temel image ile baslanacak
- `WORKDIR`: container icinde calisilan klasor
- `COPY`: dosyalari image'e kopyalar
- `RUN`: build sirasinda komut calistirir
- `EXPOSE`: uygulamanin dinledigi portu belirtir
- `CMD`: container acilinca calisacak komut

### En temel build

```bash
docker build -t my-app:latest .
```

### Basit Dockerfile ornegi

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
EXPOSE 3001
CMD ["node", "app.js"]
```
