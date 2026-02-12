## 13. Docker Volumes (Kalici Veri Yonetimi)

Container silinse bile veri kaybolmasin istiyorsan volume kullanirsin.

### Volume olusturma

```bash
docker volume create my-data
```

### Volume'lari listeleme

```bash
docker volume ls
```

### Container'da volume kullanma

```bash
docker run -d --name db -v my-data:/var/lib/postgresql/data postgres:16
```

### Mantik

- Sol taraf (`my-data`): Docker volume adi
- Sag taraf (`/var/lib/postgresql/data`): container icindeki klasor
