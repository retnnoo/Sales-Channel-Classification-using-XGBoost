# 🛒 Smart Sales Channel Prediction: Multi-Class Classification with XGBoost

![Python](https://img.shields.io/badge/Python-3.9+-blue?style=for-the-badge&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-F7931E?style=for-the-badge&logo=scikitlearn)
![XGBoost](https://img.shields.io/badge/XGBoost-1.7+-orange?style=for-the-badge)
![Machine Learning](https://img.shields.io/badge/Model-Classification-green?style=for-the-badge)
![Dataset](https://img.shields.io/badge/Dataset-Kaggle-blue?style=for-the-badge&logo=kaggle)

---

# 🎯 Business Overview

Dalam ekosistem ritel modern, memahami apakah pelanggan lebih memilih belanja **Online**, **Offline**, atau **Hybrid** merupakan kunci untuk meningkatkan efisiensi strategi pemasaran.

Proyek ini membangun model **klasifikasi multi-kelas** untuk memprediksi preferensi saluran belanja pelanggan menggunakan data perilaku digital dan karakteristik demografi pelanggan.

Dengan model ini, perusahaan ritel dapat:

- Mengoptimalkan strategi pemasaran berbasis preferensi pelanggan
- Mengalokasikan promosi secara lebih efektif antara online dan offline
- Memahami perilaku pelanggan dalam ekosistem **omnichannel retail**

---

# 📊 Dataset

**Sumber dataset:**  
https://www.kaggle.com/datasets/shree0910/online-vs-in-store-shopping-behaviour-dataset

Target variabel dalam proyek ini adalah:

**shopping_preference**

- Store
- Online
- Hybrid

Dataset terdiri dari **11.789 pelanggan** dengan berbagai fitur yang menggambarkan perilaku belanja, aktivitas digital, serta preferensi interaksi dengan produk.

**Distribusi Label**

<p align="center">
  <img src="images/label_distribution.png" width="600">
</p>

Distribusi label menunjukkan bahwa kelas **Store** mendominasi dataset dibandingkan kelas **Online** dan **Hybrid**.  
Ketidakseimbangan distribusi ini menjadi salah satu tantangan dalam proses pemodelan karena model berpotensi lebih bias terhadap kelas mayoritas.

Oleh karena itu, pada tahap modeling digunakan strategi penanganan **class imbalance** untuk meningkatkan kemampuan model dalam mengenali kelas minoritas.

---

# 🤖 Model Machine Learning

Model yang digunakan dalam proyek ini adalah **XGBoost Classifier**, sebuah algoritma berbasis **Gradient Boosting** yang terkenal memiliki performa tinggi dalam tugas klasifikasi.

### Strategi Pemodelan

- **Algoritma utama:** XGBoost Classifier
- **Penanganan Imbalanced Data:** `compute_class_weight`
- **Hyperparameter Optimization:** `RandomizedSearchCV`
- **Metode evaluasi utama:** **F1-Score**

Pendekatan ini digunakan untuk memastikan model tidak hanya memiliki akurasi tinggi, tetapi juga mampu menangani distribusi kelas yang tidak seimbang.

---

# 📊 Model Evaluation

Performa model dievaluasi menggunakan **classification report** dan **confusion matrix**.

<p align="center">
  <img src="images/confusion_matrix.png" width="600">
</p>

## Akurasi Model

**96%**

## Classification Report

| Kelas | Precision | Recall | F1-score |
|------|------|------|------|
| Store | 0.99 | 0.98 | 0.99 |
| Online | 0.91 | 0.93 | 0.92 |
| Hybrid | 0.41 | 0.51 | 0.46 |

### Analisis Hasil Model

- Model memiliki performa yang **sangat baik dalam memprediksi kelas Store dan Online**.
- Performa pada kelas **Hybrid lebih rendah**, kemungkinan karena perilaku pelanggan yang merupakan kombinasi antara belanja online dan toko fisik.
- Nilai **Weighted F1-score sebesar 0.96** menunjukkan performa model yang sangat baik secara keseluruhan.


# 🧠 Analysis & Insights

Berdasarkan hasil pemodelan dan interpretasi fitur menggunakan **SHAP (SHapley Additive exPlanations)**, ditemukan beberapa insight penting:

### 1️⃣ Digital Maturity

Fitur `tech_savvy_score` dan `daily_internet_hours` merupakan prediktor paling kuat dalam menentukan preferensi belanja pelanggan.

Pelanggan dengan tingkat kemampuan teknologi rendah hampir tidak pernah diprediksi sebagai pelanggan **Online**.

---

### 2️⃣ Hybrid Behavior Pattern

Pelanggan kategori **Hybrid** sangat sensitif terhadap `shipping_cost_sensitivity`.

- Jika biaya pengiriman meningkat → pelanggan cenderung beralih ke **Offline**
- Jika terdapat diskon → pelanggan tetap memilih **Online**

Hal ini menunjukkan bahwa pelanggan Hybrid sangat responsif terhadap strategi promosi.

---

### 3️⃣ Income Influence

Fitur `monthly_income` menunjukkan bahwa pelanggan dengan pendapatan lebih tinggi memiliki kecenderungan lebih besar untuk menjadi **Hybrid shoppers**.

Hal ini mencerminkan gaya hidup yang fleksibel antara kenyamanan belanja online dan pengalaman berbelanja secara langsung.

---

### 4️⃣ Probabilistic Threshold

Distribusi probabilitas prediksi menunjukkan bahwa kelas **Hybrid** memiliki batas klasifikasi yang lebih tipis dibandingkan dua kelas lainnya.

Oleh karena itu, pelanggan Hybrid memerlukan strategi pemasaran yang lebih spesifik untuk dapat dikonversi menjadi pelanggan **Online-first**.

---
