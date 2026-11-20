<p align="center">
  <img src="assets/ykt-holding-logo.png" alt="YKT Holding — YKTera" width="128" height="128" />
</p>

<h1 align="center">YKT Holding</h1>

<p align="center">
  <strong>YKTera</strong> tarafından geliştirilen çok-motorlu yapay zeka organizasyon ve ajan yönetim platformu.<br/>
  Yerli masaüstü uygulamasından şirketlerinizi, projelerinizi, otonom ajanlarınızı, kalıcı hafızanızı ve gömülü tarayıcınızı yönetin.
</p>

<p align="center">
  <strong>Güncel Sürüm:</strong> <code>v1.0.3</code> (2026-11-20) &nbsp;·&nbsp;
  <a href="https://github.com/ecankinsundev/YKT-Holding-Releases/releases/tag/v1.0.3">Sürüm Sayfası</a> &nbsp;·&nbsp;
  <a href="CHANGELOG.md">Tüm Sürüm Notları</a>
</p>

---

## İndirme (v1.0.3)

| Platform | Paket Türü | İndirme Bağlantısı | SHA-256 |
|---|---|---|---|
| **Windows x64** | Kurulum Sihirbazı (Önerilen) | [`YKT-Holding_1.0.3_x64-setup.exe`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.0.3/YKT-Holding_1.0.3_x64-setup.exe) | `1e643b7850945e570539ea5e38f6e610452f4c75219d35c924a2a142456cf959` |
| **Windows x64** | Portatif Arşiv (Kurulumsuz) | [`YKT-Holding_1.0.3_x64-portatif.zip`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.0.3/YKT-Holding_1.0.3_x64-portatif.zip) | `eec140b191d1a1f17ef4c61104f3106ad1c024891ff9e635b4b3e7789e25c819` |
| **Güncelleme Manifestosu** | Sürüm Kaydı | [`latest.json`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.0.3/latest.json) | — |

> **Bütünlük Doğrulama (PowerShell):**
> ```powershell
> (Get-FileHash .\YKT-Holding_1.0.3_x64-setup.exe -Algorithm SHA256).Hash.ToLower() -eq "1e643b7850945e570539ea5e38f6e610452f4c75219d35c924a2a142456cf959"
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
1. Yukarıdaki tablodan **`YKT-Holding_1.0.3_x64-setup.exe`** dosyasını indirin ve çalıştırın (yönetici izni gerektirmez).
2. Uygulama `%LOCALAPPDATA%\YKT Holding` klasörüne kurulur, kullanıcı `PATH` ortam değişkenine `ykt` komutunu ekler ve Başlat Menüsü / Masaüstü kısayollarını oluşturur.
3. **YKT Holding** uygulamasını açın; ilk açılış sihirbazı çalışma klasörünüzü, şirket/ekip yapınızı ve `ykt-guard` güvenlik kapılarını otomatik yapılandırır.

### Seçenek 2 — Portatif ZIP (Kurulumsuz)
1. **`YKT-Holding_1.0.3_x64-portatif.zip`** arşivini dilediğiniz klasöre çıkartın.
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

## Mevcut Sürümde Neler Var? (v1.0.3)

### Yenilikler ve Duzeltmeler
- **Otomatik Butce Kalibrasyonu & Sakin Arayuz:** `ykt butce` artik kalibrasyonsuz taze kurulumda hata vermez, oturum verilerini sessizce tarar ve ilk gercek Claude Code `rate_limit_event` olcumuyle kendi tavanini otomatik kalibre eder; `%0` / `%5` alti dusuk yuzde olcumleri mevcut gecerli tavani bozmaz (`HAFTA_ESIGI = 5.0`). Calisan dongusu kapaliyken arayuz arka planda 15 dakikada bir sessizce `ykt butce` calistirir. Ust seritteki ve `Kullanim` / `Ayarlar > Kota ve butce` ekranlarindaki sari kalibrasyon uyarilari kaldirildi; elle kalibrasyon `Ayarlar > Kota ve butce` altinda istege bagli acilir bolume (`Elle kalibrasyon (istege bagli)`) alindi.
- **Sade Ust Serit:** Ust seritteki sabit 3'lu butce/limit cubuklari kaldirildi (tum limitler soldaki `Kullanim` sekmesinde). Ust serit tek satirda yalniz onay/kosan/olay cipleri, `Sehir gorunumu` anahtari ve sehir gizliyken kalici `Kosan is: N  |  Patron onayi bekleyen: M  |  Ajan: K` ozet bilgisini gosterir.
- **Sehir Gorunumu Gizliyken Varsayilan `Tahta | Konusmalar`:** `Sehir gorunumu` kapatildiginda (veya gizli tercihli acilista acik panel yoksa) ekran bos kalmaz; `Tahta` ve `Konusmalar` varsayilan olarak yan yana acilir, ozet bilgi satiri gorunmeye devam eder.
- **`Projeler` ve `Tahta` Sekme Duzeltmesi:** Sol menude **`Projeler`**'e tiklamak dogrudan `Proje listesi` (`+ Yeni proje` ve proje kartlari) gorunumunu, **`Tahta`**'ya tiklamak ise Kanban is tahtasini acar.

---

> Detaylı sürüm geçmişi için [CHANGELOG.md](CHANGELOG.md) dosyasına bakın.  
> **YKT Holding** · Geliştiren: **YKTera** · Tüm hakları saklıdır.
