<p align="center">
  <img src="assets/ykt-holding-logo.png" alt="YKT Holding — YKTera" width="128" height="128" />
</p>

<h1 align="center">YKT Holding</h1>

<p align="center">
  <strong>YKTera</strong> tarafından geliştirilen çok-motorlu yapay zeka organizasyon ve ajan yönetim platformu.<br/>
  Yerli masaüstü uygulamasından şirketlerinizi, projelerinizi, otonom ajanlarınızı, kalıcı hafızanızı ve gömülü tarayıcınızı yönetin.
</p>

<p align="center">
  <strong>Güncel Sürüm:</strong> <code>v1.8.0</code> (2026-11-22) &nbsp;·&nbsp;
  <a href="https://github.com/ecankinsundev/YKT-Holding-Releases/releases/tag/v1.8.0">Sürüm Sayfası</a> &nbsp;·&nbsp;
  <a href="CHANGELOG.md">Tüm Sürüm Notları</a>
</p>

---

## İndirme (v1.8.0)

| Platform | Paket Türü | İndirme Bağlantısı | SHA-256 |
|---|---|---|---|
| **Windows x64** | Kurulum Sihirbazı (Önerilen) | [`YKT-Holding_1.8.0_x64-setup.exe`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.8.0/YKT-Holding_1.8.0_x64-setup.exe) | `d85ef87c9b5d4f4aa46e76f0bd24b3b1a297d222a6b551bffdaf17148a03aa4e` |
| **Windows x64** | Portatif Arşiv (Kurulumsuz) | [`YKT-Holding_1.8.0_x64-portatif.zip`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.8.0/YKT-Holding_1.8.0_x64-portatif.zip) | `93dda613efbedf26e0a105c3d275a1dee0b961f39de7a1fe62b47737d4af2a78` |
| **Güncelleme Manifestosu** | Sürüm Kaydı | [`latest.json`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.8.0/latest.json) | — |

> **Bütünlük Doğrulama (PowerShell):**
> ```powershell
> (Get-FileHash .\YKT-Holding_1.8.0_x64-setup.exe -Algorithm SHA256).Hash.ToLower() -eq "d85ef87c9b5d4f4aa46e76f0bd24b3b1a297d222a6b551bffdaf17148a03aa4e"
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
1. Yukarıdaki tablodan **`YKT-Holding_1.8.0_x64-setup.exe`** dosyasını indirin ve çalıştırın (yönetici izni gerektirmez).
2. Uygulama `%LOCALAPPDATA%\YKT Holding` klasörüne kurulur, kullanıcı `PATH` ortam değişkenine `ykt` komutunu ekler ve Başlat Menüsü / Masaüstü kısayollarını oluşturur.
3. **YKT Holding** uygulamasını açın; ilk açılış sihirbazı çalışma klasörünüzü, şirket/ekip yapınızı ve `ykt-guard` güvenlik kapılarını otomatik yapılandırır.

### Seçenek 2 — Portatif ZIP (Kurulumsuz)
1. **`YKT-Holding_1.8.0_x64-portatif.zip`** arşivini dilediğiniz klasöre çıkartın.
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

## Mevcut Sürümde Neler Var? (v1.8.0)

### Yenilikler ve Duzeltmeler
- **Genisletilmis Holding Rol, Skill ve Paket Katalogu (17 Rol, 125 Skill, 28 Paket):**
  - Holding kapsamini yazilim disi disiplinlerle dengeleyen **4 yeni rol** eklendi: `icerik-editoru`, `veri-analisti`, `operasyon-uzmani`, `hukuk-uyum-uzmani` (`agents/*.md`).
  - **10 yeni dogrulanmis skill** (`115 -> 125`: finansal butce/nakit akisi, fatura/maliyet mutabakati, satis hunisi/teklif, CRM/musteri segmentasyonu, musteri destek/SLA, bilgi bankasi/SSS, performans reklam/kampanya, SEO icerik/anahtar kelime, video senaryo/storyboard, marka sesi/yayin takvimi) ve **5 yeni ekip paketi** (`23 -> 28`: `finans-muhasebe`, `satis-crm`, `musteri-destek`, `pazarlama-seo-reklam`, `video-medya-produksiyon`) eklendi.
  - Agirlikli is odaklari olan **masaustu uygulamalar, mobil uygulama, mobil oyun ve sosyal medya yonetimi** paketleri (`masaustu.json`, `mobil-uygulama.json`, `mobil-oyun.json`, `sosyal-medya.json`) ve yonetici kapsam belgeleri (`agents/yonetici.md`, `agents/proje-lideri.md`) butce-maliyet bilincinde otomatik motor/model secim matrisiyle guclendirildi.
- **Akilli IDF Ekip Onerici ve Maliyet-Etkin Motor Politikasi (`ekip.rs` + `ekip-onerileri.json`):**
  - 28/28 alan-paket birebir eslesmesi, `is_turu` (`yazilim`, `donanim`, `surekli-operasyon`, `uyum-denetim`, `icerik-medya`, `analitik`) ve `kod_gerekli` siniflandirmasi ile dinamik IDF-agirlikli puanlama, deterministik esitlik kirici, siki kesinlik esigi ve hibrit coklu-alan birlestirme (`testci`/`guvenlik-testci` korunur) eklendi.
  - `rol_maliyet_motoru` ile `guvenlik-testci` -> `Fable 5.2`, cekirdek kod rolleri -> `Opus 5.5`, yonetim/test/sistem -> `Sonnet 5.5`, arastirma/icerik/veri/hukuk/operasyon/tasarim -> `Antigravity` (`AGY Argon`/`Neon`) atayarak Claude kotasini korur; kod-disi 10 uzman rol `KAPISIZ_ROLLER` kapsaminda yalitimsiz da calisabilir (kod/donanim/guvenlik rolleri K0 kancasi veya git yalitimi ile korunmaya devam eder).
- **Projeler Sayfasi: Yerel Dosya Yolu, Ayri Kaynak/Release Repo, 2-Kapsamli Yeniden Adlandirma ve Onay-Kapili Proje Silme (`proje_baglanti.rs`, `proje_yasam.rs`, `projeler.rs`):**
  - Proje sayfasina **Adim 1 (Yerel dosya yolu)**, **Adim 2 (Kaynak kod reposu `origin`)** ve **Adim 3 (Ayri Release/Dagitim reposu `release`)** baglantilari eklendi; katı HTTPS/SSH URL dogrulamasi (bayrak/kimlik/CRLF reddi, `kaynak == yayin` engeli) ve mevcut `origin` uzerine sessiz yazmama korumasi uygulanir.
  - **2-Kapsamli Yeniden Adlandirma:** **`Yalniz YKT Holding'de gorunen ad`** (varsayilan) ve **`Kaynak kod dahil gectigi her yer`** (zorunlu kuru tarama onizlemesi, kirli git agaci engeli, `.git`/`target`/`node_modules`/ikili/kilit dosyalarini atlama ve CRLF/LF koruma).
  - **Onay-Kapili Dogrudan `Proje sil`:** Arsivleme zorunlulugu olmadan cift onay (proje adi yaz + basili tut); varsayilan olarak kaynak repo ve hafiza HARIC her seyi Geri Donusum Kutusuna (`ykt cop`) tasir. Varsayilan kapali iki opt-in onay kutusuyla istenirse (a) izin listesi/symlink/monorepo korumali kaynak repo ve/veya (b) yalniz bu projenin Vault hub klasoru (`20 Projeler/.../<proje>`) de Geri Donusum Kutusuna tasinabilir.
- **Personel Ekrani: AI Model Secimi, Coklu-Proje/Holding Kapsami ve Yoneticiye Ozel Capraz Sirket Gorev Yetkisi (`kadro.rs`, `personel.rs`, `yonetim.rs`):**
  - `Ayarlar > Ekip > Personel` ekraninda `holding-gm` dahil tum yapay zeka ajanlarinin motor/modeli dogrudan degistirilebilir (`insan` haric).
  - Ajanlar mevcut kimlik ve hafizalari korunarak farkli projelere tasinabilir; **Tek proje**, **Secili projeler**, **Tum sirket**, **Secili sirketler** veya **Tum holding** kapsaminda calisabilir. `YKT Merkez` (`holding`) altinda ise alinan avukat/uzmanlar (or. 3 avukat) tum sirketlerin secilen projelerine atanabilir.
  - Yalniz **sirket yoneticisi (`rol == "yonetici"`)** icin gorunen **`Baska sirketlere gorev verebilsin`** anahtari (`capraz_sirket_gorev` + istege bagli hedef sirketler) eklendi; diger rollerde sunucu ve arayuz katmaninda kesin engellidir.
- **4-Havuz Butce-Koruyucu Capraz-Motor Kota Devri (`modeller.json`, `havuz.rs`, `devir.rs`, `calisan.rs`):**
  - 4 ayri/hiyerarsik canli havuz (`claude-fable`, `claude-genel`, `agy-gemini`, `agy-claude`) tanimlandi: `Fable` dolunca Claude genel kotasini korumak icin once `AGY Neon High`, sonra `Claude Opus 5.5`, sonra `AGY Opus 5.5` devralir; `AGY Neon` dolunca `Fable` -> `Claude Opus 5.5` -> `AGY Opus 5.5` zinciri isler; `Claude genel` dolunca ust havuza bagli `Fable` da otomatik atlanir.
  - Tek zorunlu gizlilik+K0 devre kesicisi (`gizli` kartlar asla `motor == "claude"` disina cikmaz), gizli anahtar maskeli devir ozeti, `agy-kullanim.json` + `havuz-kota.json` karamsar birlesimi ve kalici kart devri siniri (`AZAMI_KART_DEVRI = 6`) ile hem kosu oncesi proaktif hem kosu ortasi otomatik devir saglanir.

---

> Detaylı sürüm geçmişi için [CHANGELOG.md](CHANGELOG.md) dosyasına bakın.  
> **YKT Holding** · Geliştiren: **YKTera** · Tüm hakları saklıdır.
