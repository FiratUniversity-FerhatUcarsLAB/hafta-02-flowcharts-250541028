AD SOYAD : NUH DAĞ
ÖĞRENCİ NO:250541028

Tabii ✅
Aşağıda, “Hastane Randevu ve Tahlil Sistemi” için yazılmış pseudocode ve akış diyagramına uygun Sonuç Açıklaması bölümü yer alıyor.
Bu bölüm, genellikle rapor veya laboratuvar ödevi sonunda yazılır ve sistemin nasıl çalıştığını, hangi mantıkla tasarlandığını özetler.

🧾 SONUÇ AÇIKLAMASI

Bu çalışmada, bir Hastane Randevu ve Tahlil Sonuçları Yönetim Sistemi tasarlanmıştır.
Sistem, iki temel modül üzerine inşa edilmiştir:

Randevu Alma Modülü

Tahlil Sonuçlarını Görüntüleme Modülü

Öncelikle kullanıcıdan TC kimlik numarası alınarak kimlik doğrulaması yapılmaktadır.
Kullanıcı doğrulandıktan sonra ana menü üzerinden yapmak istediği işlemi seçer:

Randevu almak,

Tahlil sonuçlarını görüntülemek,

veya sistemden çıkmak.

Randevu Alma Modülünde, kullanıcı bir poliklinik seçer, ardından o polikliniğe ait doktorlar listelenir.
Doktor seçildikten sonra sistem uygun randevu saatlerini gösterir.
Kullanıcı saat seçimini yaptığında randevu onaylanır ve sistem tarafından SMS bilgilendirmesi gönderilir.

Tahlil Sonuçları Modülünde, sistem önce kullanıcının tahlil kayıtlarının olup olmadığını kontrol eder.
Eğer tahlil mevcutsa, sonucun hazır olup olmadığı kontrol edilir.
Sonuç hazırsa, kullanıcı tahlil sonuçlarını görüntüleyebilir ve dilerse PDF formatında indirebilir.
Eğer sonuç henüz hazır değilse, kullanıcıya “Sonuç henüz hazır değil” mesajı verilir.

Sistem, her işlem sonunda kullanıcıya “Başka bir işlem yapmak ister misiniz?” sorusunu yönelterek döngüsel biçimde çalışır.
Kullanıcı çıkış seçeneğini seçtiğinde sistem sonlanır.

Bu model, kullanıcı odaklı bir hastane otomasyonunun temel iş akışını yansıtmaktadır.
Pseudocode yapısında EGER–ISE–DEGILSE karar yapıları ve DONGU döngüleri kullanılarak kontrol noktaları açıkça belirtilmiştir.
Sistemin modüler tasarımı, hem randevu hem tahlil işlemlerinin bağımsız fakat bütünleşik biçimde çalışmasını sağlamaktadır.
