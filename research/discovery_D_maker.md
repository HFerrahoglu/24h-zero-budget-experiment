# Keşif D: İndie maker / solo founder problemleri (2026-11-05)

Yöntem: HN Algolia API (yorum/story metinleri ve yazar adları API'den tek tek doğrulandı), Gumroad ürün sayfalarının gömülü JSON'u (fiyat, satış, rating curl ile okundu), fiyat sayfaları WebFetch ile.
Etiketler: [KANIT] = açılıp doğrulandı, [ÇIKARIM] = kanıttan yorum, [TAHMİN] = doğrulanmadı.
Not: Süre 30 dk olduğu için 7 yerine 4 aday çıktı. Hepsinde en az 3 bağımsız yazar var. Elenen fikirler en altta.

---

## 1. Launch-directory "submission kit" + autofill bookmarklet  (EN GÜÇLÜ ADAY)

**Problem:** Her lansmanda onlarca directory sitesine (SaaSHub, BetaList, AlternativeTo vb.) aynı bilgileri (tagline, kısa/uzun açıklama, logo, ekran görüntüsü, kategori) tek tek kopyala-yapıştır yapmak ve nereye gönderdiğini takip etmek.
**Kim:** r/SideProject ve r/indiehackers'taki "ürünü yaptım, şimdi ne yapacağım" diyen solo founder'lar.

**Kanıt:**
- [KANIT] HN, 2026-01-19, krzysztofc: https://news.ycombinator.com/item?id=46676047. Alıntı: "Every time I launch a new product, I go through the same annoying routine: Googling 'SaaS directories,' digging up 5-year-old blog posts, and piecing together a messy spreadsheet of where to submit. It's frustrating and time-consuming." (Gönderide "reddit'te 500 upvote aldı" deniyor. Bunu doğrulayamadım, [TAHMİN]. Aynı metin 2025-07/08/12'de defalarca tekrar gönderilmiş, spam'a yakın.)
- [KANIT] HN, 2025-03-11, Alex-Programs, ListYour.app'in "Two sales in 24 hours" postu altında: https://news.ycombinator.com/item?id=43331842. Alıntı: "automatically submitting to directories (very useful; if I could pay 30 USD to have this done it'd be worth it)". Aynı yorum "I would never publish something LLM-generated" ve "the only directory anyone ever looks at is product hunt" da diyor. Bu ikisi önemli uyarı.
- [KANIT] HN, 2025-02-05, richard2wang: https://news.ycombinator.com/item?id=42943314. Alıntı: "When submitting product to directories ... you need screenshots, metadata, and content snippets for each site. Manually capturing these assets is tedious and time-consuming."
- [KANIT] Gumroad'da insanlar liste satın alıyor (sayfa JSON'undan okundu):
  - "list my saas" (launchpedia): **$9.99**, `sales_count: 276`, 9 rating, ort. 5.0. https://launchpedia.gumroad.com/l/list-my-saas
  - "75+ Places to launch your startup" (aynı satıcı): $0+ (kullanıcı ne isterse onu öder), `sales_count: 883`, 20 rating, ort. 4.9. https://launchpedia.gumroad.com/l/places-to-launch-your-startup
  - "SaaS Launch List": $0+, `sales_count: 382`, 4 rating. https://saasconsultsnr.gumroad.com/l/launchpad
  - "CosmoQuick LaunchStack, 400+ directories": $0+, 8 rating, ort. 5.0. https://cosmoquick.gumroad.com/l/launchstack

**Mevcut alternatifler:** Ücretsiz veya $0+ PDF/Notion listeler (yukarıda). GitHub'da awesome-saas-directories tipi listeler ve LaunchDirectories sitesi de var. Bunları arama sonucunda gördüm ama açıp doğrulamadım [TAHMİN]. Otomatik submission servisleri de var: ListYour.app (AI ile materyal üretip takip ediyor, fiyatını doğrulamadım).

**İyi bir ücretsiz alternatif var mı?** KISMEN. *Liste* tarafı tamamen metalaşmış, çoğu $0+, o yüzden liste satmak işe yaramaz. *Formu doldurma ve takip* tarafında, yani "bilgini bir kez gir, her directory formunda tek tıkla doldur, nereye gönderdiğini işaretle" işinde, ücretsiz ve istemci-taraflı iyi bir araç bulamadım [ÇIKARIM]. Tarayıcının kendi autofill'i bu alanları (tagline, uzun açıklama) doldurmuyor.

**Neden bu kitle önemser [ÇIKARIM]:** Ürünü yayınlayıp dağıtım arayan kişi tam olarak r/SideProject'te post atan kişi. Yorumlardaki "LLM ile üretilmiş metin istemem" itirazı, AI'sız ve kullanıcının kendi metnini kullanan bir aracı avantajlı kılıyor. $9.99'lık listenin 276 satışı, bu kitlenin ~$10 ödediğini gösteriyor.

**2 saatte yapılabilirlik: 4/5.**
**MVP:** Tek HTML sayfası. Profil formu (isim, URL, 60/160/500 karakterlik açıklamalar ve karakter sayacı, kategori, e-posta, sosyal linkler, logo) localStorage'a kaydedilir. Sayfa bu profili içeren kişisel bir **bookmarklet** üretir. Kullanıcı directory sitesindeyken tıklar, bookmarklet input'ları name/label/placeholder sezgisiyle eşleyip doldurur. Submit'e basmaz, kullanıcı basar (bot değil, ToS açısından güvenli). Yanında ~50 directory'lik bir takip listesi olur: durum (gönderildi/onaylandı/reddedildi), tarih, CSV export. Ayrıca "logo 256/512, ekran görüntüsü 1270x760" gibi boyutlarda istemci-taraflı canvas resize.
**Risk:** Directory listesini başkasının ücretli PDF'inden kopyalamamak lazım, kamuya açık bilgiden kendin derle. Bookmarklet bazı sitelerde (React kontrollü input'lar) doldurulan değeri tutmayabilir. Bunun için `input` event'i dispatch etmek gerekir.

---

## 2. App Store / Google Play ekran görüntüsü üreticisi (tek seferlik fiyat)

**Problem:** Yayın için her cihaz boyutu × her dil için çerçeveli, başlıklı store ekran görüntüleri üretmek.
**Kim:** Indie iOS/Android geliştiricileri.

**Kanıt:**
- [KANIT] HN, 2026-04-27, merelysounds: https://news.ycombinator.com/item?id=47917393. Alıntı: "generating N images for NUMBER_OF_SCREEN_SIZES times NUMBER_OF_LOCALIZATIONS can be a chore. In the past I wrote my own scripts for that".
- [KANIT] HN, 2026-04-27, Jonovono: https://news.ycombinator.com/item?id=47922553. Alıntı: "Making screenshots has always been my least favorite part of an app. I'd spend hours fiddling in Figma". (Aynı yazar 2026-08-03'te yine bunu söylüyor, 49156640. Bağımsız saymadım.)
- [KANIT] HN, 2026-09-01, elliotekj (UltraShot Show HN): https://news.ycombinator.com/item?id=49525324. Alıntı: "it's free so there's no need to pay monthly for something you need a few times a year ... I made it after trying a dozen different app store screenshot builders and finding each lacking". Bu "yılda birkaç kez lazım olan şeye abonelik" şikayetinin kanıtı.
- [KANIT] HN, 2025-01-27, fandorin: https://news.ycombinator.com/item?id=42842971. Alıntı: "what tool did you use to create app screenshots for AppStore?"
- [KANIT] Ücretli rakip AppScreens (https://appscreens.com/pricing): Free $0, Pro **$99/yıl**, Scale $180/yıl, tek seferlik seçenek yok. SSS'de: "For a single release, you can subscribe monthly and cancel the renewal". Yani tek seferlik iş aboneliğe çevrilmiş.

**Mevcut alternatifler:** AppScreens ($99/yıl, doğrulandı). AppLaunchpad (fiyat sayfası JS ile yükleniyor, doğrulayamadım). Ücretsiz olanlar: UltraShot (2026-09), AppShots CLI (HN 47178614, 2026-02), "simple tool" Show HN (46261934, 2025-12). Bunlara ek olarak AI tabanlı yeni girişler var.

**İyi bir ücretsiz alternatif var mı?** EVET, büyük ölçüde. UltraShot ücretsiz ve 3D cihaz render'ı var. 2025-26'da en az 4 yeni Show HN çıkmış, pazar kalabalık. Bu fikri en çok öldüren nokta bu.

**Neden bu kitle önemser [ÇIKARIM]:** r/SideProject'te mobil uygulama yayınlayanlar çok. Ama ücretsiz rakipler aynı subreddit'lere de post atıyor, $9'lık bir araç fark yaratmakta zorlanır.

**Yapılabilirlik: 3/5.**
**MVP:** Tek HTML. PNG yükle, başlık/alt başlık/gradyan arka plan seç, basit CSS/SVG cihaz çerçevesi koy. Apple ve Google'ın gerekli boyutlarının hepsini (6.9", 6.5", iPad 13", Play telefon ve feature graphic 1024x500) canvas'tan ZIP olarak export et (JSZip, CDN'den). Dil başına metni CSV'den alıp çoklu export yap. Bu sonuncusu ücretsizlerden ayıran tek özellik olabilir [TAHMİN].

---

## 3. Tarayıcıda "Screen Studio tarzı" demo video cilalayıcı

**Problem:** Lansman demo videosunu (zoom'lar, arka plan, köşe yuvarlama, padding) cilalamak için Screen Studio aylık $29 istiyor. Tek seferlik lisans artık satılmıyor.
**Kim:** Launch videosu çeken indie maker'lar.

**Kanıt:**
- [KANIT] Fiyat sayfası https://screen.studio/: Aylık **$29/mo**, yıllık $9/mo. Sayfada şu yazıyor: "purchasing one-time licenses was possible in the past, but is no longer available for new purchases."
- [KANIT] HN, 2026-04-04, colesantiago (OpenScreen tartışması): https://news.ycombinator.com/item?id=47644600. Alıntı: "Screen Studio at $29/mo is unusually and extremely expensive for a video recorder app".
- [KANIT] HN, 2026-02-12, lenvl: https://news.ycombinator.com/item?id=46995332. Alıntı: "I have been using ScreenStudio ... buying and cancelling my subscription, forgetting to cancel sometimes for months." (Kendisi tek seferlik bir alternatif yapmış.)
- [KANIT] HN, 2025-07-23, Jonovono: https://news.ycombinator.com/item?id=44655022. Alıntı: "The popular one is Screen Studio, but its a crazy subscription price ... Focusee ... one time price!"
- [KANIT] HN, 2026-04-04, Nevin1901: https://news.ycombinator.com/item?id=47644734. Alıntı: "Screen studio was unbelievably expensive for what it was".
- [KANIT] Karşı sinyal, HN 2026-04-05, canxerian: https://news.ycombinator.com/item?id=47647872. Cap ve ScreenSage'i denemiş, "many bugs and UX oddities" görüp Screen Studio'ya geri dönmüş. Kalite çıtası yüksek.

**Mevcut alternatifler:** Screen Studio ($29/ay veya $9/ay yıllık). FocuSee tek seferlik ödemeli (fiyatını doğrulamadım). OpenScreen açık kaynak (HN story 47595695, 2026-04). Cap açık kaynak.

**İyi bir ücretsiz alternatif var mı?** EVET/KISMEN. OpenScreen ve Cap ücretsiz ve açık kaynak, masaüstü uygulaması. Tarayıcıda çalışan, kurulum gerektirmeyen bir post-processor boşluğu olabilir [ÇIKARIM].

**Neden bu kitle önemser [ÇIKARIM]:** Lansman videosu r/SideProject postlarının standart parçası. Abonelik öfkesi güçlü ve tekrar eden bir duygu.

**Yapılabilirlik: 2/5.** Riskli. Yüklenen videoda imleç koordinatı olmadığı için otomatik "imleci takip eden zoom" yapılamaz, zoom keyframe'lerini kullanıcı elle tıklayarak koyar. Export `canvas.captureStream()` ve MediaRecorder ile WebM olur. Tarayıcıda MP4 desteği değişken [TAHMİN]. Gerçek zamanlı render yüzünden export, video süresi kadar sürer.
**MVP:** Video yükle. Arka plan gradyanı, padding, köşe yuvarlama ve gölge seç. Zaman çizelgesine tıklayıp zoom noktası ekle (ease-in/out). Sonucu WebM olarak indir.

---

## 4. Stripe / Gumroad / Lemon Squeezy CSV'sinden metrik paneli (istemci tarafında, gizlilik odaklı)  (ZAYIF)

**Problem:** Ödeme sağlayıcının panosu MRR, büyüme ve churn gibi derin metrikleri ücretsiz vermiyor. Baremetrics/ChartMogul gibi araçlar hesaba OAuth erişimi istiyor.
**Kim:** İlk gelirini alan solo founder'lar.

**Kanıt:**
- [KANIT] HN, 2025-08-14, warpbin (Show HN, istemci tarafında çalışan Stripe aracı): https://news.ycombinator.com/item?id=44895399. Alıntı: "One thing I felt lacking about Stripe was just the ability to dig deeper into the stats and get more insights (at least without the paid reporting add-on they have)". Aynı yazar 2025-05-09'da 43939900'ı da yazmış, bağımsız değil. Show HN 1 puan almış, ilgi zayıf.
- [KANIT] HN, 2024-10-29, ghazalidotdev: https://news.ycombinator.com/item?id=41988511. MRRTracker: "a macOS toolbar app to track MRR easily, without needing to open Stripe's dashboard every time", Product Hunt'ta #4 olmuş. 2024 tarihli, yani eski.
- [KANIT] HN, 2025-08-22: https://news.ycombinator.com/item?id=44989907. Alıntı: "Imagine the stripe dashboard MRR, today's revenue, failed charges". Bu dolaylı bir talep.

**Mevcut alternatifler:** Baremetrics (fiyat sayfası açılmadı, doğrulanamadı). ChartMogul'un ücretsiz katmanı olduğunu düşünüyorum [TAHMİN]. Stripe Billing panelinde MRR gösteriliyor [TAHMİN].

**İyi bir ücretsiz alternatif var mı?** EVET, büyük ihtimalle (Stripe'ın kendi paneli ve ChartMogul'un ücretsiz katmanı) [TAHMİN]. Doğrudan "bunun için para öderim" sinyali bulamadım.

**Neden bu kitle önemser [ÇIKARIM]:** "Build in public" yapanlar gelir ekran görüntüsü paylaşıyor. Gumroad ve Lemon CSV'si için hazır panel yokluğu niş bir boşluk olabilir. Kanıt zayıf.

**Yapılabilirlik: 4/5.**
**MVP:** CSV'yi sürükle bırak, PapaParse ile oku, sağlayıcıyı başlıklardan otomatik tanı. Aylık gelir, MRR yaklaşımı, iade oranı, en iyi ürün/ülke grafikleri göster (Chart.js). "Build in public" için paylaşılabilir PNG kart üret. Veri cihazdan çıkmaz.

---

## Elenenler (kısa)
- **Fatura üretici (freelancer):** invoice-generator.com tipi çok sayıda ücretsiz araç var. Ücretsiz alternatif EVET, o yüzden elendi [ÇIKARIM].
- **OG image / screenshot beautifier:** Ücretsiz araç bol (HN'de 2025-06 "I made a screenshot beautifier" Show HN'i). HN'de bunun için ödeme sinyali bulamadım.
- **Testimonial wall / changelog widget:** Senja ve Testimonial.to aboneliklerinden bahsedilen bir yorum var (HN 47773910), ama "çok pahalı" şikayeti 3 bağımsız kaynağa ulaşmadı. Çoğu backend de gerektiriyor.
- **Liste satmak (directory PDF):** Gumroad'da $0+ fiyatlı ve 883 satışlı ücretsiz eşdeğerler var. Sadece liste satmak işe yaramaz. Değer araçta (Aday 1).

## Sıralama önerisi [ÇIKARIM]
1. **Aday 1 (directory kit + bookmarklet).** Aynı kitlede gerçek ödeme kanıtı var ($9.99 × 276 satış), açık bir "$30 öderim" yorumu var, ücretsiz rakibi zayıf, 2 saatte yapılabilir. r/SideProject'te "dağıtım için yaptığım araç" anlatısı doğal duruyor. GitHub'a koyulursa r/coolgithubprojects'e de uyar.
2. **Aday 2.** Ödeme kanıtı güçlü ama ücretsiz rakipler bol.
3. **Aday 3.** Abonelik öfkesi en güçlüsü ama 2 saatte yapmak riskli.
4. **Aday 4.** Kanıt zayıf.
