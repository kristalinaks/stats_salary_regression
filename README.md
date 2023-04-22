# Salary Prediction Using Regression Model

## 1. Pengantar dan Latar Belakang
Terdapat sebuah dataset yang menunjukkan gaji yang dimiliki seseorang berdasarkan usia, jenis kelamin, tingkat pendidikan, jabatan, dan lama pengalaman kerja. Dari dataset tersebut, penulis ingin mengetahui pengaruh dari faktor-faktor tersebut terhadap gaji dan melakukan prediksi gaji seseorang.
- Menguji pengaruh jenis kelamin terhadap gaji dengan uji statistik
- Memprediksi gaji dari lama pengalaman kerja seseorang dengan model regresi
- Memprediksi gaji dari variabel prediktor usia, jenis kelamin, tingkat pendidikan, dan lama pengalaman kerja dengan model regresi

## 2. Dataset
Dataset yang digunakan diambil dari kaggle.com. Dataset berisikan 375 baris data usia, jenis kelamin, tingkat pendidikan, jabatan, lama pengalaman kerja, dan besar gaji.
Sebelum diolah lebih lanjut, dilakukan persiapan dengan menghapus missing value dan duplicated data sehingga didapatkan 324 baris data yang bisa digunakan. \
Data Job Title tidak akan digunakan dalam pemodelan regresi karena terlalu bervariasi. \
Data jenis kelamin (Gender) akan diubah dari data kategorikal menjadi data numerik dengan Male = 0 dan Female = 1. \
Data tingkat pendidikan (Education Level) akan diubah dari data kategorikal menjadi data numerik dengan Bachelor’s = 0, Master’s = 1, dan PhD = 2. \
Link: https://www.kaggle.com/datasets/rkiattisak/salaly-prediction-for-beginer

## 3. Regression Model
### 3.1. Single Predictor
Dilakukan pemodelan regresi untuk memprediksi gaji seseorang dari lama pengalaman kerjanya.
Dari hasil tersebut didapatkan persamaan regresi berikut dengan R-squared yang cukup baik yaitu 0,85.

### 3.2. Single Predictor with Log Transformation
Dilakukan pemodelan regresi untuk memprediksi gaji seseorang dari lama pengalaman kerjanya namun dilakukan transformasi logaritmik pada variabel prediktor.
Didapatkan hasil R-squared sebesar 0,76. Hasil ini lebih rendah dari hasil R-squared 0,85 pada pemodelan tanpa transformasi logaritmik. Sehingga untuk pemodelan regresi dengan satu variabel prediktor, digunakan model regresi tanpa transformasi.

### 3.3. Multiple Predictors with One Interaction
Dalam pemodelan ini, digunakan semua variabel prediktor yaitu usia, jenis kelamin, tingkat pendidikan, dan lama pengalaman kerja. Ditambahkan juga satu interaksi antar variabel prediktor yaitu usia dan lama pengalaman kerja. Untuk variabel tingkat pendidikan (Education Level) diperlakukan sebagai variabel kategorikal.
Didapatkan R-squared rata-rata sebesar 0,88 yang berarti model ini baik dan dapat menjelaskan 88% variansi gaji.
Hasil intercept negatif kurang baik karena kurang dapat menghasilkan interpretasi yang baik (gaji tidak mungkin negatif) dan usia kerja seseorang biasanya tidak dimulai dari nol. Oleh karena itu dilakukan centering variabel usia (age).

#### Centering Variabel Usia (Age)
Digunakan rata-rata usia pada dataset (37 tahun) sebagai acuan. Sehingga data usia akan dihitung dari jaraknya terhadap usia 37 tahun.
Didapatkan R-squared rata-rata sebesar 0,89 yang berarti model ini baik dan dapat menjelaskan 89% variansi gaji.

#### Interpretasi tingkat pendidikan
Jika membandingkan dua orang yang memiliki usia, jenis kelamin, lama pengalaman kerja yang sama, gaji seseorang dengan tingkat pendidikan Master’s diperkirakan lebih tinggi 19574 dollar daripada gaji seseorang dengan tingkat pendidikan Bachelor’s.

#### Interpretasi usia
Jika membandingkan dua orang yang memiliki jenis kelamin dan tingkat pendidikan yang sama, serta pengalaman kerja 0 tahun, seseorang yang usianya 1 tahun lebih tua dari 37 tahun diperkirakan memiliki gaji lebih tinggi 3042 dollar daripada seseorang berusia 37 tahun.

#### Interpretasi jenis kelamin
Jika membandingkan dua orang yang memiliki usia, lama pengalaman kerja, dan tingkat pendidikan yang sama, perempuan diperkirakan memiliki gaji lebih sedikit 9311 dollar dibandingkan laki-laki.

#### Interpretasi lama pengalaman kerja
Jika membandingkan dua orang berusia 37 tahun yang memiliki jenis kelamin dan tingkat pendidikan yang sama, seseorang dengan lama pengalaman kerja lebih lama 1 tahun diperkirakan memiliki gaji lebih tinggi 2561 dollar.

#### Interpretasi intercept
Seorang laki-laki yang berusia 37 tahun dengan tingkat pendidikan Bachelor’s tanpa pengalaman kerja diperkirakan memiliki gaji sebesar 68396 dollar.

## 5. Kesimpulan dan Rekomendasi
Dapat disimpulkan bahwa usia, jenis kelamin, lama pengalaman kerja, dan tingkat pendidikan berpengaruh terhadap besaran gaji seseorang sehingga bisa digunakan untuk memprediksi besaran gaji tersebut.

Model regresi yang dibangun dengan single predictor yaitu lama pengalaman kerja menghasilkan performa yang cukup bagus dengan R-squared 0,85. Transformasi logaritmik pada model ini tidak menghasilkan model yang lebih baik karena memiliki skor R-squared lebih rendah yaitu 0,76.

Model regresi yang dibangun dengan semua predictor disertai interaksi antara usia dan lama pengalaman kerja, menghasilkan performa yang lebih baik dengan R-squared 0,89. Model tersebut juga menghasilkan interpretasi yang baik dengan dilakukannya centering pada variabel usia (age).

Untuk pengembangan selanjutnya dapat dilakukan percobaan untuk berbagai variasi jumlah predictor yang digunakan. Dapat juga dilakukan pengelompokan data gaji berdasarkan industrinya sehingga didapatkan model regresi yang akurat untuk masing-masing industri.

## 6. Referensi
Statistics for Business : Decision Making and Analysis — Robert Stine and Dean Foster

Regression and Other Stories. — Andrew Gelman, Jennifer Hill, and Aki Vehtari

The Effect: An Introduction to Research Design and Causality. Chapter 13 Huntington-Klein, N. 2021
