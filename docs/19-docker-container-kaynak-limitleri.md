## 19. Docker Container Kaynak Limitleri

Bir container'in fazla CPU veya RAM tuketmesini sinirlamak icin kullanilir.

### Temel kullanim

```bash
docker run --cpus="1.5" --memory="512m" my-app:latest
```

### Ne ise yarar

- Tek bir container tum makineyi yormaz.
- Kaynak paylasimi daha dengeli olur.
