# Predictive Analytics: Graduate Admission Prediction

## Ringkasan Proyek
Proyek ini merupakan implementasi *end-to-end machine learning pipeline* untuk memprediksi **Chance of Admit** (peluang diterima) calon mahasiswa program pascasarjana berdasarkan profil akademik dan non-akademik. Fokus utama proyek adalah membangun model regresi yang akurat, stabil, dan mudah diinterpretasikan, sekaligus menunjukkan pemahaman teknikal yang kuat terhadap proses data science secara menyeluruh.
Proyek ini dikembangkan sebagai **portfolio untuk keperluan magang**, dengan penekanan pada:

* Alur kerja data science yang sistematis
* Pemilihan model berbasis analisis data
* Evaluasi dan validasi model yang tepat
* Interpretasi hasil yang logis dan aplikatif

---

## Problem Statement
Proses seleksi mahasiswa pascasarjana sering kali bersifat kompleks dan kompetitif. Calon mahasiswa ingin mengetahui peluang mereka diterima berdasarkan skor tes dan rekam akademik, sementara institusi pendidikan membutuhkan pendekatan objektif untuk mengevaluasi kandidat.
Masalah yang ingin diselesaikan:

* Bagaimana memprediksi peluang diterima mahasiswa (Chance of Admit) secara kuantitatif?
* Fitur apa saja yang paling berpengaruh terhadap keputusan penerimaan?
* Model regresi apa yang paling sesuai untuk permasalahan ini?

---

## Tujuan Proyek
1. Membangun model machine learning berbasis regresi untuk memprediksi Chance of Admit.
2. Melakukan eksplorasi data mendalam untuk memahami pola dan hubungan antar fitur.
3. Membandingkan beberapa algoritma regresi menggunakan metrik evaluasi yang relevan.
4. Menentukan model terbaik berdasarkan performa dan stabilitas.
5. Menghasilkan insight yang dapat digunakan secara praktis oleh calon mahasiswa maupun institusi.

---

## Dataset
* **Nama Dataset**: Graduate Admissions
* **Sumber**: Kaggle – Mohan S Acharya et al. (IEEE, 2019)
* **Jumlah Data**: 500 baris
* **Jumlah Fitur**: 7 fitur input + 1 target

### Fitur yang Digunakan
| Fitur             | Deskripsi                         |
| ----------------- | --------------------------------- |
| GRE Score         | Skor Graduate Record Examination  |
| TOEFL Score       | Skor kemampuan bahasa Inggris     |
| University Rating | Peringkat universitas asal (1–5)  |
| SOP               | Kekuatan Statement of Purpose     |
| LOR               | Kekuatan Letter of Recommendation |
| CGPA              | IPK (skala 10)                    |
| Research          | Pengalaman riset (0/1)            |

**Target**: Chance of Admit (nilai kontinu 0–1)

---

## Alur Kerja Proyek
### 1. Exploratory Data Analysis (EDA)
Tahap EDA dilakukan untuk memahami karakteristik data dan memastikan kualitas dataset.

Aktivitas utama:

* Pemeriksaan struktur data, tipe data, dan statistik deskriptif
* Pengecekan missing value dan duplikasi (tidak ditemukan)
* Visualisasi distribusi fitur numerik
* Analisis korelasi menggunakan heatmap
* Deteksi outlier menggunakan boxplot

Insight utama dari EDA:

* CGPA, GRE Score, dan TOEFL Score memiliki korelasi tertinggi dengan Chance of Admit
* Kolom Serial No. tidak relevan untuk pemodelan
* Distribusi data relatif bersih dan siap untuk modeling

---

### 2. Data Preprocessing
Tahapan ini bertujuan menyiapkan data agar optimal untuk proses pelatihan model.

Langkah teknikal:

* Menghapus kolom tidak relevan (Serial No.)
* Standarisasi fitur numerik menggunakan `StandardScaler`
* Pemisahan fitur (X) dan target (y)
* Split data train-test dengan rasio 80:20

Alasan standarisasi:

* Menghindari bias model terhadap fitur dengan skala besar
* Meningkatkan performa dan stabilitas model

---

### 3. Modeling
Beberapa algoritma regresi diuji untuk membandingkan performa dan karakteristik model.

Model yang digunakan:

1. **Linear Regression**

   * Baseline model
   * Mudah diinterpretasikan
   * Cocok untuk hubungan linier

2. **Random Forest Regressor**

   * Model ensemble berbasis decision tree
   * Mampu menangani hubungan non-linear
   * Robust terhadap outlier

3. **Gradient Boosting Regressor**

   * Model boosting untuk meningkatkan akurasi secara iteratif
   * Cocok untuk hubungan kompleks

---

### 4. Evaluasi Model
Evaluasi dilakukan menggunakan beberapa metrik regresi:

* Mean Squared Error (MSE)
* Root Mean Squared Error (RMSE)
* Mean Absolute Error (MAE)
* R-squared (R² Score)

Hasil utama:

* **Linear Regression** memberikan performa terbaik

  * R² Score: ~0.82
  * Error paling rendah dibanding model lain

Interpretasi:

* Hubungan antara fitur dan target cenderung linier
* Model sederhana lebih efektif dibanding model kompleks pada dataset ini

---

### 5. Cross-Validation
Untuk memastikan model tidak overfitting dan stabil, dilakukan 5-Fold Cross-Validation.

Hasil:

* Linear Regression memiliki R² mean tertinggi dan standar deviasi terendah
* Menunjukkan performa yang konsisten di berbagai subset data

---

### 6. Hyperparameter Tuning
Hyperparameter tuning dilakukan pada Random Forest menggunakan `GridSearchCV`.

Parameter yang dituning:

* `n_estimators`
* `max_depth`
* `min_samples_split`

Hasil:

* Performa Random Forest meningkat setelah tuning
* Namun masih belum melampaui Linear Regression

---

## Model Final
**Linear Regression** dipilih sebagai model akhir karena:

* Akurasi tertinggi
* Stabil pada cross-validation
* Mudah dijelaskan dan diinterpretasikan
* Efisien secara komputasi

Model ini cocok untuk dijadikan baseline sistem prediksi peluang diterima mahasiswa.

---

## Tech Stack
* Python
* Pandas, NumPy
* Matplotlib, Seaborn
* Scikit-learn

---

## Insight Bisnis dan Akademik
* CGPA merupakan faktor paling dominan dalam penerimaan
* Skor tes standar (GRE, TOEFL) masih sangat berpengaruh
* Pengalaman riset meningkatkan peluang diterima, namun tidak sepenting performa akademik

---

## Potensi Pengembangan
* Menambahkan fitur non-akademik tambahan
* Mencoba model advanced (XGBoost, LightGBM, Neural Network)
* Feature engineering dan feature selection lanjutan
* Deployment model sebagai web application atau API
* Pipeline otomatis dari preprocessing hingga inference

---

## Kesimpulan
Proyek ini menunjukkan implementasi lengkap predictive analytics menggunakan supervised learning. Dengan pendekatan yang sistematis dan evaluasi yang matang, model yang dihasilkan mampu memprediksi peluang diterima mahasiswa dengan akurasi tinggi. Proyek ini merepresentasikan kemampuan dalam data preprocessing, modeling, evaluasi, dan interpretasi yang relevan untuk peran magang di bidang data science dan machine learning.

---

## Referensi
* Acharya, M. S., et al. (2019). A Comparison of Regression Models for Prediction of Graduate Admissions.
* Scikit-learn Documentation
* Kaggle Graduate Admissions Dataset
