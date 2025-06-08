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

Dataset yang digunakan diambil dari Kaggle, berisi data survei perilaku sosial seperti durasi interaksi sosial, kenyamanan dalam keramaian, ukuran lingkaran pertemanan, dan lainnya. Link: [Extrovert vs. Introvert Behavior Data](https://www.kaggle.com/datasets/rakeshkapilavai/extrovert-vs-introvert-behavior-data)

### Fitur dalam dataset:

* `Time_spent_Alone`: waktu yang dihabiskan sendirian.
* `Social_event_attendance`: frekuensi menghadiri acara sosial.
* `Stage_fear`: ketakutan berbicara di depan umum (ya/tidak).
* `Drained_after_socializing`: merasa lelah setelah bersosialisasi (ya/tidak).
* `Friends_circle_size`: ukuran lingkaran pertemanan.
* `Personality`: target klasifikasi (0 = introvert, 1 = ekstrovert)

## Data Preparation

* **Imputasi**: missing values diisi dengan median (untuk numerik) dan modus (untuk kategorikal).
* **Encoding**: variabel kategorikal diencoding dengan `LabelEncoder`.
* **Scaling**: fitur numerik diskalakan menggunakan `StandardScaler`.
* **Split Data**: dataset dibagi 80:20 untuk pelatihan dan pengujian.

## Modeling

Dua model digunakan:

### Logistic Regression

* Model linier sederhana untuk klasifikasi.
* Cepat dan efisien pada dataset kecil/menengah.

### Random Forest Classifier

* Algoritma ensemble berbasis pohon keputusan.
* Memiliki kemampuan menangani non-linearitas dan fitur penting.

**Parameter**: digunakan default parameter dari `scikit-learn`, tanpa tuning.

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
