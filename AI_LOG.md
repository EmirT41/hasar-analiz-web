# 🤖 Yapay Zekâ Kullanım ve Karar Günlüğü (AI_LOG.md)

**Proje Adı:** Akıllı Servis Danışmanı  
**Ders:** Web Programlama Dönem Projesi  
**Kurum:** Kocaeli Sağlık ve Teknoloji Üniversitesi  
**Geliştiriciler:** Mustafa Emirhan Turhan & Mehmet Eren Yavuz  
**Kullanılan Yapay Zekâ Araçları:** Google Gemini API, Claude / GPT LLM Danışmanlığı, ChatGPT

### 1. YOLO + Gemini hibrit mimari
- **Tarih:**: 16.10.2026
- **Ne istedim:** Eğittiğim iki YOLOv11 modelini (parça segmentasyonu, hasar tespiti) backend'e bağlayan; hasar kutusunu
  parça poligonuyla kesiştirip hangi parçada olduğunu bulan bir servis, `/api/ai/damage-report` uç noktası ve React tarafında
  interaktif SVG hasar şeması.
- **Ne aldım:** `services/damage_analyzer.py` (Shapely kesişim oranı ≥ 0.15, çakışan kutuları birleştirme, numaralı kutular),
  `routers/ai_router.py`, `components/CarDamageDiagram.jsx`, `pages/DamageReportPage.jsx`, birim testleri.
- **Neyi değiştirdim:** Model dosyalarını `backend/models/parts` ve `backend/models/damage` klasörlerine koydum; yeni sayfanın
  mevcut "Hasar Analizi" sayfasının yanına eklenmesini istedim. <!-- varsa ekleyin -->
- **Neden:** Gemini tek başına hasarın hangi parçada olduğunu zaman zaman karıştırıyordu (ör. sağ kapı yerine tavan).

### 2. Hibrit doğrulama, kaza şiddeti, PDF rapor, Docker
- **Tarih:**: 17.10.2026
- **Ne istedim:** YOLO'nun eşleyemediği kutuları Gemini'nin görünen yön kuralıyla doldurması, kaza şiddeti sınıflandırması,
  PDF ekspertiz raporu, bellek optimizasyonu, Dockerfile ve canlıya alma ayarları, akademik README.
- **Ne aldım:** `services/hibrit_dogrulama.py` (izinli parça kodları, ağırlıklı baskın taraf kuralı, şiddet puanı normalizasyonu),
  `services/gemini_service.py` (şemalı JSON, model yedekleme), `utils/ekspertizRaporu.js`, `Dockerfile`, `vercel.json`, `render.yaml`.
- **Neyi değiştirdim:** `backend/.env` içinde kapatılan `gemini-2.5-flash` modelini `gemini-3.8-flash` ile değiştirdim. <!-- -->
- **Neden:** Gemini'nin tek başına uydurduğu parçaları sunucu tarafında kurallarla elemek; raporu servise götürülebilir hâle getirmek.

### 3. Gereksinim analizi (SRS) dokümanı
- **Tarih:**: 26.10.2026
- **Ne istedim:** Ders şablonuna (IEEE 830) uygun gereksinim analizi ve diyagramlar; ayrıca API kotası için önlemler ve projedeki hatalı/eksik kısımların listesi.
- **Ne aldım:** Fonksiyonel/fonksiyonel olmayan gereksinimler, kullanım senaryoları, aktivite / sıra / veri akışı / durum /
  kullanım durumu / sınıf / ER / mimari diyagramları ve izlenebilirlik matrisi.
- **Neyi değiştirdim:** 
- **Neden:**

### 4. Tek hibrit Hasar Analizi, SEO ve yalnızca PostgreSQL
- **Tarih:** 24.10.2026
- **Ne istedim:** Menüde tek bir Hasar Analizi olması ve hibrit (YOLO + Gemini) çalışması; sitenin SEO uyumlu hâle
  getirilmesi; risk yoksa veritabanının yalnızca PostgreSQL olması.
- **Ne aldım:**
  - Eski "Hasar Analizi (yalnızca Gemini)" ve "YOLO Hasar Raporu" sayfaları tek sayfada birleşti: 1–4 fotoğraf,
    marka/model ve arıza ışıkları bağlamı, parça bazında gerekli işlemler, çok fotoğraflı PDF ve analiz geçmişi.
  - YOLO'nun tanımadığı çamurluklar için Gemini'nin yazabileceği 4 parça kodu ve şemada karşılıkları (Leon fotoğrafında
    hasarın "parçaya eşlenemedi" kalmasının nedeni buydu).
  - SEO: meta/Open Graph/Twitter kartı, JSON-LD, favicon ve simgeler, manifest, robots.txt ve sitemap.xml üretimi,
    herkese açık tanıtım bölümü, sayfa başlıkları ve kişisel sayfalarda noindex, tembel yükleme.
  - `database.py` yalnızca PostgreSQL; bağlantı kopunca yeniden deneme; eski SQLite verisi için taşıma betiği.
  - **Neyi değiştirdim:**: SqLite tarafını tamamen devre dışı bıraktım. PostegreSql tarafını yazdıedım. Neon.tech adresinde postegreSql gerekliliklerini kurdum.
  - - **Neden:**: Projeyi canlıya alınca sqLite tarafı sıkıntılı olabiliyormuş. SEO isteğini ise hoca tanımladı.
