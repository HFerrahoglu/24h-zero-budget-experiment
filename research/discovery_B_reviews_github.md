# Keşif B: Düşük puanlı yorumlar, "X'e alternatif" aramaları, GitHub istekleri

Tarih: 2026-11-05, ~16:20-17:15 TR. Kaynaklar: wordpress.org yorumları, Shopify App Store yorumları, Shopify Community (Discourse JSON), Microsoft Q&A, HN (Algolia API), Product Hunt, GitHub Search API.
Etiketler: [KANIT] = linki açıp doğruladım, [ÇIKARIM] = yorumum, [TAHMİN] = sayısal tahmin.

> **Koordinatörün kanal güncellemesine göre sıralama:** Kullanabildiğimiz kanallar yalnızca r/SideProject, r/indiehackers, r/alphaandbetausers, r/coolgithubprojects ve r/IMadeThis. Bu yüzden alıcısı indie maker, solo founder veya geliştirici olan adayları üste aldım. Sadece mağaza sahiplerine ya da ofis kullanıcılarına hitap eden adayların kanıtı güçlü olsa da puanını düşürdüm.

## Özet tablo

| # | Aday | Kanıt gücü | Kanal uyumu (maker alt-redditleri) | Build (1-5) | Not |
|---|---|---|---|---|---|
| 1 | Tarayıcıda "auto-zoom" demo/launch videosu (Screen Studio aboneliğine tek seferlik alternatif) | Güçlü | **Yüksek** | 3 | Maker'lar zaten para ödüyor ($29/ay) |
| 2 | .wpress yedeğini eklentisiz/ücretsiz açma + geri yükleme kiti | Çok güçlü | Orta | 4 | 2026'da sürekli 1 yıldızlı yorum, "$69 for restore" |
| 3 | Postman'den çıkış: koleksiyonu .http/Bruno formatına dönüştürme | Orta | Yüksek | 5 | Ücretsiz alternatifler bol, ödeme isteği düşük |
| 4 | Shopify barkod etiketi (Stocky kapandı, PO'dan etiket basılamıyor) | Çok güçlü (2026) | **Düşük** | 4 | Kalabalık uygulama pazarı |
| 5 | Shopify Order Printer fatura/irsaliye şablonu üretici (Liquid) | Güçlü (ödeme kanıtı) | **Düşük** | 4 | Kişiler şablon başına $29 ödüyor |
| 6 | Microsoft Publisher sonrası toplu .pub → PDF dönüştürme | Güçlü (zamanlama) | **Düşük** | 3 | Ofis/kurum kitlesi |

---

## 1) Tarayıcıda çalışan "auto-zoom" demo videosu yapıcı (Screen Studio benzeri, tek seferlik ödeme, Windows ve Linux'ta da çalışır)

- **Problem:** Indie maker'lar launch/demo videosu için zoom ve yumuşak kamera hareketi yapan araca ihtiyaç duyuyor. Pazarın standardı Screen Studio yalnızca Mac'te çalışıyor ve aylık $29 ya da yıllık planda ayda $9 istiyor.
- **Kimde var:** Show HN, Product Hunt veya r/SideProject'e launch videosu hazırlayan solo founder'lar ve geliştiriciler. Windows ve Linux kullanıcılarının neredeyse hiç seçeneği yok.
- **Kanıt:**
  - [KANIT] https://screen.studio/ (bugün açtım): fiyat "$29/mo." aylık, "$9/mo." yıllık. Sayfada "purchasing one-time licenses was possible in the past, but is no longer available for new purchases" yazıyor. FAQ'de ise "Currently, Screen Studio only supports macOS." Yani tek seferlik lisans kaldırılmış: klasik "abonelik tuzağı" deseni.
  - [KANIT] https://news.ycombinator.com/item?id=47644600 (colesantiago, 2026-04-04): "Screen Studio at $29/mo is unusually and extremely expensive for a video recorder app…"
  - [KANIT] https://news.ycombinator.com/item?id=46995332 (lenvl, 2026-02-12): "I have been using ScreenStudio to record cool demo videos for some time already, buying and cancelling my subscription, forgetting to cancel sometimes for months. Then I just got enough." Kişi kendi aracını yazmış.
  - [KANIT] https://news.ycombinator.com/item?id=44655022 (Jonovono, 2025-07-23): "The popular one is Screen Studio, but its a crazy subscription price. I made this with Focusee … one time price!"
  - [KANIT] https://news.ycombinator.com/item?id=47349188 (femtobusa, 2026-03-12): "Mac had Screen Studio, Windows had FocuSee but Linux had nothing." Kişi Screenix'i yazmış.
  - Karşı sinyal [KANIT] https://news.ycombinator.com/item?id=47647872 (canxerian, 2026-04-05): abonelik yenileme zamanı gelince cap.so ve screensage.pro'yu denemiş, "many bugs and UX oddities" yüzünden Screen Studio'ya geri dönmüş. Kalite çıtası yüksek.
- **Mevcut alternatifler ve fiyatlar:** Screen Studio aylık $29 ya da yıllık planda ayda $9, sadece Mac [KANIT]. FocuSee "one time price" (yorumdan, fiyatı doğrulamadım) [ÇIKARIM]. Cap, ScreenSage ve Screenix var; fiyatlarını doğrulamadım.
- **Yeterince iyi ücretsiz alternatif var mı?** **Kısmen.** Açık kaynak ve yeni rakipler çoğalıyor ama yukarıdaki yorumlarda hata ve UX şikâyeti var. Kurulum gerektirmeyen, tarayıcıda çalışan, Windows ve Linux'ta da kullanılabilen tek seferlik bir araç boşluğu hâlâ makul [ÇIKARIM].
- **Kitlenin toplandığı yer ve erişim:** r/SideProject ve r/indiehackers'taki herkes launch videosu yapıyor. Aracın kendi tanıtım videosunu araçla yapmak doğal bir demo olur [ÇIKARIM]. Kanal uyumu en yüksek aday bu.
- **Build: 3/5.** MVP: kullanıcı kaydını yükler ya da `getDisplayMedia` ile tarayıcıda kaydeder. Zaman çizelgesine tıklayarak zoom anahtar kareleri ekler (bölge + süre, ease-in-out). Arka plan dolgusu, yuvarlak köşe ve gölge eklenir. Çıktı canvas + MediaRecorder ile WebM olarak, varsa WebCodecs + mp4-muxer ile MP4 olarak alınır. Risk: tarayıcı, sekme dışındaki imleci takip edemez. Bu yüzden otomatik zoom yerine manuel ya da yarı otomatik anahtar kare gerekir. Bunu "Screen Studio kalitesi" diye değil, "60 saniyede launch videosu, tek seferlik $15" diye konumlamak gerekir [ÇIKARIM]. Ticari marka: ürün adında "Screen Studio" kullanılmamalı. Karşılaştırmada metin olarak anmak yeterli.

## 2) .wpress yedeğini eklentisiz açma ve geri yükleme kiti

- **Problem:** "All-in-One WP Migration" eklentisi yedeği ücretsiz alıyor, ama büyük yedeği geri yüklemek için $69/yıl tutan "Unlimited Extension" istiyor. Kullanıcı kendi verisini dışarı çıkaramıyor.
- **Kimde var:** WordPress site sahipleri, freelance web geliştiriciler, küçük ajanslar. Sıklıkla "sitem gitti, elimde sadece .wpress var" panik anındalar.
- **Kanıt (wordpress.org 1 yıldızlı yorumlar, hepsi açıldı):**
  - [KANIT] https://wordpress.org/support/topic/free-backups-paid-restores/ (hakuna4matata, 5 Ekim 2026): "You can create a backup for free. But to restore it from the plugin's backup list, you have to pay." Ayrıca "I bought the paid version because I was stuck and urgently needed the restore to work." **Ödemiş.**
  - [KANIT] https://wordpress.org/support/topic/free-backup-but-paid-restore-absolute-rip-off/ (dieterbitz, 13 Eylül 2026): 550 MB'lık yedeği geri yüklemek için ücretli sürüme "forced to upgrade" olmuş. "this is an absolute rip-off and highly misleading."
  - [KANIT] https://wordpress.org/support/topic/i-have-the-backup-but-no-use-my-site-is-gone/ (royalbluegraphics, Nisan 2026): "Now they're asking me to pay $69 just to restore my own website."
  - [KANIT] https://wordpress.org/support/topic/scamming-plugin-that-need-extansion-to-restore-files/ (paoloeuvrard, Mayıs 2026): "they keep your data hostage…" ve Unlimited Extension için 69 USD.
  - [KANIT] Yorum listesi https://wordpress.org/support/plugin/all-in-one-wp-migration/reviews/?filter=1 : son 12 ayda 30'dan fazla 1 yıldızlı yorum var, başlıklar "Useless without paying", "Inner file size limit…", "Exported, but will not import." gibi.
- **Mevcut alternatifler ve fiyatlar:** [KANIT] https://servmask.com/products/unlimited-extension sayfasında "$69/year". [KANIT] https://help.servmask.com/knowledgebase/archiver/ : ServMask'ın kendi "Traktor" sayfası var. Web'deki dosya tarayıcısı yalnızca içeriği listeliyor ("browse"). Ücretsiz CLI araçları da var: `wpress-extract` (npm/npx) ve Wpress-Extractor (exe). Bunlar arama sonuçlarında ve dev.to yazısında anılıyor [ÇIKARIM: repolarını tek tek açmadım].
- **Yeterince iyi ücretsiz alternatif var mı?** **Kısmen.** Ücretsiz CLI var, ama terminal bilmeyen, panik halindeki kullanıcıya uygun değil. SQL'deki `SERVMASK_PREFIX_` önekini düzeltmiyor, domain değiştirirken serialize veri güvenli search-replace sunmuyor, geri yükleme adımlarını da anlatmıyor [ÇIKARIM].
- **Kitlenin toplandığı yer ve erişim:** Gerçek alıcılar Google'da "restore wpress without extension" arıyor, wordpress.org forumunda ve r/Wordpress'te. Bu kanallar ya SEO gerektiriyor ya da kendi ürününü tanıtmayı yasaklıyor. r/coolgithubprojects ve r/SideProject'e açık kaynak "browser-based .wpress extractor" olarak girebilir. Ama 20 saatte satış için kanal uyumu orta [ÇIKARIM].
- **Build: 4/5.** MVP: .wpress dosyası sürüklenir. Format basit: dosya başına 4377 baytlık başlık (ad 255, boyut 14, mtime 12, yol 4096), sonra içerik [ÇIKARIM: bilinen format, kodla doğrulanmalı]. Tarayıcı dosyayı akış halinde okur ve ZIP'e (ya da File System Access API ile klasöre) çıkarır. `database.sql` içindeki önek `wp_` olur. Opsiyonel olarak serialize verinin uzunluğunu da düzelten eski domain → yeni domain dönüşümü yapılır. Ayrıca FTP + phpMyAdmin ile geri yükleme rehberi verilir. Ücretsiz sürüm sadece listeler, $9-12 tek seferlik ödeme tam çıkarma + SQL düzeltmesi açar. Ticari marka: "for .wpress files" ifadesi kullanılmalı, ServMask adı ve logosu kullanılmamalı.

## 3) Postman'den çıkış: koleksiyonları .http, Bruno ve Hurl formatına dönüştürme

- **Problem:** Postman, 1 Mart 2026'dan itibaren Free planı tek kişilik yaptı. Küçük ekipler ya ödeme yapacak ya da koleksiyonlarını başka araca taşıyacak.
- **Kimde var:** Küçük geliştirici ekipleri, solo geliştiriciler.
- **Kanıt:**
  - [KANIT] https://blog.postman.com/new-capabilities-march-2026/ : fiyatlandırma değişikliği "March 1, 2026" tarihinde yürürlüğe giriyor. Free plan "designed for individual developers" olarak tanımlanıyor.
  - [KANIT] https://news.ycombinator.com/item?id=46844880 (2026-02-01): "Postman to limit Free plan from 3 users to 1".
  - [KANIT] https://news.ycombinator.com/item?id=46942116 (2026-02-09, 16 puan): "ASK HN: Postman removes free team collaboration (small teams capped at 1 user)".
  - [KANIT] https://news.ycombinator.com/item?id=47144164 (Letmetest, 2026-02-24): "Got the email from Postman saying free plan is ending March 1. We're moving to Bruno for the time being."
  - [KANIT, GitHub] https://github.com/postmanlabs/postman-app-support/issues/11252 : "Export collections with WebSocket and gRPC requests". 193 👍, 2022'den beri açık. Postman içinden çözülmesi gerekiyor, dışarıdan bir araç çözemez [ÇIKARIM].
- **Mevcut alternatifler:** Bruno (taşıma sayfası usebruno.com/migrate, HN linkinde geçiyor), Hoppscotch, Kvile ve benzerleri. Bunların çoğu Postman içe aktarmayı zaten yapıyor [ÇIKARIM: importer'ları tek tek test etmedim].
- **Yeterince iyi ücretsiz alternatif var mı?** **Evet.** Hedef araçların kendi içe aktarıcıları var, ödeme isteği düşük [ÇIKARIM].
- **Kanal:** r/SideProject ve r/coolgithubprojects'e tam uyuyor. Ama ücretli satış zor, ücretsiz araç + "bağış/pro" modeli daha gerçekçi [ÇIKARIM].
- **Build: 5/5.** MVP: Postman v2.1 collection ve environment JSON'u yüklenir. Çıktı olarak klasör yapısını koruyan `.http` (VS Code/JetBrains), `.bru` ve Hurl dosyaları ZIP halinde iner. Script ve test kısımları yorum satırı olarak taşınır.

## 4) Shopify ürün barkod etiketi: Stocky kapandı, satın alma siparişinden (PO) etiket basılamıyor

- **Problem:** Shopify'ın ücretsiz Stocky uygulaması Ağustos 2026'da kapandı. Yeni yerel PO akışında "teslim alınan miktar kadar barkod etiketi bas" özelliği yok. Shopify'ın ücretsiz Retail Barcode Labels uygulaması ise etiket boyutu ve şablon konusunda katı.
- **Kimde var:** Fiziksel mağazası (POS) olan küçük ve orta Shopify perakendecileri.
- **Kanıt (Shopify Community, Discourse JSON ile okundu):**
  - [KANIT] https://community.shopify.com/t/print-barcode-labels-from-purchase-orders-anyone-else/638568 (Wildernest1, 2026-06-19; 14 gönderi, 514 görüntülenme): "Is anyone else interested in being able to print barcode labels natively within Shopify Purchase Orders?" MDS73 (2026-06-26): "Every merchant would love to print labels and barcodes directly from a PO, without making the same job twice."
  - [KANIT] https://community.shopify.com/t/feature-request-print-barcode-labels-directly-from-purchase-orders-like-stocky/622687 (CBHI, 2026-05-14). CoureurGoods (2026-08-31): "FyreTrail, a $150 dollar monthly add on app simply to do many of the things we were doing in Stocky, should not be the answer."
  - [KANIT] https://community.shopify.com/t/csv-download-from-the-new-pos-creation-replacing-stocky-it-was-a-quick-and-easy-way-to-create-barcoded-labels-for-all-received-stock-items/632194 (PBN1, 2026-06-10): "Stocky is currently the only quick way to create barcode labels for incoming stock for POS locations."
  - [KANIT] https://community.shopify.com/t/allow-barcode-label-printing-directly-from-a-purchase-order-or-transfer-number/669060 (ginger_1, 2026-08-20): "the Retail Barcode Labels app requires manually adding each product individually when printing labels."
  - [KANIT] Retail Barcode Labels 1-2 yıldızlı yorumlar https://apps.shopify.com/retail-barcode-labels/reviews?ratings%5B%5D=1 ve `?ratings%5B%5D=2`: Saratoga Chocolate Co. (2026-07-29) "removed our ability to print SKU on Avery 5167 labels". Random Acts Of Art (2025-10-29) "not customizable". Exodus Ride Shop (2025-10-23) Dymo'da barkodların okunmadığını yazıyor. Cavavin Ireland (2025-11-05) "there isn't a feature … to bulk upload the labels … via CSV."
- **Mevcut alternatifler ve fiyatlar:** [KANIT] Stockie Barcode Labels (https://apps.shopify.com/stockie-barcode-labels): $9.99, $29.99 ve $59.99/ay. [KANIT] LPP Label Printer Pro (https://apps.shopify.com/label-printer-pro): $9/ay. Çok sayıda yeni uygulama ayda 200 etiketlik ücretsiz katman sunuyor (thread'lerde FlochLabels, LabelLoom, LabelDock, LabelCraft, Replenly geçiyor).
- **Yeterince iyi ücretsiz alternatif var mı?** **Kısmen.** Ayda 200 etikete kadar ücretsiz katmanlar var. Pazar Temmuz-Eylül 2026'da geliştiricilerle doldu [KANIT: thread'lerdeki "Disclosure: I build…" gönderileri].
- **Kanal:** Alıcılar Shopify Community'de. Koordinatöre göre o kanal bize kapalı ve thread'ler zaten satıcı geliştiricilerle dolu. Maker alt-redditlerinde bu alıcı yok. **Kanal uyumu düşük** [ÇIKARIM].
- **Build: 4/5.** MVP: PO ya da ürün CSV'si yüklenir, miktar sütunu seçilir, etiket boyutu seçilir (Avery 5167, Dymo 30252, Zebra 2x1, vb.). Code128 ya da EAN13 (JsBarcode) basılır, eksik veya yinelenen barkod uyarısı verilir, PDF iner. Kurulum yok, API izni yok.

## 5) Shopify Order Printer için fatura/irsaliye şablonu üretici (görsel düzenleyici → Liquid kodu)

- **Problem:** Shopify'ın ücretsiz Order Printer uygulaması HTML, CSS ve Liquid bilmeden özelleştirilemiyor. Mağaza sahipleri hazır şablon için tek seferlik para ödüyor.
- **Kimde var:** Kod bilmeyen Shopify mağaza sahipleri.
- **Kanıt:**
  - [KANIT] https://apps.shopify.com/order-printer-templates : ilk şablon $29, sonrakiler $14, tek seferlik. 778 yorum, 4.9 puan. **Güçlü ödeme sinyali:** yüzlerce kişi tek seferlik şablon satın almış.
  - [KANIT] https://apps.shopify.com/shopify-order-printer/reviews?ratings%5B%5D=1 : Wicked Bride (2024-10-14) "my templates refused to print properly", destek ekibi geliştirici tutmasını önermiş. Sabaku Artwear (2026-01-30) "Still unusable two years later. Still will not import our template." Greenvill Crafts (2025-11-09) metafield'lerin düzenlenemediğini yazıyor. Toplam 171 tane 1 yıldızlı yorum.
  - [KANIT] Shopify Community 2025 başlıkları (search.json ile doğrulandı): "Centre logo on order printer template" (2025-02-05, /t/392354), "Order Printer: what is the code..." (2025-04-17, /t/409294), "Order Printer – How to display product barcode (EAN) on packing slip?" (2025-04-26, /t/410989). Hepsi farklı mağazalardan gelen basit Liquid soruları.
- **Mevcut alternatifler:** Order Printer Templates (yukarıda). Order Printer Pro ve Sufio gibi aylık ücretli uygulamalar da var [ÇIKARIM: fiyatlarını doğrulamadım].
- **Yeterince iyi ücretsiz alternatif var mı?** **Hayır/kısmen.** Shopify'ın varsayılan şablonları sade. Özelleştirmek için kod bilgisi gerekiyor.
- **Kanal:** Bu da merchant kitlesi, Shopify Community bize kapalı. **Kanal uyumu düşük** [ÇIKARIM].
- **Build: 4/5.** MVP: logo, renk, alan seçimi (SKU, barkod, not, vergi satırı) ve 4x6/A4/Letter seçimi yapılır. liquidjs ile örnek siparişte canlı önizleme gösterilir. Kullanıcı "Liquid kodunu kopyala" ile kodu Order Printer'a yapıştırır. Risk: Order Printer'ın değişken adlarını Shopify dokümanından doğru almak gerekiyor.

## 6) Microsoft Publisher bitti: binlerce .pub dosyasını toplu PDF/DOCX'e çevirme

- **Problem:** Publisher Ekim 2026'da emekliye ayrıldı. Kurumların elinde binlerce .pub dosyası kaldı. Microsoft'un PowerShell betiğini kurmak zor, üstelik Publisher'ın kurulu olmasını gerektiriyor.
- **Kimde var:** Okullar, kiliseler, dernekler, küçük ofisler.
- **Kanıt:**
  - [KANIT] https://learn.microsoft.com/en-us/answers/questions/5809729/help-converting-pub-files (2026-03-05): "I have over 2000 pub files - what app is easiest to use to batch convert". Takip mesajı: "No, I said easy!" Yanıtlarda farklı kullanıcılar betikte "term not recognized" hatası aldıklarını yazıyor. Biri ~2000 dosyayı makroyla ~3 saatte çevirmiş.
  - [KANIT] https://learn.microsoft.com/en-us/answers/questions/5780232/can-i-migrate-my-publisher-files-what-replaces-it (2026-02-18). Dmitry Romanovich (2026-03-18) "tens of thousands of files" diyor ve PDF'i bir taşıma yolu olarak kabul etmiyor.
  - [KANIT] https://www.convertapi.com/blog/microsoft-publisher-end-of-life : ücretli bulut API ile Publisher kurulu olmadan PUB → PDF dönüşümü. Ücretli bir çözüm mevcut.
- **Mevcut alternatifler:** Microsoft'un ücretsiz `Convert-PubFileToPDF.ps1` betiği (Publisher gerekir), ConvertAPI (ücretli, fiyatı doğrulanmadı) ve LibreOffice'in .pub açabilmesi [ÇIKARIM].
- **Yeterince iyi ücretsiz alternatif var mı?** **Kısmen.** Ücretsiz yollar var ama teknik. Düzenlenebilir DOCX'e kaliteli dönüşüm yok.
- **Kanal:** Alıcılar maker değil, ofis ve kurum kullanıcıları. **Kanal uyumu düşük.**
- **Build: 3/5.** İstemci tarafında .pub ayrıştırmak 2,5 saatte mümkün değil. Bunun yerine bir Windows betiği ya da küçük GUI yazılabilir: klasörü özyinelemeli tarar, Publisher kuruluysa COM ile, değilse LibreOffice headless ile çevirir, takılmaya karşı zaman aşımı koyar, klasör yapısını korur, başarısız dosyaları loglar. Ancak test için bu makinede Publisher ya da LibreOffice bulunması gerekir.

---

## Elenen veya zayıf kalan adaylar (kısa)

- **App Store ekran görüntüsü üretici:** Ödeme isteği var. Product Hunt'ta Launch Shots sayfasında maker $29/ay aboneliği eleştiriyor, Yitian Chen "Been hit by such expensive paywalls at the final moment multiple times" diyor (~11 ay önce) [KANIT: https://www.producthunt.com/products/launch-shots]. Ama tüm kanıt tek thread'den geliyor ve pazar çok kalabalık (FrameStudio, ListingShots, Screenies, AppMockUp ücretsiz…). Kanal uyumu yüksek olsa da kanıt standardını karşılamıyor.
- **Toplu sertifika üretimi (Canva Bulk Create'e alternatif):** Ücretsiz araçlar çok fazla (CertifyALot, Certifier ücretsiz katmanı, dev.to'da ücretsiz araçlar). Pazar doymuş.
- **Termal yazıcı için 4x6 kargo etiketi kırpma:** Çok sayıda ücretsiz tarayıcı aracı var (eLabelCropper, Label4x6, Relabely).
- **Trello'yu ücretsiz planda CSV/Excel'e aktarma:** Blue Cat "Exports for Trello" manuel dışa aktarmada ücretsiz. Sinyal zayıf.
- **Google Takeout fotoğraf metadata düzeltme:** Ücretli Mac uygulaması var ($9.99), ama ücretsiz CLI'lar bol ve konu kişisel fotoğraf/GPS verisi. Kısıtlara riskli.
- **GoFullPage (Chrome):** Görünen yorumlar olumlu, paywall şikâyeti bulamadım.
- **GitHub yolu (c):** En çok 👍 alan açık istekler (Claude Code, Codex, TypeScript, Godot, Typst, Streamlit) neredeyse hep ürünün kendi içinde çözülmesi gereken özellikler. Dışarıdan bağımsız bir araçla çözülebilecek ve ödeme sinyali taşıyan bir istek bulamadım. Postman #11252 (193 👍) da dışarıdan çözülemez.

## Not

- Reddit JSON'u 403 döndü, Shopify Community HTML'i 403 döndü. Shopify Community'yi Discourse `/t/<id>.json` ve `/search.json` uç noktalarıyla okudum. Hiçbir yere giriş yapmadım, kişisel veri toplamadım.
