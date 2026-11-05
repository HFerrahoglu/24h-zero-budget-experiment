# Keşif C: Freelance pazar yerleri, Stack Exchange ve Türk kaynakları

Tarih: 2026-11-05, yaklaşık 16:20–17:10 (TR saati). Hazırlayan: araştırma alt ajanı.

Etiketler: [KANIT] = linki açıp kendim doğruladım · [ÇIKARIM] = benim yorumum · [TAHMİN] = sayısal veya zamanlama tahmini

## Önce okuyun: doğrulamanın sınırları

- **Fetch aracıma 403 dönen siteler:** Fiverr gig sayfaları, Upwork iş ilanları, community.shopify.com, excel.web.tr, technopat.net ve r10.net'in bazı konuları. Reddit, arama aracına hiç açık değildi. Bu sitelerdeki sonuçları **kanıt olarak saymadım**. Yalnızca "arama sonucunda başlık görüldü, açılamadı" diye not düştüm.
- **Bionluk:** Erişilebilen `bionluk.com/ilanlar/excel` sayfası alıcı taleplerini değil, satıcı hizmetlerini listeliyor. Bu yüzden Bionluk'tan tekrar eden iş kanıtı çıkaramadım.
- **Sonuç:** 7 aday hedefine ulaşamadım. **6 aday var: 3'ü güçlü, 3'ü zayıf.** Zayıf olanların zayıflığı her birinin altında açıkça yazıyor.

---

## Aday 1 (TR, EN GÜÇLÜ): e-Fatura/e-Arşiv XML (UBL-TR) → tek tıkla toplu Excel listesi + okunur PDF

- **Problem:** Muhasebeciler ve KOBİ'ler entegratörden veya portaldan yüzlerce e-fatura XML'ini ZIP olarak indiriyor. Bunları başlık ve kalem bazında (ürün, miktar, birim fiyat, KDV) tek bir Excel'e dökmenin kolay bir yolu yok.
- **Kimde var:** SMMM büroları, e-ticaret satıcıları, entegratör değiştiren firmalar ve fatura kalemlerini analiz etmek isteyen KOBİ'ler.

**Kanıtlar:**

1. [KANIT] R10.net, 20.03.2025: https://www.r10.net/off-topic/4400346-e-arsiv-fatura-excel-aktarim-muhasebe-programi-onerisi.html
   - Alıntı: "E Arşiv fatura ile entegre, toplu bir şekilde Excel'e aktarma yapan muhasebe programı önerisi var mı arkadaşlar?"
   - Kullanıcı birim fiyat, miktar ve tutar istiyor. Görüştüğü 3-4 programın bunu sağlayamadığını yazıyor.
   - Bir yanıtlayan ücretli özel yazılım teklif ediyor ("muhasebe uygulamalarından daha az maliyetli"). Başka bir yanıtta Mikro Jump öneriliyor.
2. [KANIT] DonanımArşivi forumu, ilk mesaj 19.12.2023, son yanıt 21.02.2025: https://forum.donanimarsivi.com/konu/xml-faturasindan-excele-veri-aktarma-yardim.859521/
   - Alıntı: "Bu faturalardan ürün hizmet kısmındaki verileri excel dosyasına aktarmam gerekiyor." Kullanıcının elinde yaklaşık 800 XML var.
   - Online dönüştürücüleri "çok yavaş, tek tek dosya ekletiyor" diye reddediyor. ABBYY dosya formatını desteklemiyor.
   - 2025'te biri ücretsiz bir GitHub aracı (xmlefatura) paylaşmış. Kullanıcının çalıştığını onayladığı görülmüyor.
3. [KANIT] GitHub o-adali/eAsist: https://github.com/o-adali/eAsist
   - Birisi sırf bu iş için Excel tabanlı bir araç yapmış: "İndirilen faturalar arasından filtreli arama yap, seçilen faturaların satırlarını tek tıkla Excel'e çıkart."
   - Araç ücretsiz ama lisans anahtarı istiyor, e-Arşiv portalına bağlanıyor ve kullanım sonu 31.12.2025 olarak planlanmış. 1 yıldız.
   - [ÇIKARIM] Bu kanıt şikâyet değil, talep sinyali.
4. [KANIT] Yurt dışında aynı iş için ücretli ürün planlanıyor: https://www.blink-brief.com/de/xrechnung-viewer
   - Almanya'da tarayıcıda çalışan bir XRechnung görüntüleyici var. Ücretsiz sürüm 5 dosyayla sınırlı. Sınırsız sürüm için **planlanan fiyat 12 €/ay**.
   - Aynı UBL mantığı. Bkz. Aday 2.
- **Doğrulanamayanlar (kanıt sayılmadı):**
  - excel.web.tr "E FATURA GIB(XML) DOSYALARINI TOPLU OLARAK EXCELE AKTARMA" konusu (403)
  - technopat "PDF içeriğini Excel'e aktarmak" konusu (403; arama özetine göre yaklaşık 20.000 fatura ve XML'leri de var)
  - Mikro forum "Toplu olarak XML olarak faturaları indirme" (yönlendiriyor)

**Mevcut alternatifler ve fiyatlar:**

- [KANIT] eAsist: ücretsiz ama portal bağımlı ve süreli.
- [KANIT] Forumda paylaşılan xmlefatura: ücretsiz, masaüstü.
- [KANIT] Freelancer'a özel yazılım yaptırmak: R10'daki teklif (fiyat verilmemiş).
- [ÇIKARIM] Bazı entegratör panellerinde Excel dışa aktarma var ama kalem detayı genelde yok (R10'daki kullanıcının şikâyeti tam da bu).
- [ÇIKARIM] Excel'in yerleşik XML içe aktarımı UBL-TR'nin iç içe yapısında kalem satırlarını düzgün açmıyor (forum yanıtlarından).

**Yeterli ücretsiz alternatif var mı?** KISMEN.
- Ücretsiz masaüstü araçlar var ama dağınık, güvensiz görünümlü ve portala bağımlı.
- "ZIP'i sürükle, kalem bazında xlsx al, hiçbir şey sunucuya gitmesin" diyen temiz, tarayıcıda çalışan bir Türkçe araç bulamadım.

**Kitle nerede ve yeni hesap ulaşabilir mi?** [ÇIKARIM]
- **excel.web.tr:** Çok aktif. Konu açıp soruyu çözen bir araç paylaşmak doğal olur. Ancak reklam kuralları sıkı olabilir, kuralları okumak gerekir.
- **R10.net "Sorum Var" / "Off-topic":** Yeni üyeye bazı bölümlerde mesaj sınırı olabilir. Satış konusu için genelde ücretli "satış bölümü" kuralı var. Ücretsiz sürümle "paylaşım" olarak girmek daha güvenli.
- **Diğerleri:** DonanımHaber yazılım bölümü, Technopat Sosyal, Ekşi'de "e-fatura" başlıkları, LinkedIn'deki SMMM grupları.
- [TAHMİN] 20 saat içinde satış için en olası kanal, eski konulara çözüm olarak yanıt yazmak ve "ücretsiz 20 fatura, sınırsız için Gumroad" modeli.

**Uygunluk ve risk:**
- Faturalar ticari belgedir. e-Arşiv'de bireysel alıcı adı bulunabilir.
- %100 tarayıcıda işlenir, hiçbir veri bize gelmez. Bunu sayfada belirgin yazmak gerekir.
- Vergi tavsiyesi içermez. Saf veri dönüştürmedir.

**2,5 saatte yapılabilirlik: 5/5**
- MVP: ZIP veya çoklu XML yükleme (JSZip) → DOMParser ile `cbc:ID`, `IssueDate`, satıcı/alıcı VKN-ünvan, `LegalMonetaryTotal`, `TaxTotal` ve `cac:InvoiceLine` (ad, miktar, birim fiyat, KDV) alanlarını okuma → iki sayfalı xlsx (Faturalar + Kalemler, SheetJS).
- Bonus: XML'e gömülü XSLT ile `XSLTProcessor` kullanarak toplu yazdırılabilir HTML/PDF.
- Ücretsiz sürüm 20 dosyayla sınırlı. Gumroad lisans anahtarı ile sınırsız.
- UBL-TR örnek XML'leri GİB'in ve GitHub'ın kamuya açık kaynaklarında bol.

---

## Aday 2 (GLOBAL: DE/BE/AB): XRechnung / Peppol (UBL ve CII) e-fatura XML → toplu Excel/CSV listesi

- **Problem:** Almanya'da 2025'ten beri B2B e-fatura alma zorunlu. Belçika'da 01.01.2026'dan beri Peppol zorunlu. Küçük işletmeler gelen XML faturaları okuyamıyor ve vergi danışmanına liste veremiyor. Resmi ücretsiz görüntüleyici tek tek dosya açıyor.
- **Kimde var:** Almanya, Belçika ve diğer AB ülkelerindeki serbest çalışanlar, küçük işletmeler ve kulüpler/dernekler.

**Kanıtlar:**

1. [KANIT] Blink Brief rehberi, güncelleme 01.11.2026: https://www.blink-brief.com/de/ratgeber/xrechnung-mehrere-dateien-pdf-excel
   - Resmi ELSTER görüntüleyici için: "Das Auswahlfeld nimmt jeweils eine Datei an." (Seçim alanı her seferinde tek dosya alıyor.)
   - Satıcı içeriği, kendi aracını öne çıkarıyor.
2. [KANIT] Blink XRechnung Viewer: https://www.blink-brief.com/de/xrechnung-viewer
   - Ücretsiz sürüm "Bis zu 5 Dateien auf einmal" (aynı anda en fazla 5 dosya). Ücretli sınırsız sürüm için planlanan fiyat 12 €/ay.
   - Tamamen tarayıcıda çalışıyor. Bu, birinin tam bu işi para karşılığı satmaya hazırlandığını gösteriyor.
3. [KANIT] invoicedataextraction.com rehberi, 22.04.2026 (güncelleme 12.05.2026): https://invoicedataextraction.com/blog/xrechnung-xml-oeffnen
   - "Wer eine XRechnung XML öffnen will, sieht nach dem Doppelklick oft nur Rohdaten." (XRechnung XML'i açmak isteyen, çift tıkladıktan sonra çoğu zaman yalnızca ham veri görür.)
   - "Ein Viewer macht die Rechnung sichtbar. Er macht daraus noch keine strukturierten Daten für Listen." (Görüntüleyici faturayı görünür kılar ama liste için yapılandırılmış veri üretmez.)
   - Rakip satıcı: ayda 50 sayfa ücretsiz, sonrası ücretli.
4. [KANIT] Access im Unternehmen dergisi, 2022: https://access-im-unternehmen.de/XRechnung_Teil_2_Rechnungen_einlesen/
   - XRechnung'u VBA ile içeri okumayı anlatan ücretli makale (13,25 €/ay abonelik).
   - [ÇIKARIM] İnsanlar bu çözüm bilgisi için bile para ödüyor.

**Zayıflık:** Kanıtların çoğu **satıcı veya içerik pazarlaması**. Bağımsız kullanıcı şikâyeti (forum veya Reddit) doğrulayamadım. Reddit ve gutefrage aramalarım sonuç vermedi veya erişilemedi.

**Mevcut alternatifler:**
- [KANIT] Blink: ücretsiz 5 dosya, ücretli sürüm planlanıyor (12 €/ay).
- [KANIT] invoicedataextraction: 50 sayfa/ay ücretsiz, sonrası ücretli.
- [ÇIKARIM] ELSTER/KoSIT görüntüleyiciler ücretsiz ama tek dosya açıyor ve Excel'e aktarmıyor. Muhasebe yazılımları (sevDesk, lexoffice vb.) aylık abonelikli.

**Yeterli ücretsiz alternatif var mı?** KISMEN. Ücretsiz görüntüleyici tek dosya veya 5 dosyayla sınırlı. Tek seferlik ücretli, sınırsız ve gizlilik odaklı bir araç için boşluk var.

**Kitle nerede?** [ÇIKARIM]
- Yerler: r/selbststaendig, r/Finanzen (kendi kendini tanıtma kuralları sıkı), r/belgium, r/BEFreelance, gutefrage.net, Indie Hackers, HN "Show HN".
- Engeller: Yeni hesapla Almanca subreddit'lerde link paylaşmak genelde kaldırılır. Show HN yeni hesaba açık ama 20 saatte satış belirsiz.
- [TAHMİN] Satış ihtimali TR'den düşük ama fiyat noktası daha yüksek (9–19 €).

**Uygunluk:**
- Ticari fatura verisi, tamamen tarayıcıda işlenir. Vergi tavsiyesi içermez.
- [ÇIKARIM] Aday 1 ile **aynı motor** (UBL 2.1). CII desteği ek iş. TR + DE için tek kod tabanı, iki açılış sayfası mümkün.

**2,5 saatte yapılabilirlik: 4/5**
- UBL kolay, CII (ZUGFeRD/Factur-X) ikinci şema olarak ek iş.
- MVP: çoklu XML/ZIP → tablo (no, tarih, satıcı, net, KDV, brüt, IBAN) → Alman Excel'i için noktalı virgüllü CSV + xlsx.

---

## Aday 3 (GLOBAL): Tedarikçi Excel/CSV → Shopify'a hazır ürün CSV'si dönüştürücü ve doğrulayıcı

- **Problem:** Mağaza sahipleri tedarikçinin Excel listesini Shopify'ın katı CSV formatına çeviremiyor. Varyant satırları, Handle, Option1 Name/Value, UTF-8 ve tırnak hataları yüzünden import bozuluyor. Bu yüzden ya Fiverr'da birine yaptırıyorlar ya da aylık uygulama alıyorlar.
- **Kimde var:** Yeni Shopify mağazaları, dropshipper'lar, tedarikçiden katalog alan butikler.

**Kanıtlar:**

1. [KANIT] Matrixify (Shopify App Store): https://apps.shopify.com/excel-export-import
   - Ücretsiz plan dosya başına 10 ürünle sınırlı. Ücretli planlar 20 $/ay, 50 $/ay ve 200 $/ay.
   - **1.861 yorum, 4,9 puan.** [ÇIKARIM] İnsanlar CSV import için düzenli ödüyor.
2. [KANIT] data.page "Supplier CSV to Shopify": https://data.page/supplier-csv-to-shopify
   - Tam bu işi satan bir ürün: ücretsiz 1 MB/gün, PRO 10 $/ay veya 80 $/yıl, masaüstü 120 $/yıl, özel iş için teklif.
3. [KANIT] eCommerce Fastlane, 30.09.2026 (Steve Hutt): https://ecommercefastlane.com/convert-supplier-pdf-to-shopify-csv/
   - "…so Shopify created a default variant and deleted the existing ones." (Shopify varsayılan bir varyant oluşturup mevcut olanları sildi.)
   - "Symbols appear in titles or descriptions because the file was not saved as UTF-8." (Dosya UTF-8 kaydedilmediği için başlık ve açıklamalarda semboller çıkıyor.)
   - Bu, import'un nerede kırıldığını anlatan güncel bir rehber.
4. [KANIT] Shopify resmi yardım sayfası "Solutions to common import problems": https://help.shopify.com/en/manual/products/import-export/common-import-issues
   - 18 ayrı hata mesajı listeleniyor ("Illegal quoting on line", "options are not unique", "Invalid CSV header: missing headers"…). Sayfada "your CSV file must be UTF-8 encoded" (CSV dosyanız UTF-8 kodlu olmalı) yazıyor.
   - [ÇIKARIM] Sorunun yaygın olduğunun dolaylı göstergesi.
- **Doğrulanamayanlar (403, kanıt sayılmadı):**
  - Arama sonucunda onlarca Fiverr gig'i görüldü, örneğin "I will convert vendor files to shopify CSV", "I will convert your vendor file into a shopify-ready CSV", "I will fix shopify CSV import errors and bulk upload products professionally".
  - Upwork'te "WooCommerce Product Import Specialist" ilanı.
  - community.shopify.com'da birçok "CSV import error / Option1 Value" konusu.

**Yeterli ücretsiz alternatif var mı?** KISMEN.
- Shopify'ın ücretsiz şablonu ve Excel ile elle eşleme mümkün ama hatalara açık.
- Matrixify'ın ücretsiz planı 10 ürünle sınırlı. data.page'in ücretsiz planı 1 MB/gün ile sınırlı.
- Tek seferlik ücretli, tarayıcıda çalışan bir "eşle → doğrula → indir" aracı için boşluk var. Rakipler aylık abonelik.

**Kitle nerede?** [ÇIKARIM]
- Yerler: r/shopify (kendi kendini tanıtma kuralları sıkı, yorumla yardım edilebilir), Shopify Community forumu (yeni hesap açılabilir, link politikası sıkı), Indie Hackers, Dev.to ("Shopify CSV'si neden bozuluyor" yazısı + araç), HN Show HN.
- [TAHMİN] Shopify kitlesi büyük ama gürültülü. 20 saatte birkaç satış mümkün ama garanti değil.

**Uygunluk:**
- Ürün verisi kişisel veri değil. Shopify'ın resmi CSV formatını kullanmak ToS ihlali değil.
- "Shopify" adını betimleyici olarak kullanmak marka riski taşır. Ürün adında "Shopify" geçmemeli, örneğin "CSV Fixer for Shopify stores" gibi betimleyici kullanım.

**2,5 saatte yapılabilirlik: 4/5**
- MVP: Excel/CSV yükleme (SheetJS) → sütun eşleme ekranı (Title, Price, SKU, Option1…) → aynı ürünün varyantlarını Handle ile gruplama → doğrulayıcı (zorunlu başlıklar, tekrarlanan opsiyon, boş fiyat, UTF-8, kıvrık tırnak) → Shopify şablonuna uygun UTF-8 CSV ve hata raporu.

---

## Aday 4 (TR, ZAYIF): Pazaryeri (Trendyol/Hepsiburada) toplu ürün kâr/komisyon tablosu

- **Problem:** Satıcılar her ürün için komisyon, hizmet bedeli, kargo/desi, KDV ve stopaj kesintilerinden sonraki net kârı hesaplamakta zorlanıyor. Çok ürünlü listede bunu topluca görmek istiyorlar.
- **Kimde var:** Trendyol ve Hepsiburada'daki küçük satıcılar.

**Kanıtlar (talep sinyali, şikâyet değil):**

1. [KANIT] GitHub DrTol/TrendyolKarHesaplamaAraci: https://github.com/DrTol/TrendyolKarHesaplamaAraci
   - Ücretsiz Excel (.xlsm/.xlsx), oranlar 10.07.2023 sonrasına göre ayarlı. 5 yıldız, Ko-fi bağış linki var.
2. [KANIT] heyvaql rehberi ve ücretsiz hesaplayıcı: https://heyvaql.com/rehber/trendyol-komisyon-ve-kar-hesaplama
   - "Kayıt istemez", tek ürünlük. Ayrıca mağaza bağlantılı ücretli analiz var (fiyat sayfada yok).
3. [KANIT] Melontik rehberi, 26.10.2026: https://melontik.com/blog/rehberler/trendyol-komisyon-ve-kar-hesaplama
   - Trendyol ve Hepsiburada için resmi API ile sipariş bazlı net kâr hesaplayan bir SaaS. Fiyat bu sayfada yok.
4. [KANIT] olaybuiste.com Excel şablonları: https://olaybuiste.com/excel-sablonlari/
   - Trendyol, Hepsiburada ve N11 kâr hesaplama Excel'leri ile ücretsiz tarayıcı araçları.

**Yeterli ücretsiz alternatif var mı?** EVET.
- Tek ürün için çok sayıda ücretsiz hesaplayıcı ve Excel var.
- Sipariş bazlı gerçek kâr için API'li SaaS'lar var.
- Boşluk yalnızca "panelden indirilen Excel'i yükle, ürün bazında gerçek kârı gör" noktasında olabilir. Ama panel export formatının örnek dosyası elimizde yok. **[ÇIKARIM] Bu büyük bir yapım riski.**

**Kitle nerede?** [ÇIKARIM] R10 e-ticaret bölümleri, Facebook'taki "Trendyol Satıcıları" grupları (giriş gerekir), Webmasterlar. Yeni hesapla erişim mümkün ama pazar kalabalık.

**Uygunluk:**
- **SINIRDA:** Kamuya açık oranlarla deterministik ticari hesap yapılıyor. Vergi oranları (KDV, stopaj) içerdiği için "finansal tavsiye değildir, oranları panelden doğrulayın" uyarısı şart.
- Trendyol markası adda kullanılmamalı.

**2,5 saatte yapılabilirlik: 4/5 (tekil ve toplu hesaplayıcı), 2/5 (panel export ayrıştırıcı, örnek dosya yok)**
- MVP: ürün listesi Excel'i (maliyet, satış fiyatı, kategori, desi) → kategori komisyon tablosu ve kargo baremi → net kâr ve marj, zarar edenler kırmızı.

---

## Aday 5 (TR, ZAYIF): Okul ve hastane nöbet çizelgesi otomatik ve adil dağıtım

- **Problem:** Müdür yardımcıları ve sorumlu hemşireler/hekimler aylık nöbet listesini elle hazırlıyor. İzin, ardışık nöbet ve hafta sonu eşitliği kısıtlarıyla saatler harcıyorlar.
- **Kimde var:** Okul idarecileri, hastane birim sorumluları, eczane ve güvenlik ekipleri.

**Kanıtlar:**

1. [KANIT] NöbetPro: https://nobet.pro/
   - Sağlık sektörü için web uygulaması, "Tamamen Ücretsiz". "1000+" kullanıcı ve "50+" hastane yazıyor.
   - [ÇIKARIM] Talep gerçek ama ücretsiz bir rakip doldurmuş.
2. [KANIT] farukguler.com "Nöbet Hazırlama Programı (Mazeretli)", 28.03.2023 (güncelleme 16.10.2026): https://farukguler.com/posts/nobet-hazirlama-programi/
   - Ücretsiz ve açık kaynak, okul/hastane/eczane için. Bir okul müdürünün yorumu: "Excel entegrasyonu güzel, Nöbetleri excel olarak indirme ve yükleme imkanı var."
3. [KANIT] Progmatic gibi ücretli okul yazılımlarında nöbet modülü var.
   - Bu bilgi yalnızca arama özetinden geliyor (recapio özeti), kaynağı açmadım. Bu yüzden bu madde [KANIT] sayılmaz, zayıf.
- **Doğrulanamayanlar:** excel.web.tr "Otomatik Nöbet Listesi Hazırlama" konusu (403). Arama özetine göre 21 personel için izin ve ardışık nöbet kısıtlı adil dağıtım isteniyor. GitHub tesaduff/nobet-gorevlendirme (açmadım).

**Yeterli ücretsiz alternatif var mı?** EVET. Okul için NobetPRO ve farukguler, hastane için NöbetPro ücretsiz. [ÇIKARIM] Tek seferlik ücretli satışa yer dar.

**Kitle nerede?** [ÇIKARIM] Öğretmen Facebook grupları (giriş gerekir), memurlar.net forumu, Ekşi "nöbet" başlıkları, excel.web.tr. Yeni hesapla erişim mümkün ama ücretsiz rakiplere karşı satış zor.

**Uygunluk:** Personel adı ve izin günleri işlenir. Sağlık verisi değil, ama "mazeret" alanına sağlık bilgisi girilmemesi uyarısı gerekir.

**2,5 saatte yapılabilirlik: 3/5.** Kısıt çözücü (açgözlü algoritma + rastgele yeniden deneme) 2,5 saatte yapılabilir ama ince ayar ister.

---

## Aday 6 (GLOBAL, ZAYIF): Takvim (Google/Outlook .ics) → saat raporu (timesheet/fatura dökümü)

- **Problem:** Serbest çalışanlar ve danışmanlar takvimdeki etkinliklerden müşteri veya proje bazında toplam saat çıkarmak istiyor.
- **Kimde var:** Saatlik çalışan freelancer'lar, terapist dışı danışmanlar, özel ders verenler.

**Kanıtlar:**

1. [KANIT] Calrows (Google Workspace Marketplace): https://workspace.google.com/marketplace/app/calrows_sheets_calendar_sync_export_time/163011926713
   - Ücretsiz sürüm ayda 50 etkinlikle sınırlı. Pro **6 $/ay veya 48 $/yıl tek seferlik ödeme**, takım 190 $/yıldan başlıyor.
   - [ÇIKARIM] İnsanlar bu iş için ödüyor.
- **Doğrulanamayanlar:**
  - Bağımsız kullanıcı şikâyeti (webapps.stackexchange, Reddit) bulamadım veya açamadım.
  - Arama sonuçlarında TimeCamp ve CalendarLabs (ücretsiz CSV export), "Google Calendar Export GCal to CSV" ve TrakkyTime Chrome eklentileri ile bir Apps Script gist'i görüldü, açmadım.

**Not:** **Bu aday ≥3 doğrulanmış kanıt şartını karşılamıyor. Yalnızca yedek fikir olarak listeledim.**

**Yeterli ücretsiz alternatif var mı?** EVET (arama sonuçlarına göre birden fazla ücretsiz CSV dışa aktarıcı ve eklenti var). [ÇIKARIM] Farklılaşma zor.

**2,5 saatte yapılabilirlik: 5/5.** .ics ayrıştırma (tekrarlayan etkinlikler dahil) → anahtar kelime ve renk bazlı gruplama → saat toplamı → CSV/PDF.

---

## GÜNCELLEME (kanal kısıtı sonrası): indie maker ve geliştirici alıcılar

Koordinatörden gelen bilgi: yeni hesapla ulaşılabilen kanallar yalnızca r/SideProject, r/indiehackers, r/alphaandbetausers, r/coolgithubprojects ve r/IMadeThis. Türk kanalları büyük ölçüde kapalı. Bu yüzden aşağıdaki iki global adayı ekledim.

## Aday 7 (GLOBAL, YENİ, KANAL UYUMU EN YÜKSEK): App Store / Google Play ekran görüntüsü üretici

Tarayıcıda çalışır: cihaz çerçevesi, başlık metni, arka plan ve mağazanın istediği tüm boyutlarda toplu dışa aktarma.

- **Problem:** Indie uygulama geliştiricileri her sürümde mağaza ekran görüntülerini Figma'da elle hazırlıyor (çerçeve, üst yazı, her cihaz boyutu için ayrı export) ve buna günler harcıyor. Hazır araçlar ise aylık abonelikli.
- **Kimde var:** Solo iOS/Android geliştiricileri, indie hacker'lar, küçük uygulama stüdyoları. Bunlar tam olarak r/SideProject ve r/indiehackers kitlesi.

**Kanıtlar:**

1. [KANIT] Jesse Squires blogu, 16.01.2024: https://www.jessesquires.com/blog/2024/01/16/app-store-screenshot-requirements/
   - "The screenshot requirements for the App Store have increasingly become a burden for developers, especially indies." (App Store ekran görüntüsü gereksinimleri geliştiriciler için, özellikle indie'ler için, giderek bir yüke dönüştü.)
   - Tanınmış, bağımsız bir iOS geliştiricisi.
2. [KANIT] Dev.to, Mateusz (@mateusz_b9), 24.10.2025: https://dev.to/mateusz_b9/i-spent-3-days-making-app-store-screenshots-so-i-built-a-tool-that-does-it-in-15-minutes-39cn
   - "I spent 3 days designing screenshots for my last app launch. It should've taken 15 minutes." (Son uygulama lansmanım için ekran görüntüsü tasarlamaya 3 gün harcadım. 15 dakika sürmeliydi.)
   - Kendi aracını ücretli satıyor: Indie 9,99 $/ay, Studio 29,99 $/ay, 100 kredilik paket 5 $.
3. [KANIT] Dev.to, Darren Egick, "Mar 15" (yıl sayfada görünmüyor): https://dev.to/darren_egick_5774637ad15e/stop-manually-creating-app-store-screenshots-a-founders-practical-solution-378d
   - "Three full days in Figma, positioning mockups, adding text overlays, exporting at the exact right resolution" (Figma'da tam üç gün: mockup yerleştirme, metin ekleme, tam doğru çözünürlükte dışa aktarma.)
   - Onun aracı AppFinish: üretim başına 5 $, 2 AI üretimi 19 $.
4. [KANIT] AppScreens fiyatları: https://appscreens.com/pricing
   - Ücretsiz plan: 1 proje, 5 ekran, "essential" boyutlar, Pro özellikleri filigranlı.
   - Pro 99 $/yıl, Scale 180 $/yıl (aylık 15 $).
5. [KANIT] Previewed fiyatları (toolradar, 05.11.2026'da kontrol edilmiş): https://toolradar.com/tools/previewed/pricing
   - Lite ücretsiz: 720p ve CC atıf lisansı, yani ticari kullanım için atıf gerekiyor.
   - **Plus 9,99 $ tek seferlik**, Pro 19 $/ay.
   - [ÇIKARIM] Tek seferlik düşük fiyat noktası bu pazarda kabul görüyor.
- **Doğrulanamayan:** AppLaunchpad'in resmi fiyat sayfası 404 verdi. Arama özetine göre Pro 29 $/ay veya 180 $/yıl.

**Yeterli ücretsiz alternatif var mı?** KISMEN.
- Ücretsiz katmanlar filigranlı, 720p, atıf zorunlu ya da 1 proje ile sınırlı. Figma şablonları ücretsiz ama elle çalışma gerektiriyor.
- **Risk [ÇIKARIM]:** Pazar çok kalabalık. Arama sonuçlarında 10'dan fazla yeni rakip çıktı (Screenhance, stora.sh, appscreenshotstudio, Shotcraft, framestudio…). Farklılaşma şart. Önerim: "tek seferlik 9–15 $, hesap yok, %100 tarayıcıda, sınırsız export, filigran yok".

**Kitle nerede?** [ÇIKARIM]
- r/SideProject ve r/IMadeThis'te "yaptığım şey" paylaşımları kabul görüyor. r/alphaandbetausers'ta beta kullanıcı istemek doğal.
- r/iOSProgramming ve r/androiddev daha isabetli olurdu ama kendi kendini tanıtma kurallarını kontrol etmek gerekir. Bunlar koordinatörün listesinde yok.
- Ücretsiz sürümü GitHub'a koyup r/coolgithubprojects'te paylaşmak mümkün.

**Uygunluk:**
- Kullanıcının kendi ekran görüntüleri işlenir, kişisel veri yok.
- **Marka riski:** Apple ve Google'ın cihaz çerçeveleri (Apple Design Resources) lisanslı. Resmi çerçeveleri gömmek yerine CSS/SVG ile kendi çizdiğimiz jenerik çerçeveleri kullanmak gerekir. Ürün adında "App Store" geçmemeli, betimleyici kullanım yeterli.

**2,5 saatte yapılabilirlik: 4/5**
- MVP: PNG yükleme (çoklu) → şablon seçimi (arka plan gradyanı, üst başlık, jenerik telefon çerçevesi, Canvas) → hedef boyutlar listesi (iPhone 6.9" 1320×2868, 6.5" 1284×2778, iPad 13", Play 1080×1920 vb.; kesin değerler Apple ve Google dokümanlarından teyit edilmeli) → tek tıkla ZIP (JSZip).
- Ücretsiz sürüm filigranlı. Gumroad lisans anahtarı filigranı kaldırır.

## Aday 8 (GLOBAL, ZAYIF): Güncel "launch directory" listesi ve gönderim takip şablonu

- **Problem:** Ürün çıkaran maker'lar onlarca "launch directory" sitesine elle gönderim yapıyor. Hazır listelerdeki linklerin çoğu ölü ya da ücretli çıkıyor.
- **Kimde var:** r/SideProject ve r/indiehackers'ın çekirdek kitlesi.

**Kanıtlar:**

1. [KANIT] Dev.to, 20.06.2026: https://dev.to/_41cda9e439997374d9a9f/i-manually-checked-100-startup-launch-directories-here-are-16-free-ones-to-start-with-1mgg
   - "half the links are dead, paywalled, or just gone." (Linklerin yarısı ölü, ücretli ya da tamamen kaybolmuş.)
   - Yazar kendi 100'den fazla dizinlik ücretli Gumroad tablosunu tanıtıyor (fiyat sayfada yok).
2. [KANIT, sınırlı] Gumroad ürünleri gerçekten var ama sayfalar JS ile yüklendiği için fiyat ve satış sayısını doğrulayamadım:
   - LaunchPedia "150+ Launch Platforms & Directories to Launch Your SaaS": https://launchpedia.gumroad.com/l/list-my-saas
   - datanerd "Submit Your Saas Startup to 100+ Directories Done For You": https://datanerd.gumroad.com/l/zrvnsn
   - abualmagd "200+ SaaS Directories and platforms": https://abualmagd.gumroad.com/l/vfrtz
   - Arama özetine göre fiyatlar 2–10 $ (liste) ve 149–347 $ (sizin yerinize yapılan hizmet). Bu fiyatlar doğrulanmadı.

**Yeterli ücretsiz alternatif var mı?** EVET. Dev.to'da ve GitHub'daki "awesome" listelerinde ücretsiz listeler bol. Değer yalnızca "bugün doğrulanmış, canlı" olmasında. [ÇIKARIM] 100'den fazla siteyi 2,5 saatte elle doğrulamak gerçekçi değil.

**2,5 saatte yapılabilirlik: 3/5.** Notion/Sheets takip şablonu kolay. Asıl iş olan güncel doğrulama zor. Ek bir fikir: tek açıklamadan her dizinin karakter sınırına göre kısaltılmış metin üreten bir "copy kit" aracı.

## İncelenip elenenler (kısa)

- **Toplu sertifika/katılım belgesi üretici (TR ve global):** Ücretsiz ve yeterli araçlar var. Eklavvya ücretsiz tarayıcı aracı batch başına 500 belge veriyor, ayrıca Word adres-mektup birleştirme var. Arama özetine göre Certifier ücretli. Elendi.
- **Apartman aidat takibi:** Ücretsiz masaüstü ve mobil uygulamalar bol (Proton Üye Takip, ApartSoft vb.). Kanıt toplanmadı. Elendi.
- **Raf etiketi / birim fiyat etiketi (TR):** Türk forumlarında doğrulanabilir talep bulamadım. Elendi.
- **GİB e-Arşiv portalında toplu fatura kesme:** Gerçek bir acı, ama portalı otomatikleştirmek ve kullanıcı şifresi işlemek gerekiyor. Kısıtları ihlal eder. Elendi.
- **Banka ekstresi PDF → Excel:** Hassas finansal kişisel veri. Elendi.

## Önerilen sıralama: kanal kısıtı sonrası GÜNCEL [ÇIKARIM]

Kanallar yalnızca İngilizce indie/maker subreddit'leri olduğu için:

1. **Aday 7 (mağaza ekran görüntüsü üretici).**
   - Alıcı tam kanal kitlesi.
   - Ödeme sinyalleri doğrulandı: Previewed 9,99 $ tek seferlik, AppScreens 99 $/yıl, Mateusz'un aracı 9,99 $/ay, AppFinish üretim başına 5 $.
   - Bağımsız şikâyet var: Jesse Squires 2024, iki dev.to kurucusu "3 gün harcadım".
   - En büyük risk rekabet. Farklılaşma: tek seferlik, hesap yok, tarayıcıda.
2. **Aday 3 (tedarikçi CSV'si → Shopify CSV'si).**
   - En güçlü "zaten ödüyorlar" sinyali: Matrixify 1.861 yorum, 20 $/ay.
   - Ama alıcı mağaza sahibi. r/SideProject kitlesine uyumu orta. Shopify işi yapan freelancer'lar da alıcı olabilir.
3. **Aday 2 (XRechnung/Peppol XML → Excel).** AB'deki serbest çalışanlar alıcı, ama listelenen subreddit'lere uyumu düşük.
4. **Aday 1 (TR e-Fatura XML → Excel).** En net boşluk ama Türk kanalları kapalı olduğu için tek TR adayı olarak yedekte kalsın. Aday 2 ile aynı motor, yani TR sürümü sonradan neredeyse bedava çıkar.
5. **Aday 4, 5, 6, 8:** Ücretsiz alternatifler yeterli veya kanıt zayıf. Önerilmez.

### İlk sıralama (kanal bilgisinden önce, kayıt için)

1. **Aday 1 + Aday 2'yi tek ürün olarak yapmak:** "UBL e-Fatura XML → Excel" motoru, TR öncelikli. Bu, en net boşluk ve en somut "biri ödeme planlıyor" sinyali (Blink 12 €/ay). Örnek veri kamuya açık, tamamen tarayıcıda çalışır, 2,5 saatte yapılır. Türk forumlarında birebir soran eski konular var, bunlara çözüm olarak yanıt yazılabilir.
2. **Aday 3 (Shopify CSV dönüştürücü):** En güçlü "zaten ödüyorlar" sinyali (Matrixify 1.861 yorum, 20 $/ay; data.page 10 $/ay; çok sayıda Fiverr gig'i). Ancak dağıtım gürültülü ve marka kullanımına dikkat gerekiyor.
3. **Aday 4–6:** Ücretsiz alternatifler yeterli olduğu için 20 saatlik satış deneyi için önerilmez.
