# pba2026-Kelompok-4
Repositori untuk tugas besar PBA

## Anggota Kelompok 4
| Nama | NIM | Username GitHub |
| --- | --- | --- |
| Muhammad Zaky Zaiddan | 122450119 | @Zakyy0101 |
| Berliana Enda Putri | 122450065 | @berlianaendaputri |
| Lisa Diani Amelia | 122450021 | @lisadiani29 |

---

Berikut adalah link hugging face untuk hasil pemodelan: https://huggingface.co/spaces/Zee292/sentiment-mbg

## Pernyataan Kontribusi
Kami berkomitmen untuk berkontribusi secara adil dalam pengerjaan Tugas Besar ini, yang akan tercermin melalui riwayat commit pada repositori ini.
# Classification of Public Opinion on the Free Nutritional Meal Program on YouTube Media Using the LSTM Method
# Klasifikasi Opini Masyarakat terhadap Program Makan Bergizi Gratis pada Media YouTube Menggunakan Metode LSTM


## Deskripsi Proyek
Proyek ini merupakan implementasi Natural Language Processing (NLP) untuk melakukan klasifikasi opini masyarakat terhadap Program Makan Bergizi Gratis (MBG) berdasarkan komentar pada platform YouTube.

Analisis dilakukan untuk mengelompokkan opini ke dalam tiga kategori sentimen, yaitu positif, negatif, dan netral.

---

## Deskripsi Dataset
Dataset yang digunakan berupa komentar YouTube yang membahas program Makan Bergizi Gratis (MBG). Data dikumpulkan dari dua channel YouTube yang relevan dengan topik tersebut.

Jumlah data yang diperoleh adalah:
- Channel 1: 3.342 komentar
- Channel 2: 4.391 komentar

Total keseluruhan data:
**7.733 komentar**

---

## Karakteristik Data
- Data berupa teks tidak terstruktur
- Mengandung bahasa informal
- Mengandung opini masyarakat yang beragam
- Berasal dari dua sumber berbeda 

---

## Sumber Dataset
Dataset dikumpulkan melalui proses scraping dari platform YouTube terkait kebijakan Makan Bergizi Gratis (MBG). 

- **Kaggle Dataset:** [Data Sentimen Makanan Bergizi Gratis di Indonesia](https://www.kaggle.com/datasets/muhammadzaiddan/data-sentimen-makanan-bergizi-gratis-di-indonesia)
- **Status:** Public Access
- **Jumlah Data:** 7.733 komentar (Gabungan dari Channel 1 dan 2)


---

## Jenis Tugas NLP
Tugas yang dilakukan dalam proyek ini adalah:

**Text Classification (Analisis Sentimen)**

Dimana komentar akan diklasifikasikan ke dalam:
- Positif
- Negatif

---

## Tujuan Penggunaan Dataset
1. Melatih model untuk mendeteksi sentimen publik terhadap program nasional MBG.
2. Membandingkan performa antara Machine Learning konvensional (via PyCaret) dan Deep Learning (LSTM).

---

## Gambaran Model yang Akan Digunakan
Model yang akan digunakan adalah:

**Long Short-Term Memory (LSTM)**

Model ini dipilih karena mampu menangkap hubungan antar kata dalam data teks berurutan sehingga cocok untuk analisis sentimen.

---

## Rencana Pipeline NLP
Tahapan yang akan dilakukan pada penelitian ini meliputi:

1. Pengumpulan data (scraping YouTube)
2. Preprocessing teks
3. Representasi teks (tokenizing & padding)
4. Pemodelan menggunakan LSTM
5. Evaluasi model

---

## Struktur Repository
```text
pba2026-Kelompok-4/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── data/
│   ├── raw/
│   │   ├── youtube_channel1.csv
│   │   ├── youtube_channel2.csv
│   │   └── combined_data.csv
│   │
│   ├── processed/
│   │   ├── cleaned_data.csv
│   │   ├── labeled_data.csv
│   │   └── final_dataset.csv
│
├── notebooks/
│   ├── 01_data_collection.ipynb
│   ├── 02_preprocessing.ipynb
│   ├── 03_exploratory_data_analysis.ipynb
│   ├── 04_modeling_pycaret.ipynb
│   ├── 05_modeling_lstm.ipynb
│   └── 06_evaluation.ipynb
│
├── src/
│   ├── __init__.py
│   │
│   ├── data/
│   │   ├── load_data.py
│   │   ├── preprocessing.py
│   │   └── labeling.py
│   │
│   ├── features/
│   │   ├── tokenization.py
│   │   └── padding.py
│   │
│   ├── models/
│   │   ├── lstm_model.py
│   │   ├── pycaret_model.py
│   │   └── train.py
│   │
│   ├── evaluation/
│   │   ├── metrics.py
│   │   └── evaluation.py
│   │
│   └── utils/
│       ├── config.py
│       └── helper.py
│
├── models/
│   ├── lstm_model.h5
│   ├── tokenizer.pkl
│   └── pycaret_model.pkl
│
├── reports/
│   ├── figures/
│   │   ├── wordcloud.png
│   │   ├── confusion_matrix.png
│   │   └── accuracy_plot.png
│   │
│   └── final_report.pdf
│
├── results/
│   ├── evaluation_results.csv
│   └── prediction_output.csv
│
└── docs/
    ├── proposal.md
    ├── methodology.md
    └── presentation.pptx
```

## Tahap Preprocessing Data

Tahap preprocessing bertujuan untuk membersihkan dan menyiapkan data mentah agar siap digunakan untuk tahap pemodelan Analisis Sentimen. Berikut alur preprocessing yang dilakukan:


### 1. Text Cleaning (Pembersihan Teks)
Proses text cleaning dilakukan untuk membersihkan data komentar dari berbagai noise agar teks menjadi lebih terstruktur dan siap digunakan dalam analisis lebih lanju. Pembersihan teks dieksekusi menggunakan pustaka *Regular Expression* (`re`). Modifikasi yang dilakukan pada setiap baris teks meliputi:
- **Case Folding:** Mengonversi seluruh teks menjadi huruf kecil (*lowercase*).
- **URL Removal:** Menghapus semua tautan/link web (`http://` atau `https://`).
- **Mention Removal:** Menghapus *username* atau *mention* akun lain (kata yang diawali simbol `@`).
- **Hashtag Removal:** Menghapus simbol tagar (`#`) dari teks.
- **Punctuation & Number Removal:** Menghapus seluruh angka, tanda baca, dan karakter spesial, menyisakan hanya karakter alfabet (a-z).
- **Whitespace Removal:** Menghapus spasi ganda atau spasi berlebih di awal/akhir kalimat.

### 2. Normalization (Normalisasi Slang)
Normalisasi dilakukan untuk mengubah kata-kata tidak baku atau slang yang sering muncul pada komentar media sosial menjadi bentuk baku.

### 3. Tokenization (Tokenisasi)
Teks yang sudah bersih dipecah menjadi kumpulan kata-kata individu (token). Tahapan ini bertujuan agar teks dapat diolah secara numerik, karena model machine learning tidak memahami kalimat utuh, melainkan memproses kata per kata

### 4. Stopword Removal (Penghapusan Stopword)
Menghapus kata-kata umum yang sering muncul tetapi tidak membawa makna sentimen yang signifikan (seperti: "dan", "di", "ke", "dari"). Proses ini diimplementasikan menggunakan `StopWordRemoverFactory` dari library `Sastrawi`.

### 5. Stemming
Langkah terakhir adalah mengembalikan setiap kata ke bentuk kata dasarnya (kata tanpa imbuhan/akhiran). Contoh: kata "memakan" akan diubah menjadi "makan". Tahap ini menggunakan `StemmerFactory` dari library `Sastrawi`. Tujuan stemming adalah untuk menyatukan berbagai variasi kata yang memiliki makna sama sehingga dapat mengurangi kompleksitas data

## Tahap Pemodelan dan Evaluasi (Modeling & Evaluation)

Fokus utama dalam proyek Analisis Sentimen ini adalah mengimplementasikan arsitektur *Deep Learning* menggunakan **Long Short-Term Memory (LSTM)**. LSTM dipilih karena kemampuannya dalam mengingat konteks dan urutan kata (sekuensial) dalam sebuah kalimat, yang sangat krusial dalam pemrosesan bahasa alami (NLP). Namun, untuk mengukur performa LSTM secara objektif, kami melakukan *benchmarking* (perbandingan) dengan beberapa algoritma *Machine Learning* tradisional sebagai *baseline*.

### Hasil Perbandingan Akurasi Model

Berikut adalah metrik akurasi yang didapatkan dari proses pengujian model pada dataset yang telah diproses:

| Peringkat | Model Klasifikasi | Akurasi (Accuracy) |
| :---: | :--- | :---: |
| 1 | **Support Vector Machine (SVM)** | **97.66%** (`0.976636`) |
| 2 | **Logistic Regression** | **95.87%** (`0.958723`) |
| 3 | **Naive Bayes** | **94.62%** (`0.946262`) |
| 4 | **LSTM (Model Utama Proyek)** | **94.62%** (`0.946262`) |

---




