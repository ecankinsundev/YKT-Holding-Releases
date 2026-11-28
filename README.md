<p align="center">
  <img src="assets/ykt-holding-logo.png" alt="YKT Holding — YKTera" width="128" height="128" />
</p>

<h1 align="center">YKT Holding</h1>

<p align="center">
  <strong>YKTera</strong> tarafından geliştirilen çok-motorlu yapay zeka organizasyon ve ajan yönetim platformu.<br/>
  Yerli masaüstü uygulamasından şirketlerinizi, projelerinizi, otonom ajanlarınızı, kalıcı hafızanızı ve gömülü tarayıcınızı yönetin.
</p>

<p align="center">
  <strong>Güncel Sürüm:</strong> <code>v1.9.1</code> (2026-11-28) &nbsp;·&nbsp;
  <a href="https://github.com/ecankinsundev/YKT-Holding-Releases/releases/tag/v1.9.1">Sürüm Sayfası</a> &nbsp;·&nbsp;
  <a href="CHANGELOG.md">Tüm Sürüm Notları</a>
</p>

---

## İndirme (v1.9.1)

| Platform | Paket Türü | İndirme Bağlantısı | SHA-256 |
|---|---|---|---|
| **Windows x64** | Kurulum Sihirbazı (Önerilen) | [`YKT-Holding_1.9.1_x64-setup.exe`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.9.1/YKT-Holding_1.9.1_x64-setup.exe) | `b22ac5189e0d67017fa4d7f46c0bd9f3c734f1a259024e6b980dc3d62db640ba` |
| **Windows x64** | Portatif Arşiv (Kurulumsuz) | [`YKT-Holding_1.9.1_x64-portatif.zip`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.9.1/YKT-Holding_1.9.1_x64-portatif.zip) | `6e22a22a0077f7a98f89a809f353a7f20c670a3175556e1797fd30661f3467cf` |
| **Güncelleme Manifestosu** | Sürüm Kaydı | [`latest.json`](https://github.com/ecankinsundev/YKT-Holding-Releases/releases/download/v1.9.1/latest.json) | — |

> **Bütünlük Doğrulama (PowerShell):**
> ```powershell
> (Get-FileHash .\YKT-Holding_1.9.1_x64-setup.exe -Algorithm SHA256).Hash.ToLower() -eq "b22ac5189e0d67017fa4d7f46c0bd9f3c734f1a259024e6b980dc3d62db640ba"
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
1. Yukarıdaki tablodan **`YKT-Holding_1.9.1_x64-setup.exe`** dosyasını indirin ve çalıştırın (yönetici izni gerektirmez).
2. Uygulama `%LOCALAPPDATA%\YKT Holding` klasörüne kurulur, kullanıcı `PATH` ortam değişkenine `ykt` komutunu ekler ve Başlat Menüsü / Masaüstü kısayollarını oluşturur.
3. **YKT Holding** uygulamasını açın; ilk açılış sihirbazı çalışma klasörünüzü, şirket/ekip yapınızı ve `ykt-guard` güvenlik kapılarını otomatik yapılandırır.

### Seçenek 2 — Portatif ZIP (Kurulumsuz)
1. **`YKT-Holding_1.9.1_x64-portatif.zip`** arşivini dilediğiniz klasöre çıkartın.
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

## Mevcut Sürümde Neler Var? (v1.9.1)

1.9.0 degisikliginin bagimsiz incelemesinde (8 inceleyici + 2 dogrulayici) dogrulanan bulgularin duzeltmeleri.
### Bagimsizlik (ayni makinede baska uygulamalarla yan yana calisma)
- **Ortak `~/.gemini/AGENTS.md` dosyasina yazilmaz (`ykt/src/kur.rs`, `calisan.rs`):** bu dosya makinedeki butun Antigravity oturumlarina yuklendigi icin `ykt kur` oraya artik `@import` yazmaz ve onceki surumun ekledigi `# YKT Holding` blogunu cikarir (baska satirlara dokunmaz). Holding kurallari `agy` / `ollama` kosusuna istemdeki yonergeyle verilir.
- **GM oturumu yalniz kendi kokunde aranir (`ykt-core/src/demir.rs`):** `~/.claude/sessions` icinde ad onekiyle eslesen oturum, calisma klasoru bu ornegin koku (ya da alti) degilse secilmez; ayni GM adini kullanan baska bir uygulamanin oturumuna ileti yazilmaz. `demir_oturum` kimligiyle secim degismedi.
- **Yalitim klasoru sahipligi (`ykt/src/yalitim.rs`, `calisan.rs`):** kurulan her yalitim klasorune sahiplik isareti (`.kart-wt/<ID>.ykt`) konur; kalinti temizligi isaretsiz ve kartin kaydindaki dalda olmayan klasoru kaldirmaz. Sicak derleme tabani `_ykt-taban` adina tasindi.
- **Drive koku (`ykt/src/bulut/drive.rs`):** kayitli kok kimligi yalniz `YKT/` ust klasoru altinda cozulduyse kullanilir; onceki surumden kalan kimlik birakilir ve esitleme `YKT/<klasor>` altinda bastan kurulur (yerel dosyalar durur, ilk esitleme yeniden yukler).
- **Ortak gecit servisi (`ykt/src/motor/gecit.rs`):** calisan claude-code-router gecidi bu uygulamanin istemci anahtarini tanimiyorsa `ykt motor gecit kur|baslat|durdur` yapilandirmayi ezmez ve sureci durdurmaz, nedenini soyleyip durur.
- **Profildeki gizli klasorler (`ykt-core/src/proje_baglanti.rs`, `ykt/src/dis_icerik.rs`):** ev klasorunun dogrudan altindaki adi `.` ile baslayan klasorler (hangi uygulamanin olursa olsun) kod silme ile silinmez ve `ykt dis topluluk` ile okunmaz.
- **Linux kurulum/kaldirma:** onceki surumlerin `~/.local/bin` altinda YKT ikililerine baglayip biraktigi ek komut baglantilari, hedefi YKT kurulum klasoru olan baglanti olduklari dogrulanarak temizlenir.
- **Kurulum hedefi denetimi (NSIS):** secilen hedef klasor bos degilse ve icinde `ykt-holding.exe` yoksa kurulum o klasore yazmaz.
### Duzeltmeler
- **Paketleme disk temizligi:** `paketle.js` artik ortak derleme klasoru `%TEMP%\ykt-build`i silmez.
- **Ana hafiza kasasi kapsami (`ykt-core/src/kapsam.rs`):** ana vault anahtari bir sirket adi sayilmaz; ayni kisa adli sirket kapsamda olsa da ana vault acikca baglanmadikca kapsamli makinede okunmaz.
- **`AGENTS.md` kopyasi:** ornek kokundeki isaretli kopya, isaretteki ad ne olursa olsun tazelenir (onceki surumun urettigi kopya bayat kalmaz).
- **Ilk kurulum iletisi, bilinmeyen komut iletisi, guncelleme sonrasi acilis denetimi (ikili basina tek kez), yukseltme provasi (kanca artik `~/.ykt/claude/settings.json` icinde aranir).**
- **Artik temizligi:** toplu yeniden adlandirmadan kalan cift liste ogeleri, kendine donen yedekler, anlamini yitirmis yorum ve testler, silinmis Node yoluna atiflar; kapi kural dosyalarinda yalniz birebir kopya girisler silindi (hicbir kural gevsetilmedi).
- **Test:** `Ayarlar > Surecler` alt bilgisi testte sabit surum etiketi cizer (surum artisi ekran goruntusunu bozmaz).
### Bilinen sinir
- Kapi kurallari yalniz bu uygulamanin kurulumunu ve `~/.ykt` klasorunu korur. Ayni makinedeki baska bir uygulamanin klasorlerini ve komutlarini ajan oturumlarina yasaklamak isteniyorsa ornegin `kurallar/kapilar.json` dosyasina (sahip oturumunda) o yollar icin `yazma_yasak` / `okuma_yasak` / `komut_yasak` girisleri eklenir.
- Yalitim klasoru ve kart dali adlari (`.kart-wt`, `kart/`) degismedi: iki uygulama AYNI kod deposunda AYNI kart kimligiyle calistirilmamalidir.

---

> Detaylı sürüm geçmişi için [CHANGELOG.md](CHANGELOG.md) dosyasına bakın.  
> **YKT Holding** · Geliştiren: **YKTera** · Tüm hakları saklıdır.
