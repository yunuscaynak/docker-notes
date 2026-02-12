## 11. Docker Compose (`docker-compose.yml`)

Birden fazla servisi tek komutla yonetmek icin kullanilir.

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
