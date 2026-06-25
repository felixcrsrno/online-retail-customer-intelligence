# Customer Intelligence & Behavioral Analytics: Segmenting Online Retail Transactors

[![Python Version](https://img.shields.io/badge/python-3.13-blue.svg)](https://www.python.org/)
[![Data Source](https://img.shields.io/badge/Dataset-UCI%20Kaggle-orange)](https://www.kaggle.com/datasets/mashlyn/online-retail-ii-uci)
[![Machine Learning](https://img.shields.io/badge/Algorithms-K--Means%20%7C%20Apriori-green)](https://scikit-learn.org/)

## 📌 Ringkasan Projek
Projek ini bertujuan untuk membangun sistem *Customer Intelligence* end-to-end dengan memanfaatkan riwayat transaksi e-commerce (`Online Retail II Dataset` yang berisi lebih dari 1 juta baris data). Melalui pendekatan analitik ini, perilaku belanja pelanggan dipetakan secara objektif menggunakan dua pilar utama:
1. **Segmentasi Perilaku (Behavioral Segmentation):** Kombinasi kerangka kerja **RFM (Recency, Frequency, Monetary)** dan algoritma pembelajaran tak terarah **K-Means Clustering**.
2. **Analisis Pola Pembelian (Market Basket Analysis):** Penerapan aturan asosiasi (*Association Rules*) untuk menemukan kombinasi item yang memiliki kecenderungan tinggi dibeli bersamaan.

Implementasi ini memberikan basis data yang kuat bagi tim pemasaran untuk menyusun strategi retensi, penentuan paket produk (*bundling*), serta personalisasi kampanye iklan.

---

## 🛠️ Alur Kerja & Metodologi

Pengerjaan projek dijalankan secara terstruktur yang dibagi menjadi beberapa fase krusial:

### 1. Eksplorasi & Pembersihan Data (EDA & Data Cleaning)
* Mengevaluasi struktur data awal (1,067,371 baris transaksi).
* Mengatasi anomali data seperti nilai yang hilang (*missing values*) pada atribut penting dan membersihkan data transaksi pembatalan (koreksi kuantitas negatif).
* Melakukan reduksi prediktif dengan berfokus pada pasar mayoritas (*United Kingdom*) untuk menjaga validitas model asosiasi.

### 2. Rekayasa Fitur RFM (Feature Engineering)
* **Recency (R):** Menghitung jumlah hari sejak transaksi terakhir pelanggan hingga tanggal referensi terkini.
* **Frequency (F):** Menghitung total volume pesanan unik yang diselesaikan oleh pelanggan.
* **Monetary (M):** Akumulasi total pengeluaran finansial dari riwayat belanja pelanggan.
* **Normalisasi:** Melakukan transformasi logaritma (`np.log1p`) untuk mengatasi bias kemiringan data (*skewed distribution*), dilanjutkan dengan standardisasi fitur menggunakan `StandardScaler`.

### 3. Pemodelan Klaster (K-Means Clustering)
* Menggunakan metode **Elbow Method** dan evaluasi nilai keinklinasian inersia untuk menentukan jumlah klaster pelanggan yang paling optimal.
* Membentuk klaster representatif seperti kelompok konsumen bernilai tinggi (*Champions/Loyal*) hingga kelompok berisiko lepas (*At-Risk/Churn*).

### 4. Penambangan Aturan Asosiasi (Market Basket Analysis)
* Mentransformasi data transaksi ritel menjadi format matriks keranjang belanja.
* Menerapkan metrik evaluasi aturan asosiasi seperti **Support**, **Confidence**, dan **Lift Score** (fokus pada aturan dengan nilai *Lift > 1*).

---

## 📊 Hasil dan Dampak Strategis

Berdasarkan eksekusi model di dalam *notebook*, sistem analitik ini berhasil mengidentifikasi komponen penting berikut:

* **Peta Distribusi Konsumen:** Profiling mendalam dari tiap klaster pelanggan yang mencerminkan kontribusi finansial riwayat belanja mereka terhadap bisnis.
* **Rekomendasi Bundling Produk:** Menemukan pola barang yang saling melengkapi (kombinasi produk dengan nilai keterikatan tinggi) untuk meningkatkan *Average Basket Size* per transaksi.

### Implikasi Bisnis (Actionable Insights):
1. **Retensi Terarah:** Memprioritaskan alokasi anggaran pemasaran bagi pelanggan di klaster *Champions* & *Loyal* untuk mempertahankan loyalitas.
2. **Re-engagement Campaign:** Merancang program promosi khusus penawaran kembali (*win-back*) untuk segmen *At-Risk* sebelum mereka sepenuhnya beralih.
3. **Cross-Selling Otomatis:** Memanfaatkan hasil rules dari Market Basket Analysis sebagai pondasi dasar algoritma rekomendasi item pada sistem aplikasi kasir atau e-commerce.

---

## 📂 Hasil Output File Projek
Eksekusi dari skrip analisis ini menghasilkan beberapa berkas aset data pendukung:
* `segment_profile.csv` — Profil demografis dan statistik lengkap untuk masing-masing klaster pelanggan.
* `segment_overview.png` — Visualisasi sebaran dan distribusi dari segmentasi konsumen.
* `bundling_recommendations.png` — Grafik rekomendasi kombinasi produk terbaik hasil algoritma asosiasi.

---

## 🚀 Cara Menjalankan Projek

1. **Clone Repositori:**
   ```bash
   git clone [https://github.com/username-kamu/nama-repo-kamu.git](https://github.com/username-kamu/nama-repo-kamu.git)
   cd nama-repo-kamu
