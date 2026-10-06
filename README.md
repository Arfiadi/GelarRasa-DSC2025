# 🏆 Data Science Competition GELAR RASA 2025

<div align="center">
  <h3>Analisis Studi Kasus: FMCG Personal Care</h3>
  <p><b>Tim: Sepertiga Malam</b></p>
  <p>Ziyad Yusuf Fauzan | Arfi Adi Nugroho | M Ikhwan Fito</p>
</div>

---

## 📌 Latar Belakang & Objektif
Proyek ini merupakan hasil analisis mendalam terhadap industri **FMCG Personal Care** untuk kompetisi **Data Science GELAR RASA 2025**. Kompetisi dibagi dalam tiga studi kasus utama yang bertujuan untuk membantu perusahaan memahami performa produk, meramalkan tren penjualan di masa depan, serta memitigasi risiko kanibalisasi antar produk.

## 🚀 Metodologi & Hasil Analisis

### 1️⃣ Study Case 1: Innovation Radar
**Tujuan:** Mengidentifikasi peluang inovasi dan merancang strategi pemasaran serta penetapan harga berdasarkan segmentasi perilaku produk.
* **Feature Engineering & Selection:** Menggunakan pendekatan **LightGBM Regressor** untuk feature selection (Gain & Permutation Importance, SHAP values). Model sangat akurat (R² = 0.9993) dalam memprediksi revenue produk.
* **Segmentasi:** Dilakukan **K-Means Clustering** (K=4) untuk mengelompokkan produk ke dalam 4 segmen:
  1. **High Revenue Big Performers (Cluster 0):** Penopang utama revenue, ukuran besar, diskon rendah.
  2. **Stabil/Standar (Cluster 1):** Harga relatif tinggi, diskon kecil, tanpa pola fluktuasi ekstrem.
  3. **Harga Rendah/Promo-Driven (Cluster 2):** Harga variatif dengan diskon tinggi (rentan pada profit margin).
  4. **Low Revenue & Small Size (Cluster 3):** Produk berukuran kecil dengan pendapatan paling rendah.
* **Visualisasi:** **Radar Chart** (Spider Plot) digunakan untuk menginterpretasikan dan membandingkan karakteristik setiap cluster.

### 2️⃣ Study Case 2: Trend Forecasting
**Tujuan:** Meramalkan tren penjualan masa depan secara konsisten di tingkat total (agregat) maupun level produk individual.
* **Pendekatan:** Menggunakan metodologi inovatif **Hierarchical Time Series (HTS)**.
* **Top-Level (Total Revenue):** Pemodelan agregat bulanan menggunakan **Prophet** (dengan fitur regressor diskon & proxy GDP) menghasilkan MAPE sangat rendah (< 2%).
* **Bottom-Level (Product Revenue):** Pemodelan per produk menggunakan **ARIMAX** (memanfaatkan harga, marketing spend, sentimen, dsb.) dengan MAPE 2-5%.
* **Reconciliation:** Menggunakan metode **MinT (Minimum Trace) Reconciliation** untuk menyelaraskan prediksi top-level dan bottom-level agar terhindar dari bias hierarki dan konsisten secara matematis.

### 3️⃣ Study Case 3: Product Cannibalization Analysis
**Tujuan:** Mengukur dampak peluncuran produk baru (PC015) terhadap produk lama yang sudah mapan (PC001).
* **Pendekatan:** **Interrupted Time Series Analysis (ITSA)** / **Synthetic Control Method (SCM)**.
* **Temuan:** Peluncuran PC015 tidak menyebabkan drop instan, namun menyebabkan erosi tren penjualan PC001 (slope negatif), masuk ke dalam **Risiko Moderate**.
* **Strategi Mitigasi (CLIMAX):** Mengalokasikan 20% budget untuk strategi **DEFEND & DIFFERENTIATE** (Misal: meluncurkan loyalty program dan varian eco-friendly/premium pada PC001).

---

## 🛠 Tech Stack
* **Bahasa:** Python 🐍
* **Data Manipulation & Analysis:** Pandas, NumPy
* **Machine Learning:** LightGBM, Scikit-Learn
* **Time Series & Forecasting:** Prophet, Statsmodels (ARIMAX, ETS, SES)
* **Visualisasi:** Matplotlib, Seaborn, SHAP

---

## 📂 Struktur Repositori
```text
├── DSC2025-Team Sepertiga Malam.ipynb  # Notebook utama berisi seluruh pipeline analisis
├── README.md                           # Ringkasan proyek (File ini)
└── data/                               # (Opsional) Dataset (sales, products, marketing, reviews)
```

## ⚙️ Cara Menjalankan
1. Pastikan Anda memiliki environment Python (>= 3.8).
2. Install dependensi yang dibutuhkan, misalnya melalui:
   ```bash
   pip install pandas numpy scikit-learn lightgbm prophet statsmodels shap matplotlib seaborn gdown
   ```
3. Buka file Jupyter Notebook `DSC2025-Team Sepertiga Malam.ipynb` menggunakan Jupyter Lab atau Google Colab.
4. Jalankan sel (cells) secara berurutan. Data akan diunduh secara otomatis dari Google Drive pada awal setup.

---
*Dibuat dengan ❤️ oleh Tim Sepertiga Malam untuk Data Science Competition GELAR RASA 2025.*
