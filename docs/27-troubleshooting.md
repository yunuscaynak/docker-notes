## 27. Troubleshooting

Sorun oldugunda bu sirayla kontrol et.

### 1) Container calisiyor mu

```bash
docker ps -a
```

### 2) Hata logu var mi

```bash
docker logs my-app
```

### 3) Port dogru mu

```bash
docker port my-app
```

### 4) Detay durum

```bash
docker inspect my-app --format '{{.State.Status}} {{.State.ExitCode}}'
```

### Yaygin problemler

- Port cakismasi
- Yanlis env degeri
- Uygulamanin acilis hatasi
