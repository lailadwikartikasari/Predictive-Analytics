# Laporan Proyek Machine Learning - Laila Dwi Kartika Sari 

## Domain Proyek -  Kesehatan

Perkembangan Machine Learning yang sangat pesat dapat membantu manusia dalam menyelesaikan permasalahan yang rumit dengan komputasi komputer. Pada proyek ini penulis ingin menggunakan Machine Learning untuk membantu manusia dalam perawatan kesehatan ibu Hamil.

Masa  Kehamilan  merupakan  masa  penting bagi seorang ibu, pada kondisi ini ibu harus lebih fokus untuk memelihara  kesehatan diri sendiri dikarenakan adanya calon manusia yang  akan dilahirkan. Kesehatan yang     buruk bagi ibu hamil akan mempengaruhi kesehatan janin yang dikandungnya. Kesehatan ibu hamil yang buruk  dapat  mengakibatkan kematian ibu dan anak. [[1](https://ejournal.bsi.ac.id/ejurnal/index.php/swabumi/article/view/15270/pdf)]

Faktor penting penyebab kehamilan berisiko terjadi pada kelompok ibu usia reproduksi <20 tahun dan umur >35 tahun. Kategori usia ibu kurang dari 20 tahun dianggap alat reproduksi masih terlalu muda dan belum matang, keadaan belum sempurna untuk proses kehamilan dan persalinan yang dapat membahayakan kondisi ibu serta pertumbuhan dan perkembangan janin dalam kandungan. Ibu dengan usia lebih dari 35 tahun dapat berisiko terjadinya penurunan fungsi reproduksi dan melemahnya tenaga untuk mengejan ketika proses kelahiran bayi[[2](https://jik.stikesalifah.ac.id/index.php/jurnalkes/article/view/708/pdf)]

Menjaga kesehatan kandungan selama kehamilan sangat bergantung pada beberapa faktor risiko, seperti: usia, Tekanan Darah Sistolik, DiastolikBP, BS, HeartRate. Berdasarkan permasalahan di atas, maka pada proyek ini akan dibangun suatu model machine learning untuk memprediksi risiko kesehatan ibu hamil. Dengan adanya model machine learning ini, diharapkan dapat membantu dan memudahkan analisa serta dapat mengambil keputusan yang tepat tentang strategi perawatan kesehatan dalam dunia kebidanan. Sehingga dapat meminimalisir kesalahan diagnosis dan komplikasi kehamilan di masa mendatang.

## Business Understanding

### Problem Statements

Bagaimana cara melakukan pemantauan faktor risiko seperti usia, tekanan darah, kadar gula darah, dan detak jantung untuk mencegah komplikasi pada kesehatan ibu hamil?

### Goals

Membangun model _machine learning_ untuk memprediksi risiko kesehatan ibu hamil secara cepat dan akurat berdasarkan parameter medis.

### Solution statements

Mengembangkan model machine learning yang menganalisis data ibu hamil (usia, tekanan darah, kadar gula, detak jantung, dll.) untuk mengklasifikasikan tingkat risiko kehamilan, sehingga dapat menjadi alat pendukung keputusan (decision support system) bagi bidan dan dokter.

## Data Understanding
- **Informasi Dataset**
  <br> Dataset yang digunakan pada proyek ini yaitu dataset [Maternal Health Risk Data](https://www.kaggle.com/datasets/csafrit2/maternal-health-risk-data), informasi lebih lanjut mengenai dataset tersebut dapat lihat pada tabel berikut:

Attribute  | Keterangan
------------- | -------------
Sumber | https://www.kaggle.com/datasets/csafrit2/maternal-health-risk-data
Age | Usia dalam tahun saat seorang wanita hamil.
SystolicBP | Nilai atas Tekanan Darah dalam mmHg, atribut penting lainnya selama kehamilan.
DiastolicBP | Nilai Tekanan Darah yang lebih rendah dalam mmHg, atribut penting lainnya selama kehamilan.
BS | Kadar glukosa darah dalam konsentrasi molar, mmol/L.
HeartRate | Denyut jantung normal saat istirahat dalam denyut per menit.
Risk Level | Tingkat Intensitas Risiko yang diprediksi selama kehamilan dengan mempertimbangkan atribut sebelumnya.

Berikut merupakan detail dari *dataset* yang digunakan untuk pembuatan model:
- Dataset berupa CSV
- Dataset terdiri dari 1014 *records* dengan 7 buah fitur yang diukur.
- Dataset terdiri dari 1 data kategori dan 6 data numerik.
- Dataset memiliki *data duplikat* sejumlah 562 records

**Analisis Univariat dan Analisis Multivariat, serta Visualisasi Data**:
Untuk memahami data lebih lanjut, dilakukan Analisis Univariat dan Analisis Multivariat, serta Visualisasi Data

Analisis univariat adalah metode analisis data sederhana yang fokus pada satu variabel saja. Visualisasi yang dihasilkan biasanya bertujuan untuk menunjukkan bagaimana data pada variabel tersebut terdistribusi. Sebaliknya, analisis multivariat melibatkan lebih dari dua variabel sekaligus. Tujuan visualisasinya adalah untuk mengungkap hubungan dan pola yang kompleks dalam data yang memiliki banyak dimensi.

Selain melakukan analisis data, visualisasi data menjadi langkah krusial dalam proyek ini karena mampu memberikan wawasan yang mendalam mengenai perilaku dari berbagai fitur yang ada dalam dataset. Beberapa teknik visualisasi spesifik telah diterapkan untuk tujuan ini. Pertama, catplot digunakan untuk memvisualisasikan distribusi data pada fitur-fitur yang bersifat kategorikal, memungkinkan pemahaman tentang bagaimana nilai-nilai dalam kategori tersebut tersebar. Kedua, pairplot dimanfaatkan untuk mengeksplorasi hubungan antar berbagai pasangan fitur dalam dataset, sehingga pola interaksi antar variabel dapat diidentifikasi. Terakhir, heatmap digunakan untuk menyajikan matriks korelasi antar semua fitur yang ada dalam dataset secara visual, mempermudah dalam memahami kekuatan dan arah hubungan linear antara satu fitur dengan fitur lainnya. Kombinasi teknik visualisasi ini diharapkan dapat memberikan pemahaman yang komprehensif terhadap karakteristik dan relasi dalam dataset.

Berikut adalah hasil Exploratory Data Analysis (EDA), dimana Gambar 1 merupakan EDA Analisis Univariat dan Gambar 2 merupakan EDA Analisis Multivariat.

### Gambar 1a. Analisis Univariat (Data Kategori)
![Gambar 1a - Analisis Univariat Data Kategori](https://github.com/lailadwikartikasari/Predictive-Analytics/blob/main/image/download.png)


Gambar tersebut adalah diagram batang (bar chart) yang menampilkan distribusi frekuensi untuk variabel RiskLevel. Sumbu horizontal (sumbu-x) menunjukkan kategori tingkat risiko, yaitu "low risk", "mid risk", dan "high risk". Sumbu vertikal (sumbu-y) menunjukkan jumlah atau frekuensi sampel untuk setiap kategori risiko.

Dari diagram batang tersebut, dapat diamati bahwa:
- Low risk memiliki frekuensi tertinggi, dengan jumlah sampel mendekati 195.
- Mid risk memiliki frekuensi yang lebih rendah dibandingkan "low risk", dengan jumlah sampel sekitar 65.
- High risk memiliki frekuensi paling rendah di antara ketiga kategori, dengan jumlah sampel sekitar 25.

### Gambar 1b. Analisis Univariat (Data Numerik)
![Gambar 1b - Analisis Univariat Data Numerik](https://github.com/lailadwikartikasari/Predictive-Analytics/blob/main/image/download%20(1).png)

Gambar tersebut menampilkan histogram dari enam fitur yang berbeda dalam sebuah dataset. Setiap histogram menunjukkan distribusi frekuensi nilai untuk masing-masing fitur. Mari kita analisis setiap histogram secara individual:

- Age: Histogram untuk fitur "Age" menunjukkan distribusi usia dalam dataset. Terlihat adanya beberapa puncak frekuensi, terutama di sekitar usia 20-30 tahun. Distribusi ini cenderung miring ke kanan, mengindikasikan bahwa sebagian besar sampel berada pada usia yang lebih muda, dengan frekuensi yang menurun seiring bertambahnya usia hingga sekitar 70 tahun. 
- SystolicBP: Histogram untuk "SystolicBP" (Tekanan Darah Sistolik) menunjukkan distribusi tekanan darah sistolik. Sebagian besar data terkumpul di sekitar nilai 120. Terdapat juga beberapa nilai ekstrem atau outlier dengan frekuensi rendah, terutama nilai yang sangat tinggi di atas 400 dan beberapa nilai di bawah 60.
- DiastolicBP: Histogram untuk "DiastolicBP" (Tekanan Darah Diastolik) menunjukkan distribusi tekanan darah diastolik. Distribusi ini terlihat memiliki beberapa puncak, dengan konsentrasi tertinggi di sekitar nilai 70-80. Terdapat juga beberapa nilai yang lebih rendah dan lebih tinggi dengan frekuensi yang lebih sedikit.
- BS: Histogram untuk "BS" (Kemungkinan merujuk pada Blood Sugar atau Gula Darah) menunjukkan distribusi kadar gula darah. Distribusi ini sangat miring ke kanan, dengan sebagian besar nilai terkumpul di rentang yang rendah (sekitar 6-8). Terdapat beberapa nilai yang jauh lebih tinggi dengan frekuensi yang sangat rendah, mengindikasikan adanya beberapa sampel dengan kadar gula darah yang tinggi.
- Body Temp: Histogram untuk "Body Temp" (Suhu Tubuh) menunjukkan distribusi suhu tubuh. Sebagian besar data terkumpul sangat rapat di sekitar nilai 98-99 derajat. Terdapat juga beberapa nilai yang jauh lebih tinggi di sekitar 102-103 derajat dengan frekuensi yang sangat rendah, yang mungkin mengindikasikan kondisi demam pada beberapa sampel.
- HeartRate: Histogram untuk "HeartRate" (Detak Jantung) menunjukkan distribusi detak jantung. Sebagian besar data terkumpul di sekitar nilai 80-90 denyut per menit. Terdapat juga beberapa nilai yang lebih rendah dan lebih tinggi dengan frekuensi yang lebih sedikit, termasuk beberapa nilai yang cukup tinggi di atas 140.

### Gambar 2a. Analisis Multivariat (Data Kategori dan Numerik)
![Gambar 2a - Analisis Multivariat](https://github.com/lailadwikartikasari/Predictive-Analytics/blob/main/image/download%20(2).png)

Berdasarkan gambar yang diberikan, grafik batang ini menunjukkan rata-rata 'HeartRate' (detak jantung) relatif terhadap 'RiskLevel' (tingkat risiko). Sumbu horizontal (sumbu-x) menunjukkan tiga kategori tingkat risiko: 'high risk' (risiko tinggi), 'low risk' (risiko rendah), dan 'mid risk' (risiko sedang). Sumbu vertikal (sumbu-y) menunjukkan nilai rata-rata 'HeartRate'.

Dari grafik tersebut, dapat diamati bahwa:
- Batang untuk 'high risk' menunjukkan rata-rata detak jantung sekitar 77.
- Batang untuk 'low risk' menunjukkan rata-rata detak jantung sekitar 73.
- Batang untuk 'mid risk' menunjukkan rata-rata detak jantung sekitar 74.

### Gambar 2b. Analisis Multivariat (Data Numerik dan Numerik)
![Gambar 2b - Analisis Multivariat](https://github.com/lailadwikartikasari/Predictive-Analytics/blob/main/image/download%20(3).png)

Tentu, mari kita analisis gambar pair plot ini. Gambar ini menyajikan visualisasi hubungan antara beberapa variabel numerik dalam sebuah dataset. Setiap variabel dibandingkan dengan variabel lainnya dalam bentuk scatter plot, dan distribusi univariat dari setiap variabel ditampilkan di diagonal.

Berikut adalah penjelasan untuk setiap bagian dari pair plot:

Diagonal (Histogram/KDE):
- Age: Distribusi usia terlihat sedikit miring ke kanan (positively skewed), dengan sebagian besar data terkumpul di usia sekitar 20-40 tahun. Ada juga beberapa individu dengan usia lebih tua hingga sekitar 70 tahun.
- SystolicBP (Tekanan Darah Sistolik): Distribusinya terlihat multimodal atau setidaknya memiliki dua puncak, menunjukkan kemungkinan adanya kelompok dengan tekanan darah sistolik yang berbeda. Sebagian besar data berada di sekitar nilai 100-140.
- DiastolicBP (Tekanan Darah Diastolik): Distribusinya juga terlihat multimodal, dengan sebagian besar data terkumpul di sekitar nilai 60-90.
- BS (Gula Darah): Distribusi gula darah sangat miring ke kanan (positively skewed), dengan sebagian besar nilai terkumpul di rentang rendah (sekitar 5-10), dan beberapa nilai ekstrem yang lebih tinggi.
- BodyTemp (Suhu Tubuh): Distribusi suhu tubuh terlihat mendekati normal, dengan sebagian besar data terkumpul di sekitar 98-100 derajat.
- HeartRate (Detak Jantung): Distribusi detak jantung terlihat sedikit miring ke kanan, dengan sebagian besar data terkumpul di sekitar 60-80 denyut per menit.

Off-Diagonal (Scatter Plots):

Setiap scatter plot di luar diagonal menunjukkan hubungan antara dua variabel yang berbeda. Mari kita lihat beberapa pola yang mungkin terlihat:

- Age vs. Variabel Lain: Tidak terlihat korelasi linear yang kuat antara usia dengan variabel tekanan darah (SystolicBP, DiastolicBP), gula darah (BS), suhu tubuh (BodyTemp), atau detak jantung (HeartRate). Namun, kita bisa melihat sebaran data yang lebih luas pada beberapa variabel seiring bertambahnya usia.
- Tekanan Darah (SystolicBP vs. DiastolicBP): Terdapat korelasi positif yang cukup kuat antara tekanan darah sistolik dan diastolik. Artinya, cenderung individu dengan tekanan darah sistolik yang lebih tinggi juga memiliki tekanan darah diastolik yang lebih tinggi.
- Tekanan Darah vs. Variabel Lain: Tidak terlihat pola linear yang jelas antara tekanan darah (sistolik atau diastolik) dengan gula darah, suhu tubuh, atau detak jantung.
- BS (Gula Darah) vs. Variabel Lain: Tidak terlihat korelasi linear yang kuat antara gula darah dengan usia, tekanan darah, suhu tubuh, atau detak jantung. Namun, karena distribusi gula darah sangat miring, sulit untuk menarik kesimpulan tentang hubungan linear dari scatter plot saja.
- BodyTemp (Suhu Tubuh) vs. Variabel Lain: Tidak terlihat korelasi linear yang kuat antara suhu tubuh dengan variabel lainnya. Sebaran data terlihat cukup homogen.
- HeartRate (Detak Jantung) vs. Variabel Lain: Tidak terlihat korelasi linear yang kuat antara detak jantung dengan usia, tekanan darah, gula darah, atau suhu tubuh.

### Gambar 3a. Analisis Matrix Korelasi
![Gambar 3a - Matrix Korelasi](https://github.com/lailadwikartikasari/Predictive-Analytics/blob/main/image/download%20(4).png)

## Data Preparation
Berikut ini merupakan tahapan-tahapan dalam melakukan pra-pemrosesan data:

1. **Melakukan Penanganan Duplikat dan Outlier**
    <br> Penanganan yang penulis lakukan pada Duplikat yaitu dengan melakukan drop data dan untuk mengatasi outlier pada proyek, penulis menggunakan penentuan batas atas dan bawah nilai kuartil pada data dengan menggunakan metode IQR.
2. **Melakukan Encoding Data Kategori**
    <br> Encoding adalah proses mengubah data kategori (teks atau label) menjadi bentuk numerik atau format lain yang bisa diproses oleh komputer atau algoritma. [Encoding](https://www.geeksforgeeks.org/ml-one-hot-encoding/)
3. **Melakukan Reduksi Dimensi dengan PCA**
    <br> Teknik mereduksi jumlah fitur dilakukan proses PCA. Teknik reduksi ini adalah prosedur yang mengurangi jumlah fitur dengan tetap mempertahankan informasi pada data. PCA ini adalah teknik untuk mereduksi dimensi, mengekstraksi fitur, dan mentransformasi data.
4. **Melakukan Train-Test Split**
    <br> Untuk mengetahui kinerja model ketika dihadapkan pada data yang belum pernah dilihat sebelumnya, maka perlu dilakukan pembagian dataset. Pada proyek ini dataset dibagi menjadi data latih dan data uji dengan rasio 90% untuk data latih dan 10% untuk data uji. Data latih merupakan data yang akan kita latih untuk membangun model _machine learning_, sedangkan data uji merupakan data yang belum pernah dilihat oleh model dan digunakan untuk melihat kinerja atau performa dari model yang dilatih.  Pembagian dataset dilakukan dengan modul [train_test_split](https://scikit-learn.org/0.24/modules/generated/sklearn.model_selection.train_test_split.html#sklearn.model_selection.train_test_split) dari scikit-learn. Setelah melakukan pembagian dataset, didapatkan jumlah sample pada data latih yaitu 912 sampel dan jumlah sample pada data uji yaitu 102 sampel dari total jumlah sample pada dataset yaitu 1014 sampel.
5. **Standardisasi data pada semua fitur numerik pada dataset**
  <br> Standardisasi merupakan teknik transformasi yang paling umum digunakan dalam tahap data _preparation_. Standardisasi membantu untuk membuat semua fitur numerik berada dalam skala data yang sama dan membuat fitur data menjadi bentuk yang lebih mudah diolah oleh algoritma. Pada proyek ini, standardisasi data dilakukan dengan menerapkan teknik [StandarScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html) dari library Scikitlearn. StandardScaler melakukan proses standardisasi fitur dengan mengurangkan mean (nilai rata-rata) kemudian membaginya dengan standard deviasi untuk menggeser distribusi.  StandardScaler menghasilkan distribusi dengan standard deviasi sama dengan 1 dan mean sama dengan 0. Sekitar 68% dari nilai akan berada di antara -1 dan 1.

## Modeling
Pada proyek ini, Proses modeling dalam proyek ini menggunakan 3 algoritma _machine learning_ yaitu `K-Nearest Neighbor`, `Random Forest` dan `Boosting Algorithm` kemudian membandingkan performanya.

### **K-Nearest Neighbor**
<br> KNN bekerja dengan membandingkan jarak satu sampel ke sampel pelatihan lain dengan memilih sejumlah k tetangga terdekat (dengan k adalah sebuah angka positif). Pada tahap ini pembuatan model dilakukan dengan menggunakan modul [KNeighborsRegressor](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsRegressor.html) dari library Scikitlearn.  

Dengan parameter:
```
knn = KNeighborsRegressor(n_neighbors=10)
```
 pada model ini akan membandingkan jarak satu sampel data ke 10 sampel data tetangganya yang terdekat, agar hasil persamaan regresi yang dihasilkannya nantinya akan lebih halus, tahapan itu akan dilakukan berulang-ulang hingga mendapatkan hasil persamaan regersi dengan nilai yang maksimal. Kemudian proses selanjutnya melakukan prediksi menggunakan data uji dan melakukan pengujian.
-   Kelebihan:
    -   Algoritma KNN merupakan algoritma yang sederhana dan mudah untuk diimplementasikan.
    -   Algoritma KNN dapat di implementasikan pada beberapa kasus seperti klasifikasi, regresi dan pencarian.
-   Kekurangan:
    -   Algoritma KNN menjadi lebih lambat secara signifikan seiring meningkatnya jumlah sampel dan/atau variabel independen.

### **Random Forest**
<br> Algoritma ini disusun dari banyak algoritma pohon (decision tree) yang pembagian data dan fiturnya dipilih secara acak. Pembuatan model dilakukan dengan menggunakan modul [RandomForestRegressor](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestRegressor.html) dari library Scikitlearn. 
  
 Dengan Parameter:
```
RF = RandomForestRegressor(n_estimators=50, max_depth=16, random_state=55, n_jobs=-1)
```
*n_estimators=50* Jumlah pohon keputusan (decision trees) dalam model Random Forest. Lebih banyak pohon biasanya meningkatkan kinerja tetapi juga meningkatkan kompleksitas dan waktu pelatihan. *max_depth=16* Kedalaman maksimum setiap pohon keputusan. Ini membatasi seberapa banyak pohon dapat bercabang, membantu mencegah overfitting. *random_state=55* Untuk memastikan bahwa hasil yang sama diperoleh setiap kali kode dijalankan, dengan mengontrol pengacakan dalam proses pembuatan pohon. *n_jobs=-1* Menggunakan semua inti prosesor yang tersedia untuk mempercepat pelatihan mode agar hasil dapat maksimal.
-   Kelebihan :
    -   Algoritma Random Forest merupakan algoritma dengan pembelajaran paling akurat yang tersedia. Untuk banyak kumpulan data, algoritma ini menghasilkan pengklasifikasi yang sangat akurat.
    -   Berjalan secara efisien pada data besar.
    -   Dapat menangani ribuan variabel input tanpa penghapusan variabel.
    -   Memberikan perkiraan variabel apa yang penting dalam klasifikasi.
    -   Memiliki metode yang efektif untuk memperkirakan data yang hilang dan menjaga akurasi ketika sebagian besar data hilang.
-   Kekurangan :
    -   Algoritma Random Forest overfiting untuk beberapa kumpulan data dengan tugas klasifikasi/regresi yang _bising/noise_.
    -   Untuk data yang menyertakan variabel kategorik dengan jumlah level yang berbeda, Random Forest menjadi bias dalam mendukung atribut dengan level yang lebih banyak. Oleh karena itu, skor kepentingan variabel dari Random Forest tidak dapat diandalkan untuk jenis data ini.

### **Boosting Algorithm**
<br> Algoritma ini bekerja dengan membangun model dari data latih. Kemudian ia membuat model kedua yang bertugas memperbaiki kesalahan dari model pertama. Model ditambahkan sampai data latih terprediksi dengan baik atau telah mencapai jumlah maksimum model untuk ditambahkan. Pada tahap ini pembuatan model dilakukan dengan menggunakan modul [Boosting Alghoritm](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.AdaBoostClassifier.html) dari library Scikitlearn. 

 Dengan Parameter:
```
boosting = AdaBoostRegressor(learning_rate=0.05, random_state=55)
```
*learning_rate=0.05* Mengontrol seberapa besar kontribusi setiap pohon baru terhadap model. Nilai yang lebih kecil menghasilkan pembelajaran yang lebih lambat tetapi berpotensi meningkatkan kinerja. *random_state=55* Untuk memastikan hasil yang konsisten dengan mengontrol pengacakan dalam proses boosting.
-   Kelebihan :
    -   Algoritma Boosting dapat mengurangi bias pada data.
    -   Prosedur Boosting cukup sederhana.
    -   Algoritma ini sangat powerful dalam meningkatkan akurasi prediksi.
    -   Algoritma boosting sering mengungguli model yang lebih sederhana seperti logistic regression dan random forest.
-   Kekurangan :
    -   AdaBoost sangat dipengaruhi oleh outlier.

## Evaluation
Pada proyek ini, metrik evaluasi yang digunakan untuk mengukur kinerja model yaitu menggunakan metrik  **MSE**.MSE sendiri merupakan _Mean Squared Error_ yang menghitung jumlah selisih kuadrat rata-rata nilai sebenarnya dengan nilai prediksi. MSE didefinisikan dalam persamaan berikut: <br>
<image src='https://www.pythonpool.com/wp-content/uploads/2021/08/20210812_200937_0000-1024x270.png' width= 500/>
<br> Keterangan:
- N = jumlah dataset
- yi = nilai sebenarnya
- yi^ = nilai prediksi

Sebelum menggunakan metrik MSE, harus dilakukan scaling fitur numerik terlebih dahulu pada data uji untuk menghindari kebocoran data. Setelah melakukan evaluasi berdasarkan metrik MSE.

Tabel 1 berikut merupakan perbandingan 3 buah model yang coba dibandingkan dengan data uji dan data latih:
|     |train|test|
|---|---|---|
|KNN|0.030923|0.106557|
|RF|0.003346|0.103572|
|Boosting|0.050693|0.091678|

Perbandingan Performa Model:
- Random Forest (RF) memiliki MSE terendah di data latih (0.003346), menunjukkan kemampuan fitting yang sangat baik.
- Boosting unggul di data uji (MSE = 0.091678), menandakan generalisasi yang lebih baik dibanding model lain.
- KNN memiliki error tertinggi di data uji (0.106557), mungkin karena overfitting atau sensitivitas terhadap noise.

Berikut ini perbandingan grafik metrik MSE pada ketiga model:
<br>
![Gambar Model](https://github.com/lailadwikartikasari/Predictive-Analytics/blob/main/image/evaluasi.png)

Berdasarkan Gambar diatas dapat disimpulkan bahwa nilai error train dan test dari Model 3 dan Model Boosting jauh lebih baik dibandingkan model lainnya.

|     |y_true|prediksi_KNN|prediksi_RF|prediksi_Boosting|
|---|---|---|---|---|
|50|66|75.4|75.5|73.8|

Berdasarkan hasil evaluasi, terlihat bahwa prediksi tingkat risiko kehamilan dengan model Boosting memberikan hasil yang paling mendekati nilai sebenarnya (y_true = 50), dimana prediksi Boosting menghasilkan nilai 73.8. Meskipun ketiga model (KNN, RF, dan Boosting) memberikan prediksi di atas nilai aktual, model Boosting menunjukkan performa terbaik dengan selisih yang paling kecil terhadap y_true. Dengan demikian, dapat disimpulkan bahwa model Boosting Regressor yang telah dikembangkan mampu memprediksi dengan akurasi yang lebih baik dibandingkan model lainnya dalam kasus ini.


**---Ini adalah bagian akhir laporan---**
