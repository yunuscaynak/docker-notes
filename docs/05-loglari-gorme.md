## 5. Loglari gorme

Uygulama neden calismiyor, hata var mi gibi sorularin ilk cevabi log'lardadir.

### Temel komut

```bash
docker logs my-app
```

### Pratik kullanim

Son 100 satiri gormek:

```bash
docker logs --tail 100 my-app
```

Canli takip etmek:

```bash
docker logs -f my-app
```

Zaman damgasi ile gormek:

```bash
docker logs -t my-app
```

### Not

Container acilip hemen kapaniyorsa once `docker logs my-app` bak.
