# Project 1: Face Recognition (Gender Classification)

Proyek ini menampilkan beragam percobaan arsitektur dan algoritma Convolitional Neural Network (CNN) dalam Computer Vision melalui implementasi klasifikasi gender menggunakan dataset CelebA. Dengan memanfaatkan teknik deep learning, model ini dilatih untuk memprediksi gender dengan akurasi berdasarkan atribut wajah.

## 🚀 Sorotan Utama:

    Teknik: Menggunakan teknik computer vision dengan library Tensorflow dan Keras.
    Model: Menggunakan arsitektur model deep learning VGG16, VGG19, GoogleNet, ResNet50 dan ResNet101.
    Kinerja: Mencapai prediksi gender terbaik dan akurat pada arsitektur ResNet50 dan ResNet101.

Jelajahi kode dan hasil untuk mendapatkan wawasan tentang dunia pengenalan wajah dan klasifikasi gender!

📝 Catatan: Proyek ini merupakan bagian dari Bootcamp Computer Vision oleh Indonesia AI.

## ★ Introduction

### Background

Identifikasi gender dari data pengguna menjadi semakin penting dalam berbagai bidng, termasuk dalam bisnis dan privasi. Pemodelan deep learning menawarkan pendekatan yang kuat dan adaptif untuk mengatasi tantangan ini, memungkinkan sebuah sistem untuk belajar pola yang kompleks dari data yang besar dan bervariasi.

### Problem Statement

Pemodelan deep learning menjanjikan solusi kuat untuk klasifikasi gender, namun terdapat tantangan dari ketidakpastian representasi gender dan ketidakseimbangan dataset. Terdapat variasi budaya/ras cukup sulit untuk dikenali, sementara ketidakseimbangan dataset dapat menyebabkan bias. Pada repositori ini, kita akan mengeksplorasi upaya untuk mencapai klasifikasi gender yang lebih akurat melalui pemodelan deep learning.
  
## ★ Getting Started

### 1. Data collection & Preparation

#### 🔍 Dataset : [CelebA (Celebrity Faces Attributes)](https://mmlab.ie.cuhk.edu.hk/projects/CelebA.html)

<img align="left" src="https://mmlab.ie.cuhk.edu.hk/projects/CelebA/intro.png" alt="Deskripsi Gambar" width="200" height="120">
Dataset diambil dari CelebA (Celebrity Faces Attributes), Dataset merupakan kumpulan data gambar wajah selebriti yang terdiri dari 200 ribu gambar wajah dari kurang lebih 10 ribu selebriti yang berbeda dengan 40 list attribute menjadi dasar proyek ini. Dalam pemrosesan kami menyaring data sebanyak 5000 gambar dengan attribute ‘Male’ yang merepresentasikan kelas Male dan Female. Kemudian menganalisis jumlah sebaran data dan melakukan split data menjadi data training, validation dan testing.

##### Data management

<p align="center">
  <img src="https://raw.githubusercontent.com/nadyanvl/gender_recognition/main/assets/Data%20Distribution.png" alt="Grafik Sebaran Data" width="400" height="300" style="margin-right: 20px; margin-bottom: 10px;" />
  <img src="https://raw.githubusercontent.com/nadyanvl/gender_recognition/main/assets/Data%20Splitting.png" alt="Data Split" width="500" height="300" />
</p>


### 2. Data Augmentation 

Untuk meningkatkan keragaman dataset pelatihan dan meningkatkan ketangguhan model, teknik augmentasi data berikut diterapkan selama pra-pemrosesan gambar:

    rescale=1.0 / 255 (Normalization)
    rotation_range=20
    width_shift_range=0.2
    height_shift_range=0.2
    horizontal_flip=True
    validation_split=0.2

Strategi augmentasi ini berkontribusi pada dataset pelatihan yang lebih beragam dan umum, meningkatkan kemampuan model untuk belajar dan berperforma baik pada berbagai input.

### 3. Model Development

#### * Base Model :
##### VGG19:
- Merupakan model arsitektur Convolutional Neural Network (CNN) yang dikembangkan oleh Visual Graphics Group (VGG) dari Universitas Oxford.
- Memiliki 19 layer, termasuk lapisan konvolusi dan lapisan fully connected.
- Dikenal dengan struktur yang dalam dan simetris.

##### VGG16
- Serupa dengan VGG19, VGG16 adalah model arsitektur CNN yang dikembangkan oleh Visual Graphics Group (VGG) dari Universitas Oxford.
- Memiliki 16 layer, termasuk lapisan konvolusi dan lapisan fully connected.
- Digunakan dalam banyak tugas penglihatan komputer dan pengenalan gambar.

##### ResNet50
- ResNet50 adalah bagian dari keluarga model ResNet (Residual Network) yang dikembangkan oleh Microsoft Research.
- Memiliki 50 layer dan dikenal dengan penggunaan blok residu, yang memudahkan pelatihan model yang sangat dalam.

##### ResNet101
- Mirip dengan ResNet50, ResNet101 adalah versi yang lebih besar dengan 101 layer.
- Didesain untuk mengatasi masalah degradasi kinerja yang mungkin terjadi pada model yang sangat dalam.

##### GoogleNet 
- GoogleNet, atau Inception, adalah model arsitektur CNN yang dikembangkan oleh Google.
- Terkenal dengan penggunaan modul Inception, yang menggunakan filter konvolusi dengan berbagai ukuran.

#### * Hyperparameter :

    Optimizer: Adam
    Learning rate: 0.0001
    Image Size: 218 x 178
    Batch Size: 32
    Epoch : 25
    Callbacks: Early Stopping, Model Checkpoint
    Loss Function : Binary Crossentropy
    Metrics : Accuracy

### 4. Training & Optimization

Pada tahap ini, dilakukan pelatihan dan optimasi model menggunakan beberapa arsitektur yang berbeda, yaitu VGG16, VGG19, ResNet50, ResNet101, dan GoogleNet (Kaggle Model). Proses ini dilakukan untuk mencari arsitektur yang memberikan hasil terbaik pada dataset CelebA.

#### * Proses Pelatihan

    Setiap model diinisialisasi dengan bobot awal.
    3200 data gambar dengan beragam augmentasi digunakan untuk melatih model.
    Pengoptimalan dilakukan dengan menggunakan algoritma transfer learning dan loss function yang sesuai.

#### * Grafik Pelatihan

##### 📚 VGG16 

<img align="center" src="https://raw.githubusercontent.com/nadyanvl/gender_recognition/main/assets/VGG16.png" alt="VGG16" width="800" height="400">

##### 📚 VGG19

<img align="center" src="https://raw.githubusercontent.com/nadyanvl/gender_recognition/main/assets/VGG19.png" alt="VGG19" width="800" height="400">

##### 📚 ResNet50

<img align="center" src="https://raw.githubusercontent.com/nadyanvl/gender_recognition/main/assets/ResNet50.png" alt="ResNet50" width="800" height="400">


##### 📚 ResNet101

<img align="center" src="https://raw.githubusercontent.com/nadyanvl/gender_recognition/main/assets/ResNet101.png" alt="ResNet101" width="800" height="400">


##### 📚 GoogleNet

<img align="center" src="https://raw.githubusercontent.com/nadyanvl/gender_recognition/main/assets/GoogleNet.png" alt="GoogleNet" width="800" height="400">


#### * Evaluasi Model

Setelah pelatihan, model dievaluasi menggunakan dataset validasi untuk mengukur akurasi hasil prediksi. Hasil evaluasi ini mencakup akurasi validasi dari setiap arsitektur model yang diuji.

#### * Tabel Validation Accuracy

Berikut adalah tabel yang menunjukkan data akurasi validasi dari setiap arsitektur model:
<img align="center" src="https://raw.githubusercontent.com/nadyanvl/gender_recognition/main/assets/val%20accuracy.png" alt="val accuracy" width="1000" height="500">

## ★ The Results

### Perbandingan Test Results

Pada tahap ini, hasil pengujian model dari setiap algoritma dari fine tuning dan transfer learning dibandingkan untuk mendapatkan pemahaman yang lebih baik tentang kinerja relatif masing-masing model. Grafik di bawah ini memvisualisasikan hasil pengujian dari setiap algoritma pada dataset CelebA. Data yang diukur adalah akurasi test pada setiap algoritma selama pengujian. 

<p align="center">
  <img src="https://raw.githubusercontent.com/nadyanvl/gender_recognition/main/assets/Model%20Accuraacy%20Fine%20Tuning.png" alt="Grafik accuracy fine tuning" width="500" height="400" style="margin-right: 20px; margin-bottom: 10px;" />
  <img src="https://raw.githubusercontent.com/nadyanvl/gender_recognition/main/assets/Model%20Accuracy%20Transfer%20Learning.png" alt="Grafik accuracy transfer learning" width="500" height="400" />
</p>

Dari hasil train dan evaluation, terlihat bahwa ResNet101 mencapai akurasi validasi tertinggi, menunjukkan bahwa arsitektur ini mungkin merupakan pilihan yang baik untuk tugas klasifikasi pada dataset CelebA.

### Inference Time

Pada tahap ini, waktu inference dari setiap model diperhitungkan untuk membandingkan kecepatan model dalam memproses data uji. Berikut data inference time pada setiap model dari pengujian fine tuning dan transfer learning :

    Fine Tuning :
    VGG19 : 12 s
    VGG16 : 12 s
    ResNet50: 13 s
    ResNet101: 12 s
    GoogleNet: 14s

    Transfer Learning  :   
    VGG19 : 17 s
    VGG16 : 15 s
    ResNet50: 14 s
    ResNet101: 13 s
    GoogleNet: 12s

### Prediction Results on Test Data
Berikut adalah beberapa gambar yang diambil dari data tes dan kemudian dilakukan prediksi gender menggunakan model terbaiik dari segi akurasi tertinggi dan inference time tercepat yaitu ResNet101 :

<img align="center" src="https://raw.githubusercontent.com/nadyanvl/gender_recognition/main/assets/predict%20data%20test.png" alt="Predict Test" width="1000" height="800">

### Real World Application : [(DEPLOYMENT)](https://s.id/GenderRecog)

Pada tahap ini, kita akan mendeploy model ResNet101 menggunakan Gradio in HuggingFace untuk menyajikan antarmuka pengguna yang sederhana untuk penggunaan model. Gradio menyediakan cara mudah untuk membangun antarmuka pengguna interaktif untuk model machine learning. Dengan menggunakan Gradio in HuggingFace, kita dapat dengan mudah membuat antarmuka yang intuitif, memberikan prediksi gender secara langsung melalui antarmuka web yang dapat diakses pada link diatas. Dibawah ini merupakan tampilan hasil dari prediksi gender secara real :

<img align="center" src="https://raw.githubusercontent.com/nadyanvl/gender_recognition/main/assets/deploy.png" alt="Deployment" width="1000" height="500">


Project ini dikerjakan secara kolaboratif oleh kelompok CV D -Alan Turing, Beberapa Notebook yang dikerjakan oleh anggota Tim dapat diakses pada [FOLDER NOTEBOOK](https://github.com/nadyanvl/gender_recognition/tree/main/notebook)

Dan notebook utama yang digunakan untuk merangkum performa setiap model dapat diakses pada [NOTEBOOK UTAMA](https://github.com/nadyanvl/gender_recognition/blob/main/notebook/Satriaji/Satriaji_project1.ipynb)