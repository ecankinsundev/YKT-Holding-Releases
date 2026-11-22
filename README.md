<p align="center">
  <img src="assets/ykt-holding-logo.png" alt="YKT Holding — YKTera" width="128" height="128" />
</p>

<h1 align="center">YKT Holding</h1>

<p align="center">
  <strong>YKTera</strong> tarafından geliştirilen çok-motorlu yapay zeka organizasyon ve ajan yönetim platformu.<br/>
  Yerli masaüstü uygulamasından şirketlerinizi, projelerinizi, otonom ajanlarınızı, kalıcı hafızanızı ve gömülü tarayıcınızı yönetin.
</p>

<p align="center">
  <strong>Güncel Sürüm:</strong> <code>v1.8.1</code> (2026-11-22) &nbsp;·&nbsp;
  <a href="https://github.com/ecankinsundev/YKT-Holding-Releases/releases/tag/v1.8.1">Sürüm Sayfası</a> &nbsp;·&nbsp;
  <a href="CHANGELOG.md">Tüm Sürüm Notları</a>
</p>

---

## İndirme (v1.8.1)

| Platform | Paket Türü | İndirme Bağlantısı | SHA-256 |
|---|---|---|---|
| **Windows x64** | Kurulum Sihirbazı (Önerilen) | [`YKT-Holding_1.8.1_x64-setup.exe`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.8.1/YKT-Holding_1.8.1_x64-setup.exe) | `5141a5a455319a87afaa9a6e3d8aed4ad5a9a29184c4e4d969d40754dcd2b2c1` |
| **Windows x64** | Portatif Arşiv (Kurulumsuz) | [`YKT-Holding_1.8.1_x64-portatif.zip`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.8.1/YKT-Holding_1.8.1_x64-portatif.zip) | `265e3be78f1105b5d3f443004d7178c7982197d6f7ebf8098a34dbe7c21b2c04` |
| **Güncelleme Manifestosu** | Sürüm Kaydı | [`latest.json`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.8.1/latest.json) | — |

> **Bütünlük Doğrulama (PowerShell):**
> ```powershell
> (Get-FileHash .\YKT-Holding_1.8.1_x64-setup.exe -Algorithm SHA256).Hash.ToLower() -eq "5141a5a455319a87afaa9a6e3d8aed4ad5a9a29184c4e4d969d40754dcd2b2c1"
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
1. Yukarıdaki tablodan **`YKT-Holding_1.8.1_x64-setup.exe`** dosyasını indirin ve çalıştırın (yönetici izni gerektirmez).
2. Uygulama `%LOCALAPPDATA%\YKT Holding` klasörüne kurulur, kullanıcı `PATH` ortam değişkenine `ykt` komutunu ekler ve Başlat Menüsü / Masaüstü kısayollarını oluşturur.
3. **YKT Holding** uygulamasını açın; ilk açılış sihirbazı çalışma klasörünüzü, şirket/ekip yapınızı ve `ykt-guard` güvenlik kapılarını otomatik yapılandırır.

### Seçenek 2 — Portatif ZIP (Kurulumsuz)
1. **`YKT-Holding_1.8.1_x64-portatif.zip`** arşivini dilediğiniz klasöre çıkartın.
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

## Mevcut Sürümde Neler Var? (v1.8.1)

### Yenilikler ve Duzeltmeler
- **Kampus ve 2.5D Ofis Mimari Degismezleri (`kampus.rs`, `kampus_yaz.rs`, `proje_yasam.rs`, `izometrik.rs`):**
  - **1 Organizasyon = 1 Cok Katli Bina, 1 Proje = 1 Kat:** Ayni sirkete acilan her yeni proje artik ikinci bos bina olusturmaz; organizasyon binasinin (`tip: "alan"`) yeni bir kati (`id: <proje-slug>`) olarak acilir.
  - **Zorunlu Kat Odalari:** Her proje katinda (a) diger odalardan gorsel olarak ayirt edilen **1 Yonetici Odasi** (`tur: "yonetici"`), (b) ekipteki her standart ajan icin **ayri 1 bireysel cam oda** (`tur: "kubik"`, oda basina 1 masa) ve rolune ozgu masa nesnesi, (c) bostaki ajanlarin dinlenmesi icin **1 Kahve & Dinlenme sosyal odasi** (`tur: "mutfak"`, 0 masa) olusturulur.
  - Ambar/cok-masali tek oda uretimi ve `yk` alt-dizgisi gibi gevsek eslesmelerle normal odalarin Baskan Suiti'ne donusmesi hatasi (`baskan_odasi_mi`) giderildi; cok katli binada proje arsivleme/geri alma/silme islemleri `kampus.json` uzerine kalici kaydedilir.
- **Proje Sihirbazi: Model/Kota Politikasi, 125-Skill Dinamik Roller ve Rol Sihirbazi (`ekip_uygunluk.rs`, `kurulus.rs`, `proje.rs`, `politika.rs`, `calisan.rs`, `sihirbaz.rs`):**
  - Yaniltici eski *"Ekip hangi model seviyesinde calissin?"* / *"Butce ve model tercihi?"* sorusu 21 paket sablonundan ve planlayici suzgecinden kaldirildi; cift `(onerilen) (onerilen)` etiketi duzeltildi.
  - Adim 4 (`Ekip`) icine **Model ve Kota Politikasi** karti eklendi: **`Ekip lideri secsin (onerilen)`** veya **`Tek tek ben seceyim`** (her uye icin 12-model secici, K0 `agy_kapi_hazir` korumali) + 3 kota devir secenegi (`Otomatik devir (Claude -> AGY)`, `AGY oncelikli (AGY -> Claude)`, `Devir kapali`). `elle` kipte `kadro.json` bireysel secimleri `motor-politikasi.json` tarafindan ezilmez; `devir_acik: false` tum proaktif/reaktif devir noktalarinda korunur.
  - **125-Skill Dinamik Rol Onerileri & 15 Yerlesik Rol:** Adim 4 rol listesi projeye gore 125 skill'den dinamik rol onerir ve **`Tum roller (15)`** acilir listesiyle tum yerlesik rollere erisim saglar.
  - **Yeni Sirkette de Etkin `+ Ozel rol` & Rol Sihirbazi:** Yeni sirket acarken bile `+ Ozel rol` etkindir (K0 guvenligi icin LLM/planlayici ciktisindan ayiklanir, yalniz kullanici sihirbazi uzerinden dogrulanarak kaydedilir). **Rol Sihirbazi** ile yaptirilmak istenen is yazildiginda 125 `SKILL.md` dosyasindan otomatik skill eslestirmesi yapilip rol taslagi doldurulur ve `Skill ara` ile ozellestirilebilir.
  - Adim 2 (`Ne yapalim?`) icine dogrulamali **`Mevcut kod klasoru (istege bagli)`** alani eklendi.
- **Paket ve Ilk Kart Akisi Duzeltmeleri (`masaustu.json`, `paket.rs`, `proje.rs`):**
  - `sablonlar/paketler/masaustu.json` sabit `["dotnet", "node"]` makine etiketlerinden arindirildi (`[]`).
  - Yeni proje ilk kartlari paralel yigilmak yerine sirali bagimlilik zinciriyle (`arastirma` -> `is-plani` -> `uygulama` -> `test`) ve dogru rol eslesmeleriyle olusturulur.
- **Genel Mudur (GM) Adlandirma Temizligi (`marka.rs`, `tahta.rs`, `grup.rs`, `demir.rs`, `ekran.rs`, `konusmalar.rs`, `sihirbaz.rs`):**
  - Arayuzde ve mesajlarda sabit kalan eski `"Demir"` kisi adi kaldirilarak **`Genel Mudur` / `GM`** (ve kadrodaki dinamik `holding-gm` adi) kullanilmaya baslandi; `marka::gm_mi` ile eski `onay: demir` kartlari ve `@demir` hitaplari geriye donuk tam uyumlu okunur.

---

> Detaylı sürüm geçmişi için [CHANGELOG.md](CHANGELOG.md) dosyasına bakın.  
> **YKT Holding** · Geliştiren: **YKTera** · Tüm hakları saklıdır.
