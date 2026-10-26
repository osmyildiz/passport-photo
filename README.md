# ABD pasaport fotoğrafı

Tek dosyalık tarayıcı uygulaması (`index.html`). Fotoğrafı ABD pasaport şartlarına göre kontrol eder, düzeltilemeyecek sorun yoksa 600×600 dijital fotoğraf ve 4×6 inç baskı sayfası (iki adet 2×2) üretir. Fotoğraf sunucuya gönderilmez; yüz noktaları ve saç/arka plan ayrımı MediaPipe modelleriyle tarayıcıda hesaplanır.

Çalıştırma:

```bash
python3 -m http.server 8765 --directory ~/projects/passport-photo
```

Sonra tarayıcıda `http://localhost:8765` açılır. Telefondan kamerayla denemek için sayfanın HTTPS üzerinden yayınlanması gerekir (ör. GitHub Pages).

Arayüz Türkçe ve İngilizce (sağ üstten seçilir). Gözlük kontrolü burun köprüsündeki çerçeve kenarını ölçer: Wikimedia portrelerinde 71 gözlüklünün 67'sini yakaladı, gözlüksüz 32 portrede yanlış alarm vermedi.

Bilinen sınırlar: netlik ve gölge eşikleri gerçek telefon fotoğraflarıyla ayarlanmadı; başlık tespiti tahminidir.
