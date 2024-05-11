
## PROJECT PCD_UTS_202231076_NURFADILAH

Citra kontras mengacu pada gambar yang memiliki perbedaan yang jelas antara area terang dan area gelap. Kontras dalam konteks citra mengukur seberapa jauh perbedaan intensitas antara piksel-piksel yang berdekatan satu sama lain. Semakin besar perbedaan intensitas antara piksel-piksel, semakin tinggi kontrasnya.

Dalam gambar atau citra, kontras sangat penting karena mempengaruhi kejelasan dan ketajaman detail. Citra dengan kontras yang tinggi cenderung memiliki detail yang lebih tajam dan lebih mudah untuk dibedakan antara objek-objek yang berbeda. Di sisi lain, citra dengan kontras rendah mungkin terlihat datar dan sulit untuk membedakan detail-detail kecil.

Deteksi warna pada citra adalah proses untuk mengidentifikasi dan mengekstraksi piksel-piksel yang memiliki nilai warna tertentu sesuai dengan kriteria yang ditentukan. Hal ini dapat dilakukan dengan berbagai metode, salah satunya adalah menggunakan ambang batas (thresholding).

Berikut adalah langkah-langkah umum dalam deteksi warna pada citra menggunakan ambang batas:

1. Baca Citra dan Konversi ke Format yang Sesuai
Pertama, baca citra yang akan dianalisis dan pastikan untuk mengonversinya ke format yang sesuai, misalnya dari BGR ke RGB jika menggunakan OpenCV di Python.

2. Pisahkan Saluran Warna
Pisahkan citra ke dalam saluran warna merah (Red Channel), hijau (Green Channel), dan biru (Blue Channel) jika diperlukan. Ini penting jika Anda ingin fokus pada deteksi warna tertentu.

3. Tentukan Kriteria Warna
Tentukan kriteria warna yang ingin Anda deteksi. Misalnya, jika Anda ingin mendeteksi objek yang berwarna merah, Anda perlu menentukan rentang nilai untuk saluran warna merah yang dianggap sebagai warna merah.

4. Ambang Batas (Thresholding)
Gunakan metode ambang batas untuk menentukan piksel-piksel yang sesuai dengan kriteria warna yang telah ditetapkan. Ini dapat dilakukan dengan mengatur ambang batas tertentu untuk saluran warna yang relevan.

5. Analisis dan Tampilan Hasil
Setelah deteksi warna dilakukan, Anda dapat menganalisis hasilnya, misalnya dengan menampilkan citra hasil deteksi atau melakukan tindakan lanjutan seperti segmentasi objek berdasarkan warna yang terdeteksi.

6. Validasi dan Penyesuaian
Penting untuk melakukan validasi hasil deteksi warna dan jika diperlukan, melakukan penyesuaian parameter seperti nilai ambang batas atau kriteria warna untuk meningkatkan akurasi deteksi.

Histogram adalah representasi visual dari distribusi intensitas piksel dalam sebuah citra. Ini adalah grafik yang menunjukkan jumlah piksel untuk setiap nilai intensitas (skala abscissa), mulai dari nilai intensitas minimum hingga maksimum yang mungkin dalam citra. Histogram sangat berguna dalam analisis citra karena memberikan wawasan tentang kontras, kecerahan, dan distribusi warna dalam citra.

### DETEKSI WARNA PADA CITRA

#### import library
import cv2
import matplotlib.pyplot as plt

citra = cv2.imread("dila.jpg")

#### Konversi Img dari BGR ke RGB
img_rgb = cv2.cvtColor(citra, cv2.COLOR_BGR2RGB)

#### Menampilkan Img dan Deteksi Warna
red_channel = img_rgb[:,:,0]
green_channel = img_rgb[:,:,1]
blue_channel = img_rgb[:,:,2]

plt.figure(figsize=(15,5))

plt.subplot(1, 4, 1)
plt.imshow(img_rgb)
plt.title('Citra Kontras') # Judul subplot 
plt.axis('off') # Menonaktifkan sumbu x dan y

plt.subplot(1, 4, 2)
plt.imshow(red_channel, cmap='gray')
plt.title('Red Channel')
plt.axis('off')

plt.subplot(1, 4, 3)
plt.imshow(green_channel, cmap='gray')
plt.title('Green Channel')
plt.axis('off')

plt.subplot(1, 4, 4)
plt.imshow(blue_channel, cmap='gray') 
plt.title('Blue Channel')
plt.axis('off')

plt.show()

#### Analisis
1. Citra Asli (Citra Kontras):

Ini adalah gambar asli yang direpresentasikan dalam mode warna RGB.
Ketika kita menampilkan gambar ini, kita dapat melihat warna-warna yang berbeda seperti merah, hijau, dan biru yang membentuk citra.

2. Saluran Warna Merah (Red Channel):

Saluran ini mengandung informasi tentang intensitas warna merah dalam gambar.
Ketika kita menampilkan saluran warna merah dalam skala abu-abu (grayscale), kita hanya melihat tingkat kecerahan yang berkorelasi dengan intensitas warna merah dalam citra asli.
Daerah-daerah dengan intensitas warna merah yang tinggi akan muncul lebih terang, sementara daerah dengan intensitas rendah akan muncul lebih gelap.

3. Saluran Warna Hijau (Green Channel):

Saluran ini mengandung informasi tentang intensitas warna hijau dalam gambar.
Ketika kita menampilkan saluran warna hijau dalam skala abu-abu (grayscale), kita hanya melihat tingkat kecerahan yang berkorelasi dengan intensitas warna hijau dalam citra asli.
Daerah-daerah dengan intensitas warna hijau yang tinggi akan muncul lebih terang, sementara daerah dengan intensitas rendah akan muncul lebih gelap.

4. Saluran Warna Biru (Blue Channel):

Saluran ini mengandung informasi tentang intensitas warna biru dalam gambar.
Ketika kita menampilkan saluran warna biru dalam skala abu-abu (grayscale), kita hanya melihat tingkat kecerahan yang berkorelasi dengan intensitas warna biru dalam citra asli.
Daerah-daerah dengan intensitas warna biru yang tinggi akan muncul lebih terang, sementara daerah dengan intensitas rendah akan muncul lebih gelap.

### Menampilkan histogram dari img RGB dan setiap saluran warna
red_hist = cv2.calcHist([red_channel], [0], None, [256], [0,256])
green_hist = cv2.calcHist([green_channel], [0], None, [256], [0,256])
blue_hist = cv2.calcHist([blue_channel], [0], None, [256], [0,256])
original_hist = cv2.calcHist([img_rgb], [0], None, [256], [0,256])


##### Menampilkan histogram
plt.subplot(2, 4, 5)
plt.plot(original_hist, color='black')
plt.title('Citra Kontras')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')
plt.xlim([0, 256])

plt.subplot(2, 4, 6)
plt.plot(red_hist, color='red')
plt.title('Red Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')
plt.xlim([0, 256])

plt.subplot(2, 4, 7)
plt.plot(green_hist, color='green')
plt.title('Green Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')
plt.xlim([0, 256])

plt.subplot(2, 4, 8)
plt.plot(blue_hist, color='blue')
plt.title('Blue Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')
plt.xlim([0, 256])

plt.tight_layout()
plt.show()

#### Berikut adalah analisis rinci dari histogram yang dihasilkan:

1. Histogram Citra Asli (Citra Kontras):

Histogram citra asli menunjukkan distribusi intensitas piksel dari seluruh saluran warna (merah, hijau, biru).
Dari histogram ini, kita dapat melihat seberapa seragam distribusi intensitas piksel di seluruh rentang warna.
Puncak-puncak yang tinggi menunjukkan area di citra yang memiliki intensitas tertentu yang sering muncul, sementara lembah-lembah menunjukkan area dengan intensitas yang jarang muncul.

2. Histogram Saluran Warna Merah (Red Histogram):

Histogram saluran warna merah menunjukkan distribusi intensitas piksel yang khusus untuk saluran warna merah.
Puncak-puncak yang tinggi pada histogram merah menunjukkan area di citra dengan intensitas merah yang dominan.
Jika ada puncak yang sangat tinggi di sekitar nilai tertentu, itu menunjukkan area dengan warna merah yang sangat terkonsentrasi.

3. Histogram Saluran Warna Hijau (Green Histogram):

Histogram saluran warna hijau menunjukkan distribusi intensitas piksel yang khusus untuk saluran warna hijau.
Puncak-puncak yang tinggi pada histogram hijau menunjukkan area di citra dengan intensitas hijau yang dominan.
Jika ada puncak yang sangat tinggi di sekitar nilai tertentu, itu menunjukkan area dengan warna hijau yang sangat terkonsentrasi.

4. Histogram Saluran Warna Biru (Blue Histogram):

Histogram saluran warna biru menunjukkan distribusi intensitas piksel yang khusus untuk saluran warna biru.
Puncak-puncak yang tinggi pada histogram biru menunjukkan area di citra dengan intensitas biru yang dominan.
Jika ada puncak yang sangat tinggi di sekitar nilai tertentu, itu menunjukkan area dengan warna biru yang sangat terkonsentrasi.

### URUTKAN AMBANG BATAS TERKECIL SAMAPAI DENGAN TERBESAR

import cv2
import matplotlib.pyplot as plt

#### Baca gambar dan konversi ke RGB
citra = cv2.imread("dila.jpg")
img_rgb = cv2.cvtColor(citra, cv2.COLOR_BGR2RGB)

#### Pisahkan saluran warna
red_channel = img_rgb[:,:,0]
green_channel = img_rgb[:,:,1]
blue_channel = img_rgb[:,:,2]

#### Buat ambang batas terkecil hingga terbesar
thresholds = [50, 100, 150, 200]
thresholded_images = []

for threshold in thresholds:
    _, thresholded = cv2.threshold(red_channel, threshold, 255, cv2.THRESH_BINARY)
    thresholded_images.append(thresholded)

#### Urutkan ambang batas dari terkecil hingga terbesar
sorted_thresholds_images = sorted(zip(thresholds, thresholded_images))
plt.figure(figsize=(15, 5))

for i, (threshold, thresholded) in enumerate(sorted_thresholds_images[:4]):
    plt.subplot(1, 4, i + 1) 
    plt.imshow(thresholded, cmap='gray')
    plt.title(f'Threshold: {threshold}')
    plt.axis('off')

plt.show()

#### Nilai ambang
Berikut adalah nilai ambang batas yang diperoleh dari kode yang Anda berikan:

1. Ambang Batas untuk Threshold 50:
   - Nilai Ambang Batas: 50
   - Alasan: Nilai ambang batas ini menentukan intensitas piksel pada saluran warna merah (Red Channel) yang harus melebihi 50 agar dianggap sebagai bagian yang relevan dalam gambar hasil thresholding.

2. Ambang Batas untuk Threshold 100:
   - Nilai Ambang Batas: 100
   - Alasan: Nilai ambang batas ini menentukan intensitas piksel pada saluran warna merah (Red Channel) yang harus melebihi 100 agar dianggap sebagai bagian yang relevan dalam gambar hasil thresholding.

3. Ambang Batas untuk Threshold 150:
   - Nilai Ambang Batas: 150
   - Alasan: Nilai ambang batas ini menentukan intensitas piksel pada saluran warna merah (Red Channel) yang harus melebihi 150 agar dianggap sebagai bagian yang relevan dalam gambar hasil thresholding.

4. Ambang Batas untuk Threshold 200:
   - Nilai Ambang Batas: 200
   - Alasan: Nilai ambang batas ini menentukan intensitas piksel pada saluran warna merah (Red Channel) yang harus melebihi 200 agar dianggap sebagai bagian yang relevan dalam gambar hasil thresholding.

Nilai ambang batas yang diberikan pada masing-masing threshold digunakan untuk memisahkan piksel dengan intensitas warna yang berbeda. Semakin tinggi nilai ambang batas, semakin sedikit piksel yang akan dianggap sebagai bagian yang relevan dalam gambar hasil thresholding karena hanya piksel dengan intensitas warna yang melebihi nilai ambang batas yang ditetapkan yang akan ditampilkan dalam gambar hasil thresholding.


### TAHAPAN PENYELASAIN PROJECT

Projek di atas adalah tentang deteksi warna pada sebuah citra menggunakan OpenCV dan matplotlib di Python. Prosesnya dapat dibagi menjadi beberapa tahap yang dijelaskan di bawah ini:

#### 1. Import Library
Mula-mula, dilakukan import library yang akan digunakan, yaitu OpenCV (`cv2`) untuk pemrosesan citra dan matplotlib (`plt`) untuk visualisasi data.

#### 2. Baca Gambar dan Konversi ke RGB
Pada tahap ini, citra dibaca menggunakan OpenCV dan kemudian dilakukan konversi dari format warna BGR (yang digunakan oleh OpenCV) ke format warna RGB yang lebih umum.


#### 3. Tampilkan Gambar dan Deteksi Saluran Warna
Dilakukan pemisahan saluran warna dari citra RGB menjadi saluran warna merah (Red Channel), hijau (Green Channel), dan biru (Blue Channel). Selanjutnya, gambar-gambar ini ditampilkan bersamaan untuk melihat perbedaan intensitas warna di setiap saluran.


#### 4. Deteksi Warna dengan Ambang Batas
Langkah selanjutnya adalah melakukan deteksi warna menggunakan ambang batas (thresholding) pada saluran warna merah (Red Channel). Dilakukan iterasi pada beberapa nilai ambang batas, dan gambar hasil thresholding ditampilkan.


#### 5. Analisis Histogram
Pada tahap terakhir, dilakukan analisis histogram dari saluran warna merah (Red Channel), hijau (Green Channel), dan biru (Blue Channel), serta histogram dari gambar asli (Citra Kontras). Histogram ini menunjukkan distribusi intensitas piksel untuk setiap saluran warna.

