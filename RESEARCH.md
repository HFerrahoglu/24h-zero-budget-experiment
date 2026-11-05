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

## 3. Aday problemler (Faz 1, 16:16-16:38)
Kaynak türleri (6): Reddit/HN/Indie Hackers (A), düşük puanlı ürün yorumları ve GitHub talepleri (B), freelance ilanları, Stack Overflow ve Türkçe forumlar (C), maker problemleri: HN Algolia, Gumroad, Chrome Web Store (D).
- Reddit doğrudan açılamadı (403). Bunu atlatmaya çalışmadık, Reddit kanıtı kullanılmadı.
- Her adayın en az 3 bağımsız kanıt linki, tarihi, alıntısı ve fiyat bilgisi ham raporlarda: [A](research/discovery_A_reddit_hn_ih.md), [B](research/discovery_B_reviews_github.md), [C](research/discovery_C_freelance_so_tr.md), [D](research/discovery_D_maker.md).
- Seçilen adayın kanıtlarını kendim de doğruladım (aşağıda §4.1).

| # | Problem (tek cümle) | Kim yaşıyor | Kanıt örneği (tamamı ham raporda) | Mevcut alternatif ve fiyat | Yeterli ücretsiz alternatif? |
|---|---|---|---|---|---|
| 1 | Stocky kapandı; PO/teslim alınan maldan toplu barkod etiketi basılamıyor | Shopify POS perakendecileri | community.shopify.com/t/622687, /638568, /669060, /587292 (8.639 görüntülenme) | Shopify Retail Barcode Labels (ücretsiz, 2.3★/476), FlochLabels $9.99-29.99/ay, FyreTrail $59/ay | Kısmen |
| 2 | Stocky sonrası barkodla mağaza sayımı ve envanter CSV'si | Shopify POS | /t/589370, /671985, /646221 | Binly ücretsiz ≤500 ürün, $12-25/ay | Kısmen |
| 3 | Satış hızına göre yeniden sipariş önerisi ve PO | Küçük Shopify mağazaları | /t/637085, /587141 (6.864 görüntülenme), /681984, /675803 | FyreTrail $59/ay, ERP $350-1k+/ay | Kısmen |
| 4 | Navlun ve gümrüğü kalemlere dağıtıp birim maliyet bulma | İthalatçı mağazalar | /t/661708, /650480, /709817 | Genel envanter uygulamaları, tablo | Kısmen |
| 5 | Shopify ürün CSV ön kontrolü ve onarımı | Taşınan mağazalar | /t/326225, /420339, /582662, /645056 | $19-25/dosya hizmetler, ücretsiz denetleyiciler | Evet'e yakın |
| 6 | Screen Studio tarzı zoom'lu demo videosu, aboneliksiz | Maker'lar | HN 47644600, 46995332, 44655022 | Screen Studio $29/ay (tek seferlik lisans kalktı) | **Evet** (OpenScreen MIT, Recordly, Cap) |
| 7 | .wpress yedeğini $69 ödemeden açma/geri yükleme | WordPress site sahipleri | wordpress.org 1★ yorumlar (2026), "$69 just to restore my own website" | ServMask Unlimited $69/yıl | Kısmen (yalnızca CLI) |
| 8 | Postman koleksiyonlarını .http/Bruno/Hurl'e çevirme | Geliştiriciler | Postman blogu + 3 HN başlığı (2026-03) | Bruno içe aktarma ücretsiz | Evet |
| 9 | Shopify Order Printer şablonu üretme | Shopify mağazaları | ham rapor B §5 | Template app şablon başı $29, 778 yorum | Kısmen |
| 10 | Binlerce .pub dosyasını toplu PDF'e çevirme | Publisher kullanıcıları | Microsoft Q&A ("over 2000 pub files") | MS betiği (Publisher kurulu olmalı) | Kısmen |
| 11 | e-Fatura/e-Arşiv XML'lerini toplu Excel'e çevirme (TR) | TR KOBİ ve muhasebe | R10 (2025-03), DonanımArşivi (~800 XML), eAsist | Dağınık, masaüstü araçlar | Kısmen |
| 12 | XRechnung/Peppol XML'lerini toplu CSV'ye çevirme | DE/BE KOBİ | ham rapor C §2 | Blink: 5 dosya ücretsiz, €12/ay | Kısmen |
| 13 | Tedarikçi Excel'ini Shopify CSV'sine çevirme | Mağazalar | ham rapor C §3 | Matrixify $20-200/ay (1.861 yorum), data.page $10/ay | Kısmen |
| 14 | Trendyol/Hepsiburada toplu kâr tablosu (TR) | TR pazaryeri satıcıları | ham rapor C §4 | Ücretsiz Excel ve hesaplayıcılar | Evet |
| 15 | Okul/hastane nöbet çizelgesi (TR) | Yöneticiler | ham rapor C §5 | NöbetPro ücretsiz | Evet |
| 16 | Takvim (.ics) etkinliklerinden saat raporu | Freelancer'lar | ham rapor C §6 (tek kanıt) | Calrows $6/ay | Kısmen |
| 17 | App Store/Play ekran görüntüsü üretimi | Indie uygulama geliştiricileri | HN 47917393, 47922553, 49525324 | AppScreens $99-180/yıl | **Evet** (UltraShot vb.) |
| 18 | Lansman dizini ve kanal listesi | Maker'lar | dev.to 2026-06 "half the links are dead" | $0+ listeler | Evet |
| 19 | **Lansmanda nereye, hangi kurallarla paylaşılır + gönderim kiti** | Ürününü yeni yayınlayan maker ve solo kurucular | HN 46676047, 43331842, 42943314; Gumroad $9.99 liste 276 satış | Listeler $0-9.99; autofill eklentileri (LaunchFill, Donkey Directories, Octane, SubmitIQ) ücretsiz ya da freemium | Kısmen (listeler var ama YZ ve yeni hesap kurallarını içermiyor) |
| 20 | Stripe/Gumroad CSV'sinden metrik paneli | Solo kurucular | HN 44895399, 41988511, 44989907 (zayıf) | Stripe paneli, ChartMogul | Muhtemelen evet |

## 4. Puanlama tablosu (Faz 2, 16:40)
Ölçek 1-5. Ulaşılabilirlik ×3 ağırlıklı, en yüksek toplam 50.
- **Ulaşılabilirlik** §2'ye göre puanlandı: yalnızca İngilizce maker sub'ları erişilebilir olduğu için mağaza sahipleri, TR KOBİ'leri ve WordPress kullanıcıları düşük puan aldı.
- **Yapılabilirlik** 2,5 saatlik inşa penceresine göre puanlandı.

| # | Aday | Acı | Ödeme kanıtı | Ulaşılabilirlik ×3 | Yapılabilirlik | Sıfır maliyet | Gumroad teslim | Ücretsiz alt. yokluğu | Düşük risk | **Toplam** |
|---|---|---|---|---|---|---|---|---|---|---|
| 19 | Lansman kanal kuralları + gönderim kiti | 3 | 4 | 5 (15) | 4 | 5 | 5 | 3 | 4 | **43** |
| 18 | Yalnızca lansman listesi | 3 | 4 | 5 (15) | 2 | 5 | 5 | 1 | 4 | 39 |
| 6 | Zoom'lu demo videosu | 3 | 4 | 4 (12) | 2 | 5 | 5 | 1 | 5 | 37 |
| 17 | Mağaza ekran görüntüsü | 3 | 4 | 4 (12) | 3 | 5 | 5 | 1 | 4 | 37 |
| 7 | .wpress açıcı | 5 | 5 | 2 (6) | 4 | 5 | 5 | 3 | 3 | 36 |
| 20 | Stripe CSV metrik | 2 | 1 | 4 (12) | 4 | 5 | 5 | 2 | 4 | 35 |
| 8 | Postman → Bruno | 2 | 1 | 3 (9) | 5 | 5 | 5 | 1 | 5 | 33 |
| 16 | .ics saat raporu | 2 | 2 | 2 (6) | 5 | 5 | 5 | 2 | 5 | 32 |
| 1 | Barkod etiketi (Stocky) | 4 | 4 | 1 (3) | 4 | 5 | 5 | 2 | 4 | 31 |
| 2 | Sayım (Stocky) | 4 | 3 | 1 (3) | 4 | 5 | 5 | 3 | 4 | 31 |
| 9 | Order Printer şablonu | 3 | 4 | 1 (3) | 4 | 5 | 5 | 3 | 4 | 31 |
| 11 | e-Fatura XML → Excel | 4 | 3 | 1 (3) | 5 | 5 | 4 | 3 | 4 | 31 |
| 13 | Tedarikçi CSV → Shopify | 3 | 5 | 1 (3) | 4 | 5 | 5 | 2 | 4 | 31 |
| 3 | Yeniden sipariş | 4 | 4 | 1 (3) | 3 | 5 | 5 | 2 | 4 | 30 |
| 4 | Birim maliyet dağıtımı | 3 | 3 | 1 (3) | 5 | 5 | 5 | 3 | 3 | 30 |
| 12 | XRechnung → CSV | 3 | 3 | 1 (3) | 4 | 5 | 5 | 3 | 4 | 30 |
| 5 | Shopify CSV ön kontrol | 3 | 3 | 1 (3) | 4 | 5 | 5 | 1 | 5 | 29 |
| 10 | .pub → PDF | 4 | 2 | 1 (3) | 1 | 5 | 5 | 2 | 4 | 26 |
| 15 | Nöbet çizelgesi | 4 | 2 | 1 (3) | 3 | 5 | 4 | 1 | 4 | 26 |
| 14 | Trendyol kâr tablosu | 3 | 2 | 1 (3) | 3 | 5 | 4 | 1 | 2 | 23 |

### 4.1 Seçim: #19, lansman kanal kuralları ve gönderim kiti
Seçilen adayın kanıtlarını kendim doğruladım (16:36-16:38):
- `[KANIT]` HN 46676047 (2026-01-19): "…digging up 5-year-old blog posts, and piecing together a messy spreadsheet of where to submit." https://news.ycombinator.com/item?id=46676047
- `[KANIT]` HN 43331842 (2025-03-11): "if I could pay 30 USD to have this done it'd be worth it" https://news.ycombinator.com/item?id=43331842
- `[KANIT]` HN 42943314 (2025-02-05): "Manually capturing these assets is tedious and time-consuming." https://news.ycombinator.com/item?id=42943314
- `[KANIT]` Gumroad "150+ Launch Platforms & Directories to Launch Your SaaS": `price_cents: 999`, `sales_count: 276`, 9 yorum, ort. 5.0 (sayfa JSON'u, curl). https://launchpedia.gumroad.com/l/list-my-saas
- `[KANIT]` Bu deneyin kendisi: Yeni hesapla nereye paylaşım yapılabileceğini bulmak 20 dakikalık çok kaynaklı bir araştırma gerektirdi. Sonuç çoğu kişinin tahmin edeceğinden çok farklı çıktı: HN ve PH yeni hesaba fiilen kapalı, çoğu büyük sub YZ metnini yasaklıyor (§2).

Neden bu `[ÇIKARIM]`:
1. **Ulaşılabilirlik:** Kurallara uyarak ulaşabildiğimiz tek kitle (r/SideProject ve benzerleri) tam olarak **şu anda lansman yapan** kişiler. Diğer adayların alıcıları bu kanallarda yok.
2. **Ödeme:** Bu kitle ~$10'luk lansman listelerine para ödüyor (276 satış).
3. **Ayırt edicilik:** Rakip listeler ve autofill eklentileri "nereye gönderilir" sorusuna cevap veriyor. Biz ise "gönderin kurallara takılır mı" sorusuna cevap veriyoruz: YZ metni yasağı, yeni hesap kapısı, kuyruk süresi, paylaşım günü, birincil ya da ikincil kaynak ve doğrulama tarihi. 2026'da çoğu maker lansman metnini YZ ile yazıyor `[ÇIKARIM]`, bu yüzden bu bilgi doğrudan "gönderim silindi" acısını önlüyor.

Elenenlerin ana nedenleri:
- **#1-5, 9, 13:** Güçlü sinyal (Stocky) ama alıcıların toplandığı Shopify Community YZ içeriğini yasaklıyor, başka bir kanalımız yok.
- **#11, 12, 14, 15:** TR ve DE kanalları kapalı.
- **#6, 17:** Yeterli ücretsiz ve açık kaynak alternatif var.
- **#7:** Acı çok güçlü ama alıcılar maker sub'larında değil, arama motorunda. SEO 24 saatte işlemez.
- **#8, 16, 20:** Ödeme kanıtı zayıf.
- **#10:** .pub formatı istemci tarafında çözülemez.

## 5. Şeytanın avukatı (#19)
1. **"Ücretsiz listeler ve autofill eklentileri zaten var (LaunchFill, Donkey Directories, Octane, SubmitIQ). Hiç tanınmayan bir satıcıdan kimse $7 vermez."**
   - Cevap: Çekirdek autofill değil, **kural verisi**. Rakipler dizin URL'si listeliyor; YZ metni politikası, hesap yaşı ve karma kapısı, paylaşım günü ve kuyruk süresini birincil kaynak alıntısı ve tarihle veren bir araç görmedik `[ÇIKARIM, sınırlı arama]`.
   - Ücretsiz sürüm en büyük kanalların kurallarını tamamen açık veriyor, değer ödemeden önce görülüyor. Ücretli sürüm kapsamı genişletiyor ve kiti ekliyor.
   - Kısmi risk kabul ediliyor.
2. **"Veri kısmen ikincil kaynaklı (rankhog gibi) ve kurallar değişir. Yanlış bilgi müşteriyi yakar."**
   - Cevap: Her satırda kaynak URL'si, kaynak türü (birincil/ikincil) ve doğrulama tarihi gösteriliyor. Operatörün bugün Reddit'te yaptığı birinci elden kontrol (Paket 2.2) veriye işlenecek.
   - Sayfada "veri 2026-11-05 itibarıyla, sonraki güncellemeler garanti edilmez" yazacak. Yanlış bilgi için koşulsuz iade var.
3. **"Kendi ürününü tanıtmak isteyen bir topluluğa tanıtım aracı satmak meta-spam gibi algılanır. Üstelik yeni Reddit hesabı filtreye takılabilir."**
   - Cevap: Paylaşım önce ücretsiz değeri veriyor. Temel bulgular tablosu gönderinin içinde, tıklamadan okunabiliyor. Deneyin hikâyesi şeffaf anlatılıyor, ürün isteğe bağlı.
   - Filtre riski kanal seviyesinde ve tüm adaylar için aynı. Fikre özgü değil. Her sub'a özgün metin yazılacak, paylaşımlar 60-90 dk arayla yapılacak.

Üç nedenin hepsine cevap verilebildi, bu yüzden #19 ile devam.

### 5.1 Deney sırasında görülen rakipler (19:27, Bluesky aramasından)
Kanıt düzeyi: Bluesky gönderilerinde gördük, sitelerin içini incelemedik.
- **postyourstartup.co/directories**: 135 dizini trafiğe göre sıralıyor (Bluesky, @timothybramlett, 5 gün önce). Bu liste bizim yanıtlamadığımız "hangi dizin gerçekten trafik getiriyor" sorusuna yanıt veriyor.
- **listaify.com**: YZ ürünleri için 1805 yer listeliyor, her birinin fiyatını gösteriyor (Bluesky, 1 gün önce).
- **Sonuç:** Şeytanın avukatı #1'deki risk güçlendi. Ücretsiz ve çok daha kapsamlı listeler var. Hâlâ görmediğimiz şey, yeni hesap ve YZ metni kurallarını kaynak alıntısıyla veren bir araç. Farkımız bu dar eksende kalıyor. Bunu bir talep kanıtı olarak değil, fiyat baskısı olarak okumak gerekiyor.
