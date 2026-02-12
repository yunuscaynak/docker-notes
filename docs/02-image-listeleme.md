## 2. Image listeleme

Bu bolumde bilgisayarindaki Docker image'larini gorursun.

### En temel komut

```bash
docker images
```

Bu komut sana su bilgileri verir:
- image adi
- tag (surum etiketi)
- image ID
- olusturulma zamani
- boyut

### Daha detayli bakis

Image'in katman gecmisini gormek icin:

```bash
docker history my-app:latest
```

Image boyutunu net olarak gormek icin:

```bash
docker image inspect my-app:latest --format='{{.Size}}'
```

### Ne zaman kullanilir

- Build sonrasi image olustu mu kontrol etmek icin.
- Diskte cok yer kaplayan image'lari tespit etmek icin.
