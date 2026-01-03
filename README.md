# 🇮🇩 Indonesian Credit Default Prediction (ADIKARA 2025)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-orange)
![Status](https://img.shields.io/badge/Competition-ADIKARA%202025-red)

> **Proyek Machine Learning untuk memprediksi risiko gagal bayar (credit default) pada sektor UMKM & Mikro di Indonesia.**

## 📌 Latar Belakang

Sektor keuangan mikro dan UMKM memegang peranan vital dalam pertumbuhan ekonomi Indonesia. Adopsi teknologi finansial (*fintech*) telah memperluas akses pembiayaan digital, namun juga memunculkan tantangan baru terkait manajemen risiko kredit.

Variasi latar belakang peminjam, jenis jaminan, dan karakteristik regional menyebabkan tingkat risiko yang beragam. Proyek ini bertujuan untuk membangun model klasifikasi biner yang dapat mengidentifikasi pola risiko dan memprediksi status gagal bayar nasabah secara akurat.

## 🎯 Tujuan Proyek

1.  **Klasifikasi Risiko:** Memprediksi status nasabah: `0` (Lancar/Non-default) atau `1` (Macet/Default).
2.  **Optimasi Metrik:** Menggunakan **Macro-averaged F1 Score** sebagai metrik evaluasi utama untuk menangani ketidakseimbangan kelas (*class imbalance*).
3.  **Analisis Faktor:** Mengidentifikasi karakteristik peminjam dan bisnis yang paling mempengaruhi risiko kredit.

## 🛠️ Metodologi & Alur Kerja

Pendekatan teknis yang dilakukan dalam repositori ini mencakup langkah-langkah *end-to-end* berikut:



### 1. Data Preprocessing & Cleaning
* **Handling Missing Values:** Mengisi nilai kosong dan menangani nilai *infinite* untuk menjaga stabilitas model.
* **Datetime Extraction:** Mengekstrak fitur temporal (`Tahun`, `Bulan`) dari kolom `tanggal_pencairan` untuk menangkap pola musiman.

### 2. Feature Engineering (Rekayasa Fitur)
Membuat fitur turunan baru untuk memperkaya informasi finansial nasabah:
* `bunga_nominal`: Selisih total pengembalian dengan pokok pinjaman.
* `bunga_persen`: Persentase bunga terhadap pokok pinjaman.
* `cicilan_harian`: Estimasi beban harian nasabah (`total_pengembalian` / `durasi_hari`).
* `ratio_lender`: Proporsi pengembalian yang menjadi hak pemberi pinjaman (*lender*).

### 3. Encoding
Mengubah variabel kategorikal menjadi format numerik menggunakan **Label Encoding**:
* `provinsi`, `jenis_pinjaman`, `status_peminjam`, `sektor_usaha`, `pendidikan`, `jenis_jaminan`.

### 4. Pemodelan (Modeling)
Algoritma yang digunakan adalah **Random Forest Classifier** dengan konfigurasi khusus untuk menangani data yang tidak seimbang:
* **Algorithm:** Random Forest
* **Class Weight:** `balanced` (Memberikan bobot lebih pada kelas minoritas/macet).
* **Estimators:** 200 trees.
* **Max Depth:** 15 (Untuk mencegah overfitting).

## 📊 Evaluasi Model

Model dievaluasi menggunakan **Macro F1-Score**. Metrik ini dipilih karena menghitung rata-rata harmonik antara *Precision* dan *Recall* untuk setiap kelas secara independen, sehingga memberikan gambaran performa yang adil meskipun jumlah data kelas "Macet" jauh lebih sedikit daripada "Lancar".

## 📂 Struktur Repository

```text
├── notebooks/          # Jupyter Notebooks untuk eksplorasi dan training
├── submission/         # Hasil prediksi (CSV)
├── README.md           # Dokumentasi Proyek
└── requirements.txt    # Dependencies library
