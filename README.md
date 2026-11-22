<p align="center">
  <img src="assets/ykt-holding-logo.png" alt="YKT Holding — YKTera" width="128" height="128" />
</p>

<h1 align="center">YKT Holding</h1>

<p align="center">
  <strong>YKTera</strong> tarafından geliştirilen çok-motorlu yapay zeka organizasyon ve ajan yönetim platformu.<br/>
  Yerli masaüstü uygulamasından şirketlerinizi, projelerinizi, otonom ajanlarınızı, kalıcı hafızanızı ve gömülü tarayıcınızı yönetin.
</p>

<p align="center">
  <strong>Güncel Sürüm:</strong> <code>v1.8.2</code> (2026-11-22) &nbsp;·&nbsp;
  <a href="https://github.com/ecankinsundev/YKT-Holding-Releases/releases/tag/v1.8.2">Sürüm Sayfası</a> &nbsp;·&nbsp;
  <a href="CHANGELOG.md">Tüm Sürüm Notları</a>
</p>

---

## İndirme (v1.8.2)

| Platform | Paket Türü | İndirme Bağlantısı | SHA-256 |
|---|---|---|---|
| **Windows x64** | Kurulum Sihirbazı (Önerilen) | [`YKT-Holding_1.8.2_x64-setup.exe`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.8.2/YKT-Holding_1.8.2_x64-setup.exe) | `bdd18a10c326041510611bba66bfedc116ffedd2c9cdb69c851311f80a43135c` |
| **Windows x64** | Portatif Arşiv (Kurulumsuz) | [`YKT-Holding_1.8.2_x64-portatif.zip`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.8.2/YKT-Holding_1.8.2_x64-portatif.zip) | `116019be3f8428b4966f8ecfe2766d5308c55c5045764fc8350834f97544124f` |
| **Güncelleme Manifestosu** | Sürüm Kaydı | [`latest.json`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.8.2/latest.json) | — |

> **Bütünlük Doğrulama (PowerShell):**
> ```powershell
> (Get-FileHash .\YKT-Holding_1.8.2_x64-setup.exe -Algorithm SHA256).Hash.ToLower() -eq "bdd18a10c326041510611bba66bfedc116ffedd2c9cdb69c851311f80a43135c"
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
1. Yukarıdaki tablodan **`YKT-Holding_1.8.2_x64-setup.exe`** dosyasını indirin ve çalıştırın (yönetici izni gerektirmez).
2. Uygulama `%LOCALAPPDATA%\YKT Holding` klasörüne kurulur, kullanıcı `PATH` ortam değişkenine `ykt` komutunu ekler ve Başlat Menüsü / Masaüstü kısayollarını oluşturur.
3. **YKT Holding** uygulamasını açın; ilk açılış sihirbazı çalışma klasörünüzü, şirket/ekip yapınızı ve `ykt-guard` güvenlik kapılarını otomatik yapılandırır.

### Seçenek 2 — Portatif ZIP (Kurulumsuz)
1. **`YKT-Holding_1.8.2_x64-portatif.zip`** arşivini dilediğiniz klasöre çıkartın.
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

## Mevcut Sürümde Neler Var? (v1.8.2)

### Yenilikler ve Duzeltmeler
- **2.5D Cam Asansor, Ferah En Ust Kat Luks Yonetim Kati & Katlar Arasi Yonetici Ziyareti (`proje.rs`, `proje_yasam.rs`, `kampus.rs`, `ofis.rs`, `iso_hareket.rs`, `izometrik.rs`):**
  - Her cok katli sirket binasinin **en ust kati daima Yonetim Kati'dir (`id: "yonetim"`, `ad: "Yonetim Kati"`, `katlar.last()`)**: tek yonetici varsa ust katta tek basina luks penthouse odasinda (`10x7` karo, gece-lacivert hali + cift seritli altin/camgobegi cerceve, strateji panosu, 2 kose salon bitkisi, misafir koltuklari, pirinc lamba), birden fazla yonetici varsa tumunun luks odalari ayni Yonetim Kati'nda (`8x6` karo) yer alir; alt proje katlarinda tek tek yonetici odasi acilmaz.
  - Cok katli binalara sol omurgada 4 kamera acisina donen tiklanabilir **2.5D cam asansor safti** eklendi (`K1`/`K2`/`YK` gostergesi, yon oklari, bosta 0 FPS).
  - Ust kattaki yonetici alt katta aktif is verirken asansorle inip ilgili personelin bireysel odasina yurur (`Teslim`), alt kattaki calisan soru/engel durumunda ust kattaki yoneticiye asansorle cikar (`Danis`); tek kaynakli deterministik ziyaret hesabiyla ajanlar asla iki katta birden klonlanmaz ve varista 0 FPS'e doner.
  - `tema_tahmini` icindeki kisa (`<5` karakter, or. `"sla"`) anahtar kelimelerin ilgisiz proje adlarinda yanlis tema secmesi hatasi giderildi.
- **Ctrl+V Panodan Dogrudan Gorsel Ekleme (`bildir.rs`, `ekran.rs`, `konusmalar.rs`, `sihirbaz.rs`, `lib.rs`):**
  - Kart Paneli (`Okunakli` ve `Teknik`), `Konusmalar` (Grup/Ajan/Kurulus), Proje Sihirbazi Adim 2 ve `Gelistiriciye bildir` metin kutularinda `Ctrl+V` (`egui::Event::PasteImage` + Windows `CF_DIB` yedegi), `+ Gorsel` dugmesi ve surukle-birak ile dogrudan ekran goruntusu eklenebilir.
  - Tum gorseller mevcut kati guvenlik boru hattindan (`<= 5 MB`, `<= 8192px`, symlink reddi, magic-byte + EXIF/polyglot temizligi + PNG yeniden kodlama, atomik yazim) gecerek `<kok>/durum/ekler/` altina kaydedilir; 32x32 onizleme cipi + `[x]` kaldirma sunulur ve gonderilmeden vazgecilen taslak gorselleri diskten otomatik temizlenir.
- **Yonetici Model & Devir Politikasi + Efor Tavani (`ekip.rs`, `havuz.rs`, `motor.rs`, `politika.rs`, `pm.rs`, `proje.rs`, `agents/{yonetici,proje-lideri}.md`):**
  - Kota dolmadikca tum yoneticiler (`rol == "yonetici"`) proje uzmanlik alanina gore **`claude / fable` (Fable 5.2)** (mimari, guvenlik/uyum, finans, gomulu/donanim, masaustu/oyun) veya **`antigravity / gemini-4-neon-high` (AGY Neon High)** (web, mobil, sosyal medya, icerik, pazarlama/SEO, satis/CRM, destek, veri/arastirma) olarak atanir.
  - Yonetici kota devri **`Fable 5.2 <-> AGY Neon High`** olarak degisir; yalniz ikisinin de kotasi dolarsa **`Claude Opus 5.5`**'e duser (gizli kartlarda K0/Claude siniri korunur).
  - Patron elle degistirmedikce otomatik efor, `proje politikasi` ve `ykt plan kartlar` WBS kartlari **en fazla `high`** ile sinirlanir; Patron'un kartta veya kadroda elle verdigi `xhigh`/`max` tercihleri korunur.
- **Arka Planda Calisma & Windows Sistem Tepsisi + Sol Menu `Cikis` Dugmesi (`sistem/tepsi.rs`, `ekran.rs`, `lib.rs`, `main.rs`):**
  - Sol menunun en altina **`Cikis`** dugmesi eklendi; normal guvenli kapatma sureci (`Sistem::kapat`, calisan ajan/taslak sorusu, cocuk temizligi) yalniz sol menu `Cikis` veya sistem tepsisi sag tik `Cikis` secildiginde yurutulur.
  - Pencere carpisina (`X`) basildiginda uygulama kapatilmaz, sag alt Windows sistem tepsisine gizlenerek arka planda calismaya devam eder (`eframe::App::logic` ile gizliyken de olay/veri tazeleme, calisan dongusu izleme ve saglik/butce tiki surer); tepsi simgesine tikla `Goster`/`Gizle`, sag tik ile `Goster` / `Gizle (Tepsiye al)` / `Cikis` secilebilir, ikinci exe acilisi gizli pencereyi geri getirir.
- **Konusmalar Vazgecilen Kurulus Filtresi & Grup Ayrimi (`konusmalar.rs`):**
  - Kurmaktan vazgecilen (`durum: "iptal"`) proje kurulus taslaklari artik `Konusmalar` listesini kirletmez; grup listesi acikca **`OFIS VE SIRKETLER`** ve **`PROJELER`** basliklarina ayrildi.

---

> Detaylı sürüm geçmişi için [CHANGELOG.md](CHANGELOG.md) dosyasına bakın.  
> **YKT Holding** · Geliştiren: **YKTera** · Tüm hakları saklıdır.
