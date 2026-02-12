## 17. Multi-stage Build

Multi-stage, Dockerfile icinde birden fazla asama kullanmaktir.
Amac: son image'i daha kucuk ve temiz yapmak.

### Mantik

1. Ilk asama: build islemleri
2. Son asama: sadece gereken ciktilar

### Ornek

```dockerfile
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY --from=builder /app/dist ./dist
EXPOSE 3001
CMD ["node", "dist/app.js"]
```

### Kazanc

- Daha kucuk image
- Daha hizli deploy
- Daha az guvenlik riski
