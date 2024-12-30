from documentation Hasura DDN(V3) -> https://hasura.io/docs/3.0/help/glossary/#immutable-build-runtime-system

### 1. Hasura DDN Glossary

## Hasura (V3)
untuk perubahan hasura v3 memiliki peningkatan signifikan pada mesin:
1. arsitektur baru
2. peralihan ke bahasa pemrograman rust
3. spesifikasi baru untuk bekerja dengan mesin.

karena spesifikasi barunya, mesin tsb sekarang dipisahkan
dari protokol API, seperti GraphQL dan untuk hasilnya dalama beberapa tahun mendatang
mesin GraphQL akan berkembang menjadi mesin GraphQL-API dan akhirnya mesin API.

## Hasura DDN
*Hasura DDN* adalah inovasi baru dalam Hasura v3 dan cloud yang terdistribusi secara global yang tersedia untuk API dan konektivitas data, memungkinkan untuk pengiriman data real-time dengan sangat cepat dan aman. Mesin runtime baru di Hasura DDN mengakses metadata berdasarkan permintaan, memungkinkan peningkatan isolasi dan skalabilitas.

DDN juga menyertakan bidang kendali baru yang terdiri dari *pembuatan metadata, CI/CD, komponen infrastruktur cloud, dan fitur kolaborasi.* Di v2, kami menggabungkan bidang kontrol dan bidang data

## Control Plane
*Bidang kontrol* dapat mengelola konfigurasi, orkestrasi, dan koordinasi elemen bidang data serta menyediakan alat untuk menulis metadata. Ia bertanggung jawab untuk menyiapkan, mengelola perilaku, kebijakan, dan aturan yang mengatur cara data diproses dan diteruskan di bidang data. Ini juga mengawasi perilaku sistem secara keseluruhan, mengelola titik akhir API, memelihara konfigurasi API, menangani mekanisme otentikasi dan kontrol akses, dan mengumpulkan analitik atau metrik yang terkait dengan penggunaan API.

## Data Plane
*Bidang data* dapat mengelola, menghandle atas permintaan dan respons API. Berikut ini adalah komponen utama bidang data:

- Mesin GraphQL Hasura v3: Mesin menerima permintaan API (misalnya kueri GraphQL), mengubahnya menjadi representasi perantara yang dapat ditangani konektor, dan membuat rencana untuk eksekusi kueri di berbagai sumber data.

- Konektor Hasura: Ini menangani eksekusi API yang sebenarnya. Mereka menerima representasi perantara dari mesin dan menggunakan mekanisme paling efisien untuk mengeksekusi kueri dan mengambil/memutasi data dari sumber data yang mendasarinya.

Kedua komponen di atas open sourced/bersumber terbuka.

## Supergraph
Supergraf yaitu arsitektur dan model operasi untuk membangun dan menskalakan beberapa domain data (atau subgraf) sebagai satu grafik entitas dan operasi data.

Supergraph dapat membantu dalam mendapatkan manfaat pendekatan monolitik terpusat (kohesi tinggi dan tata kelola yang mudah) pada model eksekusi layanan mikro gabungan (longgaran kopling dan penskalaan kepemilikan).

## Subgraph
Subgraph memungkinkan tim untuk membawa domain data yang mereka miliki ke dalam supergraf. Subgraf memiliki model izin, dan siklus hidup pengembangan perangkat lunak independen, dan dapat dikembangkan, diuji, dan dibangun secara independen. Supergraf menjamin integritas komposisi subgraf. Subgraf dianalogikan dengan layanan mikro yang dimiliki oleh tim tertentu.

## Hasura Metadata
Metadata Hasura memodelkan supergraf dan menentukan API untuk supergraf tersebut. Ini adalah konfigurasi yang disediakan secara deklaratif untuk membantu terhubung ke sumber data dan menyediakan API yang berfungsi. Ini memperkenalkan konstruksi pemodelan supergraf utama seperti Jenis, Model, Perintah, Izin, dan Hubungan, yang membantu dalam memahami dan menerapkan sistem yang selaras dengan domain dunia nyata yang ingin mereka wakili. Selain konstruksi pemodelan, metadata juga menentukan konfigurasi kunci seputar keamanan API, caching, penerapan, dan CI/CD, yang membantu menjelaskan keseluruhan sistem API untuk organisasi.

## .Hml (Hasura Metadata Language)
Ekstensi file untuk file yang sesuai dengan spesifikasi metadata Hasura untuk supergraph. Ini adalah turunan dari ekstensi .yaml (dan berbagi sintaks yang sama) dan memberikan manfaat yang sama seperti 1) keterbacaan, 2) struktur data, 3) komentar, dan 4) portabilitas, untuk menulis, memberi alasan, dan berbagi metadata.

## Subgraph Modeling
Tindakan menulis informasi agar sesuai dengan spesifikasi metadata Hasura dan proses mengidentifikasi, mendefinisikan, dan menyusun kumpulan elemen atau atribut supergraf yang berbeda.

## Immutable-Build Runtime System
Mesin runtime baru di Hasura DDN, yang mengakses metadata berdasarkan permintaan, memungkinkan peningkatan isolasi dan skalabilitas. Sistem pembangunan independen ini memungkinkan runtime yang menghilangkan masalah keadaan bersama dan cold start untuk meningkatkan kinerja.

## Data Source
Sumber data eksternal, database, atau layanan apa pun yang dapat dihubungkan ke Hasura DDN menggunakan agen Konektor Data. Setiap sumber data harus memiliki URL dan skema konektor

## Native Data Connector Specification (NDC Spec)
Spesifikasi standar yang memungkinkan Anda memperluas fungsionalitas server Hasura dengan menyediakan layanan web yang menyelesaikan sumber data dan logika bisnis baru dan membantu menentukan struktur metadata untuk API di Hasura DDN. Spesifikasi ini mendefinisikan tipe seperti koleksi, fungsi, dan prosedur yang membantu mendeskripsikan perilaku agen atau konektor yang terhubung ke sumber data pokok. Ini memberikan kerangka kerja dan pedoman tentang jenis titik akhir layanan web yang perlu diterapkan oleh konektor.

## Native Data Connectors
Agen konektor data yang mengintegrasikan Hasura dengan berbagai sumber dan layanan data eksternal dan didasarkan pada spesifikasi konektor data asli. Konektor data asli dapat berupa konektor resmi Hasura, terverifikasi oleh Hasura, atau konektor tidak terverifikasi.

## Push-Down Capabilities
Kemampuan Hasura DDN untuk mendelegasikan operasi kueri tertentu termasuk Otorisasi ke sumber data yang mendasarinya. Hal ini dapat meningkatkan optimasi dan kinerja kueri dan merupakan alasan mengapa konektor data di Hasura DDN disebut 'asli'.

## Connector Hub
Merujuk ke situs publik tempat semua Konektor Data Asli untuk Hasura DDN terdaftar. Pengguna dapat menemukan konektor, mendapatkan informasi lebih lanjut tentang fitur spesifiknya, dan menemukan dokumentasi tentang cara menggunakan setiap konektor dengan Hasura DDN.

## Model
Objek metadata yang penting untuk desain API di Hasura DDN. Model adalah entitas yang memiliki pemetaan langsung ke objek atau kumpulan konektor data asli yang mendasarinya.

Model menyertakan referensi ke tipe data dan menyertakan detail konfigurasi yang terkait dengan konfigurasi API, argumen, dan id global.

Ini mendukung operasi pilih, masukkan, perbarui dan hapus. Dalam operasi pemilihan, operasi kueri yang berbeda mencakup pemfilteran, agregasi, penomoran halaman, dan pembatasan

## Command
Entitas Hasura yang membantu merangkum logika bisnis dan mewakili tindakan yang dapat dilakukan yang mengembalikan beberapa jenis hasil. Ini secara langsung memetakan fungsi dan prosedur objek konektor data asli

## Relationship
Objek metadata di Hasura DDN yang mendefinisikan hubungan antara dua model atau antara model dan perintah. Ini memfasilitasi interkoneksi data

## Permission
Objek metadata di Hasura DDN yang mendefinisikan kontrol akses atau aturan otorisasi pada model dan perintah.

## Global ID
Mengacu pada ID global Relai yang mengkodekan tipe dan ID suatu objek dalam satu string. Di Hasura, hal ini ditentukan per model dan memungkinkan pengambilan objek apa pun secara langsung, apa pun jenis objeknya. Hasilnya adalah Anda mendapatkan bidang akar simpul dalam skema API GraphQL untuk digunakan dengan klien Relay.

## Collection
Koleksi adalah objek Spesifikasi Konektor Data Asli, yang merangkum bagian sumber data, menyediakan kemampuan kueri standar.

Setiap koleksi ditentukan berdasarkan namanya, argumen koleksi apa pun (perlu membuat parameterisasi koleksi), jenis objek (kumpulan bidang) dari barisnya, dan beberapa metadata tambahan yang terkait dengan batasan. Melacak koleksi menghasilkan pembuatan objek 'model' di metadata Hasura.

## Function
Fungsi adalah objek Spesifikasi Konektor Data Asli yang dapat dipanggil dengan argumen untuk mendapatkan hasil, dan tidak memiliki efek samping sehingga bersifat "hanya baca". Berbeda dengan koleksi, fungsi tidak mendeskripsikan batasan dan tidak memiliki tipe objek.

Melacak suatu fungsi menghasilkan pembuatan objek Command Supergraph di metadata Hasura.

## Procedure
Prosedur adalah objek spesifikasi konektor data asli, dan prosedur tersebut menentukan tindakan yang diterapkan konektor data dan dapat mengubah data serta memiliki efek samping lainnya. Setiap prosedur memiliki argumen dan tipe kembalian.

Melacak prosedur menghasilkan pembuatan objek Command di metadata Hasura.

## Build
Setiap perubahan metadata di Hasura DDN mewakili build yang tidak dapat diubah. Setiap build memiliki Titik Akhir GraphQL unik yang dapat diuji secara independen. Pembangunan ada di dalam proyek dan terdapat pemetaan satu-ke-banyak antara proyek dan pembangunan.

## Supergraph Config
Konfigurasi supergraph memberi tahu Hasura DDN cara membuat supergraph Anda. Konfigurasi akan berisi informasi seperti subgraf mana yang akan disertakan dan sumber daya mana yang akan digunakan untuk build

## Connect Config
Konfigurasi konektor memberi tahu Hasura DDN cara membuat konektor Anda. Ini akan berisi informasi seperti jenis konektor dan lokasi file konteks yang diperlukan untuk membuat konektor.

## DDN CLI (Command-Line Interface)
Alat di Hasura DDN yang memungkinkan pengembang berinteraksi dengan DDN dari baris perintah. Ini mendukung berbagai perintah untuk membuat build, melacak objek, dan menerapkan proyek

## VS Code Extension
Ekstensi Hasura VS Code mengaktifkan fitur seperti validasi sebaris metadata Hasura DDN tanpa harus membuat build, cuplikan perancah kode yang dapat digunakan untuk merangkai objek metadata DDN dengan cepat, pelengkapan otomatis cerdas yang menampilkan saran pelengkapan otomatis berdasarkan status proyek DDN saat ini, dan fitur lainnya seperti masuk ke definisi untuk objek metadata DDN yang saling terkait, dokumentasi saat mengarahkan objek metadata DDN apa pun, pohon proyek di bilah sisi yang menampilkan semua proyek DDN dan objek metadata yang ada di saat ini folder yang dibuka.

Sangat disarankan untuk mengunduh ekstensi kode VS saat bekerja dengan proyek DDN, ekstensi ini dapat diunduh dari pasar ekstensi VS Code.

## Metadata build service
Membuat build dari metadata dan membuatnya tersedia untuk Hasura v3 GraphQL Engine di edge agar dapat melayani permintaan API. Menyediakan penanganan kesalahan penting untuk debugging dan pemecahan masalah dengan cepat.

## Control plane cloud API
Komponen ini adalah layanan cloud dasar, yang memungkinkan pembuatan build, penerapan build, dan pengujian API Anda. Kami menganggap ini sebagai otak dari Konsol DDN dan CLI – komponen yang menggerakkan sebagian besar fungsi DX.

## DDN Console
Antarmuka di Hasura DDN yang menyediakan alat untuk visualisasi metadata, pengujian dan penerapan API, kolaborasi tim, dokumentasi, pelacakan, dan analitik.

## Cloud PAT
mengacu pada token autentikasi pribadi yang dibuat Hasura Cloud secara otomatis pada setiap pembuatan proyek baru. Hal ini memastikan bahwa API GraphQL selalu memiliki mekanisme keamanan. PAT yang dibuat secara otomatis disertakan dalam header API cloud_pat.
