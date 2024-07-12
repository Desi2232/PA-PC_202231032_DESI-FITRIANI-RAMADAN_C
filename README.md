# PA-PC_202231032_DESI-FITRIANI-RAMADAN_C

Nama : Desi Fitriani Ramadan

NIM  : 202231032

Pengolahan Citra Digital (C) 

### 1. Teori yang mendukung mengenai projek terkait

Proyek pemrosesan citra ini menggunakan berbagai teknik dasar dalam bidang pengolahan citra digital. Pemrosesan citra digital adalah disiplin ilmu yang melibatkan manipulasi gambar melalui algoritma komputer. Proyek ini memanfaatkan perpustakaan OpenCV dan Matplotlib dalam bahasa pemrograman Python untuk mengolah dan memvisualisasikan gambar.

Pemrosesan citra digital mencakup berbagai metode untuk memodifikasi dan menganalisis citra agar dapat diekstraksi informasi yang bermanfaat atau ditingkatkan kualitas visualnya. Dalam proyek ini, beberapa teknik dasar pemrosesan citra digunakan, termasuk rotasi, perubahan ukuran, pemotongan, pembalikan, dan translasi.

#### Rotasi Citra

Rotasi citra adalah proses memutar gambar di sekitar titik pusatnya. Ini sering digunakan dalam berbagai aplikasi, seperti pengenalan pola dan pemrosesan citra medis, untuk menyesuaikan orientasi gambar. Pada proyek ini, fungsi cv2.getRotationMatrix2D digunakan untuk membuat matriks rotasi, yang kemudian diterapkan pada citra menggunakan cv2.warpAffine. Rotasi sebesar 45 derajat dilakukan untuk mengubah orientasi gambar.

#### Perubahan Ukuran (Resize)

Mengubah ukuran citra melibatkan pengubahan dimensi gambar. Ini penting dalam berbagai aplikasi seperti penyesuaian ukuran input dalam jaringan saraf tiruan atau mengurangi resolusi untuk mempercepat pemrosesan. Pada proyek ini, fungsi cv2.resize digunakan untuk mengubah ukuran citra menjadi dimensi yang lebih kecil.

#### Pemotongan (Crop)

Pemotongan citra adalah proses mengambil bagian tertentu dari gambar. Ini sering digunakan untuk fokus pada area yang relevan atau menghapus bagian yang tidak diinginkan. Dalam proyek ini, bagian dari citra asli dipotong menggunakan slicing array untuk mendapatkan sub-citra yang lebih kecil.

#### Pembalikan (Flip)

Pembalikan citra adalah proses membalikkan gambar secara horizontal atau vertikal. Teknik ini digunakan dalam augmentasi data untuk memperbanyak data pelatihan dalam pembelajaran mesin. Pada proyek ini, cv2.flip digunakan untuk membalikkan citra secara horizontal.

#### Translasi (Translation)

Translasi citra adalah proses menggeser gambar ke posisi baru dalam ruang koordinat. Ini dapat digunakan untuk menyesuaikan posisi objek dalam gambar. Pada proyek ini, sebuah matriks translasi dibuat menggunakan numpy, dan cv2.warpAffine digunakan untuk menerapkan translasi pada citra.

#### Visualisasi Citra

Matplotlib adalah perpustakaan plotting yang digunakan untuk menampilkan citra dalam proyek ini. Ini memungkinkan visualisasi hasil dari setiap teknik pemrosesan yang diterapkan. Dengan menggunakan subplot, hasil dari berbagai teknik pemrosesan dapat ditampilkan dalam satu figure untuk perbandingan yang mudah.

Dengan memanfaatkan teknik-teknik dasar pemrosesan citra dan alat visualisasi yang disediakan oleh OpenCV dan Matplotlib, proyek ini memberikan pemahaman dasar tentang bagaimana gambar dapat dimanipulasi dan dianalisis secara digital. Teknik-teknik ini membentuk dasar bagi aplikasi yang lebih kompleks dalam pengenalan pola, analisis citra medis, penglihatan komputer, dan banyak lagi.

#### Pemrosesan Citra

Pemrosesan citra adalah teknik manipulasi data pixel untuk meningkatkan atau mengekstraksi informasi. Teknik-teknik kunci yang sering digunakan meliputi:

1. *Transformasi Citra:* Mengubah struktur geometris citra, seperti rotasi dan skala.
2. *Peningkatan Citra:* Meningkatkan tampilan visual citra, sering menggunakan teknik seperti penyaringan.
3. *Ekstraksi Fitur:* Mengidentifikasi bagian penting dari citra, seperti tepi atau bentuk.

#### Perpustakaan yang Digunakan

1. *OpenCV (Open Source Computer Vision Library):* Menyediakan alat untuk visi komputer secara real-time. Banyak digunakan untuk tugas seperti transformasi citra, penyaringan, dan ekstraksi fitur.
2. *Matplotlib:* Perpustakaan plotting untuk membuat visualisasi statis, animasi, dan interaktif dalam Python.

### 2. Menjelaskan tahapan cara menyelesaikan projek secara rinci

#### Tahap 1: Mengimpor Perpustakaan yang Diperlukan
Langkah pertama dalam proyek ini adalah mengimpor perpustakaan yang diperlukan untuk pemrosesan citra dan visualisasi:

#### *Codingan:*

import cv2

import matplotlib.pyplot as plt

import numpy as np

#### *Penjelasan:* 
- cv2: Digunakan untuk pemrosesan citra.
- matplotlib.pyplot: Digunakan untuk menampilkan gambar.
- numpy: Digunakan untuk operasi numerik.

#### Tahap 2: Memuat dan Menampilkan Gambar Asli
Langkah ini melibatkan pemuatan gambar dari sistem file dan menampilkannya menggunakan Matplotlib:

#### *Codingan:*

image_path = 'MyPhoto.jpg'

image = cv2.imread(image_path)

image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.imshow(image)

plt.title("Citra Asli")

plt.axis('on')

plt.show()

#### *Penjelasan:*

- cv2.imread(image_path): Membaca gambar dari path yang diberikan.

- cv2.cvtColor(image, cv2.COLOR_BGR2RGB): Mengonversi gambar dari format BGR (default OpenCV) ke format RGB (default Matplotlib).

- plt.imshow(image): Menampilkan gambar.

- plt.title("Citra Asli"): Menambahkan judul pada gambar.

- plt.axis('on'): Menampilkan sumbu.

#### Tahap 3: Merotasi Gambar

Langkah ini melibatkan rotasi gambar sebesar 45 derajat:

#### *Codingan:*

(h, w) = image.shape[:2]

center = (w / 2, h / 2)

M = cv2.getRotationMatrix2D(center, 45, 1.0)

rotated_image = cv2.warpAffine(image, M, (w, h))

plt.imshow(rotated_image)

plt.title("After Rotated")

plt.axis('on')

plt.show()

#### *Penjelasan:*

- image.shape[:2]: Mendapatkan dimensi gambar.

- cv2.getRotationMatrix2D(center, 45, 1.0): Membuat matriks rotasi dengan sudut 45 derajat dan skala 1.0.

- cv2.warpAffine(image, M, (w, h)): Menerapkan matriks rotasi pada gambar.

#### Tahap 4: Mengubah Ukuran Gambar

Langkah ini melibatkan perubahan ukuran gambar menjadi 50x200 piksel:

#### *Codingan:*

resized_image = cv2.resize(image, (50, 200)) 

plt.imshow(resized_image)

plt.title("After Resized")

plt.axis('on')

plt.show()

#### *Penjelasan:*

- cv2.resize(image, (50, 200)): Mengubah ukuran gambar menjadi 50x200 piksel.

#### Tahap 5: Memotong Gambar

Langkah ini melibatkan pemotongan bagian tertentu dari gambar:

#### *Codingan:*

cropped_image = image[0:250, 0:250]

plt.imshow(cropped_image)

plt.title("After Cropped")

plt.axis('on')

plt.show()

#### *Penjelasan:*

- image[0:250, 0:250]: Memotong bagian 250x250 piksel dari gambar asli.

#### Tahap 6: Membalikkan Gambar

Langkah ini melibatkan pembalikan gambar secara horizontal:

#### *Codingan:*

flipped_image = cv2.flip(image, 1)

plt.imshow(flipped_image)

plt.title("After Flipped")

plt.axis('on')

plt.show()

#### *Penjelasan:*

- cv2.flip(image, 1): Membalikkan gambar secara horizontal (parameter 1 menunjukkan pembalikan horizontal).

#### Tahap 7: Menerjemahkan Gambar

Langkah ini melibatkan penerjemahan (pergeseran) gambar:

#### *Codingan:*

M = np.float32([[1, 0, 90], [0, 1, 30]])

translated_image = cv2.warpAffine(image, M, (w, h)) 

plt.imshow(translated_image)

plt.title("After Translated")

plt.axis('on')

plt.show()

#### *Penjelasan:*

- np.float32([[1, 0, 90], [0, 1, 30]]): Membuat matriks translasi untuk menggeser gambar 90 piksel ke kanan dan 30 piksel ke bawah.

- cv2.warpAffine(image, M, (w, h)): Menerapkan matriks translasi pada gambar.

#### Tahap 8: Menampilkan Semua Hasil

Langkah terakhir adalah menampilkan semua hasil pemrosesan citra dalam satu figure menggunakan subplot:

#### *Codingan:*

fig, axs = plt.subplots(2, 3, figsize=(15, 10))

###

axs[0, 0].imshow(image)

axs[0, 0].set_title("Citra Asli")

axs[0, 0].axis('on')

###

axs[0, 1].imshow(rotated_image)

axs[0, 1].set_title("After Rotated")

axs[0, 1].axis('on')

###

axs[0, 2].imshow(resized_image)

axs[0, 2].set_title("After Resized")

axs[0, 2].axis('on')

###

axs[1, 0].imshow(cropped_image)

axs[1, 0].set_title("After Cropped")

axs[1, 0].axis('on')

###

axs[1, 1].imshow(flipped_image)

axs[1, 1].set_title("After Flipped")

axs[1, 1].axis('on')

###

axs[1, 2].imshow(translated_image)

axs[1, 2].set_title("After Translated")

axs[1, 2].axis('on')

###

plt.tight_layout()

plt.show()

#### *Penjelasan:*

- plt.subplots(2, 3, figsize=(15, 10)): Membuat figure dengan 2 baris dan 3 kolom subplot.

- axs[i, j].imshow(...): Menampilkan gambar pada subplot tertentu.

- axs[i, j].set_title(...): Menambahkan judul pada subplot tertentu.

- axs[i, j].axis('on'): Menampilkan sumbu pada subplot tertentu.

- plt.tight_layout(): Menyesuaikan tata letak subplot agar tidak saling tumpang tindih.

- plt.show(): Menampilkan figure.

### 3. Menambahkan Jurnal Terkait (Opsional)

Berikut adalah beberapa referensi jurnal terkait pemrosesan citra menggunakan Python, OpenCV, dan Matplotlib:

*"An Overview of OpenCV: The Python Image Processing Library"* - Artikel ini memberikan gambaran umum tentang OpenCV dan aplikasinya dalam pemrosesan citra.

*"Image Processing Techniques Using Python: A Review"* - Sebuah tinjauan tentang berbagai teknik pemrosesan citra yang diimplementasikan dalam Python.

*"Real-Time Image Processing Using Python and OpenCV"* - Membahas implementasi aplikasi pemrosesan citra real-time menggunakan Python dan OpenCV.
