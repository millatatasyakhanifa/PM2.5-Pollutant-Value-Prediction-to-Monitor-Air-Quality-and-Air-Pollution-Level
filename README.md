# PM2.5 Pollutant Value Prediction to Monitor Air Quality and Air Pollution Levels

## Introduction

Polusi udara merupakan masalah serius yang menyebabkan banyak efek buruk pada kesehatan dan lingkungan. Oleh karena itu, proyek ini dibuat dengan tujuan untuk membuat model yang dapat memprediksi kadar PM2.5 30 jam ke depan untuk membantu memonitor kualitas udara dan tingkat polusi udara dalam upaya mencegah pencemaran udara yang semakin parah. Model yang dibuat berupa model time series menggunakan algoritma LSTM (Long Short-Term Memory) dan CNN (Convolutional Neural Network). LSTM digunakan karena mampu memproses data time series, sedangkan CNN efektif dalam mengekstrak fitur dari data time series.

## Dataset

Dataset yang digunakan pada proyek ini adalah [Air Pollution in Seoul](https://www.kaggle.com/datasets/bappekim/air-pollution-in-seoul) dari Kaggle. Dataset ini berisi informasi pengukuran polusi udara di Seoul, Korea Selatan, termasuk kadar PM2.5. Dataset ini terdiri dari 647511 baris data dengan 11 kolom variabel yang mencakup tanggal pengukuran, kode stasiun, alamat, lintang, bujur, dan nilai rata-rata polutan lainnya.

## Data Preparation

Tahap persiapan data melibatkan:

- Feature selection: Menghapus variabel yang tidak digunakan.
- Data cleaning: Menghapus outlier pada data PM2.5.
- Train-test split: Membagi data menjadi 90% data pelatihan dan 10% data pengujian.
- Data transforms: Melakukan scaling data dan menggunakan TimeseriesGenerator untuk mengelola data time series.

## Modeling

Dibuat dua model:

1. Model LSTM dengan 2 layer LSTM dan 3 layer dense.
2. Model CNN dengan 1 layer Conv1D, 1 layer MaxPooling1D, 1 layer Flatten, dan 3 layer dense.

## Evaluation

Metrik evaluasi yang digunakan pada proyek ini adalah Mean Absolute Error (MAE).

## Kesimpulan

Proyek ini menghasilkan model yang dapat memprediksi kadar PM2.5 untuk memantau kualitas udara dan tingkat polusi udara. Pada proyek ini model CNN memiliki kinerja lebih baik dibandingkan model LSTM. Informasi lebih detail mengenai projek ini dapat dibaca pada [Laporan Proyek Machine Learning](https://github.com/millatatasyakhanifa/PM2.5-Pollutant-Value-Prediction-to-Monitor-Air-Quality-and-Air-Pollution-Level/blob/main/Laporan%20Proyek%20Machine%20Learning%20-%20Millata%20Tasyakhanifa.md).

