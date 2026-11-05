# METRICS — Kanal bazında huni

Kural: Uydurma sayı yok. Ölçülmemiş değerler `—`, tahminler `[TAHMİN]` etiketiyle yazılır. Her satır, verinin kaynağını ve okunduğu saati gösterir.

Huni: **erişim** (paylaşımın görüntülenmesi/upvote) → **ziyaret** (açılış sayfası) → **demo kullanımı** → **ödeme butonuna tıklama** → **satış**

| Kanal | ref parametresi | Erişim | Ziyaret | Demo kullanımı | Ödeme tıklaması | Satış | Kaynak / okuma saati |
|---|---|---|---|---|---|---|---|
| r/SideProject | `rsp` | 0 (Reddit filtresi kaldırdı, 17:25). **22:5x: gizli sekmede görünüyor**, operatöre göre büyük olasılıkla moderatör onayı; 1 upvote (Reddit'in yazara verdiği otomatik oy). https://www.reddit.com/r/SideProject/comments/1xojwie/we_checked_50_launch_channels_for_brandnew/ | — | — | — | — | operatör |
| r/indiehackers | `rih` | **Paylaşılamadı:** "You can't contribute in this community yet" (hesap yaşı + topluluk karması), 22:5x | — | — | — | — | operatörün ekran görüntüsü |
| r/alphaandbetausers | `rab` | İptal (hesap riskini sınırlamak için, LOG 22:52) | — | — | — | — | paylaşılmadı |
| r/coolgithubprojects | `rcg` | İptal (hesap riskini sınırlamak için, LOG 22:52) | — | — | — | — | paylaşılmadı |
| Launching Next | `ln` | 0 (kuyrukta, tahmini 4 ay) | — | — | — | — | gönderildi 17:45 |
| Bluesky | `bsky` | 5 beğeni (1'i bot), 0 repost, başkasından 0 yanıt (23:22) | 0 | 0 | 0 | — | yayında 17:46 |
| Bluesky #2 (kuyruk verisi) | `bsky2` | 2 beğeni (1'i bot), 0 repost, 0 yanıt (23:22) | 0 | 0 | 0 | — | yayında 20:18 |
| IH yorumu #2 (founderdive, davetli) | `ih2` | yeni | 0 | 0 | 0 | — | yayında 23:39 |
| Indie Hackers (yorum) | `ih` | Yoruma başlık sahibinden 2 yanıt geldi (~19:20, ~21:11), ikisi de cevaplandı. Yorumda 1 oy var, o da kendi otomatik oyumuz. Başlık 208 yorum (22:22). | 0 | 0 | 0 | — | yayında 17:48 |
| Doğrudan / README / diğer | `direct` | — | 5 | 2 | 0 | — | abacus, 23:22 |
| *Kendi testim (hariç)* | `selftest` | — | 3 | 1 | 0 | — | abacus, QA |

## Ölçüm yöntemi (Faz 5, 16:55)
- **Ziyaret / demo / ödeme tıklaması:** Ücretsiz sayfa (https://hferrahoglu.github.io/where-can-i-post/) kayıt gerektirmeyen bir sayaca anonim istek atıyor. Servis abacus.jasoncameron.dev, namespace `wcip-hf24h`. Anahtarlar: `visit_<ref>`, `demo_<ref>`, `buy_<ref>`. Okuma: `https://abacus.jasoncameron.dev/get/wcip-hf24h/visit_rsp`.
  - Sayfa yüklemesi sayılıyor, tekil ziyaretçi değil. Aynı sayfa yüklemesinde her olay bir kez sayılıyor.
  - `ref` sessionStorage'da tutuluyor. Ziyaretçi sayfada gezinirken kanal bilgisi kaybolmuyor.
- **Erişim:** Reddit gönderisinin upvote ve yorum sayısı. Operatör ekran görüntüsüyle iletecek.
- **Satış:** Gumroad paneli. Operatör iletecek.
- **GitHub:** repo traffic API (görüntülenme, referrer). Ajan doğrudan okuyabiliyor.


## Ölçüm günlüğü (saatlik izleme)
Not: abacus sayaçları sayfa yüklemesini sayıyor, tekil ziyaretçi değil. `selftest` ajanın kendi testi, toplamlara dahil değil. Reklam engelleyiciler sayaç isteğini engelleyebilir; ölçülen değer gerçek ziyaretin alt sınırı `[ÇIKARIM]`.

| Saat (TR) | direct v/d/b | Kanal ref'leri v/d/b (rsp, rih, rab, rcg, ln, bsky, bsky2, ih, ih2) | Bluesky (beğeni/repost/yanıt) | IH yorumu (upvote/yanıt) | GitHub views (where-can-i-post / deney) | Satış (Gumroad) |
|---|---|---|---|---|---|---|
| 18:22 | 4/1/0 | hepsi 0/0/0 | 5 (1 bot) / 0 / 0 | 1 / 0 | 0 / 0 (GitHub gecikmeli) | — (operatör iletecek) |
| 19:23 | 4/1/0 (değişim yok) | hepsi 0/0/0 | 5 (1 bot) / 0 / 0 başkasından (API replyCount=2 ama görünen tek yanıt bizim; bildirim yok) | 1 (büyük ihtimalle kendi otomatik oyumuz) / 0 | 0 / 0 | — |
| 20:24 | (ölçülmedi, ara kontrol) | — | — | 1 / **1 yanıt** (brent alexis, gönderi sahibi; cevaplandı ~20:23) | — | **0 satış, $0** (Gumroad ürün listesi, ajan okudu) |
| 20:26 | **5/2/0** (+1 ziyaret, +1 demo; ref yok) | hepsi 0/0/0 (bsky2 dahil) | #1: 5/0/0 başkasından; #2 (20:18): 0/0/0 | 1 / 1 (yeni yanıt yok; bildirim sayfası) | 0 / 0 | 0 |
| 21:22 | 5/2/0 | hepsi 0/0/0 | #1: 5/0/0; **#2: 2 beğeni** (buildinpublicbot, kulpinski.dev) / 0 / 0 | 1 / **2 yanıt** (brent alexis, ikincisi ~21:11) | 0 / 0 | 0 |
| 22:23 | 5/2/0 | hepsi 0/0/0 | #1: 5/0/0; #2: 2/0/0 | 1 / 2 (yeni yanıt yok; cevaplarımız 1'er oy, kendi otomatik oyumuz) | 0 / 0 | 0 |
| 23:22 | 5/2/0 | hepsi 0/0/0 (rsp dahil; r/SideProject gönderisi görünür olmasına rağmen) | #1: 5/0/0; #2: 2/0/0 | 1 / 2 (yeni yok) | 0 / 0 | 0 |
