# THYAO Hisse Senedi Analizi — Veri Bilimi Dönem Projesi

## Proje Ekibi

- **Ad Soyad:** Ahmet Melih Çakalgil
- **Öğrenci Numarası:** 1306230079
- **Çalışma şekli:** Bireysel

## Proje Özeti

Bu proje, Türk Hava Yolları (THYAO) hisse senedinin geçmiş fiyat ve hacim verileri
üzerinde veri bilimi iş akışını (veri toplama, temizleme, keşifsel veri analizi,
görselleştirme ve temel modelleme) uygulamaktadır.

## Araştırma Soruları

1. THYAO hissesinin son yıllardaki günlük getiri dağılımı nasıldır ve volatilite
   zaman içinde (özellikle önemli ekonomik/sektörel olaylar etrafında) nasıl
   değişmiştir?
2. İşlem hacmi ile fiyat volatilitesi arasında bir ilişki var mıdır? Hareketli
   ortalama kesişimleri (golden cross / death cross) anlamlı sinyaller üretiyor mu?
3. Teknik göstergeler (RSI, hareketli ortalamalar, hacim değişimi, geçmiş getiriler)
   kullanılarak ertesi günün yönü (artış/azalış) sınıflandırılabilir mi?

## Kullanılan Veri Kaynağı

- **Kaynak:** Yahoo Finance (`yfinance` Python kütüphanesi aracılığıyla)
- **Sembol:** THYAO.IS (Türk Hava Yolları, Borsa İstanbul)
- **Lisans/Kullanım koşulları:** Yahoo Finance verileri kişisel/akademik kullanım
  için sağlanmaktadır; ticari kullanım için Yahoo'nun kendi koşulları geçerlidir.
  Bu proje yalnızca akademik amaçlıdır.
- **Veri aralığı:** 2021-06-27 — 2026-06-27 (son 5 yıl, günlük veri)

## Proje Yapısı

```
thyao-veri-bilimi-projesi/
├── data/                   → ham ve temizlenmiş veri dosyaları (CSV)
├── notebooks/
│   └── thyao_analiz.ipynb  → ana çalışma dosyası (veri yükleme → modelleme)
├── report/
│   └── rapor.pdf           → kısa rapor (3-5 sayfa)
├── docs/
│   └── PROMPT_LOG.md       → geliştirme sürecinde kullanılan prompt günlüğü
├── requirements.txt        → gerekli Python kütüphaneleri
└── README.md               → bu dosya
```

## Çalıştırma Talimatları

1. Depoyu klonlayın:
   ```bash
   git clone https://github.com/ahmetmelihcakalgil-oss/thyao-veri-bilimi-projesi
   cd thyao-veri-bilimi-projesi
   ```

2. Sanal ortam oluşturun (önerilir):
   ```bash
   python -m venv venv
   source venv/bin/activate   # Windows: venv\Scripts\activate
   ```

3. Gerekli kütüphaneleri kurun:
   ```bash
   pip install -r requirements.txt
   ```

4. Jupyter Notebook'u açın:
   ```bash
   jupyter notebook notebooks/thyao_analiz.ipynb
   ```

5. Tüm hücreleri sırasıyla çalıştırın (Cell → Run All).

## Kullanılan Kütüphaneler

- `yfinance` — Yahoo Finance'ten hisse verisi çekmek için
- `pandas`, `numpy` — veri işleme
- `matplotlib`, `seaborn` — görselleştirme
- `scikit-learn` — modelleme (sınıflandırma)

(Tam liste `requirements.txt` dosyasında)

## Yöntem Özeti

Çalışma şu adımları izler:
1. Veri toplama (yfinance API)
2. Veri temizleme (eksik veri, aykırı değer, tip dönüşümü)
3. Teknik gösterge / feature üretimi (RSI, hareketli ortalama, hacim değişimi)
4. Keşifsel veri analizi (en az 4 görselleştirme türü)
5. Üç araştırma sorusunun analizle yanıtlanması
6. Basit bir sınıflandırma modeli (ertesi gün artış/azalış tahmini)
7. Sonuçların THYAO/havacılık sektörü bağlamında yorumlanması

Detaylı yöntem ve bulgular için `report/rapor.pdf` dosyasına bakınız.

## Sınırlamalar

- Tek hisseye odaklanıldığı için bulgular diğer BIST hisselerine genellenemez.
- Kısa vadeli yön tahmini, finansal piyasaların etkin piyasa hipotezi nedeniyle
  doğası gereği zordur; model performansı buna göre yorumlanmalıdır.
- Modelleme kapsamlı hiperparametre optimizasyonu içermemektedir (proje
  gereksinimleri doğrultusunda).

## Geliştirme Süreci Hakkında Not

Bu proje "vibe coding" yöntemiyle, bir AI kodlama asistanı (Claude) birincil
geliştirme ortağı olarak kullanılarak hazırlanmıştır. Kullanılan promptların
kronolojik kaydı `docs/PROMPT_LOG.md` dosyasında yer almaktadır.