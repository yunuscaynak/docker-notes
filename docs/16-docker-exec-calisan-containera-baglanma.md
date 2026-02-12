## 16. Docker Exec (Calisan Container'a Baglanma)

Calisan container'in icine girip kontrol yapmak icin kullanilir.

### Terminal acma

```bash
docker exec -it my-app sh
```

### Tek komut calistirma

```bash
docker exec -it my-app ls -la
```

## 16.1 Docker Container Kopyalama (`docker cp`)

Container'dan host'a:

```bash
docker cp my-app:/app/log.txt ./log.txt
```

Host'tan container'a:

```bash
docker cp ./config.json my-app:/app/config.json
```

### Ne zaman kullanilir

- Log dosyasi almak icin
- Config dosyasi test etmek icin
