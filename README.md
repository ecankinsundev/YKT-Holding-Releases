<p align="center">
  <img src="assets/ykt-holding-logo.png" alt="YKT Holding — YKTera" width="128" height="128" />
</p>

<h1 align="center">YKT Holding</h1>

<p align="center">
  <strong>YKTera</strong> tarafından geliştirilen çok-motorlu yapay zeka organizasyon ve ajan yönetim platformu.<br/>
  Yerli masaüstü uygulamasından şirketlerinizi, projelerinizi, otonom ajanlarınızı, kalıcı hafızanızı ve gömülü tarayıcınızı yönetin.
</p>

<p align="center">
  <strong>Güncel Sürüm:</strong> <code>v1.7.0</code> (2026-11-21) &nbsp;·&nbsp;
  <a href="https://github.com/ecankinsundev/YKT-Holding-Releases/releases/tag/v1.7.0">Sürüm Sayfası</a> &nbsp;·&nbsp;
  <a href="CHANGELOG.md">Tüm Sürüm Notları</a>
</p>

---

## İndirme (v1.7.0)

| Platform | Paket Türü | İndirme Bağlantısı | SHA-256 |
|---|---|---|---|
| **Windows x64** | Kurulum Sihirbazı (Önerilen) | [`YKT-Holding_1.7.0_x64-setup.exe`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.7.0/YKT-Holding_1.7.0_x64-setup.exe) | `b7194386d128236720bf34b221a3a5a59e6585a62cad678c5d7d7cf7d70711cf` |
| **Windows x64** | Portatif Arşiv (Kurulumsuz) | [`YKT-Holding_1.7.0_x64-portatif.zip`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.7.0/YKT-Holding_1.7.0_x64-portatif.zip) | `4df93afaf904a4dd226d523eaa4aad0bedaa679876a67af88f9f767c935a0a3c` |
| **Güncelleme Manifestosu** | Sürüm Kaydı | [`latest.json`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.7.0/latest.json) | — |

> **Bütünlük Doğrulama (PowerShell):**
> ```powershell
> (Get-FileHash .\YKT-Holding_1.7.0_x64-setup.exe -Algorithm SHA256).Hash.ToLower() -eq "b7194386d128236720bf34b221a3a5a59e6585a62cad678c5d7d7cf7d70711cf"
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
1. Yukarıdaki tablodan **`YKT-Holding_1.7.0_x64-setup.exe`** dosyasını indirin ve çalıştırın (yönetici izni gerektirmez).
2. Uygulama `%LOCALAPPDATA%\YKT Holding` klasörüne kurulur, kullanıcı `PATH` ortam değişkenine `ykt` komutunu ekler ve Başlat Menüsü / Masaüstü kısayollarını oluşturur.
3. **YKT Holding** uygulamasını açın; ilk açılış sihirbazı çalışma klasörünüzü, şirket/ekip yapınızı ve `ykt-guard` güvenlik kapılarını otomatik yapılandırır.

### Seçenek 2 — Portatif ZIP (Kurulumsuz)
1. **`YKT-Holding_1.7.0_x64-portatif.zip`** arşivini dilediğiniz klasöre çıkartın.
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

## Mevcut Sürümde Neler Var? (v1.7.0)

### Yenilikler ve Duzeltmeler
- **Antigravity Canli Kota & Tam Gorunurluk (`ykt butce --canli` + `--agy`):**
  - Resmi ve **0 token** tuketen `agy --output-format json -p="/usage"` komutu `butce_canli.rs` icine entegre edildi; her `ykt butce --canli` (ve yeni `--agy`) calismasinda `Gemini Models` ve `Claude and GPT models` (Haftalik + 5 Saatlik) kalan/kullanilan yuzdeleri ile kesin yerel sifirlama saatleri `durum/agy-kullanim.json` dosyasina atomik yazilir.
  - `Kullanim ve Limitler` ve `Ayarlar > Kota ve butce` ekranlarina **`Canli olcum`** rozeti (yas ve `reset_time` tazelik denetimli) ile **`Antigravity Olc`** dugmesi eklendi; hata/zaman asimi durumunda son gecerli dosya korunur ve Claude olcumu kesintiye ugramaz.
- **Fable 5.2 & Tum Antigravity Modellerinin Tam Gorunurlugu (`motor_secim.rs` + `modeller.json`):**
  - Eski `Fable 5.1` etiketi **`Fable 5.2`** olarak guncellendi; tum model secicilerde (Kart Paneli, Ajan Sag-Tik Menusu, Ajan Ozellikleri, `Model havuzu`) **Claude Code** (`Fable 5.2`, `Opus 5.5`, `Sonnet 5.5`, `Haiku 5.5`) ve **Antigravity** (`AGY Neon (High)`, `AGY Neon (XHigh)`, `AGY Carbon`, `AGY Argon`, `AGY Hydrogen`, `AGY Flash 3.8`, `AGY Opus 5.5`, `AGY Sonnet 5.5`) gruplu ve acik bicimde listelenir.
  - Ajan Ozellikleri acilir kutusundaki Antigravity model adlarindan tire silen hata giderildi; `sablonlar/modeller.json` kataloguna `agy-neon-xhigh` ve `agy-hydrogen-high` eklendi.
- **Gelistiriciye Bildir Dogrudan E-posta API Arayuzu (`ekinsun@yktera.com`):**
  - `Ayarlar > Hakkinda > Gelistiriciye bildir` altina acilir **`Dogrudan e-posta API ayari (Resend)`** bolumu eklendi: maskeli `BILDIRIM_EPOSTA_ANAHTAR` ve istege bagli `BILDIRIM_EPOSTA_KIMDEN` dar erisim izniyle (`~/.ykt/anahtarlar.json`, ajan ortamlarina asla verilmez) kaydedilip silinebilir, **`Test bildirimi gonder`** dugmesiyle tek tikla dogrulanabilir.
  - `ykt-core::anahtar` tum kontrol karakterlerini (CRLF/null) reddeder; Resend 401/403/422 hata mesajlari anahtari ve ham yaniti asla sizdirmaz.
- **Resimli Turkce Kullanici Kilavuzu PDF (`docs/YKT-Holding-Kullanim-Kilavuzu.pdf`):**
  - "Sirket mi, Proje mi, Kart mi?" karar rehberi (sosyal medya hesabi yonetimi dahil 7 gercek hayat ornegi), 23 hazir ekip paketi, 2.5D ofis, `Okunakli | Teknik` hibrit terminal, canli kota ve K0 guvenlik kapisi ekran goruntuleriyle 10 sayfalik PDF olarak GitHub depolarina eklendi.

---

> Detaylı sürüm geçmişi için [CHANGELOG.md](CHANGELOG.md) dosyasına bakın.  
> **YKT Holding** · Geliştiren: **YKTera** · Tüm hakları saklıdır.
