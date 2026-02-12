## 29. Docker Export/Import

Container dosya sistemini arsivleyip baska yere tasimak icin kullanilir.

### Export

```bash
docker export my-app > backup.tar
```

### Import

```bash
docker import backup.tar my-app:imported
```

### Alternatif (image history korumak icin)

```bash
docker save my-app:latest -o image-backup.tar
docker load -i image-backup.tar
```
