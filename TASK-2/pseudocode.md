AD SOYAD:NUH DAĞ
ÖĞRENCİ NO:

BASLA

    // 1. Kullanıcı Girişi Kontrolü
    Yaz("Lütfen giriş yapınız.")
    EGER kullanici_girisi_dogrulandi ISE
        Yaz("Giriş başarılı.")
    DEGILSE
        Yaz("Giriş başarısız. Lütfen tekrar deneyin.")
        BITIR
    SON

    // 2. Ürün Kategorileri Arasında Gezinme
    DONGU kategori_secimi_devam == TRUE
        Yaz("Ürün kategorileri listeleniyor...")
        kategori = kategori_sec()
        ürün = ürün_sec(kategori)

        EGER ürün != BOS ISE
            // 3. Stok Kontrolü
            stok = stok_kontrol(ürün)
            EGER stok > 0 ISE
                Yaz("Ürün sepete ekleniyor...")
                sepete_ekle(ürün)
            DEGILSE
                Yaz("Ürün stokta yok!")
            SON
        SON

        kategori_secimi_devam = kullanici_devam_ediyor_mu()
    SON

    // 4. Sepeti Görüntüleme ve Düzenleme
    DONGU sepet_düzenleme_devam == TRUE
        sepeti_göster()
        işlem = sepet_islemi_sec()

        EGER işlem == "sil" ISE
            ürün_sil()
        DEGILSE EGER işlem == "adet_degistir" ISE
            adet_güncelle()
        DEGILSE
            Yaz("İşlem yapılmadı.")
        SON

        sepet_düzenleme_devam = kullanıcı_devam_ediyor_mu()
    SON

    // 5. İndirim Kodu Uygulama
    indirim_kodu = kod_al()
    EGER indirim_kodu_gecerli_mi(indirim_kodu) ISE
        indirimi_uygula()
        Yaz("İndirim başarıyla uygulandı.")
    DEGILSE
        Yaz("Geçersiz indirim kodu.")
    SON

    // 6. Minimum 50 TL Kontrolü
    toplam = sepet_toplami()
    EGER toplam < 50 ISE
        Yaz("Minimum alışveriş tutarı 50 TL olmalıdır.")
        BITIR
    SON

    // 7. Kargo Ücreti Hesaplama
    EGER toplam >= 200 ISE
        kargo = 0
        Yaz("Kargo ücretsiz.")
    DEGILSE
        kargo = 30
        Yaz("Kargo ücreti 30 TL eklendi.")
    SON

    // 8. Ödeme Yöntemi Seçimi
    Yaz("Ödeme yönteminizi seçiniz: (Kart / Havale / Kapıda)")
    ödeme_yöntemi = ödeme_sec()
    EGER ödeme_yöntemi != BOS ISE
        ödeme_al(ödeme_yöntemi, toplam + kargo)
        Yaz("Ödeme işlemi başarılı.")
    DEGILSE
        Yaz("Geçerli bir ödeme yöntemi seçilmedi.")
        BITIR
    SON

    // 9. Sipariş Onayı
    siparis_onayla()
    Yaz("Siparişiniz başarıyla oluşturuldu.")

BITIR
