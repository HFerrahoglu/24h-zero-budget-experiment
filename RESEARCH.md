# RESEARCH — Bulgular, kanıtlar, puanlama

Etiketler: `[KANIT]` bağlantıyla doğrulanmış, `[ÇIKARIM]` benim yorumum, `[TAHMİN]` sayısal tahmin, `[DOĞRULANAMADI]`.

---

## 0. Araç envanteri (Faz 0, 16:03-16:15)

| Araç | Durum | Not |
|---|---|---|
| Web arama (WebSearch) | ✅ Çalışıyor | ABD merkezli sonuçlar |
| Sayfa çekme (WebFetch) | ✅ Çalışıyor | Yönlendirmeleri elle takip etmek gerekiyor. Bazı sayfalar içerik döndürmüyor, curl ile ham HTML alınabiliyor. |
| curl | ✅ | |
| git | ✅ 2.54 | Repo'ya özel commit e-postası: GitHub noreply |
| GitHub API | ✅ | `gh` CLI yok. GCM token'ı ile REST API kullanılıyor (yetkiler: repo, workflow, gist) |
| node / npm | ✅ 22.23 / 10.9 | |
| python | ✅ 3.13 | `python` komutuyla |
| GitHub Pages deploy | ⏳ Test ediliyor | Bkz. LOG |
| Tarayıcı (Claude in Chrome) | Mevcut, test edilmedi | Yalnızca okuma için. Hesap açma otomasyonu yok. |
| Gmail | ❌ Doğrudan erişim yok | Operatör iletecek |

## 1. Ödeme altyapısı

### 1.1 Ruul Space — KAPATILMIŞ `[KANIT]`
| Kontrol | Sonuç | Kaynak |
|---|---|---|
| ruul.space ana sayfası | "Ruul Space is no longer available. Visit ruul.io for more information." + noindex + ruul.io'ya yönlendirme | https://ruul.space/ (curl, 16:06) |
| Gerçek eski mağaza | Aynı mesaj | https://ruul.space/mavix (link kaynağı: https://www.threads.com/@mavix_xo/post/DQv5NYIkkkB) |
| "What is Ruul Space" destek makalesi | 301 → genel destek sayfası. Orada Space ile ilgili makale yok. | https://support.ruul.io/en/articles/11556960-what-is-ruul-space → https://ruul.io/support |
| Site haritası | Space veya dijital ürün sayfası yok | https://ruul.io/sitemap-0.xml (lastmod 2026-11-05) |
| Kapsam | "Only digital and knowledge-based services qualify". Ürün satışı ("product sales") hariç. | https://ruul.io/support/new-to-ruul/can-i-use-ruul |
| Müşteri | Şirket ülkesi ve adı isteniyor. Ödemeden önce şirket bilgisi istenebiliyor. | https://ruul.io/support/invoicing/how-to-add-and-manage-customers |
| Ödeme linki | Fatura başına, belirli bir müşteriye e-postayla gönderiliyor. Herkese açık link tanımlanmamış. | https://ruul.io/support/invoicing/how-invoicing-works-on-ruul |
| Komisyon | %5 (müşteriye yansıtılabiliyor). Kripto çekim +%1,5, Early Pay +%3,5. | https://ruul.io/support/new-to-ruul/fees-and-pricing-explained |
| Ödeme süresi | Ödeme sonrası genelde 1 iş günü | aynı |

Görev metninin istediği doğrulamalar (satın alma sonrası teslim, lisans anahtarı, iade, minimum fiyat, para birimi): Space kapalı olduğu için bunların hiçbiri Ruul'da artık **mevcut değil**. Faturada para birimi seçilebiliyor. İade süreci için Space'e özel bir makale yok `[DOĞRULANAMADI]`.

### 1.2 Önerilen alternatif: Gumroad (operatör onayı bekleniyor)
| Özellik | Değer | Kaynak |
|---|---|---|
| Ücret | Doğrudan satışta %10 + $0.50. Gumroad Discover üzerinden %30. | https://gumroad.com/pricing |
| Türkiye'ye ödeme | Banka, TRY ("Turkey — TRY") | https://github.com/antiwork/gumroad/blob/main/app/views/help_center/articles/contents/_13-getting-paid.html.erb |
| Asgari ödeme | $100. Satış başına 7 gün bekleme. Türkiye için ödeme günü çarşamba. | aynı |
| KYC | Stripe "belirli bir süre geçtikten ve satış biriktikten sonra" istiyor | aynı |
| Teslim | Dosya, link veya lisans anahtarı `[ÇIKARIM — yaygın bilgi, hesap açılınca doğrulanacak]` | — |
| Yeni hesapla ödeme bilgisi girmeden yayınlama | `[DOĞRULANAMADI]`, operatör kontrol edecek | — |

Fiyat hesabına örnek: $9'lık satışta Gumroad kesintisi 0,90 + 0,50 = $1,40, net $7,60 (%84). $5'lık satışta kesinti $1,00, net $4,00 (%80). $3'lık satışta net $2,20 (%73). Sabit $0,50 yüzünden çok düşük fiyat verimsiz.

## 2. Dağıtım kanalları — yeni hesap kuralları
*(Alt ajan araştırıyor. Gelince buraya işlenecek.)*

## 3. Aday problemler (Faz 1)
*(Henüz başlanmadı)*

## 4. Puanlama tablosu (Faz 2)
*(Henüz başlanmadı)*

## 5. Şeytanın avukatı
*(Henüz başlanmadı)*
