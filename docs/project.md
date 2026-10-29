# UstaBul — Proje Tanımı ve Zorunlu Gereksinimler

## 1. Projenin Amacı

UstaBul, ev veya iş yerlerinde meydana gelen arızalar için kullanıcıların bölgedeki ustaları bulabildiği ve arıza talepleri oluşturabildiği bir Flutter mobil uygulamasıdır.

Uygulamada su tesisatı, elektrik, kombi/klima, boya, çilingir ve beyaz eşya gibi hizmet alanları bulunur.

Kullanıcılar ustaların uzmanlık alanlarını, hizmet verdikleri ilçeleri, servis ücretlerini, müsaitlik durumlarını ve müşteri değerlendirmelerini inceleyebilir. Ayrıca arıza kaydı oluşturabilir, taleplerini takip edebilir ve ustaları favorilerine ekleyebilir.

Projenin temel amacı, derste öğrenilen Flutter konularını kullanarak temiz kod yapısına sahip, çalışır ve görsel açıdan kaliteli bir mobil uygulama geliştirmektir.

## 2. Temel Proje Kuralları

- Uygulama Flutter ve Dart ile geliştirilecektir.
- Kodlar okunabilir, düzenli ve sürdürülebilir olmalıdır.
- Spagetti kod yazılmamalıdır.
- Derste belirtilen `models/`, `services/`, `screens/` ve `widgets/` klasör yapısına uyulmalıdır.
- Veriler doğrudan ekran dosyalarının içine yazılmamalıdır.
- Veri işlemleri servis katmanı üzerinden yürütülmelidir.
- Her ekranın ve widget'ın sorumluluğu açık olmalıdır.
- Proje GitHub Repository üzerinden teslim edilecektir.
- Ekipteki her geliştiricinin kendi branch'i ve anlamlı commit geçmişi bulunmalıdır.
- Aşağıdaki ekranlar ve teknik gereksinimler zorunludur; geliştirme sırasında atlanmamalıdır.

## 3. Zorunlu Ekranlar

### 3.1. Usta Listesi ve Arama Ekranı

Ustalar profil kartları halinde listelenmelidir.

Her usta kartında şu bilgiler bulunmalıdır:

- Usta adı
- Uzmanlık alanı
- Hizmet verdiği ilçe
- Müşteri puanı
- Ortalama servis ücreti
- Müsait veya Yoğun durum rozeti

Teknik gereksinimler:

- Listeleme için `ListView.builder` kullanılmalıdır.
- Usta adına, ilçeye veya arıza türüne göre anlık arama yapılabilmelidir.
- Arama alanı için `TextField` kullanılmalıdır.
- Kategori filtreleri yatay olarak gösterilmelidir.
- Filtrelerde `ChoiceChip` kullanılmalıdır.
- Zorunlu kategoriler: Tümü, Elektrik, Su Tesisatı, Kombi/Klima, Boya ve Çilingir.
- Kullanıcı sayfayı aşağı çekerek listeyi yenileyebilmelidir.
- Yenileme işlemi `RefreshIndicator` ile uygulanmalıdır.

### 3.2. Usta Detay ve Hizmet Ekranı

Kullanıcı bir ustayı seçtiğinde ustanın detay sayfası açılmalıdır.

Ekranda şu bilgiler bulunmalıdır:

- Ustanın fotoğrafı veya avatarı
- Verdiği hizmetler
- Çalışma saatleri
- Hizmet verdiği ilçeler
- Tamamladığı iş sayısı
- Önceki müşterilerin yorumları
- Uygun bir alanda servis ücreti bilgisi

Teknik gereksinimler:

- Liste ekranındaki usta görselinden detay ekranına `Hero` animasyonu ile geçiş yapılmalıdır.
- Kullanıcı fiyat teklifi istemek veya ustaya not bırakmak için bir alt pencere açabilmelidir.
- Alt pencere `ModalBottomSheet` kullanılarak oluşturulmalıdır.

### 3.3. Arıza Kaydı Oluşturma Ekranı

Kullanıcı yaşadığı arızayı bir form aracılığıyla kaydedebilmelidir.

Formda şu alanlar bulunmalıdır:

- Arıza başlığı
- Arıza kategorisi
- Detaylı açıklama
- Adres veya ilçe
- Telefon numarası
- Aciliyet durumu

Teknik gereksinimler:

- Flutter `Form` kullanılmalıdır.
- Formun durumunu yönetmek için `GlobalKey<FormState>` kullanılmalıdır.
- Boş alanlar kontrol edilmelidir.
- Telefon numarasının formatı kontrol edilmelidir.
- Açıklamanın minimum uzunluğu kontrol edilmelidir.
- Form hataları kullanıcıya açık ve anlaşılır biçimde gösterilmelidir.

### 3.4. Açtığım Talepler ve Kayıtlı Ustalar Ekranı

Kullanıcı oluşturduğu arıza taleplerini ve favorilerine eklediği ustaları görebilmelidir.

Arıza taleplerinde şu durumlar bulunmalıdır:

- Bekliyor
- Usta Yolda
- Tamamlandı

Teknik gereksinimler:

- Taleplerin durumları kullanıcıya görünür olmalıdır.
- Favori ustalar listelenebilmelidir.
- Sayfalar arasında alt menü üzerinden geçiş yapılmalıdır.
- Alt menü için `NavigationBar` kullanılabilir.
- Sayfa yönlendirmesi için `GoRouter` veya standart Flutter navigasyonu kullanılabilir.

## 4. Veri Modelleri ve Servis Katmanı

Veriler doğrudan ekran dosyalarında tanımlanmamalıdır.

Projede en az aşağıdaki modeller bulunmalıdır:

- `Usta`
- `ArizaTalebi`
- `HizmetKategorisi` enum

Modellerde uygun `fromJson` ve `copyWith` metotları bulunmalıdır.

Veriler aşağıdaki seçeneklerden biriyle sağlanmalıdır:

1. `http` paketi kullanılarak gerçek bir REST API üzerinden veri çekilmesi.
2. Gecikmeli çalışan ve gerçek servis davranışını taklit eden, en az 12–15 detaylı kayıt içeren bir servis katmanı.

Servis yaklaşımı ekip tarafından seçilmelidir. Gerçek bir API kullanılmıyorsa var olmayan bir sunucuya bağlanıldığı iddia edilmemelidir.

Usta verileri için `IUstaServisi` isimli soyut servis tanımı kullanılmalıdır.

Servis katmanı, ekranların veri kaynağından bağımsız çalışmasını sağlamalıdır.

## 5. Dört Veri Durumu

Usta listesindeki veri yükleme işlemi aşağıdaki dört durumu da desteklemelidir:

1. **Yükleniyor:** Veri alınırken `CircularProgressIndicator` gösterilmelidir.
2. **Hata:** Bağlantı veya servis hatası anlaşılır bir mesajla gösterilmeli ve çalışan bir Tekrar Dene butonu bulunmalıdır.
3. **Boş liste:** Arama veya kategori filtresi sonucunda usta bulunamadığında bilgilendirici bir ekran gösterilmelidir.
4. **Başarılı:** Usta kartları listelenmelidir.

Bu durumlar birbirinden ayrılmalı ve uygun kullanıcı arayüzleriyle temsil edilmelidir.

## 6. Tema Desteği

- Material 3 kullanılmalıdır.
- Açık tema ve koyu tema desteklenmelidir.
- Kullanıcı uygulama içinden tema değiştirebilmelidir.
- Tema değişimi uygulamanın ilgili ekranlarına ve bileşenlerine tutarlı biçimde yansımalıdır.

## 7. Bellek Yönetimi ve Kod Kalitesi

- Kullanılan `TextEditingController` gibi controller nesneleri gerektiğinde `dispose()` edilmelidir.
- Bir asenkron işlem tamamlandığında ekran kapatılmış olabilir. Bu nedenle uygun durumlarda `if (mounted)` kontrolü kullanılmalıdır.
- Ekranlarda `RenderFlex overflow` hatası bulunmamalıdır.
- Farklı ekranlarda tekrarlanan bileşenler uygun widget dosyalarına ayrılmalıdır.
- Hatalar sessizce gizlenmemeli ve kullanıcıya gerektiğinde anlaşılır geri bildirim verilmelidir.

## 8. Önerilen Ekip İş Bölümü

### Geliştirici 1

- Veri modelleri
- `Usta`, `ArizaTalebi` ve `HizmetKategorisi`
- `fromJson` ve `copyWith`
- `IUstaServisi` ve servis katmanı
- Ana liste, arama ve filtreleme ekranı

### Geliştirici 2

- Usta detay ekranı
- `Hero` geçişleri
- Usta kartı widget'ı
- Müsaitlik rozeti
- Puan göstergesi
- Fiyat teklifi istemek için `ModalBottomSheet`

### Geliştirici 3

- Arıza kaydı formu
- Form validasyonları
- Taleplerim ve Kayıtlı Ustalar ekranı
- Sayfa geçişleri ve navigasyon
- Açık/koyu tema yönetimi

## 9. Geliştirme Önceliği

Öncelik, zorunlu gereksinimlerin eksiksiz ve çalışır şekilde uygulanmasıdır.

Yeni özellikler eklemek uğruna zorunlu gereksinimler atlanmamalıdır. Gereksinimlerde belirtilmeyen büyük özellikler, ek mimari katmanlar veya gereksiz karmaşıklıklar kendiliğinden projeye eklenmemelidir.

Görsel kalite önemlidir ancak hiçbir tasarım tercihi zorunlu işlevlerin veya teknik şartların önüne geçemez.