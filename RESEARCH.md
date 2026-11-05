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
| GitHub Pages deploy | ✅ Çalışıyor | API ile etkinleştirildi (main:/docs). İlk build 45 sn sürdü. https://hferrahoglu.github.io/24h-zero-budget-experiment/ → HTTP 200 (16:15) |
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

## 2. Dağıtım kanalları: yeni hesap ve YZ içerik kuralları (16:25)
Tam rapor, tüm alıntı ve linklerle: [research/distribution_channels.md](research/distribution_channels.md).

**İki eleme kriteri:**
1. YZ ile yazılmış metin yasağı. Tüm metinleri ben yazacağım ve operatör bunu açıkça belirtecek. İfşa, yasaktan muaf tutmuyor.
2. Yeni hesaba kapı (yaş, karma, bekleme süresi, inceleme kuyruğu).

| Kanal | Durum | Belirleyici kanıt |
|---|---|---|
| Hacker News | ❌ | "Please don't put generated text in HN posts" (https://news.ycombinator.com/newsguidelines.html). Show HN yeni hesaplara geçici olarak kapalı (https://news.ycombinator.com/showlim). |
| Product Hunt | ❌ | Ürün göndermek için 1 hafta bekleme (https://help.producthunt.com/en/articles/481909-how-can-i-get-access-to-post). YZ yorumları yasak. |
| Stack Overflow | ❌ | YZ içeriği yasak (https://stackoverflow.com/help/gen-ai-policy) |
| Shopify Community | ❌ | "AI-generated content is highly discouraged and will be removed". Tanıtım yalnızca Ask and Offer panosunda serbest (https://community.shopify.com/guidelines, 16:24'te curl ile okundu) |
| r/webdev, r/SaaS, r/Entrepreneur, r/InternetIsBeautiful | ❌ | YZ metni yasak. Ayrıca tanıtım yasağı, gün kısıtı ya da yaş kısıtı var (rankhog, ikincil kaynak) |
| r/selfhosted | ❌ | 90 günlük hesap gerekiyor, yeni projeler yalnızca Cuma (bugün Perşembe) |
| Dev.to | ❌ | YZ makaleye izin var ama kendi işini tanıtmak yasak (https://dev.to/guidelines-for-ai-assisted-articles-on-dev) |
| Mastodon (mastodon.social) | ⚠️ Kullanılmayacak | "Accounts may not solely post AI-generated content" (https://mastodon.social/api/v1/instance/rules). Yeni hesabımız yalnızca YZ taslaklı içerik paylaşacağı için kuralın ruhuna aykırı. |
| Dizinler (Uneed, Fazier, BetaList, AlternativeTo, SaaSHub) | ❌ | Kuyruklar haftalar sürüyor (Uneed ≥50 gün, Fazier ≤30 gün) |
| Launching Next | ⚠️ Yedek | Ücretsiz, "We review submissions every day", yayın garantisi yok |
| Ekşi Sözlük, R10, Technopat, Bionluk | ❌ | Çaylak entry'leri görünmüyor. R10 ticari konu için 1 ay üyelik + 5 itrader puanı istiyor. Technopat'ta reklam cezası var. Bionluk muhtemelen ücretli. |
| DonanımHaber | ⚠️ Yedek (TR) | SMS onayı, yeni üye mesajları onaya düşebilir. Kurallarda YZ maddesi yok. |
| **r/SideProject** | ✅ | Yazılı kural yok (Mart 2026 Wayback `rules.json` boş). YZ kuralı yok. |
| **r/indiehackers** | ✅ | Ürün başına 1 tanıtım, "Self Promotion" etiketiyle, geri bildirim amaçlı. YZ kuralı yok. |
| **r/alphaandbetausers** | ✅ | Kural yok. Başlıkta "[Web, Beta]" etiketi bekleniyor. E-posta duvarı olmamalı. |
| **r/coolgithubprojects** | ✅ | Kural yok. Proje GitHub'da barınmalı. |
| r/IMadeThis | ✅ (zayıf) | Kural yok, kitle küçük `[TAHMİN]` |
| GitHub (mevcut hesap, 13 takipçi) | ✅ (zayıf) | Repo kalıcı tanıtım sayfası işi görür. Başka projelerde tanıtım yasak (görev kuralı). |

**Sonuç `[ÇIKARIM]`:**
- Kurallara uyarak ulaşılabilir kitle **İngilizce konuşan maker, solo kurucu ve geliştirici kitlesi**, Reddit'teki 4-5 sub üzerinden.
- Türkçe kanallar 24 saat içinde fiilen kapalı. **Pazar kararı: global İngilizce** (LOG 16:28).
- En büyük bilinmeyen: Reddit'in yeni hesapları gizlice süzen filtresi (CQS/AutoModerator). Dışarıdan doğrulanamıyor.
- Her sub'a özgün metin yazılacak, paylaşımlar 60-90 dk arayla yapılacak.

**Saat dilimi:** Pencere 16:00-00:00 TR = 13:00-21:00 UTC = 08:00-16:00 ET. İlk paylaşım ne kadar erken olursa ABD gündüzünden o kadar çok pay alır. Hedef: ilk paylaşım ≤ 20:30 TR.

## 3. Aday problemler (Faz 1)
*(Henüz başlanmadı)*

## 4. Puanlama tablosu (Faz 2)
*(Henüz başlanmadı)*

## 5. Şeytanın avukatı
*(Henüz başlanmadı)*
