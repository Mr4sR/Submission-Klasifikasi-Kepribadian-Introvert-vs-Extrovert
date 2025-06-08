# Laporan Proyek Machine Learning - Ahmad Sofiyurrohman

## Domain Proyek

Pada era digital ini, pemahaman tentang kepribadian individu sangat penting, baik dalam dunia pendidikan, perekrutan kerja, maupun pengembangan produk. Klasifikasi kepribadian berdasarkan perilaku sosial dapat membantu organisasi dalam mengelompokkan individu untuk tujuan yang lebih tepat sasaran. Dengan menggunakan data survei terkait perilaku sosial, proyek ini berupaya mengklasifikasikan tipe kepribadian (introvert atau ekstrovert) dengan pendekatan machine learning.

**Mengapa penting:**

* Pengklasifikasian kepribadian bisa meningkatkan efisiensi dalam rekrutmen, pendidikan personalisasi, hingga strategi pemasaran berbasis psikologi.
* Proyek ini menyederhanakan asesmen kepribadian berbasis perilaku aktual, bukan hanya dari kuisioner panjang yang bersifat subjektif.

**Referensi:**

* Goldberg, L. R. (1990). An alternative "description of personality": the Big-Five factor structure. *Journal of Personality and Social Psychology*.
* John, O. P., & Srivastava, S. (1999). The Big Five trait taxonomy: History, measurement, and theoretical perspectives. *Handbook of personality: Theory and research*.

## Business Understanding

### Problem Statements

* Bagaimana cara mengklasifikasikan tipe kepribadian seseorang berdasarkan data perilaku sosial?
* Model machine learning mana yang paling efektif untuk memprediksi tipe kepribadian?

### Goals

* Membangun model klasifikasi kepribadian dengan akurasi tinggi berdasarkan data perilaku.
* Membandingkan performa dua algoritma machine learning: Logistic Regression dan Random Forest.

### Solution Statements

* Menggunakan dua model klasifikasi: Logistic Regression dan Random Forest Classifier.
* Mengukur performa dengan metrik akurasi, precision, recall, dan f1-score.
* Memilih model terbaik berdasarkan hasil evaluasi dan feature importance.

## Data Understanding

Dataset yang digunakan diambil dari Kaggle, berisi data survei perilaku sosial. Link: [Extrovert vs. Introvert Behavior Data](https://www.kaggle.com/datasets/rakeshkapilavai/extrovert-vs-introvert-behavior-data)

### Jumlah Baris dan Kolom

Dataset awal terdiri dari **2.900 baris** dan **8 kolom**.

### Kondisi Data Awal

Sebelum dilakukan data preparation, berikut jumlah missing values pada setiap kolom:

- Time_spent_Alone: 63
- Stage_fear: 73
- Social_event_attendance: 62
- Going_outside: 66
- Drained_after_socializing: 52
- Friends_circle_size: 77
- Post_frequency: 65
- Personality: 0

### Fitur dalam dataset:

* `Time_spent_Alone`: Waktu yang dihabiskan sendirian (numerik).
* `Social_event_attendance`: Frekuensi menghadiri acara sosial (numerik).
* `Going_outside`: Frekuensi keluar rumah untuk aktivitas di luar (numerik).
* `Post_frequency`: Frekuensi posting di media sosial (numerik).
* `Stage_fear`: Ketakutan berbicara di depan umum (kategorikal: ya/tidak).
* `Drained_after_socializing`: Merasa lelah setelah bersosialisasi (kategorikal: ya/tidak).
* `Friends_circle_size`: Ukuran lingkaran pertemanan (numerik).
* `Personality`: Target klasifikasi (0 = introvert, 1 = ekstrovert).

## Data Preparation

Tahapan data preparation yang dilakukan:

1. **Cek dan Tangani Missing Values**
   - Cek jumlah missing values pada setiap kolom.
   - Imputasi kolom numerik (`Time_spent_Alone`, `Social_event_attendance`, `Going_outside`, `Friends_circle_size`, `Post_frequency`) dengan median.
   - Imputasi kolom kategorikal (`Stage_fear`, `Drained_after_socializing`, `Personality`) dengan modus.
2. **Encoding**
   - Label Encoding pada kolom kategorikal (`Stage_fear`, `Drained_after_socializing`, `Personality`).
3. **Pisahkan Fitur dan Target**
   - Fitur disimpan di variabel features, target di variabel target.
4. **Imputasi Ulang dengan SimpleImputer (mean)**
   - Setelah pemisahan fitur, dilakukan imputasi ulang pada fitur numerik menggunakan `SimpleImputer(strategy='mean')` untuk memastikan tidak ada missing value.
5. **Scaling**
   - Fitur numerik diskalakan menggunakan `StandardScaler`.
6. **Split Data**
   - Dataset dibagi 80:20 untuk pelatihan dan pengujian.

## Modeling

Dua model digunakan:

### Logistic Regression

* Model linier sederhana untuk klasifikasi.
* Cepat dan efisien pada dataset kecil/menengah.
* **Parameter utama:**
    - random_state=42
    - C=1.0 (default)
    - solver='lbfgs' (default)
    - max_iter=100 (default)

### Random Forest Classifier

* Algoritma ensemble berbasis pohon keputusan.
* Memiliki kemampuan menangani non-linearitas dan fitur penting.
* **Parameter utama:**
    - random_state=42
    - n_estimators=100 (default)
    - max_depth=None (default)
    - min_samples_split=2 (default)
    - min_samples_leaf=1 (default)

## Evaluation

### Metrik Evaluasi

* **Akurasi**: proporsi prediksi benar terhadap seluruh prediksi.
* **Precision**: seberapa akurat model saat memprediksi kelas positif.
* **Recall**: seberapa baik model menemukan semua data kelas positif.
* **F1-Score**: harmonic mean dari precision dan recall.

### Hasil Evaluasi

#### Logistic Regression

* Akurasi: 92%
* F1-score: 0.92

#### Random Forest

* Akurasi: 92%
* F1-score: 0.92

### Feature Importance (Random Forest)

* Fitur paling berpengaruh:

    * `Stage_fear`
    * `Time_spent_alone`
    * `Drained_after_socializing`

### Model Terbaik

Kedua model memiliki performa yang sama secara metrik. Namun, **Random Forest** dipilih karena memiliki keunggulan dalam interpretasi fitur dan lebih tangguh terhadap outlier serta non-linearitas data.

---

*Catatan: Proyek ini menunjukkan bahwa data perilaku sederhana dapat digunakan secara efektif untuk mengklasifikasikan tipe kepribadian. Pengembangan selanjutnya dapat mencakup tuning model, ekspansi fitur, atau deployment sebagai aplikasi berbasis web.*
