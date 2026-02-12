## 23. Health Checks

Health check, container'in "saglikli mi" bilgisini verir.

### Dockerfile icinde

```dockerfile
HEALTHCHECK CMD curl -f http://localhost:3001/ || exit 1
```

### Durumu kontrol et

```bash
docker inspect my-app --format '{{.State.Health.Status}}'
```

### Neden onemli

Container ayakta olsa bile uygulama cevap vermiyor olabilir.
Health check bunu erken yakalar.
