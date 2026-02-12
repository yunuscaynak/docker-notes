## 21. Docker Inspect

Container veya image hakkinda detayli teknik bilgiyi JSON olarak verir.

### Temel kullanim

```bash
docker inspect my-app
```

### Sadece durum bilgisini cekmek

```bash
docker inspect my-app --format '{{.State.Status}}'
```

### Ne zaman gerekli

- IP bilgisi lazimsa
- Volume baglantisini kontrol edeceksen
- Container neden kapanmis anlamak istiyorsan
