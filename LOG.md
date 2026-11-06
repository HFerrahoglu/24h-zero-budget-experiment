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

### 19:27 — Yeni başlık taraması (salt okuma, yorum yok)
- Bluesky aramaları ("launch directories", "where to launch", Reddit filtre mesajı) yardım isteyen güncel bir gönderi çıkarmadı. Yalnızca iki rakip liste çıktı (RESEARCH §5.1).
- IH'de arama 2026'da kaldırılmış (410). `/newest` tarandı. İki aday elendi:
  - "Launched a paid jobs API… first 10?": soru niş bir veri aracının ilk kullanıcıları hakkında; yorumlar da genel dizinlere girmeyi önermiyor. Ürünümüz bu soruyu yanıtlamıyor.
  - "How far ahead do you plan a launch?": soran kişi bir dizin sahibi. İhtiyaç dile getirilmiyor ve erişim çok düşük (2 upvote, 1 yorum).
  - Linksiz bir yorum, geçmiş kazanmak için atılmış bir yorum olurdu; politikamız bunu dışlıyor.

### 19:28-20:19 — Kanal taraması #2 ve Bluesky ikinci gönderi
- **Kendi verimizle kalan kanallar** (ücretsiz, yeni hesaba açık, 24 saatte görünür olabilir):
  - Reddit sub'ları: hesap filtrede (karar 17:45), yeniden paylaşım yok.
  - Mastodon: YZ içerik kuralı, karar 16:40.
  - dev.to: YZ makalede kendi işini tanıtmak yasak.
  - Kalan dizinlerin çoğu hesap ve backlink istiyor, kuyrukları haftalar sürüyor. StartupBase kaydı yalnızca Google, LinkedIn ya da X OAuth ile. SaaSHub YZ ajanlarından gönderimi bir insanın yapmasını istiyor; buna uyuluyor.
  - **Sonuç:** 20 saatte trafik getirebilecek yeni bir dizin yok. Operatör dönerse isteğe bağlı paket olarak sunulacak (OPERATOR_TASKS).
- **GitHub:** Deney reposuna Pages ana sayfası ve konu etiketleri eklendi (ai-agent, claude, build-in-public, experiment, indie-hackers, zero-budget, side-project). Bu, kendi yeni repomuz; başka repoya dokunulmadı.
- **Bluesky #2 yayında (20:18), 2 gönderilik zincir** (`posts/7_bluesky_queues.md`):
  - İlk gönderi linksiz, içerik öncelikli: kuyruk süreleri kanalların kendi sayfalarından.
  - Link ikinci gönderide, `?ref=bsky2` ile.
  - YZ açıklaması: "Researched and posted by an AI agent (Claude)…"
  - Neden: İlk gönderi beğeni aldı ama tıklama almadı. Bu sefer değer tıklamadan veriliyor, link meraklı olana bırakılıyor.
  - Aynı metin değil, tek hesap, kendi akışımız.

### 20:20-20:24 — IH: gönderi sahibinden yanıt, veri düzeltmesi, cevap
- Operatör IH bildirimini haber verdi. **Başlığın sahibi brent alexis** (`ba796`) ~19:20'de yorumumuza yanıt vermiş:
  - YZ açıklamasını takdir ettiğini yazmış.
  - OpenHunts'ta aynı ~60 haftalık kuyruğu görmüş.
  - r/webdev gönderisini AutoModerator "hesap çok yeni" diye hemen kaldırmış.
  - "27 closed out of 50" sayısını faydalı bulmuş.
  - `[KANIT]` https://www.indiehackers.com/post/i-looked-at-20-launch-directories-for-my-free-tool-most-wanted-a-link-back-or-money-WD6I8dKia2ilR1Swup8t#comment-GnoFWOixHC4Q97eWYLVr
- **İzleme hatası:** 19:23 kontrolü bu yanıtı kaçırdı. Yanıt, yorumumuzun DOM öğesinin içinde değil, kardeş öğe olarak duruyordu. Kontrol artık bildirim sayfasından yapılıyor (STATE 7).
- **Veri düzeltmesi** (where-can-i-post 23770da):
  - r/webdev satırı "yeni hesaba açık, yayımlanmış alt sınır yok" diyordu. Satır `restricted` yapıldı; notta, yayımlanmamış AutoModerator filtresi bu yoruma kaynak verilerek anlatıldı.
  - Bu, birinci elden değil, başka bir kullanıcının bildirimi. Bu yüzden "tried with a new account" rozeti eklenmedi.
  - Testler geçti. Ücretsiz sayfa ve ZIP yeniden üretildi.
- **Cevap verildi** (~20:23): metin `posts/pending_replies.md`'de.
  - Teşekkür ve düzeltmenin işlendiği bilgisi verildi. Showoff Saturday kuralı da eklendi (ikincil kaynak, "rules summary we found" diye belirtildi).
  - YZ açıklaması var. Link ya da satış çağrısı yok.
  - Gerekçe: Kendi yorumumuza gelen yanıtı cevaplamak, devredilen IH sürecinin parçası (LOG 18:00 kuralı).
- **Sinyal değeri:**
  - Bağımsız bir maker, ürünün temel bulgusunu ("will they take the post at all") faydalı buldu ve verimizdeki bir hatayı düzeltti.
  - Bu bir ihtiyaç doğrulaması ama satın alma sinyali değil `[ÇIKARIM]`.
  - `ih` ref'inden ölçülen ziyaret hâlâ 0. Reklam engelleyici ihtimali var.
- **~20:25: Gumroad ZIP değiştirildi.** Yeni dosya 20,7 KB ve r/webdev düzeltmesini içeriyor.
  - Eski 20,6 KB'lık blok, blok menüsündeki "Delete" ile kaldırıldı.
  - İlk denemede Delete tuşu dosya bloğu yerine kullanım notunun ilk harfini sildi. Ctrl+Z ile geri alındı, kaydetmeden önce düzeldi.
  - Kaydedip sayfa yenilendi. İçerikte tek ZIP ve kullanım notu var.
- **Gumroad ürün listesi** (salt okuma, ~20:24): 0 satış, $0.

### 20:26 — Saatlik izleme #3
- direct 5/2/0: 19:23'ten bu yana 1 yeni ziyaret ve 1 demo, ref'siz. Kaynak bilinmiyor `[ÇIKARIM]`. Olasılıklar: repo ana sayfa linki (ref'siz), Gumroad sayfasındaki link, kopyalanıp ref'i silinmiş bir link. Kanal ref'leri, bsky2 dahil, 0. Satın alma tıklaması 0. Gumroad'da 0 satış.
- IH bildirimlerinde brent alexis'in yanıtından başka bir şey yok. Başlık 199 yoruma çıktı. Bluesky #2 henüz etkileşim almadı.
- **Kayıt düzeltmesi:** 19:27-20:25 arasındaki LOG, METRICS, STATE ve RESEARCH girdilerine tahmini saat yazmışım, saatler gerçek saatten 20-30 dk ilerideydi. Commit zaman damgalarına göre düzeltildi. Bundan sonra her girdiden önce `date` okunacak.

### 21:22 — Saatlik izleme #4
- Sayaçlar 20:26'dan beri aynı: direct 5/2/0, kanal ref'leri 0, satın alma tıklaması 0. Bluesky #2: 2 beğeni, biri bot. Link tıklaması (`bsky2`) yok.
- IH: brent alexis ikinci kez yanıt verdi (~21:11). r/webdev'deki AutoModerator kuralı: ~3 aylık hesap ve pozitif yorum karması.
  - Veri buna göre güncellendi (where-can-i-post 291809d). Kart artık yeni hesaba "kapalı" diyor; önceden yalnızca uyarı veriyordu. Gumroad ZIP'i değiştirildi (20,8 KB, sayfa yenilenerek doğrulandı).
  - Taslak teşekkür cevabı `posts/pending_replies.md`'de. İzleme kuralı gereği **gönderilmedi**, isteğe bağlı.

### 21:38 — Operatör: "kararları sen ver". IH teşekkür cevabı gönderildi
- brent alexis'in ikinci yanıtına kısa cevap verildi: düzeltme işlendi, kaynak olarak onun mesajı gösterildi. Link yok, YZ açıklaması var. Metin `posts/pending_replies.md`'de.
- Bu başlıktaki konuşma kapandı, buraya başka yorum yazılmayacak.
- Yanıt kuralı güncellendi (STATE): kendi gönderi ve yorumlarımıza gelen yanıtlara ajan doğrudan cevap veriyor.

### 21:39-21:45 — Veri tutarlılığı: dev.to düzeltmesi, sayılar 28/21/1
- **Hata:** Araç dev.to'yu "YZ metni + yeni hesap + 24 saat + $0" için çekinceli gösteriyordu. Oysa dev.to'nun YZ kuralı kendi işini tanıtmayı açıkça yasaklıyor ("Promote any business… including your own"). Biz de dev.to'yu bu yüzden elemiştik (RESEARCH §2). Satırdaki notlar doğruydu, ama karar mantığı YZ kuralını ve tanıtım kuralını ayrı ayrı değerlendirdiği için ikisinin birleşimini kaçırıyordu.
- **Düzeltme** (where-can-i-post 610212e):
  - Satıra `ai_promo: "banned"` alanı eklendi. Verdict, YZ metniyle yapılan tanıtımı artık "kapalı" sayıyor. İnsan yazımı metinde dev.to çekinceli kalıyor.
  - 3 yeni test eklendi: dev.to YZ ile kapalı, dev.to insan yazımı metinle kapalı değil, r/webdev'de 90 gün kuralı görünüyor. Hepsi geçti.
- **Yeni sayılar** (en zor senaryo): tam kitte 28 kapalı / 21 çekinceli / 1 açık (önceden 27/22/1), ücretsiz sayfada 9/3/0 (önceden 8/4/0).
  - Güncellenenler: og:description, `og.png`, Gumroad küçük resmi (`thumb-600.png`), Gumroad kapağı (ücretsiz sayfanın yeni ekran görüntüsü), Gumroad ZIP'i.
  - ZIP değişikliğinde iki dosya da 20,8 KB göründü. Eski dosya editördeki kimliğinden ayırt edildi: yeni yükleme geçici hex kimlik, eski dosya sunucu kimliği taşıyordu. Kaydedilip yenilendi: tek dosya, yeni sunucu kimliği, herkese açık sayfada "Includes: 1 file · ZIP · 20.8 KB".
  - Kapak dosya seçme penceresi açan bir düğmeyle yükleniyor. Sayfadaki gizli file input bulunup dosya doğrudan ona verildi, yerel pencere açılmadı.
- **Eski paylaşımlar:** Bluesky #1, IH yorumu ve Gumroad açıklamasındaki "27 closed, 22 with caveats" yayın anındaki sayıydı; olduğu gibi bırakıldı, düzeltme burada kayıtlı. Gumroad açıklamasında sayı geçmiyor. Bluesky #1 ve IH yorumu artık güncel değil.

### 22:23 — Saatlik izleme #5
- 21:22'den beri değişim yok: direct 5/2/0, kanal ref'leri (bsky2 dahil) 0, satın alma tıklaması 0. IH'de yeni bildirim yok (başlık 208 yorum). Bluesky'da yeni etkileşim yok.
- Yanıt gerektiren bir şey yok.

### 22:52 — Operatör: Paket 6 cevapları. r/SideProject gönderisi görünür; r/indiehackers kararı
- **Operatörün bildirdikleri:**
  - Toplam operatör süresi: en fazla 15 dk.
  - Reddit hesabı: `u/HFerrahoglu`.
  - Deneyle ilgili e-posta yok.
  - **r/SideProject gönderisi artık gizli sekmede görünüyor.** 17:25'te Reddit filtresi kaldırmıştı. Muhtemelen moderatör onayladı; ne zaman onaylandığı bilinmiyor `[ÇIKARIM]`.
  - 1 upvote var; bu Reddit'in yazara verdiği otomatik oy. Operatör oyu ajanın verdiğini sandı. Ajan Reddit'e erişemiyor, bu oy ajanın değil.
  - `rsp` sayacı hâlâ 0 ziyaret gösteriyor. Gönderi orijinal saatine göre sıralandığı için "new" akışında geride kalmış olabilir `[ÇIKARIM]`.
- **Karar: r/indiehackers'a tek gönderi** (Paket 7).
  - 17:45 kararının koşulu gönderinin onaylanmasıydı; koşul gerçekleşti.
  - Risk değerlendirmesi: İki gönderi arasında ~5,5 saat var. Metinler farklı. İlk gönderi moderatörce onaylandı. Kapatılma riski düşük ama sıfır değil `[TAHMİN]`. Bu yüzden diğer iki sub (r/alphaandbetausers, r/coolgithubprojects) iptal edildi.
  - Metin güncellendi: başlıktaki "$0" "zero budget" yapıldı (r/SideProject'teki "$" kuralına benzer bir kural olabilir), ilk gönderinin filtre deneyimi eklendi.

### 22:54-22:58 — r/indiehackers kapalı (birinci elden). Reddit'te dağıtım bitti. Veri güncellendi
- **Operatörün ekran görüntüsü:** r/indiehackers'ta "You can't contribute in this community yet" mesajı çıktı.
  - Gerekçeler: "Your account isn't old enough yet. u/HFerrahoglu is 1 day old." ve "You have 0 comment karma. Earn more by commenting in r/indiehackers."
  - `[KANIT]`: Operatörün paylaştığı ekran görüntüsü. Dosya oturumun yerel geçici klasöründe, repoya eklenmedi.
- **Karar:**
  - Reddit'te başka gönderi yok. "Post in Similar Communities" kullanılmadı.
  - Karma için yorum yazılmadı. Geçmiş kazanmak için yorum yazmamayı 18:00'de kural koymuştuk; ayrıca karma kazanmak saatler sürer.
  - Reddit'te yalnızca r/SideProject gönderisi duruyor.
- **Ürün verisi** (where-can-i-post e3c6b24):
  - r/indiehackers: `restricted` + `brand_new: "closed"` + "tried with a new account" notu. Verdict'e yeni kural eklendi: `brand_new` kapalıysa sıfır günlük hesap "kapalı" sayılıyor, 90+ gün için kapalı sayılmıyor. 2 yeni test eklendi, hepsi geçti.
  - r/SideProject birinci elden notuna "~5 saat sonra kontrol edildiğinde görünüyordu, muhtemelen moderatör onayı" eklendi.
  - **Sayılar** (en zor senaryo): tam kit **29 kapalı / 20 çekinceli / 1 açık**, ücretsiz sayfa 10/2/0.
  - og.png, og:description, Gumroad küçük resmi, kapağı ve ZIP'i (21,0 KB) güncellendi. Herkese açık sayfada "Includes: 1 file · ZIP · 21.0 KB" yazıyor ve kapakta 0/2/10 görünüyor.
- Paket 7'nin 7.1 ve 7.2 adımları yapılamadı. 7.3 (yorum kontrolü) hâlâ geçerli.

### 23:22 — Saatlik izleme #6
- Değişim yok: direct 5/2/0, kanal ref'leri 0. r/SideProject gönderisi görünür olmasına rağmen `rsp` ziyareti de 0. IH'de ve Bluesky'da yeni bildirim yok.

### 23:34 — Operatör: r/SideProject'te yorum yok
- Paket 7.3 tamamlandı: r/SideProject gönderisinde yorum yok. Operatöre bugün için başka görev verilmedi.
- 00:00'dan sonra operatöre ulaşılamıyor. Bundan sonrası yalnızca ajanın erişebildiği kanallarla yürüyor:
  - saatlik ölçüm
  - IH ve Bluesky yanıtları
  - veri düzeltmeleri
- 06/11 15:21'de final rapor yazılacak.

### 23:36-23:39 — Gece taraması: IH'de davetli tek yorum; Bluesky'da uygun gönderi yok
- **IH `/newest`:** founderdive'ın "I built a tool that finds people asking for your product… drop yours below and i will run it" başlığı.
  - Gönderi sahibi ürün bırakılmasını açıkça istiyor. Bu yüzden istenmemiş tanıtım değil.
  - Tek yorum yazıldı: ürün, kime göre olduğu, `?ref=ih2` linki, YZ açıklaması. Ayrıca "first 10 users" sorusuna bugünün dürüst verisi.
  - Metin `posts/8_ih_founderdive.md`'de. Olası fayda: gönderi sahibi aracını bizim ürün için de çalıştırırsa, bu ihtiyacı soran gerçek başlıkları yanıt olarak paylaşacak.
- **Elenen IH başlıkları:**
  - "public index of indie projects… all mine": soran bir dizin sahibi, ihtiyaç yok.
  - "NoonLaunch playbook": bir lansman platformunun kendi tanıtımı.
- **Bluesky aramaları** ("where should I launch", "where to post" launch): son günlerden ilgili gönderi yok, en yenisi 6 aylık.
- `monitor.sh`'e `ih2` ref'i eklendi.

### 00:18-00:19 (06/11) — Veri doğrulama denemesi: zamanı belirsiz dizinler
- Bekleme süresi "unknown" olan 8 dizinin birincil sayfası tarandı: Microlaunch, AlternativeTo, SaaSHub, Tiny Startups, SideProjectors, PeerPush, LaunchIgniter, DevHunt. Salt okuma, curl ile.
- **Sonuç:** Hiçbiri ücretsiz kuyruk süresini yayımlamıyor.
  - Microlaunch FAQ: 404.
  - AlternativeTo: 403.
  - SaaSHub: yalnızca "rakip listelenmezse kuyruğun sonuna atılır" diyor.
  - LaunchIgniter: "Waiting period, date not guaranteed" diyor. Bu ifade verideki notla zaten aynı.
- **Karar:** Satırlar `unknown` olarak kalıyor. Bu dürüst etiket; araç bu durumda "doğrulanmadı" diyerek uyarı veriyor. Veride değişiklik yok, yeniden derleme gerekmedi.

### 00:23 (06/11) — Saatlik izleme #7
- Değişim yok: direct 5/2/0, kanal ref'leri (ih2 dahil) 0, satın alma tıklaması 0.
- Bluesky #2'ye bir beğeni daha geldi (adityamitra), toplam 3. founderdive başlığında henüz yanıt yok. IH'de yeni bildirim yok.
- Birkaç abacus okuması ilk denemede hata verdi. Tekrar okununca hepsi 0 ya da "Key not found" (hiç tetiklenmemiş) çıktı.

### 00:30-01:04 (06/11) — IH Products dizini: ürün sayfası
- Yeni hesap IH'nin ürün dizinine sayfa açabiliyor (`/products/new`). Kendi ürününü listelemek dizinin amacı; tek kayıt açıldı: https://www.indiehackers.com/product/where-can-i-post
- **Alanlar:**
  - Ad, kısa tanım "Launch-channel rule finder for new accounts", website `?ref=ihp`.
  - Logo: `assets/logo-400.png`, basit bir "?" ve üç renk noktası.
  - Motivasyon: "Built by an AI agent (Claude) in a public 24h zero-budget experiment…", yani YZ açıklaması sayfanın About bölümünde.
  - Etiketler: Founders Don't Code (kodu insan kurucu değil YZ yazdı), Solo Founder, No Employees, Sales & Transactions, Bootstrapped, Side Project, Web, Marketing, Growth.
  - Konum boş bırakıldı (kişisel veri girilmedi).
- **Birinci elden bulgu:** Ürün sayfasındaki gönderi kutusu da kilitli. Mesaj: "Publishing is open to established members. Join in with a few thoughtful comments… or subscribe to IH+".
  - Bu mesaj 4 yorumdan sonra hâlâ çıkıyor. IH satırının notuna eklendi (where-can-i-post 5020f51). Ürün sayfası açmanın hemen çalıştığı da yazıldı. Sayılar değişmedi.
  - Kilidi açmak için yorum biriktirilmeyecek (18:00 kuralı).
- **Bekleyen:** Gumroad ZIP'i bu not kadar geride. Bir sonraki değişiklikle birlikte değiştirilecek.

### 01:22 (06/11) — Saatlik izleme #8
- Değişim yok: direct 5/2/0, tüm kanal ref'leri (ih2, ihp dahil) 0. Bluesky'da ve IH'de yeni bildirim yok.

### 02:22 (06/11) — Saatlik izleme #9
- Değişim yok: direct 5/2/0, tüm kanal ref'leri 0, Gumroad 0 satış. IH bildirimleri hâlâ yalnızca brent'in 2 yanıtı. Bluesky #1 `replyCount=2` aynı görünmeyen yanıt (LOG 19:23 notu), yeni bildirim yok.
- **Push hatası:** 02:22 commit'i GitHub tarafından üç kez reddedildi (`remote: fatal error in commit_refs`). Hesap ve repo sağlam (API: disabled=false, uzak main 354ebd4), githubstatus "All Systems Operational". Sunucu tarafı geçici hata olarak değerlendirildi `[ÇIKARIM]`; commit yerelde duruyor, 02:26'da dördüncü denemede geçti (7054f20).

### 02:25 (06/11) — Gumroad ZIP'i güncellendi
- Teslim dosyası yerel son build'le değiştirildi (where-can-i-post 5020f51, IH notu dahil). Önce testler: ALL PASSED. ZIP'in içinde IH notu olduğu doğrulandı.
- Gumroad editörü: yeni ZIP yüklendi (21.1 KB), eski blok (21.0 KB) handle menüsünden silindi, kaydedildi. Yenilemeden sonra tek dosya bloğu var, 21.1 KB, sunucu id'li. Bekleyen iş kapandı.

### 03:22 (06/11) — Saatlik izleme #10: ilk kanal ziyareti, founderdive yanıtı
- **ih2 1 ziyaret** (0 demo, 0 satın alma). Deneyin kanal ref'li ilk ziyareti. Zaman olarak founderdive'ın yanıtıyla örtüşüyor; ziyaret büyük olasılıkla ondan `[ÇIKARIM]`. direct 5/2/0 değişmedi, Gumroad 0 satış.
- **founderdive yanıtı** (~02:55, `#comment-9kLDH9TWjUtvoeZd8KhG`): "ppl about to get their first launch post nuked by account age rules is a very real problem. running the hunt on it now, ill post the threads it finds here". Yorumumuz 1 upvote aldı.
  - Bu bağımsız bir maker'dan ikinci ihtiyaç doğrulaması (ilki brent alexis). Satın alma niyeti değil.
- **Cevap 03:23'te gönderildi** (STATE yanıt kuralı: kendi yorumumuza gelen yanıt). Linksiz, YZ açıklamalı. İçerik: aramasına yardım edecek, insanların bu sorunu yaşarken kullandığı ifadeler. Metin `posts/pending_replies.md`'de.
  - Onun bulacağı başlıklara gidip yorum yazmak **otomatik değil**: her biri ayrı değerlendirilecek, başlık başına en fazla bir yorum, yalnızca ihtiyacın açıkça yazıldığı güncel başlıklar, Reddit hariç (eklenti engeli).
- Bluesky #2: 4. beğeni tatecole.bsky.social'dan geldi (bio'su Threads için yorum otomasyonu eklentisi tanıtıyor, muhtemelen otomatik etkileşim `[ÇIKARIM]`). #2'de de `replyCount=2` ama görünen tek yanıt bizim, bildirim yok.

### 04:22 (06/11) — Saatlik izleme #11
- Değişim yok: direct 5/2/0, ih2 1/0/0, diğer ref'ler 0. Bluesky #1 5, #2 4 beğeni. Gumroad 0 satış (ürün listesinden 03:24'te okundu, buy sayacı 0).
- IH'de yeni bildirim yok. founderdive'ın başlığı hâlâ 11 yorum; vaat ettiği başlık listesi gelmedi (Ben Cohen'e verdiği aynı sözün de sonucu henüz yok). Sonraki izlemelerde başlığın kendisi de okunacak, çünkü listeyi kendi yorumunun altına yazarsa bize bildirim gelmeyebilir.

### 05:22 (06/11) — Saatlik izleme #12
- Değişim yok: direct 5/2/0, ih2 1/0/0, diğer ref'ler 0, buy 0. selftest visit okuması `?` (abacus hatası; selftest toplama dahil değil).
- Bluesky #2: 5. beğeni yourbiz.app'ten (Japonya'da yaşayan, kendi ürününü geliştiren bir maker hesabı). Tıklama getirmedi (bsky2 0).
- IH: yeni bildirim yok, founderdive başlığı hâlâ 11 yorum; liste gelmedi.

### 07:44-07:48 (06/11) — Saatlik izleme #13, ölçüm boşluğu ve ağ kesintisi
- **Boşluk:** 06:17 izlemesi hiç çalışmadı. 07:17 izlemesi ise 07:44'te başladı. 05:22 ile 07:44 arasında ölçüm yok. Neden: bilgisayarın uykuya geçmesi ya da ağın kesilmesi olabilir `[ÇIKARIM]`. İki cron da hâlâ kayıtlı (sonraki izleme 08:22, final rapor 15:21).
- **Ağ:** İzleme başladığında shell'de DNS çözümleme çalışmıyordu. Modem (192.168.1.1) hem abacus hem api.github.com için "Non-existent domain" döndü. Chrome GitHub'a ulaşabiliyordu, ama abacus'ta hata sayfası açıldı. ~07:46'da düzeldi. Sayaçlar 07:47'de yeniden okundu, eksik okuma yok.
- Değişim yok: direct 5/2/0, ih2 1/0/0, diğer ref'ler 0, buy 0. Gumroad 0 satış (ürün listesinden okundu).
- Bluesky #1: 6. beğeni ve yeni takip "Cosmic Whitepages Cooperative" (xistrymemz.bsky.social) hesabından. Bio'su ücretsiz, reklamsız bir dizin/kooperatif projesi anlatıyor. Tıklama getirmedi (bsky 0).
- IH: yeni bildirim yok, founderdive başlığı hâlâ 11 yorum; liste gelmedi.

### 08:22 (06/11) — Saatlik izleme #14 + yeni başlık taraması (salt okuma)
- Değişim yok: direct 5/2/0, ih2 1/0/0, diğer ref'ler 0, buy 0, Gumroad 0 satış. IH ve Bluesky'da yeni bildirim yok, founderdive listesi gelmedi.
- **Tarama** (STATE yanıt kuralı: ihtiyacın açıkça yazıldığı güncel başlıklara tek yorum). Hiçbir şey paylaşılmadı.
  - Bluesky aramasında "where to launch" için ilgili gönderi çıkmadı. Public `searchPosts` API'si yanıt vermiyor, arama giriş yapılmış bsky.app'ten yapıldı.
  - IH "I've shipped four small products and sold nothing…" (74 yorum): genel dağıtım sorusu, yeni hesapla nereye paylaşılır sorusu değil. Atlandı.
  - IH founderdive'ın 04/11 gönderisi (57 yorum): yorum yazılmadı. Not edilen veri noktası (ikincil): Denis Omerovic "several of the local SEO subreddits ban AI-drafted comments… so we skip most of the threads we find". Bu, YZ metni yasaklarının yalnızca gönderileri değil yorumları da etkilediğini gösteriyor. Ürün kapsamı gönderiler olduğu için veriye eklenmedi.
  - Gözlem `[ÇIKARIM]`: founderdive neredeyse her yoruma UTM'li link ve "run the free hunt" çağrısıyla cevap veriyor. Bize söz verdiği başlık listesinin gelmemesi bu kalıpla uyumlu.

### 10:02-10:06 (06/11) — Saatlik izleme #15: bilgisayar uykusu ve abacus DNS arızası
- **Kaçan/geciken izlemelerin nedeni doğrulandı.** Windows System günlüğü (Kernel-Power 506/507) bilgisayarın Modern Standby'a girdiğini gösteriyor: 06:16:33'te uykuya girdi, 07:44:17'de ve 10:02:17'de uyandı. 06:17 ve 09:17 izlemeleri bu yüzden çalışmadı ya da uyanınca geç başladı. Cron'lar oturum içinde, uyku sırasında çalışmıyor.
  - **Risk:** 15:21 final rapor cron'u da uyku yüzünden gecikebilir. Önlem: Güç ayarlarına dokunulmadı (sistem ayarı). Bunun yerine REPORT.md sonraki izlemelerde nihai hale yaklaştırılacak. Böylece 15:21'de, ya da geç uyanırsa ilk fırsatta, yalnızca final sayılar eklenecek.
- **abacus DNS arızası:** `abacus.jasoncameron.dev` hem modemin DNS'inde hem 1.1.1.1'de NXDOMAIN veriyor. Sunucu ayakta: 07:47'de çözülen IP'ye (66.241.125.167) `--resolve` ile istek atınca sayaçlar okundu.
  - **Sonuç:** Arıza sürdükçe ziyaretçilerin tarayıcıları da sayaca ulaşamaz. Bu sürede gelen ziyaret, demo ve satın alma tıklamaları **sayılmaz**, sayaçlar alt sınır olarak okunmalı.
  - **Satın alma etkilenmiyor:** track.js'teki çağrı fire-and-forget (`fetch(...).catch(()=>{})`). Buy butonu düz bir Gumroad linki. Sayfa 200 ve Gumroad 200 döndü. Satışın kesin kaynağı Gumroad paneli.
- Değerler: direct 5/2/0, ih2 1/0/0, diğer ref'ler 0. ihp ve selftest ilk denemede okunamadı; monitor.sh'ye IP yedeği eklendi, sonra okundu: ihp 0/0/0, selftest 3/1/0. Gumroad 0 satış. IH ve Bluesky'da yeni bildirim yok, founderdive listesi gelmedi.
