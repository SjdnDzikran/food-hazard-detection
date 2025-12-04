# Food Hazard Detection

## Anggota Kelompok

1. Gafna Al Faatiha Prabowo (23/513334/PA/21930)
2. Dzikran Azka Sajidan (23/516665/PA/22110)
3. Muhammad Khairul Hasbi (23/519845/PA/22310)
4. Rifky Setiawan (23/519942/PA/22326)

## 1. Shared Task yang Dipilih

- **Nama Shared Task**: SemEval 2025 Task 9: The Food Hazard Detection Challenge - SubTask 1: Text classification for food hazard prediction, predicting the type of hazard and product
- **Tahun**: 2025
- **Sumber**: [GitHub Repository](https://github.com/food-hazard-detection-semeval-2025/food-hazard-detection-semeval-2025.github.io)

## 2. Definisi Permasalahan

- **Input**: Teks pendek judul recall makanan (title) beserta metadata sederhana seperti tanggal dan negara
- **Output**: Prediksi kategori bahaya (hazard-category) dan kategori produk (product-category) dari setiap judul recall
- **Deskripsi**: Shared Task ini bertujuan untuk menghasilkan sebuah sistem yang dapat mengklasifikasikan laporan recall makanan ke dalam kategori bahaya dan kategori produk hanya dari teks singkat. Model diharapkan mampu tetap bekerja dengan baik pada judul yang pendek dan distribusi label yang tidak seimbang, sehingga dapat membantu pemantauan isu keamanan pangan secara otomatis di berbagai negara. Dalam proyek ini, fokus kami berada pada SubTask 1 yang secara khusus memformulasikan permasalahan sebagai multi-task classification apakah sebuah judul termasuk ke dalam kombinasi kategori hazard-category dan product-category tertentu.
- **Metrik Evaluasi**: Macro F1-Score

## 3. Dataset

- **Nama Dataset**: SemEval-2025 Task 9 Dataset
- **Sumber Dataset**: [GitHub Data](https://github.com/food-hazard-detection-semeval-2025/food-hazard-detection-semeval-2025.github.io/tree/main/data)
- **Ukuran Data**:
  - Training: 5,032 sampel
  - Validation: 565 sampel
  - Test: 997 sampel
- **Rencana Pembagian Data**:
  - Training: Seluruh data latih akan digunakan untuk melatih model pada Task 1
  - Validation: Data validasi akan digunakan untuk pemilihan hyperparameter dan model terbaik
  - Test: Data tes akan digunakan untuk evaluasi akhir performa model pada data yang tidak terlihat

## 4. Pendekatan yang Direncanakan

- **Kelompok Model yang Dipilih**: Transformer

- **Alasan Pemilihan Model**: Tantangan utama task ini adalah klasifikasi multi-label dengan jumlah kelas yang sangat besar dan tidak seimbang (long-tail distribution), yang diekstraksi dari teks input yang sangat pendek. Model berbasis Transformer dipilih karena kemampuannya yang terbukti dalam menangkap representasi semantik yang kaya dari teks. Attention mechanism diharapkan dapat membantu model fokus pada kata kunci spesifik yang mengindikasikan bahaya atau produk, bahkan untuk kelas yang jarang muncul (minority classes).

- **Metodologi**: Kami mengusulkan arsitektur two-path (dua jalur). Path A akan menggunakan model Transformer (seperti BERT) untuk memproses 'Raw Text Title' dan mengekstrak text embedding (fitur semantik). Secara paralel, Path B akan memproses 'Engineed Features' (seperti panjang teks atau keyword) dan mengubahnya menjadi meta-features vector.

  Kedua vektor keluaran dari Path A dan Path B kemudian akan digabungkan (concatenate) dan dimasukkan ke 'Classification Head'. Lapisan output terakhir akan menggunakan aktivasi Sigmoid untuk melakukan prediksi multi-label pada 'Hazard Category' dan 'Product Category'.

## 5. Linimasa Pengerjaan

| Task | Week 11 | Week 12 | Week 13 | Week 14 |
|------|---------|---------|---------|---------|
| Proposal Proyek | ✓ | | | |
| Koleksi dan Mempersiapkan Data | ✓ | ✓ | | |
| Training dan Evaluasi Model | | ✓ | | |
| Uji Model dan Optimisasi | | ✓ | ✓ | |
| Menulis Laporan Akhir | | | ✓ | ✓ |
| Presentasi Hasil Akhir | | | | ✓ |