## 14. Docker Network

Container'larin birbiriyle konusmasini Docker network saglar.

### Ozel network olustur

```bash
docker network create my-net
```

### Network'leri goster

```bash
docker network ls
```

### Ayni network'te iki container calistir

```bash
docker run -d --name app --network my-net my-app:latest
docker run -d --name api --network my-net my-api:latest
```

### Neden onemli

Ayni network'teki container'lar birbirine isimle ulasabilir (`api`, `app` gibi).
