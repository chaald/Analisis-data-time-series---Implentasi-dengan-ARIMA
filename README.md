# Analisis-data-time-series---Implentasi-dengan-ARIMA
Analisis data time series pada harga penutupan harian saham Apple Inc untuk pengambilan keputusan investasi menggunakan ARIMA

## Deskripsi Data  
Dataset berasal dari Yahoo Finance dan berisi beberapa kolom data harga saham harian, yaitu:  
- **Date**: Tanggal pencatatan harga saham.  
- **Open**: Harga pembukaan saham pada tanggal tersebut.  
- **High**: Harga tertinggi saham diperdagangkan.  
- **Low**: Harga terendah saham diperdagangkan.  
- **Close**: Harga penutupan selama sesi perdagangan reguler.  
- **Adjusted Close**: Harga penutupan yang disesuaikan dengan memperhitungkan dividen dan stock split.  
- **Volume**: Jumlah saham yang diperdagangkan.  

Kolom yang digunakan sebagai fokus utama adalah **Adjusted Close** karena memberikan gambaran nilai saham yang lebih akurat.

## Periode Data  
Dataset mencakup harga saham Apple Inc. dari tahun 1980 sampai 2021, dengan fokus analisis dan forecasting pada tahun 1985.

## Pola Data  
Analisis tren harga saham Apple (1990-2020) menunjukkan:  
- 1990-2000: Harga relatif datar.  
- 2000-2010: Pertumbuhan lambat.  
- 2010-2020: Kenaikan signifikan.

## Transformasi Box-Cox  
Variansi data tidak stabil akibat fluktuasi harga, sehingga dilakukan transformasi Box-Cox untuk menstabilkan variansi.

## Proses Pemodelan  

### 1. Uji Stasioneritas (Augmented Dickey-Fuller)  
Data asli tidak stasioner (p-value > 0.05), sehingga dilakukan proses differencing.

### 2. Differencing  
Differencing orde pertama membuat data stasioner (p-value < 0.05).

### 3. Analisis ACF dan PACF  
Plot ACF dan PACF digunakan untuk menentukan parameter ARIMA dengan lag hingga 30.

### 4. Pemilihan Model Terbaik (AIC)  
Model ARIMA(4,1,4) terpilih berdasarkan nilai AIC terendah.

### 5. Estimasi Parameter (Maximum Likelihood)  
Parameter diestimasi dengan metode Maximum Likelihood, dengan sebagian besar parameter signifikan (p-value < 0.05).

### 6. Diagnostik Residual  
- **Ljung-Box Test**: Residual bebas autokorelasi (p-value > 0.05).  
- **Shapiro-Wilk Test**: Residual berdistribusi normal (p-value > 0.05).

### 7. Peramalan (Forecasting)  
Model digunakan untuk memprediksi 12 langkah ke depan dengan hasil yang mengikuti tren data aktual.

### 8. Evaluasi Model (RMSE)  
RMSE digunakan untuk mengukur akurasi prediksi, dengan nilai lebih kecil berarti model lebih baik.
