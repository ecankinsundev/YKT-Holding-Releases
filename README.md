<p align="center">
  <img src="assets/ykt-holding-logo.png" alt="YKT Holding — YKTera" width="128" height="128" />
</p>

<h1 align="center">YKT Holding</h1>

<p align="center">
  <strong>YKTera</strong> tarafından geliştirilen çok-motorlu yapay zeka organizasyon ve ajan yönetim platformu.<br/>
  Yerli masaüstü uygulamasından şirketlerinizi, projelerinizi, otonom ajanlarınızı, kalıcı hafızanızı ve gömülü tarayıcınızı yönetin.
</p>

<p align="center">
  <strong>Güncel Sürüm:</strong> <code>v1.8.8</code> (2026-11-24) &nbsp;·&nbsp;
  <a href="https://github.com/ecankinsundev/YKT-Holding-Releases/releases/tag/v1.8.8">Sürüm Sayfası</a> &nbsp;·&nbsp;
  <a href="CHANGELOG.md">Tüm Sürüm Notları</a>
</p>

---

## İndirme (v1.8.8)

| Platform | Paket Türü | İndirme Bağlantısı | SHA-256 |
|---|---|---|---|
| **Windows x64** | Kurulum Sihirbazı (Önerilen) | [`YKT-Holding_1.8.8_x64-setup.exe`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.8.8/YKT-Holding_1.8.8_x64-setup.exe) | `f381cf296dda3eb607493ead5bdfdb419f02a12efa6c53611d3763a11b5bec53` |
| **Windows x64** | Portatif Arşiv (Kurulumsuz) | [`YKT-Holding_1.8.8_x64-portatif.zip`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.8.8/YKT-Holding_1.8.8_x64-portatif.zip) | `46c4a9a8746d525694913d9e4b990f1480a04ca6ab5f10d625cdf057e8b046d6` |
| **Güncelleme Manifestosu** | Sürüm Kaydı | [`latest.json`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.8.8/latest.json) | — |

> **Bütünlük Doğrulama (PowerShell):**
> ```powershell
> (Get-FileHash .\YKT-Holding_1.8.8_x64-setup.exe -Algorithm SHA256).Hash.ToLower() -eq "f381cf296dda3eb607493ead5bdfdb419f02a12efa6c53611d3763a11b5bec53"
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
1. Yukarıdaki tablodan **`YKT-Holding_1.8.8_x64-setup.exe`** dosyasını indirin ve çalıştırın (yönetici izni gerektirmez).
2. Uygulama `%LOCALAPPDATA%\YKT Holding` klasörüne kurulur, kullanıcı `PATH` ortam değişkenine `ykt` komutunu ekler ve Başlat Menüsü / Masaüstü kısayollarını oluşturur.
3. **YKT Holding** uygulamasını açın; ilk açılış sihirbazı çalışma klasörünüzü, şirket/ekip yapınızı ve `ykt-guard` güvenlik kapılarını otomatik yapılandırır.

### Seçenek 2 — Portatif ZIP (Kurulumsuz)
1. **`YKT-Holding_1.8.8_x64-portatif.zip`** arşivini dilediğiniz klasöre çıkartın.
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

## Mevcut Sürümde Neler Var? (v1.8.8)

### Duzeltmeler
- **Sade Ajan Ustu Etiketi (`kampus/izometrik.rs`):**
  - 2.5D ic kat kesitinde her ajanin uzerindeki cam rozette artik adinin yaninda unvani tekrarlanmaz (odalarin cam duvarinda zaten isim + unvan yer alir); boylece yan yana gelen ajan etiketleri sade ve cakismasiz gorunur.
  - Ajanin uzerine tiklandiginda acilan Hizli Ajan Karti'nda gorevi/unvani (`Ad — Unvan`, unvan bossa `rol` yedekli) gosterilmeye devam eder.
- **Canli Orkestrasyon Odalari Esitlemesi:**
  - `YKT Orkestrasyon Muhendislik` binasindaki 6 bireysel odanin adlari diger sirketlerle ayni `<Ad> - <Rol>` standardina esitlendi.

---

> Detaylı sürüm geçmişi için [CHANGELOG.md](CHANGELOG.md) dosyasına bakın.  
> **YKT Holding** · Geliştiren: **YKTera** · Tüm hakları saklıdır.
