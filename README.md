<p align="center">
  <img src="assets/ykt-holding-logo.png" alt="YKT Holding — YKTera" width="128" height="128" />
</p>

<h1 align="center">YKT Holding</h1>

<p align="center">
  <strong>YKTera</strong> tarafından geliştirilen çok-motorlu yapay zeka organizasyon ve ajan yönetim platformu.<br/>
  Yerli masaüstü uygulamasından şirketlerinizi, projelerinizi, otonom ajanlarınızı, kalıcı hafızanızı ve gömülü tarayıcınızı yönetin.
</p>

<p align="center">
  <strong>Güncel Sürüm:</strong> <code>v1.1.0</code> (2026-11-21) &nbsp;·&nbsp;
  <a href="https://github.com/ecankinsundev/YKT-Holding-Releases/releases/tag/v1.1.0">Sürüm Sayfası</a> &nbsp;·&nbsp;
  <a href="CHANGELOG.md">Tüm Sürüm Notları</a>
</p>

---

## İndirme (v1.1.0)

| Platform | Paket Türü | İndirme Bağlantısı | SHA-256 |
|---|---|---|---|
| **Windows x64** | Kurulum Sihirbazı (Önerilen) | [`YKT-Holding_1.1.0_x64-setup.exe`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.1.0/YKT-Holding_1.1.0_x64-setup.exe) | `52eb2cfd51fdd42452f0a09b0c06dd5d014c1604bbdae6298ca96d7b0e6e3e06` |
| **Windows x64** | Portatif Arşiv (Kurulumsuz) | [`YKT-Holding_1.1.0_x64-portatif.zip`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.1.0/YKT-Holding_1.1.0_x64-portatif.zip) | `c1c660f6262c0b9f893051bab6f60b2de08fc78d01f3909f5a23eb1fb508fefd` |
| **Güncelleme Manifestosu** | Sürüm Kaydı | [`latest.json`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.1.0/latest.json) | — |

> **Bütünlük Doğrulama (PowerShell):**
> ```powershell
> (Get-FileHash .\YKT-Holding_1.1.0_x64-setup.exe -Algorithm SHA256).Hash.ToLower() -eq "52eb2cfd51fdd42452f0a09b0c06dd5d014c1604bbdae6298ca96d7b0e6e3e06"
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
1. Yukarıdaki tablodan **`YKT-Holding_1.1.0_x64-setup.exe`** dosyasını indirin ve çalıştırın (yönetici izni gerektirmez).
2. Uygulama `%LOCALAPPDATA%\YKT Holding` klasörüne kurulur, kullanıcı `PATH` ortam değişkenine `ykt` komutunu ekler ve Başlat Menüsü / Masaüstü kısayollarını oluşturur.
3. **YKT Holding** uygulamasını açın; ilk açılış sihirbazı çalışma klasörünüzü, şirket/ekip yapınızı ve `ykt-guard` güvenlik kapılarını otomatik yapılandırır.

### Seçenek 2 — Portatif ZIP (Kurulumsuz)
1. **`YKT-Holding_1.1.0_x64-portatif.zip`** arşivini dilediğiniz klasöre çıkartın.
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

## Mevcut Sürümde Neler Var? (v1.1.0)

### Yenilikler ve Duzeltmeler
- **3 Katmanli 2.5D Izometrik Cam Kule Ofis (`OfisKipi::Izometrik`, varsayilan):** Eski piksel-art haritanin yanina saf 2D `egui::Painter` vektor cizimiyle (3D motor / shader yok) yeni varsayilan **2.5D** Ofis gorunumu eklendi ([izometrik.rs](crates/ykt-holding/src/kampus/izometrik.rs)). Ust cubuktaki `2.5D` / `Klasik` secimi `~/.ykt/arayuz-ofis-kipi.txt` dosyasinda kalici saklanir; `Duzenle (E)` mevcut klasik izgara duzenleyicisine sorunsuz gecer.
  - **Katman 1 (Dis Kampus):** Altin tacli cam kule (`YKT Merkez`) ve kat sayisina olcekli sirket pavyonlari, aktif/onay bekleyen kat isiklari, cam kopruler, yalniz gercek hedef degisiminde kopruden suzulen 2.5D ajan figuru + isik izi ve bina ustu tiklanabilir canli durum kartlari.
  - **Katman 2 (Bina Ici 2.5D Kat Kesiti):** Binaya cift tiklandiginda `kampus.json` odalari cam bolmeli 2.5D kat kesiti olarak acilir (cok katli binalarda kat secici + alt hayalet levhalar); 6 `Durum` + ortogonal `uzak` hologram gorunumu ve `veri.kartlar` (`ust` / `test_edilen` / `test_karti`) uzerinden gercek delegasyon Bezier yaylari cizilir.
  - **Katman 3 (Hizli Ajan Karti):** 2.5D gorunumde ajana sol tiklandiginda (HLD-AJS-0206 guncellemesi, Patron 2026-11-21) tuvali kapatmadan yaninda buzlu cam kontrol karti acilir: **`Canli Izle`** (binadan cikmadan `AjaniIzle` acar), **`Mesaj Yaz`**, **`Karti Ac`** ve **`Motor Degistir`** ([ajan_menu.rs](crates/ykt-holding/src/ajan_menu.rs)); ilk `Esc` karti, ikinci `Esc` binayi kapatir.
- **Bosta 0 FPS Yeniden Cizim & WCAG AA Tema Uyumu:** 2.5D kipte kopru gecisi/kamera hareketi veya odakta kosan is yokken kampus kendi yeniden cizim istemez (`izometrik_cizim_araligi` -> `None`; bosta 0 FPS), aktif kopru gecisinde ~20 FPS (50 ms), odakta kosan iste ~8 Hz (125 ms) calisir. Gece ve Gunduz izometrik paletleri uygulama temasini izler ve WCAG AA (`>= 4.5:1`) kontrast testiyle kilitlidir.

---

> Detaylı sürüm geçmişi için [CHANGELOG.md](CHANGELOG.md) dosyasına bakın.  
> **YKT Holding** · Geliştiren: **YKTera** · Tüm hakları saklıdır.
