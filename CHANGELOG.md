# YKT Holding — Sürüm Geçmişi

## v1.8.12 (2026-11-24)

### Yenilikler
- **Patron Odasi Ziyareti & En Cok 3 Ajan Kapasitesi (`kampus/mod.rs`, `kampus/iso_hareket.rs`, `kampus/izometrik.rs`):**
  - Patron onayi/karari bekleyen yerel ajanlar (`patron-onayi` veya `onay-bekliyor` + `onay: patron`) dis haritada cam koprulerden Merkez Ofis'e (`ykt-merkez`) yurur ve Patron odasina (`yk-odasi` / `baskan-odasi`) gelir; kendi binalarinda klonlanmaz.
  - Patron odasinin icine ayni anda en cok **3 ajan** (`PATRON_ODA_KAPASITE = 3`) cakismayan ziyaretci noktalarina (`Patron onayi` + altin gulen yuz) alinir.
- **Lobi Kuyrugu & Onay Sonrasi Yumusak Giris (`kampus/iso_hareket.rs`):**
  - 3'ten fazla onay bekleyen ajan varsa fazlaliklar Merkez Ofis'teki **Lobi** odasinda (lobi yoksa Patron odasinin kapi onunde koridorda) deterministik sira numarasiyla (`Lobide sira (#1)`, `#2`, ...) bekler.
  - Patron icerdeki bir ajana onay verdiginde o ajan kendi binasina doner ve lobide bekleyen siradaki ajan koridordan yumusak yuruyusle (`IcHareket`) Patron odasina girip varista 0 FPS'e doner.

## v1.8.11 (2026-11-24)

### Duzeltmeler
- **Kart Bagimlilik Okumasi (`ykt-core/src/kart.rs`):**
  - `Kart` yapisi kart on-bilgisindeki `bagimli: [...]` listesini artik dogrudan okur.
- **Durust 2.5D Gorev Teslimi (`ykt-holding/src/kampus/iso_hareket.rs`):**
  - Katlar arasi (`bina_katlar_arasi_ziyaretler`) ve ayni kat (`hedefleri_hesapla`) teslim/dagitim akisi ortak `aktif_teslim_karti` kuralina baglandi.
  - `bekliyor` durumundaki bir kart yalniz tum `bagimli` onkosullari `bitti` oldugunda ve lider o an gercekten aktif (`Calisiyor` veya uzerinde `durum: calisiyor` karti varken) teslim olarak gosterilir; uyuyan/bosta liderler veya bagimliligi bitmemis kartlar icin artik sahte `YK · Gorev -> ...` / `Gorev aliyor` gosterilmez.

## v1.8.10 (2026-11-24)

### Yenilikler ve Duzeltmeler
- **Kanonik `onay: gm` Yazimi (`ykt-core/src/kart.rs`, `ykt/src/{proje,pm,denetci,calisan}.rs`):**
  - Tum uretim kart yazicilari (`proje.rs`, `pm.rs`, `denetci.rs`, `calisan.rs` ve `ykt_core::kart::onay_sahibi`) eski `onay: demir` yerine kanonik `onay: gm` (`marka::GM_KIMLIGI`) yazar; eski kartlar `marka::gm_mi` ile geriye uyumlu okunmaya devam eder.
- **Gercek Eskalasyon — Kalici Engel 24 Saat Asiminda Otomatik Patron'a Yukseltme (`ykt-core/src/kart/durum_makinesi.rs`, `ykt-core/src/sohbet.rs`, `ykt/src/calisan.rs`, `ykt-holding/src/ekran.rs`):**
  - Durum makinesine `Engel -> PatronOnayi` gecisi eklendi; gecici olmayan `engel` kartlari 24 saat `zaman_asimi` doldugunda sessizce takili kalmak yerine otomatik olarak `durum: patron-onayi` (`onay: patron`, `sahip: patron`, `yukseltme_nedeni: <engel_sinifi>`, `engel` temizlenerek ve `Sorular`'a engel ozeti eklenerek) durumuna yukseltilir.
  - Yukseltilmis engel kartlari kart panelinde "is bitti" yerine durustce **"Engel · Karar"** ve **"Engel yukseltildi (<sinif>) - yonetici/GM sure icinde cozemedi, senin kararini bekliyor"** olarak gosterilir.
  - `durum_cek_ic` kart `engel` durumundan cikarken eski `engel:` alanini temizler.
- **Durust 2.5D Ofis ve Lider Etiketi (`ykt-holding/src/kampus/iso_hareket.rs`):**
  - Yalniz gercekten yonetici/GM incelemesi bekleyen (`onay-bekliyor`, Patron onayi olmayan) kartlar ajani liderin odasina (`Lidere soruyor` + mavi `?`) goturur; teknik `engel` (kirmizi `!`) ve `patron-onayi` (altin gulen yuz) kartli ajanlar kendi masalarinda kalir.
  - Uyuyan veya bosta olan bir liderin ustunde artik sahte `"Soru yanitliyor"` yazmaz: yalniz `Calisiyor` durumundaki lider `"Soru yanitliyor"`, bosta/uykuda olan lider `"Inceleme bekliyor"` gosterir.

## v1.8.9 (2026-11-24)

### Yenilikler ve Duzeltmeler
- **Canli Ajan Kafa Simgeleri (`kampus/izometrik.rs`, `kampus/mod.rs`):**
  - Ajanlarin kafalarinin sag-ustunde saf 2D vektor durum baloncuklari eklendi: is tikandiginda / 10+ dk ilerlemediginde (`takildi`) / hata veya teknik engelde **kirmizi unlem (`!`)**, Patron'a soru veya Patron onayi/karari gerektiginde **altin gulen yuz**, liderden veya GM'den cevap beklendiginde **mavi soru isareti (`?`)**.
- **Kompakt, Cakismasiz Ajan Rozetleri ve Kat Kisaltmasi (`kampus/izometrik.rs`, `kampus/iso_hareket.rs`):**
  - Ajan ustu rozetinden AI motoru/model ve uzak makine tekrari kaldirildi; yan yana duran ajan rozetleri dikey basamaklanarak cakismaz.
  - Baska kata cikan/inen ajanlarda uzun `"Asansorle cikti"` / `"Asansorle geldi"` yerine kaynak kat kisaltmasi (`K1 · Lidere soruyor`, `YK · Gorev -> ...`) gosterilir.
- **Ferah Hizli Ajan Karti & Okunakli Model Etiketleri (`kampus/izometrik.rs`, `ykt-core/src/motor_secim.rs`):**
  - Ajana tiklandiginda acilan Hizli Ajan Karti (`336px`) ad, gorev/unvan, acik durum, `AI Motoru:` rozeti (`AGY Neon (Med)` vb.), ilgili kart ve fonksiyon dugmelerini kendi satirlarinda kesilmeden ve ust uste binmeden gosterir.
- **Engel / Onay Karti Baglama Duzeltmesi (`kampus/mod.rs`, `kampus/iso_hareket.rs`):**
  - Acik `engel` / `onay-bekliyor` / `patron-onayi` karti bulunan ajanlarin kart bilgisi `Ajan.kart` alanina baglandi; boylece lider odasina cikan ajanlara tiklandiginda `"Aktif kart yok"` gorunmesi giderildi ve karti olmayan ajanlar icin sahte danisma ziyareti engellendi.

## v1.8.8 (2026-11-24)

### Duzeltmeler
- **Sade Ajan Ustu Etiketi (`kampus/izometrik.rs`):**
  - 2.5D ic kat kesitinde her ajanin uzerindeki cam rozette artik adinin yaninda unvani tekrarlanmaz (odalarin cam duvarinda zaten isim + unvan yer alir); boylece yan yana gelen ajan etiketleri sade ve cakismasiz gorunur.
  - Ajanin uzerine tiklandiginda acilan Hizli Ajan Karti'nda gorevi/unvani (`Ad — Unvan`, unvan bossa `rol` yedekli) gosterilmeye devam eder.
- **Canli Orkestrasyon Odalari Esitlemesi:**
  - `YKT Orkestrasyon Muhendislik` binasindaki 6 bireysel odanin adlari diger sirketlerle ayni `<Ad> - <Rol>` standardina esitlendi.

## v1.8.7 (2026-11-23)

### Yenilikler ve Duzeltmeler
- **2.5D Izometrik Oda Duvari Plaketleri ve Bina Cati Tabelalari (`kampus/izometrik.rs`):**
  - Ic kat kesitinde odalarin onunde havada durup cok odali katlarda birbirine karisan zemin etiketleri kaldirilarak her odanin **on-sol cam duvarinin icine tam duvar egiminde gomulu 2.5D mimari plaket** (`oda_duvar_etiketi_ciz`) eklendi.
  - Tek satira sigmayan uzun `ISIM - UNVAN` etiketleri `" - "` / `" · "` / `" / "` ya da en dengeli kelime sinirindan otomatik olarak **2 temiz satira bolunur** (`etiketi_ikiye_bol`, `metni_sigdir`), 0.5 px adimli font olcekleme (`font_adim`) ve dusuk zoom gorunurlugu ile komsu odalarla cakismaz.
  - Dis bina gorunumlerinde sokak seviyesindeki yuzer isim rozeti kaldirilarak her binanin catisina celik destekli ve 4 kamera acisina uyumlu **2.5D mimari cati tabelasi** (`cati_tabelasi_ciz`) sabitlendi; bina durum kartlari tabelanin ustunde cakismadan konumlanir.
- **Tam Ekran (Maximized) Baslangic (`main.rs`):**
  - Uygulama sifirdan acildiginda dogrudan ekrani tamamen kaplayarak (`.with_maximized(true)`) acilir; pencere kucultuldugunde (Restore) son kaydedilen normal boyut/konuma (yoksa `1280x800`) doner.
- **Eski Surum Metinleri, 17 Ajan Profili (`agents/*.md`) ve Sablon Temizligi:**
  - `Tum ofis` grubundaki `"Demir'in yerine konusma planlayicisi"` basligi `"Ofis is planlayicisi"` olarak duzeltildi; arayuz, CLI, cekirdek mesajlari, 17 `agents/*.md` rol profili (`yonetici.md` ve `ux-tasarimcisi.md` tutarliligi dahil), `sablonlar/` ve `docs/KONUSMALAR.md` eski surum artiklarindan (`Demir`, `ajans`, `ajans.json`, `~/.ajans`, `cop.js`, ic kart kimlikleri) arindirildi.
  - Tum dahili geriye uyumluluk sozlesmeleri (`~/.ajans`, `ajans.json`, `onay: demir`, `--kimden gm|demir`, `Demir otomatik onayi:` + `GM otomatik onayi:`, `kapilar.json` regex desenleri) korundu.
- **K0 Guvenlik Kapisi `ykt cop` Sertlestirmesi (`ykt-guard/src/kapi.rs`):**
  - `kesin_segment` ve `yazan_komut()` icinde yalniz `ajans cop` degil, `ykt cop` / `ykt.exe cop` / `ykt --kok <yol> cop` komutlari da yazma hedefi olarak denetlenerek kart siniri ve K0 korunan yol kontrollerine baglandi (`komut_yapilacak` iki bicimi de tanir).

## v1.8.6 (2026-11-23)

### Yenilikler ve Duzeltmeler
- **Proje Baslatma ve Kapsam Kesfi Kapisi (`proje.rs`, `kurulus.rs`, `sihirbaz.rs`, `agents/yonetici.md`):**
  - Yeni bir proje kuruldugunda artik ekip kartlari Patron'dan girdi ve onay almadan kendi basina kosmaya baslamaz.
  - Her yeni projede **`<ONEK>-0001`** numarali ilk kart projenin **yoneticisine (`rol: yonetici`, `pm: kesif`, `onay: patron`, `cwd: <kok>`)** acilir; yonetici bu kartta uretim/kodlama/yayin yapmadan proje turune ve aciklamaya gore eksik kritik bilgileri (hedef platform/kanallar, erisim/hesap/kaynak, teslimat bicimi/ton, kapsam siniri, oncelik ve takvim) **2-4 secenekli onerilerle** (`(onerilen)` ilk sirada) Patron'a sorar.
  - Sonraki tum ekip kartlari (`0002`, `0003`, ...) kendi bagimlilik zincirlerini indeks kaymasiz koruyarak **`<ONEK>-0001`'e bagimli** acilir ve baslamadan once kesif notundaki / hub notundaki Patron cevaplarini okumasi zorunlu kilinir; Patron kesif kartini cevaplayip onaylamadan hicbir ekip karti kosmaz.
  - Kesif karti `cwd: <kok>` ile kod deposunda gereksiz bos worktree acmaz; Rapor `KANIT: TAM` + ters tirnakli `- Belge: \`...\`` bicimiyle kanit kapisindan dogrudan gecer.
- **Temiz Worktree Kurtarma Duzeltmesi (`calisan.rs::kalinti_worktree`):**
  - Sifir commitli veya bitmis/birlestirilmis **temiz ve ignore'suz** `.kart-wt` kalinti klasorlerinde Windows Geri Donusum Kutusu (`SHFileOperationW`) kilit/tasima hatasiyla kartlarin kalici `engel`e dusmesi giderildi: once resmi `git worktree remove` + `prune` denenir (dal korunur), gerekirse Geri Donusum yedegine dusulur ve iki hata birlikte raporlanir.

## v1.8.5 (2026-11-23)

### Duzeltmeler
- **GitHub Releases Yonlendirme Zinciri Destegi (`sistem/guncelleme.rs`):**
  - `latest_getir()` ve `indir()` artik OAuth icin tum yonlendirmeleri kapatan `bulut::istemci()` (`Policy::none()`) yerine, yalnizca resmi HTTPS GitHub yayin adreslerine (`github.com/ecankinsundev/YKT-Holding-Releases/...`, `release-assets.githubusercontent.com`, `objects.githubusercontent.com`) izin veren ozel guvenli `indirme_istemcisi()` (`.https_only(true)`, port/userinfo reddi, en cok 5 adim) kullanir.
  - Boylece guncelleme denetimi ve `setup.exe` indirmesi sirasinda GitHub'in `302/303` CDN yonlendirmelerinden kaynaklanan `HTTP 302/303` hatasi kokten giderildi; OAuth istemcisi `Policy::none()` izolasyonu korundu.

## v1.8.4 (2026-11-23)

### Yenilikler ve Duzeltmeler
- **Windows Sistem Tepsisi Versiyon ve Guncelleme Menusu (`sistem/tepsi.rs`, `sistem/guncelleme.rs`, `sistem/ekran.rs`, `lib.rs`, `main.rs`):**
  - Sag alt sistem tepsisi uzerine gelindiginde gorunen ipucu (`szTip`) ve sag tik menusu basligi canli uygulama surumunu (`YKT Holding v1.8.4`) ve guncelleme durumunu (`(Guncel)`, `Yeni surum vX.Y.Z hazir!`, `indiriliyor...`, `kuruluma hazir`) gosterir.
  - Sag tik menusune **`Guncellemeleri denetle`** ve yeni surum bulundugunda **`Guncelle (vX.Y.Z)` / `Simdi kur (vX.Y.Z)`** secenekleri eklendi; pencere tepsiye gizliyken bile `eframe::App::logic` uzerinden arka planda `latest.json` denetlenir, sonuc Windows tepsi balon bildirimiyle (`NIF_INFO`) gosterilir, `setup.exe` SHA-256 dogrulamasiyla indirilir ve guvenli kapatma uzerinden kurulum baslatilir.
  - Indirilen kurulum dosyasinin beklenen surum dosyasiyla birebir eslesmesi (`kurulum_dosyasi`) ve kapanis kutusunda `Vazgec` secildiginde bekleyen kurulum planinin temizlenmesi guvence altina alindi.

## v1.8.3 (2026-11-23)

### Duzeltmeler
- **Oda Disi Bos Kat Kosesine Yerlesme Hatasi Giderildi (`iso_hareket.rs`):**
  - Ust kattaki yonetici alt kata gorev teslimi (`Teslim`) icin indiginde, o katta soru/onay/engel bekleyen baska bir ajanin bu katta ofisi olmayan ziyaretci yoneticiyi hedefleyip oda disi bos kat kosesine (`yedek_konum(None)`) dusmesi hatasi kokten giderildi.
  - **Net Katlar Arasi Koreografi:** Lidere soru/onay/engel sorulacagi zaman (`Danis`) calisan asansorle **liderin ofisine** (`Yonetim Kati`) cikar ve sorulan lider soruyu yanitlamak icin kendi ofisinde kalir; odasinda danisan ajan yoksa lider is vermek icin asansorle **ajanin bireysel odasina** iner (`Teslim`). Ayni-kat danisma gecisi de yalniz bu katta gercek ofisi bulunan (ziyaretci olmayan) liderleri hedef alir; hicbir ajan oda disi bos koseye yerlestirilmez.

## v1.8.2 (2026-11-22)

### Yenilikler ve Duzeltmeler
- **2.5D Cam Asansor, Ferah En Ust Kat Luks Yonetim Kati & Katlar Arasi Yonetici Ziyareti (`proje.rs`, `proje_yasam.rs`, `kampus.rs`, `ofis.rs`, `iso_hareket.rs`, `izometrik.rs`):**
  - Her cok katli sirket binasinin **en ust kati daima Yonetim Kati'dir (`id: "yonetim"`, `ad: "Yonetim Kati"`, `katlar.last()`)**: tek yonetici varsa ust katta tek basina luks penthouse odasinda (`10x7` karo, gece-lacivert hali + cift seritli altin/camgobegi cerceve, strateji panosu, 2 kose salon bitkisi, misafir koltuklari, pirinc lamba), birden fazla yonetici varsa tumunun luks odalari ayni Yonetim Kati'nda (`8x6` karo) yer alir; alt proje katlarinda tek tek yonetici odasi acilmaz.
  - Cok katli binalara sol omurgada 4 kamera acisina donen tiklanabilir **2.5D cam asansor safti** eklendi (`K1`/`K2`/`YK` gostergesi, yon oklari, bosta 0 FPS).
  - Ust kattaki yonetici alt katta aktif is verirken asansorle inip ilgili personelin bireysel odasina yurur (`Teslim`), alt kattaki calisan soru/engel durumunda ust kattaki yoneticiye asansorle cikar (`Danis`); tek kaynakli deterministik ziyaret hesabiyla ajanlar asla iki katta birden klonlanmaz ve varista 0 FPS'e doner.
  - `tema_tahmini` icindeki kisa (`<5` karakter, or. `"sla"`) anahtar kelimelerin ilgisiz proje adlarinda yanlis tema secmesi hatasi giderildi.
- **Ctrl+V Panodan Dogrudan Gorsel Ekleme (`bildir.rs`, `ekran.rs`, `konusmalar.rs`, `sihirbaz.rs`, `lib.rs`):**
  - Kart Paneli (`Okunakli` ve `Teknik`), `Konusmalar` (Grup/Ajan/Kurulus), Proje Sihirbazi Adim 2 ve `Gelistiriciye bildir` metin kutularinda `Ctrl+V` (`egui::Event::PasteImage` + Windows `CF_DIB` yedegi), `+ Gorsel` dugmesi ve surukle-birak ile dogrudan ekran goruntusu eklenebilir.
  - Tum gorseller mevcut kati guvenlik boru hattindan (`<= 5 MB`, `<= 8192px`, symlink reddi, magic-byte + EXIF/polyglot temizligi + PNG yeniden kodlama, atomik yazim) gecerek `<kok>/durum/ekler/` altina kaydedilir; 32x32 onizleme cipi + `[x]` kaldirma sunulur ve gonderilmeden vazgecilen taslak gorselleri diskten otomatik temizlenir.
- **Yonetici Model & Devir Politikasi + Efor Tavani (`ekip.rs`, `havuz.rs`, `motor.rs`, `politika.rs`, `pm.rs`, `proje.rs`, `agents/{yonetici,proje-lideri}.md`):**
  - Kota dolmadikca tum yoneticiler (`rol == "yonetici"`) proje uzmanlik alanina gore **`claude / fable` (Fable 5.2)** (mimari, guvenlik/uyum, finans, gomulu/donanim, masaustu/oyun) veya **`antigravity / gemini-4-neon-high` (AGY Neon High)** (web, mobil, sosyal medya, icerik, pazarlama/SEO, satis/CRM, destek, veri/arastirma) olarak atanir.
  - Yonetici kota devri **`Fable 5.2 <-> AGY Neon High`** olarak degisir; yalniz ikisinin de kotasi dolarsa **`Claude Opus 5.5`**'e duser (gizli kartlarda K0/Claude siniri korunur).
  - Patron elle degistirmedikce otomatik efor, `proje politikasi` ve `ykt plan kartlar` WBS kartlari **en fazla `high`** ile sinirlanir; Patron'un kartta veya kadroda elle verdigi `xhigh`/`max` tercihleri korunur.
- **Arka Planda Calisma & Windows Sistem Tepsisi + Sol Menu `Cikis` Dugmesi (`sistem/tepsi.rs`, `ekran.rs`, `lib.rs`, `main.rs`):**
  - Sol menunun en altina **`Cikis`** dugmesi eklendi; normal guvenli kapatma sureci (`Sistem::kapat`, calisan ajan/taslak sorusu, cocuk temizligi) yalniz sol menu `Cikis` veya sistem tepsisi sag tik `Cikis` secildiginde yurutulur.
  - Pencere carpisina (`X`) basildiginda uygulama kapatilmaz, sag alt Windows sistem tepsisine gizlenerek arka planda calismaya devam eder (`eframe::App::logic` ile gizliyken de olay/veri tazeleme, calisan dongusu izleme ve saglik/butce tiki surer); tepsi simgesine tikla `Goster`/`Gizle`, sag tik ile `Goster` / `Gizle (Tepsiye al)` / `Cikis` secilebilir, ikinci exe acilisi gizli pencereyi geri getirir.
- **Konusmalar Vazgecilen Kurulus Filtresi & Grup Ayrimi (`konusmalar.rs`):**
  - Kurmaktan vazgecilen (`durum: "iptal"`) proje kurulus taslaklari artik `Konusmalar` listesini kirletmez; grup listesi acikca **`OFIS VE SIRKETLER`** ve **`PROJELER`** basliklarina ayrildi.

## v1.8.1 (2026-11-22)

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

## v1.8.0 (2026-11-22)

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

## v1.7.0 (2026-11-21)

### Yenilikler ve Duzeltmeler
- **Antigravity Canli Kota & Tam Gorunurluk (`ykt butce --canli` + `--agy`):**
  - Resmi ve **0 token** tuketen `agy --output-format json -p="/usage"` komutu `butce_canli.rs` icine entegre edildi; her `ykt butce --canli` (ve yeni `--agy`) calismasinda `Gemini Models` ve `Claude and GPT models` (Haftalik + 5 Saatlik) kalan/kullanilan yuzdeleri ile kesin yerel sifirlama saatleri `durum/agy-kullanim.json` dosyasina atomik yazilir.
  - `Kullanim ve Limitler` ve `Ayarlar > Kota ve butce` ekranlarina **`Canli olcum`** rozeti (yas ve `reset_time` tazelik denetimli) ile **`Antigravity Olc`** dugmesi eklendi; hata/zaman asimi durumunda son gecerli dosya korunur ve Claude olcumu kesintiye ugramaz.
- **Fable 5.2 & Tum Antigravity Modellerinin Tam Gorunurlugu (`motor_secim.rs` + `modeller.json`):**
  - Eski `Fable 5.1` etiketi **`Fable 5.2`** olarak guncellendi; tum model secicilerde (Kart Paneli, Ajan Sag-Tik Menusu, Ajan Ozellikleri, `Model havuzu`) **Claude Code** (`Fable 5.2`, `Opus 5.5`, `Sonnet 5.5`, `Haiku 5.5`) ve **Antigravity** (`AGY Neon (High)`, `AGY Neon (XHigh)`, `AGY Carbon`, `AGY Argon`, `AGY Hydrogen`, `AGY Flash 3.8`, `AGY Opus 5.5`, `AGY Sonnet 5.5`) gruplu ve acik bicimde listelenir.
  - Ajan Ozellikleri acilir kutusundaki Antigravity model adlarindan tire silen hata giderildi; `sablonlar/modeller.json` kataloguna `agy-neon-xhigh` ve `agy-hydrogen-high` eklendi.
- **Gelistiriciye Bildir Dogrudan E-posta API Arayuzu (`ekinsun@yktera.com`):**
  - `Ayarlar > Hakkinda > Gelistiriciye bildir` altina acilir **`Dogrudan e-posta API ayari (Resend)`** bolumu eklendi: maskeli `BILDIRIM_EPOSTA_ANAHTAR` ve istege bagli `BILDIRIM_EPOSTA_KIMDEN` dar erisim izniyle (`~/.ykt/anahtarlar.json`, ajan ortamlarina asla verilmez) kaydedilip silinebilir, **`Test bildirimi gonder`** dugmesiyle tek tikla dogrulanabilir.
  - `ykt-core::anahtar` tum kontrol karakterlerini (CRLF/null) reddeder; Resend 401/403/422 hata mesajlari anahtari ve ham yaniti asla sizdirmaz.
- **Resimli Turkce Kullanici Kilavuzu PDF (`docs/YKT-Holding-Kullanim-Kilavuzu.pdf`):**
  - "Sirket mi, Proje mi, Kart mi?" karar rehberi (sosyal medya hesabi yonetimi dahil 7 gercek hayat ornegi), 23 hazir ekip paketi, 2.5D ofis, `Okunakli | Teknik` hibrit terminal, canli kota ve K0 guvenlik kapisi ekran goruntuleriyle 10 sayfalik PDF olarak GitHub depolarina eklendi.

## v1.6.0 (2026-11-21)

### Yenilikler ve Duzeltmeler
- **Hibrit Gercek Terminal & Tek Tikla Oturumu Devral (`ykt kosu izle` + `devral` / `geri-ver`):**
  - Ortak stream-json bicimleyici `ykt-core::kosu_akis` modulune tasindi ve **`ykt kosu izle <ID> [--takip]`** CLI alt komutu eklendi; `Teknik` kipteki gercek gomulu PowerShell artik ham JSONL yerine renkli, Claude CLI tarzinda okunakli canli cikti gosterir (`Ctrl+C` ile temizce `PS>` satirina doner; raw ESC/kontrol kacislari ve gizli veriler temizlenir).
  - Kosan/bekleyen Claude kartlarina tek tikla **`Oturumu Devral (Claude)`** ve **`Ajana geri ver (Baslat)`** eklendi: ajan guvenle durdurulur, yalitim worktree'si korunur, `devralan: patron` kilidi cift calisma ve `cevapla` cakismasini engeller, PowerShell ortami tum `AJANS_*` / `YKT_*` degiskenlerinden arindirilir ve `Ajana geri ver` acik terminali kapatip ajana kaldigi oturumdan devam etmesini soyler.
- **Silikon Vadisi 2.5D Kampus Peyzaji (`izometrik.rs`):**
  - Gereksiz/sahte bina eklenmeden yalniz gercek holding binalarinin cevresine Apple Park / Bay View tarzinda pahli tas avlu meydani, yuruyus yollari, mimari cim adalari, yansimali havuz, 3 farkli 2.5D agac/cit stili (Kaliforniya selvisi, zeytin/mese taci, saksili simsir), ahsap avlu banklari ve gece sicak isik halkali yol lambalari eklendi (Gece & Gunduz palet uyumlu, 4 kamera acisinda tam derinlik siralamali, bosta **0 FPS**).
- **Guvenli Gelistiriciye Bildir (`ekinsun@yktera.com` + Ekran Goruntusu):**
  - `Ayarlar > Hakkinda > Gelistiriciye bildir` her zaman etkin hale getirildi; yorum kutusu, dosya secici (`GetOpenFileNameW`), panodan yapistirma (`CF_DIB`) ve surukle-birak ile en cok 3 ekran goruntusu eklenebilir.
  - Guvenlik kapisi yalniz **PNG, JPG, JPEG, WEBP** kabul eder (`<= 5 MB` okuma oncesi sinir, symlink reddi, magic-byte + boyut `<= 8192px` dogrulama, EXIF/tEXt/COM ve polyglot son-ek temizligi, PNG piksel yeniden kodlama, sabit `ekran-N` adlandirma, CRLF baslik temizligi ve sifir gomulu sir).
- **Opsiyonel Otomatik Guncelleme & Surum Notlu Bildirim:**
  - `Ayarlar > Surecler` ve `Ayarlar > Hakkinda` altina **`Otomatik guncelle`** anahtari eklendi (varsayilan kapali). Acikken yeni surum resmi HTTPS kaynaktan indirilir, SHA-256 iki kez (yazarken ve baslatmadan once) dogrulanir ve kosan isler bitince otomatik kurulur. Kapaliyken ust seritte **`Yeni surum mevcut`** bildirimiyle kisa degisiklik ozeti + **`Indir ve kur`** / **`Sonra`** dugmeleri gosterilir.
- **Kurulu Tum Motorlar & Antigravity Kotalari (`Kullanim` + `Ayarlar > Butce`):**
  - `Kullanim ve Limitler` ve `Ayarlar > Butce` ekranlari artik yalniz Claude'u degil, `motorlar-onbellek.json`'daki **kurulu tum motorlari** (Claude, Antigravity, kuruluysa Ollama ve Gecit) gosterir; Antigravity icin gunluk havuz sayaclari, UTC sifirlama geri sayimi, aktif rate-limit bekleme kartlari ve elle Antigravity kota/sifirlama kaydi eklendi.
- **Ayarlar Alt Oge Hiyerarsisi + Ust Ogeyi Kapatma & 1 Cumlelik Onay Ozeti:**
  - Ayarlar sol menusunde ust gruplar acik/kapali oku (`▾`/`▸`) ve vurgu seridiyle, alt ogeler ise dikey agac cizgisi + girintiyle net bicimde ayrildi; acik ust gruba tekrar tiklandiginda grup kapanip **Ayarlar Ana Sayfasi** kart gorunumune doner.
  - Sol **Onay bekleyenler** panelinde artik teknik log satiri yerine kartin amacini anlatan **1 cumlelik sade ozet** gosterilir (`ENGEL:` ve acik kararlar oncelikli).

## v1.5.0 (2026-11-21)

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

## v1.4.0 (2026-11-21)

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
