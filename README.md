<p align="center">
  <img src="assets/ykt-holding-logo.png" alt="YKT Holding — YKTera" width="128" height="128" />
</p>

<h1 align="center">YKT Holding</h1>

<p align="center">
  <strong>YKTera</strong> tarafından geliştirilen çok-motorlu yapay zeka organizasyon ve ajan yönetim platformu.<br/>
  Yerli masaüstü uygulamasından şirketlerinizi, projelerinizi, otonom ajanlarınızı, kalıcı hafızanızı ve gömülü tarayıcınızı yönetin.
</p>

<p align="center">
  <strong>Güncel Sürüm:</strong> <code>v1.2.0</code> (2026-11-21) &nbsp;·&nbsp;
  <a href="https://github.com/ecankinsundev/YKT-Holding-Releases/releases/tag/v1.2.0">Sürüm Sayfası</a> &nbsp;·&nbsp;
  <a href="CHANGELOG.md">Tüm Sürüm Notları</a>
</p>

---

## İndirme (v1.2.0)

| Platform | Paket Türü | İndirme Bağlantısı | SHA-256 |
|---|---|---|---|
| **Windows x64** | Kurulum Sihirbazı (Önerilen) | [`YKT-Holding_1.2.0_x64-setup.exe`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.2.0/YKT-Holding_1.2.0_x64-setup.exe) | `9bbd146b1f291ebecf4a7f0dc0311942d81842d03ab7dbf1a4ddf777ffbdd018` |
| **Windows x64** | Portatif Arşiv (Kurulumsuz) | [`YKT-Holding_1.2.0_x64-portatif.zip`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.2.0/YKT-Holding_1.2.0_x64-portatif.zip) | `426fc6e8d9e92a3ebc1e2342585a5f3486471956e33b08db88b1868d4a69bd30` |
| **Güncelleme Manifestosu** | Sürüm Kaydı | [`latest.json`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.2.0/latest.json) | — |

> **Bütünlük Doğrulama (PowerShell):**
> ```powershell
> (Get-FileHash .\YKT-Holding_1.2.0_x64-setup.exe -Algorithm SHA256).Hash.ToLower() -eq "9bbd146b1f291ebecf4a7f0dc0311942d81842d03ab7dbf1a4ddf777ffbdd018"
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
1. Yukarıdaki tablodan **`YKT-Holding_1.2.0_x64-setup.exe`** dosyasını indirin ve çalıştırın (yönetici izni gerektirmez).
2. Uygulama `%LOCALAPPDATA%\YKT Holding` klasörüne kurulur, kullanıcı `PATH` ortam değişkenine `ykt` komutunu ekler ve Başlat Menüsü / Masaüstü kısayollarını oluşturur.
3. **YKT Holding** uygulamasını açın; ilk açılış sihirbazı çalışma klasörünüzü, şirket/ekip yapınızı ve `ykt-guard` güvenlik kapılarını otomatik yapılandırır.

### Seçenek 2 — Portatif ZIP (Kurulumsuz)
1. **`YKT-Holding_1.2.0_x64-portatif.zip`** arşivini dilediğiniz klasöre çıkartın.
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

## Mevcut Sürümde Neler Var? (v1.2.0)

### Yenilikler ve Duzeltmeler
- **2.5D Izometrik 4 Yonlu Kamera Dondurme (`< Sol` / `Sag >`, `Q` / `R`):** Hem dis kampuste hem bina ici 2.5D kat kesitinde 90° adimlarla 4 izometrik bakis acisi (`On 0°`, `Sag 90°`, `Arka 180°`, `Sol 270°`) eklendi ([izometrik.rs](crates/ykt-holding/src/kampus/izometrik.rs)). Binalar, cam kopruler, kopruden suzulen ajanlar, kat odalari, masalar, ajan figurleri ve poligon isabet testi aktif aciya gore gercek zamanli dondurulup derinlik siralanir.
- **Hem 2.5D Hem Klasik Icin Yerinde Duzenleme ve 2.5D Bina Kozmetikleri (`Duzenle (E)`):**
  - 2.5D gorunumde `Duzenle (E)` artik klasik kipe atlamadan dogrudan 2.5D uzerinde acilir.
  - **Dis Kampus 2.5D Duzenleme:** Secili binayi yeniden adlandir, aktif kamera acisina gore ekrana uyumlu tasi (`Sola / Saga / Yukari / Asagi`, `tasima_deltasi`), `Geri al` ve `BinaKozmetik` ile her projenin/sirketin 2.5D mimarisini ozellestir (**Stil:** `Oto | Kule | Pavyon | Studyo`, **Vurgu:** `Oto | Camgobegi | Zumrut | Kehribar | Mor`, **Kat:** `Oto | 1..4`; [kampus_yaz.rs](crates/ykt-core/src/kampus_yaz.rs)). Merkez binasi (`YKT Merkez`) kozmetik/ad/silme degisikliklerine karsi korunur, secim ve kamera duzenleme boyunca korunur.
  - **Bina Ici 2.5D Kat Duzenleme:** Odaya tiklayip secme (duzenleme acikken hizli ajan kartiyla cakismaz), `Otomatik / Elle` yerlesim gecisi, `+ Oda`, `Adlandir`, ekrana gore `Sola / Saga / Yukari / Asagi` tasima, `+ Masa`, `- Masa`, onayli `Oda sil` ve `Geri al`.
- **`Klasik Piksel` Gorunumu ve Acik `Aydinlik / Karanlik` Modu `Ayarlar > Makine ve surecler > Tema` Altinda:**
  - Varsayilan ofis gorunumu **2.5D Izometrik**'tir; ust cubuktaki `2.5D / Klasik` dugmeleri kaldirilip **`Ayarlar > Makine ve surecler > Tema`** altina tasindi (`2.5D Izometrik` / `Klasik Piksel`, `~/.ykt/arayuz-ofis-kipi.txt`; [ayarlar.rs](crates/ykt-holding/src/ayarlar.rs)).
  - Ayni sayfada tum uygulamaya (2.5D Ofis dahil) uygulanan **`Gorunum modu (Aydinlik / Karanlik)`** secimi (`Gunduz`, `Gece`, `Otomatik`) belirgin baslik ve aciklamalarla netlestirildi.
- **Sehir Gorunumu Aktifken Sabit `Tahta | Konusmalar` Gelmez:** `Sehir gorunumu` kapaliyken `Tahta | Konusmalar` yan yana acilmaya devam eder; `Sehir gorunumu` tekrar acildiginda ekranda yalniz bu varsayilan paneller varsa otomatik kapanir ve 2.5D Ofis engelsiz gorunur ([lib.rs](crates/ykt-holding/src/lib.rs)). Kullanicinin actigi `Hafiza` gibi baska paneller veri kaybi olmadan katlanir.

---

> Detaylı sürüm geçmişi için [CHANGELOG.md](CHANGELOG.md) dosyasına bakın.  
> **YKT Holding** · Geliştiren: **YKTera** · Tüm hakları saklıdır.
