# YKT Holding — Sürüm Geçmişi

## v1.3.1 (2026-11-21)

### Yenilikler ve Duzeltmeler
- **Sifir Surtunmeli Varsayilan Ajan Izinleri (Hem 0-dan Kurulum Hem `--yenile`):**
  - `ykt kur` ve `ykt kur --yenile` artik ornek klasorundeki `<kok>/.claude/settings.json` dosyasina (kullanici-genel `~/.claude/settings.json` dosyasini ve YKT disi depolari etkilemeden; bozuk dosyayi ezmeden ve yedek alarak) kapsami daraltilmis `permissions.allow` (`Read`, `Glob`, `Grep`, `ykt` is akisi alt komutlari, yerel `git`, `cargo`, `npm test`, `pytest` — Bash ve PowerShell) ile `permissions.additionalDirectories` (`ornek`, `vault`, `kod`) kurallarini kullanicinin mevcut izin ve `deny`/`ask` tercihlerini ezmeden birlestirir ([kur.rs](crates/ykt/src/kur.rs)). Tum arac cagrilari yine once `ykt-guard.exe kapi` (PreToolUse, K0) kancasindan gecer.
  - Ilk kurulumdaki calisma alani guveni (`guven_isaretle`) artik `kok` ve `app` yaninda `vault` klasorunu de `~/.claude.json` icinde guvenli isaretler (`kod` ust dizini ucuncu taraf repolari otomatik guvenmemek icin disarida tutulur).
  - `guvenli` mod (`acceptEdits`) ek dizin listesine (`ek_dizinler`) `ayar.kod` klasoru de eklendi ([calisan.rs](crates/ykt/src/calisan.rs)).
- **Haftalik Rapor & Temiz Kapanis Duzeltmeleri:**
  - Haftalik durum raporu karti ve taslagi artik eski `ajans plan sapma` yerine `ykt plan sapma` komutunu kullanir ([rapor.rs](crates/ykt/src/rapor.rs)).
  - Calisan dongusunun normal kapanisinda yarim kalan kosu yoksa (`idler.is_empty()`) `durum/olaylar.jsonl` icine sahte `exe-kapandi` alarmi yazilmaz ([calisan.rs](crates/ykt/src/calisan.rs)).
- **0-dan Kurulum Sablon Temizligi:**
  - Ilk sirket `CLAUDE.md` sablonundaki sahte `(ornek) ProjeAdi` satiri kaldirildi (haftalik rapor ajanlarinin olmayan `ProjeAdi` hakkinda soru sormasi onlendi) ve `sablonlar/ornek/kampus.json` icindeki her iki baslangic binasina **`Kahve & Dinlenme`** sosyal odasi eklendi.
- **Okunabilir Ajan Akisi & Arayuz Dili:**
  - `Ajani izle` -> **`Sohbet`** gorunumunde ajanin ve Patron'un mesajlari artik 300 karakterde kesilmez ve satir sonlari korunur (`Kopyala` dugmesiyle birlikte); arac hata sonuclari da genisletildi, boylece ajanin ne dedigini okumak icin `Terminal` gorunumune gecmeye gerek kalmaz ([kosu_akis.rs](crates/ykt-holding/src/kosu_akis.rs)).
  - Arayuzdeki `nihai` ifadeleri (`Patron'un nihai testi`, `nihai surum degil` vb.) daha dogal **`Son kontrol`** / **`kararli surum`** ifadeleriyle degistirildi ([ekran.rs](crates/ykt-holding/src/ekran.rs), [onay_paneli.rs](crates/ykt-holding/src/onay_paneli.rs)).

## v1.3.0 (2026-11-21)

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

## v1.2.0 (2026-11-21)

### Yenilikler ve Duzeltmeler
- **2.5D Izometrik 4 Yonlu Kamera Dondurme (`< Sol` / `Sag >`, `Q` / `R`):** Hem dis kampuste hem bina ici 2.5D kat kesitinde 90° adimlarla 4 izometrik bakis acisi (`On 0°`, `Sag 90°`, `Arka 180°`, `Sol 270°`) eklendi ([izometrik.rs](crates/ykt-holding/src/kampus/izometrik.rs)). Binalar, cam kopruler, kopruden suzulen ajanlar, kat odalari, masalar, ajan figurleri ve poligon isabet testi aktif aciya gore gercek zamanli dondurulup derinlik siralanir.
- **Hem 2.5D Hem Klasik Icin Yerinde Duzenleme ve 2.5D Bina Kozmetikleri (`Duzenle (E)`):**
  - 2.5D gorunumde `Duzenle (E)` artik klasik kipe atlamadan dogrudan 2.5D uzerinde acilir.
  - **Dis Kampus 2.5D Duzenleme:** Secili binayi yeniden adlandir, aktif kamera acisina gore ekrana uyumlu tasi (`Sola / Saga / Yukari / Asagi`, `tasima_deltasi`), `Geri al` ve `BinaKozmetik` ile her projenin/sirketin 2.5D mimarisini ozellestir (**Stil:** `Oto | Kule | Pavyon | Studyo`, **Vurgu:** `Oto | Camgobegi | Zumrut | Kehribar | Mor`, **Kat:** `Oto | 1..4`; [kampus_yaz.rs](crates/ykt-core/src/kampus_yaz.rs)). Merkez binasi (`YKT Merkez`) kozmetik/ad/silme degisikliklerine karsi korunur, secim ve kamera duzenleme boyunca korunur.
  - **Bina Ici 2.5D Kat Duzenleme:** Odaya tiklayip secme (duzenleme acikken hizli ajan kartiyla cakismaz), `Otomatik / Elle` yerlesim gecisi, `+ Oda`, `Adlandir`, ekrana gore `Sola / Saga / Yukari / Asagi` tasima, `+ Masa`, `- Masa`, onayli `Oda sil` ve `Geri al`.
- **`Klasik Piksel` Gorunumu ve Acik `Aydinlik / Karanlik` Modu `Ayarlar > Makine ve surecler > Tema` Altinda:**
  - Varsayilan ofis gorunumu **2.5D Izometrik**'tir; ust cubuktaki `2.5D / Klasik` dugmeleri kaldirilip **`Ayarlar > Makine ve surecler > Tema`** altina tasindi (`2.5D Izometrik` / `Klasik Piksel`, `~/.ykt/arayuz-ofis-kipi.txt`; [ayarlar.rs](crates/ykt-holding/src/ayarlar.rs)).
  - Ayni sayfada tum uygulamaya (2.5D Ofis dahil) uygulanan **`Gorunum modu (Aydinlik / Karanlik)`** secimi (`Gunduz`, `Gece`, `Otomatik`) belirgin baslik ve aciklamalarla netlestirildi.
- **Sehir Gorunumu Aktifken Sabit `Tahta | Konusmalar` Gelmez:** `Sehir gorunumu` kapaliyken `Tahta | Konusmalar` yan yana acilmaya devam eder; `Sehir gorunumu` tekrar acildiginda ekranda yalniz bu varsayilan paneller varsa otomatik kapanir ve 2.5D Ofis engelsiz gorunur ([lib.rs](crates/ykt-holding/src/lib.rs)). Kullanicinin actigi `Hafiza` gibi baska paneller veri kaybi olmadan katlanir.

## v1.1.0 (2026-11-21)

### Yenilikler ve Duzeltmeler
- **3 Katmanli 2.5D Izometrik Cam Kule Ofis (`OfisKipi::Izometrik`, varsayilan):** Eski piksel-art haritanin yanina saf 2D `egui::Painter` vektor cizimiyle (3D motor / shader yok) yeni varsayilan **2.5D** Ofis gorunumu eklendi ([izometrik.rs](crates/ykt-holding/src/kampus/izometrik.rs)). Ust cubuktaki `2.5D` / `Klasik` secimi `~/.ykt/arayuz-ofis-kipi.txt` dosyasinda kalici saklanir; `Duzenle (E)` mevcut klasik izgara duzenleyicisine sorunsuz gecer.
  - **Katman 1 (Dis Kampus):** Altin tacli cam kule (`YKT Merkez`) ve kat sayisina olcekli sirket pavyonlari, aktif/onay bekleyen kat isiklari, cam kopruler, yalniz gercek hedef degisiminde kopruden suzulen 2.5D ajan figuru + isik izi ve bina ustu tiklanabilir canli durum kartlari.
  - **Katman 2 (Bina Ici 2.5D Kat Kesiti):** Binaya cift tiklandiginda `kampus.json` odalari cam bolmeli 2.5D kat kesiti olarak acilir (cok katli binalarda kat secici + alt hayalet levhalar); 6 `Durum` + ortogonal `uzak` hologram gorunumu ve `veri.kartlar` (`ust` / `test_edilen` / `test_karti`) uzerinden gercek delegasyon Bezier yaylari cizilir.
  - **Katman 3 (Hizli Ajan Karti):** 2.5D gorunumde ajana sol tiklandiginda (HLD-AJS-0206 guncellemesi, Patron 2026-11-21) tuvali kapatmadan yaninda buzlu cam kontrol karti acilir: **`Canli Izle`** (binadan cikmadan `AjaniIzle` acar), **`Mesaj Yaz`**, **`Karti Ac`** ve **`Motor Degistir`** ([ajan_menu.rs](crates/ykt-holding/src/ajan_menu.rs)); ilk `Esc` karti, ikinci `Esc` binayi kapatir.
- **Bosta 0 FPS Yeniden Cizim & WCAG AA Tema Uyumu:** 2.5D kipte kopru gecisi/kamera hareketi veya odakta kosan is yokken kampus kendi yeniden cizim istemez (`izometrik_cizim_araligi` -> `None`; bosta 0 FPS), aktif kopru gecisinde ~20 FPS (50 ms), odakta kosan iste ~8 Hz (125 ms) calisir. Gece ve Gunduz izometrik paletleri uygulama temasini izler ve WCAG AA (`>= 4.5:1`) kontrast testiyle kilitlidir.

## v1.0.4 (2026-11-20)

### Yenilikler ve Duzeltmeler
- **Sol Menu Ac/Kapa (Toggle):** Sol menude halihazirda ekranda acik/gorunur olan bir bolmeye (`Konusmalar`, `Tahta`, `Projeler`, `Ajani izle` kosan karti izlerken, `Kullanim`, `Hafiza`, `Tarayici`, `Ayarlar`) tekrar tiklandiginda o bolme kapatilir ve kalan bolmeler bosluk birakmadan tam alana genisler ([ekran.rs](crates/ykt-holding/src/ekran.rs)). `Tahta` acikken `Projeler`'e (veya tersine) tiklamak kapatmak yerine diger gorunume gecer; tam ekran modunda arka planda gizli kalan bir bolmeye tiklamak ise o bolmeyi one getirir.
- **Sehir Gizliyken `Ofis` = Varsayilan `Tahta | Konusmalar` (Bos Ekran Yok):** `Sehir gorunumu` gizliyken sol menuden **`Ofis`** sekmesine tiklandiginda (veya gizli tercihli acilista / sehir gizlendiginde acik bolme yoksa) artik bos genel bakis ekrani yerine **`Tahta` (sol) ve `Konusmalar` (sag)** dogrudan yan yana acilir ([lib.rs](crates/ykt-holding/src/lib.rs)). Yalniz `Hepsini kapat` ile tum paneller kapatilirsa acilan genel bakis ekranina tek tik **`Tahta + Konusmalar ac`** dugmesi eklendi.
- **Belirgin Kalici Durum Rozeti:** `Sehir gorunumu` gizliyken ust seritteki `Kosan is: N  |  Patron onayi bekleyen: M  |  Ajan: K` bilgi satiri belirgin cerceveli durum rozeti icinde surekli gorunur kalir ([ekran.rs](crates/ykt-holding/src/ekran.rs)).

## v1.0.3 (2026-11-20)

### Yenilikler ve Duzeltmeler
- **Otomatik Butce Kalibrasyonu & Sakin Arayuz:** `ykt butce` artik kalibrasyonsuz taze kurulumda hata vermez, oturum verilerini sessizce tarar ve ilk gercek Claude Code `rate_limit_event` olcumuyle kendi tavanini otomatik kalibre eder; `%0` / `%5` alti dusuk yuzde olcumleri mevcut gecerli tavani bozmaz (`HAFTA_ESIGI = 5.0`). Calisan dongusu kapaliyken arayuz arka planda 15 dakikada bir sessizce `ykt butce` calistirir. Ust seritteki ve `Kullanim` / `Ayarlar > Kota ve butce` ekranlarindaki sari kalibrasyon uyarilari kaldirildi; elle kalibrasyon `Ayarlar > Kota ve butce` altinda istege bagli acilir bolume (`Elle kalibrasyon (istege bagli)`) alindi.
- **Sade Ust Serit:** Ust seritteki sabit 3'lu butce/limit cubuklari kaldirildi (tum limitler soldaki `Kullanim` sekmesinde). Ust serit tek satirda yalniz onay/kosan/olay cipleri, `Sehir gorunumu` anahtari ve sehir gizliyken kalici `Kosan is: N  |  Patron onayi bekleyen: M  |  Ajan: K` ozet bilgisini gosterir.
- **Sehir Gorunumu Gizliyken Varsayilan `Tahta | Konusmalar`:** `Sehir gorunumu` kapatildiginda (veya gizli tercihli acilista acik panel yoksa) ekran bos kalmaz; `Tahta` ve `Konusmalar` varsayilan olarak yan yana acilir, ozet bilgi satiri gorunmeye devam eder.
- **`Projeler` ve `Tahta` Sekme Duzeltmesi:** Sol menude **`Projeler`**'e tiklamak dogrudan `Proje listesi` (`+ Yeni proje` ve proje kartlari) gorunumunu, **`Tahta`**'ya tiklamak ise Kanban is tahtasini acar.

## v1.0.2 (2026-11-20)

### Yenilikler ve Duzeltmeler
- **Uygulama Ici Tam Yerlesik Bolmeli Pencere Yoneticisi (Serbest Pencere Yok):** `Konusmalar`, `Projeler`, `Kullanim`, `Hafiza`, `Tarayici`, `Ayarlar` ve kart panelleri artik serbest (yuzen) pencere olarak acilmaz; tek panel acikken calisma alanini tam ekran (%100) doldurur, ikinci ve sonraki paneller otomatik yan yana / alt alta bolunur. Baslik surukleyerek hedef bolmenin `Sola / Saga / Uste / Alta` yarisina birakabilir, ortadaki ayiricilari surukleyebilir, baslik dugmeleriyle `Sola / Saga / Alta yasla` veya `Tam ekran` (`Ctrl+Shift+X` / cift tik) kullanabilirsin; bir panel kapatilinca kalan paneller bosluk birakmadan genisler. Sol menudeki `Yerlesim` kismina `Tam ekran`, `Yan yana`, `Alt alta` eklendi (`Kademeli` kaldirildi).
- **Kalici `Sehir gorunumu` Ac/Kapa Anahtari (CPU/GPU Tasarrufu):** Ust seride kaydirmali **`Sehir gorunumu`** anahtar dugmesi eklendi. Gizli konumdayken (veya acik bolmeli paneller ekrani kaplarken) harita cizimi ve 30 FPS yenileme dongusu tamamen durur; secim `~/.ykt/arayuz-harita.txt` dosyasinda kalici olarak saklanir ve gizli modda hafif YKT Holding genel bakis ekrani gosterilir.
- **"Kampus" Ifadesinin Kaldirilmasi:** Kullanici arayuzundeki tum `Kampus` etiketleri kurumsal holding yapisina uygun olarak **`Ofis`** ve **`Sehir gorunumu`** olarak yenilendi.

## v1.0.1 (2026-11-20)

### Yenilikler ve Duzeltmeler
- **Sol Menu > Kullanim Sekmesi (`Ctrl+8`):** Tum yapay zeka motorlarinin 5 saatlik, gunluk ve haftalik kullanim limitleri tek ekranda toplandi: Claude Code (5 Saatlik, Haftalik, ayri Haftalik Fable havuzu ve durdurma esikleri), Antigravity (`Gemini 4 Neon / Carbon / Argon` ve `AGY Claude` 5 saatlik/haftalik dilimleri + gunluk UTC istek sayaclari), aktif rate-limit kota beklemeleri, yerel Ollama durumu, haftalik ajan kullanimi tablosu ve tek tik `"Olcumu yenile"` (`ykt butce`).
- **Kota Olcumu Bayatlama Duzeltmesi (`ykt butce` & `ykt-core`):** Onceki haftalik pencereden kalan `claude-code-rate-limit` veya elle kota olcumlerinin yeni haftada `durum/butce.json` dosyasini dondurup 70+ saatlik eski deger gostermesi giderildi (`elle_korunur` haftalik pencere sinirini denetler, ayni hafta icinde suresi dolan 5 saatlik pencereyi donmadan tazeler ve yeni haftada gecmis `bes_saat_sifirlama` kaydini temizler); taze gercek kota olcumu varken ust seritte eski kalibrasyon yasi uyarisi cikarilmaz.
- **Haritada Gezen Piksel Temizligi (Kampus):** Gokyuzunden gecen kus piksel surusu (`kuslar`) kaldirildi, otopark araclari yalniz aktif is varken (`kosan > 0`) cizilecek sekilde sinirlandirildi ve uzak gorunumde ajanlarin 8x8 renkli kare noktalar yerine gercek piksel-art karakter olarak cizilmesi saglandi.
- **Sol Menu & Ust Bar Kozmetik Duzeltmesi:** Sol menudeki marka satiri (`YKT HOLDING` + 24px logo) `MENU_GENISLIK` (`150px`) icinde sabitlenecek sekilde sinirlandirildi (`set_max_width` + `Truncate`), boylece sol menunun Kampus ust bari ve limit seridinin ustune binip harfleri kesmesi tamamen giderildi.

## v1.0.0 (2026-11-19)

### Yenilikler
- **YKTera / YKT Holding Marka Kimligi & Yeni Logo:** Altin geometrik `Y` monogrami ve elektrik-camgobegi yapay zeka elmas dugumuyle yeni `icon.png` / `icon.ico` / `icon.icns` uygulama simgeleri, sol menu marka rozeti ve `Ayarlar > Hakkinda` logosu tek elden yenilendi.
- **Gomulu Tarayici (Windows Glow + WebView2):** `eframe 0.37` Windows'ta varsayilan `Glow` (OpenGL) cizici + `WS_CLIPCHILDREN` ile gomulu WebView2 sekmeleri tam calisir hale getirildi (OpenGL yoksa otomatik `Wgpu` yedeklemesi); gercek URL'den kilit simgesi, sayfa ici URL senkronizasyonu, `Git` odak korumasi, `baglanti_istendi` CDP kuyruk korumasi, yetim WebView2 temizligi ve siki `localhost`/userinfo URL siniri eklendi.
- **Sade Kampus & WCAG AA Arayuz:** Sehir gorunumunden turuncu/beyaz parcacik yagmuru, konteyner/vinc/forklift/duman/kivilcim ogeleri kaldirildi; araclar yalniz aktif is varken gorunur. Sol menu 6 bolume indi (`Organizasyon` -> `Projeler` ust sekmesi), `Hesap`/`Bulten` kaldirildi, `Maliyet` -> `Kota ve butce` altinda birlestirildi, `"Nagihan"` -> `"Kalite denetimi"` oldu, Gece/Gunduz WCAG AA (`>= 4.5:1`) kontrast oranlari testle kilitlendi.
- **Motor Otomatik Guncelleme (`ykt motor guncelle`):** `claude update` ve `agy update` icin CLI alt komutu, `Ayarlar > Baglantilar > Motorlar > Motorlari guncelle` dugmesi, OS cekirdek `File::try_lock()` kilidi, zaman asiminda `taskkill /T /F` temizligi ve 6 saatlik ayri arka plan guncelleyici eklendi.
- **Tuketim Butcesi Duyarli `Fable` & `Gemini 4 Neon`:** Ayri haftalik Fable havuzu (`hafta_fable_yuzde`, `fable_esik`) arayuze baglandi; derin mimari/kok-neden/guvenlik isleri sayac taze ve koruma sinirinin altindayken `opus -> fable` terfi edilir, kuyrukta kota dolarsa yalniz otomatik terfiler `opus`'a iner (acik Patron secimi korunur). Kataloga `agy-neon-high` (`gemini-4-neon-high`) ve `agy-neon` (`gemini-4-neon-medium`) eklendi (15 model, `-xhigh` destekli).
- **Yayin Hatti (`YKT-Holding-Releases`):** `YAYIN_DEPOSU` `ecankinsundev/YKT-Holding-Releases` olarak yapilandirildi ve `crates/ykt-holding/paket/yayinla.js` ile her surumde kurulum/kullanim rehberi (`README.md`), `CHANGELOG.md`, `latest.json` ve GitHub Release varliklarinin otomatik yayinlanmasi eklendi.
