AAD SOYAD:NUH DAĞ
ÖĞRENCİ NO:250541028

🏦 ATM Para Çekme Sistemi – Sistem Açıklaması

Bu sistem, bir ATM (Otomatik Para Çekme Makinesi) üzerinden müşterilerin güvenli bir şekilde para çekme işlemi yapabilmelerini sağlayan bir yazılım akışını tanımlar. Sistem, kullanıcı kimlik doğrulaması, bakiye ve limit kontrolleri, işlem doğrulama mekanizmaları ve kullanıcı etkileşim döngülerinden oluşur.

🔹 1. Kart ve PIN Doğrulama

Kullanıcı, ATM’ye bankamatik kartını yerleştirdiğinde sistem, PIN (kişisel kimlik numarası) girişi ister.
Girilen PIN, sistemde kayıtlı verilerle karşılaştırılır:

Eğer PIN doğru ise kullanıcı işlem menüsüne yönlendirilir.

Eğer PIN hatalı ise hata sayısı bir artırılır.

Üç kez hatalı PIN girilmesi durumunda kart bloke edilir ve işlem sonlandırılır.

Bu aşama, güvenlik amacıyla yetkisiz erişimi önlemeyi hedefler.

🔹 2. İşlem Menüsü

PIN doğrulamasından sonra kullanıcıya üç temel seçenek sunulur:

Bakiye Görüntüleme

Para Çekme

Çıkış

Kullanıcı seçim yaptıktan sonra sistem, ilgili işleme yönlendirme yapar. Yanlış seçim yapılması durumunda, sistem kullanıcıyı uyararak menüye geri döndürür.

🔹 3. Bakiye Görüntüleme

Kullanıcı bakiye sorgulama seçeneğini seçtiğinde, sistem mevcut hesap bakiyesini ekranda gösterir. Ardından kullanıcıya “Başka işlem yapmak ister misiniz?” sorusu yöneltilir.

Evet (E) yanıtında menüye geri dönülür.

Hayır (H) yanıtında işlem sonlandırılır, kart iade edilir.

🔹 4. Para Çekme İşlemi

Kullanıcı para çekme seçeneğini seçtiğinde, sistem aşağıdaki kontrolleri sırasıyla gerçekleştirir:

Yetersiz Bakiye Kontrolü:
Girilen tutar, mevcut bakiyeden büyükse sistem “Yetersiz bakiye” uyarısı verir ve tutar yeniden girilmek üzere kullanıcıya geri dönülür.

20 TL’nin Katı Kontrolü:
Çekilmek istenen tutarın 20 TL’nin katı olup olmadığı kontrol edilir. Değilse sistem “Tutar 20 TL’nin katı olmalıdır” uyarısı verir ve kullanıcıdan yeni giriş ister.

Günlük Limit Kontrolü:
Bankanın belirlediği günlük para çekme limitinin aşılmadığı doğrulanır. Limit aşımı varsa “Günlük limit aşıldı” mesajı gösterilir.

Bu kontrollerin hepsi başarıyla geçildikten sonra sistem, parayı verir ve işlem fişini çıkarır. Kullanıcıya işlem sonucunun başarılı olduğu bildirilir.

🔹 5. İşlem Tekrarı

Her başarılı işlemin sonunda sistem kullanıcıya şu soruyu yöneltir:
“Başka bir işlem yapmak ister misiniz?”

Eğer Evet (E) yanıtı verilirse sistem tekrar ana menüye döner.

Eğer Hayır (H) yanıtı verilirse, sistem kartı iade eder ve “İyi günler” mesajı ile sonlanır.

🔹 6. Sistem Döngüleri ve Koşullar

Sistemde iki temel döngü yapısı bulunur:

PIN Doğrulama Döngüsü: Üç hatalı girişe kadar tekrar edilir.

İşlem Tekrarı Döngüsü: Kullanıcı “Evet” yanıtı verdiği sürece devam eder.

Koşul ifadeleri (EĞER-İSE) hem doğrulama (PIN, bakiye, limit) hem de işlem geçerliliği (20 TL katı kontrolü) için kullanılmıştır.

🔹 7. Sistem Çıkışı

Kullanıcı “Çıkış” seçeneğini seçtiğinde veya işlem tekrarını reddettiğinde:

Kart ATM’den iade edilir,

Fiş verilmişse kaydedilir,

Sistem “İyi günler” mesajı göstererek işlemi sonlandırır.

⚙️ Özetle Sistem İşleyişi

Kart tak → PIN doğrula (3 hak)

Menü göster → seçim yap

Bakiye görüntüle veya para çek

Para çekme sırasında tüm kontrolleri uygula

İşlem sonrası tekrar isteği sor → devam et veya bitir
