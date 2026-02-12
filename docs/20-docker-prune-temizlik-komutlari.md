## 20. Docker Prune (Temizlik Komutlari)

Kullanilmayan Docker nesnelerini temizleyip disk alani acarsin.

### Tum kullanilmayanlari temizle

```bash
docker system prune
```

### Sadece kullanilmayan image'lari temizle

```bash
docker image prune
```

### Once disk durumunu gor

```bash
docker system df
```

### Dikkat

Prune geri alinamaz.
