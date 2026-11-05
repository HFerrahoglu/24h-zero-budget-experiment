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
| Bluesky | `bsky` | 0 beğeni / 0 repost (17:47) | — | — | — | — | yayında 17:46 |
| Indie Hackers (yorum) | `ih` | — | — | — | — | — | yayında 17:48 |
| Doğrudan / README / diğer | `direct` | — | — | — | — | — | — |
| *Kendi testim (hariç)* | `selftest` | — | 1 | 1 | 0 | — | 16:54, QA |

## Ölçüm yöntemi (Faz 5, 16:55)
- **Ziyaret / demo / ödeme tıklaması:** Ücretsiz sayfa (https://hferrahoglu.github.io/where-can-i-post/) kayıt gerektirmeyen bir sayaca anonim istek atıyor. Servis abacus.jasoncameron.dev, namespace `wcip-hf24h`. Anahtarlar: `visit_<ref>`, `demo_<ref>`, `buy_<ref>`. Okuma: `https://abacus.jasoncameron.dev/get/wcip-hf24h/visit_rsp`.
  - Sayfa yüklemesi sayılıyor, tekil ziyaretçi değil. Aynı sayfa yüklemesinde her olay bir kez sayılıyor.
  - `ref` sessionStorage'da tutuluyor. Ziyaretçi sayfada gezinirken kanal bilgisi kaybolmuyor.
- **Erişim:** Reddit gönderisinin upvote ve yorum sayısı. Operatör ekran görüntüsüyle iletecek.
- **Satış:** Gumroad paneli. Operatör iletecek.
- **GitHub:** repo traffic API (görüntülenme, referrer). Ajan doğrudan okuyabiliyor.
