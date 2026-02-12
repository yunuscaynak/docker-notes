## 26. Security Best Practices

Docker tarafinda temel guvenlik adimlari.

### En onemli maddeler

- Root yerine non-root kullan (`USER node` gibi)
- Kucuk base image kullan (`alpine` gibi)
- Gereksiz paketleri image'e koyma
- Gizli bilgileri image icine yazma

### Ornek runtime sertlestirme

```bash
docker run --read-only --cap-drop=ALL --security-opt no-new-privileges my-app:latest
```

### Kisa kural

Image ne kadar sadeyse risk o kadar azalir.
