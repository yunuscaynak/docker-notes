## 30. Makefile ile Proje Genel Kullanim

Uzun komutlari ezberlemek yerine `make` hedefleri kullanabilirsin.

### Yardim

```bash
make help
```

### Uygulama akisi

```bash
make build
make up
make logs
make down
```

### Image islemleri

```bash
make image-build TAG=v2
make image-history TAG=v2
make image-inspect TAG=v2
```

### Registry islemleri

```bash
make hub-push TAG=v2
make hub-pull TAG=v2
make hub-run TAG=v2
```

---

## 31. Node Script Komutlari (Makefile)

`package.json` scriptlerini `make` uzerinden de cagirabilirsin.

```bash
make npm-install
make npm-start
make npm-build
make npm-test
```

Esdeger npm komutlari:

```bash
npm install
npm start
npm run build
npm test
```
