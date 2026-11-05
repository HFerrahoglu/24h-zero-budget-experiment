# STATE — Şu anki durum

**Son güncelleme:** 2026-11-05 16:18 (TR, UTC+3)
**Faz:** 0 — Envanter (bitmek üzere)
**Deney:** 05/11 16:00 → 06/11 16:00

## Kritik gerçekler (yeni oturumda önce bunları oku)
1. **Ruul Space kapatılmış.** Ruul'da yalnızca müşteri başına elle fatura kalmış ve ürün satışı kapsam dışı (LOG 16:05). Self-servis ödeme için **Gumroad** önerildi, operatör onayı bekleniyor (OPERATOR_TASKS 1.2).
2. **Operatöre yalnızca bugün 16:00-00:00 arasında ulaşılabiliyor.** Gece yarısından sonra paylaşım, yorum cevabı ve hesap işlemi yapılamaz. Bu yüzden zaman planı sıkıştırıldı (LOG 16:12).
3. GitHub erişimi REST API üzerinden. Token GCM'den çalışma anında okunuyor. Yardımcı script: `<scratchpad>/bin/ghapi.sh` (repo dışında, token içermiyor). `gh` CLI yok.
4. Commit e-postası repo'ya özel noreply adresi. Global git ayarına dokunulmadı.

## Sıkıştırılmış zaman planı
| Saat | Faz |
|---|---|
| 16:00-16:30 | Faz 0 Envanter |
| 16:30-18:00 | Faz 1 Keşif (paralel ajanlarla) |
| 18:00-18:20 | Faz 2 Seçim |
| 18:20-20:50 | Faz 4 MVP |
| 20:50-21:30 | Faz 5 Satış altyapısı (Gumroad ürünü + açılış sayfası) |
| 21:30-00:00 | Faz 6 aktif dağıtım (operatör paylaşır, yorumlara cevap verir) |
| 00:00-16:00 | Faz 6 pasif dağıtım + sayfa iyileştirme + Faz 7 rapor |

## Sıradaki 3 adım
1. GitHub repo'yu (public) oluştur, push et, Pages deploy'unu test et.
2. Dağıtım araştırması ajanının sonucunu RESEARCH.md §2'ye işle. Pazar/dil kararını ver. Paket 2'yi (kanal hesapları) hazırla.
3. Faz 1 keşfini başlat: 5+ kaynak türü, 15+ aday, her biri için 3 kanıt linki. Seçilen kanallardaki kitleye göre yönlendir.

## Açık riskler
- R1: Gumroad'u operatör reddederse elimizde yalnızca Ruul'un elle fatura akışı kalır. Gece satışı imkânsızlaşır.
- R2: Gumroad yeni hesaplardan ürün yayınlamadan önce ödeme veya kimlik bilgisi isteyebilir. Bu doğrulanmadı.
- R3: Platformlar yapay zekâ üretimi içeriği yasaklıyor olabilir (HN, Stack Overflow, bazı subredditler). Bu durumda kanal havuzu daralır. Araştırılıyor.
- R4: İnşa süresi 2,5 saatle sınırlı. Kapsam taşarsa paylaşımlar 00:00'dan sonraya kalır, yani hiç yapılamaz.
- R5: Yeni hesapların görünürlüğü düşük (karma, spam filtreleri).

## Bekleyen operatör yanıtları
- Paket 1: 1.1 Ruul menüsü, 1.2 ONAY/RET, 1.3 Gumroad hesabı, 1.4 sabah ulaşılabilirlik
