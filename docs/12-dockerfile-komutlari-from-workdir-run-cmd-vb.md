## 12. Dockerfile komutlari (FROM, WORKDIR, RUN, CMD, vb.)

Dockerfile satirlarinin ne yaptigini kisa ve net sekilde bilmek yeterlidir.

### En cok kullanilan komutlar

- `FROM`: baslangic image'i
- `WORKDIR`: calisma klasoru
- `COPY`: dosya kopyalama
- `RUN`: build asamasinda komut
- `ENV`: ortam degiskeni
- `EXPOSE`: port bilgisi
- `CMD`: varsayilan calisma komutu

### Kisa ornek

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
ENV NODE_ENV=production
EXPOSE 3001
CMD ["node", "app.js"]
```

### Akilda kalacak kural

- `RUN`: build sirasinda
- `CMD`: container calisirken
