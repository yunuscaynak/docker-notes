## 18. `.dockerignore` Dosyasi

Build sirasinda image'e gitmesini istemedigin dosyalari burada belirtirsin.

### Neden gerekli

- Build hizlanir
- Image boyutu kuculur
- Gizli dosyalar yanlislikla image'e girmez

### Ornek

```txt
node_modules
.git
.env
dist
```

### Kural

Proje kokundeki `.dockerignore`, `docker build` context'ini filtreler.
