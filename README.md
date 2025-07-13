# Proyek-Analisis-Sentimen-Aplikasi-JKN-Mobile
About Ini adalah proyek analisis sentimen yang saya buat untuk memenuhi submission awal kelas ML Menengah dari Dicoding (per 8/12/2024)

## Business Understanding
Aplikasi JKN Mobile merupakan platform layanan kesehatan digital yang digunakan oleh masyarakat Indonesia dalam mengakses berbagai layanan BPJS Kesehatan. Ulasan pengguna pada aplikasi ini di Google Play Store mencerminkan kepuasan atau ketidakpuasan pengguna atas layanan atau performa dalam aplikasi ini. Untuk meningkatkan kualitas layanan, penting untuk memahami persepsi dan sentimen pengguna berdasarkan ulasan yang telah diberikan.

## Permasalahan Bisnis
Apa saja sentimen yang muncul dari ulasan pengguna terhadap aplikasi JKN Mobile? Bagaimana distribusi sentimen positif, negatif, dan netral dari ulasan tersebut sehingga dapat membantu dalam meningkatkan kualitas layanan aplikasi? Apa pemodelan Machine Learning terbaik dari pengujian model dengan Naive Bayes, Random Forest, Logistic Regression dan Decision Tree?

## Cakupan Proyek
Proyek ini bertujuan membantu pihak terkait dalam memahami persepsi pengguna aplikasi JKN Mobile dengan pendekatan analisis sentimen menggunakan Natural Language Processing (NLP) dan Machine Learning dalam memprediksi sentimen kalimat/kata.

1. Data Collection:
Melakukan scraping ulasan pengguna aplikasi JKN Moble dari Google Play Store, mengambil data ulasan hanya berupa komentarnya saja dan maksimal sebanyak 10.000 entry data.

2. Data Understanding:
Memahami struktur data hasil scraping, termasuk panjang komentar, distribusi rating, dan waktu ulasan untuk melihat pola data awal.

3. Data Cleaning dan Pre-Processing Teks:
Melakukan pembersihan data seperti menghapus nilai yang kosong, nilai duplikat, dan melakukan pre-processing seperti menghilangkan tanda baca, link, hashtag, menyamakan huruf menjadi kecil semua, melakukan tokenizing (memecah kalimat menjadi teks), melakukan filtering, menerapkan stopwords serta melakukan normalisasi teks untuk keperluan analisis NLP.

4. Pelabelan Sentimen:
Melakukan import dari kamus positif dan negatif dari github untuk memberikan label pada data yang telah melalui pre-processing. Dimana ini membuat fungsi untuk menentukan skor dalam kata positif, negatif, dan netral sesuai kamus yang sudah didapat.

5. Analisis Hasil Label Sentimen dengan Pie Chart dan Wordcloud:
Hasil pelabelan menghasilkan sentimen positif sebanyak 1647 ulasan, sentimen negatif 7942 ulasan dan sentimen netral sebanyak 411 ulasan. Berikut ini adalah hasil pie chart presentase sentimen data.

<img width="701" height="525" alt="image" src="https://github.com/user-attachments/assets/69d64155-13a5-4dd2-9a88-a5aa024e224b" />

Hasil visualisasi di atas menunjukkan ulasan pengguna didominasi oleh sentimen negatif sebesar 79.42%, sementara sisanya ada 16.47% sentimen positif dan hanya 4.11% sentimen netral. Ini menunjukkan jika ulasan aplikasi JKN Mobile perlu mendapat banyak evaluasi dan perbaikan besar karena nilai sentimen negatif yang sangat banyak dan jauh dari nilai-nilai sentimen lainnya.

Sementara itu, wordcloud leseluruhan sentimen ditunjukkan pada gambar berikut:

<img width="819" height="580" alt="image" src="https://github.com/user-attachments/assets/7f6ac87c-dc45-468e-85df-8aadd944ee0a" />

Dapat dilihat jika wordcloud leseluruhan sentimen didominasi oleh kata "aplikasi", "login", "update", "daftar" hingga "susah". Sementara itu, untuk wordcloud sentimen negatif sendiri seperti berikut ini:

<img width="819" height="580" alt="image" src="https://github.com/user-attachments/assets/842482a5-2c4f-49c4-872f-33db2d8f557e" />

Terlihat jika kata yang paling menonjol dari wordcloud di atas masih "aplikasi", namun dengan kata-kata lainnya seperti "ribet", "buruk", "error" hingga "kode otp". Sebaliknya, pada sentimen wordclout positif sendiri seperti berikut ini:

<img width="819" height="580" alt="image" src="https://github.com/user-attachments/assets/0f5e69ed-7263-4d9c-913d-190808235ffc" />

Dari wordcloud di atas tampak juga masih didominasi kata "aplikasi" namun ada kata-kata seperti "membantu", "udah", "sesuai", hingga "mudah". Pada wordclout netral terlihat seperti berikut:

<img width="819" height="580" alt="image" src="https://github.com/user-attachments/assets/7efc4322-c2d3-438a-b8ce-4e627f5660eb" />

Kata-kata pada wordclout di atas terlihat acak dan tanpa makna, seperti "root", "hp", "wkwkwk", "sistemnya" dan "verifikasi".

Berikut ini menampilkan frekuensi kata-kata yang paling sering muncul dengan bar chart.

<img width="1042" height="547" alt="image" src="https://github.com/user-attachments/assets/336abd1f-f351-4110-94ac-9d8e55281c4a" />

Terlihat jika top 20 kata-kata yang paling sering muncul adalah "aplikasi", kemudian "daftar", "verifikasi", hingga "nomor".

6. Pemodelan Analisis Sentimen:
Melakukan klasifikasi sentimen ulasan menjadi tiga kategori: positif, negatif, dan netral menggunakan algoritma Naive Bayes, Random Forest, Logistic Regression dan Decision Tree.

a. Data splitting
Dengan memisahkan fitur x dan label y, menggunakan TF-IDF Vectorizer untuk ekstraksi fitur dengan parameter max_features=200, min_df=17, max_df=0.8.
b. Pemodelan
Membangun model klasifikasi dengan menggunakan Naive Bayes, Random Forest, Logistic Regression dan Decision Tree untuk dibandingkan evaluasi hasilnya.
c. Evaluasi
Model dievaluasi menggunakan akurasi. Hasil evaluasi model menunjukkan:

```
              Model  Accuracy Test
2  Logistic Regression       0.861000
1        Random Forest       0.834333
0          Naive Bayes       0.816000
3        Decision Tree       0.774000
```
Sehingga, Logistic Regression menjadi model dengan akurasi tertinggi pada dataset ini.

> Output akhir prediksi kalimat sentimen
Model dapat digunakan untuk memprediksi sentimen dari kalimat baru secara otomatis. Contoh prediksi:
```
Masukkan kalimat baru:
perbaiki sistem bayarnya

Output:
Sentimen kalimat baru adalah NEGATIF.
```

