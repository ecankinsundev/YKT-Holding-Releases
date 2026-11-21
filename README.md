<p align="center">
  <img src="assets/ykt-holding-logo.png" alt="YKT Holding — YKTera" width="128" height="128" />
</p>

<h1 align="center">YKT Holding</h1>

<p align="center">
  <strong>YKTera</strong> tarafından geliştirilen çok-motorlu yapay zeka organizasyon ve ajan yönetim platformu.<br/>
  Yerli masaüstü uygulamasından şirketlerinizi, projelerinizi, otonom ajanlarınızı, kalıcı hafızanızı ve gömülü tarayıcınızı yönetin.
</p>

<p align="center">
  <strong>Güncel Sürüm:</strong> <code>v1.5.0</code> (2026-11-21) &nbsp;·&nbsp;
  <a href="https://github.com/ecankinsundev/YKT-Holding-Releases/releases/tag/v1.5.0">Sürüm Sayfası</a> &nbsp;·&nbsp;
  <a href="CHANGELOG.md">Tüm Sürüm Notları</a>
</p>

---

## İndirme (v1.5.0)

| Platform | Paket Türü | İndirme Bağlantısı | SHA-256 |
|---|---|---|---|
| **Windows x64** | Kurulum Sihirbazı (Önerilen) | [`YKT-Holding_1.5.0_x64-setup.exe`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.5.0/YKT-Holding_1.5.0_x64-setup.exe) | `76e3944d48dba388f93028e24e124c66fe5d9034d46eae7bed04eb5c75d5fe01` |
| **Windows x64** | Portatif Arşiv (Kurulumsuz) | [`YKT-Holding_1.5.0_x64-portatif.zip`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.5.0/YKT-Holding_1.5.0_x64-portatif.zip) | `f864184efe6a6fcbfc588b2dc71efc41e353eed348e16ff385647a48ca150abc` |
| **Güncelleme Manifestosu** | Sürüm Kaydı | [`latest.json`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.5.0/latest.json) | — |

> **Bütünlük Doğrulama (PowerShell):**
> ```powershell
> (Get-FileHash .\YKT-Holding_1.5.0_x64-setup.exe -Algorithm SHA256).Hash.ToLower() -eq "76e3944d48dba388f93028e24e124c66fe5d9034d46eae7bed04eb5c75d5fe01"
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
1. Yukarıdaki tablodan **`YKT-Holding_1.5.0_x64-setup.exe`** dosyasını indirin ve çalıştırın (yönetici izni gerektirmez).
2. Uygulama `%LOCALAPPDATA%\YKT Holding` klasörüne kurulur, kullanıcı `PATH` ortam değişkenine `ykt` komutunu ekler ve Başlat Menüsü / Masaüstü kısayollarını oluşturur.
3. **YKT Holding** uygulamasını açın; ilk açılış sihirbazı çalışma klasörünüzü, şirket/ekip yapınızı ve `ykt-guard` güvenlik kapılarını otomatik yapılandırır.

### Seçenek 2 — Portatif ZIP (Kurulumsuz)
1. **`YKT-Holding_1.5.0_x64-portatif.zip`** arşivini dilediğiniz klasöre çıkartın.
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

## Mevcut Sürümde Neler Var? (v1.5.0)

### Yenilikler ve Duzeltmeler
- **4'lu Sekme Kalabaliginin Kaldirilmasi -> Tek ve Net `Okunakli | Teknik` 2 Modlu Yapi:**
  - Kart paneli ve `Konusmalar` icindeki kafa karistiran `Sohbet | Ham cikti` alt sekmeleri tamamen kaldirildi; tum uygulamada tek ve net **`Okunakli | Teknik`** kipi kullanilir ([ekran.rs](crates/ykt-holding/src/ekran.rs), [kosu_akis.rs](crates/ykt-holding/src/kosu_akis.rs), [konusmalar.rs](crates/ykt-holding/src/konusmalar.rs), [ayarlar.rs](crates/ykt-holding/src/ayarlar.rs)).
  - **`Okunakli` Mod (Varsayilan — AgentSpace / Linear Tarzi Temiz Patron Gorunumu):**
    - Yan terminal bolmesi, muhendislik dugmeleri (`Duzenle`, `Baska projeye tasi`, `Harcama`, `Kart diff`, `Motor`, `Devret`, `Push izni`) ve ham arac ciktilari tamamen gizlenir.
    - Tek sutunlu ferah yerlesimde yalniz **`ISTENILEN IS`**, **`YAPILANLAR VE SONUC`** (kosarken ajanin sade Turkce canli guncellemeleri), varsa **`SORULAR VE ENGELLER`** ve **`SOHBET GECMISI`** (balon gorunumu) yer alir.
    - Ekranin altinda her zaman gorunur sabit bir **`KARAR VE AKSIYON`** doku bulunur: acik karar secenekleri, yorum/talimat kutusu (`Gonder`, kosarken canli stdin teslimi) ve duruma uygun **`Onayla`**, **`Geri gonder`**, **`Iptal et`** dugmeleri.
  - **`Teknik` Mod (Gercek Gomulu PowerShell ConPTY + Muhendislik Paneli):**
    - Kartin calisma klasorunde (`cwd`) dogrudan **gercek etkilesimli Windows PowerShell ConPTY** oturumu acar; pencere boyutuna gore dinamik yeniden boyutlanir (`ResizePseudoConsole`) ve **5000 satir geri kaydirma** (scrollback) destekler ([konsol.rs](crates/ykt-core/src/konsol.rs), [konsol_ekran.rs](crates/ykt-holding/src/konsol_ekran.rs)).
    - Ust arac cubugunda tek tikla **`Dis PowerShell`** (bagimsiz pencere), **`Claude (--resume)`** (guvenli `session_id` beyaz listesiyle dogrudan PowerShell satirina yazar; [sohbet.rs](crates/ykt-core/src/sohbet.rs)), kosan kartta **`Canli kaydi izle`** ve **`Yeniden baslat`** yer alir.
    - Kart degistirildiginde veya panel kapatildiginda onceki kartin yerel PowerShell sureci otomatik kapatilir (surec birikmesi onlenir; [lib.rs](crates/ykt-holding/src/lib.rs)).
- **Canli Coklu-Model Kota & Kesin Yerel Reset Saatleri (`Kullanim ve Limitler`):**
  - `motor::kota_olayi` artik `rate_limit_event.rate_limit_info.unifiedWindows` altindaki **tum** pencereleri (`five_hour`, `seven_day`, Fable/overage `seven_day_overage_included`, `seven_day_sonnet`, `seven_day_opus` vb.) ayristirir; `butce::yaz_kota` mevcut gecerli pencereleri olcum zamaniyla koruyarak atomik birlestirir ([motor.rs](crates/ykt/src/motor.rs), [butce.rs](crates/ykt/src/butce.rs), [ykt-core/src/butce.rs](crates/ykt-core/src/butce.rs)).
  - `ykt butce --canli --fable` secenegi ve **`Fable Dahil Olc`** dugmesi eklendi; normal `ykt butce --canli` hafif `haiku` yoklamasi yapip son kosulardaki taze ek havuzlari gercek kosu zamani damgasiyla birlestirir ([butce_canli.rs](crates/ykt/src/butce_canli.rs)).
  - `Kullanim ve Limitler` ekraninda her pencere icin hem `%` hem kesin yerel reset tarih/saati + kalan sure (`Sifirlama: 21 Kas 21:10 (4 sa 30 dk)` / ileri sarilmissa `Tahmini sifirlama` / eskiyse `bayat`), altinda **`Model Bazli Haftalik Kullanim`** tablosu (`claude-fable-5-2` fiyat tanimli) ve Antigravity icin seffaf yerel sayac + rate-limit takibi gosterilir ([kullanim_ekran.rs](crates/ykt-holding/src/kullanim_ekran.rs)).

---

> Detaylı sürüm geçmişi için [CHANGELOG.md](CHANGELOG.md) dosyasına bakın.  
> **YKT Holding** · Geliştiren: **YKTera** · Tüm hakları saklıdır.
