# UstaBul — Geliştirme Kuralları ve Uygulama Becerileri

## 1. Genel Çalışma Prensibi

UstaBul projesinde bir Flutter geliştiricisi gibi dikkatli, tutarlı ve kontrollü çalış.

Önceliklerin:

1. Hocanın zorunlu gereksinimlerine uymak.
2. Mevcut kodun yapısını anlamadan değişiklik yapmamak.
3. Temiz, okunabilir ve tekrar kullanılabilir kod yazmak.
4. Ekranları işlevsel hale getirmek.
5. Tasarım bütünlüğünü korumak.
6. Yapılan değişiklikleri test etmek.

Hocanın belirttiği bir gereksinimi kendi kararınla kaldırma, başka bir teknolojiyle değiştirme veya önemsiz kabul etme.

## 2. Kod Yazma Kuralları

- Dart ve Flutter'ın yerleşik özelliklerini uygun şekilde kullan.
- Kodları tek bir büyük dosyada toplama.
- Model, servis, ekran ve tekrar kullanılabilir widget sorumluluklarını birbirinden ayır.
- Bir widget yalnızca küçük ve anlaşılır bir sorumluluğu yerine getirmelidir.
- Aynı arayüz parçasını birden fazla yerde kullanıyorsan uygun olduğunda ortak widget oluştur.
- Gereksiz soyutlamalar ve ihtiyaç duyulmayan katmanlar ekleme.
- Kodun anlaşılabilirliğini azaltan gereksiz kısaltmalardan kaçın.
- Mevcut kodu anlamadan dosyaları topluca yeniden yazma.
- Kullanılan paketlerin mevcut proje sürümüyle uyumunu kontrol et.
- Bir işlevi tamamlamadan yalnızca görsel olarak çalışıyormuş gibi gösterme.

## 3. Veri ve Servis Kuralları

- Verileri doğrudan ekran dosyalarında tanımlama.
- Veri erişimini servis katmanında tut.
- Usta verileri için `IUstaServisi` soyut servis tanımını kullan.
- Ekip tarafından seçilen veri yaklaşımına sadık kal: gerçek REST API veya gecikmeli çalışan, detaylı kayıtlar içeren servis katmanı.
- En az 12–15 detaylı usta kaydı şartını koru.
- Model dönüşümlerinde `fromJson` ve `copyWith` metotlarını uygula.
- Servis hatalarını uygun şekilde ele al.
- Yükleniyor, hata, boş liste ve başarılı veri durumlarının tamamını uygula.
- Tekrar Dene butonu gerçekten veri yükleme işlemini yeniden başlatmalıdır.
- Arama ve kategori filtreleri gerçek liste verisi üzerinde çalışmalıdır.
- Yeni bir veri kaynağı kullanıyorsan mevcut ekranların bu kaynağa nasıl bağlandığını kontrol et.

## 4. Flutter Form Kuralları

- Arıza formunda `Form` ve `GlobalKey<FormState>` kullan.
- Zorunlu alanları doğrula.
- Telefon numarasının biçimini kontrol et.
- Açıklama için minimum uzunluk doğrulaması uygula.
- Hata mesajlarını ilgili alanın yanında anlaşılır biçimde göster.
- Başarısız validasyonda formun başarılı şekilde kaydedildiğini gösterme.
- Form controller'larını uygun yaşam döngüsünde yönet ve `dispose()` et.
- Formun farklı ekran boyutlarında taşmadan çalışmasını sağla.

## 5. Widget ve Animasyon Kuralları

- Usta kartı, müsaitlik rozeti ve puan göstergesi ayrı widget dosyalarında bulunmalıdır.
- Usta listesi `ListView.builder` kullanmalıdır.
- Liste yenileme `RefreshIndicator` ile yapılmalıdır.
- Kategori filtreleri `ChoiceChip` ile uygulanmalıdır.
- Usta görseli ile detay ekranındaki görsel arasında `Hero` geçişi bulunmalıdır.
- Teklif isteme alt penceresi `ModalBottomSheet` ile açılmalıdır.
- Animasyonlar işlevi desteklemeli; gereksiz veya aşırı hareket kullanılmamalıdır.
- Küçük ekranlarda uzun isimler, yorumlar ve fiyatlar arayüzü bozmamalıdır.

## 6. Asenkron İşlemler ve Bellek Yönetimi

- Asenkron işlemler için uygun `async` ve `await` kullanımını tercih et.
- Ekran kapandıktan sonra `State` üzerinde işlem yapma riskini kontrol et.
- Gereken yerlerde asenkron işlem sonrasında `if (mounted)` kontrolü kullan.
- Kullanılan `TextEditingController` ve benzeri kaynakları yaşam döngülerine uygun şekilde temizle.
- Gereksiz tekrarlanan isteklerden ve kontrolsüz durum güncellemelerinden kaçın.
- Hataları yakalarken anlamlı hata yönetimini koru.

## 7. Tema ve Tasarım Kuralları

- Material 3 standartlarına uy.
- Açık ve koyu temayı destekle.
- Tema değişimini uygulama içinden yapılabilir tut.
- Renkleri, metin stillerini ve ortak görsel değerleri `design-system.md` dosyasındaki kararlara göre uygula.
- Rastgele renkler veya her ekranda farklı buton stilleri kullanma.
- Hazır yapay zekâ arayüzlerinde sık görülen fosforlu mor, aşırı gradient, gereksiz glow ve cam efekti kullanımından kaçın.
- Görsel çekiciliği okunabilirlik ve kullanılabilirlikle birlikte değerlendir.
- Tüm ekranlarda tutarlı boşluklar, kart köşeleri, yazı stilleri ve ikon kullanımı sağla.

## 8. Hata Kontrolü ve Test

Her anlamlı geliştirme sonrasında:

1. Değiştirilen kodu gözden geçir.
2. İlgili ekranın normal durumunu kontrol et.
3. Yükleniyor, hata ve boş liste gibi ilgili durumları kontrol et.
4. Form validasyonlarını dene.
5. Navigasyonun çalıştığını doğrula.
6. Açık ve koyu temayı kontrol et.
7. Küçük ekranlarda taşma olup olmadığını kontrol et.
8. Uygunsa `flutter analyze` çalıştır ve bulunan sorunları düzelt.

Gerçekten çalıştırılmamış bir testi çalıştırılmış gibi bildirme.

## 9. Ekip Çalışması ve Git

- Her geliştirici kendi branch'inde çalışmalıdır.
- Commit mesajları yapılan değişikliği açıklamalıdır.
- Birden fazla geliştiricinin ortak kullandığı dosyaları değiştirmeden önce mevcut sorumlulukları kontrol et.
- Başka bir geliştiricinin tamamladığı işi izinsiz olarak yeniden yazma.
- Bir ekranın ihtiyaç duyduğu model veya widget henüz hazır değilse önce ekipteki ilgili geliştiriciyle arayüz sözleşmesini netleştir.
- Birleştirme sırasında oluşabilecek çakışmaları dikkatle çöz.
- Çalışan kodu gereksiz yere değiştirme.

## 10. Değişiklik Yaparken İzlenecek Yol

Bir görev aldığında:

1. İlgili Markdown dosyalarını oku.
2. Etkilenecek mevcut dosyaları incele.
3. Değişikliğin hangi geliştiricinin sorumluluğunda olduğunu belirle.
4. Gereksinime uygun en küçük ve anlaşılır çözümü uygula.
5. İlgili ekranları ve bağlantılı bileşenleri kontrol et.
6. Testleri ve analizleri çalıştır.
7. Nelerin değiştiğini, hangi dosyaların etkilendiğini ve hangi kontrollerin yapıldığını açıkça bildir.

Amaç yalnızca kod üretmek değil, hocanın şartlarına uyan, çalışan ve bakımı kolay bir uygulama oluşturmaktır.