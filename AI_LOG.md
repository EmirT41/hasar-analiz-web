# 🤖 Yapay Zekâ Kullanım ve Karar Günlüğü (AI_LOG.md)

**Proje Adı:** Akıllı Servis Danışmanı  
**Ders:** Web Programlama Dönem Projesi  
**Kurum:** Kocaeli Sağlık ve Teknoloji Üniversitesi  
**Geliştiriciler:** Mustafa Emirhan Turhan & Mehmet Eren Yavuz  
**Kullanılan Yapay Zekâ Araçları:** Google Gemini API, Claude / GPT LLM Danışmanlığı, ChatGPT

---

## 1. Giriş ve Amaç
Bu günlük; sistemin yapay zekâ destekli hasar tespit, arıza lambası analizi ve maliyet hesaplama modüllerinin geliştirilmesi sürecinde karşılaşılan problemlerin, yapay zekâya danışılan mimari alternatiflerin ve alınan teknik kararların kaydını içerir.

---

## 2. Karşılaşılan Problemler ve Semptomlar
* **Görsel Halüsinasyon (False Positive Hasar Tespiti):**
  * Gemini API'ye doğrudan serbest metin istemi (prompt) ile hasar analizi yaptırıldığında; araçta sadece çamurluk bölgesinde fiziksel hasar bulunmasına rağmen, fotoğraftaki ışık kırılması veya gölgeler nedeniyle model tavan bölgesini de "boyalı/hasarlı" olarak raporlamıştır.
* **Segment Bağımsız Fiyatlandırma Sapması:**
  * Hasar onarım maliyeti doğrudan LLM'e sorulduğunda; model pazar dinamiklerini, döviz endeksini ve işçilik tarifelerini hesaba katamayarak Lamborghini ile Tofaş gibi uç segmentteki araçlara benzer/tutarsız maliyetler tahmin etmiştir.

---

## 3. Yapay Zekâ ile Değerlendirilen Mimari Alternatifler

### Alternatif A: Google Colab Üzerinde Multimodal LLM Eğitimi (Fine-Tuning)
* **Değerlendirme:**
  * Görsel dil modellerinin (VLM / Multimodal LLM) Colab ücretsiz GPU katmanında (Nvidia T4) eğitilmesi donanım/VRAM (OOM) ve oturum süre sınırları nedeniyle verimsiz bulundu.
  * Modelin parçaları karıştırmaması için binlerce profesyonelce etiketlenmiş hasar verisi gerekeceği, aksi halde aşırı öğrenme (overfitting) oluşacağı analiz edildi.
* **Sonuç:** Reddedildi (Zaman, donanım ve doğruluk verimsizliği).

### Alternatif B: Açık Kaynak Veri Setleri ile Bilgisayarlı Görü (Computer Vision / YOLO)
* **Değerlendirme:**
  * Akademik ve açık kaynaklı araç hasar veri setleri incelendi (*CarDD - Car Damage Dataset*, *Roboflow Universe Araç Hasar Setleri*).
  * Hasar türü ve parça tespiti için YOLOv8/YOLOv11 gibi nesne tespit modellerinin Colab T4 üzerinde 30–45 dakika gibi kısa sürede eğitilebileceği; piksel koordinatı (bounding box) üreterek görsel halüsinasyonu sıfırlayacağı ve milisaniyeler (20–250 ms) düzeyinde yanıt vereceği belirlendi.
* **Sonuç:** Hasar tespiti için birincil görsel model adayı olarak benimsendi.

### Alternatif C: Yapılandırılmış Çıktı (Structured JSON) + Backend Kural Motoru
* **Değerlendirme:**
  * Gemini API'den maliyet veya serbest metin yerine yalnızca fiziksel parça ve hasar şiddetini içeren katı JSON şeması (`response_schema`, Pydantic) talep edilmesi kararlaştırıldı (`temperature: 0.1`).
  * Fiyat tahmininin LLM'e bırakılmayıp; FastAPI backend'inde araç segment çarpanları (Tofaş: 1.0x, Lamborghini: 20x) ve PostgreSQL parça matrisi ile deterministik olarak hesaplanması tasarlandı.
* **Sonuç:** Kabul edildi (Uygulanabilirlik hızı ve finansal tutarlılık).

---

## 4. Alınan Nihai Mimari Karar (Hibrit Yaklaşım)

Yapay zekâ istişaresi sonucunda sistemin sorumlulukları şu şekilde ayrıştırılmıştır:
[Kullanıcı Görseli & Araç Bilgisi]
│
├──► [Hasar Görsel Analizi]: YOLOv8 / Bounding Box (Doğrudan piksel tespiti)
│    veya Gemini JSON Mode (Düşük temperature + Katı Pydantic Şeması)
│
├──► [OCR & Gösterge Lambası]: Gemini Multimodal API (Ruhsat & Arıza lambası okuma)
│
└──► [Maliyet Hesaplama]: FastAPI Kural Motoru + PostgreSQL Çarpan Matrisi

## 5. Projeye Teknik Katkısı
1. **Halüsinasyon Engellendi:** Parça tespiti ve maliyet ayrıştırılarak tavan boyası gibi yanlış tespitlerin önüne geçildi.
2. **Deterministik Fiyatlandırma:** Araç segmentine ve güncel parça katsayılarına göre tutarlı servis ve ekspertiz aralıkları elde edildi.
3. **Maliyet & Kaynak Optimizasyonu:** Gereksiz LLM eğitim maliyetlerinden kaçınılarak projenin 12 haftalık zaman planına sadık kalındı.
