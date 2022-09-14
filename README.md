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
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
