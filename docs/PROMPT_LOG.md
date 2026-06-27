# Prompt Günlüğü

**Öğrenci:** Ahmet Melih Çakalgil — 1306230079

---

## 1. Tema ve Kapsam Belirleme

**Tarih:** 27.06.2026 | **Aşama:** Planlama

**Prompt:**
> "Final sınavı yerine dönem projesi olarak... vibe coding kullanabilirsiniz...
> nasıl yaparız"

**Değerlendirme:** Finans & Ekonomi (BIST) temasını seçtim, çünkü daha önce
yfinance ile bir BIST analiz aracı geliştirmiştim.

---

## 2. Modelleme Yönteminin Belirlenmesi

**Tarih:** 27.06.2026 | **Aşama:** Planlama

**Prompt:**
> "Finans & Ekonomi (BIST hisseleri)" / "Bireysel" / "Tek bir hisse, uzun
> zaman serisi" / "Henüz kararsızım, önerini istiyorum"

**Değerlendirme:** Regresyonun random walk problemi nedeniyle yanıltıcı
olabileceğini anladım, bu yüzden sınıflandırma (yön tahmini) yöntemini
seçtim.

---

## 3. Araştırma Sorularının ve Hisse Seçiminin Netleştirilmesi

**Tarih:** 27.06.2026 | **Aşama:** Planlama

**Prompt:**
> "Bu 3 araştırma sorusu ve sınıflandırma yaklaşımı uygun mu?" → "Evet, bu
> şekilde devam edelim" / "THYAO (Türk Hava Yolları)"

**Değerlendirme:** Üç araştırma sorusunu onayladım. THYAO'yu seçtim çünkü
likit bir hisse ve kur/yakıt maliyeti gibi etkenlere duyarlılığı yorum
yapmamı kolaylaştırıyor.

---

## 4. Proje İskeletinin Kurulması

**Tarih:** 27.06.2026 | **Aşama:** Proje kurulumu

**Prompt:**
> "Önce GitHub repo iskeletini ve klasör yapısını kuralım"

**Değerlendirme:** `data/`, `notebooks/`, `report/`, `docs/` klasörleriyle
README ve requirements.txt taslaklarını oluşturdum.

---

## 5. Notebook'un Baştan Sona Oluşturulması

**Tarih:** 27.06.2026 | **Aşama:** Veri toplama → modelleme

**Prompt:**
> "5 yıl geri git fazla soru sorma en optimal şekilde yap hangi dosyaya hangi
> kodu yapıştıracağımı söyle"

**Değerlendirme:** Notebook'u çalıştırmadan önce her hücreyi okudum;
özellikle train/test ayrımının neden kronolojik yapıldığını (veri sızıntısını
önlemek için) anladım.

---

## 6. RSI Hesaplamasındaki Sonsuz (inf) Değer Hatasının Çözümü

**Tarih:** 27.06.2026 | **Aşama:** Hata ayıklama

**Prompt:**
> "model random forest kısmında bu yazdı ValueError: Input X contains
> infinity or a value too large for dtype('float32')."

**Değerlendirme:** Hatanın RSI hesaplamasında sıfıra bölmeden (`ortalama_kayip
= 0`) kaynaklandığını, `inf` değerinin `dropna()` ile yakalanamadığını
anladım. `df.replace([np.inf, -np.inf], np.nan)` ekleyerek çözdüm.

---

## 7. EDA Çıktılarının Yorumlanması

**Tarih:** 27.06.2026 | **Aşama:** Keşifsel veri analizi

**Prompt:**
> [8 grafik paylaşıldı] "istediklerini attım doldur"

**Değerlendirme:** Hacim-volatilite grafiğindeki ölçek bozukluğunu fark
ettim; nedeninin `Hacim_Degisim` hesabındaki benzer bir sıfıra bölme sorunu
olduğunu anlayıp bunu rapora bir sınırlama olarak ekledim.

---

## 8. Araştırma Sorusu 1 ve 2 Bulgularının Yorumlanması

**Tarih:** 27.06.2026 | **Aşama:** Analiz / yorumlama

**Prompt:**
> [Yıllık volatilite serisi ve golden/death cross sonuçları paylaşıldı]

**Değerlendirme:** 2021/2023'teki yüksek volatiliteyi THYAO'nun hızlı fiyat
artışıyla ilişkilendirdim. Golden/death cross getirilerinin birbirine yakın
çıkmasını, sinyalin net bir ayırt edici güç taşımadığı şeklinde yorumladım.

---

## 9. Model Performansının Değerlendirilmesi

**Tarih:** 27.06.2026 | **Aşama:** Modelleme sonucu yorumlama

**Prompt:**
> [Karışıklık matrisi, feature önemi ve sınıflandırma raporu paylaşıldı]

**Değerlendirme:** Model accuracy'sinin (%51) baseline'a eşit olduğunu, yani
modelin gerçekte bir şey öğrenmediğini fark ettim. Bunu başarısızlık değil,
THYAO'nun kısa vadede piyasa etkinliğine işaret eden savunulabilir bir sonuç
olarak yorumladım.

---

## Genel Değerlendirme

AI çıktılarını doğrudan kabul etmedim, her adımı sorguladım:
- Regresyon yerine sınıflandırma seçimini bağımsız olarak değerlendirip
  onayladım.
- Kronolojik train/test ayrımının veri sızıntısını neden önlediğini anladım.
- RSI ve hacim değişimi hesaplamalarındaki `inf` hatalarını kök nedenini
  anlayarak çözdüm.
- Model performansını ham accuracy değil, baseline karşılaştırmasıyla
  yorumladım.