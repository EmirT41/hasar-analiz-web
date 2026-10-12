# PROBLEM KARTI (PROBLEM.md)
**Proje Adı:** Akıllı Servis Danışmanı  
**Proje Ekibi:**  
- Mustafa Emirhan Turhan (Öğrenci No: 240502019)  
- Mehmet Eren Yavuz (Öğrenci No: 240502010)  
**Ders:** Web Programlama Dönem Projesi  
**Tarih:** Ekim 2026  

---

## 1. Problemi Kim Yaşıyor ve İletişim Bilgileri

Projede ele alınan problem; oto sanayi esnafı, bireysel araç sahipleri ve şirket araçlarını yöneten işletme sahipleri tarafından üç farklı boyutta yaşanmaktadır. Görüşme yapılan ve süreci bizzat yaşayan kişiler:

1. **Mevlüt Yeşil** – Honda Özel Servisi & Yedek Parça İşletmecisi*  
   - **Konum:** Sanayi Mahallesi, İzmit Küçük Sanayi Sitesi, Kocaeli  
   - **Rolü:** Hizmet Veren / Usta & Esnaf (Honda ve Japon grubu araçların mekanik/elektronik tamiri, parça temini ve müşteri servis kayıtlarını yöneten servis sahibi)

2. **Yusuf Uğur** – *Bireysel Araç Sahibi (Özel Sektör Çalışanı)*  
   - **Konum:** Derince, Kocaeli  
   - **Rolü:** Hizmet Alan / Sürücü (Günlük aktif araç kullanan, gösterge arıza ışıklarında ve kaza/hasar anlarında teknik bilgi eksikliği yaşayan araç sahibi)

3. **Mehmet Akova** – *Şirket Sahibi / Firma Yöneticisi 
   - **Konum:** İlimtepe, Körfez
   - **Rolü:** Şirket Filo / Araç Yöneticisi (Şirket bünyesindeki 8 adet ticari ve binek aracın muayene, sigorta, periyodik bakım ve servis masraflarını takip eden işletme sahibi)

---

## 2. Problemi Yaşayan Kişilerle Yapılan Görüşmelerin Notları

### Görüşme 1: Mevlüt Yeşil (Honda Özel Servis & Yedek Parça)
* **Görüşme Tarihi & Şekli:** 08 Ekim 2026 – Yüz Yüze (İzmit Sanayi Mahallesi Servis Dükkânı)
* **Görüşme Notları:**
  - *"Müşteriler gün boyu WhatsApp’tan fotoğraf atıyor; kimi arıza lambasını çekip 'Usta yolda kalır mıyım?' diyor, kimi sürtme/kaza fotoğrafı atıp 'Tampon tırnağı mı kırık, komple parça mı değişecek, elinde çıkma var mı?' diye soruyor."*
  - Mesaj trafiği arasında parça kodlarını ve fiyatlandırmayı teyit etmenin dükkândaki asıl mekanik işi böldüğünü ve büyük vakit kaybı yarattığını belirtti.
  - Düzenli gelen müşterilerin dahi geçmişte hangi tarihte, hangi kilometrede hangi parçayı (triger, buji, şanzıman yağı vb.) değiştirdiğini tezgâh üstündeki defterden bulmanın çok zor olduğunu aktardı.
* **Kritik İhtiyaç:** Müşterinin hasarını ve arıza lambasını fotoğraf yükleyerek sisteme tarif edebileceği, aracın geçmiş bakım/parça kayıtlarının tek ekranda görülebileceği dijital bir servis platformu.

---

### Görüşme 2: Yusuf Uğur (Bireysel Araç Sahibi)
* **Görüşme Tarihi & Şekli:** 09 Ekim 2026 – Telefon Görüşmesi
* **Görüşme Notları:**
  - *"Geçtiğimiz ay göstergede motor ikaz ışığı yandı. Sorunun ne olduğunu bilemediğim için panikleyip arabayı kenara çektim ve çekici aradım. Meğer basit bir yakıt kapağı/sensör uyarısıymış, gereksiz masraf yaptım."*
  - Ufak bir maddi hasarlı sürtmede torpidodaki kaza tutanağını nasıl dolduracağını, krokisini nasıl çizeceğini bilmediğini ve karşı tarafla gerginlik yaşadığını ifade etti.
  - Muayene ve kasko tarihlerini unuttuğu için gecikme cezası ödediğini, torpidodaki evrakların dağınık ve yıpranmış olduğunu ekledi.
* **Kritik İhtiyaç:** Arıza lambasını ve hasarı analiz edip sürüş tavsiyesi veren, kaza tutanağını adım adım doldurtan, ruhsat ve poliçe sürelerini hatırlatan akıllı bir web danışmanı.

---

### Görüşme 3: Mehmet Akova (Şirket Sahibi / Araç Yönetimi)
* **Görüşme Tarihi & Şekli:** 10 Ekim 2026 – Yüz Yüze (Şirket Ofisi / İzmit)
* **Görüşme Notları:**
  - *"Şirketimizde sahada çalışan 8 adet aracımız var. Bakımları, kilometreleri, TÜVTÜRK muayeneleri ve kaskoları bir Excel dosyasında tutmaya çalışıyorum. Ancak personeller kilometre bilgisini düzenli vermediği için periyodik bakımlar gecikiyor, motor masrafları katlanıyor."*
  - Araçlardan biri şehir dışında veya İzmit çevre yollarında arıza yaptığında şoförün en yakın ve açık özel servisi bulmakta zorlandığını, rastgele yerlere gidip yüksek maliyetlerle karşılaştıklarını belirtti.
  - Ruhsat, sigorta ve bakım faturalarının fiziksel klasörlerde kaybolduğunu vurguladı.
* **Kritik İhtiyaç:** Şirket araçlarının kilometre ve bakım durumunu tek merkezden takip eden, yaklaşan muayene/bakımlarda uyaran ve arıza anında harita üzerinden en yakın yetkili/özel servisi listeleyen merkezi bir sistem.

---

## 3. İşin Bugün Nasıl Yapıldığı (Mevcut Durum Analizi)

İncelemeler ve yapılan 3 görüşme sonucunda, sürecin bugün tamamen **manuel, parçalı ve aksamalara açık** yürütüldüğü görülmüştür:

1. **WhatsApp Üzerinden Düzensiz İletişim:** Araç sahipleri hasar veya arıza fotoğraflarını ustalara WhatsApp'tan göndermekte; fotoğrafların net olmaması, mesajların yoğunlukta kaybolması iletişimi aksatmaktadır.
2. **Fiziksel Defterler ve Manuel Excel Tabloları:** Servis ustaları (Mevlüt Bey gibi) müşteri kayıtlarını fiziksel ajandalarda; şirket sahipleri (Mehmet Bey gibi) araç listelerini manuel güncellenmesi gereken Excel dosyalarında takip etmektedir.
3. **Torpidoda Yıpranan Kağıt Evraklar:** Ruhsat, trafik sigortası, kasko poliçesi ve kaza tespit tutanağı torpidoda fiziksel olarak durmakta; acil ihtiyaç anında bulunamamakta veya süre bitimleri unutulmaktadır.
4. **Motor İçi Karton Yağ Kartları:** Periyodik bakım takibi motor kaputuna asılan, sıcaktan ve yağdan silinen küçük karton kartlara emanet edilmektedir.
5. **Rastgele ve Filtresiz Servis Arama:** Yolda arıza yaşandığında sürücüler panikle genel arama motorlarından servis aramaya çalışmakta, uzmanlık alanına veya araç markasına uygun açık servisi hızlıca tespit edememektedir.

---

## 4. Çözümün En Önemli 3 Özelliği

*Akıllı Servis Danışmanı*, basit bir tanıtım sitesi veya sıradan bir form/liste uygulaması olmayıp, oto servis süreçlerini uçtan uca dijitalleştiren şu **3 temel özelliğe** odaklanır:

1. **Yapay Zekâ (Google Gemini AI) ile Görsel Hasar ve Arıza Lambası Teşhisi:**  
   Kullanıcının yüklediği fotoğraftan hasarlı araç parçasını tespit eder ve hasar şiddetini sınıflandırır. Gösterge panelindeki arıza lambalarını tanıyarak sürücüye *"Güvenle yola devam edilebilir mi, çekici mi çağrılmalı?"* şeklinde anlık aksiyon tavsiyesi üretir.

2. **Merkezi Dijital Garaj, OCR Belge Tarama ve Kilometre/Tarih Bazlı Bakım Takvimi:**  
   Ruhsat ve poliçe görsellerini OCR ile okuyarak araç bilgilerini sisteme kaydeder. Girilen kilometre ve süreye göre yaklaşan periyodik bakım, muayene ve sigorta tarihlerini hesaplayarak kullanıcıyı ve filo yöneticisini otomatik uyarır (defter ve yağ kartı karmaşasını sonlandırır).

3. **İnteraktif Kaza Tespit Tutanağı Rehberi ve Konum Bazlı Servis Haritası (OSM):**  
   Maddi hasarlı kaza anında sürücüye yasal mevzuata uygun adım adım tutanak doldurma rehberliği sunar. Aracın anlık konumuna göre çevredeki en yakın özel ve yetkili servisleri OpenStreetMap altyapısıyla haritada listeler ve rota oluşturur.

---

## 5. Seçilen Teknik Özellikler ve Mimari

* **Frontend:** **React + Vite**  
  - Hızlı, modüler tek sayfa uygulama (SPA) mimarisi.  
  - Mobil, tablet ve masaüstü uyumlu responsive tasarım.  
  - Leaflet kütüphanesi ile OpenStreetMap (OSM) harita ve rota entegrasyonu.
* **Backend:** **Python + FastAPI**  
  - Asenkron çalışan, yüksek performanslı RESTful API servisi.  
  - Swagger/OpenAPI otomatik dokümantasyonu üzerinden uçtan uca test edilebilirlik.
* **Veritabanı & ORM:** **SqlLite & SQLAlchemy**  
  - Araç, kullanıcı, bakım geçmişi ve servis kayıtları için ilişkisel veri modeli ve veri tutarlılığı.
* **Kimlik Doğrulama & Depolama:** **Firebase**  
  - **Firebase Authentication:** Güvenli kullanıcı kaydı, oturum açma ve token doğrulama.  
  - **Firebase Storage:** Kaza fotoğrafları, belge taramaları ve araç resimleri için bulut depolama.
* **Yapay Zekâ Servisi:** **Google Gemini Multimodal API**  
  - Görsel analiz, hasar sınıflandırma ve arıza lambası tanıma modülleri.
* **Güvenlik & Repozituar Kuralları:**  
  - API anahtarları, Firebase kimlikleri ve veritabanı şifreleri depoya eklenmez; `.env` dosyasında tutulur, depoda yalnızca `.env.example` paylaşılır.  
  - Geliştirmeler GitHub Pull Request (PR) akışıyla yürütülür ve kapatılan görevler standart açıklamayla (`Closes #issue`) ana dala birleştirilir.
