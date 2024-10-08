 ## 1. Apa Itu Hasura DDN
**Hasura DDN** *(Data Delivery Network)* yaitu platform data terfederasi yang dirancang untuk memudahkan dalam mengakses ke berbagai sumber
data dengan pendekatan berbasis metadata. Pengembang dapat juga mengelola API dan data secara terstruktur melalui metadata sehingga memungkinkan
pengelolaan lebih cepat dan terstandarisasi.

 Hasura DDN berfokus pada manajemen metadata yang dimana pengembang bisa memodelkan domain,entitas, dan hubungan data melalui metadata. 
tidak hanya mempercepat pembuatan API, tetapi juga meningkatkan tata kelola data,sehingga memudahkan manajemen izin, penggunaan data,
serta mengurangi kompleksitas dalam menghubungkan berbagai sistem data.

 ## 2. Cara Kerja dan Arsitektur
 Tujuan utamanya yaitu untuk menyediakan akses data yang terintegrasi dan aman dari berbagai sumber data yang heterogen, seperti SQL,NoSQL,
 layanan API, dan event streams. Berikut adalah beberapa elemen utama dari arsitektur dan cara kerjanya

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
