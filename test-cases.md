# Test Case'ler — automationexercise.com

**Hazırlayan:** Hatice Pınar | **Tarih:** 17.10.2026 | **Sürüm:** 1.1
**Ortam:** Google Chrome (güncel), Windows, masaüstü 1920x1080

## Özet

| Pass | Fail | Blocked | Not Run | Toplam |
|------|------|---------|---------|--------|
| 17   | 5    | 0       | 1       | 23     |

| TC ID | Modül | Başlık | Öncelik | Durum |
|-------|-------|--------|---------|-------|
| TC-01 | Signup | Geçerli bilgilerle kayıt olma | High | ✅ Pass |
| TC-02 | Signup | Kayıtlı e-posta ile tekrar kayıt | High | ✅ Pass |
| TC-03 | Signup | Telefon alanına geçersiz değer | Medium | ❌ Fail |
| TC-04 | Signup | Adres alanlarına geçersiz format girme | Medium | ❌ Fail |
| TC-05 | Signup | Zorunlu alanı (Password) boş bırakma | High | ✅ Pass |
| TC-06 | Login | Doğru bilgilerle giriş | High | ✅ Pass |
| TC-07 | Login | Yanlış şifre ile giriş | High | ✅ Pass |
| TC-08 | Login | Çıkış yapma (Logout) | Medium | ✅ Pass |
| TC-09 | Products | Tüm ürünleri listeleme | Medium | ✅ Pass |
| TC-10 | Products | Ürün arama — geçerli kelime | High | ✅ Pass |
| TC-11 | Products | Ürün arama — sonuçsuz kelime | Low | ❌ Fail |
| TC-12 | Products | Kategori filtresi | Medium | ✅ Pass |
| TC-13 | Products | Ürün detay sayfası | Medium | ✅ Pass |
| TC-14 | Cart | Sepete ürün ekleme | High | ✅ Pass |
| TC-15 | Cart | Ürün detayından miktar ile ekleme | High | ✅ Pass |
| TC-16 | Cart | Sepette geçersiz miktar (0 / negatif) | Medium | ❌ Fail |
| TC-17 | Cart | Sepetten ürün silme | Medium | ✅ Pass |
| TC-18 | Checkout | Giriş yapmadan checkout | High | ✅ Pass |
| TC-19 | Checkout | Eksi tutarlı sepet ve geçersiz kartla ödeme (negatif) | Critical | ❌ Fail |
| TC-20 | Contact Us | İletişim formu gönderme (dosya ile) | Medium | ✅ Pass |
| TC-21 | Login | Silinmiş hesapla giriş denemesi (negatif) | High | ✅ Pass |
| TC-22 | Login | Şifre alanı boş bırakılarak giriş (negatif) | Medium | ✅ Pass |
| TC-23 | Checkout | Geçerli sepet ve kartla sipariş tamamlama | Critical | ⏳ Not Run |

---

## Signup

### TC-01 — Geçerli bilgilerle kayıt olma
- **Ön koşul:** Kullanıcı çıkış yapmış
- **Test verisi:** Ad: Hatice Pınar; daha önce kayıtlı olmayan bir e-posta
- **Adımlar:**
  1. Signup / Login'e tıkla
  2. Ad ve yeni e-postayı gir, Signup'a tıkla
  3. Tüm zorunlu alanları geçerli verilerle doldur
  4. Create Account'a tıkla
- **Beklenen sonuç:** 'ACCOUNT CREATED!' mesajı görünür; Continue sonrası 'Logged in as Hatice Pınar' yazar
- **Gerçek sonuç:** 'ACCOUNT CREATED!' mesajı göründü; Continue sonrası 'Logged in as Hatice Pınar' yazdı
- **Durum:** Pass | **Öncelik:** High | **Kanıt:** EK-03

### TC-02 — Kayıtlı e-posta ile tekrar kayıt
- **Ön koşul:** Hesap mevcut
- **Test verisi:** Ad: ayşe, E-posta: ayse123@gmail.com (kayıtlı)
- **Adımlar:**
  1. Signup / Login'e tıkla
  2. Kayıtlı e-posta ile Signup'a tıkla
- **Beklenen sonuç:** 'Email Address already exist!' hata mesajı
- **Gerçek sonuç:** 'Email Address already exist!' mesajı göründü
- **Durum:** Pass | **Öncelik:** High | **Kanıt:** EK-01

### TC-03 — Telefon alanına geçersiz değer
- **Ön koşul:** Signup formu açık
- **Test verisi:** Mobile Number: jashgdhjads (yalnızca harf)
- **Adımlar:**
  1. Mobile Number alanına harflerden oluşan değeri gir
  2. Diğer zorunlu alanları doldur
  3. Create Account'a tıkla
- **Beklenen sonuç:** Geçersiz telefon için uyarı verilmeli, kayıt engellenmeli
- **Gerçek sonuç:** Hesap oluşturuldu, uyarı verilmedi. Bkz. BUG-01
- **Durum:** Fail | **Öncelik:** Medium | **Kanıt:** EK-02, EK-03

### TC-04 — Adres alanlarına geçersiz format girme
- **Ön koşul:** Signup formu açık
- **Test verisi:** Address: istanbul, Country: India, State: 1234, City: 123, Zipcode: hsafgdh
- **Adımlar:**
  1. Address, State, City ve Zipcode alanlarına test verisini gir
  2. Country olarak India seç
  3. Diğer zorunlu alanları doldur, Create Account'a tıkla
- **Beklenen sonuç:** Zipcode, City ve State formatı doğrulanmalı, hata mesajı gösterilmeli
- **Gerçek sonuç:** Tüm değerler kabul edildi, hesap oluşturuldu. Bkz. BUG-03, BUG-04, UX-05
- **Durum:** Fail | **Öncelik:** Medium | **Kanıt:** EK-02, EK-03

### TC-05 — Zorunlu alanı (Password) boş bırakma
- **Ön koşul:** Signup formu açık
- **Test verisi:** Password: boş; diğer alanlar dolu
- **Adımlar:**
  1. Password alanını boş bırak
  2. Diğer zorunlu alanları doldur
  3. Create Account'a tıkla
- **Beklenen sonuç:** Alan zorunlu uyarısı görünür, kayıt oluşmaz
- **Gerçek sonuç:** Şifre alanında 'Lütfen bu alanı doldurun.' uyarısı çıktı, kayıt oluşmadı
- **Durum:** Pass | **Öncelik:** High | **Kanıt:** EK-28, EK-29, EK-30

---

## Login

### TC-06 — Doğru bilgilerle giriş
- **Ön koşul:** Kayıtlı hesap var, kullanıcı çıkış yapmış
- **Test verisi:** Kayıtlı test hesabının e-posta ve şifresi
- **Adımlar:**
  1. Signup / Login'e tıkla
  2. E-posta ve şifreyi gir
  3. Login'e tıkla
- **Beklenen sonuç:** Menüde 'Logged in as <ad>' görünür
- **Gerçek sonuç:** Giriş yapıldı; menüde 'Logged in as Hatice Pınar' görünüyor
- **Durum:** Pass | **Öncelik:** High | **Kanıt:** EK-13

### TC-07 — Yanlış şifre ile giriş
- **Ön koşul:** Kayıtlı hesap var
- **Test verisi:** Kayıtlı e-posta + yanlış şifre
- **Adımlar:**
  1. Doğru e-posta ve yanlış şifre gir
  2. Login'e tıkla
- **Beklenen sonuç:** 'Your email or password is incorrect!' mesajı, giriş yapılmaz
- **Gerçek sonuç:** 'Your email or password is incorrect!' mesajı çıktı, giriş yapılmadı
- **Durum:** Pass | **Öncelik:** High | **Kanıt:** EK-05

### TC-08 — Çıkış yapma (Logout)
- **Ön koşul:** Kullanıcı giriş yapmış
- **Adımlar:**
  1. Logout'a tıkla
- **Beklenen sonuç:** Login sayfasına yönlenir, menüde Signup / Login görünür
- **Gerçek sonuç:** Çıkış yapıldı, menüde Signup / Login göründü
- **Durum:** Pass | **Öncelik:** Medium | **Kanıt:** —

### TC-21 — Silinmiş hesapla giriş denemesi (negatif)
- **Ön koşul:** Hesap 'Delete Account' ile silinmiş
- **Test verisi:** Silinen hesabın e-posta ve şifresi (ayse123tf@gmail.com)
- **Adımlar:**
  1. Signup / Login'e tıkla
  2. Silinen hesabın e-posta ve şifresini gir
  3. Login'e tıkla
- **Beklenen sonuç:** Giriş yapılamamalı; hesabın varlığını ele vermeyen genel bir hata mesajı gösterilmeli
- **Gerçek sonuç:** 'Your email or password is incorrect!' mesajı göründü, giriş yapılamadı; mesaj hesabın silindiğini ele vermiyor
- **Durum:** Pass | **Öncelik:** High | **Kanıt:** EK-05

### TC-22 — Şifre alanı boş bırakılarak giriş (negatif)
- **Ön koşul:** Kullanıcı çıkış yapmış
- **Test verisi:** E-posta: ayse123tf@gmail.com, Şifre: boş
- **Adımlar:**
  1. Signup / Login'e tıkla
  2. Login bölümüne e-postayı gir, şifreyi boş bırak
  3. Login'e tıkla
- **Beklenen sonuç:** Giriş yapılmamalı, şifre alanı için zorunlu alan uyarısı gösterilmeli
- **Gerçek sonuç:** Şifre alanında 'Lütfen bu alanı doldurun.' uyarısı çıktı, giriş yapılmadı
- **Durum:** Pass | **Öncelik:** Medium | **Kanıt:** EK-27

---

## Products

### TC-09 — Tüm ürünleri listeleme
- **Adımlar:**
  1. Products menüsüne tıkla
- **Beklenen sonuç:** 'ALL PRODUCTS' sayfası ve ürün listesi görünür
- **Gerçek sonuç:** 'ALL PRODUCTS' başlığı ve ürün listesi göründü
- **Durum:** Pass | **Öncelik:** Medium | **Kanıt:** EK-07

### TC-10 — Ürün arama — geçerli kelime
- **Test verisi:** top
- **Adımlar:**
  1. Products sayfasına git
  2. Arama kutusuna 'top' yaz
  3. Büyüteç düğmesine tıkla
- **Beklenen sonuç:** 'SEARCHED PRODUCTS' altında ilgili ürünler listelenir
- **Gerçek sonuç:** Blue Top, Winter Top, Summer White Top listelendi. (Enter ile arama çalışmıyor → UX-06)
- **Durum:** Pass | **Öncelik:** High | **Kanıt:** EK-08

### TC-11 — Ürün arama — sonuçsuz kelime
- **Test verisi:** xvs
- **Adımlar:**
  1. Products sayfasına git
  2. Arama kutusuna 'xvs' yaz
  3. Büyüteç düğmesine tıkla
- **Beklenen sonuç:** 'Sonuç bulunamadı' benzeri bir bilgilendirme gösterilmeli
- **Gerçek sonuç:** 'SEARCHED PRODUCTS' başlığının altı tamamen boş, bilgilendirme mesajı yok. Bkz. UX-07
- **Durum:** Fail | **Öncelik:** Low | **Kanıt:** EK-09

### TC-12 — Kategori filtresi
- **Adımlar:**
  1. Sol menüden Women, Men ve Kids altındaki tüm alt kategorileri sırayla seç
- **Beklenen sonuç:** Her seçimde yalnızca ilgili kategorinin ürünleri ve doğru başlık görünür
- **Gerçek sonuç:** Tüm alt kategoriler doğru ürünleri listeledi
- **Durum:** Pass | **Öncelik:** Medium | **Kanıt:** —

### TC-13 — Ürün detay sayfası
- **Test verisi:** product_details/11 (Sleeves Printed Top - White)
- **Adımlar:**
  1. Ürünün 'View Product' linkine tıkla
- **Beklenen sonuç:** Ad, kategori, fiyat, stok durumu, ürün durumu ve marka görünür
- **Gerçek sonuç:** Category: Kids > Tops & Shirts, Rs. 499, Availability: In Stock, Condition: New, Brand: Babyhug görünüyor
- **Durum:** Pass | **Öncelik:** Medium | **Kanıt:** EK-10

---

## Cart

### TC-14 — Sepete ürün ekleme
- **Test verisi:** Blue Top (Rs. 500)
- **Adımlar:**
  1. Ürünün üzerindeki Add to cart'a tıkla
  2. View Cart'a tıkla
- **Beklenen sonuç:** Ürün sepette doğru fiyat ve miktarla görünür
- **Gerçek sonuç:** Quantity 1, Price Rs. 500, Total Rs. 500
- **Durum:** Pass | **Öncelik:** High | **Kanıt:** EK-20

### TC-15 — Ürün detayından miktar ile ekleme
- **Test verisi:** Men Tshirt (Rs. 400), Quantity: 5
- **Adımlar:**
  1. Ürün detayında Quantity'yi 5 yap
  2. Add to cart'a tıkla
  3. View Cart'a tıkla
- **Beklenen sonuç:** Sepette miktar 5, toplam = fiyat × 5 (Rs. 2000)
- **Gerçek sonuç:** Quantity 5, Total Rs. 2000
- **Durum:** Pass | **Öncelik:** High | **Kanıt:** EK-20

### TC-16 — Sepette geçersiz miktar (0 / negatif)
- **Ön koşul:** Giriş yapılmış, ürün detayı açık
- **Test verisi:** product_details/11 (Rs. 499); Quantity: 0 ve -1
- **Adımlar:**
  1. Quantity alanına 0 yaz, Add to cart'a tıkla
  2. Quantity alanına -1 yaz, Add to cart'a tıkla
  3. View Cart'a tıkla
- **Beklenen sonuç:** Geçersiz miktar engellenmeli, ürün sepete eklenmemeli
- **Gerçek sonuç:** Quantity=0 ile 'Added!' mesajı alındı; sepette 0 adet / Rs. 0 satırı oluştu ve Proceed To Checkout aktif. Quantity=-1 de kabul edildi; tekrarlı eklemelerle sepette -9 adet / Rs. -4491 oluştu. Bkz. BUG-05, BUG-07
- **Durum:** Fail | **Öncelik:** Medium | **Kanıt:** EK-11, EK-12, EK-13, EK-14, EK-15

### TC-17 — Sepetten ürün silme
- **Ön koşul:** Sepette ürün var
- **Adımlar:**
  1. View Cart'a tıkla
  2. Satırdaki X düğmesine tıkla
- **Beklenen sonuç:** Ürün sepetten kalkar; sepet boşsa bilgi mesajı görünür
- **Gerçek sonuç:** Ürün sepetten silindi. X düğmesi neredeyse şeffaf, zor fark ediliyor → UX-08
- **Durum:** Pass | **Öncelik:** Medium | **Kanıt:** EK-20

---

## Checkout

### TC-18 — Giriş yapmadan checkout
- **Ön koşul:** Kullanıcı çıkış yapmış
- **Adımlar:**
  1. Sepete ürün ekle
  2. View Cart'a tıkla
  3. Proceed To Checkout'a tıkla
- **Beklenen sonuç:** Register / Login yapılması istenir
- **Gerçek sonuç:** 'Register / Login account to proceed on checkout.' penceresi çıktı. (Not: çıkış yapınca sepet boşaldı, 'Cart is empty!' mesajı doğru gösterildi)
- **Durum:** Pass | **Öncelik:** High | **Kanıt:** EK-21, EK-22

### TC-19 — Eksi tutarlı sepet ve geçersiz kartla ödeme (negatif)
- **Ön koşul:** Giriş yapılmış, sepet toplamı Rs. -4491 (bkz. TC-16)
- **Test verisi:** Card Number: 4111111111111111111 (19 hane), CVC: 12, Expiration: 22 / 22
- **Adımlar:**
  1. Proceed To Checkout'a tıkla
  2. Place Order'a tıkla
  3. Kart bilgilerini gir, Pay and Confirm Order'a tıkla
- **Beklenen sonuç:** Eksi tutarlı sipariş ve geçersiz kart bilgileri reddedilmeli, hata mesajı gösterilmeli
- **Gerçek sonuç:** Ödeme kabul edildi ('Your order has been placed successfully!'); ardından payment_done/-4491 adresine yönlendirildi ve DEBUG=True ile Django 404 sayfası açıldı. Bkz. BUG-07, BUG-08, BUG-09, BUG-10
- **Durum:** Fail | **Öncelik:** Critical | **Kanıt:** EK-17, EK-18, EK-19

### TC-23 — Geçerli sepet ve kartla sipariş tamamlama
- **Ön koşul:** Giriş yapılmış, sepette geçerli miktarda ürün var
- **Test verisi:** Test kartı: 4111 1111 1111 1111, geçerli CVC (3 hane), ileri bir son kullanma tarihi
- **Adımlar:**
  1. Proceed To Checkout'a tıkla
  2. Adres ve sipariş özetini kontrol et
  3. Place Order'a tıkla
  4. Kart bilgilerini gir, Pay and Confirm Order'a tıkla
- **Beklenen sonuç:** 'ORDER PLACED!' mesajı görünür; teslimat adresi kayıttaki adresle aynıdır
- **Gerçek sonuç:** —
- **Durum:** Not Run | **Öncelik:** Critical | **Kanıt:** —

---

## Contact Us

### TC-20 — İletişim formu gönderme (dosya ile)
- **Test verisi:** Name, Email, Subject, Message dolu; ek dosya: .docx
- **Adımlar:**
  1. Contact us sayfasını aç
  2. Name, Email, Subject ve Message alanlarını doldur
  3. Dosya yükle
  4. Submit'e tıkla, açılan pencerede Tamam'a bas
- **Beklenen sonuç:** 'Success! Your details have been submitted successfully.' mesajı
- **Gerçek sonuç:** 'Press OK to proceed!' penceresi çıktı (bkz. UX-10); Tamam'a basınca başarı mesajı göründü
- **Durum:** Pass | **Öncelik:** Medium | **Kanıt:** EK-24, EK-25, EK-26
