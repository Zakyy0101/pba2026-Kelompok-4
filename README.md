# pba2026-Kelompok-4
Repositori untuk tugas besar PBA

## Anggota Kelompok 4
| Nama | NIM | Username GitHub |
| --- | --- | --- |
| Muhammad Zaky Zaiddan | 122450119 | @Zakyy0101 |
| Berliana Enda Putri | 122450065 | @berlianaendaputri |
| Lisa Diani Amelia | 122450021 | @lisadiani29 |

---

## Pernyataan Kontribusi
Kami berkomitmen untuk berkontribusi secara adil dalam pengerjaan Tugas Besar ini, yang akan tercermin melalui riwayat commit pada repositori ini.
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
- Netral

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





## Tahapan Analisis
1. Exploratory Data Analysis (EDA)

EDA dilakukan untuk memahami karakteristik data, meliputi:

Distribusi panjang komentar
Distribusi jumlah kata
Visualisasi WordCloud
Analisis frekuensi kata


2. Text Preprocessing

Tahapan preprocessing dilakukan untuk membersihkan teks dari noise sebelum digunakan dalam model. Proses yang dilakukan meliputi:

Lowercasing (mengubah huruf menjadi kecil)
Menghapus URL, simbol, dan angka
Normalisasi kata tidak baku (slang)
Tokenisasi (memecah kalimat menjadi kata)
Stopword removal
(Opsional) Stemming menggunakan Sastrawi


3. Pelabelan Data

Komentar diklasifikasikan ke dalam tiga label:

Positif
Negatif
Netral

4. Pemodelan

Model yang digunakan dalam penelitian ini:

