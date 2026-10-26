# ABD pasaport fotoğrafı

Tek dosyalık tarayıcı uygulaması (`index.html`). Fotoğrafı ABD pasaport şartlarına göre kontrol eder, düzeltilemeyecek sorun yoksa 600×600 dijital fotoğraf ve 4×6 inç baskı sayfası (iki adet 2×2) üretir. Fotoğraf sunucuya gönderilmez; yüz noktaları ve saç/arka plan ayrımı MediaPipe modelleriyle tarayıcıda hesaplanır.

Çalıştırma:

```bash
python3 -m http.server 8765 --directory ~/projects/passport-photo
```

Sonra tarayıcıda `http://localhost:8765` açılır. Telefondan kamerayla denemek için sayfanın HTTPS üzerinden yayınlanması gerekir (ör. GitHub Pages).

Bilinen sınırlar: eşikler (netlik, gölge, gözlük) gerçek bir fotoğraf setiyle ayarlanmadı; gözlük ve başlık tespiti tahminidir.
