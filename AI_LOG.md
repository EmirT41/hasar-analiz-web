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
- **Tarih:** 2026-10-17
- **Ne istedim:** YOLO'nun eşleyemediği kutuları Gemini'nin görünen yön kuralıyla doldurması, kaza şiddeti sınıflandırması,
  PDF ekspertiz raporu, bellek optimizasyonu, Dockerfile ve canlıya alma ayarları, akademik README.
- **Ne aldım:** `services/hibrit_dogrulama.py` (izinli parça kodları, ağırlıklı baskın taraf kuralı, şiddet puanı normalizasyonu),
  `services/gemini_service.py` (şemalı JSON, model yedekleme), `utils/ekspertizRaporu.js`, `Dockerfile`, `vercel.json`, `render.yaml`.
- **Neyi değiştirdim:** `backend/.env` içinde kapatılan `gemini-2.5-flash` modelini `gemini-3.8-flash` ile değiştirdim. <!-- -->
- **Neden:** Gemini'nin tek başına uydurduğu parçaları sunucu tarafında kurallarla elemek; raporu servise götürülebilir hâle getirmek.
