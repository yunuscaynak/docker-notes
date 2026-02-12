## 3. Container calistirma

Image hazirsa uygulamayi container olarak calistirirsin.

### En temel komut

```bash
docker run -d --name my-app -p 3001:3001 my-app:latest
```

Komutun anlami:
- `-d`: arka planda calisir.
- `--name my-app`: container ismi verir.
- `-p 3001:3001`: host portunu container portuna baglar.
- `my-app:latest`: calisacak image.

### Port mapping mantigi

Format:

```bash
docker run -p HOST_PORT:CONTAINER_PORT IMAGE
```

Ornek:

```bash
docker run -d --name my-app -p 8080:3001 my-app:latest
```

Bu durumda tarayicidan `http://localhost:8080` ile erisirsin.

### Calistigini kontrol et

```bash
docker ps
```

Listede `my-app` goruyorsan container calisiyordur.

### Kod guncelleme sonrasi container yenileme

Eger kodu degistirdiysen eski container'i yeni image ile degistir:

```bash
docker stop my-app
docker rm my-app
docker run -d --name my-app -p 3001:3001 my-app:latest
```
