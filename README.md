<p align="center">
  <img src="assets/ykt-holding-logo.png" alt="YKT Holding — YKTera" width="128" height="128" />
</p>

<h1 align="center">YKT Holding</h1>

<p align="center">
  <strong>YKTera</strong> tarafından geliştirilen çok-motorlu yapay zeka organizasyon ve ajan yönetim platformu.<br/>
  Yerli masaüstü uygulamasından şirketlerinizi, projelerinizi, otonom ajanlarınızı, kalıcı hafızanızı ve gömülü tarayıcınızı yönetin.
</p>

<p align="center">
  <strong>Güncel Sürüm:</strong> <code>v1.4.0</code> (2026-11-21) &nbsp;·&nbsp;
  <a href="https://github.com/ecankinsundev/YKT-Holding-Releases/releases/tag/v1.4.0">Sürüm Sayfası</a> &nbsp;·&nbsp;
  <a href="CHANGELOG.md">Tüm Sürüm Notları</a>
</p>

---

## İndirme (v1.4.0)

| Platform | Paket Türü | İndirme Bağlantısı | SHA-256 |
|---|---|---|---|
| **Windows x64** | Kurulum Sihirbazı (Önerilen) | [`YKT-Holding_1.4.0_x64-setup.exe`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.4.0/YKT-Holding_1.4.0_x64-setup.exe) | `1a3ebde35e65fdfa5955d9d4617eee55a58692bd911f92a8486380a952340887` |
| **Windows x64** | Portatif Arşiv (Kurulumsuz) | [`YKT-Holding_1.4.0_x64-portatif.zip`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.4.0/YKT-Holding_1.4.0_x64-portatif.zip) | `9159c52450fe4555c30ec137d4fc7517a83728aa497b1e2fc6b2c608f8fbd431` |
| **Güncelleme Manifestosu** | Sürüm Kaydı | [`latest.json`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.4.0/latest.json) | — |

> **Bütünlük Doğrulama (PowerShell):**
> ```powershell
> (Get-FileHash .\YKT-Holding_1.4.0_x64-setup.exe -Algorithm SHA256).Hash.ToLower() -eq "1a3ebde35e65fdfa5955d9d4617eee55a58692bd911f92a8486380a952340887"
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
1. Yukarıdaki tablodan **`YKT-Holding_1.4.0_x64-setup.exe`** dosyasını indirin ve çalıştırın (yönetici izni gerektirmez).
2. Uygulama `%LOCALAPPDATA%\YKT Holding` klasörüne kurulur, kullanıcı `PATH` ortam değişkenine `ykt` komutunu ekler ve Başlat Menüsü / Masaüstü kısayollarını oluşturur.
3. **YKT Holding** uygulamasını açın; ilk açılış sihirbazı çalışma klasörünüzü, şirket/ekip yapınızı ve `ykt-guard` güvenlik kapılarını otomatik yapılandırır.

### Seçenek 2 — Portatif ZIP (Kurulumsuz)
1. **`YKT-Holding_1.4.0_x64-portatif.zip`** arşivini dilediğiniz klasöre çıkartın.
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

## Mevcut Sürümde Neler Var? (v1.4.0)

### Yenilikler ve Duzeltmeler
- **Secilebilir `Okunakli | Teknik` Anlati Kipi (`~/.ykt/arayuz-anlati.txt`):**
  - Hem **Tahta** ust cubugundan, hem **Kart paneli** basligindan hem de **`Ayarlar > Makine ve surecler > Tema`** altindan tek tikla degistirilebilen kalici **`Okunakli | Teknik`** gorunum kipi eklendi ([lib.rs](crates/ykt-holding/src/lib.rs), [ekran.rs](crates/ykt-holding/src/ekran.rs), [ayarlar.rs](crates/ykt-holding/src/ayarlar.rs)).
  - **Okunakli kip (varsayilan):** Tahta kartlarinda insan okunur baslik one cikar, kritik uyarilar (`takildi?`, `? karar`, bekleme nedeni) korunurken gurultulu teknik rozetler gizlenir; kart panelinde bos `"yok"` satirlari ve bos `Kart diff` satiri gizlenir; yeni acilan `Ajani izle` panelleri varsayilan **`Sohbet`** sekmesinde acilir ([kosu_akis.rs](crates/ykt-holding/src/kosu_akis.rs)).
  - **Teknik kip:** Tahta kartlarinda tum rozet/maliyet/oncelik bilgisi gorunur, kart panelinde tum teknik ozet alanlari gorunur ve yeni acilan `Ajani izle` panelleri varsayilan **`Ham cikti`** sekmesinde acilir (`Terminal` sekme adi gercek ConPTY `Konsol` ile karismamasi icin **`Ham cikti`** olarak netlestirildi; [kosu_akis.rs](crates/ykt-holding/src/kosu_akis.rs), [konusmalar.rs](crates/ykt-holding/src/konusmalar.rs)).
- **3 Saniyede Anlasilan Kart Yonetici Ozeti & Jargon Temizligi:**
  - Kart panelinin en ustunde buyuk insan okunur baslik + kucuk soluk kart kodu ve 4 satirlik sade yonetici ozeti (**`Neden acildi`**, **`Sorumlu`**, **`Durum`**, **`Senden ne bekleniyor`**) yer alir ([ekran.rs](crates/ykt-holding/src/ekran.rs), [sohbet.rs](crates/ykt-core/src/sohbet.rs)).
  - `(kartin Istek bolumu)`, `(AJ4)`, `engel: sinif yok` gibi ic jargonlar ve henuz onay asamasina gelmemis kartlardaki yersiz `"Son kontrol adimlari bolumu bos"` uyarisi kaldirildi ([onay_paneli.rs](crates/ykt-holding/src/onay_paneli.rs)).
- **Karar & Onay Mekanizmasi Duzeltmeleri:**
  - Acik bir `karar` sorusu olan kartta secenek secilmeden kartin kapatilmasi engellendi: cekirdek `sohbet_yaz` reddeder ([kart_yaz.rs](crates/ykt-core/src/kart_yaz.rs)), kart paneli `Onayla` dugmesini gizler ve sol onay paneli **`Karar ver`** gosterir ([onay_paneli.rs](crates/ykt-holding/src/onay_paneli.rs)).
  - `butce-durdu` durumundaki kartlarin dugmesiz kalmasi giderildi (`Geri gonder (bekliyor)` ve `Iptal et` eklendi).
- **Ayarlar > Haftalik Otomatik Durum Raporu Anahtari:**
  - **`Ayarlar > Kota ve butce`** altina **`Haftalik otomatik durum raporu`** ac/kapa anahtari (`rapor_dongu`, varsayilan **acik**) eklendi; `<kok>/ykt.json` (ve varsa `ajans.json`) dosyasina kaydedilir ([ayarlar.rs](crates/ykt-holding/src/ayarlar.rs)).

---

> Detaylı sürüm geçmişi için [CHANGELOG.md](CHANGELOG.md) dosyasına bakın.  
> **YKT Holding** · Geliştiren: **YKTera** · Tüm hakları saklıdır.
