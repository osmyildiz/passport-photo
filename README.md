# Pasaport/vize fotoğrafı ve belge tarayıcı

İki sayfalık tarayıcı uygulaması. Hiçbir dosya sunucuya gönderilmez; bütün işlem tarayıcıda yapılır.

**`index.html` — vesikalık fotoğraf.** Fotoğrafı seçilen belgenin şartlarına göre kontrol eder, düzeltilemeyecek sorun yoksa dijital fotoğraf ve 4×6 inç baskı sayfası üretir. Üç biçim var: ABD pasaportu (2×2 inç, 600×600), Türk pasaportu ve kimliği (50×60 mm), Schengen vizesi (35×45 mm). Yüz noktaları ve saç/arka plan ayrımı MediaPipe modelleriyle tarayıcıda hesaplanır.

**`doc.html` — belge tarayıcı.** Telefonla çekilen belge fotoğrafında kâğıdın köşelerini bulur (kullanıcı sürükleyerek düzeltebilir), perspektifi düzeltir, kâğıdı beyazlatır ve sayfaları seçilen boyut sınırının (1/2/4/10 MB) altında tek PDF'te toplar. Dış kütüphane kullanmaz.

Çalıştırma:

```bash
python3 -m http.server 8765 --directory ~/projects/passport-photo
```

Sonra tarayıcıda `http://localhost:8765` açılır. Telefondan kamerayla denemek için sayfanın HTTPS üzerinden yayınlanması gerekir (ör. GitHub Pages).

Arayüz Türkçe ve İngilizce (sağ üstten seçilir).

Ölçümler:
- Gözlük kontrolü burun köprüsündeki çerçeve kenarını ölçer: Wikimedia portrelerinde 71 gözlüklünün 67'sini yakaladı, gözlüksüz 32 portrede yanlış alarm vermedi.
- Işık kontrolü yüzde yedi bölgenin parlaklığını karşılaştırır; eşikler 73 stüdyo portresine göre seçildi, güçlü yapay gölgenin 80 örneğinden 76'sı yakalandı.
- Belge tarayıcı: kamera modeliyle üretilmiş 9 sentetik fotoğrafta (25–40° eğim, 45°'ye kadar dönüş) köşe hatası en fazla 11 piksel (2400 piksellik görüntüde), sayfa oranı 9'un 8'inde %0,5 içinde. Gerçek fotoğraflarda üst üste duran kâğıtlar tek bölge sayılıyor; köşeleri elle düzeltmek gerekiyor.

Bilinen sınırlar: eşikler gerçek telefon fotoğraflarıyla ayarlanmadı; başlık tespiti tahminidir. NVİ baş boyu yayımlamıyor; Türk biçimindeki 34 mm yaygın uygulamadır.
