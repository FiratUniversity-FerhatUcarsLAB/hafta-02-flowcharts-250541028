AD SOYAD:NUH DAĞ
ÖĞRENCİ NO:22505541028
🎯 Sistem Adı:

Online Alışveriş Sepet Sistemi

🧠 Sistem Amacı:

Bu sistem, kullanıcıların bir e-ticaret platformu üzerinden ürünleri incelemesini, sepete eklemesini, indirim ve kargo koşullarını değerlendirmesini, ödeme yöntemini seçmesini ve sipariş onayını tamamlamasını modellemektedir.
Sistem, hem kullanıcı etkileşimini hem de kontrol koşullarını içeren bir karar-döngü tabanlı iş akışı içerir.

⚙️ Sistem İşleyişi:

Kullanıcı Girişi:
Sistem ilk olarak kullanıcı oturumunun olup olmadığını kontrol eder.
Giriş yapılmadıysa, kullanıcıya “Giriş Yap” ekranı gösterilir.

Ürün Kategorilerinde Gezinme (Döngü):
Kullanıcı dilediği kadar kategori arasında dolaşabilir.
Her kategori seçiminde ürünler listelenir.

Ürün Seçimi ve Stok Kontrolü:
Kullanıcı bir ürün seçtiğinde sistem stok kontrolü yapar.

Stok varsa ürün sepete eklenir.

Stok yoksa uyarı mesajı verilir.

Sepeti Görüntüleme ve Düzenleme (Döngü):
Kullanıcı, sepet içeriğini görüntüleyebilir, ürün miktarını değiştirebilir veya ürünü silebilir.
Kullanıcı onaylayana kadar bu işlem tekrarlanabilir.

İndirim Kodu Uygulama (Koşul):
Kullanıcı bir indirim kodu girebilir.

Kod geçerliyse indirim uygulanır.

Kod geçersizse hata mesajı verilir.

Minimum Tutar Kontrolü (Koşul):
Toplam alışveriş tutarı 50 TL’den azsa, sistem uyarı verir ve devam etmez.
50 TL ve üzeri tutarlarda süreç devam eder.

Kargo Ücreti Hesaplama (Koşul):

200 TL ve üzeri alışverişlerde kargo ücretsizdir.

200 TL altı alışverişlerde 30 TL kargo ücreti eklenir.

Ödeme Yöntemi Seçimi (Koşul):
Kullanıcı kredi kartı, havale/EFT veya kapıda ödeme seçeneklerinden birini seçer.
Geçerli bir seçim yapılmazsa sistem hata verir.

Sipariş Onayı:
Kullanıcı ödeme işlemini tamamladığında sipariş onaylanır ve süreç başarıyla sonlanır.

🧩 Kullanılan Mantıksal Yapılar:
Yapı Türü	Kullanım Amacı	Örnek
EGER – ISE – DEGILSE	Koşul denetimi (ör. stok, indirim, tutar, kargo)	EGER stok > 0 ISE ... DEGILSE ... SON
DONGU – SON	Tekrarlanan işlemler (kategori gezme, sepet düzenleme)	DONGU kategori_secimi_devam == TRUE ... SON
BASLA / BITIR	Her ana sürecin başlangıç ve bitişini belirtir	BASLA ... BITIR
📝 NOTLAR

Sistem Modeli, klasik bir e-ticaret sepet sürecini temel alır.
Döngü ve koşulların iç içe kullanımıyla “Orta-Zor” zorluk düzeyindedir.

Pseudocode formatı, laboratuvar standartlarına uygun olarak:

Koşullar: EGER ... ISE ... DEGILSE ... SON

Döngüler: DONGU ... SON

Yapısal Başlangıç/Bitiş: BASLA – BITIR şeklinde yazılmıştır.

Kontrol Noktaları:
Sistem boyunca 6 temel kontrol noktası bulunur:

Kullanıcı giriş doğrulaması

Stok kontrolü

İndirim kodu geçerliliği

Minimum 50 TL kontrolü

Kargo ücretsiz koşulu

Ödeme yöntemi kontrolü

Amaç:
Öğrencinin koşullu akış yapıları, döngüler ve karar noktaları arasındaki ilişkileri bir pseudocode ve akış diyagramı üzerinden uygulamalı biçimde öğrenmesini sağlamaktır.

Ek Not:
Eğer bu sistem, akış diyagramı (Graphviz/DOT) formatında çizilecekse,
“layout” parametresi dot olarak kalmalı, nokta yazılmamalıdır.
(layout=dot; veya bu satır tamamen kaldırılabilir.)
