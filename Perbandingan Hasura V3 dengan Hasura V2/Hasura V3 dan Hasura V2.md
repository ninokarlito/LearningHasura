 ## 1. Apa Itu Hasura DDN
**Hasura DDN** *(Data Delivery Network)* yaitu sebuah platform untuk menyederhanakan dalam pengembangan dan pengoperasian api data
terfederasi modern, agar memecahkan tantangan utama dalam prosesnya.

degan perkakas yang canggih dan alur kerja berbasis kode, Hasura DDN tidak sekadar peningkatan pada bagian akses data dalam siklus hidup *(lifecycle)* pengembangan produk, tetapi juga pengubah permainan yang lengkap dalam cara Anda membuat, menjalankan, serta mengelola API.

 ## 2. Dasar/Cara Kerja dan arsitektur Hasura DDN
 Dengan menggunakan Hasura DDN dapat menghubungkan sumber data anda ke Hasura Engine secara mulus menggunakan standar metadata yang fleksibel dan konsep yang disebut konektor data asli. Arsitektur ini, yang dikenal sebagai supergraf data *(data supergraph)* , memungkinkan metode pendekatan yang 100% mengutamakan kode dengan pembuatan API instan.

 engan Hasura DDN, Anda dapat dengan mudah menghubungkan dan menggabungkan data dari semua sumber, sehingga menghilangkan silo data. Anda akan memiliki visibilitas yang jelas terhadap kueri Anda, kontrol keamanan yang kuat, dan sistem yang andal dan tangguh. Nikmati fleksibilitas untuk melakukan penskalaan sesuai kebutuhan, menyederhanakan alur kerja pengembangan Anda dengan alat CI/CD yang canggih, dan mengoptimalkan kinerja dengan kueri asli, sekaligus menjaga data Anda tetap aman dan logika bisnis Anda tetap terpusat.








 1. Metadata-Driven API Layer
 Di inti Hasura DDN, API yang dihasilkan dikendalikan oleh metadata, bukan kode secara langsung. Metadata ini mencakup:
 Schema API: Menggambarkan struktur data, seperti tabel, relasi, dan model.Data Catalog: Mendokumentasikan sumber data yang tersedia dan bagaimana mereka dapat diakses.
 Permissions: Mengatur izin akses granular untuk setiap bagian data yang diekspos melalui API.
 Metadata ini memungkinkan Hasura untuk secara otomatis membangun API tanpa harus menulis kode API manual. Hal ini memudahkan pengelolaan data di berbagai sumber tanpa menambah beban kerja pada pengembang.

2. Federated Data Access
Hasura DDN memungkinkan federasi akses data dari berbagai tim atau domain yang berbeda. Dengan federasi ini:
Tim bisa mengelola dan mengakses data mereka secara independen.
Metadata setiap tim dikelola secara modular dan dapat diintegrasikan ke dalam satu API secara federatif.
Supergraph: Hasura DDN menyatukan berbagai metadata dari beberapa sumber ke dalam satu "supergraph," memungkinkan akses data yang terintegrasi untuk semua sumber tersebut​(
Hasura GraphQL Engine)​
(Database Trends and Applications).

3. CI/CD Multi-Tim
Dalam arsitektur ini, setiap tim dapat bekerja pada metadata mereka sendiri dalam repositori terpisah dan menjalankan siklus CI/CD secara independen. Setiap perubahan metadata diuji dalam konteks "supergraph" secara keseluruhan untuk memastikan integrasi yang mulus dan deteksi konflik lebih awal​(
Database Trends and Applications).

4. Hierarchical Access Control
Sistem kontrol akses hierarkis yang domain-sentris memungkinkan pengembang untuk membuat perubahan pada metadata di level domain, tetapi hanya admin domain yang dapat menerapkan perubahan tersebut pada "supergraph" produksi. Ini memberikan fleksibilitas bagi tim untuk bekerja secara mandiri sambil tetap menjaga keamanan dan pengendalian di level produksi​(
Database Trends and Applications).

5. Skema Registry dan Changelog
Hasura DDN menyediakan alat untuk manajemen evolusi skema API, seperti:
Registry Skema: Memudahkan manajemen perubahan skema dari berbagai sumber data.
Changelog: Alat ini membantu pengembang untuk mengidentifikasi perubahan yang aman atau berpotensi merusak dari setiap versi skema, memberikan kontrol lebih baik dalam mengelola API yang berkembang​(
Hasura GraphQL Engine).

## Cara Kerja:

-Inisialisasi Supergraph: Pengembang memulai dengan membuat supergraph yang merupakan API komposit, menggabungkan berbagai sumber data dan metadata. Supergraph ini berfungsi sebagai gateway tunggal untuk mengakses seluruh data yang tersebar di berbagai sumber.

-Pembangunan Metadata: Dengan menggunakan CLI atau dashboard Hasura, metadata dari sumber data diintrospeksi dan ditambahkan ke supergraph. Metadata ini yang kemudian membentuk dasar API.

-Federasi dan Sinkronisasi Metadata: Setiap tim yang bekerja pada bagian metadata mereka dapat menyinkronkan hasil kerja mereka ke supergraph utama tanpa harus mengganggu pekerjaan tim lain.

-Penyebaran: Setelah semua elemen supergraph diuji dan siap, API tersebut dapat dideploy baik di lingkungan cloud Hasura atau di infrastruktur lokal.

Hasura v3 membawa sejumlah pembaruan signifikan dibandingkan Hasura v2, terutama dengan peralihan ke arsitektur Data Delivery Network (DDN). Berikut perbedaan utamanya:

## 3. Perbedaan fitur Hasura V3 & V2
1. **Autentikasi dan Otorisasi**:
   - Hasura v3 menawarkan mekanisme autentikasi yang lebih fleksibel, termasuk autentikasi berbasis JWT dan webhook. V3 juga memperkenalkan kontrol akses berbasis peran yang lebih detail, memungkinkan pengaturan izin hingga tingkat baris dan kolom.

2. **Kinerja dan Skalabilitas**:
   - V3 mengoptimalkan eksekusi query API dan caching dengan DDN, yang meningkatkan kinerja serta mengurangi latensi. Arsitektur DDN memungkinkan aplikasi untuk menangani beban tinggi dan mengaktifkan deployment tanpa downtime.

3. **Model Harga**:
   - Pada Hasura v3, harga didasarkan pada model aktif. Hanya model yang menerima lebih dari 1.000 permintaan per bulan yang dikenakan biaya, memberikan prediksi biaya yang lebih jelas dan menghindari pembayaran untuk model yang tidak aktif.

4. **Deployment dan CI/CD**:
   - V3 mempercepat deployment dengan fitur CI/CD instan, perubahan metadata langsung, dan tanpa downtime. Fitur ini juga memungkinkan pengontrolan versi metadata yang lebih baik, memudahkan pengelolaan perubahan.

5. **Manajemen Metadata dan API**:
   - Di v3, manajemen metadata lebih efisien dengan pendekatan berbasis kode. Pengembang dapat mendefinisikan seluruh skema API secara deklaratif dan mengontrol versi metadata dengan fitur kolaborasi yang lebih baik.

6. **Native Data Connectors (NDCs)**:
   - Hasura v3 mendukung integrasi yang lebih luas dengan sumber data eksternal menggunakan Native Data Connectors, memungkinkan penggabungan berbagai sumber data ke dalam satu supergraph.
   - Supergraf adalah arsitektur dan model operasi untuk membangun dan menskalakan beberapa domain data sebagai grafik tunggal dari entitas dan operasi yang dapat disusun

Dengan peningkatan-peningkatan ini, Hasura v3 menjadi lebih fleksibel, scalable, dan lebih hemat biaya dibandingkan versi sebelumnya.

## Keunggulan dan kekurangan

### **Keunggulan Hasura v2**:

1. **Sederhana dan Mudah Dikelola**:
   - **Hasura v2** cocok untuk pengembangan cepat dengan kebutuhan sederhana, seperti membangun GraphQL API dari database PostgreSQL tanpa perlu menulis banyak kode backend. 
   - Arsitekturnya lebih mudah untuk diatur dan digunakan untuk tim kecil dengan lingkungan pengembangan yang tidak terlalu kompleks.

2. **Stabilitas**:
   - Sebagai versi yang telah lebih lama digunakan, **Hasura v2** memiliki basis pengguna yang lebih luas dan stabilitas yang sudah teruji di berbagai aplikasi komersial. 

3. **Harga yang Lebih Transparan**:
   - Model harga **v2** berdasarkan pada jumlah query yang dijalankan, memberikan perkiraan biaya yang lebih mudah diprediksi untuk banyak kasus penggunaan yang sudah ada.

### **Kekurangan Hasura v2**:

1. **Kurang Skalabilitas**:
   - **v2** tidak dirancang untuk menangani aplikasi besar yang tersebar secara global dengan query caching atau pengoptimalan distribusi data. 
   - Tidak ada fitur seperti **DDN** yang dapat mengatasi latensi dalam permintaan dari berbagai lokasi geografis.

2. **Pengelolaan Metadata yang Terbatas**:
   - Pengelolaan metadata dalam **v2** masih bergantung pada konsol atau database metadata, yang dapat membatasi kolaborasi tim dan menyebabkan tantangan dalam hal CI/CD otomatis.

---

### **Keunggulan Hasura v3**:

1. **Performa dan Skalabilitas Tinggi**:
   - **Hasura v3** memiliki performa yang lebih baik berkat **Data Delivery Network (DDN)**, yang menyediakan jaringan global dengan caching dan eksekusi query yang dioptimalkan, memberikan pengalaman API yang lebih cepat dan scalable tanpa perlu downtime.
   
2. **Pengelolaan Metadata Lebih Fleksibel**:
   - Di **v3**, metadata sepenuhnya dikelola melalui **CLI dan ekstensi VS Code**, dengan kemampuan untuk memantau dan mengontrol versi metadata, sehingga pengembang bisa bekerja dengan lebih kolaboratif dan efisien.

3. **Model Harga Berbasis Penggunaan Aktif**:
   - **Hasura v3** menawarkan model harga berdasarkan "model aktif", artinya hanya model data yang digunakan secara aktif yang dikenakan biaya. Ini memberikan fleksibilitas biaya yang lebih besar, terutama untuk sistem yang memiliki banyak model tidak aktif.

4. **Native Data Connectors (NDCs)**:
   - Memungkinkan integrasi dengan lebih banyak jenis sumber data dan API eksternal, memberi fleksibilitas lebih besar untuk membangun "supergraph" yang menggabungkan banyak sumber data.

5. **CI/CD Instan dan Tanpa Downtime**:
   - **v3** memperkenalkan kemampuan CI/CD yang lebih cepat dan seamless, memungkinkan deployment metadata secara real-time tanpa menghentikan aplikasi atau sistem.

### **Kekurangan Hasura v3**:

1. **Lebih Kompleks untuk Setup Awal**:
   - **Hasura v3** memiliki arsitektur yang lebih kompleks, terutama dengan fitur federasi data dan **DDN**. Ini bisa membuat konfigurasi awal lebih menantang bagi tim kecil atau aplikasi dengan kebutuhan sederhana.

2. **Biaya Lebih Tinggi pada Skala Besar**:
   - Walaupun model harga v3 berbasis model aktif, penggunaan pada skala besar dengan banyak model aktif dapat meningkatkan biaya secara signifikan dibandingkan **v2**, terutama jika aplikasi membutuhkan banyak sumber data dan entitas yang selalu digunakan.

3. **Penggunaan Metadata yang Lebih Berfokus pada CLI**:
   - Walaupun CLI memberikan kontrol penuh terhadap metadata, ini bisa menjadi hambatan bagi pengguna yang terbiasa dengan pendekatan GUI yang lebih sederhana pada **v2**.

---

### Kesimpulan:
- **Hasura v2** lebih cocok untuk proyek kecil hingga menengah yang membutuhkan solusi sederhana, cepat, dan stabil.
- **Hasura v3** ideal untuk aplikasi skala besar yang membutuhkan performa tinggi, federasi data, dan integrasi global yang kompleks dengan biaya yang lebih fleksibel, terutama jika diprioritaskan pada model data aktif.
