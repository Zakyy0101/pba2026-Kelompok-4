# pba2026-Kelompok-4
Repositori untuk tugas besar PBA

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
Dataset diperoleh melalui proses scraping dari komentar YouTube.

Link dataset:


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
1.

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
