## 7. Image tagleme (versiyonlama)

Ayni image'e farkli surum etiketleri verebilirsin.

### Temel komut

```bash
docker tag my-app:latest my-app:v2
```

Bu komut yeni image olusturmaz.
Ayni image'e ikinci bir isim/surum etiketi ekler.

Neden yeni image olusmaz:
- Docker'da asil kimlik `image ID`'dir.
- `tag`, bu ayni ID'ye verilen ek isimdir.

### Neden faydali

- `latest`: en son kullanim
- `v2`, `v2.1.0`: sabit surum takibi

### Kod degisti ise dogru akis

`tag` tek basina yeterli degildir. Kod degisince yeniden build almalisin:

```bash
# 1) Yeni kodla yeni image
docker build -t my-app:latest -t my-app:v2 .

# 2) Eski container'i durdur/sil
docker stop my-app
docker rm my-app

# 3) Yeni image ile tekrar calistir
docker run -d --name my-app -p 3001:3001 my-app:latest
```
