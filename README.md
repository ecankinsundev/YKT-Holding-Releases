<p align="center">
  <img src="assets/ykt-holding-logo.png" alt="YKT Holding — YKTera" width="128" height="128" />
</p>

<h1 align="center">YKT Holding</h1>

<p align="center">
  <strong>YKTera</strong> tarafından geliştirilen çok-motorlu yapay zeka organizasyon ve ajan yönetim platformu.<br/>
  Yerli masaüstü uygulamasından şirketlerinizi, projelerinizi, otonom ajanlarınızı, kalıcı hafızanızı ve gömülü tarayıcınızı yönetin.
</p>

<p align="center">
  <strong>Güncel Sürüm:</strong> <code>v1.6.0</code> (2026-11-21) &nbsp;·&nbsp;
  <a href="https://github.com/ecankinsundev/YKT-Holding-Releases/releases/tag/v1.6.0">Sürüm Sayfası</a> &nbsp;·&nbsp;
  <a href="CHANGELOG.md">Tüm Sürüm Notları</a>
</p>

---

## İndirme (v1.6.0)

| Platform | Paket Türü | İndirme Bağlantısı | SHA-256 |
|---|---|---|---|
| **Windows x64** | Kurulum Sihirbazı (Önerilen) | [`YKT-Holding_1.6.0_x64-setup.exe`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.6.0/YKT-Holding_1.6.0_x64-setup.exe) | `0489f46fabba45b914523ba9e1cce3b74feb8b9fa6c7853ad24b1dbc18b4f794` |
| **Windows x64** | Portatif Arşiv (Kurulumsuz) | [`YKT-Holding_1.6.0_x64-portatif.zip`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.6.0/YKT-Holding_1.6.0_x64-portatif.zip) | `c90df7c16ce8078f45d7c663ee104703277019490225d18f3ed0bfd4ef8e61ed` |
| **Güncelleme Manifestosu** | Sürüm Kaydı | [`latest.json`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.6.0/latest.json) | — |

> **Bütünlük Doğrulama (PowerShell):**
> ```powershell
> (Get-FileHash .\YKT-Holding_1.6.0_x64-setup.exe -Algorithm SHA256).Hash.ToLower() -eq "0489f46fabba45b914523ba9e1cce3b74feb8b9fa6c7853ad24b1dbc18b4f794"
> ```
> Çıktı `True` dönmelidir.

---

## Gereksinimler

- **İşletim Sistemi:** Windows 10 / Windows 11 (64-bit) ve Microsoft Edge WebView2 Runtime (gömülü tarayıcı için).
- **Yapay Zeka Motoru (en az biri):**
  - **Claude Code CLI** (`claude`)
  - **Antigravity CLI** (`agy`)
  - *(İsteğe bağlı)* Yerel **Ollama** veya harici API geçidi
- **Git:** İş ağacı yalıtımı ve sürüm kontrolü için yerel Git kurulumu.

---

## Kurulum

### Seçenek 1 — Windows Kurulum Dosyası (Önerilen)
1. Yukarıdaki tablodan **`YKT-Holding_1.6.0_x64-setup.exe`** dosyasını indirin ve çalıştırın (yönetici izni gerektirmez).
2. Uygulama `%LOCALAPPDATA%\YKT Holding` klasörüne kurulur, kullanıcı `PATH` ortam değişkenine `ykt` komutunu ekler ve Başlat Menüsü / Masaüstü kısayollarını oluşturur.
3. **YKT Holding** uygulamasını açın; ilk açılış sihirbazı çalışma klasörünüzü, şirket/ekip yapınızı ve `ykt-guard` güvenlik kapılarını otomatik yapılandırır.

### Seçenek 2 — Portatif ZIP (Kurulumsuz)
1. **`YKT-Holding_1.6.0_x64-portatif.zip`** arşivini dilediğiniz klasöre çıkartın.
2. Klasör içindeki `ykt-holding.exe` dosyasını çalıştırın.

### Mevcut Sürümden Güncelleme
- Yeni `setup.exe` dosyasını doğrudan mevcut kurulumun üzerine çalıştırabilirsiniz (kullanıcı verileriniz, projeleriniz, kartlarınız ve hafızanız korunur).
- Uygulama ilk açılışta yeni sürümü algılar ve `ykt kur --yenile` ile rol tanımlarını, skill'leri ve K0 güvenlik kapısını otomatik tazeler.

---

## Nasıl Kullanılır?

### 1. Masaüstü Arayüzü (Tam Yerleşik Bölmeli Çalışma Alanı)
- **Ofis (2.5D İzometrik Cam Kule & Kat Kesiti):** Şirket binalarınızı, 4 yönlü döndürülebilir modern 2.5D cam kule görünümünü, çift tıkla açılan cam bölmeli kat kesitini, canlı delegasyon yaylarını ve hızlı ajan kontrol kartını tek ekrandan yönetin (boşta 0 FPS; isterseniz üst şeritten `Sehir gorunumu` kapatıldığında `Tahta | Konuşmalar` yan yana açılır, `Ayarlar > Tema` altından Klasik Piksel görünüme de geçilebilir).
- **Konuşmalar:** Holding Genel Müdürü ve proje liderleriyle doğal Türkçe mesajlaşarak iş kartları planlayın, karar verin veya onay verin.
- **Tahta & Projeler (Tahta · Liste · Plan · Akış · Organizasyon):** Tüm şirket ve projelerinizi, kart durum sütunlarını (`Tahta`), canlı delegasyon grafiğini (`Akış`) ve şirket/ekip yapısını (`Organizasyon`) tek pencerede yönetin.
- **Kullanım:** Claude Code (5s / Haftalık / Fable), Antigravity (Gemini 4 Neon / Carbon / Argon & Claude) ve yerel Ollama limitlerini tek sekmede izleyin.
- **Hafıza:** Obsidian uyumlu kalıcı Markdown bilgi tabanı, dersler ve karar kayıtları.
- **Tarayıcı:** Uygulama içi gömülü WebView2 tarayıcısı; ajanların web araştırması ve önizleme adımlarını aynı pencerede güvenle izleyin (giriş/2FA/ödeme adımlarında ajan otomatik durur ve kontrolü size bırakır).
- **Ayarlar:** Aydınlık/Karanlık Tema (Gece / Gündüz WCAG AA) + Ofis kipi (2.5D / Klasik), **Kota ve bütçe**, **Bağlantılar > Motorlar** (tek tıkla **"Motorları güncelle"**), güvenlik kapısı ve sistem sağlığı.

### 2. Temel CLI Komutları

```powershell
ykt saglik                 # Sistem hazırlık puanı ve sağlık denetimi
ykt durum                  # Aktif kartlar, bütçe ve çalışan ajan özeti
ykt motor kontrol          # Kurulu motorların (claude, agy, ollama) sürüm ve kimlik durumu
ykt motor guncelle         # Claude Code ve Antigravity CLI motorlarını tek komutla güncelle
ykt kur --yenile           # Rol, skill ve K0 güvenlik kancalarını tazele
ykt calisan                # Bu makinedeki otonom kart çalıştırma döngüsünü başlat
ykt gm-yerel               # Holding Genel Müdürü ile terminal oturumu aç
```

### 3. Güvenlik ve Veri Sahipliği
- Tüm ajan oturumları yerel **`ykt-guard`** K0 kanca kapısı üzerinden çalışır: izinsiz kalıcı dosya silme (Geri Dönüşüm Kutusu zorunlu), kapsam dışı yazma, izinsiz `git push` / yayın ve hassas kural değişiklikleri kanca seviyesinde engellenir.
- Tüm verileriniz (kadro, kartlar, kurallar, Obsidian hafızası) tamamen **kendi bilgisayarınızda** kalır; bu depo yalnızca kurulum paketlerini ve sürüm notlarını barındırır.

---

## Mevcut Sürümde Neler Var? (v1.6.0)

### Yenilikler ve Duzeltmeler
- **Hibrit Gercek Terminal & Tek Tikla Oturumu Devral (`ykt kosu izle` + `devral` / `geri-ver`):**
  - Ortak stream-json bicimleyici `ykt-core::kosu_akis` modulune tasindi ve **`ykt kosu izle <ID> [--takip]`** CLI alt komutu eklendi; `Teknik` kipteki gercek gomulu PowerShell artik ham JSONL yerine renkli, Claude CLI tarzinda okunakli canli cikti gosterir (`Ctrl+C` ile temizce `PS>` satirina doner; raw ESC/kontrol kacislari ve gizli veriler temizlenir).
  - Kosan/bekleyen Claude kartlarina tek tikla **`Oturumu Devral (Claude)`** ve **`Ajana geri ver (Baslat)`** eklendi: ajan guvenle durdurulur, yalitim worktree'si korunur, `devralan: patron` kilidi cift calisma ve `cevapla` cakismasini engeller, PowerShell ortami tum `AJANS_*` / `YKT_*` degiskenlerinden arindirilir ve `Ajana geri ver` acik terminali kapatip ajana kaldigi oturumdan devam etmesini soyler.
- **Silikon Vadisi 2.5D Kampus Peyzaji (`izometrik.rs`):**
  - Gereksiz/sahte bina eklenmeden yalniz gercek holding binalarinin cevresine Apple Park / Bay View tarzinda pahli tas avlu meydani, yuruyus yollari, mimari cim adalari, yansimali havuz, 3 farkli 2.5D agac/cit stili (Kaliforniya selvisi, zeytin/mese taci, saksili simsir), ahsap avlu banklari ve gece sicak isik halkali yol lambalari eklendi (Gece & Gunduz palet uyumlu, 4 kamera acisinda tam derinlik siralamali, bosta **0 FPS**).
- **Guvenli Gelistiriciye Bildir (`ekinsun@yktera.com` + Ekran Goruntusu):**
  - `Ayarlar > Hakkinda > Gelistiriciye bildir` her zaman etkin hale getirildi; yorum kutusu, dosya secici (`GetOpenFileNameW`), panodan yapistirma (`CF_DIB`) ve surukle-birak ile en cok 3 ekran goruntusu eklenebilir.
  - Guvenlik kapisi yalniz **PNG, JPG, JPEG, WEBP** kabul eder (`<= 5 MB` okuma oncesi sinir, symlink reddi, magic-byte + boyut `<= 8192px` dogrulama, EXIF/tEXt/COM ve polyglot son-ek temizligi, PNG piksel yeniden kodlama, sabit `ekran-N` adlandirma, CRLF baslik temizligi ve sifir gomulu sir).
- **Opsiyonel Otomatik Guncelleme & Surum Notlu Bildirim:**
  - `Ayarlar > Surecler` ve `Ayarlar > Hakkinda` altina **`Otomatik guncelle`** anahtari eklendi (varsayilan kapali). Acikken yeni surum resmi HTTPS kaynaktan indirilir, SHA-256 iki kez (yazarken ve baslatmadan once) dogrulanir ve kosan isler bitince otomatik kurulur. Kapaliyken ust seritte **`Yeni surum mevcut`** bildirimiyle kisa degisiklik ozeti + **`Indir ve kur`** / **`Sonra`** dugmeleri gosterilir.
- **Kurulu Tum Motorlar & Antigravity Kotalari (`Kullanim` + `Ayarlar > Butce`):**
  - `Kullanim ve Limitler` ve `Ayarlar > Butce` ekranlari artik yalniz Claude'u degil, `motorlar-onbellek.json`'daki **kurulu tum motorlari** (Claude, Antigravity, kuruluysa Ollama ve Gecit) gosterir; Antigravity icin gunluk havuz sayaclari, UTC sifirlama geri sayimi, aktif rate-limit bekleme kartlari ve elle Antigravity kota/sifirlama kaydi eklendi.
- **Ayarlar Alt Oge Hiyerarsisi + Ust Ogeyi Kapatma & 1 Cumlelik Onay Ozeti:**
  - Ayarlar sol menusunde ust gruplar acik/kapali oku (`▾`/`▸`) ve vurgu seridiyle, alt ogeler ise dikey agac cizgisi + girintiyle net bicimde ayrildi; acik ust gruba tekrar tiklandiginda grup kapanip **Ayarlar Ana Sayfasi** kart gorunumune doner.
  - Sol **Onay bekleyenler** panelinde artik teknik log satiri yerine kartin amacini anlatan **1 cumlelik sade ozet** gosterilir (`ENGEL:` ve acik kararlar oncelikli).

---

> Detaylı sürüm geçmişi için [CHANGELOG.md](CHANGELOG.md) dosyasına bakın.  
> **YKT Holding** · Geliştiren: **YKTera** · Tüm hakları saklıdır.
