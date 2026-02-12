## 24. Restart Policies

Container kapaninca otomatik yeniden acilmasini saglar.

### Temel kullanim

```bash
docker run --restart=always my-app:latest
```

### Secenekler

- `no`: otomatik yeniden baslatmaz
- `always`: her durumda yeniden baslatir
- `on-failure`: hata olursa yeniden baslatir
- `unless-stopped`: elle durdurana kadar yeniden baslatir

### Pratik oneriler

Sunucu ortaminda genelde `unless-stopped` veya `always` kullanilir.
