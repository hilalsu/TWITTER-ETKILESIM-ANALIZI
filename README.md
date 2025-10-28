# Twitter Etkileşim Analizi
Bu proje, Twitter User Social Network veri seti üzerinde kapsamlı veri madenciliği ve sosyal ağ analizi gerçekleştirir. 40,000 kullanıcı verisi ile makine öğrenmesi modelleri, kümeleme analizi ve ağ görselleştirmeleri içerir.

## Veri Seti
- **Ad**: Twitter User Social Network
- **Boyut**: 40,000 kullanıcı (39,402 temiz kayıt)
- **Format**: CSV (`data2.csv`)
- **Özellikler**: Takipçi sayısı, takip edilen sayısı, etiketler, aktivite seviyesi

## Hızlı Başlangıç

### Google Colab ile Çalıştırma (Önerilen)
1. Yukarıdaki "Open In Colab" rozetine tıklayın
2. `data2.csv` dosyasını Colab'a yükleyin
3. Notebook'u çalıştırın

### Yerel Kurulum
```bash
# Depoyu klonlayın
git clone https://github.com/hilalsu/TWITTER-ETKILESIM-ANALIZI.git
cd TWITTER-ETKILESIM-ANALIZI

# Sanal ortam oluşturun
python -m venv .venv
source .venv/bin/activate  # Linux/Mac
# veya
.venv\Scripts\activate     # Windows

# Gerekli paketleri yükleyin
pip install -r requirements.txt

# Jupyter Notebook'u başlatın
jupyter notebook
```

## Kodda Neler Yapılıyor?

### 1. Veri Yükleme ve Ön İşleme
- **Ham Veri Yükleme**: CSV dosyasından 40,000 Twitter kullanıcı verisi okunur
- **Veri Temizleme**: 39,402 temiz kayıt elde edilir (gürültü temizliği ile)
- **Özellik Mühendisliği**: 
  - `tags_count`: Kullanıcının etiket sayısı
  - `followers_friends_ratio`: Takipçi/takip edilen oranı
  - `activity_level`: Aktivite seviyesi hesaplaması

### 2. Veri Standardizasyonu
- **RobustScaler**: Aykırı değerlere karşı dayanıklı ölçeklendirme
- **DBSCAN**: Gürültü temizliği için kümeleme algoritması
- **MinMaxScaler + PowerTransformer**: Regresyon için veri dönüşümü

### 3. Kümeleme Analizi
- **Elbow Yöntemi**: Optimal küme sayısı belirleme (K=5)
- **K-Means**: Kullanıcıları 5 farklı gruba ayırma
- **PCA + t-SNE**: 2D boyut indirgeme ve görselleştirme
- **Korelasyon Matrisi**: Özellikler arası ilişki analizi

### 4. Makine Öğrenmesi Modelleri
5 farklı regresyon modeli test edilir:
- **Linear Regression**: Temel doğrusal model
- **Ridge Regression**: L2 regularizasyon
- **Lasso Regression**: L1 regularizasyon  
- **Gradient Boosting**: Ensemble yöntemi
- **XGBoost**: Gelişmiş gradient boosting

### 5. Model Değerlendirme
- **Cross-Validation**: 5-fold çapraz doğrulama
- **Overfitting Kontrolü**: Train vs Test performans karşılaştırması
- **Metrikler**: R², MSE, MAE skorları
- **En İyi Model**: Gradient Boosting (R² = 0.999)

### 6. Görselleştirmeler
- **20+ Grafik**: Kümeleme, korelasyon, model performansı
- **3D Görselleştirme**: Çok boyutlu veri analizi
- **Residual Analizi**: Model hatalarının dağılımı
- **Gerçek vs Tahmin**: Model doğruluğu görselleştirmesi

### 7. Sosyal Ağ Analizi
- **NetworkX**: Ağ grafiği oluşturma
- **Louvain Algoritması**: Topluluk algılama
- **39,402 Topluluk**: Her kullanıcı ayrı topluluk olarak algılanır
- **Spring Layout**: Ağ görselleştirmesi

### 8. Performans Sonuçları
- **Veri Boyutu**: 40,000 → 39,402 (temizlenmiş)
- **En İyi Model**: Gradient Boosting
- **Test R²**: 0.999 (mükemmel uyum)
- **Test MSE**: 4,850 (düşük hata)
- **Test MAE**: 19.55 (ortalama mutlak hata)

## Proje Yapısı
```
TWITTER-ETKILESIM-ANALIZI/
├── README.md                    # Bu dosya
├── requirements.txt             # Python bağımlılıkları
├── .gitignore                   # Git ignore dosyası
├── data2.csv                    # Twitter sosyal ağ verisi
└── verimadenciliği.ipynb        # Ana analiz notebook'u
```

## Gereksinimler
- Python 3.9+
- Jupyter Notebook
- Gerekli paketler: `requirements.txt` dosyasında listelenmiştir

## Sonuçlar
- **En Yüksek Performans**: Gradient Boosting (R² = 0.999)
- **Kümeleme**: 5 farklı kullanıcı grubu
- **Ağ Analizi**: 39,402 topluluk tespit edildi
- **Görselleştirme**: 20+ analitik grafik
