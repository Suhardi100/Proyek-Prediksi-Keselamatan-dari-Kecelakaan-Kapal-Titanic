# Laporan Proyek Prediksi Keselamatan Penumpang Kapal Titanic - Suhardi

## Project Overview

- Proyek prediksi tingkat keberlangsungan hidup penumpang kapal Titanic menggunakan data historis merupakan upaya pemanfaatan teknologi analitik untuk memahami pola penyintas dalam tragedi tersebut. Dengan menggunakan dataset Titanic yang mencakup informasi seperti usia, jenis kelamin, kelas tiket, dan status keluarga, analisis ini tidak hanya menjadi tantangan pemodelan data, tetapi juga memberikan wawasan tentang bagaimana faktor sosial dan demografis memengaruhi kemungkinan bertahan hidup. Melalui proyek ini, penerapan algoritma pembelajaran mesin dapat membantu meningkatkan kemampuan prediksi berbasis data dalam situasi darurat.
- Masalah prediksi tingkat keberlangsungan hidup penumpang Titanic relevan untuk dipelajari karena pemahaman ini dapat digunakan dalam konteks yang lebih luas, seperti perencanaan evakuasi bencana, pengelolaan risiko, atau pengambilan keputusan berbasis data dalam situasi darurat. Masalah ini dapat diselesaikan dengan mengolah dataset Titanic menggunakan teknik analitik data dan algoritma pembelajaran mesin. Prosesnya melibatkan eksplorasi data untuk memahami pola, pembersihan data untuk mengatasi nilai yang hilang atau tidak sesuai, dan pembangunan model prediksi. Evaluasi model dilakukan untuk memastikan prediksi akurat, dengan hasil akhirnya berupa sistem yang mampu memprediksi kemungkinan bertahan hidup berdasarkan karakteristik penumpang.
  
## Business Understanding

Tragedi tenggelamnya kapal Titanic pada tahun 1912 menimbulkan banyak pertanyaan mengenai faktor-faktor yang memengaruhi kemungkinan bertahan hidup para penumpangnya. 

### Problem Statements

Berdasarkan dataset historis, muncul beberapa permasalahan utama:
- Apa saja variabel utama (seperti usia, jenis kelamin, kelas tiket) yang memengaruhi tingkat keberlangsungan hidup?
- Sejauh mana suatu algoritma pembelajaran mesin dapat digunakan untuk membuat prediksi yang akurat berdasarkan data tersebut?

### Goals

Tujuan dari pengerjaan proyek ini adalah:
- Mengidentifikasi dan memahami variabel-variabel yang memiliki dampak signifikan terhadap kelangsungan hidup penumpang Titanic.
- Mengembangkan model prediksi yang akurat menggunakan algoritma pembelajaran mesin.
- Memberikan wawasan yang dapat diaplikasikan dalam konteks lain, seperti mitigasi risiko dalam situasi darurat.
- Mendemonstrasikan kemampuan analitik data dan penerapan pembelajaran mesin untuk menyelesaikan masalah berbasis data historis.

### Solution statements
    Solusi dari permasalahan ini adalah dengan penggunaan algoritma machine learning mulai dari yang konvensional hingga yang modern.
    - Algoritma K-NN (K-Nearest Neighboor) dengan pencarian tertangga terdekat yang terbaik.
    - Algoritma Random Forest Classifier yang setelah itu kemudian dilakukan tuning terhadap beberapa pilihan parameternya. 
    - Algoritma XGBoost Classifier yang setelah itu dilakukan tuning terhadap beberapa pilihan parameternya.
    - Keberhasilan masing-masing algoritma di atas diukur dengan akurasi dan confussion matrix. Solusi dikatakan berhasil apabila masing-masing matrix penilian di atas sudah melebihi 80 persen. 

## Data Understanding
Dataset Titanic diunduh dari [Kaggle dengan nama akun Data Science Dojo](https://raw.githubusercontent.com/datasciencedojo/datasets/refs/heads/master/titanic.csv)
Dataset Titanic memiliki 12 kolom: PassengerId, Survived, Pclass, Name, Sex, Age, SibSp, Parch, Ticket, Fare, Cabin, dan Embarked. Dari 12 kolom tersebut, kolom yang tidak digunakan karena tidak memiliki keterkaitan langsung secara logis adalah kolom PassengerId, Name, Ticket, dan Embarked. Sedangkan, kolom fiturnya adalah kolom Pclass, Sex, Age, SibSp, Parch, Fare, dan Cabin serta kolom targetnya adalah Survived.
Dataset ini terdiri dari 891 baris data, tetapi tidak semua terisi dengan data, masih terdapat banyak baris-baris yang kosong sebagai berikut ini.
- Kolom Age sebanyak 177 baris datanya kosong.
- Kolom Cabin sebanyak 687 baris datanya kosong.
- Kolom Embarked sebanyak 2 baris datanya kosong.
- Kolom Fare ada 15 baris yang bernilai 0. 
Setelah dilakukan pengecekan lebih lanjut terhadap baris yang berisi data duplikat diperoleh hasil 0, artinya pada dataset ini tidak terdapat baris yang duplikat.
Penulisan data pada setiap barisnya pada kolom-kolom fitur maupun target yang digunakan sudah konsisten sehingga tidak perlu pembersihan data lebih lanjut.

Variabel-variabel pada Kaggle dengan nama akun Data Science Dojo adalah sebagai berikut:
- PassengerId: Nomor unik untuk mengidentifikasi setiap penumpang. Kolom ini bertipe data int64.
- Survived: Indikator kelangsungan hidup (0 = tidak selamat, 1 = selamat). Kolom ini bertipe data int64.
- Pclass: Kelas tiket penumpang (1 = kelas utama, 2 = kelas menengah, 3 = kelas ekonomi). Kolom ini bertipe data int64.
- Name: Nama lengkap penumpang. Kolom ini bertipe data object.
- Sex: Jenis kelamin penumpang (male = laki-laki, female = perempuan). Kolom ini bertipe data object.
- Age: Usia penumpang dalam tahun (dapat berupa nilai kosong). Kolom ini bertipe data float64.
- SibSp: Jumlah saudara kandung atau pasangan yang ikut serta di kapal. Kolom ini bertipe data int64.
- Parch: Jumlah orang tua atau anak yang ikut serta di kapal. Kolom ini bertipe data int64.
- Ticket: Nomor tiket yang dimiliki penumpang. Kolom ini bertipe data object.
- Fare: Harga tiket yang dibayarkan oleh penumpang. Kolom ini bertipe data float64.
- Cabin: Nomor kabin tempat tinggal penumpang (banyak nilai kosong). Kolom ini bertipe data object.
- Embarked: Pelabuhan keberangkatan penumpang (C = Cherbourg, Q = Queenstown, S = Southampton). Kolom ini bertipe data object.

Beberapa teknik yang digunakan untuk mengetahui gambaran tentang data secara lebih menyeluruh adalah sebagai berikut ini:
- Menggunakan built-in function ".info()" untuk memberikan ringkasan informasi tentang struktur dataset.
- Menggunakan built-in function ".describe()" untuk memberikan statistik deskriptif untuk kolom numerik.
- Menggunakan percabangan/kondisional untuk mengecek masing-masing data yang bernilai nol.
- Membuat visualisasi terhadap kemunculan setiap kategori pada setiap kolom.

### Pembahasan Hasil Visualisasi
Wawasan yang bisa diambil dari diagram batang frekuensi pada setiap kolom adalah sebagai berikut ini.
1. Frekuensi Kolom "Survived" (Selamat).
   proporsi penumpang yang selamat sangat kecil, ini menunjukkan bahwa bencana yang terjadi di Titanic sangat fatal dan mayoritas penumpang tidak berhasil bertahan hidup.
2. Frekuensi Kolom "Sex" (Jenis Kelamin).
   Diagram batang ini menunjukkan distribusi jenis kelamin penumpang (pria dan wanita). Diperoleh wawasan bahwa lebih banyak penumpang pria daripada wanita.
3. Frekuensi Kolom "Pclass" (Kelas).
   Kolom Pclass menunjukkan kelas sosial penumpang (1, 2, atau 3). Diagram batang frekuensi di sini akan menunjukkan seberapa banyak penumpang yang ada di setiap kelas. Kelas 3 akan memiliki jumlah penumpang yang lebih banyak, karena lebih banyak penumpang berada di kelas ekonomi. Sementara itu, kelas 1 dan 2 akan memiliki jumlah penumpang yang lebih sedikit.
4. Frekuensi Kolom "Age" (Usia).
   Meskipun kolom ini cenderung memiliki banyak nilai yang hilang atau kosong, tetapi sudah dilakukan proses pengisian dengan metode KNN. Setelah dilakukan pengisian diperoleh wawasan bahwa penumpang terbanyak adalah penumpang yang berusia dewasa kemudian diikuti secara berturut-turut dari yang paling banyak jumlahnya adalah penumpang yang berusia remaja, tua, ananak-anak, lalu manula.
5. Frekuensi Kolom "SibSp" (Jumlah Saudara atau Pasangan di Kapal).
   Kolom ini menunjukkan berapa banyak saudara atau pasangan penumpang yang ikut dalam perjalanan Titanic. Diagram batang ini dapat memperlihatkan bahwa penumpang yang membawa keluarga mereka dalam perjalanan ini lebih banyak daripada yang tidak membawa.
6. Frekuensi Kolom "Parch" (Jumlah Orang Tua atau Anak di Kapal).
   Kolom ini menunjukkan jumlah orang tua atau anak yang ikut bersama penumpang. Seperti kolom SibSp, ini memberi gambaran tentang penumpang yang bepergian dengan keluarga. Dari diagram batang tersebut menunjukkan bahwa paling banyak tidak membawa orang tua atau anak-anak dalam perjalanan ini, lalu diikuti yang hanya membawa 1 atau 2, dan yang paling sedikit yang membawa lebih dari 2 orang tua atau anak-anak.
7. Frekuensi Kolom "Fare" (Harga Tiket).
   Kolom ini menunjukkan harga tiket yang dibayar penumpang. Meskipun ini bukan kolom kategori, jika diubah menjadi kategori ("murah", "medium", "mahal", dan kelas khusus), bisa terlihat distribusi harga tiket yang dibayar penumpang. Wawasan yang diperoleh bahwa penumpang yang membeli tiket dengan harga murah paling banyak kemudian secara berturut-turut dari yang paling banyak adalah medium, kelas khusus, kemudian yang paling sedikit yang membeli tiket dengan harga yang mahal.
8. Frekuensi Kolom "Cabin" (Kabin).
   Kolom ini menunjukkan kabin tempat penumpang duduk. Banyak nilai yang kosong pada kolom ini yang selanjutnya dikategorikan sebagai tidak diketahui tempat duduknya, bagian ini yang paling banyak. Kemudian secara berturut-turut diikuti dari yang terbanyak adalah kelas atas, kelas menengah, dan yang paling sedikit adalah kelas bawah.  
   
## Data Preparation
Teknik data preparation yang dilakukan untuk mempersiapkan data yang akan digunakan untuk pelatihan model adalah sebagai berikut ini.
- Menghapus kolom yang tidak diperlukan: Kolom seperti PassengerId, Name, Ticket, dan Embarked dihapus karena tidak memberikan informasi yang berguna untuk model prediksi, sehingga hanya menyisakan kolom yang relevan untuk analisis dan pelatihan model.
- Mengganti nilai 0 dengan null pada kolom Fare: Nilai 0 pada kolom Fare diartikan sebagai data yang hilang atau tidak valid, sehingga diganti dengan null (NaN) agar dapat diisi dengan teknik imputasi yang sesuai.
- Mengisi data yang kosong pada kolom Age, Cabin, dan Fare: Kolom yang memiliki nilai kosong (null) seperti Age, Cabin, dan Fare diisi menggunakan metode imputasi untuk memastikan tidak ada nilai yang hilang, yang dapat mempengaruhi kualitas model.
- Mengelompokkan nilai pada kolom Cabin, Age, SibSp, Parch, dan Fare: Kolom Cabin dikelompokkan berdasarkan kondisi tertentu karena struktur datanya sulit untuk dibinning, sementara kolom Age, SibSp, Parch, dan Fare dikelompokkan dengan sistem binning untuk membagi data ke dalam kategori yang lebih terstruktur.
- Encoding kolom-kolom non-numerik: Kolom non-numerik seperti Sex, Cabin, dan Age diubah menjadi format numerik menggunakan teknik encoding seperti Label Encoding atau One-Hot Encoding, agar dapat digunakan dalam model machine learning yang memerlukan input numerik.
- Mendefinisikan fitur dan target serta membagi data menjadi data latih dan data uji: Fitur (X) dan target (y) dipisahkan, dan data kemudian dibagi menjadi set pelatihan dan set pengujian (training dan testing set), untuk memastikan model dapat dilatih dan dievaluasi secara efektif.
- Menghapus kolom yang tidak relevan dengan fitur target: Kolom-kolom seperti PassengerId, Name, Ticket, dan Embarked dihapus menggunakan fungsi .drop(), karena kolom-kolom ini tidak memberikan kontribusi langsung terhadap prediksi target (Survived). Menghapus kolom yang tidak relevan sangat penting untuk mengurangi kompleksitas model dan meningkatkan akurasi, karena data yang tidak berkaitan bisa memperkenalkan noise dan memperburuk performa model. Dengan mengeliminasi kolom tersebut, model hanya bekerja dengan data yang relevan dan bisa fokus pada fitur yang benar-benar mempengaruhi hasil. Proses ini memastikan bahwa model lebih efisien dalam mempelajari pola dari data yang benar-benar penting.
- Mengganti nilai 0 dengan null pada kolom Fare: Nilai 0 pada kolom Fare diubah menjadi null (NaN) menggunakan fungsi .replace() untuk menghindari nilai yang tidak valid atau tidak logis. Nilai 0 pada kolom ini bisa menunjukkan data yang hilang atau salah input, sehingga mengubahnya menjadi null memungkinkan kita untuk mengimputasi nilai yang lebih relevan. Hal ini penting agar nilai kosong pada kolom tersebut dapat digantikan dengan data estimasi yang lebih akurat. Setelah nilai kosong diganti dengan nilai yang terduga, kualitas dataset menjadi lebih baik dan siap untuk pelatihan model.
- Mengisi data yang kosong pada kolom Age, Cabin, dan Fare dengan metode K-NN: Data yang kosong pada kolom Age, Cabin, dan Fare diisi menggunakan metode K-NN yang memilih nilai dari tetangga terdekat berdasarkan fitur lainnya. Metode ini mengisi data yang hilang dengan cara mencari pola yang ada pada data lain yang mirip, sehingga nilai yang dihasilkan lebih akurat dan tidak acak. Mengisi nilai kosong sangat penting untuk memastikan model tidak mengabaikan baris data yang hilang, yang bisa mengurangi efektivitas model. Dengan imputasi yang tepat, data menjadi lebih lengkap dan siap diproses lebih lanjut.
- Mengelompokkan nilai pada kolom Cabin, Age, SibSp, Parch, dan Fare: Kolom-kolom seperti Cabin, Age, SibSp, Parch, dan Fare dikelompokkan menggunakan teknik binning atau percabangan untuk mengubah nilai kontinu menjadi kategori. Pengelompokan ini membantu dalam menyederhanakan data dan menjadikan pola lebih terlihat, seperti mengelompokkan usia menjadi kategori "Anak", "Dewasa", dll. Binning juga membantu dalam mengurangi dampak outlier dan mempermudah model untuk mempelajari hubungan antara fitur dan target. Dengan pengelompokan ini, model dapat menangani fitur-fitur tersebut lebih efektif dan efisien.
- Encoding kolom-kolom non-numerik dengan modul LabelEncoder: Kolom seperti Sex, Cabin, dan Age yang awalnya berupa data kategorikal diubah menjadi bentuk numerik menggunakan LabelEncoder. Proses encoding ini penting karena sebagian besar algoritma machine learning hanya menerima data numerik sebagai input. Dengan mengubah data non-numerik menjadi numerik, model dapat lebih mudah memproses informasi dan menemukan pola yang tersembunyi dalam data. Hal ini memungkinkan data yang semula tidak dapat digunakan oleh model untuk diproses dengan benar.
- Mendefinisikan fitur dan target serta membagi data menjadi data latih dan data uji: Proses pemisahan fitur (X) dan target (y) dilakukan dengan fungsi .drop() untuk memastikan bahwa model hanya melatih data berdasarkan fitur yang relevan, sementara target (Survived) digunakan untuk memprediksi hasil. Selanjutnya, dataset dibagi menjadi data latih dan data uji menggunakan train_test_split, yang penting untuk menghindari overfitting dan memastikan model diuji pada data yang tidak pernah dilihat sebelumnya. Pembagian ini memungkinkan kita untuk melatih model dengan data latih dan menguji performanya pada data uji untuk mendapatkan evaluasi yang lebih akurat. Dengan cara ini, kita dapat memastikan bahwa model dapat generalisasi dengan baik ke data baru.
  
## Modeling
Model yang digunakan dalam proyek ini adalah sebagai berikut ini.
1. Algoritma K-NN (K-Nearest Neighbor) dengan Parameter Memilih Jumlah Tetangga Terbaik pada Rentang 1-50 Tetangga
K-NN adalah algoritma berbasis instance yang mengklasifikasikan data baru berdasarkan kedekatannya dengan data latih terdekat. Dalam konteks dataset Titanic, K-NN mengukur jarak antara sampel yang tidak diketahui dan sampel yang ada (misalnya menggunakan Euclidean distance). Untuk memilih jumlah tetangga terbaik, model mencoba berbagai nilai K (jumlah tetangga) dalam rentang 1-50 dan memilih yang memberikan akurasi tertinggi pada data validasi. Pemilihan K yang optimal sangat penting karena K yang terlalu kecil atau terlalu besar dapat memengaruhi kinerja model. Model ini umumnya digunakan untuk masalah klasifikasi sederhana namun sangat dipengaruhi oleh skala data dan outliers.

2. Algoritma Random Forest Classifier dengan Parameter n_estimators
Random Forest adalah algoritma ensemble yang menggabungkan banyak pohon keputusan untuk meningkatkan akurasi klasifikasi. Pada dataset Titanic, model ini membangun beberapa pohon keputusan berdasarkan subset acak dari data latih, dan hasil klasifikasi akhir ditentukan oleh mayoritas keputusan dari semua pohon. Parameter n_estimators menentukan jumlah pohon keputusan yang dibangun. Semakin banyak pohon yang digunakan, model cenderung lebih akurat dan stabil, namun juga memerlukan lebih banyak sumber daya komputasi. Pengaturan yang tepat untuk n_estimators penting untuk mencapai keseimbangan antara kinerja dan efisiensi komputasi.

3. Algoritma Random Forest Classifier yang Dituning dengan Parameter n_estimators, max_depth, min_samples_split, dan min_samples_leaf
Random Forest yang dituning dengan parameter tambahan bertujuan untuk meminimalkan overfitting dan meningkatkan generalisasi. max_depth membatasi kedalaman maksimum setiap pohon, yang dapat mengurangi kompleksitas model dan mencegah overfitting. min_samples_split dan min_samples_leaf mengatur batasan jumlah sampel minimum untuk membagi node dan menjadi daun pohon, mempengaruhi granularitas pembelajaran model. Melalui grid search atau teknik optimasi lain, parameter-parameter ini dapat disesuaikan untuk mendapatkan model yang lebih baik. Pada dataset Titanic, tuning parameter ini membantu menyesuaikan model dengan karakteristik data, seperti ketidakseimbangan kelas dan noise.

4. Algoritma XGBoost Classifier
XGBoost adalah algoritma pembelajaran boosting yang menggabungkan banyak model pohon keputusan dalam urutan yang berurutan, di mana model berikutnya mengoreksi kesalahan dari model sebelumnya. Pada dataset Titanic, XGBoost digunakan untuk memprediksi kelangsungan hidup penumpang berdasarkan fitur seperti usia, jenis kelamin, dan kelas. Keunggulan utama XGBoost adalah kemampuannya untuk mengatasi overfitting melalui teknik regularisasi dan kemampuannya mengoptimalkan loss function dengan cara yang efisien. XGBoost bekerja sangat baik pada dataset tabular dan biasanya lebih cepat serta lebih akurat dibandingkan model lain dalam tugas klasifikasi. Algoritma ini sangat populer dalam kompetisi data science seperti Kaggle.

5. Algoritma XGBoost Classifier yang Dituning dengan Parameter learning_rate, n_estimators, max_depth, subsample, dan colsample_bytree
Tuning XGBoost dengan parameter seperti learning_rate, n_estimators, max_depth, subsample, dan colsample_bytree bertujuan untuk meningkatkan akurasi dan mencegah overfitting. learning_rate mengontrol kecepatan pembelajaran model, di mana nilai yang lebih kecil dapat meningkatkan akurasi dengan biaya komputasi yang lebih tinggi. n_estimators menentukan jumlah pohon dalam ensemble, sementara max_depth mengatur kedalaman pohon yang membatasi kompleksitas model. subsample dan colsample_bytree mengatur proporsi data dan fitur yang digunakan untuk setiap pohon, mengurangi korelasi antar pohon dan meningkatkan generalisasi. Parameter-parameter ini dapat dioptimalkan untuk menghasilkan model yang lebih efisien pada dataset Titanic.

6. Model Gradient Boosting Classifier
Gradient Boosting Classifier adalah algoritma boosting yang membangun model pohon keputusan secara berurutan, di mana setiap pohon baru memfokuskan pada kesalahan yang dibuat oleh pohon sebelumnya. Dalam konteks Titanic, model ini digunakan untuk memprediksi kelangsungan hidup penumpang dengan menggabungkan prediksi dari berbagai pohon keputusan. Keuntungan utama gradient boosting adalah kemampuannya untuk menangani data yang kompleks dan ketidakseimbangan kelas dengan baik. Meskipun lebih lambat dalam pelatihan dibandingkan dengan Random Forest atau XGBoost, model ini sering memberikan hasil yang sangat akurat. Gradient Boosting dapat sangat efektif bila parameter yang digunakan telah dioptimalkan dengan baik.

7. Model Gradient Boosting Classifier yang Dituning dengan Parameter learning_rate, n_estimators, max_depth, dan subsample
Tuning Gradient Boosting dengan parameter seperti learning_rate, n_estimators, max_depth, dan subsample bertujuan untuk mengoptimalkan kinerja model dan mencegah overfitting. learning_rate menentukan kontribusi setiap pohon dalam pembelajaran, di mana nilai lebih kecil memperlambat proses tetapi dapat meningkatkan akurasi model akhir. n_estimators mengatur jumlah pohon dalam model boosting, sementara max_depth membatasi kedalaman pohon untuk menghindari model yang terlalu kompleks. subsample mengontrol proporsi data yang digunakan untuk membangun setiap pohon, yang dapat mengurangi overfitting. Melalui tuning yang hati-hati, model ini dapat mencapai performa terbaik pada dataset Titanic.

Adapun dua fitur yang paling tinggi memberikan kontribusi pada pelatihan semua model adalah fitur "Sex" dan "PClass". Sedangkan, fitur ketiga yang berkontribusi secara optimal ada beberapa perbedaan dengan perincian sebagai berikut ini.
- Pada model KNN fitur ketiga yang paling berkontribusi adalah "SibSp".
- Pada model Random Forest Classifier dan Gradient Boosting Classifier baik yang dituning maupun tidak fitur ketiga yang paling berkontribusi adalah "Age".
- Pada model Random Forest Classifier yang dituning dan XGBoost Classifier baik yang dituning maupun tidak fitur ketiga yang paling berkontribusi adalah "Cabin".
  
Secara umum tahapan pemilihan model yang digunakan sebagai berikut ini.
- Pemilihan Model: Memilih algoritma yang sesuai dengan data dan permasalahan (K-NN, Random Forest, XGBoost).
- Prapemrosesan Data: Melakukan pembersihan dan transformasi data (mengisi nilai kosong, encoding, dll).
- Visualisasi Data: Melakukan plotting data untuk melihat sebaran data setiap kategori pada tiap kolom.
- Tuning Model: Meningkatkan kemampuan model dengan menyesuaikan parameter-parameternya.
- Pelatihan Model: Melatih model menggunakan data latih dan mengoptimalkan dengan tuning parameter.
- Evaluasi Model: Menggunakan metrik seperti accuracy dan confussion matrix untuk mengevaluasi performa model. 

Algoritma yang digunakan sebagai solusi rekomendasi yakni, model Random Forest Classifier dan XGBoost Classifier.
- Random Forest Classifier memiliki keunggulan dalam hal keandalan dan stabilitas serta dapat menangani overfitting, namun membutuhkan lebih banyak sumber daya dan waktu untuk pelatihan pada dataset besar.
- XGBoost memberikan akurasi tinggi dan kecepatan dalam pelatihan, tetapi memerlukan proses tuning yang lebih rumit dan dapat lebih sulit diinterpretasikan dibandingkan dengan model yang lebih sederhana seperti Random Forest.

## Evaluation
Metrik yang digunakan adalah accuracy dan confussion matrix. Dengan penggunakan matrik tersebut berikut ini merupakan hasil dari tiap-tiap model berikut ini.
- Algoritma K-NN (K-Nearest Neighboor) dengan parameter memilih jumlah tetangga terbaik pada rentang 1-50 tetangga menghasilkan akurasi sebesar 0,82 dengan jumlah tetangga terdekat sebanyak k=5. 
- Algoritma Random Forest Classifier dengan parameter n_estimators sebesar 100 menghasilkan akurasi sebesar 0.79. 
- Algoritma Random Forest Classifier yang dituning dengan parameter n_estimators, max_depth, min_samples_split, dan min_samples_leaf menghasilkan akurasi sebesar 0.81 pada max_depth sebesar 12, min_samples_leaf sebanyak 3, min_samples_split sebanyak 15 dan n_estimators sebanyak 80.  
- Algoritma XGBoost Classifier menghasilkan akurasi sebesar 0.78. 
- Algoritma XGBoost Classifier yang dituning dengan pameter learning_rate, n_estimators, max_depth, subsample, dan colsample_bytree menghasilkan akurasi sebesar 0.80 pada colsample_bytree sebesar 0.8, learning_rate sebesar 0.01, max_depth sebesar 3, n_estimators sebesar 800, dan subsample sebesar 0.8.
- Model Gradient Boosting Classifier menghasilkan akurasi sebesar 0.79. 
- Model Gradient Boosting Classifier yang dituning dengan parameter learning_rate, n_estimators, max_depth, dan subsample menghasilkan akurasi sebesar 0.80 pada learning_rate sebesar 0.01, max_depth sebesar 5, n_estimators sebesar 300 dan subsample sebesar 1.0.

Proyek ini sudah menjawab problem statement yang diungkapkan di awal, yakni variabel yang paling berpengaruh pada proyek ini adalah fitur "Sex" dan "PClass" pada semua model yang digunakan dalam proyek ini. Kemudian telah menjawab juga mengenai seberapa jauh suatu algoritma digunakan dalam memprediksi berdasarkan data ini, yang diperoleh hasil rata-rata mampu memprediksi sebesar 80% tepat dalam memprediksi data ini.
Model yang mampu memenuhi target yang ditetapkan dari proyek ini sebanyak 4 model, yakni algoritma K-NN (K-Nearest Neighboor), algoritma Random Forest Classifier yang dituning, XGBoost Classifier yang dituning, dan algoritma Gradient Boosting Classifier yang dituning. Sedangkan tiga model lainnya tingkat akurasinya masih sedikit (1-2%) di bawah target yang ditentukan, yakni algoritma Random Forest Classifier, lgoritma XGBoost Classifier, dan algoritma Gradient Boosting Classifier. 
Pernyataan solusi pada proyek ini bermanfaat untuk menjadi suatu referensi dalam mitigasi keselamatan sarana transportasi laut. Pihak-pihak terkait keselamatan sarana transportasi laut dapat memberikan pengamanan tambahan kepada beberapa penumpang yang rentan tidak selamat berdasarkan hasil prediksi model ini.

- Accuracy merupakan matrik yang mengukur seberapa sering model menghasilkan prediksi yang benar. Cara kerjanya Akurasi dihitung dengan membandingkan hasil prediksi model dengan label asli data. Semakin tinggi nilai akurasi, semakin baik model dalam memprediksi dengan benar. Formula pada matrik accuracy adalah prediksi yang tepat dibagi dengan jumlah data.
- Confussion matrix merupakan matrik yang digunakan untuk mendeteksi bagaimana model mengklasifikasikan data ke dalam kelas-kelas yang benar dan salah. Cara kerjanya memberikan gambaran yang lebih rinci tentang kesalahan yang dilakukan model, termasuk jenis kesalahan (false positives dan false negatives). Ini membantu kita untuk memahami apakah model cenderung membuat lebih banyak prediksi positif yang salah atau negatif yang salah. Formula dari matrik ini menghitung jumlah true positif dan negatif serta false positif dan negatif.

### Tabel Evaluasi Model
| Model  | Akurasi | TP | TN | FP | FN | Kesimpulan |
| ------------- | ------------- |------------- | ------------- |------------- | ------------- |------------- |
| K-NN (K-Nearest Neighboor)  | 0,82  | 52 | 95 | 22 | 10 | Tingkat akurasinya sudah sesuai target yang ditentukan |
| Random Forest Classifier  | 0,79  | 52 | 90 | 22  | 15 | Tingkat akurasinya di bawah target yang ditentukan |
| Algoritma Random Forest Classifier Tuning Parameter  | 0,81  | 50 | 95 | 24 | 10 | Tingkat akurasinya sedikit di atas target yang ditentukan |
| XGBoost Classifier  | 0,78  | 51 | 90 | 23 | 15 | Tingkat akurasinya di bawah target yang ditentukan |
| XGBoost Classifier Tuning Parameter  | 0,80  | 50 | 94 | 24 | 11 | Tingkat akurasinya sudah sesuai target yang ditentukan |
| Gradient Boosting Classifier  | 0,79 | 49 | 94 | 25 | 11 | Tingkat akurasinya di bawah target yang ditentukan |
| Gradient Boosting Classifier Tuning Parameter  | 0,80 | 50 | 94 | 24 | 11 | Tingkat akurasinya sudah sesuai target yang ditentukan |


**---Ini adalah bagian akhir laporan---**


# Lampiran Frekuensi Data Setiap Kolom
1. Visualisasi frekuensi pada kolom "Survived"
   ![image alt](https://github.com/Suhardi100/Proyek-Prediksi-Keselamatan-dari-Kecelakaan-Kapal-Titanic/blob/main/Hasil%20Visualisasi_Frekuensi%20Survived.png?raw=true)
3. Visualisasi frekuensi pada kolom "PClass"
   ![image alt](https://github.com/Suhardi100/Proyek-Prediksi-Keselamatan-dari-Kecelakaan-Kapal-Titanic/blob/main/Hasil%20Visualisasi_Frekuensi%20PClass.png?raw=true)
4. Visualisasi frekuensi pada kolom "Sex"
   ![image alt](https://github.com/Suhardi100/Proyek-Prediksi-Keselamatan-dari-Kecelakaan-Kapal-Titanic/blob/main/Hasil%20Visualisasi_Frekuensi%20Sex.png?raw=true)
5. Visualisasi frekuensi pada kolom "Age"
   ![image alt](https://github.com/Suhardi100/Proyek-Prediksi-Keselamatan-dari-Kecelakaan-Kapal-Titanic/blob/main/Hasil%20Visualisasi_Frekuensi%20Age.png?raw=true)
6. Visualisasi frekuensi pada kolom "SibSp"
   ![image alt](https://github.com/Suhardi100/Proyek-Prediksi-Keselamatan-dari-Kecelakaan-Kapal-Titanic/blob/main/Hasil%20Visualisasi_Frekuensi%20SibSp.png?raw=true)
7. Visualisasi frekuensi pada kolom "Parch"
   ![image alt](https://github.com/Suhardi100/Proyek-Prediksi-Keselamatan-dari-Kecelakaan-Kapal-Titanic/blob/main/Hasil%20Visualisasi_Frekuensi%20Parch.png?raw=true)
8. Visualisasi frekuensi pada kolom "Fare"
   ![image alt](https://github.com/Suhardi100/Proyek-Prediksi-Keselamatan-dari-Kecelakaan-Kapal-Titanic/blob/main/Hasil%20Visualisasi_Frekuensi%20Fare.png?raw=true)
9. Visualisasi frekuensi pada kolom "Cabin"
   ![image alt](https://github.com/Suhardi100/Proyek-Prediksi-Keselamatan-dari-Kecelakaan-Kapal-Titanic/blob/main/Hasil%20Visualisasi_Frekuensi%20Cabin.png?raw=true)
