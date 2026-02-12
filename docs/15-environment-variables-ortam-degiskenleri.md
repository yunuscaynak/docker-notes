## 15. Environment Variables (Ortam Degiskenleri)

Uygulama ayarlarini koda gommeden disaridan vermek icin kullanilir.

### Komut satirindan degisken verme

```bash
docker run -e NODE_ENV=production -e PORT=3001 my-app:latest
```

### `.env` dosyasi ile verme

```bash
docker run --env-file .env my-app:latest
```

### Ornek `.env`

```env
NODE_ENV=production
PORT=3001
DB_HOST=localhost
DB_USER=admin
```

### Neden faydali

Ayni image'i farkli ortamlarda farkli ayarlarla calistirabilirsin.
