# Prediksi Harga Rumah Jabodetabek

Proyek end-to-end machine learning untuk memprediksi harga jual rumah
di Jabodetabek dari data listing properti.

> Demo: (diisi setelah deploy)

## 1. Tujuan
Satu-dua kalimat: model memprediksi harga jual rumah tinggal
berdasarkan lokasi, luas tanah, luas bangunan, jumlah kamar, dll.
Sebutkan siapa yang terbantu (pembeli, agen, investor).

## 2. Dataset
- Sumber: Kaggle "Daftar Harga Rumah Jabodetabek" (nafisbarizki),
  hasil scraping rumah123.com tahun 2022
- Ukuran awal: 3553 baris, 27 kolom
- Ukuran setelah cleaning: 3424 baris, 24 kolom
- Catatan: harga adalah harga listing (permintaan penjual), bukan harga transaksi

## 3. Struktur folder
(tempel struktur folder kamu: data/raw, data/processed, notebook, src, app, models)

## 4. Cleaning (notebook/02_cleaning.ipynb)
Tabel: langkah | alasan | baris terbuang
- Duplikat | iklan sama terhitung dua kali | 79
- Properti komersial (kos, hotel, guest house) | bukan rumah tinggal, kamar membengkak | 20
- Oper kredit / take over | harga bukan harga pasar | 10
- Lelang | harga bukan harga pasar | 5
- Salah ketik (luas bangunan < 10, rasio harga tidak masuk akal, dll.) | sisanya
- Total dibuang: 129 baris
- Kolom dibuang: lat/long (hanya titik tengah kecamatan, bukan lokasi presisi),
  year_built (duplikat building_age), 3 kolom turunan harga per m²
  (berisiko data leakage)

(Cocokkan angka per langkah dengan log di notebook kamu.)

## 5. Temuan EDA (notebook/03_eda.ipynb)
3-5 poin, masing-masing satu kalimat. Contoh yang sudah kamu temukan:
- Harga sangat miring ke kanan (skewness 11,85), jadi di-log menjadi 0,69
- Luas bangunan dan jumlah kamar mandi berkorelasi kuat dengan log harga
- Missing value terbesar: building_orientation (~46%) dan building_age (~41%)
Tambahkan 1-2 gambar grafik dengan ![](path/gambar.png)

## 6. Keterbatasan (isi sambil jalan)
- Harga listing 2022, bukan transaksi
- Lokasi hanya level kecamatan
- Sebagian kolom banyak kosong

## 7. Cara menjalankan (isi di akhir)
## 8. Hasil model (isi di akhir)