 ## 1. Apa Itu Hasura DDN
**Hasura DDN** *(Data Delivery Network)* yaitu sebuah platform untuk menyederhanakan dalam pengembangan dan pengoperasian api data
terfederasi modern, agar memecahkan tantangan utama dalam prosesnya.

degan perkakas yang canggih dan alur kerja berbasis kode, Hasura DDN tidak sekadar peningkatan pada bagian akses data dalam siklus hidup *(lifecycle)* pengembangan produk, tetapi juga pengubah permainan yang lengkap dalam cara Anda membuat, menjalankan, serta mengelola API.

 ## 2. Ringkasan Hasura DDN
 Dengan menggunakan Hasura DDN dapat menghubungkan sumber data ke Hasura Engine secara mulus menggunakan standar metadata yang fleksibel dan konsep yang disebut konektor data asli. Arsitektur ini, yang dikenal sebagai supergraf data *(data supergraph)* , memungkinkan metode pendekatan yang 100% mengutamakan kode dengan pembuatan API instan.

 ## 3. Konsep Inti ***(Core Concepts)***
 Hasura DDN menggunakan konsep Supergraf Data dalam pengelolaan. **Supergraf data** adalah kerangka kerja yang menyatukan semua subgraf ke dalam satu API yang aman, memungkinkan terciptanya aplikasi yang mencakup berbagai sumber data, layanan, API pihak ketiga, logika bisnis.
 Bagaimana cara membuat supergraf data?
 pada saat menambahkan subgraf ke proyek hasura, Hasura DDN secara otomatis membuat supergraf dari semua sumber data Anda.

 Subgraf lebih dari sekedar sumber data tunggal, **Subgraf** ialah semua metadata yang dibutuhkan dan bertindak sebagai entitas mandiri yang dapat ditulis, dimiliki, dipelihara, dan dibangun secara independen oleh tim individu, untuk kemudian menjadi bagian yang saling berhubungan dari API terpadu.
 Bagaimana cara membuat subgraf?
 Setelah menghubungkan sumber data, kemudian dapat membuat metadata menggunakan Hasura CLI dan ekstensi Hasura VS Code . Metadata ini kemudian dibuat pada instans Hasura DDN kita, yang digunakan untuk melayani API GraphQL kita.

![image](https://github.com/user-attachments/assets/7826d848-5d2e-4a43-8ce6-5a9b5d126412)
![image](https://github.com/user-attachments/assets/b6d704cc-5e4f-469d-9ce9-f100a43ff9d6)


## 4. Arsitektur Hasura DDN
Dibandingkan dengan Hasura v2, peningkatan arsitektur fundamental dimasukkan ke dalam Hasura v3, dimana waktu pembuatan dan waktu proses dipisahkan menjadi komponen yang berbeda. Bidang kontrol membangun metadata proyek dan membuatnya tersedia untuk mesin Hasura v3 yang berjalan pada bidang data.
![image](https://github.com/user-attachments/assets/60b2356d-eec9-4750-9fdc-7f291dc6cea9)

### 1. Control Plane
Pengembang berinteraksi dengan bidang kontrol Hasura DDN untuk membuat supergraph build . Setiap supergraph build menghasilkan API GraphQL yang unik, yang dihosting oleh bidang data. Sebagai pengembang, dapat menggunakan konsol Hasura pada bidang kontrol untuk memvisualisasikan supergraph dan berinteraksi dengan API GraphQL. Control Plane juga menyediakan fitur pemantauan dan observasi. Konsol memungkinkan dapat menambahkan kolaborator sehingga bisa mengundang pengembang lain untuk berkontribusi pada supergraph dan juga untuk berbagi GraphQL API dengan konsumen.

### 2. Data Plane
Hasura v3 Engine dan konektor data berjalan pada bidang data. Bidang data Hasura DDN menjalankan versi mesin v3 yang disempurnakan yang mampu melayani beberapa API GraphQL secara bersamaan. Ini adalah runtime seperti tanpa server di mana konfigurasi untuk mengeksekusi permintaan GraphQL dimuat sesuai permintaan dan dibuang setelah memproses permintaan. Hal ini membuat runtime sangat efisien dan sangat skalabel.

Konektor tertentu juga menggunakan strategi serupa untuk menangani kumpulan koneksi secara efisien, hanya membuatnya sesuai permintaan.
Fitur ini tersedia di GCP, AWS, dan Azure, dan juga dapat diterapkan pada Hasura DDN yang dihosting sendiri, dengan catatan infrastrukturnya mendukung kemampuan jaringan yang diperlukan.

### Menjelajah Supergraph anda 
Halaman penjelajah konsol *GUI berbasis web Hasura* menawarkan:
* **Visualisasi Komprehensif**: Lihat representasi visual API Anda yang lengkap dan real-time, termasuk hubungan dan izin.
* **Dokumentasi yang Dihasilkan Secara Otomatis**: Hasilkan dan perbarui dokumentasi API secara otomatis, memastikan konsistensi dan keakuratan.
* **Kolaborasi yang Ditingkatkan**: Dorong komunikasi dan koordinasi yang lebih baik antar tim dengan alat visual yang intuitif dan digunakan bersama.

### Berinteraksi dengan Supergraph
Hasura DDN menawarkan solusi komprehensif melalui penjelajah GraphiQL-nya, yang dirancang untuk menyederhanakan dan mempercepat proses interaksi API.

Dengan menggunakan penjelajah GraphiQL untuk membuat dan menguji kueri langsung di dalam konsol, menyediakan:
* **Definisi Skema**: Lihat seluruh skema GraphQL dan dokumentasi untuk semua kueri dan mutasi yang tersedia.
* **Pengujian Kueri Terintegrasi**: Uji kueri dengan header dan lihat hasil waktu nyata, semuanya di satu tempat.
* **Pelacakan Bawaan**: Lacak kueri secara instan untuk mengidentifikasi hambatan kinerja dan optimalkan secara efisien.
* **Alur Kerja yang Disederhanakan**: Hemat waktu dan kurangi peralihan konteks dengan menyediakan semua yang Anda butuhkan dalam satu antarmuka.

### Memantau Supergraph
Hasura DDN menyederhanakan pemantauan kinerja dengan menyediakan:
* **Wawasan Instan**: Akses metrik dan jejak utama secara real-time di halaman wawasan.
* **Pemantauan Terintegrasi**: Pantau kinerja langsung dalam konsol tanpa memerlukan alat tambahan.
* **Optimasi Proaktif**: Mengidentifikasi dan mengatasi masalah kinerja dengan cepat, memastikan pengalaman API supergraph yang lancar dan efisien.

### Otorisasi, Otentikasi dan Hasura 
Dengan menggunakan variabel sesi yang diteruskan melalui *JWT* atau *webhook* dari layanan autentikasi, Hasura dapat dapat membuat aturan kontrol akses terperinci untuk menentukan dengan tepat data apa yang dapat diakses pengguna.
Autentikasi dapat dikonfigurasi melalui token web JSON (JWT) atau layanan webhook dan dapat diintegrasikan dengan penyedia manapun  (seperti, Auth0 , Firebase Auth , AWS Cognito , solusi khusus, dll.) untuk memverifikasi pengguna dan menetapkan variabel sesi yang kemudian mengontrol akses ke data.
