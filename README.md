# 20P03519-MID_SEMESTER

## Dataset

Dataset ini berisi data fitur-fitur kimiawi dari anggur merah
dan putih serta nilai kualitasnya, dengan total 857 entri dan 13 kolom. Berikut adalah deskripsi setiap kolom:
1. `fixed acidity` – Kandungan asam tetap, terutama terdiri dari asam tartarat dan malat.
2. `volatile acidity` – Kandungan asam mudah menguap seperti asam asetat, yang dapat memengaruhi aroma dan rasa.
3. `citric acid` – Asam sitrat, menambah kesegaran dan kompleksitas rasa.
4. `residual sugar` – Jumlah gula yang tersisa setelah proses fermentasi selesai.
5. `chlorides` – Kandungan garam yang memengaruhi rasa dan kestabilan.
6. `free sulfur dioxide` – Jumlah SO₂ bebas yang berperan sebagai agen antimikroba dan antioksidan.
7. `total sulfur dioxide` – Total SO₂ (bebas dan terikat), digunakan sebagai indikator perlindungan oksidatif.
8. `density` – Kepadatan cairan, berkaitan dengan kandungan gula dan alkohol.
9. `pH` – Tingkat keasaman dari sampel.
10. `sulphates` – Kandungan sulfat, berperan dalam pengawetan dan memengaruhi rasa.
11. `alcohol` – Persentase kandungan alkohol (% volume).
12. `quality` – Nilai kualitas minuman berdasarkan penilaian panel (skala ordinal, kemungkinan 0–10).
13. `Id` – 	Nomor identifikasi unik untuk setiap entri data.

## 1. Eksplorasi Data

### *Missing Values*

Berdasarkan hasil analisis tidak ditemukan nilai yang hilang (*missing values*) dalam dataset. Ini berarti dataset bersih dan tidak memerlukan penanganan tambahan untuk mengatasi missing values.

### Visualisasi Data

#### A. Histogram Distribusi Kualitas Wine

<img src="Images/Image1.png">

Histogram tersebut menampilkan distribusi nilai kualitas minuman anggur dalam dataset. Dari grafik terlihat bahwa nilai kualitas yang paling sering muncul adalah 5 dan 6, masing-masing dengan lebih dari 300 sampel, menjadikannya sebagai kategori yang paling dominan. Nilai kualitas 7 muncul dalam jumlah yang jauh lebih sedikit, sekitar 100 sampel, sementara nilai 3, 4, dan 8 hanya muncul dalam jumlah yang sangat kecil, masing-masing kurang dari 50 sampel. Distribusi ini menunjukkan bahwa sebagian besar anggur dalam dataset dinilai memiliki kualitas sedang, sedangkan anggur dengan kualitas sangat rendah atau sangat tinggi jarang ditemukan. Hal ini mengindikasikan ketidakseimbangan distribusi, yang perlu dipertimbangkan jika data ini akan digunakan untuk pemodelan klasifikasi.

#### B. Boxplot antar Fitur dan Kualitas

<img src="Images/Image2.png">

Boxplot di atas menggambarkan distribusi kandungan alkohol terhadap nilai kualitas minuman anggur. Setiap nilai kualitas (dari 3 hingga 8) memiliki sebaran kandungan alkohol yang ditampilkan melalui rentang interkuartil dan median. Terlihat bahwa terdapat kecenderungan yang cukup jelas: semakin tinggi nilai kualitas, semakin tinggi pula median kandungan alkoholnya. Untuk anggur dengan kualitas 3 hingga 5, kandungan alkohol umumnya berada di bawah 10,5%, dengan median sekitar 9,5% hingga 10%. Sementara itu, pada kualitas 6 hingga 8, median alkohol meningkat dan sebagian besar sampel memiliki kandungan alkohol di atas 11%. Hal ini menunjukkan adanya hubungan positif antara kadar alkohol dan kualitas anggur, yang mengindikasikan bahwa alkohol dapat menjadi salah satu faktor penentu dalam penilaian kualitas minuman dalam dataset ini.

#### C. Heatmap Korelasi antar Fitur

<img src="Images/Image3.png">

Heatmap korelasi yang dihasilkan merupakan visualisasi dari hubungan linear antar fitur numerik dalam dataset anggur, kecuali kolom `Id` yang telah dihapus sebelumnya. Setiap sel pada heatmap menunjukkan nilai korelasi Pearson antara dua fitur, dengan warna merah menunjukkan korelasi positif, biru menunjukkan korelasi negatif, dan warna netral menunjukkan korelasi lemah atau mendekati nol. Semakin mendekati angka 1 atau -1, semakin kuat hubungan linear antar fitur tersebut. Beberapa korelasi yang cukup tinggi dapat diamati, seperti antara `free sulfur dioxide` dan `total sulfur dioxide` (0.66) yang menunjukkan keterkaitan logis karena SO₂ total mencakup SO₂ bebas, serta antara `fixed acidity` dan `density` (0.69), yang mengindikasikan bahwa meningkatnya kadar asam tetap juga berdampak pada peningkatan kepadatan cairan.

Dalam konteks hubungan terhadap kualitas anggur (`quality`), fitur `alcohol` memiliki korelasi positif paling tinggi, yaitu sebesar 0.47, yang menunjukkan bahwa kadar alkohol yang lebih tinggi cenderung dikaitkan dengan kualitas anggur yang lebih baik. Sebaliknya, `volatile acidity` memiliki korelasi negatif yang cukup kuat terhadap kualitas (-0.43), menunjukkan bahwa semakin tinggi kandungan asam volatil, semakin rendah kualitas anggur yang dirasakan. Fitur lain seperti `sulphates` dan `citric acid` juga menunjukkan korelasi positif terhadap kualitas, meskipun dalam tingkat yang lebih rendah. Dari visualisasi ini, dapat disimpulkan bahwa fitur-fitur tertentu memiliki pengaruh yang lebih besar terhadap persepsi kualitas anggur, dan informasi ini dapat dimanfaatkan dalam proses seleksi fitur atau pembuatan model prediktif selanjutnya.

#### D. Heatmap Korelasi antar Fitur

<img src="Images/Image4.png">

Scatterplot tersebut menunjukkan hubungan antara kadar alkohol dan asam volatil dalam sampel anggur, dengan warna titik mewakili nilai kualitas (`quality`). Sumbu horizontal menunjukkan kadar alkohol (%), sedangkan sumbu vertikal menunjukkan kadar asam volatil. Warna titik menggunakan skema `viridis`, di mana warna lebih terang mewakili kualitas yang lebih tinggi.

Dari grafik ini terlihat bahwa anggur dengan kualitas tinggi umumnya memiliki kadar alkohol yang lebih tinggi dan kadar asam volatil yang lebih rendah. Sebaliknya, anggur dengan kualitas rendah cenderung memiliki alkohol rendah dan asam volatil tinggi. Hal ini sejalan dengan hasil korelasi sebelumnya yang menunjukkan alkohol berpengaruh positif terhadap kualitas, sementara asam volatil berpengaruh negatif.

#### E. Bar Plot Rata-Rata Fitur per Kategori Kualitas

<img src="Images/Image5.png">

Barplot tersebut menampilkan rata-rata nilai dari beberapa fitur kimia anggur (`volatile acidity`, `chlorides`, `citric acid`, dan `sulphates`) berdasarkan tingkat kualitas anggur (`quality`). Sumbu horizontal menunjukkan nilai kualitas (dari 3 hingga 8), sedangkan sumbu vertikal menunjukkan rata-rata nilai dari masing-masing fitur. Warna batang menunjukkan jenis fitur yang dianalisis.

Dari grafik tersebut, terlihat pola yang konsisten: nilai `volatile acidity` dan `chlorides` cenderung menurun seiring meningkatnya kualitas anggur, sedangkan `citric acid` dan `sulphates` justru meningkat. Hal ini menunjukkan bahwa anggur dengan kualitas tinggi umumnya memiliki kadar asam volatil dan garam yang lebih rendah, serta kandungan asam sitrat dan sulfat yang lebih tinggi. Visualisasi ini memperkuat pemahaman tentang pengaruh masing-masing fitur terhadap persepsi kualitas anggur.

## 2. Preprocessing Data

### Balancing Data

Data diseimbangkan berdasarkan nilai kualitas anggur (`quality`). Pertama, data fitur kimia disimpan dalam variabel `X`, sedangkan label target disimpan dalam `y`. Kemudian digunakan metode SMOTE (*Synthetic Minority Over-sampling Technique*) untuk melakukan oversampling pada kelas minoritas. SMOTE bekerja dengan membuat data sintetis baru berdasarkan sampel minoritas yang ada dan tetangga terdekatnya. Dalam kode ini, digunakan 3 tetangga terdekat (`k_neighbors=3`) untuk membentuk sampel baru secara acak, sehingga distribusi kelas menjadi lebih seimbang dan model dapat belajar dengan lebih baik.

### Feature Scaling Fitur Numerik

Dilakukan *scaling* pada fitur numerik menggunakan `StandardScaler`, yang mengubah data agar memiliki rata-rata 0 dan standar deviasi 1. Proses ini penting agar semua fitur berada pada skala yang sama, sehingga model tidak bias terhadap fitur dengan nilai besar. Scaling membantu meningkatkan performa model, terutama untuk algoritma yang sensitif terhadap jarak antar data seperti KNN atau SVM.

### Data Training & Data Testing

Data dibagi menjadi data latih (80%) dan data uji (20%) menggunakan `train_test_split`. Parameter `stratify` menjaga distribusi label tetap seimbang, dan `random_state=42` memastikan hasil pembagian konsisten. Train-test split digunakan untuk menguji performa model dengan memisahkan sebagian data sebagai data uji, agar hasil prediksi bisa dievaluasi secara objektif.

## 3. Processing Data

Beberapa model digunakan untuk melatih dan mengevaluasi klasifikasi pada data kualitas anggur. Enam model yang digunakan adalah: Logistic Regression, Decision Tree, Random Forest, SVM, KNN, dan MLP Neural Network. Masing-masing model dilatih menggunakan `X_train` dan `y_train`, lalu dilakukan prediksi terhadap `X_test`. Selanjutnya dihitung metrik evaluasi: akurasi, presisi, recall, dan F1-score dengan rata-rata berbobot (`average='weighted'`) agar memperhitungkan distribusi label yang tidak seimbang. Hasil evaluasi disimpan dalam list `evaluation_results` untuk dibandingkan.

Pemilihan model ini dikarenakan:
- Logistic Regression cocok untuk klasifikasi multikelas dan interpretatif.
- Decision Tree mudah dipahami dan bisa menangani fitur non-linear.
- Random Forest memperbaiki kelemahan decision tree tunggal dan baik untuk data yang kompleks.
- SVM efektif untuk data berdimensi tinggi dan dapat bekerja baik dengan margin klasifikasi yang jelas.
- KNN sederhana namun efektif untuk dataset kecil-menengah.
- MLP Neural Network mampu menangkap hubungan kompleks antar fitur karena memiliki arsitektur non-linear yang fleksibel.

Dengan membandingkan semua model ini, dapat diperoleh model mana yang paling akurat dan sesuai untuk prediksi kualitas anggur dalam dataset ini.

## 4. Evaluasi Model

### Metric Evaluasi Model

| Model               | Accuracy | Precision | Recall | F1 Score |
|---------------------|----------|-----------|--------|----------|
| Logistic Regression | 0.6322   | 0.6282    | 0.6322 | 0.6261   |
| Decision Tree       | 0.7632   | 0.7641    | 0.7632 | 0.7624   |
| Random Forest       | 0.8437   | 0.8378    | 0.8437 | 0.8399   |
| SVM                 | 0.7494   | 0.7375    | 0.7494 | 0.7412   |
| KNN                 | 0.7632   | 0.7465    | 0.7632 | 0.7435   |
| MLP Neural Network  | 0.8414   | 0.8354    | 0.8414 | 0.8374   |

Output tersebut menunjukkan hasil evaluasi enam model klasifikasi berdasarkan akurasi, presisi, recall, dan F1-score pada data pengujian. Berikut interpretasinya:

- Random Forest memiliki performa terbaik di semua metrik (akurasi: 0.8437, F1-score: 0.8399), menunjukkan kemampuannya menangani kompleksitas dan variasi data dengan baik.
- MLP Neural Network juga menunjukkan performa sangat baik (akurasi: 0.8414), sedikit di bawah Random Forest, menjadikannya alternatif kuat dalam kasus ini.
- Decision Tree dan KNN menghasilkan akurasi serupa (0.7632), tetapi KNN memiliki F1-score yang lebih rendah, mengindikasikan ketidakseimbangan antara presisi dan recall.
- SVM memiliki performa cukup baik (akurasi: 0.7494), tetapi lebih rendah dibanding model-model sebelumnya.
- Logistic Regression menghasilkan skor terendah di semua metrik, menunjukkan model ini kurang cocok untuk dataset ini yang memiliki karakteristik non-linear dan kompleks.

Secara keseluruhan, Random Forest adalah model paling andal untuk klasifikasi kualitas anggur dalam dataset ini, dengan kombinasi metrik yang seimbang dan tinggi.

### Confusion Matrix

<img src="Images/Image6.png">

Confusion matrix untuk model terbaik yaitu Random Forest menunjukkan bahwa model mampu mengklasifikasikan kualitas anggur dengan sangat baik, terutama pada kelas 3, 4, dan 8, di mana semua prediksi tepat tanpa kesalahan. Namun, kesalahan klasifikasi terjadi pada kelas tengah seperti 5, 6, dan 7. Misalnya, kelas 5 sering diprediksi sebagai kelas 6, dan sebaliknya, kelas 6 juga salah diprediksi sebagai kelas 5 dan 7. Hal ini menunjukkan bahwa model mengalami kebingungan dalam membedakan kualitas anggur yang berada pada rentang menengah, yang kemungkinan besar disebabkan oleh kemiripan fitur di antara kelas-kelas tersebut. Meskipun demikian, performa secara keseluruhan tetap sangat baik, sejalan dengan skor evaluasi yang tinggi pada metrik akurasi, presisi, recall, dan F1-score.

### Feature Importance

<img src="Images/Image7.png">

Gambar tersebut menunjukkan grafik feature importance atau tingkat kepentingan masing-masing fitur dalam memprediksi penyakit ginjal kronis. Fitur dengan kontribusi paling besar adalah volatile acidity (14,44%), diikuti oleh sulphates (12,75%) dan alcohol (11,86%). Ini berarti bahwa perubahan dalam kadar keasaman volatil, kadar sulfat, dan kandungan alkohol memiliki pengaruh paling signifikan terhadap hasil prediksi. Sementara itu, fitur seperti fixed acidity dan residual sugar memberikan pengaruh paling kecil, masing-masing hanya sekitar 5,65% dan 5,67%. Interpretasi ini penting untuk membantu dalam proses seleksi fitur atau untuk memahami faktor-faktor dominan yang memengaruhi prediksi model, sehingga bisa digunakan untuk optimasi data atau analisis lebih lanjut dalam konteks medis atau analitik.

## 5. Kesimpulan

Berdasarkan hasil eksplorasi, pemrosesan, dan evaluasi model pada dataset, dapat disimpulkan bahwa model Random Forest memberikan performa terbaik dalam memprediksi kualitas wine dibandingkan model lainnya. Hal ini terlihat dari nilai akurasi sebesar 84.37%, serta nilai precision, recall, dan f1-score yang juga tinggi dan seimbang. Selain itu, analisis confusion matrix menunjukkan bahwa model mampu mengklasifikasikan setiap kelas dengan cukup baik, meskipun masih terdapat beberapa kesalahan prediksi pada kelas-kelas yang memiliki distribusi data tidak seimbang.

Dari analisis feature importance, diketahui bahwa fitur seperti volatile acidity, sulphates, dan alcohol memberikan kontribusi paling besar terhadap prediksi kualitas wine. Hal ini menunjukkan bahwa faktor-faktor kimia tertentu sangat berpengaruh dalam menentukan kualitas akhir produk wine.

Secara keseluruhan, proses yang dilakukan mulai dari eksplorasi data, pembersihan data, visualisasi, pemodelan, hingga evaluasi model telah menghasilkan sistem prediksi yang cukup akurat dan dapat diandalkan untuk klasifikasi kualitas wine.
