# Keşif A: Reddit / HN / Indie Hackers (2026-11-05)

## Yöntem ve sınırlar (önce okuyun)
- [KANIT] Reddit'e erişilemedi. `reddit.com/*.json`, `api.reddit.com` ve WebFetch 403 döndü. Ayna site (redlib) denemesi izin sistemi tarafından "bot check circumvention" gerekçesiyle reddedildi, ben de zorlamadım. Bu yüzden raporda **hiç Reddit linki yok**. Açıp doğrulayamadığım linkleri talimata uyarak attım.
- [KANIT] HN Algolia API çalıştı. Ama Ask HN'deki "is there a tool / I'd pay" aramaları çoğunlukla geliştirici ve yapay zekâ konularıyla ilgiliydi, küçük işletme acısı neredeyse hiç çıkmadı. İşe yarayan tek HN bulgusu QR konusu (elenenler bölümünde).
- [KANIT] Asıl verimli kaynak **Shopify Community** oldu. Discourse tabanlı olduğu için `/t/<id>.json` ve `/search.json` ile her başlık açılıp tarih ve alıntı doğrulandı. Aşağıdaki tüm linkler bu şekilde açıldı.
- [ÇIKARIM] Sonuçta en güçlü sinyaller tek bir olaya toplandı: **Shopify, ücretsiz envanter uygulaması Stocky'yi 31 Ağustos 2026'da kapattı.** Mağazalar POS Pro paketinin içinde ücretsiz gelen satın alma siparişi (PO), etiket, sayım, yeniden sipariş ve maliyet özelliklerini kaybetti. Bu yüzden 5 adayın 5'i de aynı kitleye hitap ediyor. Bunları ayrı ayrı satmak yerine tek bir "Stocky boşluğu kiti" olarak paketlemek de mümkün.
- [KANIT] Zamanlama avantajı var. Başlık adlarına göre Stocky'nin salt okunur dışa aktarma süresi ~29 Kasım'da bitiyor: "Stocky's read-only window closes around the end of November" (2026-09-26) https://community.shopify.com/t/687775 ve "Stocky's export window closes ~Nov 29" (2026-10-16) https://community.shopify.com/t/699126 . İkisinde de yalnızca başlığı gördüm, gövdeyi okumadım.
- [KANIT] Rekabet yoğun. Shopify Community'de 2026'da onlarca "Stocky alternatifi yaptım" tanıtım gönderisi var (ör. 674679, 673381, 660233, 699293). Yani bu kitleye yeni hesapla tanıtım yapmak orada olağan. Öte yandan sesinizi duyurmak zor.

---

## Aday 1: Satın alma siparişinden / teslim alınan maldan toplu barkod etiketi basma (Stocky sonrası)
**Problem:** Mağaza mal teslim alınca, gelen her ürün için doğru adette barkod veya fiyat etiketini tek seferde basamıyor. Stocky bunu yapıyordu, yerine gelen Shopify PO ekranı yapmıyor.

**Kimde var:** Shopify POS kullanan fiziksel perakendeciler (butik, hediyelik, kitap/medya, giyim). Dymo, Zebra, Brother QL ya da Avery A4/Letter etiket kâğıdı kullanıyorlar.

**Kanıtlar:**
- [KANIT] 2026-05-14 · "Feature Request: Print Barcode Labels Directly from Purchase Orders (like Stocky)". Alıntı: "Without it, you have to cross-reference the PO manually and print labels separately, which adds significant time to the receiving workflow." (657 görüntülenme, 14 gönderi) https://community.shopify.com/t/feature-request-print-barcode-labels-directly-from-purchase-orders-like-stocky/622687
- [KANIT] 2026-06-19 · "Print Barcode Labels from Purchase Orders - Anyone else?". Bir yanıttaki alıntı: "Every merchant would love to print labels and barcodes directly from a PO, without making the same job twice." (514 görüntülenme) https://community.shopify.com/t/print-barcode-labels-from-purchase-orders-anyone-else/638568
- [KANIT] 2026-08-20 · "Allow barcode label printing directly from a Purchase Order or Transfer number". Alıntı: "the Retail Barcode Labels app requires manually adding each product individually when printing labels — even after you've already received inventory" https://community.shopify.com/t/allow-barcode-label-printing-directly-from-a-purchase-order-or-transfer-number/669060
- [KANIT] 2026-06-10 · "Csv download from the new PO's creation…". Alıntı: "Stocky is currently the only quick way to create barcode labels for incoming stock for POS locations." https://community.shopify.com/t/csv-download-from-the-new-pos-creation-replacing-stocky-it-was-a-quick-and-easy-way-to-create-barcoded-labels-for-all-received-stock-items/632194
- [KANIT] 2026-02-04 · "Stocky App Going Away after August 31 2026". Kaybedilenler arasında sayılıyor: "print price labels directly from the PO for what was received". (8.639 görüntülenme, 153 gönderi) https://community.shopify.com/t/stocky-app-going-away-after-august-31-2026/587292

**Mevcut alternatifler ve fiyatlar:**
- [KANIT] Shopify'ın kendi "Retail Barcode Labels" uygulaması ücretsiz, ama puanı **2.3/5 (476 yorum)**. Ürünler tek tek ekleniyor. https://apps.shopify.com/retail-barcode-labels
- [KANIT] FlochLabels: 200 etiket/ay ücretsiz, Pro $9.99/ay, Unlimited $29.99/ay. https://apps.shopify.com/flochlabels
- [KANIT] FyreTrail: ücretsiz plan var, PO'dan etiket basma Starter planında, $59/ay. https://apps.shopify.com/fyretrail
- [KANIT] LabelCraft: ilgili başlıkta (632194) "Free up to 200 labels a month" diye tanıtılıyor.

**Yeterince iyi ücretsiz alternatif var mı?** KISMEN. [ÇIKARIM] Ücretsiz katmanlar aylık 200 etiketle sınırlı ve hepsi abonelik. Resmi ücretsiz uygulama ise düşük puanlı ve elle çalışıyor. Düzenli mal kabulü yapan bir mağaza 200 etiketi hızla aşar. "Bir kez $15–19 öde, sınırsız bas, veri tarayıcıdan çıkmasın" diye konumlanacak bir ürünün yeri var.

**Nerede toplanıyorlar / yeni hesapla ulaşılır mı?** [ÇIKARIM] Shopify Community'nin "Shopify Discussion" ve "Inventory/POS" bölümleri. Yukarıdaki başlıklara geliştiricilerin "Disclosure: I build X" diye yazdığı çok örnek var, yani açıkça belirtilen tanıtım fiilen kabul görüyor. Ek kanallar r/shopify ve r/smallbusiness. Bunların kurallarını Reddit'e erişemediğim için doğrulayamadım.

**Yapılabilirlik:** 5/5. [ÇIKARIM] MVP şöyle olur: Shopify ürün veya envanter CSV'si, ya da PO satırlarını içeren CSV/yapıştırılmış SKU listesi yüklenir. Adetler düzenlenir. Şablon seçilir: Avery 5160/L7160, Dymo 30252, Zebra 2x1", Brother 62 mm. JsBarcode ile EAN-13/Code128 üretilir (eksik barkod için geçerli EAN-13 oluşturulur). Fiyat, ad ve varyant alanları eklenir. Çıktı yazdırılabilir HTML/PDF olur. Tamamen istemci tarafında çalışır.

---

## Aday 2: Barkod okuyucuyla mağaza sayımı (stocktake/cycle count) → Shopify envanter CSV
**Problem:** Stocky'nin ücretsiz yıl sonu ve dönemsel sayım özelliği gitti. Shopify'ın yerine koyduğu çözümde sayılmamış ürünleri göstermek ve farkları onaylayıp toplu güncellemek gibi temel işlevler eksik.

**Kimde var:** Shopify POS perakendecileri. Muhasebe ya da yıl sonu sayımı yapması gereken küçük mağazalar.

**Kanıtlar:**
- [KANIT] 2026-02-23 · "Feature Request - Add 'Missed Products' View to Quick Count for Stock Takes". Alıntı: "shows all products at the selected location that haven't been scanned or counted during the current stock take session … With Stocky being discontinued" (361 görüntülenme) https://community.shopify.com/t/feature-request-add-missed-products-view-to-quick-count-for-stock-takes/589370
- [KANIT] 2026-08-24 · "How are you handling period Inventory Cycle Counts for your stores?". Bir yanıttaki alıntı: "That is what most POS Pro shops were using for stocktakes and it came free with the plan" https://community.shopify.com/t/how-are-you-handling-period-inventory-cycle-counts-for-your-stores/671985
- [KANIT] 2026-07-07 · "Replacement for Stocky?" OP'nin istekleri: "Stocktakes at year end. Reports of my inventory?" ve "$59/month is a large charge when every app costs you money and stocky was free that I have used for 6 years." (2.566 görüntülenme, 75 gönderi) https://community.shopify.com/t/replacement-for-stocky/646221
- [KANIT] 2026-02-04 · 587292 numaralı başlıkta kaybedilenler arasında: "completing our whole store inventory via barcode scanning" (link Aday 1'de).

**Mevcut alternatifler ve fiyatlar:**
- [KANIT] Binly: 500 ürüne kadar ücretsiz ("Barcode stocktakes, one phone per count"), Starter $12/ay, Pro $25/ay. https://apps.shopify.com/binly
- [KANIT] FyreTrail Starter $59/ay (yukarıda).
- [KANIT] Shopify Quick Count POS eklentisi var, ama 589370'te eksik özellik şikâyeti yapılıyor.

**Yeterince iyi ücretsiz alternatif var mı?** KISMEN. [ÇIKARIM] 500 üründen küçük mağazalar için Binly'nin ücretsiz katmanı yeterli olabilir. Daha büyük katalogda abonelik gerekiyor. Yılda 1–4 kez sayım yapan biri için aylık ücret anlamsız, tek seferlik satın alma burada güçlü bir argüman.

**Nerede toplanıyorlar / yeni hesapla ulaşılır mı?** [ÇIKARIM] Aday 1 ile aynı kitle ve kanallar.

**Yapılabilirlik:** 4/5. [ÇIKARIM] MVP şöyle olur: Shopify "Inventory" CSV dışa aktarımı yüklenir. Tarayıcıda USB/Bluetooth barkod okuyucu klavye gibi davrandığı için okutulan her ürün sayılır. Sayılmayan ürünler listelenir, farklar tablosu gösterilir. Sonuç Shopify'ın envanter içe aktarma formatında CSV olarak dışa verilir. Oturum localStorage'da tutulur. Shopify envanter CSV'sinin tam kolon formatını (ör. "On hand (new)") inşa sırasında Shopify yardım sayfasından doğrulamak gerekiyor. Eş zamanlı satış düzeltmesi MVP'de olmaz.

---

## Aday 3: Satış CSV'sinden "ne sipariş etmeliyim" önerisi + tedarikçi PO çıktısı
**Problem:** Shopify'ın yeni PO ekranında satış hızına ve tedarik süresine göre yeniden sipariş önerisi yok. Küçük mağazalar bunu karmaşık tablolarla elle hesaplıyor ya da ERP veya $59+/ay uygulamalara itiliyor.

**Kimde var:** Tedarikçiden düzenli stok alan küçük Shopify mağazaları, hem online hem POS.

**Kanıtlar:**
- [KANIT] 2026-06-15 · "Stocky shuts down in August. What are you actually moving to for reorder/POs?" Alıntı: "the native replacement drops the parts I cared about most, reorder suggestions and purchase orders … The bigger paid apps and ERPs feel like overkill and got expensive … if a simple tool did just the reorder suggestions plus an exportable PO" (2.881 görüntülenme, 79 gönderi) https://community.shopify.com/t/stocky-shuts-down-in-august-what-are-you-actually-moving-to-for-reorder-pos/637085
- [KANIT] 2026-02-03 · "Replacement to Stocky?" Alıntı: "the only way to have something even remotely close to Stocky is to go pay for an ERP … Shelling out another $350-1k+/mo" (6.864 görüntülenme, 83 gönderi) https://community.shopify.com/t/replacement-to-stocky/587141
- [KANIT] 2026-09-15 · "How are you guys handling inventory reorders?" Alıntı: "once you have a lot of products it gets pretty messy doing all of that manually in a spreadsheet" https://community.shopify.com/t/how-are-you-guys-handling-inventory-reorders/681984
- [KANIT] 2026-09-02 · "How are you handling supplier lead times and reorder triggers post-Stocky?" Alıntı: "Native Shopify handles basic PO creation, but it completely leaves out the calculation side—specifically mapping out 30-day sales velocity against actual supplier lead times" (655 görüntülenme, 28 gönderi) https://community.shopify.com/t/how-are-you-handling-supplier-lead-times-and-reorder-triggers-post-stocky/675803
- [KANIT] 2026-07-07 · 646221'de OP: "I'm not paying a thousand dollars a year for an app that I had for free for years." (link Aday 2'de)

**Mevcut alternatifler ve fiyatlar:**
- [KANIT] FyreTrail Starter $59/ay.
- [KANIT] Binly'de PO ve tedarikçi özellikleri Starter planda, $12/ay.
- [KANIT] Thread başlıklarında "Replenly - free Stocky alternative … (paid plans from $19)" (674679) ve "Inmana Restock … a $19 Stocky alternative" (673381) geçiyor. Bunların yalnızca başlığını gördüm. 646221'de ChannelBay için "This App free" deniyor.

**Yeterince iyi ücretsiz alternatif var mı?** KISMEN. [ÇIKARIM] Ücretsiz uygulamalar var ama yeni ve az yorumlu. Tüccarlar uygulama ve abonelik yorgunluğundan açıkça şikâyetçi. Bir yorumda geçici çözüm olarak "Google Sheets with formulas for reorder points" öneriliyor. Bunun yerine geçecek hazır bir araç makul bir fırsat. Yine de rekabet en yoğun alan bu.

**Nerede toplanıyorlar / yeni hesapla ulaşılır mı?** [ÇIKARIM] Aynı kanallar.

**Yapılabilirlik:** 4/5. [ÇIKARIM] MVP şöyle olur: Shopify "Sales by product variant" raporu CSV'si ile envanter CSV'si yüklenir. Kullanıcı tedarikçi tedarik süresini ve güvenlik gününü girer. Araç günlük satış hızını hesaplar; stokta sıfır olunan günler hariç tutulabilir, 675803'teki uyarıya göre. Ardından kaç gün stok kaldığını ve önerilen adedi çıkarır. Sonuç tedarikçiye göre gruplanır, yazdırılabilir PO ve CSV olarak dışa verilir. Matematik basit, işin çoğu CSV kolon eşleme.

---

## Aday 4: Navlun, gümrük ve indirimleri PO kalemlerine dağıtıp birim maliyeti bulmak ("Cost per item" CSV)
**Problem:** İthal mal alan mağaza navlun, gümrük vergisi ve erken ödeme indirimini ürün kalemlerine elle dağıtıyor. Shopify'daki "Cost per item" değeri bu yüzden yanlış kalıyor. Stocky bunu teslim alma sırasında kısmen yapıyordu.

**Kimde var:** İthalat yapan küçük Shopify mağazaları. 2025–26'daki gümrük tarifesi değişiklikleri nedeniyle konu güncel.

**Kanıtlar:**
- [KANIT] 2026-08-07 · "How are you handling landed cost per unit once Stocky is gone?" Alıntı: "The PO says the goods cost 4,200. Then freight. Then duty. Then the supplier knocks 3% off … the number that finally lands in Shopify as your unit cost is still 4,200". OP bir uygulama geliştirdiğini açıkça belirtiyor. (804 görüntülenme, 26 gönderi) https://community.shopify.com/t/how-are-you-handling-landed-cost-per-unit-once-stocky-is-gone/661708
- [KANIT] 2026-07-11 · "Feature Request: Landed Cost Field in Purchase Order Receiving Workflow". Alıntı: "we need the ability to record the actual landed cost per unit at the time of receiving". Bir yanıt: "That's what we used Stocky was for." (424 görüntülenme, 16 gönderi) https://community.shopify.com/t/feature-request-landed-cost-field-in-purchase-order-receiving-workflow/650480
- [KANIT] 2026-11-04 · "How do you reprice when a duty rate changes?" Alıntı: "do you work from a landed cost per product (product cost plus freight, duty and fees) or from a rough markup on the supplier price". Dünkü bir başlık ama 34 görüntülenmeyle zayıf. https://community.shopify.com/t/how-do-you-reprice-when-a-duty-rate-changes/709817
- [KANIT] 2026-02-04 · 587292'de kaybedilenler arasında: "adjust our costs when receiving to utilize average costs on products".

**Mevcut alternatifler ve fiyatlar:** [KANIT] Geniş envanter uygulamaları (FyreTrail $59/ay vb.) ve tablo yöntemi. [ÇIKARIM] Bu dar işi tek başına yapan ucuz bir araç görmedim. Doğrulama yapmadım, rakip araması derinleştirilmeli.

**Yeterince iyi ücretsiz alternatif var mı?** KISMEN. Excel veya Sheets ile yapılabiliyor ama her PO'da elle tekrar ediliyor.

**Uyarı:** [ÇIKARIM] Ürün yalnızca aritmetik dağıtım yapar (değere, adede ya da ağırlığa göre). Gümrük oranı önermez, vergi veya muhasebe tavsiyesi vermez, değerleri kullanıcı girer. Finans tavsiyesi yasağına takılmaması için metinler buna göre yazılmalı.

**Nerede toplanıyorlar / yeni hesapla ulaşılır mı?** [ÇIKARIM] Shopify Community; ithalatçı ve e-ticaret toplulukları.

**Yapılabilirlik:** 5/5. [ÇIKARIM] MVP şöyle olur: PO kalemleri (SKU, adet, birim fiyat, ağırlık) CSV ile yüklenir ya da yapıştırılır. Navlun, gümrük ve indirim tutarları ile dağıtım yöntemi girilir. Araç birim başına maliyeti ve isteğe bağlı ağırlıklı ortalama maliyeti hesaplar. Shopify ürün CSV'sine "Cost per item" güncellemesi olarak dışa verir.

---

## Aday 5: Shopify ürün CSV'si için tarayıcıda ön kontrol ve onarım
**Problem:** Shopify ürün içe aktarmaları belirsiz hata mesajlarıyla düşüyor. Satır sonu (CRLF), UTF-8 ve aksan sorunları, "Inventory policy" değerleri, varyant satırları ve görsel kolonları başlıca nedenler. Tüccarlar saatlerce uğraşıyor.

**Kimde var:** Etsy veya WooCommerce'ten taşınanlar, tedarikçi dosyası yükleyenler, İspanyolca, Türkçe gibi aksanlı dillerde satış yapanlar.

**Kanıtlar:**
- [KANIT] 2024-05-26 · "CSV Etsy import error empty line 2". Alıntı: "Unquoted fields do not allow new line in line 2 … I could not get it right." https://community.shopify.com/t/csv-etsy-import-error-empty-line-2-csv-error-import/326225
- [KANIT] 2025-06-20 · "Can't Import Products CSV. Keep Getting Error Inventory policy is not included." Alıntı: "I downloaded the sample CSV provided on the Shopify Help Center … I'm getting the error". (386 görüntülenme) https://community.shopify.com/t/cant-import-products-csv-keep-getting-error-inventory-policy-is-not-included/420339
- [KANIT] 2026-01-09 · "¿Problemas importando CSVs con caracteres españoles (ñ, á, é)?" Alıntı: "Me sale error o los caracteres aparecen raros. ¿Usan alguna herramienta específica?" https://community.shopify.com/t/problemas-importando-csvs-con-caracteres-espanoles-n-a-e/582662
- [KANIT] 2026-07-02 · "CSV Import Issue". Alıntı: "Line 2: Validation failed: Cannot add more than 10000 references to a file." (418 görüntülenme) https://community.shopify.com/t/csv-import-issue/645056
- [KANIT] Bu iş için para isteyen hizmetler var: "CSV Preflight … $19 per file" (2026-09-21) https://community.shopify.com/t/csv-preflight-for-failed-shopify-product-imports-19-per-file/684883 ve "Shopify CSV import repair — fixed $25" (2026-11-02) https://community.shopify.com/t/shopify-csv-import-repair-fixed-25-free-file-assessment-first/708266 . Bunlar satıcı ilanı; alıcı olduğunu kanıtlamıyor.

**Mevcut alternatifler:** [KANIT] Ücretsiz rakip araçlar çıkmış: "Shopify CSV import errors? Free preflight check" (2026-10-18) https://community.shopify.com/t/shopify-csv-import-errors-free-preflight-check-before-uploading/700498 . Başlık adlarına göre 667001 ve 665019 da "Free … CSV checker". Matrixify gibi ücretli toplu içe aktarma uygulamaları da var, fiyatını doğrulamadım.

**Yeterince iyi ücretsiz alternatif var mı?** EVET'e yakın KISMEN. [ÇIKARIM] Son 3 ayda en az 3 ücretsiz denetleyici çıktı, farklılaşmak zor. Tek başına zayıf; Aday 1–4 paketine "bonus" olarak eklenmesi daha mantıklı.

**Nerede toplanıyorlar / yeni hesapla ulaşılır mı?** [ÇIKARIM] Shopify Community "Technical Q&A".

**Yapılabilirlik:** 4/5. [ÇIKARIM] MVP şöyle olur: Papa Parse ile dosya okunur. Kurallar denetlenir: zorunlu kolonlar, Handle tutarlılığı, varyant ve seçenek satırları, geçerli "Inventory policy" değerleri, karışık satır sonları, kodlama. Sorunlar satır satır raporlanır, otomatik düzeltilmiş UTF-8 CSV indirilir.

---

## Elenenler (zayıf sinyal veya doğrulanamayanlar)
- **Abonelik tuzağına düşürmeyen / toplu QR kod üretici.** [KANIT] HN'de aynı şikâyet tekrar ediyor. 2026-04-19 "Show HN: I couldn't find any BS-free QR code generator… scanning QR codes actually pings their servers" https://news.ycombinator.com/item?id=47826799 . 2024-08-16 "Free QR Code Generator… No ads, expiration, sign up" https://news.ycombinator.com/item?id=41264199 . 2026-02-07 yorum: "dynamic codes that expire unless you pay a massive annual fee" https://news.ycombinator.com/item?id=46922411 . [ÇIKARIM] Acı gerçek, ama HN'de 2024'ten beri 200'den fazla QR hikâyesi var ve ücretsiz alternatifler bol. Ücretli satış zor, bu yüzden elendi.
- **Etsy → Shopify CSV dönüştürücü.** [KANIT] Shopify Community'de birkaç başlık var (326225, 386223) ama düşük etkileşimli. Easy:Import uygulaması ve Shopify'ın Marketplace Connect'i zaten var. Sinyal zayıf.
- **DMARC XML rapor görüntüleyici.** [ÇIKARIM] Arama sonuçlarına göre Resend Mart 2026'da ücretsiz ve açık kaynak bir DMARC analizcisi çıkarmış, Postmark ücretsiz haftalık özet veriyor. Yeterince iyi ücretsiz alternatif var, ayrıca kaynağı açıp doğrulamadım. Elendi.
- **Etsy dijital planlayıcılara (PDF) iç bağlantı ekleme.** Fiverr'da çok sayıda "hyperlinked planner" ilanı çıktı; insanlar bu iş için freelancer tutuyor. Ama Fiverr sayfalarını ve topluluk şikâyetlerini açıp doğrulayamadım, bu yüzden aday olarak eklemedim. [ÇIKARIM] Kaynak B/C bunu doğrulayabilirse güçlü bir niş olabilir. pdf-lib ile 2,5 saatte yapılabilir.

## Genel çıkarım
- [ÇIKARIM] En güçlü ve en güncel sinyal "Stocky boşluğu". Kanıtlar binlerce görüntülenme alıyor (8,6 bin, 6,9 bin, 2,9 bin, 2,6 bin), alıntılar açıkça "abonelik pahalı, eskiden ücretsizdi" diyor ve dışa aktarma süresi ~29 Kasım'da bitiyor.
- [ÇIKARIM] Önerilen paket: Aday 1 (etiket) ana ürün olsun, Aday 2 (sayım) ve Aday 4 (birim maliyet) eklensin. Tek HTML dosyası, istemci tarafında çalışır, "aylık ücret yok, veriler tarayıcınızdan çıkmaz" vaadiyle $15–19'a tek seferlik satılır.
- [ÇIKARIM] Riskler: (a) Tüccarlar Shopify'a gömülü uygulama bekliyor, CSV dışa/içe aktarma adımı sürtünme yaratıyor. (b) Rakipler çok ve ücretsiz katmanlar var. (c) Shopify Community'de yeni hesapla ilk satışı 20 saat içinde almak belirsiz. [TAHMİN] 20 saatte satış olasılığı düşük-orta.
- [ÇIKARIM] Kitlenin tek ekosistemde toplanması da risk. Ana ajan bu dosyayı Reddit'e erişebilen bir kaynakla birleştirip farklı nişlerle çeşitlendirmeli.
