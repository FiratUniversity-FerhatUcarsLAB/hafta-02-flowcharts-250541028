AD SOYAD:NUH DAĞ
ÖĞRENCİ NO:250541028

BASLA

    // Kimlik Doğrulama
    Yaz("Lütfen TC Kimlik Numaranızı Giriniz:")
    TC = Girdi_Al()

    EGER Kimlik_Dogrula(TC) ISE
        Yaz("Kimlik doğrulandı. Hoş geldiniz.")
    DEGILSE
        Yaz("Geçersiz TC Kimlik Numarası! Lütfen tekrar deneyiniz.")
        BITIR
    SON

    // Randevu Alma Modülü
    DONGU poliklinik_secimi_devam == TRUE

        // Poliklinik Seçimi
        Yaz("Mevcut Poliklinikler:")
        Poliklinik_Listesini_Goster()
        poliklinik = Poliklinik_Sec()

        EGER poliklinik != BOS ISE
            Yaz("Seçilen Poliklinik: " + poliklinik)

            // Doktor Listesi
            Doktor_Listesini_Goster(poliklinik)
            doktor = Doktor_Sec()

            EGER doktor != BOS ISE
                Yaz("Seçilen Doktor: " + doktor)

                // Uygun Saat Seçimi
                Uygun_Saatleri_Goster(doktor)
                saat = Saat_Sec()

                EGER saat != BOS ISE
                    // Randevu Onayı
                    Yaz("Randevu onaylanıyor...")
                    Randevu_Onayla(TC, poliklinik, doktor, saat)

                    // SMS Gönderimi
                    SMS_Gonder(TC, doktor, saat)
                    Yaz("Randevunuz başarıyla oluşturuldu. Onay SMS'i gönderildi.")
                    poliklinik_secimi_devam = FALSE
                DEGILSE
                    Yaz("Uygun saat seçilmedi. Lütfen tekrar deneyin.")
                SON

            DEGILSE
                Yaz("Doktor seçimi yapılmadı. Lütfen tekrar deneyin.")
            SON

        DEGILSE
            Yaz("Poliklinik seçimi yapılmadı. Lütfen bir poliklinik seçin.")
        SON

    SON

    Yaz("Randevu Alma İşlemi Tamamlandı.")

BITIR
