# Sistem Rekomendasi Restoran - Husnan

## Domain Proyek

Pada perusahaan food delivery service biasanya mereka mengumpulkan berbagai informasi mengenai pelanggan, restoran dan masakannya, serta rating yang diberikan pelanggan untuk restoran-restoran tersebut. Tentu perusahaan ingin memanfaatkan data tersebut untuk meningkatkan transaksi di perusahaan.

## Business Understanding
### Problem Statements
- Berdasarkan data mengenai pengguna, bagaimana membuat sistem rekomendasi yang dipersonalisasi dengan teknik content-based filtering?
- Dengan data rating yang Anda miliki, bagaimana perusahaan dapat merekomendasikan restoran lain yang mungkin disukai dan belum pernah dikunjungi oleh pengguna?

### Goals

Menjelaskan tujuan dari pernyataan masalah:
- Menghasilkan sejumlah rekomendasi restoran yang dipersonalisasi untuk pengguna dengan teknik content-based filtering.
- Menghasilkan sejumlah rekomendasi restoran yang sesuai dengan preferensi pengguna dan belum pernah dikunjungi sebelumnya dengan teknik collaborative filtering.

## Data Understanding
Data yang digunakan pada proyek kali ini adalah [restaurant and consumer](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data) dataset.
Dalam kasus ini, kita memiliki 9 file terpisah mengenai restoran, konsumen, dan rating.

## Data Preparation
Data preparation yang dilakukan adalah sebagai berikut:
- Mengatasi Missing Value
  - Mengecek missing value pada dataframe all_resto
  - Membersihkan missing value dengan fungsi dropna()
  - Mengecek kembali missing value pada variabel all_resto_clean
- Menyamakan Jenis masakan
  - Mengurutkan resto berdasarkan PlaceID kemudian memasukkannya ke dalam variabel fix_resto
  - Mengecek berapa jumlah fix_resto
  - Mengecek kategori masakan yang unik
  - Mengecek kategori masakan Game
  - Mengecek kategori masakan pada nama restoran KFC
  - Mengubah nama kategori masakan ‘Game’ menjadi ‘American’
  - Membuang data duplikat pada variabel preparationMembuat variabel preparation yang berisi dataframe fix_resto kemudian mengurutkan berdasarkan placeID
  - Mengonversi data series ‘placeID’ menjadi dalam bentuk list
  - Mengonversi data series ‘Name’ menjadi dalam bentuk list
  - Mengonversi data series ‘Rcuisine’ menjadi dalam bentuk list
  - Membuat dictionary untuk data ‘resto_id’, ‘resto_name’, dan ‘cuisine’

## Modeling
Modelling yang dilakukan adalah sebagai berikut:
- Model Development dengan Content Based Filtering
  - TF-IDF Vectorizer
    - Inisialisasi TfidfVectorizer
    - Melakukan perhitungan idf pada data cuisine
    - Mapping array dari fitur index integer ke fitur nama
    - Melakukan fit lalu ditransformasikan ke bentuk matrix
    - Melihat ukuran matrix tfidf
    - Mengubah vektor tf-idf dalam bentuk matriks dengan fungsi todense()
    - Membuat dataframe untuk melihat tf-idf matrix
  - Cosine Similarity
    - Menghitung cosine similarity pada matrix tf-idf
    - Membuat dataframe dari variabel cosine_sim dengan baris dan kolom berupa nama resto
    - Melihat similarity matrix pada setiap resto
  - Mendapatkan Rekomendasi
    - Mengambil data dengan menggunakan argpartition untuk melakukan partisi secara tidak langsung sepanjang sumbu yang diberikan    
    - Mengambil data dengan similarity terbesar dari index yang ada
    - Drop nama_resto agar nama resto yang dicari tidak muncul dalam daftar rekomendasi
    - Mendapatkan rekomendasi restoran yang mirip dengan KFC
 
- Model Development dengan Collaborative Filtering
  - Data Understanding
  - Data Preparation
    - Mengubah userID & placeID menjadi list tanpa nilai yang sama
    - Melakukan encoding userID & placeID
    - Melakukan proses encoding angka ke ke userID & placeID
    - Mapping userID ke dataframe user
    - Mapping placeID ke dataframe resto
    - Mendapatkan jumlah user
    - Mendapatkan jumlah resto
    - Mengubah rating menjadi nilai float
  - Membagi Data untuk Training dan Validasi
    - Mengacak dataset
    - Membuat variabel x untuk mencocokkan data user dan resto menjadi satu value
    - Membuat variabel y untuk membuat rating dari hasil 
    - Membagi menjadi 80% data train dan 20% data validasi

## Evaluation
- Model ini menggunakan Binary Crossentropy untuk menghitung loss function, Adam (Adaptive Moment Estimation) sebagai optimizer, dan root mean squared error (RMSE) sebagai metrics evaluation. 
