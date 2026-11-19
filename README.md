<p align="center">
  <img src="assets/ykt-holding-logo.png" alt="YKT Holding — YKTera" width="128" height="128" />
</p>

<h1 align="center">YKT Holding</h1>

<p align="center">
  <strong>YKTera</strong> tarafından geliştirilen çok-motorlu yapay zeka organizasyon ve ajan yönetim platformu.<br/>
  Yerli masaüstü uygulamasından şirketlerinizi, projelerinizi, otonom ajanlarınızı, kalıcı hafızanızı ve gömülü tarayıcınızı yönetin.
</p>

<p align="center">
  <strong>Güncel Sürüm:</strong> <code>v1.0.0</code> (2026-11-19) &nbsp;·&nbsp;
  <a href="https://github.com/ecankinsundev/YKT-Holding-Releases/releases/tag/v1.0.0">Sürüm Sayfası</a> &nbsp;·&nbsp;
  <a href="CHANGELOG.md">Tüm Sürüm Notları</a>
</p>

---

## İndirme (v1.0.0)

| Platform | Paket Türü | İndirme Bağlantısı | SHA-256 |
|---|---|---|---|
| **Windows x64** | Kurulum Sihirbazı (Önerilen) | [`YKT-Holding_1.0.0_x64-setup.exe`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.0.0/YKT-Holding_1.0.0_x64-setup.exe) | `6e31f63314f4cb64306a4b0293f6d0ffd1c3786b3d764705eb542f0ee63c2298` |
| **Windows x64** | Portatif Arşiv (Kurulumsuz) | [`YKT-Holding_1.0.0_x64-portatif.zip`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.0.0/YKT-Holding_1.0.0_x64-portatif.zip) | `c9324910ab8858dc77a74371d589d63c4d6bdabb66b694a3f197ee8bee80b515` |
| **Güncelleme Manifestosu** | Sürüm Kaydı | [`latest.json`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.0.0/latest.json) | — |

> **Bütünlük Doğrulama (PowerShell):**
> ```powershell
> (Get-FileHash .\YKT-Holding_1.0.0_x64-setup.exe -Algorithm SHA256).Hash.ToLower() -eq "6e31f63314f4cb64306a4b0293f6d0ffd1c3786b3d764705eb542f0ee63c2298"
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
1. Yukarıdaki tablodan **`YKT-Holding_1.0.0_x64-setup.exe`** dosyasını indirin ve çalıştırın (yönetici izni gerektirmez).
2. Uygulama `%LOCALAPPDATA%\YKT Holding` klasörüne kurulur, kullanıcı `PATH` ortam değişkenine `ykt` komutunu ekler ve Başlat Menüsü / Masaüstü kısayollarını oluşturur.
3. **YKT Holding** uygulamasını açın; ilk açılış sihirbazı çalışma klasörünüzü, şirket/ekip yapınızı ve `ykt-guard` güvenlik kapılarını otomatik yapılandırır.

### Seçenek 2 — Portatif ZIP (Kurulumsuz)
1. **`YKT-Holding_1.0.0_x64-portatif.zip`** arşivini dilediğiniz klasöre çıkartın.
2. Klasör içindeki `ykt-holding.exe` dosyasını çalıştırın.

### Mevcut Sürümden Güncelleme
- Yeni `setup.exe` dosyasını doğrudan mevcut kurulumun üzerine çalıştırabilirsiniz (kullanıcı verileriniz, projeleriniz, kartlarınız ve hafızanız korunur).
- Uygulama ilk açılışta yeni sürümü algılar ve `ykt kur --yenile` ile rol tanımlarını, skill'leri ve K0 güvenlik kapısını otomatik tazeler.

---

## Nasıl Kullanılır?

### 1. Masaüstü Arayüzü (6 Ana Bölüm)
- **Kampüs (Arka Plan):** Şirket binalarınızı, proje ekiplerinizi ve çalışan ajanları canlı izlediğiniz etkileşimli görünüm. Ajanlara tıklayarak anlık görev detayını veya canlı terminalini açabilirsiniz.
- **Konuşmalar:** Holding Genel Müdürü ve proje liderleriyle doğal Türkçe mesajlaşarak iş kartları planlayın, karar verin veya onay verin.
- **Projeler (Tahta · Liste · Plan · Akış · Organizasyon):** Tüm şirket ve projelerinizi, kart durum sütunlarını (`Tahta`), canlı delegasyon grafiğini (`Akış`) ve şirket/ekip yapısını (`Organizasyon`) tek pencerede yönetin.
- **Hafıza:** Obsidian uyumlu kalıcı Markdown bilgi tabanı, dersler ve karar kayıtları.
- **Tarayıcı:** Uygulama içi gömülü WebView2 tarayıcısı; ajanların web araştırması ve önizleme adımlarını aynı pencerede güvenle izleyin (giriş/2FA/ödeme adımlarında ajan otomatik durur ve kontrolü size bırakır).
- **Ayarlar:** Tema (Gece / Gündüz WCAG AA), **Kota ve bütçe** (haftalık/5s limitler ve ayrı **Fable** havuzu), **Bağlantılar > Motorlar** (tek tıkla **"Motorları güncelle"**), güvenlik kapısı ve sistem sağlığı.

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

## Mevcut Sürümde Neler Var? (v1.0.0)

### Yenilikler
- **YKTera / YKT Holding Marka Kimligi & Yeni Logo:** Altin geometrik `Y` monogrami ve elektrik-camgobegi yapay zeka elmas dugumuyle yeni `icon.png` / `icon.ico` / `icon.icns` uygulama simgeleri, sol menu marka rozeti ve `Ayarlar > Hakkinda` logosu tek elden yenilendi.
- **Gomulu Tarayici (Windows Glow + WebView2):** `eframe 0.37` Windows'ta varsayilan `Glow` (OpenGL) cizici + `WS_CLIPCHILDREN` ile gomulu WebView2 sekmeleri tam calisir hale getirildi (OpenGL yoksa otomatik `Wgpu` yedeklemesi); gercek URL'den kilit simgesi, sayfa ici URL senkronizasyonu, `Git` odak korumasi, `baglanti_istendi` CDP kuyruk korumasi, yetim WebView2 temizligi ve siki `localhost`/userinfo URL siniri eklendi.
- **Sade Kampus & WCAG AA Arayuz:** Sehir gorunumunden turuncu/beyaz parcacik yagmuru, konteyner/vinc/forklift/duman/kivilcim ogeleri kaldirildi; araclar yalniz aktif is varken gorunur. Sol menu 6 bolume indi (`Organizasyon` -> `Projeler` ust sekmesi), `Hesap`/`Bulten` kaldirildi, `Maliyet` -> `Kota ve butce` altinda birlestirildi, `"Nagihan"` -> `"Kalite denetimi"` oldu, Gece/Gunduz WCAG AA (`>= 4.5:1`) kontrast oranlari testle kilitlendi.
- **Motor Otomatik Guncelleme (`ykt motor guncelle`):** `claude update` ve `agy update` icin CLI alt komutu, `Ayarlar > Baglantilar > Motorlar > Motorlari guncelle` dugmesi, OS cekirdek `File::try_lock()` kilidi, zaman asiminda `taskkill /T /F` temizligi ve 6 saatlik ayri arka plan guncelleyici eklendi.
- **Tuketim Butcesi Duyarli `Fable` & `Gemini 4 Neon`:** Ayri haftalik Fable havuzu (`hafta_fable_yuzde`, `fable_esik`) arayuze baglandi; derin mimari/kok-neden/guvenlik isleri sayac taze ve koruma sinirinin altindayken `opus -> fable` terfi edilir, kuyrukta kota dolarsa yalniz otomatik terfiler `opus`'a iner (acik Patron secimi korunur). Kataloga `agy-neon-high` (`gemini-4-neon-high`) ve `agy-neon` (`gemini-4-neon-medium`) eklendi (15 model, `-xhigh` destekli).
- **Yayin Hatti (`YKT-Holding-Releases`):** `YAYIN_DEPOSU` `ecankinsundev/YKT-Holding-Releases` olarak yapilandirildi ve `crates/ykt-holding/paket/yayinla.js` ile her surumde kurulum/kullanim rehberi (`README.md`), `CHANGELOG.md`, `latest.json` ve GitHub Release varliklarinin otomatik yayinlanmasi eklendi.

---

> Detaylı sürüm geçmişi için [CHANGELOG.md](CHANGELOG.md) dosyasına bakın.  
> **YKT Holding** · Geliştiren: **YKTera** · Tüm hakları saklıdır.
