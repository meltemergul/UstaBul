# UstaBul — Mimari ve Klasör Yapısı

## 1. Mimari Amaç

UstaBul, Flutter ve Dart ile geliştirilen, sorumlulukları ayrılmış bir mobil uygulamadır.

Projenin temel klasörleri:

- `models/`
- `services/`
- `screens/`
- `widgets/`

Bu klasörler hocanın belirttiği temel yapıdır ve korunmalıdır.

Amaç, veri modellerini, veri erişimini, sayfa arayüzlerini ve tekrar kullanılabilir bileşenleri birbirinden ayırmaktır.

Gereksiz mimari karmaşıklık oluşturulmamalıdır.

## 2. Önerilen Klasör Yapısı

```text
lib/
├── main.dart
├── models/
│   ├── usta.dart
│   ├── ariza_talebi.dart
│   └── hizmet_kategorisi.dart
├── services/
│   ├── i_usta_servisi.dart
│   └── usta_servisi.dart
├── screens/
│   ├── usta_listesi_screen.dart
│   ├── usta_detay_screen.dart
│   ├── ariza_kaydi_screen.dart
│   └── taleplerim_screen.dart
└── widgets/
    ├── usta_karti.dart
    ├── musaitlik_rozeti.dart
    └── puan_gostergesi.dart
```

Bu yapı başlangıç için önerilen temel yapıdır. Gereksinim duyulan küçük yardımcı dosyalar eklenebilir ancak hocanın istediği klasörler kaldırılmamalı ve gereksiz klasörler oluşturulmamalıdır.

## 3. Modeller

### 3.1. `Usta`

Bir ustanın uygulamada gösterilecek bilgilerini temsil eder.

Gereksinimlere göre aşağıdaki bilgileri kapsamalıdır:

- Kimlik bilgisi
- İsim
- Uzmanlık alanı
- Hizmet verdiği ilçeler
- Profil fotoğrafı veya avatar bilgisi
- Puan
- Ortalama servis ücreti
- Müsaitlik durumu
- Hizmet kalemleri
- Çalışma saatleri
- Tamamladığı iş sayısı
- Müşteri yorumları

Alanların isimleri ve veri tipleri uygulamanın diğer bölümleriyle uyumlu biçimde belirlenmelidir.

Modelde `fromJson` ve `copyWith` metotları bulunmalıdır.

### 3.2. `ArizaTalebi`

Kullanıcının oluşturduğu bir arıza kaydını temsil eder.

Gerekli alanlar:

- Kimlik bilgisi
- Arıza başlığı
- Arıza kategorisi
- Detaylı açıklama
- Adres veya ilçe
- Telefon numarası
- Aciliyet durumu
- Talep durumu

Talep durumları en az `Bekliyor`, `Usta Yolda` ve `Tamamlandı` değerlerini desteklemelidir.

Modelde `fromJson` ve `copyWith` metotları bulunmalıdır.

### 3.3. `HizmetKategorisi`

Usta uzmanlık alanlarını ve arıza kategorilerini tutarlı şekilde temsil etmek için enum kullanılmalıdır.

Zorunlu kategoriler:

- Tümü
- Elektrik
- Su Tesisatı
- Kombi/Klima
- Boya
- Çilingir

Beyaz eşya proje tanımında geçen bir hizmet alanıdır. Kategori enum'una nasıl dahil edileceği ekip tarafından kararlaştırılmalı ve mevcut zorunlu kategoriler korunmalıdır.

`Tümü`, filtre ekranında tüm kategorileri göstermek için kullanılabilir; tek bir ustanın uzmanlık alanı olarak değerlendirilmesi gerekmez.

## 4. Servis Katmanı

### 4.1. `IUstaServisi`

Usta verileriyle ilgili işlemlerin arayüzünü tanımlar.

Bu soyut servis tanımı, ekranların verinin nereden geldiğini bilmeden çalışabilmesini sağlar.

Gerekli işlemler en azından şu ihtiyaçları karşılamalıdır:

- Usta listesini getirmek
- Belirli bir ustayı kimliği üzerinden bulmak veya mevcut liste üzerinden seçmek
- Veri yükleme hatalarını üst katmana iletmek

Gerekli metot imzaları seçilen veri yaklaşımına göre belirlenmelidir.

### 4.2. `UstaServisi`

`IUstaServisi` tanımının çalışan uygulamasıdır.

Ekip aşağıdaki iki yaklaşımdan birini seçmelidir:

**Seçenek A — REST API**

- `http` paketiyle veri alınır.
- JSON verileri `Usta` modeline dönüştürülür.
- Bağlantı ve yanıt hataları ele alınır.

**Seçenek B — Gecikmeli servis**

- En az 12–15 detaylı usta kaydı sağlanır.
- Veri yükleme işlemi gecikmeli çalışır.
- Servis başarılı sonuç ve hata durumlarını yönetebilecek şekilde tasarlanır.
- Veri ekranların içine gömülmez; servis katmanında tutulur.

Hangi yaklaşım seçilirse seçilsin, ekranların veri erişimini `IUstaServisi` üzerinden gerçekleştirmesi hedeflenmelidir.

## 5. Ekranların Sorumlulukları

### 5.1. `usta_listesi_screen.dart`

Sorumlulukları:

- Usta listesini göstermek
- Anlık arama işlemini yönetmek
- Kategori filtrelerini yönetmek
- Listeyi aşağı çekerek yenilemek
- Yükleniyor, hata, boş liste ve başarılı durumları göstermek
- Seçilen ustanın detay ekranına geçiş yapmak

Listeleme `ListView.builder`, arama `TextField`, kategori filtreleri `ChoiceChip` ve yenileme `RefreshIndicator` ile uygulanmalıdır.

Usta kartının görünümü `widgets/usta_karti.dart` üzerinden kullanılmalıdır.

### 5.2. `usta_detay_screen.dart`

Sorumlulukları:

- Seçilen ustanın bilgilerini göstermek
- Hizmetleri, çalışma saatlerini ve hizmet bölgelerini göstermek
- Tamamlanan iş sayısını ve müşteri yorumlarını göstermek
- Usta görseli için `Hero` geçişini sağlamak
- Teklif isteme alt penceresini açmak

Bu ekran, seçilen `Usta` modelini kullanmalıdır. Liste ekranından detay ekranına geçerken seçilen ustanın yanlış gösterilmemesi gerekir.

### 5.3. `ariza_kaydi_screen.dart`

Sorumlulukları:

- Arıza kaydı formunu göstermek
- Form alanlarını yönetmek
- `Form` ve `GlobalKey<FormState>` ile validasyon yapmak
- Hatalı girdiler için mesaj göstermek
- Başarılı form gönderiminde bir `ArizaTalebi` oluşturmak

Telefon numarası, zorunlu alanlar ve açıklamanın minimum uzunluğu kontrol edilmelidir.

Formun başarılı olmasıyla talebin gerçekten kaydedilmesi birbirinden ayrı konulardır. Uygulamanın veri saklama yaklaşımına göre kaydetme işlemi uygulanmalıdır.

### 5.4. `taleplerim_screen.dart`

Sorumlulukları:

- Kullanıcının oluşturduğu arıza taleplerini göstermek
- Talep durumlarını göstermek
- Favori ustaları görüntülemek

Taleplerim ve Kayıtlı Ustalar aynı ana sayfa içinde iki ayrı bölüm veya sekme olarak sunulabilir. Kullanıcının iki özelliğe de kolayca erişebilmesi gerekir.

Favori ustaların ve taleplerin verisi tek bir ekran dosyasında tanımlanmış örneklerden yönetilmemelidir.

## 6. Ortak Widget'lar

### `usta_karti.dart`

Ustanın listede gösterilen profil kartını temsil eder.

İsim, uzmanlık alanı, ilçe, puan, servis ücreti ve müsaitlik bilgilerini gösterir.

Kart, seçilen ustayı detay ekranına iletebilmelidir.

### `musaitlik_rozeti.dart`

Ustanın Müsait veya Yoğun durumunu gösterir.

Metin ve görsel durum birbiriyle uyumlu olmalıdır. Durum yalnızca renkle anlatılmamalı; kullanıcı rozetteki metni de okuyabilmelidir.

### `puan_gostergesi.dart`

Ustanın müşteri puanını tutarlı biçimde gösterir.

Puan gösterimi liste ve detay ekranında aynı görsel yaklaşımı kullanmalıdır.

Bu üç bileşen ayrı dosyalarda bulunmalıdır.

## 7. Navigasyon

Uygulamada dört ana ekran grubu bulunur:

1. Usta Listesi
2. Usta Detay
3. Arıza Kaydı Oluşturma
4. Taleplerim ve Kayıtlı Ustalar

Usta detay ekranı, listeden seçilen ustaya göre açılır. Alt menü, ana ekran grupları arasında geçiş sağlar.

Navigasyon için `NavigationBar` ile birlikte `GoRouter` veya standart Flutter navigasyonu kullanılabilir. Ekip tek bir yaklaşım seçmeli ve tutarlı biçimde uygulamalıdır.

Detay ekranı alt menüde bağımsız bir ana sekme olmak zorunda değildir; ana liste üzerinden açılabilir.

## 8. Tema Yapısı

Material 3 tabanlı açık ve koyu tema bulunmalıdır.

Tema ayarları tek bir yerde tutarlı şekilde yönetilmelidir. Ekranlar renkleri birbirinden bağımsız ve rastgele seçmemelidir.

Renkler, yazı stilleri, kartlar, butonlar ve durum renkleri için `design-system.md` esas alınmalıdır.

Kullanıcı uygulama içinden tema değiştirebilmelidir.

## 9. Ekip Entegrasyonu

Üç geliştirici paralel çalıştığı için ortak modellerin ve widget'ların arayüzleri erken belirlenmelidir.

Özellikle:

- Usta modelinin alanları ekipçe netleştirilmelidir.
- Usta kartının hangi verileri aldığı belirlenmelidir.
- Detay ekranının seçilen ustayı nasıl aldığı kararlaştırılmalıdır.
- Servis metotlarının isimleri ve dönüş tipleri ortaklaştırılmalıdır.
- Navigasyon yöntemi ekipçe seçilmelidir.

Bir geliştiricinin dosya isimleri veya metot imzaları üzerinde yaptığı değişiklik, diğer geliştiricilerin kodunu etkileyebilir. Bu nedenle ortak dosyalar gelişigüzel yeniden yazılmamalıdır.

## 10. Mimari Sınırlar

Bu proje için zorunlu temel klasörler `models/`, `services/`, `screens/` ve `widgets/` klasörleridir.

Hocanın istemediği yeni mimari desenleri, gereksiz katmanları veya kapsamlı altyapıları zorunlu hale getirme.

Amaç, mevcut ders kapsamına uygun, anlaşılır ve işlevsel bir uygulama oluşturmaktır.