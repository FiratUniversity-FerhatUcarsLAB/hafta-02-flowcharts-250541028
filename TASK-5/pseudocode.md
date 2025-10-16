AD SOYAD:NUH DAĞ
ÖĞRENCİ NO:250541028

BASLA

    EGER sistem_aktif DEGILSE
        Yaz("Sistem kapalı. Çalıştırmak için aktif edin.")
        BITIR
    SON

    // Sonsuz döngü: sürekli sensör okuma ve alarm kontrolü
    DONGU DOĞRU

        // Sensör okuma
        hareket_var = Hareket_Sensor_Oku()
        kapi_pencere_acik = Kapi_Pencere_Sensor_Oku()
        alarm_sifirlandi = Alarm_Sifirlama_Kontrol()
        ev_sahibi_evde = Ev_Sahibi_Kontrol()

        // Tehdit Algılama
        EGER hareket_var ISE
            Kamera_Aktive_Et()
        SON

        EGER kapi_pencere_acik ISE
            Kamera_Aktive_Et()
        SON

        // Yanlış alarm kontrolü
        EGER ev_sahibi_evde ISE
            Yaz("Yanlış alarm. Alarm devreye girmedi.")
        DEGILSE
            // Alarm seviyesi belirleme
            EGER hareket_var VE kapi_pencere_acik ISE
                alarm_seviyesi = 3 // yüksek
            DEGILSE EGER hareket_var ISE
                alarm_seviyesi = 2 // orta
            DEGILSE
                alarm_seviyesi = 1 // düşük
            SON

            // Alarmı aktive et ve bildirim gönder
            Alarm_Aktif_Et(alarm_seviyesi)
            Bildirim_Gonder(SMS, App, Email, alarm_seviyesi)
        SON

        // Alarm sıfırlama kontrolü
        EGER alarm_sifirlandi ISE
            Alarm_Sifirla()
        SON

        Bekle(1 saniye) // Döngü tekrar başlat
    SON

BITIR
