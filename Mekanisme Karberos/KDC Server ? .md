## 1. Pengertian Karberos
Karberos adalah protocol autentikasi jaringan yang dirancang untuk memberikan autentikasi yang kuat bagi aplikasi klien dan server menggunakan kriptografi kunci rahasia. Solusi ini biasanya digunakan di antara stack Hadoop untuk autentikasi di seluruh ekosistem software.

## 2. Alur Skema Sederhana Karberos
![image](https://github.com/user-attachments/assets/6c4dfd5d-6c5c-4bfa-9b31-a126be967245)

## Garis Besar Karberos
Protocol autentifikasi jaringan yang menggunakan prinsip trusted third party, maksudnya baik client atau server dalam mengotentifikasi seseorang yang login mempercayakan pihak ketiga(Key Distribution Center/KDC). Dalam aksinya karberos melakukan otentikasi dengan menggunakan ticket yang dikeluarkan oleh pihak ketiga (KDC Server) dan authenticator yang dibuat sendiri oleh client. Ticket tsb bersift reusable artinya dapat digunakan berulang-ulang sampai waktu kadaluarsanya habis.

## Kelebihan
- Keamanan Tinggi: Data dilindungi oleh enkripsi simetris yang kuat.
- Single Sign-On (SSO): Pengguna cukup login sekali untuk mengakses berbagai layanan
  
## Kelemahan
- Jika server Down, maka tidak ada yang dapat mengakses server karena akses terhadap jaringan harus melalui proses otorisasi karberos
- Rawan terhadap serangan Denial-of-Service(DOS), Server tidak perlu benar-benar dibuat crash, cukup dibanjiri request maka server akan kesulitan menghandle request.

**KDC (Key Distribution Center)** adalah komponen utama dalam protokol otentikasi Kerberos yang berfungsi sebagai server pusat untuk menangani distribusi kunci dan tiket autentikasi. KDC bertanggung jawab untuk memastikan bahwa komunikasi antara klien dan layanan dilakukan dengan aman melalui mekanisme tiket dan enkripsi.

### Fungsi KDC
KDC memiliki dua fungsi utama yang diimplementasikan dalam dua komponen internalnya:

1. **Authentication Server (AS)**  
   - **Tugas utama**: Memvalidasi identitas pengguna atau klien.  
   - Ketika klien mengirimkan permintaan autentikasi, AS:
     - Memeriksa kredensial klien (misalnya username dan password yang terenkripsi).
     - Jika valid, AS menerbitkan **Tiket Granting Ticket (TGT)**, yang digunakan untuk permintaan layanan selanjutnya.

2. **Ticket Granting Server (TGS)**  
   - **Tugas utama**: Mengeluarkan **Service Ticket** kepada klien berdasarkan TGT yang sudah dimiliki.  
   - Ketika klien ingin mengakses layanan tertentu (misalnya, file server atau database), TGS:
     - Memvalidasi TGT.
     - Menerbitkan Service Ticket yang akan digunakan untuk mengakses layanan tersebut.

### Cara Kerja KDC
1. **Authentication Server (AS)**:  
   - Klien mengirimkan permintaan autentikasi ke AS.  
   - AS memverifikasi identitas klien dan memberikan TGT.  
   - TGT ini terenkripsi menggunakan kunci rahasia KDC, sehingga hanya KDC yang dapat membacanya.

2. **Ticket Granting Server (TGS)**:  
   - Klien menggunakan TGT untuk meminta tiket baru yang spesifik untuk layanan tertentu.  
   - TGS memeriksa TGT, memastikan klien memiliki izin, dan mengeluarkan **Service Ticket**.  
   - Service Ticket ini dienkripsi menggunakan kunci rahasia layanan yang dituju.

3. **Server Layanan**:  
   - Klien memberikan Service Ticket ke server layanan (misalnya, server file).  
   - Server layanan memvalidasi tiket dan mengizinkan akses jika tiket valid.

### Alasan Menggunakan KDC
- **Keamanan Terpusat**: Semua otentikasi dan pengelolaan tiket dikelola oleh KDC, sehingga meminimalkan risiko kebocoran data di jaringan.
- **Efisiensi**: Klien hanya perlu berkomunikasi dengan KDC untuk mendapatkan tiket yang dapat digunakan untuk mengakses berbagai layanan.
- **Fleksibilitas**: Mendukung Single Sign-On (SSO), di mana pengguna cukup login satu kali untuk mendapatkan akses ke beberapa layanan.

### Tantangan dalam KDC
- **Single Point of Failure**: Jika KDC tidak tersedia (misalnya, down), maka seluruh sistem Kerberos tidak dapat berfungsi.
- **Keamanan KDC**: Karena KDC menyimpan semua kunci rahasia, KDC menjadi target utama serangan. Oleh karena itu, KDC harus diamankan dengan sangat baik.

KDC biasanya diimplementasikan dalam jaringan perusahaan dan diinstal pada server yang memiliki sumber daya tinggi untuk menangani beban permintaan tiket secara efisien. 

Apakah Anda memerlukan penjelasan tambahan tentang instalasi atau pengaturan KDC? 😊



