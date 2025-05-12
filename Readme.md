# Laporan Proyek Machine Learning - Rizki Wahyu Nurcahyani Fajarwati 
- **Nama:** Rizki Wahyu Nurcahyani Fajawrati
- **Email:** a123xbf441@devacademy.id
- **ID Dicoding:** a123xbf441

## Domain Proyek

**Latar Belakang** 

Cuaca adalah keadaan udara di atmosfer pada waktu dan tempat tertentu yang sifatnya tidak menentu dan berubah-ubah. Penilaian terhadap kategori cuaca umumnya dinyatakan dengan memperhatikan kondisi hujan, suhu udara, jumlah tutupan awan, penguapan, kelembapan, dan kecepatan angin di suatu tempat dari hari ke hari. 

Cuaca memiliki pengaruh yang besar terhadap berbagai sektor seperti pertanian, transportasi, pariwisata, dan perencanaan kota. Perubahan cuaca yang cepat dan tak terduga dapat menyebabkan kerugian ekonomi dan risiko keselamatan. Oleh karena itu, prediksi cuaca yang akurat menjadi sangat penting.

**Kenapa Masalah Ini Penting**

Dengan kemajuan dalam machine learning, kita bisa memanfaatkan data historis cuaca untuk mengklasifikasikan kondisi cuaca yang akan terjadi. Ini dapat membantu dalam pengambilan keputusan berbasis data. Prediksi cuaca yang lengkap dan akurat sangat dibutuhkan agar dapat meningkatkan kinerja dari berbagai bidang akivitas manusia. Informasi cuaca sangat bermanfaat dalam berbagai bidang antara lain bidang transportasi, pertanian dan industri\[1].

**Refrensi**

\[1]. Tita Lattifia, et al. “Model Prediksi Cuaca Menggunakan Metode LSTM.” JITTER Jurnal Ilmiah Teknologi Dan Komputer, vol. 3, no. 1, 31 Mar. 2022, pp. 994–994, https://doi.org/10.24843/jtrti.2022.v03.i01.p35. Accessed 4 Mei 2025.


## Business Understanding

### Problem Statements

Dalam berbagai sektor yang ada di Indonesia seperti perekonomian, pertanian, pariwisata, dll informasi mengenai kondisi cuaca sangat dibutuhkan. Maka dari itu diperlukan sistem yang mampu memprediksi jenis cuaca seperti Sunny, Rainy, Cloudy, Snowy, dan lainnya berdasarkan data historis yang dimiliki seperti suhu, kelembapan, dll.

### Goals

Tujuan dari adanya proyek ini adalah membangun sebuah model klasifikasi cuaca yang dapat memprediksi jenis cuaca berdasarkan input dari berbagai fiturnya seperti fitur numerik dan kategorikal. Dengan adanya model ini diharapkan mampu memberikan prediksi yang dapat digunakan untuk mendukung pengambilan keputusan.

### Solution statements
Untuk mencapai tujuan di atas, akan dilakukan pendekatan berbasis machine learning dengan menggunakan algoritma klasifikasi seperti Logistic Regression, Decision Tree, dan XGBoost. Namun, data akan melalui diproses melalui proses seperti preprocessing(normalisasi dengan MinMaxScaler dan label encoder). Setelah modeling, model yang telah jadi akan dievaluasi berdasarkan metrik performa seperti akurasi dan confusion matrix guna memilih model terbaik.

## Data Understanding
**Informasi Dataset**

Dataset Weather Classification merupakan dataset yang berasal dari kaggle, dengan link berikut : https://www.kaggle.com/datasets/nikhil7280/weather-type-classification/data. Dataset ini disimpan dengan nama weather_classification_data.csv. 

**Kondisi Dataset**

- Dataset weather_classification_data memiliki data sebanyak 13.200 baris data serta 11 kolom dan saat dilakukan proses preprocessing, dan data akan berkurang menjadi 11.586 baris data.
- Dataset tidak memiliki missing value dan data duplikat
- Dataset terdapat outlier di beberapa fitur sehingga memerlukan penanganan yang lebih lanjut. 
- Dataset memiliki fitur numerik dan kategorikal. Numerik antara lain Temperature, Humidity, Wind Speed, Precipitation (%), Atmospheric Pressure, UV Index, Visibility (km). Dan kategorikal antara lain Cloud Cover, Season, Location, Weather Type.

### Variabel-variabel pada Dataset Cuaca adalah sebagai berikut:
- Temperature: Suhu yang dicatat dalam derajat Celcius. Mulai dari suhu yang dingin, sampai yang terpanas. Memiliki rata-rata 19,13°C dengan Minimum Tempraturenya -25°C dan maksimum tempraturenya 109°C. Rentang suhu ini menunjukkan adanya outlier, karena suhu maksimum 109°C dan tidak mungkin terjadi dalam kondisi cuaca normal di berbagai sehingga perlu dibersihkan dalam tahap preprocessing.
- Humidity: Kelembapan udara yang dicatat dalam persen (%). Memiliki rata-rata 68,71% dengan Minimum kelembapan 20% dan maksimum kelembapan 109%. Kelembapan udara tidak mungkin melebihi 100%, sehingga nilai maksimum ini juga merupakan outlier dan tidak mungkin terjadi dalam kondisi normal di berbagai sehingga perlu dibersihkan dalam tahap preprocessing. 
- Wind Speed: Kecepatan angin yang dicatat dalam km/jam. Memiliki rata-rata 9,83 km/h dengan Minimum kecepatan angin 0 km/ dan maksimum kecepatan angin 48,5 km/h. Kecepatan angin terlihat wajar, dengan nilai maksimum masih berada dalam rentang yang nyata untuk kondisi cuaca biasa. 
- Precipitation: Persentase curah hujan yang dicatat dalam persen (%). Memiliki rata-rata 53,64% dengan Minimum curah hujan 0% dan maksimum curah hujan 109%. Curah hujan dalam bentuk persentase tidak mungkin melebihi 100%, sehingga nilai maksimum ini juga merupakan outlier dan tidak mungkin terjadi dalam kondisi normal di berbagai sehingga perlu dibersihkan dalam tahap preprocessing. 
- Cloud Cover: Deskripsi tingkat tutupan awan. Kategori 'clear', 'partly cloudy', dan 'overcast' terlihat banyak, namun untuk 'cloudy' sedikit.
- Atmospheric Pressure: Tekanan atmosfer dalam hPa. Memiliki rata-rata 1005,83 hPa dengan Minimum tekanan atmosfer 800,12 hPa dan maksimum tekanan atmosfer 1199,21 hPa. Tekanan atmosfer ini berada dalam rentang yang normal untuk kondisi permukaan laut.
- UV Index: Indeks sinar ultraviolet, yang mengindikasikan kekuatan radiasi ultraviolet. Memiliki rata-rata 4,01 dengan Minimum UV index 0 dan maksimum UV index 14. Nilai indeks UV maksimum 14 menunjukkan paparan sinar UV yang sangat tinggi.
- Season: Musim saat data dicatat. Terdapat musim Winter, Autumn, Spring, dan Summer. Musim Winter mendominasi data, jumlah datanya jauh lebih banyak dibanding musim lain.
- Visibility: Jarak pandang dalam kilometer (km). Memiliki rata-rata 5,46 km dengan Minimum Tempraturenya 0 km dan maksimum tempraturenya 20 km. Tingkat visibilitas tampak realistis, dengan rata-rata penglihatan sekitar 5,5 km.
- Location: Lokasi geografis saat data dicatat. terdapat Kategori 'inland', 'mountain', dan 'coastal' yang masing-masing memiliki jumlah data yang cukup seimbang.
- Weather Type: Variabel target untuk klasifikasi, yang menunjukkan jenis cuaca. Memiliki kategori cuaca 'Rainy', 'Cloudy', 'Sunny', dan 'Snowy' dan masing-masing memiliki distribusi seimbang.

### Eksplorasi Data (EDA) & Visualisasi
Untuk memahami struktur dan pola dalam data, dilakukan beberapa teknik eksplorasi sebagai berikut:
- Histogram digunakan untuk melihat distribusi masing-masing fitur numerik.
- Heatmap korelasi membantu mengidentifikasi hubungan antar variabel numerik dan potensi multikolinearitas. 
    - Terdapat beberapa korelasi antara lain : 
        - yang cukup kuat : Humidity dengan Precipitation (0.64), Humidity dengan Wind Speed (0.41), Precipitation dengan Wind Speed (0.44), Temperature dengan UV Index (0.37), Visibility dengan UV Index (0.36)
        - yang cukup lemah : Humidity dengan Visibility (–0.48), Precipitation dengan Visibility (–0.46), Humidity dengan UV Index (–0.34), Temperature dengan Wind Speed (–0.07), Wind Speed dengan UV Index (–0.07). 
- Boxplot digunakan untuk mendeteksi outlier pada fitur numerik. Outlier yang terdeteksi kemudian dihapus untuk meningkatkan kualitas data dan akurasi model.

## Data Preparation
#### Langkah-langkah Persiapan Data
Dalam tahap ini, dilakukan beberapa proses untuk memastikan data siap digunakan dalam pemodelan machine learning:
- Tidak terdapat handling missing value dan data duplikat, dikarenakan pada saat data understanding tidak terdapat missing value dan data duplikat. 
- Outlier Removal : Dilakukan proses penghapusan outlier dikarenakan berdasarkan hasil eksplorasi menggunakan boxplot, sejumlah outlier pada fitur numerik berhasil diidentifikasi contohnya pada fitur temprature, wind speed, atmosphere pressure, dan visibility. pada proses ini, data yang mengandung outlier dihapus untuk menjaga konsistensi data serta meningkatkan akurasi model. Pembersihan ini berhasil menghilangkan sebagian besar nilai ekstrem tanpa menghilangkan variasi data.
- Encoding Fitur Kategorikal : Fitur kategorikal seperti Season, Location, Cloud Cover, dan Weather Type diubah menjadi bentuk numerik menggunakan Label Encoding, agar dapat diproses oleh algoritma machine learning. untuk kolom Weather type memiliki 3 nilai yaitu ['Sunny', 'Rainy', 'Cloudy'] dengan label encoder diubah menjadi [2, 1, 0]
- Splitting Data : Dataset dibagi menjadi dua bagian: 80% untuk data pelatihan dan 20% untuk data pengujian, guna mengevaluasi performa model.
- Feature Scaling : Semua fitur numerik seperti Temperature, Humidity, Wind Speed, Precipitation, Atmospheric Pressure, UV Index, dan Visibility dinormalisasi menggunakan MinMaxScaler. Normalisasi ini mengubah nilai-nilai fitur ke dalam rentang 0–1 agar setiap fitur berada dalam skala yang sama. Contoh nya adalah nilai 14.0 menjadi nilai 0.53684211 setelah dilakukan feature scalling. 


## Modeling
Dalam tahap ini, dilakukan pembangunan dan pelatihan beberapa model klasifikasi untuk memprediksi jenis cuaca berdasarkan fitur-fitur yang tersedia. Pemilihan model mempertimbangkan keseimbangan antara interpretabilitas, kompleksitas, dan akurasi.

#### Model yang Digunakan:
1. Logistic Regression : 


    bekerja dengan mengklasifikasikan berdasarkan probabilitas dari kelas target menggunakan fungsi sigmoid. Seperti memperkirakan kemungkinan suatu peristiwa terjadi, contoh : tipe cuaca seperti rainy, cloudy, dll berdasarkan dataset variabel yang diberikan. Untuk kasus ini adalah klasifikasi multikelas. Logistic Regression bekerja dengan mengestimasi koefisien untuk setiap fitur, dan membuat prediksi berdasarkan kombinasi linier dari fitur-fitur tersebut.

    Dengan Parameter max_iter=1000: untuk menentukan jumlah maksimum iterasi dalam proses optimasi. Nilai ini diperbesar dari default untuk memastikan konvergensi model. 

    Kelebihan dari Logistic Regression adalah Sederhana dan cepat dilatih, selain itu mudah untuk diinterpretasikan. Sedangkan kekurangannya adalah Kurang cocok untuk data dengan hubungan non-linear yang kompleks.

2. Decision Tree : 

    Dikarenakan Decision Tree adalah algoritma klasifikasi berbasis pohon maka algoritma ini bekerja dengan membagi data berdasarkan fitur-fitur tertentu menggunakan metrik. Proses pembentukan pohon dilakukan secara rekursif dengan memilih fitur dan nilai threshold terbaik pada setiap node, hingga mencapai kondisi tertentu seperti maksimum kedalaman atau jumlah minimum sampel. Proses dimulai dengan memilih fitur terbaik sebagai awal, lalu membuat cabang berdasarkan nilai-nilai fitur tersebut. Pada setiap cabang, model kembali memilih fitur terbaik dari subset data dan membagi lagi, hingga mencapai node akhir (leaf) yang menentukan kelas tipe cuaca dengan cara tersebut.

    Disini saya tidak mengatur apapun untuk parameter, sehingga saya membiarkan untuk default. 

    Kelebihan dari Decision Tree adalah kemudahan visualisasi dan pemahaman terhadap proses pengambilan keputusan yang dilakukan oleh model. sedangkan kekurangannya adalah Rentan terhadap overfitting. 

3. XGBoost Classifier : 

    Dikarenakan XGBoost adalah algoritma ensemble yang membangun model prediktif secara bertahap maka akan memprediksi tipe cuaca dengan membangun serangkaian pohon keputusan secara bertahap, di mana setiap pohon baru dibuat untuk memperbaiki kesalahan prediksi dari pohon-pohon sebelumnya. Proses yang disebut boosting ini merupakan proses di mana model belajar dari kesalahan residual sebelumnya dan memperkuat prediksi dengan penyesuaian bobot. Proses ini diulang hingga mencapai jumlah pohon tertentu dan hasil akhir prediksi cuaca seperti rainy, cloudy diperoleh dari gabungan prediksi seluruh pohon. Dengan teknik ini, XGBoost sangat efektif dalam menangani pola cuaca yang kompleks dan data yang tidak linear. 

    Dengan Parameter use_label_encoder=False digunakan untuk menonaktifkan encoder label default XGBoost agar kompatibel dengan sklearn. eval_metric='mlogloss' digunakan untuk mengukur performa klasifikasi multikelas dengan log loss.

    Kelebihan dari XGBoost adalah Performa tinggi, sangat baik untuk data kompleks. sedangkan kekurangannya adalah Butuh tuning parameter untuk performa optimal. 

## Evaluation

#### Matriks
Evaluasi dilakukan terhadap tiga model klasifikasi: Logistic Regression, Decision Tree, dan XGBoost dengan menampilkan laporan klasifikasi dan confusion matrix dengan menggunakan classification_report serta confusion matrix menggunakan metrik antara lain :
1. accuracy digunakan untuk memprediksi yang benar terhadap seluruh data. 
2. precision digunakan untuk memprediksi benar positif dibandingkan dengan keseluruhan hasil yang diprediksi positif
3. recall digunakan untuk melihat seberapa baik model dalam menangkap semua instance dari tiap kelas
4. f1-score digunakan dengan meratakan precision dan recall, berguna untuk menyeimbangkan keduanya.

Dengan matriks tersebut, model mendapatkan hasil evaluasi memberikan gambaran seberapa baik model mengenali masing-masing kelas cuaca. Metrik-metrik ini sangat relevan untuk proyek klasifikasi kondisi cuaca, karena untuk memprediksi tidak hanya akurat secara keseluruhan, tetapi juga seimbang dalam mengenali semua jenis kondisi cuaca, termasuk yang jarang terjadi. 

#### Hasil Evaluasi Model

- Logistic Regression : Menunjukkan performa yang cukup baik dengan akurasi 94%. Model ini mampu menyeimbangkan precision, recall, dan f1-score di keempat kelas, meskipun turun pada kelas cuaca ke-4 (label 3).
- Decision Tree : Berhasil meningkatkan performa dibanding Logistic Regression dengan akurasi 97%. Precision dan recall tinggi di seluruh kelas menunjukkan model ini mampu mengenali pola dengan baik.
- XGBoost Classifier : Mendapat hasil terbaik, dengan akurasi 97%, dan sedikit keunggulan pada recall untuk kelas pertama (label 0). Secara keseluruhan, model ini paling konsisten dan unggul dalam hal f1-score antar kelas.

#### Hubungan dengan Business Understanding

Dengan adanya proyek yang bertujuan untuk membangun sebuah model klasifikasi cuaca yang dapat memprediksi jenis cuaca berdasarkan input dari berbagai fiturnya seperti fitur numerik dan kategorikal ini sudah berhasil dan menjawab permasalahan dari berbagai sektor yang ada di indonesia seperti sektor pertanian, pariwisata, dll mengenai klasifikasi cuaca yang tentunya tidak menentu sehingga mendukung untuk pengambilan keputusan.

#### Model yang Paling Unggul

Dari hasil evaluasi, XGBoost menjadi model terbaik untuk menjawab problem statement yang telah dirumuskan sebelumnya:
- Model ini menjawab kebutuhan akan akurasi tinggi dan konsistensi prediksi di semua jenis kondisi cuaca.
- Semua goals seperti akurasi tinggi, stabil di seluruh kelas tercapai.
- Solusi yang diusulkan dapat berdampak nyata dan bisa diintegrasikan dengan sistem lainnya.

