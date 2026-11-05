# OPERATOR_TASKS — Operatörden istenen işler

Kurallar: Her görevde numaralı adımlar, tam linkler ve tahmini süre var. Her görevin sonunda **"Bana geri bildirin"** başlığı altında neyi yazmanız gerektiği belirtilmiş. Şifre, doğrulama kodu ve token'ları **bana ya da herhangi bir dosyaya yazmayın**.

Operatör penceresi: yalnızca 16:00-00:00 (bugün). Toplam bütçe: en fazla 480 dk.

## Süre takibi

| Paket | Verildiği saat | Tahmini süre | Gerçek süre (operatör yazar) | Durum |
|---|---|---|---|---|
| Paket 1 | 16:16 | ~15 dk | | Bekliyor |
| Paket 2 | 16:30 | ~14 dk | | Bekliyor |
| Paket 3 | 16:55 | ~20 dk | 3.1'i ajan yaptı (operatör izniyle tarayıcıdan) | 3.1 ✅ 17:14 · 3.2 (Launching Next) operatörde: bot kontrolü var |
| Paket 4 | 16:55 (saatleri içinde) | ~10 dk/paylaşım + cevaplar | | Bekliyor |
| **Toplam** | | | | |

---

## PAKET 1 — 16:16 (tahmini toplam: ~15 dk)

Bu paketin amacı şunu netleştirmek: ödemeyi nereden alacağız? Ruul Space kapatılmış görünüyor (kanıtlar LOG.md 16:05 kaydında). Kalan her şey buna bağlı.

### Görev 1.1 — Ruul panelinde bilgi kontrolü (~3 dk)
1. Ruul hesabınıza her zamanki gibi giriş yapın (https://ruul.io → Log in).
2. Ana menüdeki (sol menü ya da üst menü) başlıkları sırayla bana yazın. Örnek: "Dashboard, Invoices, Customers, Subscriptions, …".
3. Menüde **"Space"**, **"Mağaza/Store"**, **"Products/Ürünler"** ya da **"Payment link/Ödeme linki"** gibi bir başlık var mı? Varsa tıklayın ve açılan sayfadaki ana mesajı aynen yazın.
4. **Hiçbir ayarı değiştirmeyin.** Ödeme hesabı, kimlik ve para çekme bölümlerine girmeyin.

**Bana geri bildirin:** (a) menü başlıkları, (b) Space veya ürün satışı bölümü var mı, varsa sayfada ne yazıyor.

### Görev 1.2 — Kural gereği onay: alternatif ödeme sağlayıcısı (~1 dk)
Görev kuralı şöyle diyor: "Ruul yetersiz kalırsa bunu kanıtıyla LOG.md'ye yaz, alternatifi ancak ondan sonra öner." Kanıt LOG.md'de (16:05). Önerim:

> **Gumroad** (https://gumroad.com). Neden: Tanımadığımız bir alıcı gece saatlerinde operatöre ihtiyaç olmadan ödeme yapıp ürünü otomatik olarak alabilmeli. Ruul'da bunu sağlayan bir yol yok, yalnızca müşteri başına elle fatura kesilebiliyor. Gumroad'un kurulum ücreti ve kart şartı yok. Satış başına %10 + $0.50 kesiyor. Türkiye'ye TRY olarak banka ödemesini destekliyor (kaynaklar LOG.md 16:09 kaydında).
>
> Not: Bu deney sırasında sizden ödeme hesabı, banka ya da kimlik bilgisi girmenizi **istemeyeceğim**. Bunlar Gumroad'da ilk satış için gerekmiyor. Para çekmek isterseniz bu, deney sonrasında tamamen sizin kararınız.

**Bana geri bildirin:** `ONAY` ya da `RET`. RET gelirse Plan B'ye geçerim: Ruul'dan elle fatura, ürün "dijital hizmet" olarak tasarlanır.

### Görev 1.3 — Yeni hesap talebi: Gumroad (yalnızca 1.2'ye ONAY verdiyseniz, ~8 dk)
- **Platform:** Gumroad
- **Neden:** Kendi kendine ödeme ve dijital ürünün otomatik teslimi (dosya, link veya lisans anahtarı).
- **Önerilen kullanıcı adı:** `hferrahoglu` (alınmışsa `hferrahoglu-tools`)
- **Görünen ad:** Gerçek adınız, Hamza Ferrahoğlu. Sahte kişilik kullanmıyoruz.
- **Profil metni (Bio) — kopyalayın:**
  ```
  Small, focused software tools. Built by an AI agent (Claude) with me as the human operator, as part of a public 24-hour experiment.
  ```
- **Profil fotoğrafı:** Boş bırakın ya da kendi gerçek fotoğrafınızı kullanın. Yapay zekâyla üretilmiş görsel kullanmayın.

Adımlar:
1. https://gumroad.com/signup adresine gidin ve **hferrahoglu@gmail.com** ile e-posta kaydı yapın. Şifreyi kendiniz belirleyin, bana yazmayın.
2. Gmail'e gelen doğrulama e-postasındaki linke tıklayın.
3. Profil/ayarlar bölümünde kullanıcı adını, görünen adı ve Bio'yu yukarıdaki gibi girin.
4. **Ödeme/banka/kimlik bilgisi GİRMEYİN.** Gumroad ürün yayınlamak için bunları zorunlu tutuyorsa durun ve ekrandaki mesajı aynen bana yazın.
5. "Products" → "New product" ekranını açın. Sunulan ürün türlerini (ör. Digital product, Course, Ebook, Membership…) bana yazın. **Henüz ürün oluşturmayın.**

**Bana geri bildirin:** (a) hesap açıldı mı, (b) kesinleşen kullanıcı adı ve profil URL'si, (c) ürün yayınlamadan önce ödeme/kimlik bilgisi isteyen bir ekran çıktı mı, (d) ürün türleri listesi, (e) kayıt sırasında karşılaştığınız kısıtlar (telefon doğrulaması, CAPTCHA, inceleme bekleme süresi vb.).

### Görev 1.4 — Bilgi sorusu (~10 sn)
06/11 sabahı (00:00-16:00 arası) ulaşılabilir misiniz? Görev metnine dayanarak **hayır** varsayıyorum ve planı buna göre kuruyorum (LOG.md 16:12).

**Bana geri bildirin:** `Evet` / `Hayır`

---

## PAKET 2 — 16:30 (tahmini toplam: ~14 dk)

Kanal araştırmasının sonucu (RESEARCH.md §2): Yapay zekâ ile yazılmış metni yasaklamayan ve yeni hesaba kapalı olmayan kanallar yalnızca birkaç İngilizce Reddit topluluğu. HN, Product Hunt, Stack Overflow ve Shopify Community'yi bu yüzden kullanmıyoruz. Bu paketin amacı tek bir Reddit hesabı açmak ve hedef toplulukların kurallarını sizin gözünüzle doğrulamak. Reddit bu ortamdan erişimime kapalı: curl 403 dönüyor, tarayıcı eklentisi de engelliyor.

### Görev 2.1 — Yeni hesap talebi: Reddit (~6 dk)
- **Platform:** Reddit
- **Neden:** r/SideProject, r/indiehackers, r/alphaandbetausers ve r/coolgithubprojects'te paylaşım yapmak için.
- **Önerilen kullanıcı adı:** `hferrahoglu` (alınmışsa `hferrahoglu_dev`)
- **Profil "About" metni (177 karakter) — kopyalayın:**
  ```
  Human operator of a public 24h experiment: an AI agent (Claude) builds one small tool. Agent drafts posts, I publish them. Log: github.com/HFerrahoglu/24h-zero-budget-experiment
  ```
- **Avatar:** Varsayılan kalsın. Yapay zekâyla üretilmiş görsel kullanmayın.

Adımlar:
1. https://www.reddit.com/register adresinde **hferrahoglu@gmail.com** ile kaydolun. Şifreyi kendiniz belirleyin, bana yazmayın.
2. Gmail'e gelen doğrulama e-postasıyla e-postanızı doğrulayın.
3. Kullanıcı adını yukarıdaki gibi seçin.
4. Ayarlar → Profile → "About" alanına yukarıdaki metni yapıştırın.
5. **Hiçbir şey paylaşmayın, yorum yapmayın, oy vermeyin ve toplu olarak topluluğa katılmayın.** Karma kasmak deney kurallarına aykırı.

**Bana geri bildirin:** (a) kesinleşen kullanıcı adı, (b) telefon doğrulaması, CAPTCHA ya da başka bir engel çıktı mı, (c) hesap açılış saati.

### Görev 2.2 — Hedef toplulukların kurallarını kontrol (~8 dk)
Hesapla giriş yapmış hâlde aşağıdaki 5 topluluğun her biri için:
1. Topluluk sayfasını açın:
   - https://www.reddit.com/r/SideProject/
   - https://www.reddit.com/r/indiehackers/
   - https://www.reddit.com/r/alphaandbetausers/
   - https://www.reddit.com/r/coolgithubprojects/
   - https://www.reddit.com/r/IMadeThis/
2. Sağ kenar çubuğundaki **"Rules"** bölümünü açın. Kural başlıklarını yazın. Özellikle şu konulara dikkat edin: kendi ürününü tanıtma, yapay zekâ, hesap yaşı/karma, link ve etiket (flair). Kural yoksa "kural yok" yazın.
3. O topluluğun içinde **"Create Post"**a tıklayın, ama **paylaşmayın**. Şunlardan biri çıkarsa yazın: "karma yetersiz", "hesap çok yeni", zorunlu etiket (flair) listesi ya da başka bir uyarı. Sonra paylaşmadan kapatın.

**Bana geri bildirin:** Her topluluk için (a) kuralların özeti, (b) "Create Post" ekranındaki uyarılar ve (c) varsa zorunlu flair seçenekleri.

---

## PAKET 3 — 16:55 (tahmini ~20 dk) · yalnızca 1.2'de ONAY verdiyseniz

Ürün hazır ve test edildi:
- Ücretsiz sürüm: https://hferrahoglu.github.io/where-can-i-post/
- Repo: https://github.com/HFerrahoglu/where-can-i-post
- Ürünün kendisi: lansman yapanlara, yeni hesapla ve YZ destekli metinle hangi kanalın paylaşımı kabul edeceğini, kuralı ve kaynağıyla gösteren bir araç. Ücretli kit $7.

Bu paket Gumroad'da ürünü kuruyor. Gumroad linki çalışmadan Reddit paylaşımı yapamayız, çünkü satın alma butonu boşa çıkar.

### Görev 3.1 — Gumroad'da ürünü oluşturun (~12 dk) · ✅ AJAN YAPTI (17:14, operatör ONAY'ı ile)
**Yüklenecek dosya (bilgisayarınızda):** `C:\Users\hferr\Desktop\24HourChallenge\product\dist\where-can-i-post-full-kit.zip` (20 KB)
**Kapak görseli:** `C:\Users\hferr\Desktop\24HourChallenge\product\assets\screenshot-free.png`

1. Gumroad → **Products** → **New product**.
2. **Name** alanına kopyalayın:
   ```
   Where Can I Post? Full Kit: 50 launch channels checked for new accounts & AI-assisted posts (Nov 2026)
   ```
3. Tür olarak **Digital product** seçin.
4. **Price:** `7` (USD). Pay-what-you-want açmayın.
5. **Next / Customize** → **Description** alanına aşağıdaki metni yapıştırın:
   ```
   Most launch channels quietly reject posts from new accounts or posts written with AI help. This kit shows which of 50 launch channels will take your post in your situation, with the rule and its source for each one.

   What's inside (one offline HTML file + README):
   • All 50 channels: subreddits, Hacker News, Product Hunt, Indie Hackers, Dev.to, Hashnode, Medium, HackerNoon, Lobsters, 20+ launch directories with their real free-queue times and paid fast lanes, Mastodon, Bluesky, Shopify Community, Turkish forums.
   • Finder: account age × AI-assisted text × how fast you need visibility × budget, sorted into open / caveats / closed, with the rule quote and source. Each row says whether the source is the platform's own page, an archived copy, or a third-party tracker.
   • Launch profile with character counters (60/160/500) and one-click copy.
   • Autofill bookmarklet for submit forms. It never submits. No extension, no permissions, and nothing leaves your browser.
   • Submission tracker with CSV export.
   • The full dataset as CSV and JSON.

   Try the free version first (12 channels): https://hferrahoglu.github.io/where-can-i-post/

   Honest limits: this is a data snapshot from 2026-11-05. Rules change and updates aren't promised. "Open" means no blocking rule was found, not that you'll get traffic. Not legal advice.

   Built by an AI agent (Claude, by Anthropic) with me as the human operator, as part of a public 24-hour experiment: https://github.com/HFerrahoglu/24h-zero-budget-experiment

   Refunds: full refund within 14 days for any reason. Reply to your receipt or email hferrahoglu@gmail.com.
   ```
6. **Cover** olarak yukarıdaki `screenshot-free.png` dosyasını yükleyin.
7. **Content** bölümüne `where-can-i-post-full-kit.zip` dosyasını yükleyin.
8. Satın alma sonrası mesaj ("Thank you"/receipt note) alanı varsa şunu yapıştırın:
   ```
   Thanks! Download the ZIP, unzip it, and open where-can-i-post-full.html in your browser. README.txt explains the autofill bookmarklet. Questions or a refund: just reply to this email.
   ```
9. **Settings** bölümünde:
   - Ürün URL'sini (custom permalink) `wherecanipost` yapın.
   - "Refund policy" alanı varsa "14-day money back guarantee" seçeneğini ya da en yakınını seçin.
10. **Publish** (Yayınla).
11. **Kontrol, para harcamadan:** Ürün sayfasını gizli sekmede açın ve Gumroad'un **Preview** özelliğiyle içerik/indirme sayfasına bakın. **Satın alma yapmayın ve indirim kodu oluşturmayın.** Ekran görüntüsünü bana göndermeniz yeterli.

**Bana geri bildirin:** (a) ürünün tam URL'si (ör. `https://hferrahoglu.gumroad.com/l/wherecanipost`), (b) yayında mı, (c) Preview'da ZIP görünüyor mu, (d) ücret, ödeme ya da kimlik bilgisi isteyen bir ekran çıktı mı, (e) ürün sayfasının ekran görüntüsü.

### Görev 3.2 — Launching Next'e ücretsiz gönderim (~4 dk)
Bunu kendi veri setimiz gerektiriyor: Launching Next ücretsiz ve "We review submissions every day" diyor, ama yayın garantisi yok.
1. https://www.launchingnext.com/submit/ adresini açın.
2. Alanları doldurun:
   - **Startup Name:** `Where Can I Post?`
   - **Startup URL:** `https://hferrahoglu.github.io/where-can-i-post/?ref=ln`
   - **Your headline:**
     ```
     See which launch channels accept new accounts and AI-assisted posts
     ```
   - **Full startup description:**
     ```
     A free, client-side tool for makers about to launch. Pick your account age, whether AI helped write your post, how fast you need visibility and your budget. It sorts launch channels (Hacker News, Product Hunt, subreddits, directories) into open, caveats and closed for your situation, and shows the rule and its source for each one. Data checked on 2026-11-05. An optional $7 kit covers 50 channels and adds an autofill bookmarklet and a tracker. Built by an AI agent with a human operator, as part of a public 24-hour experiment.
     ```
   - **Tags:** `launch, marketing, indie hackers, startup directories, product launch, side project`
   - **Funding:** "bootstrapped / self-funded" ya da ona en yakın seçenek.
   - **Marketing budget:** `$0`
   - **Your Name:** Hamza Ferrahoğlu
   - **Email:** hferrahoglu@gmail.com
   - **Newsletter kutusunun işaretini KALDIRIN.** Gerekmeyen hiçbir şeye onay vermiyoruz.
   - "Quick Check" sorusunu siz cevaplayın.
3. **Submit Startup** butonuna basın.

**Bana geri bildirin:** Gönderildi mi, ekranda ne yazdı?

---

## PAKET 4 — Reddit paylaşımları ve cevaplar (Gumroad linki çalışınca başlar)

**Kurallar:**
- Her topluluğa farklı metin, paylaşımlar arasında en az 60-75 dk.
- Paylaşmadan önce Görev 2.2'de gördüğünüz kurallarla çelişen bir şey varsa **paylaşmayın**, bana yazın.
- Her metnin sonundaki açıklama kalacak: bu metni YZ ajanı yazdı, siz yayınlıyorsunuz.
- Linkleri olduğu gibi kopyalayın. `?ref=` parametresi hangi kanaldan ziyaret geldiğini ölçüyor.
- Metinleri Gumroad URL'si kesinleşince son hâline getireceğim. Gumroad URL'sini aldığımda size güncel paketi vereceğim. Taslaklar repoda: `posts/` klasörü.

**Takvim (TR saati, hedef):**
1. r/SideProject: Gumroad hazır olur olmaz (hedef ≤18:30, ABD Doğu 10:30)
2. r/indiehackers: +75 dk ("Self Promotion" flair)
3. r/alphaandbetausers: +75 dk (başlıkta "[Web, Beta]")
4. r/coolgithubprojects: +75 dk
5. Her 30-40 dakikada bir yorumlara bakıp gelen yorumları bana yapıştırın. Ben cevap taslaklarını hazırlarım, siz yayınlarsınız.

Hazır cevaplar (sık sorulacaklar): `posts/faq_replies.md`.
