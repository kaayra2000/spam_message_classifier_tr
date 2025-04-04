# Türkçe Spam Mesaj Tespit Modeli

Bu proje, Türkçe SMS mesajlarını "spam" veya "normal" olarak sınıflandırmak için bir doğal dil işleme (NLP) modeli geliştirmektedir. BERT tabanlı derin öğrenme modeli kullanarak yüksek doğrulukta spam tespiti yapar.

## Proje Hakkında

Bu projede, Türkçe SMS mesajlarından oluşan bir veri kümesi kullanılarak, mesajların spam olup olmadığını tespit eden bir sınıflandırma modeli geliştirilmiştir. Proje, transfer öğrenme yaklaşımı ile önceden eğitilmiş Türkçe BERT modelini kullanarak yüksek doğrulukta sonuçlar elde etmeyi amaçlamaktadır.

## Özellikler

- Türkçe SMS mesajlarında spam tespiti
- BERT tabanlı derin öğrenme modeli (dbmdz/bert-base-turkish-128k-cased)
- Yüksek doğruluk, F1 skoru, kesinlik ve duyarlılık metrikleri
- Kolay kullanımlı tahmin arayüzü
- Detaylı eğitim metrikleri ve görselleştirmeler

## Gereksinimler

Projeyi çalıştırmak için aşağıdaki kütüphanelere ihtiyaç vardır:

```python
transformers>=4.30.0
torch>=2.0.0
pandas>=1.5.0
numpy>=1.24.0
kagglehub
datasets
scikit-learn
matplotlib
seaborn
```

## Kurulum
1. Projeyi klonlayın:
```bash
git clone https://github.com/kaayra2000/spam_message_classifier_tr.git
cd spam_message_classifier_tr
```	
2. (İsteğe bağlı) Google Colab'da çalıştırmak için, notebook'ları ilgili ortama yükleyin ve çalıştırın.

## Veri Kümesi
Bu projede Kaggle platformundan "Turkish SMS Collection" (onurkarasoy/turkish-sms-collection) veri kümesi kullanılmıştır. Veri kümesi, etiketlenmiş Türkçe SMS mesajlarını içermektedir:
* Spam mesajlar (Group=1)
* Normal mesajlar (Group=2)

Veri kümesi, eğitim (%80), doğrulama (%10) ve sınama (%10) olarak ayrılmıştır.
## Eğitim

Model eğitimi için `train.py` dosyası kullanılır. Bu dosya:
1. Kaggle'dan veri kümesini indirir ve işler
2. Veri kümesini eğitim, doğrulama ve sınama kümelerine böler
3. BERT tabanlı modelin eğitimini gerçekleştirir
4. Modeli eğitir ve başarımını değerlendirir
5. Eğitim sürecini ve sonuçları görselleştirir
6. Eğitilen modeli kaydeder

## Tahmin
Modeli kullanmak için `test.py` dosyası kullanılır:

1. Eğitilmiş model ve tokenizer yüklenir
2. Kullanıcıdan bir SMS mesajı alınır
3. Mesajın spam olup olmadığı tahmin edilir
4. Sonuç ekrana yazdırılır

## Model Mimarisi
* Temel model: `dbmdz/bert-base-turkish-128k-cased`
* Çıkış katmanı: İki sınıflı sınıflandırma (spam/normal)
* Eğitim parametreleri:
    * Optimizasyon algoritması: AdamW
    * Batch boyutu: 128
    * Öğrenme oranı: 2e-5
    * Döngü sayısı: 1

## Notlar
* Bu model, yalnızca Türkçe SMS mesajları için eğitilmiştir
* Farklı biçimdeki metinler için ek eğitim gerekebilir