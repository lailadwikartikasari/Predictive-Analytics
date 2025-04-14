# Laporan Proyek Machine Learning - Laila Dwi Kartika Sari 

## Domain Proyek -  Kesehatan

Perkembangan Machine Learning yang sangat pesat dapat membantu manusia dalam menyelesaikan permasalahan yang rumit dengan komputasi komputer. Pada proyek ini penulis ingin menggunakan Machine Learning untuk membantu manusia dalam perawatan kesehatan ibu Hamil.

Masa  Kehamilan  merupakan  masa  penting bagi seorang ibu, padakondisi ini ibu harus lebih fokus untuk memelihara  kesehatan diri sendiri dikarenakan adanya calon manusia yang  akan dilahirkan.Kesehatan yang     buruk bagi ibu hamil akan mempengaruhi kesehatan janin yang dikandungnya.Kesehatan ibu hamil yang buruk  dapat  mengakibatkan kematian ibu dan anak. [[1](https://ejournal.bsi.ac.id/ejurnal/index.php/swabumi/article/view/15270/pdf)]

Faktor penting penyebab kehamilan berisiko terjadi pada kelompok ibu usia reproduksi <20 tahun dan umur >35 tahun. Kategori usia ibu kurang dari 20 tahun dianggap alat reproduksi masih terlalu muda dan belum matang, keadaan uterus belum sempurna untuk proses kehamilan dan persalinan yang dapat membahayakan kondisi ibu serta pertumbuhan dan perkembangan janin dalam kandungan.Ibu dengan usia lebih dari 35 tahun dapat berisiko terjadinya penyulit disebabkan penurunan fungsi reproduksi dan melemahnya tenaga untuk mengejan ketika proses kelahiran bayi[[2](https://jik.stikesalifah.ac.id/index.php/jurnalkes/article/view/708/pdf)]

Menjaga kesehatan kandungan selama kehamilan sangat bergantung pada beberapa faktor risiko, seperti: usia, Tekanan Darah Sistolik, DiastolikBP, BS, HeartRate. Berdasarkan permasalahan di atas, maka pada proyek ini akan dibangun suatu model machine learning untuk memprediksi risiko kesehatan ibu hamil. Dengan adanya model machine learning ini, diharapkan dapat membantu dan memudahkan analisa serta dapat mengambil keputusan yang tepat tentang strategi perawatan kesehatan dalam dunia kebidanan. Sehingga dapat meminimalisir kesalahan diagnosis dan komplikasi kehamilan di masa mendatang. Kemudian untuk tahap pengembangan selanjutnya, diharapkan implementasi dari model ini dapat dijalankan pada sebuah aplikasi berbasis web ataupun android nantinya, yang dapat digunakan oleh tenaga medis maupun ibu hamil untuk memantau kondisi kehamilan secara berkala.

## Business Understanding

### Problem Statements

Menjelaskan pernyataan masalah latar belakang:
- Bagaimana cara melakukan pra-pemrosesan data tingkat risiko kesehatan ibu hamil sehingga dapat digunakan untuk membuat model yang baik?
- Bagaimana mengolah dataset agar dapat dibuat menjadi model prediksi tingkat risiko kesehatan ibu hamil yang akurat?

### Goals

Menjelaskan tujuan dari pernyataan masalah:
- Melakukan pra-pemrosesan data tingkat risiko kesehatan ibu hamil agar dapat digunakan dalam membangun model.
- Melakukan proses data wragling dan data preparation terhadap dataset agar dapat dibuat model predksi tingkat risiko kesehatan ibu hamil yang akurat.

### Solution statements
- **Pra-pemrosesan Data**. Pada pra-pemrosesan data dapat dilakukan beberapa tahapan, antara lain:
  
    -   Melakukan perhitungan dataset berdasarkan data: Age, SystolicBP, DiastolicBP, BS, BodyTemp, HeartRate, RiskLevel.
    -   Melakukan pembagian dataset.
    -   Mengatasi data pencilan (_outliers_) dengan Metode IQR.
    -   Standardisasi data fitur numerik pada dataset.
    
- Agar didapatkan model prediksi yang baik maka dilakukan proses Data Wragling yang meliputi Data Gathering, Data Assessing, dan Data Cleaning.

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

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

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

