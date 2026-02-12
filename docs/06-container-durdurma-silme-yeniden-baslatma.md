## 6. Container durdurma / silme / yeniden baslatma

Calisan container'i yonetmek icin en temel komutlar.

### Durdurma

```bash
docker stop my-app
```

### Silme

```bash
docker rm my-app
```

### Yeniden baslatma

```bash
docker restart my-app
```

### Kisa kural

- Gecici kapatmak istiyorsan `stop`.
- Tamamen kaldirmak istiyorsan `rm`.
- Sorun yasarsan hizli deneme icin `restart`.
