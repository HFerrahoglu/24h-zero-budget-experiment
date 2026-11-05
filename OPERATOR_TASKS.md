# OPERATOR_TASKS — Operatörden istenen işler

Kurallar: Her görevde numaralı adımlar, tam linkler ve tahmini süre var. Her görevin sonunda **"Bana geri bildirin"** başlığı altında neyi yazmanız gerektiği belirtilmiş. Şifre, doğrulama kodu ve token'ları **bana ya da herhangi bir dosyaya yazmayın**.

Operatör penceresi: yalnızca 16:00-00:00 (bugün). Toplam bütçe: en fazla 480 dk.

## Süre takibi

| Paket | Verildiği saat | Tahmini süre | Gerçek süre (operatör yazar) | Durum |
|---|---|---|---|---|
| Paket 1 | 16:16 | ~15 dk | | Bekliyor |
| Paket 2 | 16:30 | ~14 dk | | Bekliyor |
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

*Paket 3 (ürün kurulumu ve paylaşım metinleri) ürün seçildikten sonra, tahminen 19:30-20:00 arasında gelecek. Paylaşımlar ~20:30'da başlayıp 00:00'a kadar sürecek. Bu aralıkta ayırabileceğiniz süreyi en çok buna ayırmanızı rica ederim, yorumlara cevap da bu sürede verilecek.*
