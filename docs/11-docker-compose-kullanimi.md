## 11. Docker Compose (`docker-compose.yml`)

Birden fazla servisi tek komutla yonetmek icin kullanilir.

### `docker-compose.yml` dosyasi nasil olusturulur

1. Proje klasorune gir:

```bash
cd proje-klasoru
```

2. Klasor icinde `docker-compose.yml` dosyasi olustur.
3. Asagidaki minimum icerigi ekle:

```yaml
services:
  app:
    image: my-app:latest
    container_name: my-app
    ports:
      - "3001:3001"
```

Bu dosya su anlama gelir:
- `services`: calisacak servislerin listesi
- `app`: servis adi
- `image`: kullanilacak image
- `ports`: host ve container port eslestirmesi

### Ornek: birkac servis (`app + db + redis`)

Asagidaki ornek, uygulama + PostgreSQL + Redis'i birlikte calistirir:

```yaml
services:
  app:
    image: my-app:latest
    container_name: my-app
    ports:
      - "3001:3001"
    environment:
      - DB_HOST=db
      - DB_PORT=5432
      - REDIS_HOST=redis
      - REDIS_PORT=6379
    depends_on:
      - db
      - redis

  db:
    image: postgres:16
    container_name: my-db
    environment:
      - POSTGRES_DB=myapp
      - POSTGRES_USER=admin
      - POSTGRES_PASSWORD=admin123
    volumes:
      - db-data:/var/lib/postgresql/data

  redis:
    image: redis:7-alpine
    container_name: my-redis

volumes:
  db-data:
```

Bu yapida:
- `app`, `db` ve `redis` ile ayni compose aginda haberlesir.
- `DB_HOST=db` yazarak uygulama veritabanina servis adi ile baglanir.
- `db-data` volume'u veritabani verisini kalici tutar.

### Servisleri baslat

```bash
docker compose -f docker-compose.yml up -d
```

### Servisleri durdur

```bash
docker compose -f docker-compose.yml down
```

### Loglari izle

```bash
docker compose -f docker-compose.yml logs -f
```

### Ne zaman kullanilir

- Uygulama + veritabani birlikte calisacaksa.
- Uzun `docker run` komutlarini tek dosyada toplamak istiyorsan.
