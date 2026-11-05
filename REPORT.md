# REPORT: Final rapor (TASLAK, 06/11 15:21'de tamamlanacak)

> Bu dosya deney sürerken taslak olarak dolduruluyor. Sayılar ve sonuçlar 06/11 15:21'deki final ölçümle güncellenecek. `[KESİNLEŞMEDİ]` etiketli bölümler henüz bitmedi.

## 1. Özet `[KESİNLEŞMEDİ]`
- **Ürün:** Where Can I Post?
  - Ne yapıyor: Yeni hesap, YZ destekli metin, zaman ve bütçe durumuna göre 50 lansman kanalını açık / çekinceli / kapalı diye ayırıyor. Her kararın kuralını ve kaynağını gösteriyor. Hiçbir YZ çağrısı yapmıyor, tamamen tarayıcıda çalışıyor.
  - Ücretsiz sürüm (12 kanal): https://hferrahoglu.github.io/where-can-i-post/
  - Ücretli kit (50 kanal + profil + autofill bookmarklet + takip + dışa aktarma): https://hferrahoglu.gumroad.com/l/wherecanipost
- **Fiyat:** $7, tek seferlik. Gumroad kesintisi %10 + $0.50, satış başına net $5,80.
- **Satış adedi / gelir:** —

## 2. İhtiyaç gerçek miydi? `[KESİNLEŞMEDİ]`
**Deneyden önceki kanıtlar** (RESEARCH §4.1):
- HN 46676047, 43331842 ("would pay 30 USD"), 42943314
- Gumroad'da $9.99'luk lansman listesi, 276 satış

**Deney sırasında gelen sinyaller:**
- IH'de 2026-11-03 tarihli "I looked at 20+ launch directories…" başlığı (32 upvote, 172 yorum). Yorumlarda aynı acı birebir anlatılıyor: aylarca süren kuyruklar, yeni hesapla Show HN reddi, Reddit filtresi.
- Deneyin kendi dağıtımı aracın tezini doğruladı (LOG 17:26, 17:40, 17:45):
  - Yeni hesabın Reddit gönderisi filtreye takıldı.
  - IH yeni hesaba paylaşım izni vermedi.
  - Launching Next 4 ay kuyruk verdi.

**Kullanıcıdan gelen sinyaller** (ziyaret, demo, satın alma tıklaması, yorum, satış): —

**Etiket:** —

## 3. Kanal bazında huni `[KESİNLEŞMEDİ]`
METRICS.md'den aktarılacak.

## 4. Alıcının bağımsızlığı `[KESİNLEŞMEDİ]`
—

## 5. En iyi 3 ve en kötü 3 karar `[KESİNLEŞMEDİ]`
**İyi kararlar (aday):**
1. Dağıtım araştırmasını fikir seçiminden önce yapmak. YZ metni yasaklarını en baştan araştırmak, HN, PH ve Shopify Community'de olası ihlalleri önledi.
2. Ruul Space'in kapandığını ilk 10 dakikada kanıtlamak ve self-servis ödemeye (Gumroad) geçmek.
3. Ürünü 20 dakikada bitirip kalan zamanı dağıtıma ayırmak. Her kanal denemesinden gelen birinci elden bilgiyi ürüne geri eklemek.

**Kötü kararlar (aday):**
1. Kanal havuzu bu kadar darken, tek bir Reddit hesabıyla link içeren bir gönderiyi ilk hamle yapmak. Filtre riski önceden biliniyordu (R3).
2. Gumroad URL'sini yazarken alan içeriğini Ctrl+A ile seçtiğimi doğrulamamak: URL `awherecanipost` oldu. Yayından önce fark edildi.
3. Verdict mantığında kurallar arasındaki etkileşimi test etmemek. dev.to'nun "YZ metniyle kendi işini tanıtma yasak" kuralı 5 saat boyunca "çekinceli" göründü. Satırın notu doğruydu, ama kararı yalnızca alanlar tek tek belirliyordu. Yayımlanan "27 closed / 22 caveats" sayısı bu yüzden 1 kanal kadar iyimserdi (LOG 21:39).

## 6. Operatör müdahalesi ve hesaplar `[KESİNLEŞMEDİ]`
- **Operatör süresi:** — (operatörden istenecek)
- **Operatörün yaptıkları:**
  - Hesap açma: Gumroad, Reddit, Bluesky, Indie Hackers.
  - Gumroad ödeme ve kimlik bilgileri (operatör kendisi girdi).
  - Reddit kural kontrolü, paylaşım ve modmail denemesi.
  - Bluesky e-posta doğrulaması.
  - Launching Next bot kontrolü.
  - Onaylar: Gumroad yayını, IH yorumu.
- **Ajanın tarayıcıyla yaptıkları** (operatör 16:58'de izin verdi):
  - Gumroad ürün kurulumu ve güncellemeleri.
  - Bluesky profili ve gönderileri.
  - IH yorumu.
  - Launching Next formu.
  - Ruul panelinde salt okunur kontrol.
- **Sıfırdan açılan hesaplar ve kısıtları:** ACCOUNTS.md'de 4 hesap.
  - Gumroad: kısıt yok.
  - Reddit: site filtresi gönderiyi kaldırdı, modmail gönderilemiyor.
  - Bluesky: ilk gönderi için e-posta doğrulaması gerekiyor.
  - IH: yeni hesap paylaşım yapamıyor.
- **Ne kadar "kendi başına":**
  - Fikir, seçim, inşa, fiyat, metinler ve kanal kararları tamamen ajandan.
  - İnsan kimliği gerektiren adımlar ve bot kontrolleri operatörden.
  - Reddit eklenti tarafından engellendiği için Reddit'te paylaşımı operatör yaptı.

## 7. Sıfır maliyet denetimi
| Servis | Kullanım | Ücret | Kart istendi mi? |
|---|---|---|---|
| GitHub (repo + Pages) | Kod, açılış sayfası, günlük | $0 (public repo) | Hayır |
| Gumroad | Ödeme ve teslim | $0 sabit; satış başına %10 + $0.50 (gelirden kesilir, bütçe sayılmaz) | Hayır |
| abacus.jasoncameron.dev | Anonim sayaç | $0, kayıt yok | Hayır |
| Reddit, Bluesky, Indie Hackers | Dağıtım | $0 | Hayır |
| Launching Next | Ücretsiz dizin gönderimi ($99 hızlandırma **alınmadı**) | $0 | Hayır |
| Ruul | Yalnızca kontrol (Space kapalı) | $0 | — |
| jsdom (npm), Edge headless | Test, ekran görüntüsü | $0 (açık kaynak / kurulu) | — |

Harcanan para: **$0**. Hiçbir ücretli plan, reklam, alan adı ya da ücretli API kullanılmadı. Kalan doğrulama: deney sonunda operatörün kart ve hesap hareketlerinde bu servislere bir ödeme olmadığını teyit etmesi.

## 8. 7 gün daha olsaydı `[KESİNLEŞMEDİ]`
—

## 9. Deney sonrası yükümlülükler `[KESİNLEŞMEDİ]`
- Alıcılara 14 günlük koşulsuz iade sözü verildi. Bu, Gumroad panelinden operatörün yükümlülüğü.
- Destek e-postası: hferrahoglu@gmail.com.
- Kapatma veya sürdürme kararı: —
