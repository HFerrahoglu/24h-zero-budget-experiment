# METRICS — Kanal bazında huni

Kural: Uydurma sayı yok. Ölçülmemiş değerler `—`, tahminler `[TAHMİN]` etiketiyle yazılır. Her satır, verinin kaynağını ve okunduğu saati gösterir.

Huni: **erişim** (paylaşımın görüntülenmesi/upvote) → **ziyaret** (açılış sayfası) → **demo kullanımı** → **ödeme butonuna tıklama** → **satış**

| Kanal | ref parametresi | Erişim | Ziyaret | Demo kullanımı | Ödeme tıklaması | Satış | Kaynak / okuma saati |
|---|---|---|---|---|---|---|---|
| r/SideProject | `rsp` | 0 (Reddit filtresi kaldırdı, 17:25) | — | — | — | — | operatör; modmail bekleniyor |
| r/indiehackers | `rih` | — | — | — | — | — | paylaşılmadı |
| r/alphaandbetausers | `rab` | — | — | — | — | — | paylaşılmadı |
| r/coolgithubprojects | `rcg` | — | — | — | — | — | paylaşılmadı |
| Launching Next | `ln` | 0 (kuyrukta, tahmini 4 ay) | — | — | — | — | gönderildi 17:45 |
| Bluesky | `bsky` | 5 beğeni (1'i bot), 0 repost, başkasından 0 yanıt (18:22) | 0 | 0 | 0 | — | yayında 17:46 |
| Bluesky #2 (kuyruk verisi) | `bsky2` | yeni | 0 | 0 | 0 | — | yayında 20:18 |
| Indie Hackers (yorum) | `ih` | yorum 1 upvote, 0 yanıt; başlık 33 upvote / 176 yorum (18:24) | 0 | 0 | 0 | — | yayında 17:48 |
| Doğrudan / README / diğer | `direct` | — | 4 | 1 | 0 | — | abacus, 18:22 |
| *Kendi testim (hariç)* | `selftest` | — | 1 | 1 | 0 | — | 16:54, QA |

## Ölçüm yöntemi (Faz 5, 16:55)
- **Ziyaret / demo / ödeme tıklaması:** Ücretsiz sayfa (https://hferrahoglu.github.io/where-can-i-post/) kayıt gerektirmeyen bir sayaca anonim istek atıyor. Servis abacus.jasoncameron.dev, namespace `wcip-hf24h`. Anahtarlar: `visit_<ref>`, `demo_<ref>`, `buy_<ref>`. Okuma: `https://abacus.jasoncameron.dev/get/wcip-hf24h/visit_rsp`.
  - Sayfa yüklemesi sayılıyor, tekil ziyaretçi değil. Aynı sayfa yüklemesinde her olay bir kez sayılıyor.
  - `ref` sessionStorage'da tutuluyor. Ziyaretçi sayfada gezinirken kanal bilgisi kaybolmuyor.
- **Erişim:** Reddit gönderisinin upvote ve yorum sayısı. Operatör ekran görüntüsüyle iletecek.
- **Satış:** Gumroad paneli. Operatör iletecek.
- **GitHub:** repo traffic API (görüntülenme, referrer). Ajan doğrudan okuyabiliyor.


## Ölçüm günlüğü (saatlik izleme)
Not: abacus sayaçları sayfa yüklemesini sayıyor, tekil ziyaretçi değil. `selftest` ajanın kendi testi, toplamlara dahil değil. Reklam engelleyiciler sayaç isteğini engelleyebilir; ölçülen değer gerçek ziyaretin alt sınırı `[ÇIKARIM]`.

| Saat (TR) | direct v/d/b | Kanal ref'leri v/d/b (rsp, rih, rab, rcg, ln, bsky, bsky2, ih) | Bluesky (beğeni/repost/yanıt) | IH yorumu (upvote/yanıt) | GitHub views (where-can-i-post / deney) | Satış (Gumroad) |
|---|---|---|---|---|---|---|
| 18:22 | 4/1/0 | hepsi 0/0/0 | 5 (1 bot) / 0 / 0 | 1 / 0 | 0 / 0 (GitHub gecikmeli) | — (operatör iletecek) |
| 19:23 | 4/1/0 (değişim yok) | hepsi 0/0/0 | 5 (1 bot) / 0 / 0 başkasından (API replyCount=2 ama görünen tek yanıt bizim; bildirim yok) | 1 (büyük ihtimalle kendi otomatik oyumuz) / 0 | 0 / 0 | — |
| 20:50 | (ölçülmedi, ara kontrol) | — | — | 1 / **1 yanıt** (brent alexis, gönderi sahibi; cevaplandı 20:44) | — | **0 satış, $0** (Gumroad ürün listesi, ajan okudu) |
