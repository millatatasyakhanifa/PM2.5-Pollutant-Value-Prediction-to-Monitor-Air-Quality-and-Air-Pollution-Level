# **Laporan Proyek Machine Learning - Millata Tasyakhanifa**
## **1. Kesehatan dan Lingkungan**
Polusi udara merupakan masalah serius yang menyebabkan banyak efek buruk pada kesehatan, lingkungan dan biaya medis[1]. IQAir sebagai platform yang menampilkan kualitas udara dan tingkat polusi udara negara di seluruh dunia menyatakan bahwa Indonesia berada pada peringkat 9 sebagai negara dengan kualitas udara terburuk[2]. Dan menurut IQAir, pada tahun 2021 DKI Jakarta sebagai Ibu Kota negara Indonesia diperkirakan telah terjadi 12,000 kasus kematian dan kerugian sekitar $3,000,000,000 USD yang disebabkan oleh polusi udara. Polutan utama yang yang mencemari udara di Jakarta adalah PM2.5.[3] PM2.5 didefinisikan sebagai partikel udara ambien yang berukuran hingga 2,5 mikron. PM2.5 mencakup berbagai susunan kimia yang berasal dari berbagai sumber. Sumber paling umum yang disebabkan oleh manusia yaitu kendaraan bermotor berbahan bakar fosil, pembangkit listrik, kegiatan industri, pertanian dan pembakaran biomassa. PM2.5 menjadi polutan yang paling berbahaya bagi kesehatan manusia karena ukuran mikroskopisnya memungkinkan partikel-partikel PM2.5 dapat terserap jauh ke dalam aliran darah saat terhirup. Hal ini berpotensi menyebabkan efek kesehatan yang luas seperti asma, kanker paru-paru, dan penyakit jantung. Paparan PM2.5 juga dapat menyebabkan penyakit kardiovaskular, kematian dini dan telah dikaitkan dengan berat badan lahir rendah, peningkatan infeksi saluran pernapasan akut, dan stroke.[4] Melihat dampak negatif yang diberikan oleh polutan PM2.5 sangat besar bagi kesehatan manusia dan lingkungan. Oleh karena itu, agar dapat mengatasi masalah tersebut perlu dilakukan prediksi kadar PM2.5 yang ada di udara untuk memonitor kualitas udara dan tingkat polusi udara pada 30 jam ke depan. Hal ini juga dapat menjadi salah satu upaya untuk mencegah pencemaran udara semakin parah.

1. [mdpi.com](https://www.mdpi.com/1660-4601/18/13/7087)
2. [iqair.com](https://www.iqair.com/id/world-air-quality)
3. [iqair.com](https://www.iqair.com/id/indonesia/jakarta)
4. [greenpeace.org](https://www.greenpeace.org/static/planet4-indonesia-stateless/2021/03/5e9889e6-2020_world_air_quality_report.pdf)

## **2. Business Understanding**
### **2.1 Problem Statements**
Diberikan sebuah input berupa data kadar PM2.5. Dan dari input tersebut diharapkan menghasilkan output berupa kadar PM2.5 untuk 30 jam ke depan. Bagaimana cara memprediksi kadar PM2.5 pada 30 jam ke depan untuk memonitor kualitas udara dan tingkat polusi udara?

### **2.2 Goals**
Pada proyek ini goals yang ingin dicapai adalah sebagai berikut:
	- Membuat model yang dapat memprediksi PM2.5 pada 30 jam ke depan untuk membantu memonitor kualitas udara dan tingkat polusi udara.

### **2.3 Solution statements**
Solusi yang dapat dilakukan untuk menyelesaikan problem statement pada proyek ini adalah dengan membuat sebuah model time series yang dapat memprediksi kadar PM2.5 pada 30 jam ke depan dengan memanfaatkan data PM2.5 yang tersedia pada saat ini. Algoritma yang akan digunakan untuk membuat model adalah sebagai berikut:
	- LSTM merupakan salah satu jenis arsitektur dari RNN (Recurrent Neural Network). Algoritma ini dapat digunakan untuk menyelesaikan masalah berkaitan dengan time series karena LSTM dapat menyimpan informasi dalam jangka waktu yang lama. Oleh karena itu, ini dapat digunakan untuk memproses, memprediksi, dan mengklasifikasikan berdasarkan data time series.[5]
	- CNN merupakan algoritma yang dapat digunakan untuk masalah time series. Algoritma ini memiliki keunggulan karena highly noise-resistant dan dapat mengekstrak fitur dan membuat representasi time series yang informatif dan mendalam secara otomatis.[6]

5. [geeksforgeeks.org](https://www.geeksforgeeks.org/deep-learning-introduction-to-long-short-term-memory/)
6. [towardsdatascience.com](https://towardsdatascience.com/how-to-use-convolutional-neural-networks-for-time-series-classification-56b1b0a07a57)

## **3. Data Understanding**
Dataset yang digunakan pada proyek ini adalah dataset Air Pollution in Seoul yang diunduh dari Kaggle. Dataset ini berisi informasi pengukuran polusi udara di kota Seoul, Korea Selatan. Pada dataset ini terdapat 647511 baris data dan 11 kolom variabel. Adapun variabel-variabel yang terdapat pada dataset Air Pollution in Seoul adalah sebagai berikut:
	- Measurement date: berisi tanggal pengukuran data polutan
	- Station code: berisi kode stasiun tempat diambilnya data polutan
	- Address: berisi alamat tempat diambilnya data polutan
	- Latitude: berisi garis lintang tempat diambilnya data polutan
	- Longitude: berisi garis bujur tempat diambilnya data polutan
	- SO2: nilai rata-rata untuk polutan SO2
	- NO2: nilai rata-rata untuk polutan NO2
	- O3: nilai rata-rata untuk polutan O3
	- CO: nilai rata-rata untuk polutan CO
	- PM10: nilai rata-rata untuk polutan PM10
	- PM2.5: nilai rata-rata untuk polutan PM2.5

Pada dataset Air Pollution in Seoul tidak ditemukan data yang terduplikat dan semua data yang ada memiliki nilai yang unik. Dataset ini juga bersih dari missing value sehingga tidak perlu dilakukan penghapusan missing value pada tahap data preparation.

Pada proyek ini juga dilakukan visualisasi nilai PM2.5 selama 30 jam mulai dari tanggal 01-01-2017 pukul 00:00 sampai tanggal 02-01-2017 pukul 05:00 seperti pada gambar berikut.

![image](https://github.com/millatatasyakhanifa/PM2.5-Pollutant-Value-Prediction-to-Monitor-Air-Quality-and-Air-Pollution-Level/blob/main/PM2.5%20Visualization.JPG)

Dilihat dari hasil plotnya dapat disimpulkan bahwa di kota Seoul khususnya di Jongno District memiliki kadar PM2.5 di bawah 65 pada pukul 00:00 sampai pukul 08:00 pagi dan mulai naik pada pukul 08:00 dan puncaknya pada pukul 10:00 pagi sampai pukul 13:00 siang dengan kadar PM2.5 di atas 75. Dan pada pukul 14:00 tanggal 01-01-2017 sampai pukul 05:00 tanggal 02-01-2017 kadar PM2.5 menjadi menurun menjadi <=75.

Untuk mengunduh dataset Air Pollution in Seoul dari Kaggle dapat menggunakan link berikut ini: 

7. [kaggle.com](https://www.kaggle.com/bappekim/air-pollution-in-seoul)

## **4. Data Preparation**
Pada proyek ini dilakukan tahapan-tahapan data preparation sebagai berikut:
	- Teknik Feature selection: Pada proyek ini dilakukan penghapusan variabel yang tidak digunakan. Penghapusan variabel yang tidak digunakan ini bertujuan untuk membersihkan data yang tidak diperlukan dalam pembuatan model. Karena jika tidak dihapus data ini dapat memakan ruang memori.
	 -Teknik data Cleaning: Pada proyek ini dilakukan pembersihan data dengan menghapus outlier pada data PM2.5. Dan Penghapusan outlier dilakukan karena data yang digunakan pada proyek ini terdapat banyak outlier. Dan jika tidak dihapus outlier dapat menyebabkan model yang akan dibuat memiliki kinerja rendah dan hasil yang tidak bisa diandalkan. 
	-Teknik Train Test Split: Pada proyek ini dilakukan pembagian data menjadi 90% data training dan 10% data testing dengan menggunakan train test split. Jadi jumlah data training yang digunakan sebanyak 554442 dan untuk jumlah data testing sebanyak 61605.
	-Teknik data transforms: Pada proyek ini dilakukan scaling data menggunakan MinMaxScaler. MinMaxScaler digunakan untuk mengubah data yang digunakan pada proyek ini berada pada rentang 0 sampai 1. Kemudian membuat generator menggunakan TimeseriesGenerator untuk membantu menangani time series dengan mudah. TimeseriesGenerator dapat membantu menentukan prediksi yang ingin dilakukan. Pada proyek ini akan dilakukan prediksi kadar PM2.5 pada 30 jam ke depan. Generator yang dibuat pada tahap ini akan digunakan untuk training model dengan parameter yang digunakan sebagai berikut:
	1. Scaled train yang merupakan data sekaligus target yang digunakan model.
	2. Length merupakan panjang setiap sempel yang digunakan untuk training model dan untuk proyek ini menggunakan length=30. 
	3. Batch size merupakan ukuran sub-seri output per batch dan pada proyek ini menggunakan batch_size=128.
	Dan test_generator dibuat untuk digunakan pada saat prediksi menggunakan model terbaik. Parameter yang digunakan sama seperti generator untuk training model hanya saja Scaled train diubah menjadi Scaled test yang merupakan data sekaligus target yang digunakan untuk prediksi menggunakan model terbaik.

## **5. Modeling**
Setelah data selesai dipreprocessing, pembuatan model dapat dilakukan. Pada proyek ini akan dibuat 2 model. Model pertama dibuat menggunakan LSTM dengan 2 layer LSTM dan 3 dense layer. Kemudian model dicompile menggunakan tf.keras.losses.Huber, optimizer SGD dengan learning rate=1e-3 momentum=0.9 dan metrics yang digunakan adalah MAE. Proses training model pertama menggunakan generator dan 10 epochs. Model kedua dibuat menggunakan CNN dengan 1 layer Conv1D, 1 layer MaxPooling1D, 1 layer Flatten, dan 3 dense layer. Model kedua juga dicompile menggunakan tf.keras.losses.Huber, optimizer SGD dengan learning rate=1e-4 momentum=0.9 dan metrics yang digunakan adalah MAE. Proses training model kedua juga menggunakan generator dan 10 epochs. Pada saat mengcompile model, tf.keras.losses.Huber dipilih sebagai parameter loss pada kedua model dikarenakan tf.keras.losses.Huber dapat digunakan dalam masalah berkaitan dengan memprediksi nilai real atau regresi. Optimizer SGD dipilih karena dapat memperbarui parameter model lebih sering dan membutuhkan sedikit memori. metrics MAE dipilih karena proyek ini akan memprediksi nilai real dan MAE juga biasa digunakan pada masalah time series.
Setelah proses training ke dua model selesai dihasilkan nilai sebagai berikut:

| Model | Nilai MAE | Nilai Loss | Waktu Training |
| ----- | --------- |------------|----------------|
| LSTM  |   0.1358  |   0.0160   |286s (66ms/step)|
| CNN   |   0.0787  |   0.0062   |29s (7ms/step)  |

Dari hasil proses training model LSTM dan model CNN di atas dapat dilihat bahwa model CNN menghasilkan nilai loss, dan nilai MAE lebih kecil dari pada model LSTM. Proses training model CNN juga lebih cepat dibandingkan dengan model LSTM. Hal ini menunjukkan bahwa pada proyek ini model CNN memiliki kinerja yang lebih baik. Dan pada saat model CNN digunakan untuk memprediksi kadar PM2.5 pada data test diperoleh hasil MAE dan loss sebagai berikut:

| Model | Nilai MAE | Nilai Loss |
| ----- | --------- |------------|
| CNN   |   0.0767  |   0.0059   |

## **6. Evaluation**
Metrik evaluasi yang digunakan untuk mengukur kinerja model pada proyek ini adalah MAE atau Mean Absolute Error. Dalam machine learning MAE didefinisikan sebagai kesalahan absolut yang mengacu pada besarnya perbedaan antara nilai prediksi dengan nilai aktualnya. MAE akan mengambil nilai rata-rata dari kesalahan absolut untuk sekelompok data prediksi sebagai pengukuran besarnya kesalahan dari seluruh kelompok.[8] Adapun rumus menghitung nilai MAE adalah sebagai berikut:
MAE = 1/n ∑|ya-yp|
Dimana: 
ya  = nilai aktual
yp = nilai prediksi
n = jumlah baris data

8. [c3.ai](https://c3.ai/glossary/data-science/mean-absolute-error/)

Pada proyek ini MAE dipilih sebagai metrik evaluasi karena MAE umum digunakan untuk mengukur kesalahan perkiraan dari masalah yang berkaitan dengan time series. Selain itu MAE dapat digunakan untuk mengukur seberapa akurat hasil prediksi dengan nilai aslinya. Berikut gambar yang menampilkan hasil plot loss dan MAE dari model LSTM dan model CNN yang dibuat pada proyek ini. 

![image](https://github.com/millatatasyakhanifa/PM2.5-Pollutant-Value-Prediction-to-Monitor-Air-Quality-and-Air-Pollution-Level/blob/main/loss%20graph%20of%20lstm%20model.JPG)

![image](https://github.com/millatatasyakhanifa/PM2.5-Pollutant-Value-Prediction-to-Monitor-Air-Quality-and-Air-Pollution-Level/blob/main/MAE%20graph%20of%20LSTM%20Model.JPG)

![image](https://github.com/millatatasyakhanifa/PM2.5-Pollutant-Value-Prediction-to-Monitor-Air-Quality-and-Air-Pollution-Level/blob/main/loss%20graph%20of%20cnn%20model.JPG)

![image](https://github.com/millatatasyakhanifa/PM2.5-Pollutant-Value-Prediction-to-Monitor-Air-Quality-and-Air-Pollution-Level/blob/main/MAE%20graph%20of%20CNN%20Model.JPG)

Ke-4 plot tersebut mengalami penurunan yang signifikan. Di mana loss model LSTM turun dari  0.0199 sampai 0.0160. Dan MAE model LSTM turun dari 0.1576 sampai 0.1358. Sedangkan untuk model CNN nilai lossnya turun dari 0.0134 sampai 0.0062. Dan nilai MAEnya turun dari 0.1222 sampai 0.0787.

Dari hasil di atas dapat dilihat bahwa model CNN menghasilkan nilai MAE dan loss yang lebih kecil dari model LSTM. Sehingga model CNN memiliki kinerja yang bagus dan dapat memprediksi kadar PM2.5 lebih baik dari model LSTM. Berikut gambar yang menampilkan plot nilai actual PM2.5 dan nilai prediksi PM2.5 menggunakan model CNN.

![image](https://github.com/millatatasyakhanifa/PM2.5-Pollutant-Value-Prediction-to-Monitor-Air-Quality-and-Air-Pollution-Level/blob/e87a58d06bf817083a95f6e094202dc064c24b8b/PM2.5%20Predict%20vs%20PM2.5%20Actual.JPG)

Dilihat dari plot di atas model yang dibuat pada proyek ini masih perlu dilakukan pengembangan untuk menghasilkan model yang lebih andal dan akurat dalam memprediksi kadar PM2.5. Pengembangan tersebut dapat dilakukan dengan membuat arsitektur model yang lebih kompleks dengan menambahkan layer atau dengan melakukan hyperparameter tuning pada model yang dibuat. 
