# Yeni hesapla 24 saatte dağıtım: platform araştırması

Tarih: 5 Kasım 2026, **Perşembe**. Yayın penceresi: 16:00–00:00 TR = 13:00–21:00 UTC = 08:00–16:00 ET. Metinler yapay zekâ ile taslaklanıyor, bir insan yayınlıyor ve bunu açıkça belirtiyor.

**Etiketler:** Linki olan cümleler doğrulanmış bilgidir. **(çıkarım)** = benim yorumum. **(tahmin)** = kaynağı olmayan kestirim. **doğrulanamadı** = birincil kaynağa ulaşamadım. **(ikincil)** = üçüncü taraf site (ör. rankhog, okara, prowlo); bunlar Reddit'in kural sayfasını Eylül–Ekim 2026'da okuduğunu söylüyor. Reddit sayfaları bu ortamdan doğrudan açılamadı.

**İki ana eleme kriteri:**
1. **Yapay zekâ metni yasağı.** HN, Stack Overflow, Product Hunt yorumları, r/webdev, r/SaaS, r/Entrepreneur ve r/InternetIsBeautiful YZ ile yazılmış metni açıkça yasaklıyor. "YZ kullandım" demek bu yasaktan muaf tutmuyor. Dev.to YZ makaleye izin veriyor ama bu makalede kendi ürününü tanıtmayı yasaklıyor.
2. **Gün ve saat.** Bugün Perşembe. r/webdev'de proje paylaşımı yalnızca Cumartesi (Showoff Saturday), r/selfhosted'da yeni projeler Cuma, Peerlist'te lansman Pazartesi yapılabiliyor. Bunların hiçbiri pencereye denk gelmiyor.

## 1. Özet tablo

| Platform | Yeni hesap kısıtı | Kendi ürününü tanıtma kuralı | YZ metni | 24 saatte görünürlük | Kayıt şartı | Kaynak URL |
|---|---|---|---|---|---|---|
| Hacker News | Show HN yeni hesaplara "geçici" kapalı | Ara sıra kendi işini paylaşmak serbest; Show HN için ürün denenebilir olmalı, kayıt sayfası olmamalı | **Yasak** | Yok | Kullanıcı adı ve şifre (e-posta zorunlu değil, çıkarım) | news.ycombinator.com/showlim |
| Reddit (site geneli) | Yayınlanmış karma eşiği yok; gizli spam filtresi ve CQS var | Kural her alt toplulukta (sub) ayrı; 9:1 resmi bir kural değil | Site genelinde yasak bulunamadı | Sub'a bağlı | E-posta ya da Google/Apple (çıkarım) | redditapis.com (aşağıda) |
| r/SideProject | Yayınlanmış alt sınır yok | **Yazılı kural yok**; topluluk proje paylaşmak için var | Kural yok | **Orta** | — | rankhog.com/subreddits/sideproject |
| r/InternetIsBeautiful | Son katılımının %90'ı kendi siten dışında olmalı; yeni hesap bu şartı fiilen karşılayamaz | Mağaza, ücretli ya da giriş/e-posta isteyen site yasak | **Yasak** | Yok | — | rankhog.com/subreddits/internetisbeautiful |
| r/webdev | Alt sınır yok | Yalnızca Cumartesi; ticari tanıtım her gün yasak | **Yasak** | Yok | — | rankhog.com/subreddits/webdev |
| r/SaaS | 60 günlük hesap (ikincil) | 60 günde 1 bahis ya da 3 link | **Yasak** | Yok | — | rankhog.com/subreddits/saas |
| r/Entrepreneur | Alt sınır yok | Tanıtım yasak | **Yasak** | Yok | — | rankhog.com/subreddits/entrepreneur |
| r/smallbusiness | Alt sınır yok | Yalnızca haftalık tanıtım konusunda | Kural yok | Yok | — | rankhog.com/subreddits/smallbusiness |
| r/indiehackers | Alt sınır yok | Ürün başına **1 kez**, "Self Promotion" etiketiyle, geri bildirim amaçlı | Kural yok | Düşük–Orta | — | rankhog.com/subreddits/indiehackers |
| r/alphaandbetausers | Alt sınır yok | Yazılı kural yok; ürün test edilebilir olmalı (ikincil) | Kural yok | Düşük–Orta | — | rankhog.com/subreddits/alphaandbetausers |
| r/IMadeThis | Alt sınır yok | Yazılı kural yok | Kural yok | Düşük (tahmin) | — | rankhog.com/subreddits/imadethis |
| r/coolgithubprojects | Alt sınır yok | Yazılı kural yok; yalnızca GitHub projeleri (ikincil) | Kural yok | Düşük–Orta | — | rankhog.com/subreddits/coolgithubprojects |
| r/selfhosted | Gönderi için 90 günlük hesap (ikincil) | 3 aydan genç projeler yalnızca megathread'de | Moderatörler YZ'yi artık denetlemiyor | Yok | — | rankhog.com/subreddits/selfhosted |
| r/Turkey, r/KGBTR | doğrulanamadı | doğrulanamadı | doğrulanamadı | Düşük (çıkarım) | — | — |
| Indie Hackers | Yeni ücretsiz hesap bir süre gönderi yapamıyor (ikincil) | doğrulanamadı | doğrulanamadı | Yok–Düşük | IH+ 198 $/yıl bu bekleme süresini kaldırıyor | profitablefounder.xyz |
| Product Hunt | Ürün göndermek için **1 hafta bekleme** | Kişisel hesap şart | YZ yorumu yasak | Yok | E-posta | help.producthunt.com |
| Dev.to | Yeni hesaplar spam filtresinde daha sıkı değerlendiriliyor | Gönderi asıl olarak tanıtım amaçlı olmamalı | Serbest, ama ifşa şart ve **kendi işini tanıtmak yasak** | Yok (YZ + tanıtım) | E-posta ya da GitHub | dev.to/guidelines-for-ai-assisted-articles-on-dev |
| Hashnode | doğrulanamadı | Yalnızca tanıtım yapan hesaplar yasak | Serbest, sorumluluk yazarda | Düşük (tahmin) | — | hashnode.com/code-of-conduct |
| Stack Overflow | doğrulanamadı | Ürünle bağını belirtmek zorunlu | **Yasak** | Yok | — | stackoverflow.com/help/gen-ai-policy |
| Ekşi Sözlük | Çaylak entry'leri herkese görünmüyor, linkleri tıklanamıyor; 10 entry'den sonra onay sırasına giriliyor | Reklam/spam kuralı (metni doğrulanamadı) | doğrulanamadı | **Yok** | E-posta, doğum tarihi, cinsiyet | eksisozluk.com/entry/66762977 |
| DonanımHaber | Telefon (SMS) onayı; telefonsuz yeni üyenin mesajı yönetici onayına düşüyor (eski bilgi) | Genel kurallarda açık bir reklam maddesi yok | Kurallarda madde yok | Düşük (tahmin) | E-posta ve telefon | forum.donanimhaber.com/rules.asp |
| Technopat Sosyal | Blog için 100 mesaj gerekiyor; yanıt vermeyen üyenin konusu onaylanmayabilir | Sunucu tanıtımı ve referans kodu yasak; ücretsiz proje paylaşan bir kullanıcı "reklam" uyarısı almış (anekdot) | Kurallarda madde yok | Düşük | doğrulanamadı | technopat.net/sosyal (kurallar) |
| Webmasterlar.net | Alan adı 5 Kasım'da çözümlenmiyor | — | — | Yok | — | — |
| R10.net | Ticari konu için ≥1 ay üyelik ve 5 itrader puanı, ya da ücretli üyelik | Ticari konu kurallarına bağlı | doğrulanamadı | Yok | E-posta | r10.net (kategori kuralları) |
| Bionluk | İlanlar yayından önce YZ destekli kontrolden geçiyor | Freelancer kaydı muhtemelen ücretli (69,90 TL, ikincil) | — | Yok (sıfır bütçe) | — | bionluk.com |
| BetaList | Ücretsiz inceleme "birkaç haftaya kadar" sürüyor | Hızlandırma ücretli | — | Yok | — | betalist.com/support |
| Uneed | Ücretsiz sırada **en az 50 gün** | 14,99 $ / 39,99 $ ile hızlanıyor | — | Yok | — | uneed.best/pricing |
| Microlaunch | Lansman 30 gün sürüyor; ücretsiz bekleme süresi doğrulanamadı | Pro ücretli | — | doğrulanamadı | — | microlaunch.net/premium |
| Peerlist | **Doğrulanmış profil** gerekiyor; pencere Pazartesi açılıyor | — | — | Yok | — | help.peerlist.io |
| AlternativeTo | Ücretsiz sırada tarih verilmiyor | Öncelikli inceleme ücretli | — | Yok | — | alternativeto.net/faq |
| SaaSHub | Rakip listelenmezse "kuyruğun sonuna" atılıyor | — | — | Yok (tahmin) | — | saashub.com/services/submit |
| Fazier | Ücretsiz: "30 gün içinde" + backlink şart | Ücretli seçenek anında yayın | — | Yok | — | fazier.com/submit |
| Tiny Startups | Her ilan elle onaylanıyor, süre belirtilmemiş | — | — | doğrulanamadı | — | tinystartups.com |
| There's An AI For That | Yalnızca YZ araçları; yaklaşık 49 $ (ikincil); site 403 verdi | — | — | Yok | — | doğrulanamadı |
| Launching Next | Ücretsiz; "her gün inceleriz", yayın garantisi yok | 99 $ ile 1 iş günü | — | Düşük | — | launchingnext.com/submit |
| OpenAlternative | doğrulanamadı | — | — | doğrulanamadı | — | openalternative.co/submit |
| Mastodon (mastodon.social) | Kayıt açık, onaysız, 16 yaş üstü | Kurallarda tanıtım maddesi yok | **İfşa şart**; yalnızca YZ içeriği paylaşan hesap yasak | Düşük–Orta (tahmin) | E-posta | mastodon.social/api/v1/instance/rules |
| Bluesky | Kurallarda yeni hesap kısıtı yok | Ticari içerik açıkça belirtilmeli | Genel bir kural yok | Düşük (tahmin) | E-posta; telefon şartı doğrulanamadı | bsky.social/about/support/community-guidelines |
| X/Twitter | Kayıtta SMS kodu istenebiliyor | — | doğrulanamadı | Düşük (tahmin) | E-posta ya da telefon | help.x.com |
| LinkedIn | doğrulanamadı | doğrulanamadı | doğrulanamadı | Çok düşük (0 bağlantı, tahmin) | — | — |
| Threads | Instagram/Facebook ile giriş; bağımsız kayıt kademeli açılıyor (ikincil) | — | — | Düşük (tahmin) | — | opentermsarchive.org |

## 2. Platform notları (kurallardan alıntılar)

**Hacker News**
- Gönderiler: "Please don't put generated text in HN posts." Yorumlar: "Don't post generated text or AI-edited text. HN is for conversation between humans." [Kılavuz](https://news.ycombinator.com/newsguidelines.html)
- [/showlim](https://news.ycombinator.com/showlim) sayfası: "We're temporarily restricting Show HNs".
- dang, Mart 2026: "We're going to at least restrict Show HNs for a while", ardından "Just new ones for now." [Yorum](https://news.ycombinator.com/item?id=47300772). Ekim 2026 tarihli bir rehber kısıtın hâlâ sürdüğünü yazıyor ([gtmhacker](https://gtmhacker.ai/guides/hacker-news-launch-guide/)).
- Show HN için: "Don't post landing pages or fundraisers." [Kurallar](https://news.ycombinator.com/showhn.html)
- **Sonuç: HN iki nedenle elendi.** Hem YZ metni yasak hem de Show HN yeni hesaplara kapalı.

**Reddit (site geneli)**
- Contributor Quality Score (CQS) 2023'ten beri moderatörlerin AutoModerator kurallarında kullanılabiliyor ([r/modnews](https://www.reddit.com/r/modnews/comments/16is6dh/)).
- En büyük 100 sub'ın 84'ünün kurallarında karma ya da hesap yaşı hiç geçmiyor. Ancak AutoModerator ayarları dışarıdan görünmüyor ([redditapis, 9 Eylül 2026](https://www.redditapis.com/blogs/subreddit-posting-requirements-measured-2026)).
- Haberlere göre Reddit, moderatörler istemedikçe YZ içeriğini toptan yasaklamıyor. Reddit'in resmi metnine ulaşamadım.
- **(çıkarım)** Yeni bir hesap birkaç saat içinde birden çok sub'a link atarsa site genelindeki spam filtresine takılabilir. Bu filtre gönderiyi sessizce gizler ve en büyük bilinmeyen budur.

**r/SideProject**
- 6 Mart 2026 arşiv kopyasında `rules` dizisi boş ([Wayback](https://web.archive.org/web/20260306124858/https://www.reddit.com/r/SideProject/about/rules.json)).
- rankhog 29 Eylül 2026'da da yazılı kural bulamamış.

**r/InternetIsBeautiful** (rankhog, 29 Ekim 2026)
- "90% of your recent participation on Reddit should have nothing to do with a site you own or operate."
- Ana içeriği YZ ile üretilmiş gönderiler kabul edilmiyor.
- 2018 arşivinde de şu kural var: "Online stores, paid services, or sites which serve only to sell a specific product."

**r/webdev**
- Kural 4: "We do not allow any commercial promotion or solicitation."
- Kural 8: "LLM generated posts or comments" kaldırılır.

**r/SaaS**
- "Max 1 mention or 3 links every 60 days." YZ ile üretilmiş metin, kendin kopyalayıp yapıştırsan bile yasak.

**r/Entrepreneur**
- "AI-generated posts or comments are not permitted."
- "Do not use this community to sell, promote, recruit… or drive traffic"

**r/indiehackers**
- "You can self promote your product only one time and you must use the Self Promotion flair." Nisan 2026 arşivindeki sürüm: "The purpose is for feedback and critique not advertisement." ([Wayback](https://web.archive.org/web/20260401023620/https://www.reddit.com/r/indiehackers/about/rules.json))

**r/alphaandbetausers**
- Başlıkta aşama ve platform etiketi bekleniyor (ör. "[Web, Beta]"). Yalnızca e-posta toplayan ya da "başvur" sayfası olan gönderiler kaldırılıyor ([okara, Ağustos 2026](https://okara.ai/blog/subreddits-that-allow-self-promotion)).
- **(çıkarım)** Buranın kitlesi alıcıdan çok test eden kullanıcı.

**r/coolgithubprojects**
- Yalnızca GitHub'da barınan projeler kabul ediliyor (okara). Mevcut GitHub hesabını kullanmak için uygun bir yer.

**r/selfhosted**
- Mart 2026 duyurusu: 3 aydan genç projeler yalnızca Cuma günü paylaşılabiliyor ve moderatörler YZ kullanımını artık denetlemiyor ([duyuru](https://www.reddit.com/r/selfhosted/comments/1rmt39o/)). Bugün Perşembe ve gönderi için 90 günlük hesap gerekiyor, bu yüzden elendi.

**Indie Hackers**
- "New free accounts wait through an anti-spam period before posting." ([25 Eylül 2026](https://www.profitablefounder.xyz/blog/is-indie-hackers-worth-it))
- 7 Ekim 2026 tarihli bir PR, giriş yapmış ama gönderi izni olmayan hesap durumunu ele alıyor ([GitHub](https://github.com/3956ray/ButtonPost/pull/29)).
- Bekleme süresi doğrulanamadı.

**Product Hunt**
- "you will need to wait one week before you can post a product." ([yardım sayfası](https://help.producthunt.com/en/articles/481909-how-can-i-get-access-to-post))
- Yorum kurallarında "AI-Generated Comments" kaçınılacaklar arasında: "No LLMs or Chrome extensions please!" ([yorum kuralları](https://help.producthunt.com/en/articles/10030102-commenting-guidelines))

**Dev.to**
- YZ makalelere izin var ama şunu yapmamalılar: "Promote any business, program, or course (including your own)." İfşa şart (#ABotWroteThis etiketi ya da not) ([kılavuz](https://dev.to/guidelines-for-ai-assisted-articles-on-dev)).

**Hashnode**
- "AI-generated content is permitted, but you must review and take responsibility for everything you publish." "primarily for self-promotion" kullanılan hesaplar yasak ([davranış kuralları](https://hashnode.com/code-of-conduct)).

**Stack Overflow**
- "Generative artificial intelligence … tools may not be used to generate content for Stack Overflow." ([politika](https://stackoverflow.com/help/gen-ai-policy))
- Tanıtım kuralı: "you must disclose your affiliation in your post." ([kural](https://stackoverflow.com/help/promotion))
- Link atmak için gereken itibar puanı doğrulanamadı.

**Ekşi Sözlük**
- SSS'ye göre 10 entry tamamlanınca onay sırasına giriliyor; sıra o gün giriş yapanlar arasında belirleniyor ([SSS](https://eksisozluk.com/entry/66762977)).
- Bir kullanıcı entry'si (2012): çaylak entry'leri "herkes tarafından görünen ekşi sözlük içeriğine dahil değil … web linkleri de tıklanamıyor" ([entry](https://eksisozluk.com/caylaklar--2289594)). Kuralın 2026'da da aynı olduğu çıkarımdır.

**DonanımHaber**
- [Genel kurallarda](https://forum.donanimhaber.com/rules.asp) reklam ya da YZ maddesi yok. İkinci el bölümünde "24 saat içersinde iki konu açmak yasaktır."
- SMS onayı ve yeni üye mesajlarının onaya tabi olması kullanıcı konularına dayanıyor ([örnek](https://forum.donanimhaber.com/gsm-no-dogrulama-hakkinda--25544757-8)); güncelliği doğrulanamadı.

**Technopat Sosyal**
- [Kurallar](https://www.technopat.net/sosyal/konu/technopat-sosyal-kurallari.3056861/): "Sunucu tanıtımı yapmak yasaktır." "Reklamlı link kısaltma servisi ve referans kod paylaşımı yapanlar siteden uzaklaştırılır." Blog için 100 mesaj gerekiyor.
- 2022 anekdotu: ücretsiz proje paylaşan bir kullanıcı "reklam" uyarısı ve ceza almış ([konu](https://forum.donanimarsivi.com/konu/technopat-konu-acamiyorum.585195/)).

**R10.net**
- Ticari konu için "en az 1 aylık üye olmalı", "minimum 5 ticaret ( itrader ) puanına sahip olmalı"; alternatifi ücretli Platin ya da Kurumsal üyelik (26 Temmuz 2025, [kategori kuralları](https://www.r10.net/toplu-script-satisi/4514130-toplu-script-satisi-kategori-kurallari.html)).

**Türkçe Discord/Telegram**
- Örneğin Quantum sunucusunun tanıtımında "Share your projects" yazıyor ([discord.me](https://discord.me/quantumdev)).
- Kurallar sunucuya göre değişiyor. Kuralları ve yeni üye kanal izinlerini doğrulayamadım.

**Mastodon (mastodon.social)**
- Kurallardan: "use of generative AI must be disclosed", "Accounts may not solely post AI-generated content." ([kurallar](https://mastodon.social/api/v1/instance/rules))
- `approval_required: false`, `min_age: 16` (API, 5 Kasım 2026).
- Operatör YZ kullanımını zaten açıkça belirttiği için bu kurallarla uyumlu.

**Bluesky**
- "Do not post undisclosed commercial content… or advertising" ([topluluk kuralları](https://bsky.social/about/support/community-guidelines)).

**Dizinler**
- [Uneed](https://www.uneed.best/pricing): "We assign your launch date, at least 50 days out."
- [Fazier](https://fazier.com/submit): "Reviewed & listed within 30 days."
- [Launching Next](https://www.launchingnext.com/submit/): "Submitting to Launching Next is free" ve "We review submissions every day."
- [AlternativeTo](https://alternativeto.net/faq/): "We can't give you a date."
- [SaaSHub](https://www.saashub.com/services/submit) gönderim sayfasında YZ ajanlarına, gönderimi insan operatörün yapmasını söyleyen bir not var. Operatör zaten insan olduğu için sorun değil.
- **(çıkarım)** 24 saat içinde gerçek trafik getirebilecek tek dizin Launching Next, o da garantili değil.

## 3. Yeni hesap için en iyi 5 kanal

Önce **yaklaşık 16 saat yanıt verilemeyecek** olmasının etkisi: Reddit'te gönderi sıralaması büyük ölçüde ilk saatlerdeki oylara bağlı ve gönderi sub'ın "hot" listesinde yaklaşık bir gün kalabiliyor (tahmin). Bu yüzden en sık sorulacak soruların cevabı (fiyat, gizlilik, "neden ücretli") baştan gönderi metnine yazılmalı (çıkarım). Her sub'a özgün metin yazılmalı ve gönderiler en az 60–90 dakika arayla yapılmalı (tahmin). Bu hem aynı metni çoklu paylaşma yasağına uyar hem de spam filtresi riskini azaltır.

1. **r/SideProject**: 13:00–14:30 UTC (08:00–09:30 ET).
   - Neden: Yazılı kural, karma ya da yaş sınırı ve YZ kuralı yok; topluluk kendi projeni paylaşmak için var (doğrulandı).
   - Risk: Site genelindeki gizli filtre.
   - ABD sabahı pencerenin başına denk geliyor ve gönderi ABD iş günü boyunca görünür kalıyor (tahmin).
2. **r/alphaandbetausers**: yaklaşık 15:00 UTC.
   - Neden: Kural yok, ürün tanıtımı topluluğun amacı.
   - Başlığa "[Web, Beta]" gibi bir etiket ekle; e-posta duvarı olmasın.
   - Alıcı niyeti düşük (çıkarım). Ücretsiz deneme ve ücretli yükseltme modeli buraya uyar.
3. **r/indiehackers**: yaklaşık 16:30 UTC.
   - Ürün başına tek hak; "Self Promotion" etiketi şart.
   - "Geri bildirim istiyorum" diye çerçevelenmeli. YZ kuralı yok.
4. **r/coolgithubprojects**: yaklaşık 18:00 UTC, ancak ürünün herkese açık bir GitHub reposu varsa.
   - Mevcut GitHub hesabıyla (13 takipçi) tutarlı. Repo aynı zamanda kalıcı bir tanıtım sayfası işi görür.
   - Kural yok (rankhog, 7 Ekim 2026).
5. **Mastodon (mastodon.social)**: pencere içinde herhangi bir saat.
   - Anında ve onaysız hesap. YZ ifşa kuralı operatörün dürüst beyanıyla örtüşüyor (doğrulandı).
   - Erişim hashtag'lere bağlı ve düşük–orta (tahmin). Etki büyük ölçüde ilk birkaç saatte (tahmin).

**Yedekler:**
- **Launching Next**: Ücretsiz; garanti yok.
- **r/IMadeThis**: Kural yok ama kitlesi küçük (tahmin).
- **DonanımHaber**: Türkçe için en makul aday. TR akşam saatleri (20:00–23:00, tahmin) pencere içinde. Ancak SMS onayı ve yönetici onayı riski var; reklam sayılma riski Technopat'tan düşük görünüyor (çıkarım).
- Ekşi Sözlük ve R10'un 24 saatte işe yaraması **mümkün değil**.

**En önemli tek kısıt:** Trafiği yüksek kanalların çoğu (HN, Stack Overflow, r/webdev, r/SaaS, r/Entrepreneur, r/InternetIsBeautiful, Product Hunt yorumları, Dev.to'da tanıtım) YZ ile yazılmış metni açıkça yasaklıyor ve ifşa bu yasaktan muaf tutmuyor. Geri kalanların çoğu da yeni hesabı süre şartıyla kapatıyor: Show HN kısıtı, Product Hunt'ta 1 hafta, r/SaaS'ta 60 gün, r/selfhosted'da 90 gün, R10'da 1 ay, Ekşi'de çaylaklık. Geriye birkaç kuralsız Reddit sub'ı ve Mastodon kalıyor. Bunlarda da asıl risk, Reddit'in yeni hesapları sessizce süzen ve dışarıdan görünmeyen filtresi.
