AD SOYAD:NUH DAĞ
ÖĞRENCİ NO:250541028

BASLA

    // Öğrenci Girişi
    Yaz("Lütfen öğrenci numaranızı giriniz:")
    ogr_no = Girdi_Al()
    Yaz("Lütfen şifrenizi giriniz:")
    sifre = Girdi_Al()

    EGER Giris_Dogrula(ogr_no, sifre) ISE
        Yaz("Giriş başarılı. Hoş geldiniz, öğrenci no: " + ogr_no)
    DEGILSE
        Yaz("Hatalı giriş bilgileri! Sistem sonlandırılıyor.")
        BITIR
    SON

    // Ders Listesini Görüntüleme
    Yaz("Mevcut dersler listeleniyor...")
    Ders_Listesini_Goster()

    toplam_kredi = 0
    DONGU kayıt_devam == TRUE

        Yaz("Ders eklemek için 1, ders çıkarmak için 2, kayıtı tamamlamak için 0 giriniz:")
        secim = Girdi_Al()

        EGER secim == 1 ISE
            Yaz("Eklemek istediğiniz ders kodunu giriniz:")
            ders = Girdi_Al()

            // Kontenjan Kontrolü
            EGER Kontenjan_Mevcut_Mu(ders) ISE

                // Önkoşul Dersi Kontrolü
                EGER Onkosul_Saglandi_Mi(ogr_no, ders) ISE

                    // Zaman Çakışması Kontrolü
                    EGER Zaman_Cakismasi_Yok_Mu(ogr_no, ders) ISE

                        // Kredi Limiti Kontrolü
                        ders_kredi = Ders_Kredisi(ders)
                        EGER toplam_kredi + ders_kredi <= 35 ISE
                            Ders_Ekle(ogr_no, ders)
                            toplam_kredi = toplam_kredi + ders_kredi
                            Yaz("Ders başarıyla eklendi. Toplam kredi: " + toplam_kredi)
                        DEGILSE
                            Yaz("Kredi limiti aşıldı! (35 krediyi geçemezsiniz)")
                        SON

                    DEGILSE
                        Yaz("Zaman çakışması tespit edildi! Bu dersi ekleyemezsiniz.")
                    SON

                DEGILSE
                    Yaz("Önkoşul dersi tamamlanmamış! Bu dersi seçemezsiniz.")
                SON

            DEGILSE
                Yaz("Kontenjan dolu! Bu derse kayıt yapılamaz.")
            SON

        DEGILSE EGER secim == 2 ISE
            Yaz("Çıkarmak istediğiniz ders kodunu giriniz:")
            ders = Girdi_Al()
            Ders_Cikar(ogr_no, ders)
            toplam_kredi = toplam_kredi - Ders_Kredisi(ders)
            Yaz("Ders çıkarıldı. Güncel kredi: " + toplam_kredi)

        DEGILSE EGER secim == 0 ISE
            Yaz("Ders kayıt işlemi tamamlanıyor...")
            kayıt_devam = FALSE
        DEGILSE
            Yaz("Geçersiz seçim. Lütfen tekrar deneyiniz.")
        SON

    SON

    // Danışman Onayı Kontrolü
    gpa = GPA_Hesapla(ogr_no)
    EGER gpa < 2.5 ISE
        Yaz("GPA 2.5 altında. Danışman onayı gerekli.")
        Danisman_Onayi_Al(ogr_no)
    DEGILSE
        Yaz("GPA yeterli. Danışman onayı gerekmez.")
    SON

    // Kayıt Özeti ve Onay
    Yaz("Kayıt özeti oluşturuluyor...")
    Kayit_Ozetini_Goster(ogr_no)
    Yaz("Onaylamak için 'E' tuşuna basınız:")
    onay = Girdi_Al()

    EGER onay == "E" ISE
        Yaz("Ders kayıt işleminiz başarıyla tamamlandı!")
    DEGILSE
        Yaz("Kayıt işlemi iptal edildi.")
    SON

BITIR
