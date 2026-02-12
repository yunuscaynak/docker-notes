## 25. Docker Registry

Registry, image'larini sakladigin uzak depodur.

### Yaygin secenekler

- Docker Hub
- GHCR (GitHub Container Registry)
- GitLab Registry
- Private registry

### Local registry ornegi

```bash
docker run -d -p 5000:5000 --name registry registry:2
docker tag my-app:latest localhost:5000/my-app:latest
docker push localhost:5000/my-app:latest
```

### Ne zaman kullanilir

- Ekip ici image paylasimi
- CI/CD pipeline'da image dagitimi
