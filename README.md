# 3-2-1! Ortak Oyuncu ⚽

Kafede oynanan **3-2-1** oyunu için mobil web uygulaması.

**Oyun:** "3, 2, 1!" diye sayılır, iki kişi birer futbol takımı söyler (ör. *AC Milan* ve *Real Madrid*). İki takımda da oynamış bir oyuncuyu ilk söyleyen kazanır.

**Uygulama:** İki takımı seçersin, 3·2·1 geri sayımından sonra iki takımda da oynamış bütün oyuncular ünlülük ve güncelliğe göre sıralanmış olarak çıkar.

## Özellikler

- 📱 Telefon odaklı arayüz, ana ekrana eklenebilir
- 🛡️ Bütün takımların armaları (Wikipedia'dan otomatik)
- ⚡ 24 popüler takım tek dokunuşla seçilir, diğer takımlar aranabilir
- 🔄 Veriler canlı olarak Wikidata'dan gelir, yeni transferler de görünür
- 🏆 Ünlülük ve güncelliğe göre sıralama, "şu an bu takımda" etiketi ve **Güncel** filtresi
- 🔎 Sonuç listesinde isimle arama
- 👤 **Oyuncu kariyeri:** takım seçmeden bir futbolcu ara, oynadığı bütün kulüpleri gör
- 🎲 Rastgele eşleşme
- 📟 Retro stadyum skorbordu teması

## Nasıl çalışır?

Tek bir `index.html` dosyasından oluşur, sunucu ya da API anahtarı gerekmez.

- **Oyuncular:** [Wikidata SPARQL](https://query.wikidata.org/) ile iki takımda da kaydı (P54) olan futbolcular çekilir.
- **Ünlülük:** Oyuncunun kaç farklı dilde Wikipedia sayfası olduğu.
- **Güncellik:** Takımlardaki son yılı; yakın zamandakiler öne çıkar.
- **"Şu an" kontrolü:** Wikidata'da bitiş tarihi unutulmuş kayıtlar çok, bu yüzden ona güvenilmez. Oyuncunun İngilizce Wikipedia sayfasındaki "current club" bilgisi bu takımı gösteriyorsa "şu an" yazılır; emin olunamazsa yazılmaz.
- **Arama:** Hem baştan eşleşen hem tam metin araması yapılır ("osimhen" → Victor Osimhen).
- **Armalar:** Önce İngilizce Wikipedia arması, yoksa Wikidata logosu, o da yoksa Türkçe/İspanyolca/İtalyanca/Almanca/Fransızca/Portekizce/Hollandaca Wikipedia görseli.
- Sonuçlar tarayıcıda 6 saat saklanır, aynı eşleşme ikinci kez anında açılır.

## Yerelde çalıştırma

```bash
python -m http.server 5391
```

Sonra tarayıcıda `http://localhost:5391` adresini aç.

---

Resmi olmayan hayran projesidir. Veriler Wikidata (CC0) ve Wikipedia'dan gelir; takım armaları ilgili kulüplerin markalarıdır.
