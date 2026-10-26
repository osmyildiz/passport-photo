# ABD pasaport fotoğrafı

Tek dosyalık tarayıcı uygulaması (`index.html`). Fotoğrafı ABD pasaport şartlarına göre kontrol eder, düzeltilemeyecek sorun yoksa 600×600 dijital fotoğraf ve 4×6 inç baskı sayfası (iki adet 2×2) üretir. Fotoğraf sunucuya gönderilmez; yüz noktaları ve saç/arka plan ayrımı MediaPipe modelleriyle tarayıcıda hesaplanır.

Çalıştırma:

```bash
python3 -m http.server 8765 --directory ~/projects/passport-photo
```

Sonra tarayıcıda `http://localhost:8765` açılır. Telefondan kamerayla denemek için sayfanın HTTPS üzerinden yayınlanması gerekir (ör. GitHub Pages).

Arayüz Türkçe ve İngilizce (sağ üstten seçilir). Gözlük kontrolü burun köprüsündeki çerçeve kenarını ölçer: Wikimedia portrelerinde 71 gözlüklünün 67'sini yakaladı, gözlüksüz 32 portrede yanlış alarm vermedi.

Işık kontrolü yüzde yedi bölgenin (alın, göz altları, yanaklar, çene) parlaklığını karşılaştırır; yan ışık, tepeden gelen ışık ve parlama için ayrı öneri verir. Eşikler 73 stüdyo portresinin dağılımına göre seçildi (4 uyarı) ve yapay gölgeyle sınandı (güçlü gölgenin 80 örneğinden 76sı yakalandı).

Bilinen sınırlar: eşikler gerçek telefon fotoğraflarıyla ayarlanmadı; başlık tespiti tahminidir.
