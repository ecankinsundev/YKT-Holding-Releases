<p align="center">
  <img src="assets/ykt-holding-logo.png" alt="YKT Holding — YKTera" width="128" height="128" />
</p>

<h1 align="center">YKT Holding</h1>

<p align="center">
  <strong>YKTera</strong> tarafından geliştirilen çok-motorlu yapay zeka organizasyon ve ajan yönetim platformu.<br/>
  Yerli masaüstü uygulamasından şirketlerinizi, projelerinizi, otonom ajanlarınızı, kalıcı hafızanızı ve gömülü tarayıcınızı yönetin.
</p>

<p align="center">
  <strong>Güncel Sürüm:</strong> <code>v1.3.0</code> (2026-11-21) &nbsp;·&nbsp;
  <a href="https://github.com/ecankinsundev/YKT-Holding-Releases/releases/tag/v1.3.0">Sürüm Sayfası</a> &nbsp;·&nbsp;
  <a href="CHANGELOG.md">Tüm Sürüm Notları</a>
</p>

---

## İndirme (v1.3.0)

| Platform | Paket Türü | İndirme Bağlantısı | SHA-256 |
|---|---|---|---|
| **Windows x64** | Kurulum Sihirbazı (Önerilen) | [`YKT-Holding_1.3.0_x64-setup.exe`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.3.0/YKT-Holding_1.3.0_x64-setup.exe) | `6ba83d8dc823789350d72c0bdb425f9be1c5df08ed9ac687d16e9d99f6167562` |
| **Windows x64** | Portatif Arşiv (Kurulumsuz) | [`YKT-Holding_1.3.0_x64-portatif.zip`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.3.0/YKT-Holding_1.3.0_x64-portatif.zip) | `cdf04ad216eca281307a415e743da6d00700fe4dd7fd272e69d2c18417eb6fe6` |
| **Güncelleme Manifestosu** | Sürüm Kaydı | [`latest.json`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.3.0/latest.json) | — |

> **Bütünlük Doğrulama (PowerShell):**
> ```powershell
> (Get-FileHash .\YKT-Holding_1.3.0_x64-setup.exe -Algorithm SHA256).Hash.ToLower() -eq "6ba83d8dc823789350d72c0bdb425f9be1c5df08ed9ac687d16e9d99f6167562"
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
1. Yukarıdaki tablodan **`YKT-Holding_1.3.0_x64-setup.exe`** dosyasını indirin ve çalıştırın (yönetici izni gerektirmez).
2. Uygulama `%LOCALAPPDATA%\YKT Holding` klasörüne kurulur, kullanıcı `PATH` ortam değişkenine `ykt` komutunu ekler ve Başlat Menüsü / Masaüstü kısayollarını oluşturur.
3. **YKT Holding** uygulamasını açın; ilk açılış sihirbazı çalışma klasörünüzü, şirket/ekip yapınızı ve `ykt-guard` güvenlik kapılarını otomatik yapılandırır.

### Seçenek 2 — Portatif ZIP (Kurulumsuz)
1. **`YKT-Holding_1.3.0_x64-portatif.zip`** arşivini dilediğiniz klasöre çıkartın.
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

## Mevcut Sürümde Neler Var? (v1.3.0)

### Yenilikler ve Duzeltmeler
- **Her Binada Sosyal / Takilmalik Alanlar & Bosta Ajan Davranisi:**
  - Yeni olusturulan her binaya (`Islem::BinaEkle`) otomatik olarak **`Toplanti Odasi`** (`tur: "toplanti"`) ve **`Kahve & Dinlenme`** (`tur: "mutfak"`) odalari eklenir ([kampus_yaz.rs](crates/ykt-core/src/kampus_yaz.rs)).
  - 2.5D kat kesitinde artik `mutfak`/`kahve` odalari **espresso bari + kafe masalari**, `dinlenme`/`lobi` odalari **L-koltuk + sehpa + ic mekan bitkisi**, `toplanti` odalari ise **oval cam masa + sandalyeler + is dagitiminda parlak holografik halka** ile cizilir ([izometrik.rs](crates/ykt-holding/src/kampus/izometrik.rs)).
  - **Kideme Gore Masa Mimarisi & Rol/Skill Kisisel Esyalari:** Calisma masalari artik kademeye gore farklilasir (**Holding/GM:** altin seritli buyuk yonetici masasi, panoramik kavisli monitor ve pirinc lamba; **Proje Lideri:** L-bicimli yonetici masasi ve genis uclu monitor; **Uzman:** modern cift monitorlu studyo masasi) ve her kullanilan masanin uzerinde ajanin rol ve skill'lerine ozgu 2.5D kisisel esya (altin kupa/dosya, strateji kuresi, Kanban tableti, PCB devresi, guvenlik kalkani, test kupasi, mini sunucu kulesi, mobil telefon standi, kahve+mekanik klavye veya teknik kitaplar) yer alir.
  - Isi olmayan (`Bosta` / `Uykuda`) ajanlar masalarinda sabit beklemek yerine binanin sosyal alanlarinda (`Kahve molasi`, `Dinleniyor`, `Lobide`) takilir; aktif is baslayinca masalarina yurur ([iso_hareket.rs](crates/ykt-holding/src/kampus/iso_hareket.rs)).
- **Lider Is Dagitimi, Birebir Gorev Teslimi ve Lidere Danisma Hareketleri:**
  - **Coklu is dagitimi (2+ alt kart):** Ekip lideri (`yonetici` / `holding-gm`) **`Toplanti Odasi`** masasi basina gecip isi dagitir (`Is dagitiyor`).
  - **Tekli gorev verme (1 alt kart):** Ekip lideri dogrudan isi verdigi ajanin masasinin yanina giderek gorevi teslim eder (`Gorev veriyor -> <Ad>`).
  - **Lidere soru / onay sorma (`SeniBekliyor` / `onay-bekliyor` / `engel`):** Soru/onay bekleyen ajan liderin odasina/masasinin yanina gidip ziyaretci noktasinda bekler (`Lidere soruyor`), lider ise odasinda kalir.
  - Kat ici tum konum gecisleri koridordan yumusak yuruyusle animasyonlanir ve hedefe varinca yeniden **bosta 0 FPS** kuralina doner.
- **Canli Claude Kota Olcumu (`ykt butce --canli`):**
  - `Kullanim` ve `Ayarlar > Kota ve butce` sayfalarindaki **`Yenile`** dugmesi artik `ykt butce --canli` calistirarak 1 turluk hafif `haiku` sorgusuyla gercek Anthropic `rate_limit_event` yuzdelerini (`Haftalik` + `5 Saatlik` + sifirlanma saatleri) ve kalibrasyon tavanini otomatik ceker ([butce_canli.rs](crates/ykt/src/butce_canli.rs)); taze/kalibrasyonsuz kurulumda uygulama oturum basina bir kez otomatik kendini kalibre eder (`%0 / %?` takilmasi biter).
- **Otomatik `sirket + masa` Esleme (`ev_masa_coz`):** `kadro.json` icinde tam `ev_masa` yolu yazmasa bile kisa `masa` kimligi ve `sirket` bilgisinden ajan otomatik olarak binasina ve masasina yerlestirilir, ayni masa silinmeye karsi korunur ([kampus.rs](crates/ykt-core/src/kampus.rs)).

---

> Detaylı sürüm geçmişi için [CHANGELOG.md](CHANGELOG.md) dosyasına bakın.  
> **YKT Holding** · Geliştiren: **YKTera** · Tüm hakları saklıdır.
