## 9. Docker Hub'dan cekip calistirma

Baska bir yerde push edilmis image'i indirip calistirabilirsin.

### 1) Image'i cek

```bash
docker pull myuser/my-app:v2
```

### 2) Container'i calistir

```bash
docker run -d --name my-app -p 3001:3001 myuser/my-app:v2
```

### Not

Eger `v2` yoksa dogru tag adini kontrol et.
