# chess.com-review-sentiment-analysis
End-to-end Sentiment Analysis pipeline for Chess.com app reviews. Features Google Play scraping, advanced NLP preprocessing (slang/negation handling), and model comparison (SVM, XGBoost, Deep Learning/TensorFlow).

# ♟️ Analisis Sentimen Ulasan Aplikasi Chess.com

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.0%2B-orange)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Latest-yellow)
![Status](https://img.shields.io/badge/Status-Completed-success)

Proyek ini bertujuan untuk menganalisis sentimen pengguna aplikasi **Chess.com** berdasarkan ulasan dari Google Play Store. Sistem ini menerapkan teknik **Natural Language Processing (NLP)** mulai dari *scraping* data, *preprocessing* tingkat lanjut, pelabelan otomatis berbasis Lexicon, hingga klasifikasi menggunakan algoritma Machine Learning dan Deep Learning.

## 📋 Daftar Isi
- [Latar Belakang](#-latar-belakang)
- [Alur Kerja (Pipeline)](#-alur-kerja-pipeline)
- [Teknologi yang Digunakan](#-teknologi-yang-digunakan)
- [Fitur Utama](#-fitur-utama)
- [Hasil & Evaluasi](#-hasil--evaluasi)
- [Cara Menjalankan](#-cara-menjalankan)

## 🔍 Latar Belakang
Ulasan pengguna adalah sumber data berharga untuk memahami kepuasan pengguna. Proyek ini mengotomatiskan proses membaca ribuan ulasan untuk mengklasifikasikannya menjadi **Positif**, **Negatif**, atau **Netral**, sehingga pengembang dapat dengan cepat mengidentifikasi bug (sentimen negatif) atau fitur yang disukai (sentimen positif).

## 🚀 Alur Kerja (Pipeline)

1.  **Data Scraping**: Mengambil data ulasan nyata dari Google Play Store menggunakan `google-play-scraper`.
2.  **Preprocessing**:
    * *Cleaning*: Menghapus karakter khusus, angka, dan link.
    * *Slang Word Correction*: Mengubah kata gaul (ex: "bgt", "u", "thx") menjadi kata baku (Bahasa Indonesia & Inggris).
    * *Stopword Removal*: Menghapus kata umum yang tidak bermakna.
    * *Lemmatization*: Mengubah kata menjadi bentuk dasar.
    * *Negation Handling*: Menangani kata ingkar (ex: "not good" diperlakukan sebagai kata negatif, bukan terpisah).
3.  **Labeling**: Pelabelan otomatis menggunakan **Bing Liu Lexicon** (score based).
4.  **Feature Extraction**:
    * TF-IDF
    * Word2Vec
    * Bag of Words (BoW) & N-Gram
5.  **Modeling**: Melatih berbagai model untuk mencari akurasi terbaik.

## 🛠 Teknologi yang Digunakan

* **Bahasa**: Python
* **Data Processing**: Pandas, NumPy
* **NLP Libs**: NLTK, Gensim (Word2Vec)
* **Machine Learning**: Scikit-Learn (SVM, Logistic Regression, Random Forest), XGBoost
* **Deep Learning**: TensorFlow/Keras (Sequential Model, Dense Layer, Dropout)
* **Visualisasi**: Matplotlib, Seaborn, WordCloud

## ✨ Fitur Utama

### 1. Advanced Preprocessing
Kode mencakup kamus *slang words* yang sangat lengkap (baik Indo maupun English) dan algoritma penanganan negasi (*negation handling*) untuk meningkatkan akurasi konteks kalimat.

### 2. Komparasi Model Luas
Proyek ini membandingkan kinerja berbagai algoritma:
* **Machine Learning**: Random Forest, Logistic Regression, Linear SVC, XGBoost.
* **Deep Learning**: Neural Network (Sequential) dengan *Early Stopping* untuk mencegah *overfitting*.

### 3. Visualisasi Data
Menampilkan distribusi sentimen (Bar/Pie Chart) dan *Word Cloud* untuk melihat kata-kata yang paling sering muncul dalam ulasan.

## 📊 Hasil & Evaluasi

Sistem menggunakan metrik **Akurasi** untuk evaluasi. Pada tahap Deep Learning, diterapkan mekanisme `EarlyStopAtDualAccuracy` di mana pelatihan berhenti otomatis jika akurasi *Training* dan *Validation* sama-sama mencapai ambang batas tertentu (misal: >93%).

| Metode | Fitur | Hasil (Estimasi) |
| :--- | :--- | :--- |
| **Deep Learning (DNN)** | TF-IDF | **High Accuracy (>90%)** |
| **Linear SVC** | TF-IDF | Medium-High |
| **Random Forest** | Word2Vec | Medium |

*> Catatan: Hasil detail dapat dilihat pada output notebook.*

## 💻 Cara Menjalankan

1.  **Clone Repository**
    ```bash
    git clone [https://github.com/damar-iswara/chess.com-review-sentiment-analysis.git](https://github.com/damar-iswara/chess.com-review-sentiment-analysis.git)
    cd chess.com-review-sentiment-analysis
    ```

2.  **Install Dependencies**
    Disarankan menggunakan Google Colab, namun jika di lokal:
    ```bash
    pip install -r requirements.txt
    ```

3.  **Konfigurasi Target App**
    Pastikan pada bagian scraping kode, ID aplikasi diarahkan ke Chess.com:
    ```python
    scrapreview, _ = reviews(
        'com.chess', # ID Paket Chess.com
        lang='en',
        country='us',
        ...
    )
    ```

4.  **Jalankan Notebook**
    Buka file `main.ipynb` di Jupyter Notebook atau Google Colab dan jalankan setiap sel secara berurutan.

## 👤 Author
**Wahyu Damar Iswara**
* [GitHub Profile](https://github.com/damar-iswara)
* [LinkedIn](https://www.linkedin.com/in/wahyu-damar-iswara/)

---
*Jika proyek ini bermanfaat, jangan lupa berikan ⭐ pada repositori ini!*
