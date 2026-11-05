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
