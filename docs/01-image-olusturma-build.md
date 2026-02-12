## 1. Image olusturma (build)

Docker image, uygulamanin calismasi icin gereken her seyin paketlenmis halidir.
`build` komutu bu paketi olusturur.

### Baslamadan once

1. Docker Desktop acik olsun.
2. Terminalde projenin klasorune gir:

```bash
cd proje-klasoru
```

3. Bu klasorde `Dockerfile` oldugundan emin ol.

### En basit image olusturma

```bash
docker build -t my-app:latest .
```

Bu komutta:
- `docker build`: image olusturur.
- `-t my-app:latest`: image adi (`my-app`) ve etiketi (`latest`).
- `.`: mevcut klasoru build kaynagi olarak kullanir.

### Build basarili mi nasil anlarsin

```bash
docker images
```

Listede `my-app` ve `latest` goruyorsan build tamamdir.

### Dockerfile farkli konumdaysa

```bash
docker build -t my-app:latest -f Dockerfile .
```

`-f` ile Dockerfile yolunu acikca verirsin.

### Farkli surum etiketi vermek

```bash
docker build -t my-app:v2 .
```

### Kod guncelledikten sonra ne yapilir

Kod degisince ayni image'i yeniden build etmen gerekir:

```bash
# 1) Yeni kodla yeni image
docker build -t my-app:latest -t my-app:v2 .
```

Bu komutla:
- `latest` guncellenir
- `v2` gibi sabit bir surum etiketi de olusur

Sonra eski container'i yeni image ile degistirirsin:

```bash
# 2) Eski container'i durdur/sil
docker stop my-app
docker rm my-app

# 3) Yeni image ile tekrar calistir
docker run -d --name my-app -p 3001:3001 my-app:latest
```

### Ihtiyac olursa kullanilacak ek secenekler

Cache kullanmadan sifirdan build:

```bash
docker build --no-cache -t my-app:latest .
```

Base image'i guncelleyerek build:

```bash
docker build --pull -t my-app:latest .
```
