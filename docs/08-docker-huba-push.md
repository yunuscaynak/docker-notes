## 8. Docker Hub'a push

Image'i baska makinelerde kullanmak icin registry'ye gonderirsin.

### 1) Giris yap

```bash
docker login
```

### 2) Image'i kendi hesabina tagle

```bash
docker tag my-app:v2 myuser/my-app:v2
```

### 3) Push et

```bash
docker push myuser/my-app:v2
```

### Kontrol

Docker Hub hesabinda `myuser/my-app:v2` gorunuyorsa islem tamamdir.
