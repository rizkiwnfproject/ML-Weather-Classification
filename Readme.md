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

Dataset yang digunakan dalam proyek ini merupakan data yang berasal dari kaggle yang merepresentasikan kondisi cuaca secara umum. Data ini berisi 13.200 baris dan 11 kolom sebelum proses pembersihan, dan 11.586 baris data setelah proses pembersihan termasuk penghapusan outlier.

### Variabel-variabel pada Dataset Cuaca adalah sebagai berikut:
- Temperature: Suhu yang dicatat dalam derajat Celcius. Mulai dari suhu yang dingin, sampai yang terpanas.
- Humidity: Kelembapan udara yang dicatat dalam persen (%).
- Wind Speed: Kecepatan angin yang dicatat dalam km/jam.
- Precipitation: Persentase curah hujan yang dicatat dalam persen (%).
- Cloud Cover: Deskripsi tingkat tutupan awan.
- Atmospheric Pressure: Tekanan atmosfer dalam hPa.
- UV Index: Indeks sinar ultraviolet, yang mengindikasikan kekuatan radiasi ultraviolet.
- Season: Musim saat data dicatat.
- Visibility: Jarak pandang dalam kilometer (km).
- Location: Lokasi geografis saat data dicatat.
- Weather Type: Variabel target untuk klasifikasi, yang menunjukkan jenis cuaca.

### Eksplorasi Data (EDA) & Visualisasi
Untuk memahami struktur dan pola dalam data, dilakukan beberapa teknik eksplorasi sebagai berikut:
- Histogram digunakan untuk melihat distribusi masing-masing fitur numerik.
- Heatmap korelasi membantu mengidentifikasi hubungan antar variabel numerik dan potensi multikolinearitas.
- Boxplot digunakan untuk mendeteksi outlier pada fitur numerik. Outlier yang terdeteksi kemudian dihapus untuk meningkatkan kualitas data dan akurasi model.

## Data Preparation
#### Langkah-langkah Persiapan Data
Dalam tahap ini, dilakukan beberapa proses untuk memastikan data siap digunakan dalam pemodelan machine learning:
- Handling Missing Values : Setelah dilakukan pengecekan, tidak ditemukan data kosong atau nilai hilang, sehingga tidak diperlukan adanya proses imputasi.
- Encoding Fitur Kategorikal : Fitur kategorikal seperti Season, Location, Cloud Cover, dan Weather Type diubah menjadi bentuk numerik menggunakan Label Encoding, agar dapat diproses oleh algoritma machine learning.
- Feature Scaling : Semua fitur numerik seperti Temperature, Humidity, Wind Speed, Precipitation, Atmospheric Pressure, UV Index, dan Visibility dinormalisasi menggunakan MinMaxScaler. Normalisasi ini mengubah nilai-nilai fitur ke dalam rentang 0–1 agar setiap fitur berada dalam skala yang sama. 
- Outlier Removal : Berdasarkan hasil eksplorasi menggunakan boxplot, sejumlah outlier pada fitur numerik berhasil diidentifikasi dan dihapus untuk menjaga konsistensi data serta meningkatkan akurasi model.
- Train-Test Split : Dataset dibagi menjadi dua bagian: 80% untuk data pelatihan dan 20% untuk data pengujian, guna mengevaluasi performa model.

## Modeling
Dalam tahap ini, dilakukan pembangunan dan pelatihan beberapa model klasifikasi untuk memprediksi jenis cuaca berdasarkan fitur-fitur yang tersedia. Pemilihan model mempertimbangkan keseimbangan antara interpretabilitas, kompleksitas, dan akurasi.

#### Model yang Digunakan:
- Logistic Regression : Digunakan sebagai model baseline karena bersifat sederhana, cepat, dan efisien dalam menangani masalah klasifikasi multikelas. Pada model ini, mendapatkan akurasi sebesar 94%.
    - Parameter utama : max_iter=1000 digunakan untuk memastikan proses optimisasi konvergen, terutama saat fitur banyak atau data kompleks.
- Decision Tree : Merupakan model yang bersifat interpretatif dan mampu menangani hubungan non-linear antar fitur. Keunggulan utamanya adalah kemudahan visualisasi dan pemahaman terhadap proses pengambilan keputusan yang dilakukan oleh model. Pada model ini, mendapatkan akurasi sebesar 97%.
    - Parameter default digunakan dalam eksperimen awal.
- XGBoost Classifier : Merupakan algoritma ensemble berbasis gradient boosting yang dikenal dalam menghasilkan akurasi tinggi. XGBoost juga memiliki kemampuan penanganan overfitting dan efisiensi komputasi yang baik, menjadikannya pilihan utama untuk prediksi yang kompleks. Pada model ini, mendapatkan akurasi sebesar 97%.
    - Parameter utama : use_label_encoder=False digunakan untuk menonaktifkan encoder label default XGBoost agar kompatibel dengan sklearn. eval_metric='mlogloss' digunakan untuk mengukur performa klasifikasi multikelas dengan log loss.

## Evaluation
Evaluasi dilakukan terhadap tiga model klasifikasi: Logistic Regression, Decision Tree, dan XGBoost, menggunakan metrik accuracy, precision, recall, dan f1-score. Hasil evaluasi memberikan gambaran seberapa baik model mengenali masing-masing kelas cuaca.

- Logistic Regression : Menunjukkan performa yang cukup baik dengan akurasi 94%. Model ini mampu menyeimbangkan precision, recall, dan f1-score di keempat kelas, meskipun turun pada kelas cuaca ke-4 (label 3).
- Decision Tree : Berhasil meningkatkan performa dibanding Logistic Regression dengan akurasi 97%. Precision dan recall tinggi di seluruh kelas menunjukkan model ini mampu mengenali pola dengan baik.
- XGBoost Classifier : Mendapat hasil terbaik, dengan akurasi 97%, dan sedikit keunggulan pada recall untuk kelas pertama (label 0). Secara keseluruhan, model ini paling konsisten dan unggul dalam hal f1-score antar kelas.

