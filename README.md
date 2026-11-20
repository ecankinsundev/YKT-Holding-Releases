<p align="center">
  <img src="assets/ykt-holding-logo.png" alt="YKT Holding — YKTera" width="128" height="128" />
</p>

<h1 align="center">YKT Holding</h1>

<p align="center">
  <strong>YKTera</strong> tarafından geliştirilen çok-motorlu yapay zeka organizasyon ve ajan yönetim platformu.<br/>
  Yerli masaüstü uygulamasından şirketlerinizi, projelerinizi, otonom ajanlarınızı, kalıcı hafızanızı ve gömülü tarayıcınızı yönetin.
</p>

<p align="center">
  <strong>Güncel Sürüm:</strong> <code>v1.0.4</code> (2026-11-20) &nbsp;·&nbsp;
  <a href="https://github.com/ecankinsundev/YKT-Holding-Releases/releases/tag/v1.0.4">Sürüm Sayfası</a> &nbsp;·&nbsp;
  <a href="CHANGELOG.md">Tüm Sürüm Notları</a>
</p>

---

## İndirme (v1.0.4)

| Platform | Paket Türü | İndirme Bağlantısı | SHA-256 |
|---|---|---|---|
| **Windows x64** | Kurulum Sihirbazı (Önerilen) | [`YKT-Holding_1.0.4_x64-setup.exe`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.0.4/YKT-Holding_1.0.4_x64-setup.exe) | `6ce3613220b6635710d34d790aa766d90646dd7a3904039140facd8f1ec3b3c8` |
| **Windows x64** | Portatif Arşiv (Kurulumsuz) | [`YKT-Holding_1.0.4_x64-portatif.zip`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.0.4/YKT-Holding_1.0.4_x64-portatif.zip) | `66d8b2b7129de77db7c940bee8076c2bb794630ecf7fa2f18a2859a74cbe07dc` |
| **Güncelleme Manifestosu** | Sürüm Kaydı | [`latest.json`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.0.4/latest.json) | — |

> **Bütünlük Doğrulama (PowerShell):**
> ```powershell
> (Get-FileHash .\YKT-Holding_1.0.4_x64-setup.exe -Algorithm SHA256).Hash.ToLower() -eq "6ce3613220b6635710d34d790aa766d90646dd7a3904039140facd8f1ec3b3c8"
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
1. Yukarıdaki tablodan **`YKT-Holding_1.0.4_x64-setup.exe`** dosyasını indirin ve çalıştırın (yönetici izni gerektirmez).
2. Uygulama `%LOCALAPPDATA%\YKT Holding` klasörüne kurulur, kullanıcı `PATH` ortam değişkenine `ykt` komutunu ekler ve Başlat Menüsü / Masaüstü kısayollarını oluşturur.
3. **YKT Holding** uygulamasını açın; ilk açılış sihirbazı çalışma klasörünüzü, şirket/ekip yapınızı ve `ykt-guard` güvenlik kapılarını otomatik yapılandırır.

### Seçenek 2 — Portatif ZIP (Kurulumsuz)
1. **`YKT-Holding_1.0.4_x64-portatif.zip`** arşivini dilediğiniz klasöre çıkartın.
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

## Mevcut Sürümde Neler Var? (v1.0.4)

### Yenilikler ve Duzeltmeler
- **Sol Menu Ac/Kapa (Toggle):** Sol menude halihazirda ekranda acik/gorunur olan bir bolmeye (`Konusmalar`, `Tahta`, `Projeler`, `Ajani izle` kosan karti izlerken, `Kullanim`, `Hafiza`, `Tarayici`, `Ayarlar`) tekrar tiklandiginda o bolme kapatilir ve kalan bolmeler bosluk birakmadan tam alana genisler ([ekran.rs](crates/ykt-holding/src/ekran.rs)). `Tahta` acikken `Projeler`'e (veya tersine) tiklamak kapatmak yerine diger gorunume gecer; tam ekran modunda arka planda gizli kalan bir bolmeye tiklamak ise o bolmeyi one getirir.
- **Sehir Gizliyken `Ofis` = Varsayilan `Tahta | Konusmalar` (Bos Ekran Yok):** `Sehir gorunumu` gizliyken sol menuden **`Ofis`** sekmesine tiklandiginda (veya gizli tercihli acilista / sehir gizlendiginde acik bolme yoksa) artik bos genel bakis ekrani yerine **`Tahta` (sol) ve `Konusmalar` (sag)** dogrudan yan yana acilir ([lib.rs](crates/ykt-holding/src/lib.rs)). Yalniz `Hepsini kapat` ile tum paneller kapatilirsa acilan genel bakis ekranina tek tik **`Tahta + Konusmalar ac`** dugmesi eklendi.
- **Belirgin Kalici Durum Rozeti:** `Sehir gorunumu` gizliyken ust seritteki `Kosan is: N  |  Patron onayi bekleyen: M  |  Ajan: K` bilgi satiri belirgin cerceveli durum rozeti icinde surekli gorunur kalir ([ekran.rs](crates/ykt-holding/src/ekran.rs)).

---

> Detaylı sürüm geçmişi için [CHANGELOG.md](CHANGELOG.md) dosyasına bakın.  
> **YKT Holding** · Geliştiren: **YKTera** · Tüm hakları saklıdır.
