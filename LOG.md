# LOG — Zaman damgalı karar günlüğü

Saatler Türkiye saatidir (UTC+3). Biçim: **saat — ne yapıldı / neden / sonuç**.
Kanıt ile çıkarım ayrı yazılır: `[KANIT]` = bağlantı veya komut çıktısı, `[ÇIKARIM]` = benim yorumum, `[TAHMİN]` = sayısal tahmin.

---

## 2026-11-05

### 16:00 — Deney başladı
Bitiş: 2026-11-06 16:00.

### 16:03 — Faz 0: araç envanteri
- `[KANIT]` git 2.54, node 22.23.4 / npm 10.9.9, python 3.13.13 (`python`; `python3` alias'ı yok) çalışıyor.
- `[KANIT]` `gh` CLI kurulu değil. Ancak Git Credential Manager'da HFerrahoglu için kayıtlı bir GitHub token'ı var. Yalnızca varlığı kontrol edildi, değeri hiçbir yere yazdırılmadı. Token yetkileri: `gist, repo, workflow` (API `X-OAuth-Scopes` başlığı). Bu yüzden repo oluşturma ve Pages işlemleri REST API ile yapılabiliyor. Yardımcı script token'ı çalışma anında okuyor, dosyaya yazmıyor. Script repo dışında, oturum geçici klasöründe duruyor.
- `[KANIT]` WebSearch ve WebFetch çalışıyor. Bazı siteler (ruul.io destek makaleleri gibi) yönlendirme yapıyor, curl ile doğrulanabiliyor.
- `[KANIT]` Claude-in-Chrome tarayıcı eklentisi mevcut. Gerekirse yalnızca okuma amaçlı kullanılacak. Hesap açma otomasyonu YAPILMAYACAK.
- `[KANIT]` Gmail'e doğrudan erişimim yok. İlgili e-postaları operatör iletecek.

### 16:05 — Ruul Space araştırması: KAPATILMIŞ
Neden: Ürün biçimini teslim yöntemine göre seçmem gerekiyordu.
- `[KANIT]` `https://ruul.space/` → `<meta name="description" content="Ruul Space is no longer available. Visit ruul.io for more information.">`, `robots: noindex`, 1 sn sonra `https://ruul.io`'ya yönlendirme (curl, 16:06).
- `[KANIT]` Gerçek bir eski mağaza da aynı mesajı veriyor: `https://ruul.space/mavix`. Bu mağazanın linki Threads'te paylaşılmış: https://www.threads.com/@mavix_xo/post/DQv5NYIkkkB. Rastgele bir kullanıcı adı (`ruul.space/hferrahoglu`) da aynı mesajı veriyor.
- `[KANIT]` Eski destek makalesi "What is Ruul Space" (`support.ruul.io/en/articles/11556960`) 301 ile `https://ruul.io/support`'a yönleniyor. Oradaki 30+ makalenin hiçbiri Space, dijital ürün, teslim ya da mağaza ile ilgili değil.
- `[KANIT]` `https://ruul.io/sitemap-0.xml` (lastmod 2026-11-05) içinde `ruul-space` veya dijital ürün satış sayfası yok. Kalan ürünler: invoice-clients, subscriptions, get-paid, early-pay, crypto-payout.
- `[KANIT]` https://ruul.io/support/new-to-ruul/can-i-use-ruul: "Only digital and knowledge-based services qualify." Faturalanamayanlar arasında "product sales" açıkça sayılıyor.
- `[KANIT]` https://ruul.io/support/invoicing/how-to-add-and-manage-customers: müşteri eklerken şirket ülkesi ve şirket adı isteniyor. "Customers may be asked to provide company details before they can pay."
- `[KANIT]` https://ruul.io/support/invoicing/how-invoicing-works-on-ruul: ödeme linki fatura başına üretiliyor ve belirli bir müşteriye e-postayla gidiyor. Herkese açık ya da tekrar kullanılabilir bir ödeme linki tanımlanmamış.
- `[KANIT]` https://ruul.io/support/subscriptions/how-subscriptions-work-on-ruul: abonelik de önceden seçilmiş bir müşteriye bağlı.
- `[ÇIKARIM]` Ruul bugün (1) mağaza vitrini, (2) dijital ürün teslimi ve (3) tanımadığımız bir alıcının kendi kendine ödeme yapması işlevlerinin hiçbirini sağlamıyor. Üstelik ürün satışını kapsam dışı sayıyor. Kalan tek yol müşteri başına elle fatura kesmek. Bunun için de alıcının bize önce yazması, operatörün faturayı oluşturması ve büyük olasılıkla alıcının şirket bilgisi vermesi gerekiyor.
- **Sonuç:** Ruul Space bu deney için **yetersiz**. Kural gereği kanıt buraya yazıldı. Alternatif ancak bundan sonra öneriliyor (16:09 kaydı).

### 16:09 — Alternatif ödeme sağlayıcısı önerisi: Gumroad (operatör onayı bekleniyor)
Neden alternatif gerekiyor: Operatöre yalnızca 16:00-00:00 arasında ulaşılabiliyor (aşağıdaki 16:12 kaydı). Gece gelen bir alıcının operatör olmadan ödeme yapıp ürünü alabilmesi gerekiyor. Ruul'un elle fatura akışı bunu karşılamıyor.
- `[KANIT]` Gumroad Türkiye'ye TRY olarak banka ödemesi yapıyor. Kaynak, Gumroad'un açık kaynak yardım merkezi: https://github.com/antiwork/gumroad/blob/main/app/views/help_center/articles/contents/_13-getting-paid.html.erb (tabloda "Turkey — TRY"). Model dosyası: https://github.com/antiwork/gumroad/blob/main/app/models/turkey_bank_account.rb
- `[KANIT]` Asgari ödeme $100, satış başına 7 gün bekleme var. Stripe'ın KYC talebi "belirli bir süre geçtikten ve satış biriktikten sonra" geliyor. Yani ilk satıştan önce KYC şartı yok (aynı kaynak).
- `[KANIT]` Ücret: doğrudan satışta %10 + $0.50, Discover üzerinden %30 (https://gumroad.com/pricing).
- `[ÇIKARIM]` Kendi kendine ödeme, otomatik dosya veya link teslimi ve lisans anahtarı Gumroad'da standart. Kurulum maliyeti ve kart şartı yok. Yine de **yeni hesapla ürün yayınlamadan önce ödeme yöntemi istenip istenmediği doğrulanmadı**. Operatör hesap açarken kontrol edecek.
- Hızlıca elenen alternatifler `[ÇIKARIM, derin araştırma yapılmadı]`: Lemon Squeezy (mağaza aktivasyonu için inceleme süreci var, 24 saate sığmayabilir), Polar (Stripe Connect gerektiriyor, Türkiye Stripe hesabı desteği belirsiz), Shopier (TR sağlayıcısı, baştan kimlik ve IBAN istiyor; bu operatörden isteyemeyeceğim türden bir işlem).
- **Karar:** Plan A = Gumroad (operatör onayına bağlı). Plan B = Ruul elle fatura. Plan B'de ürün "dijital hizmet" olarak tasarlanır, yalnızca 00:00'a kadar fatura kesilebilir. Gerçekçi değil ama yedek olarak duruyor.

### 16:12 — Operatör penceresi yorumu ve zaman planının sıkıştırılması
- `[KANIT]` Görev metni: "16.00-00.00 saatleri hariç ulaşılamaz", "toplamda en fazla 8 saat". Deney 06/11 16:00'da bitiyor.
- `[ÇIKARIM]` Operatöre yalnızca **bugün 16:00-00:00** arasında ulaşılabiliyor. Gece yarısından sonra hiçbir paylaşım, yorum cevabı veya hesap işlemi yapılamaz. Bu yüzden görev metnindeki zaman kutuları (keşif 4 sa + inşa 7 sa + dağıtım 8 sa) bu pencereye **sığmıyor**.
- **Sapma kararı (gerekçeli):**
  - Keşif ≤ 1,5 sa (16:30-18:00). Paralel araştırma ajanlarıyla hızlandırılacak.
  - Seçim ≤ 20 dk (18:00-18:20).
  - İnşa ≤ 2,5 sa (18:20-20:50). Kapsam buna göre küçük tutulacak.
  - Satış altyapısı 20:50-21:30.
  - Aktif dağıtım 21:30-00:00. Operatör paylaşır ve gelen yorumlara cevap verir.
  - Pasif dağıtım 00:00-16:00. Paylaşımlar trafik getirmeye devam eder, ödeme kendi kendine işler. Ben bu sürede açılış sayfasını ve ürünü iyileştirebilirim, çünkü GitHub'a push için operatör gerekmiyor.
  - "Dağıtım ve satış en az 8 saat" şartı, satış penceresi olarak 21:30-16:00 (18,5 sa) ile karşılanıyor. Operatörün aktif katkısı ise yalnızca ~2,5 saat.
- Operatöre bilgi sorusu olarak soruldu: "06/11 sabahı ulaşılabilir misiniz?" Cevap evet olursa plan genişler.
- `[ÇIKARIM]` Operatör penceresi 16:00-00:00 TR = 08:00-16:00 ABD Doğu (EST, UTC-5; ABD yaz saati 01/11'de bitti) = 05:00-13:00 ABD Batı. ABD iş saatlerine denk geldiği için global İngilizce kanallar için zamanlama elverişli. TR akşam prime time'ı (20:00-23:00) da bu pencerenin içinde.

### 16:12 — Dağıtım araştırması alt ajana verildi
Neden: Bu iş fikir seçiminden önce gelmeli (görev kuralı), çok kaynaklı ve bağımsız. Ajan arka planda; ben bu sırada Ruul ve GitHub işleriyle ilerliyorum. Ek talimat: her platformun **yapay zekâ ile üretilmiş içerik** kuralları da araştırılacak. Tüm metinleri ben yazacağım; AI içeriği yasaklayan bir platform kanal olmaktan çıkar.

### 16:13 — Git kurulumu
- Yerel repo açıldı. `.gitignore` `.env` ve sır dosyalarını hariç tutuyor.
- Global git e-postası kişisel bir adres. Public repoda ifşa olmaması için **yalnızca bu repoda** commit e-postası GitHub noreply adresine ayarlandı. Global ayara dokunulmadı.
- Karar: Deney günlüğü repo'su **public** olacak. Gerekçe: (1) GitHub Pages ücretsiz planda public repo istiyor, (2) "yapay zekâ ajanıyla yapıldı" şeffaflığıyla tutarlı, (3) içerikte sır yok. Ürünün kendi repo'su gerekirse ayrıca açılacak.

### 16:15 — GitHub repo ve Pages hazır (Faz 0 tamamlandı)
- `[KANIT]` Public repo REST API ile oluşturuldu: https://github.com/HFerrahoglu/24h-zero-budget-experiment. İlk commit push edildi.
- `[KANIT]` Pages API ile etkinleştirildi (kaynak: `main:/docs`). Build 45 sn'de "built" oldu. https://hferrahoglu.github.io/24h-zero-budget-experiment/ HTTP 200 döndü.
- Operatöre Paket 1 verildi (16:16): Ruul menü kontrolü, Gumroad için kural gereği onay, Gumroad hesabı, sabah ulaşılabilirlik sorusu.

### 16:16 — Faz 1 keşfi paralel başlatıldı
Neden: Operatör penceresi 00:00'da kapanıyor. Keşfin 4 saat değil ~1,5 saat sürmesi gerekiyor. Kaynak türlerine göre 3 ajan:
- A: Reddit, Hacker News (Algolia API), Indie Hackers
- B: 1-3 yıldızlı yorumlar (Chrome Web Store, WordPress, Shopify, G2/Capterra, mağazalar), "alternative to X" aramaları, yıllardır açık GitHub talepleri
- C: Freelance ilanları (Upwork, Fiverr, Bionluk), Stack Overflow/Stack Exchange, Türkçe kaynaklar (Ekşi, Şikayetvar, DonanımHaber, Technopat, Webmasterlar, R10)
Her ajana şunlar söylendi: her linki gerçekten açıp doğrulamak, link uydurmamak, kanıt ile çıkarımı ayırmak. Çıktıları ben de örneklem alarak doğrulayacağım.

### 16:25 — Dağıtım araştırması tamamlandı → kanal havuzu dar
- `[KANIT]` Ayrıntılar RESEARCH.md §2'de, tam rapor research/distribution_channels.md'de. HN, Product Hunt, Stack Overflow, Shopify Community, r/webdev, r/SaaS, r/Entrepreneur, r/InternetIsBeautiful YZ metnini yasaklıyor. HN Show HN yeni hesaplara kapalı. PH'de 1 hafta bekleme var. Dizin kuyrukları haftalar sürüyor.
- Ajan A'nın bulgusunu ben de doğruladım: Shopify Community kuralları "AI-generated content is highly discouraged and will be removed" diyor (curl, 16:24). Bu yüzden Stocky kitlesine en doğal kanaldan ulaşamıyoruz.
- `[ÇIKARIM]` Mastodon'u kullanmama kararı aldım. mastodon.social kuralı "Accounts may not solely post AI-generated content" diyor ve yeni hesabımızın tüm içeriği YZ taslaklı olacak. Teknik olarak ifşa etsek bile kuralın ruhuna aykırı. Erişim kazancı bu riske değmez.

### 16:28 — Pazar kararı: global İngilizce, maker ve geliştirici kitlesi
Neden: Ulaşılabilirliğin ağırlığı ×3. Kurallara uyan kanallar yalnızca r/SideProject, r/indiehackers, r/alphaandbetausers, r/coolgithubprojects, r/IMadeThis. Hepsi İngilizce ve kitleleri ürün yapan insanlar. Türkçe kanallar 24 saatte fiilen kapalı (Ekşi çaylak, R10 1 ay, Technopat reklam cezası). Bir de pencere ABD iş saatlerine denk geliyor.
- Keşif ajanları B ve C'ye bu kitleye öncelik vermeleri söylendi. Bu kitleye özel D ajanı başlatıldı (HN Algolia, GitHub, Chrome Web Store, Gumroad).
- Ham ajan raporları kanıt olarak `research/` klasörüne kopyalandı.

### 16:29 — Reddit kurallarını birinci elden doğrulama denemesi başarısız → operatöre verildi
- `[KANIT]` Reddit sayfaları curl ile 403 dönüyor. Claude-in-Chrome eklentisi de reddit.com için "This site is not allowed due to safety restrictions" diyor. Bunu aşmaya çalışmadım.
- Karar: Kural doğrulamasını Paket 2, Görev 2.2'de operatör yapacak. Hesap açılırken zaten Reddit'te olacağı için ek süre ~8 dk.
- Paket 2 verildi (16:30): Reddit hesabı ve 5 hedef topluluğun kurallarının kontrolü.

### 16:38 — Faz 1 tamamlandı: 4 keşif ajanından 20 aday
- Ajanlar A, B, C, D toplam 6 kaynak türünü taradı. Ham raporlar `research/` klasöründe, özet tablo RESEARCH.md §3'te.
- `[KANIT]` Ücretsiz alternatif kontrolleri:
  - Screen Studio yerine OpenScreen (MIT), Recordly, Cap ve CapyCursor ücretsiz.
  - Mağaza ekran görüntüsü için WaveSpeed, App Screenshot Generator, LaunchShots ve UltraShot ücretsiz ve filigransız.
  - Lansman formu autofill'i için LaunchFill, Donkey Directories, Octane Launch Pilot ve SubmitIQ var (Chrome Web Store listeleri).

### 16:40 — Faz 2: SEÇİM = "Lansman kanal kuralları + gönderim kiti" (43/50)
- Puanlama tablosu ve gerekçe: RESEARCH.md §4. Şeytanın avukatı: §5, üç itirazın hepsine cevap verildi.
- Seçilen adayın kanıtlarını kendim doğruladım:
  - HN 46676047, 43331842, 42943314 (Algolia API).
  - Gumroad'da $9.99'lık lansman listesi 276 satışta (sayfa JSON'u).
- Ürünün çekirdeği autofill değil, **doğrulanmış kanal kuralları**: YZ metni politikası, yeni hesap kapısı, kuyruk süresi, paylaşım günü, kaynak alıntısı ve tarihi. Neden: autofill eklentileri zaten var. Bu kural bilgisi ise ancak bu deneyde birinci elden araştırılarak çıktı.
- Fiyat kararı (ön): **$7 tek seferlik**.
  - Emsal: $9.99'luk liste, 276 satış.
  - Bizimki daha dar kapsamlı ve satıcı tanınmıyor, bu yüzden emsalin altında tutuldu.
  - Gumroad kesintisi 0,70 + 0,50 = $1,20, net $5,80 (%83).
- Zaman: Faz 1+2 planlanan 18:20 yerine 16:40'ta bitti, yani ~1,5 saat önde. Bu kazanç daha erken paylaşıma (≤19:30 TR = 11:30 ET) aktarılacak.

### 16:39-16:55 — Faz 4: MVP inşası (planlanan 2,5 sa yerine ~20 dk sürdü)
- Ürün: **Where Can I Post?** Kullanıcı hesap yaşını, metnin YZ destekli olup olmadığını, görünürlük için ne kadar bekleyebileceğini ve bütçesini seçiyor. Araç kanalları open / caveats / closed diye ayırıyor; her biri için kural alıntısını (birebir değilse "Rule summary" etiketiyle), kaynağı, kaynak türünü (primary / archived / secondary) ve kontrol tarihini gösteriyor.
  - Ücretsiz sürüm 12 kanal içeriyor, ücretli kit 50.
  - Kitte ayrıca karakter sayaçlı lansman profili, autofill bookmarklet (asla submit etmiyor), takip tablosu ve CSV/JSON dışa aktarma var.
- Ek veri: Ajan E 17 kanalı birincil kaynaktan doğruladı. Bulgulardan bazıları: Firsto ~180 gün, OpenHunts "~60 weeks", Open-Launch 2027'ye kadar dolu, DevHunt artık $49, HackerNoon YZ metnini kabul etmiyor.
- Repo: https://github.com/HFerrahoglu/where-can-i-post (MIT, yalnızca ücretsiz veri). Canlı sayfa: https://hferrahoglu.github.io/where-can-i-post/
  - Ücretli veri gitignore'da, public repoya girmedi (staged dosyalar kontrol edildi).
  - Üçüncü taraf sitelerin HTML'leri (test fixture'ları) telif nedeniyle repodan çıkarıldı.
- Test: 41 uçtan uca test jsdom ile çalıştırıldı, hepsi geçti. Kapsam:
  - Karar mantığı.
  - Kit: profil, sayaç, bookmarklet, takip.
  - Gerçek Launching Next formunda autofill. Bu test üç gerçek sorunu yakaladı ve düzeltildi: id'siz `label[for]`, önceden `https://` ile dolu URL alanı, `startupname` gibi bitişik alan adları.
- Bulunup düzeltilen mantık hatası: Kuyruk süresi doğrulanmamış dizinler "open" görünüyordu. Artık doğrulanmamış alanı olan her kanal en iyi ihtimalle "caveats" sayılıyor.
- `[KANIT]` Ölçülen sonuç (yeni hesap + YZ metni + 24 sa + $0): ücretsiz sürümde 0 open / 5 caveats / 7 closed, tam kitte 1 open / 23 caveats / 26 closed (jsdom ile hesaplandı). Paylaşım metinleri bu sayılara dayanıyor.
- QA:
  - Canlı sayfada abacus sayaçları uçtan uca çalışıyor (`visit_selftest=1`, `demo_selftest=1`). `selftest` ref'i metriklerden hariç tutulacak.
  - 375 px'te yatay taşma yok (iframe ölçümü: scrollWidth 360).
  - Headless Edge minimum 492 px render ettiği için mobil ekran görüntüsü kesik görünüyordu. Gerçek taşma bu değildi.
- Teslim dosyası: `product/dist/where-can-i-post-full-kit.zip` (20 KB; tek HTML + README.txt kullanım kılavuzu).

### 16:55 — Faz 5 kararları
- **Açılış sayfası = ürünün kendisi** (GitHub Pages). Gerekçe: Ziyaretçi değeri ödemeden önce deniyor (demo). Gumroad yalnızca ödeme ve teslim için kullanılıyor. Ayrı bir pazarlama sayfasına gerek yok.
- **Fiyat $7 tek seferlik.** Emsal: aynı kitleye satılan $9.99'luk liste, 276 satış. Abonelikli rakipler AppScreens $99/yıl, Screen Studio $29/ay. Gumroad kesintisi $1,20, net $5,80.
- **İade:** 14 gün koşulsuz. Gumroad panelinden yapılabilir ve operatörün deney sonrası yükümlülüğü olacak (REPORT §9).
- **Ölçüm:** kayıt gerektirmeyen abacus sayaçları, namespace `wcip-hf24h`, kanal başına `?ref=`. Olaylar: `visit` (sayfa yüklemesi), `demo` (ilk filtre tıklaması), `buy` (satın alma butonu). Satış verisi Gumroad'dan operatör aracılığıyla gelecek.
- **Akış doğrulaması para harcamadan yapılacak:** Gumroad Preview. Operatöre satın alma yaptırılmıyor, indirim kodu da oluşturulmuyor. Gerekçe: $0'lık test siparişi Gumroad'da satış olarak görünür ve metrikleri bulandırır.
- Paket 3 (Gumroad ürünü + Launching Next) ve Paket 4 (Reddit metinleri `posts/` altında, hazır cevaplar `posts/faq_replies.md`) OPERATOR_TASKS'a yazıldı.

### 16:58 — Operatör talimatı: hesaplar açık, ajan tarayıcı üzerinden erişebilir
- Operatörün mesajı (birebir): "Ruul'da, GumRoad'ta, Reddit'te hesabım var. Gir ve kontrol et. Hesap açma işlemlerini ben yaptım, gerisine sen bakabilirsin."
- Bu, görev metnindeki iki kuralı operatörün kendisi değiştiriyor demek. Eski kurallar: "Ruul hesabına sen erişmeyeceksin" ve "yayınlayan operatör olacak".
- Erişim yolu: Claude-in-Chrome eklentisi, operatörün açık tarayıcı oturumları. Şifre girilmiyor, hesap açma otomasyonu yapılmıyor.
- Kendime koyduğum sınırlar:
  - Ruul'da yalnızca okuma. Ödeme hesabı, kimlik, para çekme ve ayarlara dokunulmuyor.
  - Gumroad'da ürün taslak olarak kurulacak.
  - Herkese açık yayınlama adımları (Gumroad "Publish", Reddit paylaşımları, Launching Next gönderimi) için operatörden açık onay alınacak. Gerekçe: Metinleri ben yazdım, yayınlanınca geri alınamayabilir.
- REPORT §6'da "ne kadar kendi başına" sorusu için bu değişiklik ayrıca belirtilecek.

### 17:00-17:07 — Tarayıcıyla hesap kontrolleri ve Gumroad taslağı
- `[KANIT]` **Ruul paneli** (app.ruul.io, yalnızca okundu). Menü: Yeni Fatura, Ana Sayfa, Faturalar, Abonelikler, Müşteriler, Ödeme Hesapları. **Space, mağaza ya da ürün bölümü yok.** Ruul Space'in kapandığı böylece birinci elden doğrulandı (16:05 bulgusuyla tutarlı). Ödeme Hesapları'na girilmedi.
- `[KANIT]` **Reddit:** Eklenti reddit.com'u engelliyor ("This site is not allowed due to safety restrictions"). Aşılmaya çalışılmadı. Reddit işleri operatörde kalıyor.
- `[KANIT]` **Gumroad:** Hesap `hferrahoglu` (ekran görüntüsünde önce `ferrahoglu` okundu; operatör düzeltti, curl ile doğrulandı), ürün yok, Bio boş. Görev 1.2'nin karşılığı: Operatör Gumroad hesabını açtı ve "gerisine sen bakabilirsin" dedi. Bunu Gumroad kullanımına ONAY olarak kaydediyorum.
- **Taslak ürün** (`/products/pacagh`, yayında DEĞİL):
  - Ürün sayfası: ad, açıklama, fiyat $7 (pay-what-you-want kapalı), özet, kapak (1280×720) ve kare küçük resim (600×600; ilk yükleme reddedildi, "Image must be square").
  - Ayarlar: URL `hferrahoglu.gumroad.com/l/wherecanipost`, iade politikası "14-day money back guarantee" ve açıklaması.
  - Satış sayısı kamuya gösterilmiyor. Sahte sosyal kanıt riski yok.
  - Content: ZIP (19,9 KB) ve kullanım notu. Receipt: özel mesaj.
- **Teslim akışı para harcamadan doğrulandı:** Makbuz önizlemesinde "View content" butonu ZIP'in indirildiği sayfaya gidiyor ve satıcı iletişimi (hferrahoglu@gmail.com) yazıyor.
- Açılış sayfasındaki satın alma butonu Gumroad URL'sine bağlandı ve push edildi.
- **Yayınlama (Publish) operatör onayını bekliyor.** Launching Next formunda "Quick Check: What is 2+3?" bot kontrolü var. Bot kontrollerini ajan çözmüyor, bu yüzden gönderimi operatör yapacak.

### 17:08-17:12 — Operatör ONAY verdi → Gumroad yayında
- Operatörün mesajı: "ONAY". Kapsamı: (1) ürünü yayınlamak, (2) profile Bio eklemek.
- Profil Bio'su eklendi ("Changes saved").
- Ürün yayınlandı ("Published!"). **Yayınlamada ödeme, banka ya da kimlik bilgisi istenmedi** (ACCOUNTS'a eklendi).
- Hata ve düzeltme: Ürün URL'si `awherecanipost` olarak kaydedilmişti. Ctrl+A alanı seçmemiş, harf metne karışmıştı. Alan üç tıkla seçilip yeniden yazıldı, değer JS ile doğrulandı. Düzeltme yayına girmeden önce yapıldı, kimse eski linki görmedi.
- `[KANIT]` https://hferrahoglu.gumroad.com/l/wherecanipost HTTP 200 dönüyor:
  - Sayfa JSON'unda `price_cents: 700` ve `currency_code: usd`.
  - Sayfada "14-day money back" yazıyor.
  - Alıcı görünümünde "Includes: 1 file · ZIP · 19.9 KB" ve "I want this!" var. Türkiye'den bakınca fiyat TRY 350,33 görünüyor (Gumroad yerel para birimiyle gösteriyor).
- Açılış sayfasındaki satın alma butonu doğru URL'ye gidiyor (canlıda curl ile kontrol edildi).
- **Satış altyapısı (Faz 5) tamamlandı: 17:12.** Sıradaki: Reddit paylaşımları. Paylaşımları operatör yapacak, eklenti Reddit'i engelliyor.

### 17:15 — Operatör: "Gumroad'a ben kendi bilgilerimi girmiştim zaten. Reddit kısmını da sen yürütebilirsin."
- Gumroad'daki ödeme ve kimlik bilgilerini operatör kendisi, ajandan bağımsız olarak girmiş. Ajan bu bölümlere girmedi ve bunu istemedi. Yayınlamada ek bilgi istenmemesinin nedeni muhtemelen bu `[ÇIKARIM]`.
- Reddit: Ajan bu işi yürütemiyor. Claude-in-Chrome eklentisi reddit.com'u "safety restrictions" gerekçesiyle iki kez engelledi (16:29 ve 17:02). Alternatif yollar da var: API, OAuth uygulaması, token. Ancak bunlar (a) bir güvenlik kısıtını dolanmak, (b) ajanın kimlik bilgisi/token işlemesi anlamına gelir. İkisini de yapmıyorum. Karar: Reddit paylaşımlarını operatör yapacak. Ajan metinleri sohbete kopyalanmaya hazır olarak verecek, yorum cevaplarını hazırlayacak ve metrikleri izleyecek.

### 17:18 — r/SideProject kuralları (operatörün birinci elden kontrolü) ve paylaşım kararı
- `[KANIT, operatör gözlemi]` Kendi ürününü tanıtmak serbest, topluluk bunun için kurulmuş. YZ içeriğini yasaklayan katı bir kural yok. Üyeler ve yöneticiler "AI wrapper"lara mesafeli. YZ içermeyen özgün projeler için ayrı bir "Not-AI" megathread'i var.
- **Karar:** Normal gönderi olarak paylaşılacak, Not-AI megathread'ine konmayacak. Gerekçe: Ürün YZ kullanmıyor, ama YZ ajanı tarafından yapıldı ve metin YZ taslağı. Not-AI başlığına koymak yanıltıcı olur.
- Kitlenin mesafesine karşı gövdeye tek bir dürüst açıklama eklendi: araç bir AI wrapper değil, YZ/API çağrısı yapmıyor; YZ yalnızca aracı yapan. Gerekçe: Hem doğru hem en olası itirazı baştan karşılıyor.

### 17:22 — r/SideProject başlık kısıtı
- `[KANIT, operatör]` Reddit gönderi formunda: "You may not have "$" in your title." Bu kural üçüncü taraf takipçide yoktu. Otomatik kural olduğu için yalnızca form ekranında görünüyor.
- Düzeltme: "$0" ifadesi "zero-budget" ile değiştirildi. Metnin geri kalanı aynı. Bu kısıt ürünün r/SideProject satırına notu olarak eklenecek.

### 17:26 — r/SideProject gönderisi Reddit filtresine takıldı (R3 gerçekleşti)
- `[KANIT, operatör]` Ekranda "Sorry, this post was removed by Reddit's filters." yazıyor. Gönderi gizli sekmede de görünmüyor.
- `[ÇIKARIM]` Kaldıran moderatörler değil, Reddit'in site geneli spam/itibar filtresi. Yeni hesap ve link birleşimi buna yol açtı.
- Ajan kontrol edemiyor, Reddit eklenti tarafından engelli.
- **Kararlar:**
  1. **Yeniden paylaşım yok, yeni hesap yok, linksiz versiyonla filtreyi dolanmak da yok.** Üçü de görev kurallarındaki "kısıtları hileyle aşma" yasağına giriyor ve hesabın spam olarak işaretlenme riskini artırıyor.
  2. **r/SideProject moderatörlerine tek bir kibar modmail gönderilecek.** Filtreye takılan gönderiyi moderatörler elle onaylayabiliyor ve bu meşru bir yol.
  3. **Diğer sub'lardaki paylaşımlar bekletiliyor.** Aynı filtre büyük olasılıkla onlarda da çalışır. Art arda kaldırılan link gönderileri hesabın askıya alınma riskini artırır; hesap yasağı deneyin başarısızlığı demek. Modmail'e cevap gelene ya da gönderi onaylanana kadar bekleniyor.
  4. Bu birinci elden bulgu ürünün r/SideProject satırına işlendi: yeni hesap = restricted, "$" başlıkta yasak, Not-AI megathread'i var. Ücretsiz sayfa güncellendi.

### 17:26-17:40 — Modmail engeli; Bluesky, Launching Next ve Indie Hackers tarayıcıdan
- `[KANIT, operatör]` Modmail denemesinde "You can't message that user." uyarısı çıktı. Olası neden: URL alıcıyı kullanıcı olarak algıladı. Operatöre sub kenar çubuğundaki "Message the mods" butonu önerildi.
- Operatör Bluesky ve Indie Hackers hesaplarını açtı, bu süreçleri ajana devretti.
- **Bluesky** (`hferrahogludev.bsky.social`): Görünen ad ve Bio eklendi. Gönderi atılamadı: Bluesky e-posta doğrulaması istiyor, link hferrahoglu@gmail.com'a gitti. Doğrulama operatörde.
- **Launching Next:** Tüm alanlar dolduruldu (bülten kutusu kapatıldı, "A side project", $0). "Quick Check: What is 2+3?" bir bot kontrolü olduğu için ajan cevaplamadı. Sekme açık bırakıldı; cevap ve Submit operatörde.
- `[KANIT]` **Indie Hackers** (`HFerrahoglu`): Yeni hesap paylaşım yapamıyor. "You can't post just yet. Publishing is open to established members. Join in with a few thoughtful comments … or subscribe to IH+." Paylaşım izni için yorum biriktirmek karma kasmak olur, bu yüzden yapılmayacak.
- `[KANIT]` **Deney sırasında gelen bağımsız ihtiyaç sinyali (güçlü).** IH'de 2026-11-03 tarihli "I looked at 20+ launch directories for my free tool. Most wanted a link back or money." gönderisi: 32 upvote, 172 yorum. Yorumlardan:
  - "Launching Next quoted about 4 months, PeerPush put me at #5615"
  - "Hacker News refused the Show HN outright from a new account, and Reddit's filter removed the post in five minutes"
  - "one gave me a date in June 2027"
  - Gönderi sahibi: "check the excluded categories before you spend 20 minutes filling out the form"
  - Bunlar ürünün çözdüğü acının (gönderiden önce kuralları bilmek) başkaları tarafından da bağımsız olarak yaşandığını gösteriyor.
- Ürün verisi birinci elden kontrollerle güncellendi:
  - Indie Hackers satırı: yeni hesap kapalı, birincil kaynak.
  - Güncel ölçüm: yeni hesap + YZ metni + 24 sa + $0 için 27 kapalı / 22 çekinceli / 1 açık (önceki 26/23/1).
  - Gumroad küçük resmi ve ZIP güncel veriyle yenilendi. Eski ZIP içerikten kaldırıldı, tek dosya kaldı.
- IH için **tek bir yardımcı yorum** taslağı hazırlandı (`posts/6_ih_comment.md`). Herkese açık ve ajan yazdığı için operatör onayı bekleniyor.

### 17:43 — Operatör: Bluesky doğrulandı; IH yorumuna ONAY; yeni hesaplarda geçmiş kazanma serbest; "Quick Check'i sen yapabilirsin"
- **Kural güncellemesi (operatör):** Var olan bir hesapla geçmiş kazanmak yasak. Yeni açılan hesaplarda ise zorunluysa, uzun beklemeden geçmiş kazanılabilir.
  - Değerlendirmem `[KANIT + ÇIKARIM]`: IH'de bu yol pencereye sığmıyor. Aynı başlıktaki bir kullanıcı şöyle diyor: "commented 4 times (genuine ones, not spam!) 2 days ago and still locked out". Reddit'e ajan erişemiyor.
  - Karar: Geçmiş biriktirmek için yorum yapılmayacak. Yorumlar yalnızca ihtiyacın dile getirildiği, gerçekten yardımcı olunabilecek başlıklarda yapılacak.
- **Quick Check (Launching Next "What is 2+3?"):** Operatör izin verse de ajan bot kontrollerini ve CAPTCHA'ları çözmüyor. Bu, ajanın kendi güvenlik kuralı ve kullanıcı izniyle değişmiyor. Cevap ve Submit operatörde kalıyor (~20 sn).
- **Reddit:** Operatör "hâlâ olumsuz" dedi (gönderi kaldırılmış durumda, modmail gitmiyor). Reddit kanalı bu hesapla kapandı. Yeniden deneme yapılmayacak.
- Bluesky gönderisi yazılırken **Claude-in-Chrome eklentisinin bağlantısı koptu.** Bluesky zinciri ve onaylanan IH yorumu yayınlanmadı. Operatörden eklentiyi yeniden bağlaması istendi.

### 17:44-17:49 — Launching Next gönderildi, Bluesky ve IH yayında
- Eklenti bağlantısı geri geldi.
- **Launching Next:** Bot kontrolünü (2+3) operatör cevapladı, formu ajan gönderdi.
  - `[KANIT]` Sonuç sayfası: "Status: In Queue (Estimated Wait: 4 Months)". Hemen ardından $99 "Fast-Track" teklifi ("Only 3 express slots left this week") geldi. Satın alınmadı.
  - Bu birinci elden bulgu ürün verisine işlendi: Launching Next `time_to_visible: months`. Önceki "We review submissions every day" bilgisi yanıltıcıydı.
- **Bluesky:** İki gönderilik zincir yayında. Ana gönderi: https://bsky.app/profile/hferrahogludev.bsky.social/post/3mzl4casvi226 (`at://…/3mzl4casvi226`), açıklama yanıtı: `3mzl4dedpfs2h`. Metrikler herkese açık API'den okunabiliyor (getAuthorFeed).
- **Indie Hackers:** Operatörün onayladığı yorum, 172 yorumlu "I looked at 20+ launch directories…" gönderisine yazıldı. Sayfada görünüyor.

### 17:53 — Ara değerlendirme #1 (deneyin 2. saati)
**Metrikler** `[KANIT, METRICS.md]`:
- Sayfa yükleme: 3, demo: 1, satın alma tıklaması: 0. Hepsi "direct", kaynağı belirsiz. `selftest` hariç.
- Kanal ref'lerinden ziyaret yok. Bluesky 0 etkileşim, gönderi 12 dk önce yayınlandı. IH yorumu 10 dk önce yayınlandı.
- Launching Next kuyrukta, tahmini 4 ay. Reddit gönderisi filtrelendi.

**İşe yarayanlar:**
- Hızlı inşa: ürün 16:55'te yayındaydı, plandan ~3,5 sa önce.
- Her kanal denemesi ürünün verisine birinci elden bilgi ekledi: Reddit filtresi, "$" başlık kuralı, IH yeni hesap kilidi, Launching Next 4 ay.
- IH'deki 172 yorumlu başlık, sorunun gerçek ve güncel olduğunu bağımsız olarak doğruluyor.

**İşe yaramayanlar:**
- Dağıtım. Kurallara uyan kanalların çoğu yeni hesaba fiilen kapalı ya da çok yavaş.
- Ürünün tezi ("yeni hesap + YZ metni = çoğu kanal kapalı") deneyin kendi dağıtımında aynen gerçekleşti.

**Plan değişiklikleri:**
1. Reddit bu hesapla kapandı. Yeniden paylaşım, linksiz paylaşım ya da yeni hesap denenmeyecek.
2. IH ve Bluesky'da "yalnızca ihtiyacın açıkça dile getirildiği güncel başlıklara, başlık başına tek yorum" politikası uygulanacak. Aynı linki art arda birçok başlığa bırakmak yok.
3. DonanımHaber elendi: kendi sitene link "reklam" sayılıyor ve siliniyor (https://forum.donanimhaber.com/bolumde-yapilan-reklamlar-hakkinda--87352680).
4. Gece takibi için saatlik izleme cron'u (yalnızca okuma ve kayıt) ve 06/11 15:21 final rapor cron'u kuruldu. İkisi de yalnızca oturum açık kaldıkça çalışıyor.

**Dürüst beklenti** `[TAHMİN]`: Mevcut erişimle 24 saat içinde satış olasılığı düşük (tek haneli yüzde).

### 17:58 — Operatör: "Sen kendi kararlarına uygun devam edebilirsin." Ek kanal taraması
- **X (Twitter): ELENDİ.** `[KANIT, ikincil]`
  - Communities özelliğinin Mayıs 2026'da kapatıldığı bildiriliyor, kaynaklar çelişiyor (posteverywhere, autotweet, uniladtech).
  - Doğrulanmamış hesaplara günlük gönderi, yanıt ve takip sınırları getirilmiş (Mayıs 2026; deccanchronicle, propakistani).
  - Operatörün mevcut X hesabı görev kuralı gereği kullanılamıyor. 0 takipçili yeni hesap için doğrulanabilir bir erişim mekanizması yok. Operatörün 10 dakikasına değmez.
- **Değerlendirilip elenenler:**
  - HN link gönderimi: YZ metni yasağının ruhuna aykırı, yeni hesap gönderileri genelde ölü.
  - Quora: etkisi günler içinde görülür.
  - Discord #self-promo kanalları: link yığını, erişim çok düşük `[TAHMİN]`.
  - Medium: YZ etiketli hikâyeler yalnızca yazarın ağına dağıtılıyor, yeni hesabın ağı yok.
  - Lemmy (programming.dev): bot korumasıyla erişime kapalı.
- **Sonuç:** Kalan kanallar Bluesky, IH (yalnızca ilgili başlıklara tek yorum), Launching Next ve r/SideProject (moderatör onayı ihtimali, düşük). Zaman izlemeye, gelen her yoruma hızlı cevaba ve verinin birinci elden iyileştirilmesine ayrılacak.

### 18:00-18:14 — Operatör birkaç saat yok: "soru sorma ve duraklama işini daha az yap". Ürün iyileştirmesi
- Çalışma kuralı (kendi kararım):
  - Paylaşımlarımıza gelen yanıtlara cevap vermek, operatörün devrettiği Bluesky ve IH süreçlerinin parçası. Bunu kendim yapacağım.
  - Yeni başlıklara ilk yorum taslakta bekleyecek (`posts/pending_replies.md`).
  - Bot kontrolü ve CAPTCHA yok.
- **Ürün iyileştirmeleri** (dönüşümü artırmak için; kitle küçük olduğu için her ziyaretçi değerli):
  - "Tried with a new account" rozeti ve "What happened when we tried" notu dört kanalda: r/SideProject (filtre, "$" kuralı), IH (yeni hesap kilidi), Launching Next (4 ay), Bluesky (e-posta doğrulaması). Rakip listelerde olmayan birinci elden kanıt.
  - OG/Twitter meta etiketleri ve 1200×630 `og.png`. Link paylaşıldığında görsel kart çıkıyor.
  - Testler 44/44 geçti.
  - Bir kez başarısız testle push edildi (yeni not `.rule` sınıfını kullanıyordu), 2 dk içinde düzeltildi.
- Gumroad ZIP'i yeni sürümle değiştirildi (20,6 KB, tek dosya, sayfa yenilenerek doğrulandı).

### 18:24 — Saatlik izleme #1
- Toplam: direct 4 ziyaret, 1 demo, 0 satın alma tıklaması. Kanal ref'lerinden ziyaret yok.
- Bluesky ana gönderisi 5 beğeni aldı (biri `buildinpublicbot`; gerçek görünen hesaplardan biri OpenAlternative'in kurucusu kulpinski.dev). Linke tıklama ölçülmedi. Link ve kart `?ref=bsky` taşıyor, ölçüm tarafında hata yok.
- IH yorumu görünüyor, yanıt yok, başlık 176 yoruma çıktı. Cevaplanacak bir şey yok.

### 19:23 — Saatlik izleme #2
- Sayaçlarda değişim yok: direct 4/1/0, kanal ref'leri 0. Saat 18:22'den bu yana yeni ziyaret yok.
- Bluesky: 5 beğeni değişmedi. API `replyCount=2` diyor ama hem herkese açık thread'de hem giriş yapılmış sayfada tek yanıt (bizim 2/2 açıklama gönderimiz) görünüyor, bildirim yok. Muhtemelen silinmiş ya da moderasyonla gizlenmiş bir yanıt `[ÇIKARIM]`. Yeni takipçi: bir YZ bot hesabı.
- IH yorumu: 0 yanıt. Upvote öğesi `comment-voter--upvoted` sınıfı taşıyor, yani tek oy büyük ihtimalle IH'nin kendi yorumuna verdiği otomatik oy. 18:22 satırındaki "1 upvote" başkasından gelmiş sayılmamalı. Başlık 187 yoruma çıktı.
- `monitor.sh` düzeltmesi: abacus ara sıra "Failed to get data" dönüyor ve script bunu 0 yazıyordu (ilk okumada demo 1→0 görünmesinin nedeni). Artık 3 kez deniyor, başarısızsa `?` yazıyor.
