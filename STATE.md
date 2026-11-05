# STATE — Şu anki durum

**Son güncelleme:** 2026-11-05 19:23 (TR, UTC+3) — saatlik izleme #2: değişim yok (4 ziyaret, 1 demo, 0 satın alma tıklaması); Bluesky 5 beğeni; IH yanıt yok
**Faz:** 6 (Dağıtım). Yayında olanlar: Gumroad ($7), ücretsiz sayfa, Bluesky zinciri, IH yorumu, Launching Next (4 ay kuyruk). Reddit filtrelendi. İzleme cron'u saat başı :17'de.
**Deney:** 05/11 16:00 → 06/11 16:00

## Kritik gerçekler (yeni oturumda önce bunları oku)
1. **Ürün:** "Where Can I Post?" Yeni hesap, YZ destekli metin, zaman ve bütçe durumuna göre 50 lansman kanalının kurallarını kaynaklarıyla gösteriyor.
   - Ücretsiz sürüm (12 kanal): https://hferrahoglu.github.io/where-can-i-post/
   - Repo: https://github.com/HFerrahoglu/where-can-i-post
   - Kaynak klasör: `product/` (ayrı git repo; dış repoda gitignore'da)
   - Ücretli veri `product/data/channels.full.json` ve `channels.extra.json` dosyalarında. İkisi de gitignore'da, public değil.
   - Build: `cd product && node build.js <GUMROAD_URL>` → `docs/index.html`'e kopyala, ZIP'i yeniden üret. Test: `node test/test.js`.
2. **Ödeme:** Ruul Space kapalı (LOG 16:05, panelden de doğrulandı 17:01). Gumroad hesabı `hferrahoglu`, ürün yayında. Fiyat $7, iade 14 gün. Teslim dosyası `product/dist/where-can-i-post-full-kit.zip`. Ajan, operatörün tarayıcı oturumundan Gumroad'a erişebiliyor. Reddit'e erişemiyor (eklenti engeli).
3. **Kanallar:** Yalnızca r/SideProject, r/indiehackers, r/alphaandbetausers, r/coolgithubprojects (+ Launching Next). Neden: HN, PH, SO ve büyük sub'lar YZ metnini yasaklıyor ya da yeni hesaba kapalı (RESEARCH §2). Metinler `posts/` klasöründe, hazır cevaplar `posts/faq_replies.md`'de.
4. **Operatöre yalnızca bugün 16:00-00:00 arasında ulaşılabiliyor.** Tüm paylaşımlar ve cevaplar 00:00'dan önce yapılmalı.
5. **Ölçüm:** abacus sayaçları (`wcip-hf24h`, `visit|demo|buy_<ref>`). Okuma METRICS.md'de anlatılıyor. Ajan istediği zaman okuyabiliyor.
7. **Saatlik izleme için:** `bash <scratchpad>/bin/monitor.sh` (paralel, ~8 sn). Ölçtükleri: abacus sayaçları, Bluesky, GitHub traffic. IH yanıtları tarayıcıdan salt okuma ile kontrol ediliyor. Sonuçlar METRICS.md'deki "Ölçüm günlüğü" tablosuna yazılıyor.
6. GitHub erişimi `<scratchpad>/bin/ghapi.sh` üzerinden (token GCM'den okunuyor). Commit'ler noreply e-postasıyla atılıyor.

## Sıradaki 3 adım (17:53)
1. Saatlik izleme: METRICS'i güncelle, IH yanıtlarını oku. Yanıt gerekirse taslağı `posts/pending_replies.md`'ye yaz ve operatörden onay al (00:00'a kadar).
2. IH ve Bluesky'da yalnızca ihtiyacın dile getirildiği güncel başlıklara tek, onaylı yorum.
3. 23:30'da son operatör paketi. 06/11 15:21'de REPORT.md.

## (Eski) Sıradaki 3 adım
1. Operatörden Paket 1 cevaplarını al (özellikle 1.2 ONAY ve Gumroad kullanıcı adı), Paket 2'yi (Reddit hesabı + kurallar) ve Paket 3'ü (Gumroad ürünü) al.
2. Gumroad URL'si gelince `node build.js <URL>` çalıştır, docs ve ZIP'i güncelle, push et, satın alma butonunu canlıda doğrula.
3. Paket 4: r/SideProject paylaşımı → +75 dk r/indiehackers → +75 dk r/alphaandbetausers → +75 dk r/coolgithubprojects. Her 30-40 dk'da yorumları al, cevap taslağı ver. Sayaçları oku ve METRICS'e yaz.

## Açık riskler
- R1: Gumroad'a RET gelirse Plan B devreye girer (Ruul'dan elle fatura, ürün "hizmet" olarak sunulur). Gece satışı imkânsızlaşır.
- R2: Gumroad yeni hesaptan ödeme ya da kimlik bilgisi isteyebilir. Doğrulanmadı.
- R3: Reddit'in site genelindeki filtresi yeni hesabın gönderilerini gizleyebilir. Dışarıdan görülemez. Operatör gizli sekmede gönderinin görünüp görünmediğini kontrol edecek.
- R4: Operatör yanıtları gecikirse ABD sabah penceresi kaçar. Yine de 00:00'a kadar ABD öğleden sonrası sürüyor.
- R5: Veri kısmen ikincil kaynaklı. Yanlış satır itibar riski taşıyor. Her satırda kaynak türü etiketli, düzeltmeler aynı gün yapılacak.
