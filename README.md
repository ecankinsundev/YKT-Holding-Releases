<p align="center">
  <img src="assets/ykt-holding-logo.png" alt="YKT Holding — YKTera" width="128" height="128" />
</p>

<h1 align="center">YKT Holding</h1>

<p align="center">
  <strong>YKTera</strong> tarafından geliştirilen çok-motorlu yapay zeka organizasyon ve ajan yönetim platformu.<br/>
  Yerli masaüstü uygulamasından şirketlerinizi, projelerinizi, otonom ajanlarınızı, kalıcı hafızanızı ve gömülü tarayıcınızı yönetin.
</p>

<p align="center">
  <strong>Güncel Sürüm:</strong> <code>v1.8.6</code> (2026-11-23) &nbsp;·&nbsp;
  <a href="https://github.com/ecankinsundev/YKT-Holding-Releases/releases/tag/v1.8.6">Sürüm Sayfası</a> &nbsp;·&nbsp;
  <a href="CHANGELOG.md">Tüm Sürüm Notları</a>
</p>

---

## İndirme (v1.8.6)

| Platform | Paket Türü | İndirme Bağlantısı | SHA-256 |
|---|---|---|---|
| **Windows x64** | Kurulum Sihirbazı (Önerilen) | [`YKT-Holding_1.8.6_x64-setup.exe`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.8.6/YKT-Holding_1.8.6_x64-setup.exe) | `9316a08100233a7a5141a59dcadd7d93e7dc772ba5963aa85d5760fe8c5a14f8` |
| **Windows x64** | Portatif Arşiv (Kurulumsuz) | [`YKT-Holding_1.8.6_x64-portatif.zip`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.8.6/YKT-Holding_1.8.6_x64-portatif.zip) | `29e668df766804cbb3ea4ad4a57d17a05e6735ac7b073c037755b86d601e2cc8` |
| **Güncelleme Manifestosu** | Sürüm Kaydı | [`latest.json`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.8.6/latest.json) | — |

> **Bütünlük Doğrulama (PowerShell):**
> ```powershell
> (Get-FileHash .\YKT-Holding_1.8.6_x64-setup.exe -Algorithm SHA256).Hash.ToLower() -eq "9316a08100233a7a5141a59dcadd7d93e7dc772ba5963aa85d5760fe8c5a14f8"
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
1. Yukarıdaki tablodan **`YKT-Holding_1.8.6_x64-setup.exe`** dosyasını indirin ve çalıştırın (yönetici izni gerektirmez).
2. Uygulama `%LOCALAPPDATA%\YKT Holding` klasörüne kurulur, kullanıcı `PATH` ortam değişkenine `ykt` komutunu ekler ve Başlat Menüsü / Masaüstü kısayollarını oluşturur.
3. **YKT Holding** uygulamasını açın; ilk açılış sihirbazı çalışma klasörünüzü, şirket/ekip yapınızı ve `ykt-guard` güvenlik kapılarını otomatik yapılandırır.

### Seçenek 2 — Portatif ZIP (Kurulumsuz)
1. **`YKT-Holding_1.8.6_x64-portatif.zip`** arşivini dilediğiniz klasöre çıkartın.
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

## Mevcut Sürümde Neler Var? (v1.8.6)

### Yenilikler ve Duzeltmeler
- **Proje Baslatma ve Kapsam Kesfi Kapisi (`proje.rs`, `kurulus.rs`, `sihirbaz.rs`, `agents/yonetici.md`):**
  - Yeni bir proje kuruldugunda artik ekip kartlari Patron'dan girdi ve onay almadan kendi basina kosmaya baslamaz.
  - Her yeni projede **`<ONEK>-0001`** numarali ilk kart projenin **yoneticisine (`rol: yonetici`, `pm: kesif`, `onay: patron`, `cwd: <kok>`)** acilir; yonetici bu kartta uretim/kodlama/yayin yapmadan proje turune ve aciklamaya gore eksik kritik bilgileri (hedef platform/kanallar, erisim/hesap/kaynak, teslimat bicimi/ton, kapsam siniri, oncelik ve takvim) **2-4 secenekli onerilerle** (`(onerilen)` ilk sirada) Patron'a sorar.
  - Sonraki tum ekip kartlari (`0002`, `0003`, ...) kendi bagimlilik zincirlerini indeks kaymasiz koruyarak **`<ONEK>-0001`'e bagimli** acilir ve baslamadan once kesif notundaki / hub notundaki Patron cevaplarini okumasi zorunlu kilinir; Patron kesif kartini cevaplayip onaylamadan hicbir ekip karti kosmaz.
  - Kesif karti `cwd: <kok>` ile kod deposunda gereksiz bos worktree acmaz; Rapor `KANIT: TAM` + ters tirnakli `- Belge: \`...\`` bicimiyle kanit kapisindan dogrudan gecer.
- **Temiz Worktree Kurtarma Duzeltmesi (`calisan.rs::kalinti_worktree`):**
  - Sifir commitli veya bitmis/birlestirilmis **temiz ve ignore'suz** `.kart-wt` kalinti klasorlerinde Windows Geri Donusum Kutusu (`SHFileOperationW`) kilit/tasima hatasiyla kartlarin kalici `engel`e dusmesi giderildi: once resmi `git worktree remove` + `prune` denenir (dal korunur), gerekirse Geri Donusum yedegine dusulur ve iki hata birlikte raporlanir.

---

> Detaylı sürüm geçmişi için [CHANGELOG.md](CHANGELOG.md) dosyasına bakın.  
> **YKT Holding** · Geliştiren: **YKTera** · Tüm hakları saklıdır.
