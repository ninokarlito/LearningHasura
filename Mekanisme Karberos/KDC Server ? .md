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




