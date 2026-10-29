# UstaBul — Tasarım Sistemi

## 1. Tasarımın Amacı

UstaBul, ev ve iş yerlerindeki arızalar için kullanıcıların güvenilir hizmetlere ulaşmasını sağlayan bir mobil uygulamadır.

Tasarım şu duyguları vermelidir:

- Güvenilirlik
- Profesyonellik
- Kolay kullanım
- Düzen ve açıklık
- Yerel hizmet hissi
- Modernlik

Uygulama ne eski tip bir ilan panosu gibi görünmeli ne de bir yapay zekâ arayüzünün hazır şablonuna benzemelidir.

Tasarım modern, özenli ve kendine özgü olmalıdır. Kullanıcı, uygulamayı açtığında ustaları kolayca karşılaştırabilmeli ve aradığı işlemi fazla düşünmeden yapabilmelidir.

## 2. Görsel Kimlik

### Tasarım yaklaşımı

- Modern ve sade mobil uygulama tasarımı kullan.
- Gereksiz dekorasyon yerine güçlü görsel hiyerarşi oluştur.
- Kartların, başlıkların ve butonların yerleşimini özenle tasarla.
- İçeriklerin nefes almasını sağlayan dengeli boşluklar kullan.
- Gerektiğinde küçük renk vurgularıyla önemli bilgileri öne çıkar.
- Ekranları aynı şablonun kopyaları gibi değil, ortak tasarım dilini paylaşan farklı işlevler olarak tasarla.
- Tasarımda gerçek bir ürün ekibinin hazırladığı, kullanıma hazır bir mobil uygulama kalitesi hedefle.

### Kaçınılması gereken tasarımlar

- Fosforlu mor ve parlak mor ağırlıklı arayüzler
- Gereksiz neon renkler
- Her kartta farklı gradient kullanımı
- Her bileşende glow veya parlama efekti
- Aşırı cam efekti ve glassmorphism
- Gereksiz büyük, dekoratif boşluklar
- Çok fazla iç içe kart
- Her yere konulan yuvarlak kapsül butonlar
- Birbirinden kopuk ikon stilleri
- Okunabilirliği azaltan düşük kontrast
- Sırf modern görünmek için kullanılan anlamsız animasyonlar
- Uygulamanın hizmet amacıyla ilgisi olmayan dekoratif grafikler

## 3. Renk Paleti

### Ana renkler

| Renk | HEX | Kullanım |
|---|---|---|
| Sıcak kırık beyaz | `#F6F4EF` | Açık tema ana arka planı |
| Beyaz | `#FFFFFF` | Kartlar ve belirgin yüzeyler |
| Koyu orman yeşili | `#29483B` | Ana butonlar, önemli vurgular |
| Derin yeşil | `#1D352B` | Koyu tema ana vurgu rengi |
| Yumuşak adaçayı | `#DCE6DD` | Hafif vurgulu yüzeyler |
| Koyu mürekkep | `#252B28` | Ana metin |
| Taş grisi | `#777D77` | İkincil metin |
| İnce sınır grisi | `#E3E1D9` | Kart ve alan sınırları |
| Sıcak bakır | `#B8754B` | Sınırlı sayıda önemli vurgu |
| Soluk kum | `#EDE3D5` | İkincil dekoratif yüzeyler |

### Renk kullanım kuralları

- Ana arka plan sıcak kırık beyaz olmalıdır.
- Ana eylem butonlarında koyu orman yeşili kullanılmalıdır.
- Bakır rengi yalnızca küçük ve kontrollü vurgular için kullanılmalıdır.
- Bakır rengi büyük alanları kaplamamalıdır.
- Metinler açık arka planda koyu ve rahat okunabilir olmalıdır.
- Sınırlar ve ikincil metinler dikkat dağıtmayacak kadar yumuşak olmalıdır.
- Her bileşende bütün paleti kullanmak zorunlu değildir.
- Renkler anlamlı ve tutarlı görevler üstlenmelidir.

### Koyu tema

Koyu tema, açık temanın arka planını basitçe siyaha çevirerek oluşturulmamalıdır.

Önerilen renkler:

| Renk | HEX | Kullanım |
|---|---|---|
| Ana arka plan | `#171C19` | Genel arka plan |
| Kart yüzeyi | `#222A25` | Kartlar ve paneller |
| İkincil yüzey | `#2B342D` | Ayrıştırılmış yüzeyler |
| Ana metin | `#F0F1EA` | Başlık ve gövde metni |
| İkincil metin | `#B3BBB2` | Yardımcı bilgiler |
| Ana vurgu | `#9AB7A0` | Önemli butonlar ve seçili durumlar |
| Sınır | `#3A443D` | Kart ve alan sınırları |
| Bakır vurgu | `#D49A72` | Sınırlı vurgu |

Koyu temada metin ve bileşenler rahatça ayırt edilmelidir. Kullanıcı uygulama içinden tema değiştirdiğinde bütün ekranlar yeni temaya uyum sağlamalıdır.

## 4. Tipografi

- Uygulamanın tamamında tutarlı bir yazı karakteri kullanılmalıdır.
- Tercih edilen yazı karakteri: **Manrope**.
- Projede uygun biçimde kullanılamıyorsa Flutter'ın okunabilir varsayılan yazı karakteri tercih edilebilir.
- Yazılar gereksiz yere ince veya küçük olmamalıdır.
- Başlıklar ile yardımcı metinler arasında belirgin bir hiyerarşi bulunmalıdır.

### Önerilen yazı boyutları

| Kullanım | Boyut |
|---|---:|
| Ana sayfa başlığı | 28–32 |
| Bölüm başlığı | 20–24 |
| Kart başlığı | 16–18 |
| Gövde metni | 14–16 |
| Yardımcı metin | 12–13 |
| Buton metni | 14–16 |
| Belirgin servis ücreti | 22–26 |

Bunlar tasarım rehberidir. İçeriğin uzunluğuna ve ekranın genişliğine göre gerekli uyarlamalar yapılabilir.

## 5. Boşluklar ve Yerleşim

- Yerleşimde tutarlı bir boşluk sistemi kullan.
- Küçük boşluklar için yaklaşık 4–8 px, bileşenler arası boşluklar için 12–16 px ve büyük bölüm ayrımları için 20–28 px aralığını temel al.
- Sayfa kenarlarında yeterli iç boşluk bırak.
- Kart içeriklerini kenarlara sıkıştırma.
- Bir ekranda gereksiz sayıda bilgi kutusu oluşturma.
- Liste kartlarının birbirinden ayırt edilmesini sağla.
- İçerik miktarı arttığında metinleri kesmek yerine uygun satır düzeni ve kaydırma kullan.
- Küçük ekranlarda yatay taşmaya izin verme.

## 6. Kart Tasarımı

UstaBul'un temel bileşenlerinden biri usta profil kartıdır.

Kart tasarımı:

- Temiz ve düzenli olmalıdır.
- Profil görseli kolay fark edilmelidir.
- Ustanın adı belirgin olmalıdır.
- Uzmanlık ve ilçe bilgileri kolay taranabilmelidir.
- Puan ve servis ücreti görünür olmalıdır.
- Müsaitlik rozeti anlaşılır biçimde yerleştirilmelidir.
- Metinler ile ikonlar arasında yeterli boşluk bulunmalıdır.
- Kartın tamamı gereksiz bilgiyle doldurulmamalıdır.

Kartlar, düz ve özensiz dikdörtgenler gibi görünmemelidir. İnce sınırlar, dengeli yüzey kontrastı ve çok hafif gölgeler kullanılabilir.

Aşırı gölge, parlak kenarlık veya yoğun gradient kullanılmamalıdır.

## 7. Usta Listesi ve Arama Ekranı

Bu ekran, kullanıcının uygulamada en çok etkileşim kuracağı alanlardan biridir.

- Üst bölümde anlaşılır bir sayfa başlığı bulunmalıdır.
- Arama alanı kolay fark edilmeli ve rahat kullanılmalıdır.
- Kategori filtreleri yatay olarak kaydırılabilmelidir.
- Seçili `ChoiceChip`, seçili olmayan filtrelerden açıkça ayrılmalıdır.
- Usta kartları aynı görsel düzene sahip olmalıdır.
- Servis ücreti, puan ve müsaitlik bilgisi hızlıca karşılaştırılabilmelidir.
- Sayfa kaydırıldığında başlık ve filtreler içerikle uyumlu davranmalıdır.
- Yenileme işlemi `RefreshIndicator` ile çalışmalıdır.
- Yükleniyor, hata ve boş liste durumları da tasarım sisteminin bir parçası olarak tasarlanmalıdır.

Boş listede yalnızca boş bir ekran gösterme. Kullanıcıya sonuç bulunamadığını anlatan kısa bir metin ve gerekiyorsa arama veya filtreyi değiştirme önerisi sun.

Hata durumunda anlaşılır mesaj ve çalışan Tekrar Dene butonu bulunmalıdır.

## 8. Usta Detay Ekranı

Bu ekran güven duygusunu desteklemelidir.

- Ustanın görseli belirgin olmalıdır.
- İsim ve uzmanlık alanı ilk bakışta anlaşılmalıdır.
- Puan, tamamlanan iş sayısı ve hizmet bilgileri düzenli bir hiyerarşide sunulmalıdır.
- Çalışma saatleri ve hizmet verilen ilçeler rahat okunmalıdır.
- Müşteri yorumları birbirinden ayrılmalıdır.
- Hizmet ücretleri anlaşılır gösterilmelidir.
- Fiyat teklifi isteme eylemi kolay fark edilmelidir.
- Liste ekranından gelen `Hero` geçişi doğal görünmelidir.

Görsel geçişler, içerik değişiminin anlaşılmasına yardımcı olmalı; kullanıcıyı bekletmemelidir.

## 9. Fiyat Teklifi Alt Penceresi

`ModalBottomSheet` görsel olarak uygulamanın geri kalanıyla tutarlı olmalıdır.

- Üstte anlaşılır bir başlık bulunmalıdır.
- Kullanıcı ustadan fiyat teklifi istemek veya not bırakmak istediğini kolayca anlayabilmelidir.
- Gerekli metin alanları rahat kullanılmalıdır.
- Ana işlem butonu belirgin olmalıdır.
- Alt pencere ekranın altındaki sistem alanlarıyla çakışmamalıdır.
- Klavye açıldığında alanlar erişilebilir kalmalıdır.
- İşlem sonrasında uygun başarı veya hata geri bildirimi gösterilmelidir.

## 10. Arıza Kaydı Formu

Form ekranında estetikten önce anlaşılabilirlik ve kullanılabilirlik gelir.

- Alan etiketleri açık olmalıdır.
- Arıza başlığı, kategori, açıklama, adres/ilçe, telefon ve aciliyet alanları düzenli sıralanmalıdır.
- Zorunlu alanlar gerektiğinde belirtilmelidir.
- Hatalı alanlar açıkça anlaşılmalıdır.
- Hata mesajları alanın yakınında gösterilmelidir.
- Form gönderme butonu kolay bulunmalıdır.
- Uzun açıklamalarda ekran taşmamalıdır.
- Klavye açıldığında form kullanılabilir kalmalıdır.

`Form` ve `GlobalKey<FormState>` ile yapılan doğrulamalar yalnızca teknik olarak çalışmakla kalmamalı, kullanıcıya anlaşılır şekilde yansıtılmalıdır.

## 11. Taleplerim ve Kayıtlı Ustalar

- Talepler ve favoriler görsel olarak ayırt edilebilir olmalıdır.
- Taleplerin mevcut durumları kolayca okunmalıdır.
- `Bekliyor`, `Usta Yolda` ve `Tamamlandı` durumları yalnızca renkle anlatılmamalıdır; durum metni de görünmelidir.
- Durum renkleri ölçülü kullanılmalıdır.
- Kullanıcının henüz talebi veya favorisi yoksa uygun bir boş durum gösterilmelidir.
- Kartlar arasında gereksiz görsel farklılık oluşturulmamalıdır.

## 12. Rozetler ve Puan Göstergesi

### Müsaitlik rozeti

- Müsait ve Yoğun durumları farklı biçimde algılanabilmelidir.
- Renk ve metin birlikte kullanılmalıdır.
- Rozet küçük ama okunabilir olmalıdır.
- Gereksiz animasyon veya parlama kullanılmamalıdır.

### Puan göstergesi

- Puanın yanında uygun bir yıldız ikonu kullanılabilir.
- Sayısal puan kolay okunmalıdır.
- Liste ve detay ekranında aynı yaklaşım korunmalıdır.

## 13. Butonlar ve Etkileşimler

- Birincil eylemler koyu orman yeşiliyle öne çıkarılmalıdır.
- İkincil eylemler daha sakin bir görsel ağırlığa sahip olmalıdır.
- Buton metinleri kısa ve anlaşılır olmalıdır.
- Tıklanabilir alanlar parmakla rahat kullanılacak boyutta olmalıdır.
- İkon butonlarında anlamı belirsiz simgelerden kaçınılmalıdır.
- Etkileşimlerde gerektiğinde hafif animasyon veya geri bildirim kullanılabilir.
- Bütün butonlar gerçekten çalışmalıdır; yalnızca dekoratif buton oluşturulmamalıdır.

## 14. İkonlar ve Görseller

- Tutarlı bir ikon stili kullanılmalıdır.
- Aynı işlev için farklı ekranlarda farklı ikonlar kullanılmamalıdır.
- Usta görseli yoksa düzenli bir avatar gösterilmelidir.
- Görsellerin boyutları ve kırpılması tutarlı olmalıdır.
- Görseller metinleri veya diğer kart içeriklerini taşırmamalıdır.
- Gereksiz stok görseller ve dekoratif illüstrasyonlarla ekran doldurulmamalıdır.

## 15. Animasyonlar

- `Hero` animasyonu, usta listesinden detay ekranına geçişte kullanılmalıdır.
- Diğer hareketler ölçülü ve işlevsel olmalıdır.
- Geçişler gereksiz yere uzun tutulmamalıdır.
- Kullanıcının bir eylemi gerçekleştirdiği anlaşılmalıdır.
- Animasyonlar temel işlevleri geciktirmemelidir.

## 16. Erişilebilirlik ve Responsive Tasarım

- Metin ve arka plan arasında yeterli kontrast bulunmalıdır.
- Yalnızca renge dayalı anlam aktarımından kaçınılmalıdır.
- Uzun usta isimleri ve yorumlar taşma oluşturmamalıdır.
- Formlar küçük ekranlarda kullanılabilir olmalıdır.
- Farklı ekran genişlikleri kontrol edilmelidir.
- Büyük metin boyutlarında mümkün olduğunca içerik kaybı veya taşma önlenmelidir.

## 17. Son Tasarım Kontrolü

Her ekran tamamlandığında şu soruları kontrol et:

1. Ekran UstaBul'un güvenilir ve modern kimliğine uyuyor mu?
2. Renkler palete uygun mu?
3. Başlıklar ve içerikler arasında doğru hiyerarşi var mı?
4. Kullanıcı ana işlemi kolayca bulabiliyor mu?
5. Metinler rahat okunuyor mu?
6. Kartlar, butonlar ve alanlar diğer ekranlarla tutarlı mı?
7. Açık ve koyu temada görünüm doğru mu?
8. Küçük ekranlarda taşma var mı?
9. Yükleniyor, hata ve boş durumlar özenle tasarlanmış mı?
10. Görsel efektler işlevin önüne geçiyor mu?

UstaBul'un tasarımı yalnızca güzel bir ekran görüntüsü oluşturmayı hedeflememelidir. Tasarım, gerçek bir mobil uygulamada kullanılabilecek kadar tutarlı, anlaşılır ve işlevsel olmalıdır.