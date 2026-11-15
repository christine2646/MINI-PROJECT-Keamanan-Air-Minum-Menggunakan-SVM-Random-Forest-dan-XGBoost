# MINI-PROJECT-Keamanan-Air-Minum-Menggunakan-SVM-Random-Forest-dan-XGBoost

# 💧 Klasifikasi Keamanan Air Minum Menggunakan Machine Learning

## 📌 Deskripsi Proyek

Proyek ini merupakan mini project yang bertujuan untuk melakukan klasifikasi keamanan air minum berdasarkan kandungan zat kimia dan mikroorganisme menggunakan algoritma Machine Learning.

Penelitian ini membandingkan tiga algoritma klasifikasi, yaitu **Support Vector Machine (SVM), Random Forest, dan XGBoost**, untuk mengetahui algoritma yang memiliki performa terbaik dalam mengklasifikasikan air ke dalam dua kategori, yaitu aman dan tidak aman untuk dikonsumsi.

Dataset yang digunakan adalah **Water Quality Dataset** yang diperoleh dari Kaggle. Dataset ini memuat berbagai parameter kualitas air yang digunakan sebagai variabel prediktor dalam proses klasifikasi.

## 🎯 Tujuan Penelitian

1. Menerapkan algoritma SVM, Random Forest, dan XGBoost untuk mengklasifikasikan keamanan air minum.
2. Mengevaluasi performa masing-masing algoritma menggunakan berbagai metrik evaluasi klasifikasi.
3. Membandingkan hasil klasifikasi untuk menentukan model dengan performa terbaik.
4. Mengidentifikasi variabel yang paling berpengaruh terhadap klasifikasi keamanan air.

## 📊 Dataset

Dataset yang digunakan adalah **Water Quality Dataset** yang diperoleh dari Kaggle.

- Jumlah data awal: 7.999 sampel.
- Jumlah data setelah preprocessing: 7.996 sampel.
- Jumlah variabel prediktor: 20 variabel.
- Variabel target: `is_safe`.
- Jenis permasalahan: Binary Classification.

### Variabel Target

| Nilai | Keterangan |
|---|---|
| 0 | Air tidak aman |
| 1 | Air aman |

### Variabel Prediktor

Dataset memiliki 20 parameter kualitas air, yaitu:

`Aluminium`, `Ammonia`, `Arsenic`, `Barium`, `Cadmium`, `Chloramine`, `Chromium`, `Copper`, `Fluoride`, `Bacteria`, `Viruses`, `Lead`, `Nitrates`, `Nitrites`, `Mercury`, `Perchlorate`, `Radium`, `Selenium`, `Silver`, dan `Uranium`.

## ⚙️ Metodologi

Penelitian dilakukan melalui beberapa tahapan sebagai berikut:

### 1. Data Preprocessing

Tahapan preprocessing meliputi:
- Pemeriksaan struktur dan tipe data.
- Penghapusan 3 baris yang mengandung nilai tidak valid (`#NUM!`).
- Konversi tipe data menjadi numerik.
- Penanganan 10 nilai negatif pada variabel ammonia dengan mengubahnya menjadi 0.
- Pemeriksaan missing values dan data duplikat.
- Deteksi outlier menggunakan metode Interquartile Range (IQR).
- Analisis korelasi antarvariabel.

Nilai outlier dipertahankan karena dianggap masih berpotensi mengandung informasi penting terkait kualitas air.

### 2. Data Splitting

Dataset dibagi menggunakan metode Stratified Sampling dengan proporsi:

- 80% data training (6.396 sampel).
- 20% data testing (1.600 sampel).
- Random state: 42.

### 3. Pemodelan Machine Learning

Tiga algoritma digunakan dalam penelitian ini:

**a. Support Vector Machine (SVM)**

Menggunakan kernel Radial Basis Function (RBF) untuk mempelajari hubungan nonlinier antarvariabel. Standardisasi fitur dilakukan menggunakan StandardScaler.

**b. Random Forest**

Menggunakan pendekatan ensemble learning dengan menggabungkan beberapa decision tree untuk menghasilkan prediksi klasifikasi.

**c. XGBoost**

Menggunakan pendekatan gradient boosting yang membangun decision tree secara bertahap untuk memperbaiki kesalahan prediksi model sebelumnya.

### 4. Hyperparameter Tuning

Optimasi hyperparameter dilakukan menggunakan GridSearchCV dengan Stratified 5-Fold Cross-Validation.

Pemilihan parameter terbaik didasarkan pada nilai F1-score untuk kelas positif, yaitu air aman (`is_safe = 1`).

### 5. Evaluasi Model

Kinerja model dievaluasi menggunakan metrik:

- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC
- PR-AUC

Evaluasi lebih menekankan F1-score karena dataset memiliki distribusi kelas yang tidak seimbang.

## 📈 Hasil dan Perbandingan Model

Berdasarkan hasil pengujian pada data testing, diperoleh perbandingan performa ketiga algoritma sebagai berikut:

| Model | Accuracy | Precision | Recall | F1-Score |
|---|---:|---:|---:|---:|
| SVM | 92,88% | 67,53% | 71,98% | 69,68% |
| Random Forest | 96,00% | 92,75% | 70,33% | 80,00% |
| XGBoost | **96,75%** | 87,36% | **83,52%** | **85,39%** |

### Hasil Evaluasi Tambahan

| Model | ROC-AUC | PR-AUC |
|---|---:|---:|
| SVM | 0,9581 | 0,7791 |
| Random Forest | 0,9766 | 0,9120 |
| XGBoost | **0,9838** | **0,9384** |

### 🏆 Model Terbaik: XGBoost

Berdasarkan hasil evaluasi, XGBoost memperoleh performa terbaik dengan nilai:

- Accuracy: 96,75%
- Precision: 87,36%
- Recall: 83,52%
- F1-Score: 85,39%
- ROC-AUC: 0,9838
- PR-AUC: 0,9384

XGBoost memberikan keseimbangan terbaik antara precision dan recall dibandingkan SVM dan Random Forest.

Sementara itu, Random Forest menghasilkan precision tertinggi sebesar 92,75%, yang menunjukkan ketepatan prediksi air aman paling tinggi di antara ketiga model.

## 🔍 Feature Importance

Berdasarkan analisis feature importance, beberapa variabel yang memiliki pengaruh penting dalam proses klasifikasi adalah:

1. Aluminium
2. Cadmium
3. Arsenic
4. Perchlorate
5. Viruses
6. Silver
7. Chloramine

Aluminium dan cadmium merupakan dua variabel yang secara konsisten menempati posisi teratas dalam analisis kepentingan fitur pada ketiga model.

## 📝 Kesimpulan

Berdasarkan hasil penelitian, algoritma XGBoost menunjukkan performa terbaik dalam mengklasifikasikan keamanan air minum dibandingkan SVM dan Random Forest. Model XGBoost memperoleh F1-score sebesar 85,39% dan PR-AUC sebesar 0,9384.

Hasil penelitian menunjukkan bahwa pendekatan Machine Learning dapat dimanfaatkan sebagai alat bantu dalam proses klasifikasi kualitas air berdasarkan parameter kimia dan mikrobiologi.

Namun, model ini masih memiliki kemungkinan kesalahan klasifikasi. Oleh karena itu, hasil prediksi sebaiknya digunakan sebagai alat penyaringan awal dan tidak menggantikan pengujian laboratorium untuk memastikan keamanan air minum.

## 🛠️ Teknologi dan Tools

Teknologi dan library yang digunakan dalam penelitian ini meliputi:

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- Jupyter Notebook
