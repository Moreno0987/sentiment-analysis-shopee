# Analisis Sentimen Ulasan Produk Shopee (Bahasa Indonesia)

## Deskripsi

Proyek ini bertujuan untuk melakukan analisis sentimen terhadap ulasan produk Shopee berbahasa Indonesia menggunakan pendekatan Natural Language Processing (NLP).
Klasifikasi sentimen dibagi menjadi tiga kategori: **positif, negatif, dan netral**.

Penelitian ini berfokus pada perbandingan dua metode representasi teks, yaitu **Bag of Words (BoW)** dan **TF-IDF**, dengan menggunakan algoritma klasifikasi **Multinomial Naive Bayes**.

---

##  Dataset

Dataset yang digunakan berasal dari Kaggle:

* Ulasan produk Shopee (Bahasa Indonesia)
* Kolom utama:

  * `content` → teks ulasan
  * `score` → rating (1–5)

Label sentimen dibuat berdasarkan rating:

* 1–2 → negatif
* 3 → netral
* 4–5 → positif

---

## Metodologi

### 1. Text Preprocessing

* Cleaning (lowercase, hapus simbol & URL)
* Tokenization (NLTK)
* Stopword Removal (Sastrawi)
* Stemming (Sastrawi)

### 2. Representasi Teks

* Bag of Words (BoW)
* TF-IDF

Parameter:

* `max_features = 5000`
* `min_df = 5`
* `max_df = 0.8`

### 3. Modeling

* Multinomial Naive Bayes

### 4. Evaluasi

* Accuracy
* Precision
* Recall
* F1-score
* Confusion Matrix

---

## Hasil Eksperimen

| Metode | Accuracy | Catatan                       |
| ------ | -------- | ----------------------------- |
| BoW    | ~75%     | Semua kelas terdeteksi        |
| TF-IDF | ~77%     | Gagal mendeteksi kelas netral |

---

##  Insight Penting

* Dataset memiliki **ketidakseimbangan kelas (imbalance)**
* **TF-IDF meningkatkan accuracy**, tetapi:

  * gagal mengenali kelas netral (recall = 0)
* **BoW lebih stabil** karena mampu mendeteksi semua kelas
* Kelas netral sulit dikenali karena:

  * tidak memiliki kata kunci spesifik
  * sering menggunakan kata umum

---

## Cara Menjalankan

### 1. Clone Repository

```bash
git clone https://github.com/username/sentiment-analysis-shopee-nlp.git
cd sentiment-analysis-shopee-nlp
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Jalankan Project

Buka file notebook:

```bash
notebook/analisis_sentimen.ipynb
```

Atau jalankan di Google Colab.

---

## Visualisasi

Project ini menggunakan beberapa visualisasi:

* Distribusi label sentimen
* WordCloud
* Confusion Matrix

---

## Kesimpulan

* TF-IDF unggul dalam accuracy, tetapi tidak stabil untuk semua kelas
* Bag of Words lebih seimbang dalam klasifikasi
* Pemilihan metode tidak boleh hanya berdasarkan accuracy, tetapi juga distribusi performa antar kelas

---

##  Pengembangan Selanjutnya

* Menggunakan teknik balancing data (SMOTE / oversampling)
* Menambahkan n-gram
* Menggunakan Word Embeddings (Word2Vec, FastText)
* Menggunakan model berbasis Transformer (BERT)

---

## Referensi

* Jurafsky & Martin (2009)
* Manning et al. (2008)
* Scikit-learn Documentation
* Kaggle Dataset Shopee Review
