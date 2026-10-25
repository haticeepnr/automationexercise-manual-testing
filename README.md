# automationexercise.com — Manuel Test Projesi

[automationexercise.com](https://automationexercise.com) e-ticaret demo sitesinin temel kullanıcı akışlarını manuel olarak test ettiğim portföy projesi.

**Hazırlayan:** Hatice Pınar | **Tarih:** Ekim 2026
**Ortam:** Chrome 155, Windows 11 (masaüstü 1920x1080)

## Sonuçlar

| Test case | Pass | Fail | Not Run | Bulgu (bug + UX) |
|-----------|------|------|---------|------------------|
| 23        | 17   | 5    | 1       | 20 (10 bug, 10 UX) |

**Öne çıkan bulgular:**
- **Negatif miktar kabul ediliyor:** Sepete -1 adet ürün eklenebiliyor ve sepet toplamı eksi tutara düşüyor (Critical). Jira: AE-1
- **Geçersiz kartla ödeme kabul ediliyor:** 19 haneli kart, 2 haneli CVC ve geçersiz tarihle sipariş tamamlanıyor (High). Jira: AE-2
- **DEBUG modu açık:** Eksi tutarlı ödeme sonrası açılan 404 sayfası sitenin tüm URL yapısını gösteriyor (bilgi ifşası).

## Kullanılan teknikler

- Senaryo bazlı manuel test, pozitif ve negatif test case'ler
- Sınır değer analizi ve eşdeğer bölümleme (form alanları, miktar alanı)
- Risk bazlı önceliklendirme (ödeme ve sepet akışları öncelikli)
- 2 adet 60 dakikalık exploratory session (CRUD, Goldilocks heuristic'leri)
- Bug raporlama: severity ve priority ayrımı, tekrar üretilebilir adımlar, ekran görüntüsü kanıtı
- Jira'da bug yaşam döngüsü (Scrum board, sprint, ilişkili ticket'lar)

## Test planı (özet)

**Kapsam:** Signup / Login / Logout / Delete Account, ürün listeleme, filtre ve arama, ürün detay, sepet, checkout ve ödeme (test verisiyle), Contact Us formu.

**Kapsam dışı:** Performans/yük testi, güvenlik (penetrasyon) testi, API testleri, gerçek ödeme, e-posta teslimatı, çapraz tarayıcı matrisi.

**Bu turda koşulmadı:** Footer abonelik (Subscription), mobil görünüm (375px), TC-23 (geçerli kartla sipariş tamamlama).

**Riskler:** Sitedeki tam ekran reklamlar test akışını kesebiliyor; demo site olduğu için veriler sıfırlanabilir.

## Bulgular

| ID | Başlık | Severity | Priority | Kanıt |
|----|--------|----------|----------|-------|
| BUG-01 | Mobile Number alanı geçersiz telefon numarasını kabul ediyor | Medium | High | EK-02, EK-03 |
| BUG-02 | Adres alanı eksik bilgiyle kabul ediliyor | Medium | High | — |
| BUG-03 | Zipcode alanı harf kabul ediyor | Medium | Medium | EK-02, EK-03 |
| BUG-04 | City ve State alanları yalnızca rakam kabul ediyor | Low | Medium | EK-02, EK-03 |
| BUG-05 | Quantity=0 ile ürün sepete 0 adet / Rs. 0 olarak ekleniyor | High | High | EK-11, EK-12, EK-13 |
| BUG-06 | Delete Account onay sormadan hesabı kalıcı olarak siliyor | High | High | EK-04 |
| BUG-07 | Negatif miktar kabul ediliyor; sepet toplamı eksiye düşüyor | Critical | High | EK-14, EK-15, EK-16 |
| BUG-08 | Ödeme formu geçersiz kart bilgilerini kabul ediyor | High | High | EK-17, EK-18 |
| BUG-09 | Eksi tutarlı ödeme sonrası onay sayfası 404 veriyor | High | High | EK-19 |
| BUG-10 | Canlı sitede Django DEBUG modu açık; URL yapısı ifşa oluyor | High | High | EK-19 |
| UX-01 | Footer abonelik metninde dil bilgisi hatası ("your self") | Low | Low | — |
| UX-02 | Telif hakkı yılı güncel değil (2021) | Low | Low | — |
| UX-03 | Contact Us sayfasında "for testing purpose" iç notu görünüyor | Low | Low | EK-24 |
| UX-04 | Tam sayfa reklam siteyi kullanılamaz hale getiriyor | Medium | Medium | EK-06 |
| UX-05 | Adres ile seçilen ülke arasında tutarlılık kontrolü yok | Low | Low | EK-02, EK-03 |
| UX-06 | Ürün aramada Enter tuşu çalışmıyor | Low | Medium | — |
| UX-07 | Sonuçsuz aramada kullanıcıya bilgi verilmiyor | Low | Medium | EK-09 |
| UX-08 | Sepetteki silme (X) düğmesi neredeyse görünmüyor | Medium | Medium | EK-13, EK-20 |
| UX-09 | Sepet sayfasında genel toplam gösterilmiyor | Low | Medium | EK-20 |
| UX-10 | İletişim formunda anlamsız onay penceresi ("Press OK to proceed!") | Low | Low | EK-25 |

## Jira

BUG-07 ve BUG-08 Jira'da bug ticket'ı olarak raporlandı ve birbirine bağlandı (ikisi birlikte eksi tutarlı sipariş oluşturulmasına yol açıyor).

![AE-1](jira/AE-1.png)
![AE-2](jira/AE-2.png)

## Klasörler

- [`test-cases.md`](test-cases.md) — 23 test case'in tamamı (adımlar, test verisi, beklenen/gerçek sonuç)
- [`evidence/`](evidence/) — ekran görüntüleri (EK-01 … EK-30)
- [`jira/`](jira/) — Jira ticket ekran görüntüleri

> Not: automationexercise.com test otomasyonu pratiği için hazırlanmış bir demo sitedir. Bulgular öğrenme ve portföy amacıyla raporlanmıştır.
