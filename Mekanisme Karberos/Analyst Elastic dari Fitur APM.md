### Analyst Elastic dari Fitur APM
![image](https://github.com/user-attachments/assets/d2a1784e-00f0-4270-bd23-e5e523b8de88)

---
dashboard **Elastic Observability** dengan fokus pada transaksi di aplikasi **Hasura**. Berikut adalah analisis dari interface yang terlihat:



## **Elemen Utama dalam Tampilan**
1. **Tab Observability:**
   - Anda berada di modul *Observability* yang dirancang untuk memantau kinerja aplikasi, log, dan infrastruktur secara menyeluruh.

2. **Service: `hasura`:**
   - Anda sedang memantau layanan `hasura`, yang menunjukkan transaksi GraphQL endpoint `/v1/graphql`.

3. **Tab Navigasi:**
   - **Transactions:** Berisi detail transaksi termasuk durasi, performa, atau error yang terjadi.
   - **Dependencies:** Memetakan ketergantungan layanan terhadap layanan lain.
   - **Errors:** Menampilkan kesalahan yang terjadi pada layanan.
   - **Metrics:** Memantau metrik seperti durasi respon, permintaan per detik, dll.
   - **Infrastructure:** Memberikan gambaran tentang host atau infrastruktur yang mendukung layanan.

4. **Query Filter:**
   - bisa memfilter data dengan query, misalnya `transaction.duration.us > 300000` untuk menemukan transaksi dengan durasi lebih dari 300ms.

5. **Waktu dan Perbandingan:**
   - Analisis mencakup waktu **30 menit terakhir** dengan perbandingan ke **hari sebelumnya**.

6. **SLO (Service Level Objective):**
   - Menyediakan opsi untuk membuat tujuan tingkat layanan guna memastikan performa tetap sesuai target.

---

## **Langkah Analisis**
Berikut langkah-langkah untuk menganalisis performa atau masalah menggunakan dashboard ini:

### **1. Monitor Durasi Transaksi**
- Gunakan query seperti:
  ```
  transaction.duration.us > 300000
  ```
  untuk menemukan transaksi yang memakan waktu lama (lebih dari 300ms).

### **2. Analisis Kesalahan**
- Pindah ke tab **Errors** untuk mengidentifikasi:
  - Jumlah error yang terjadi.
  - Jenis error (misalnya, error 500 atau 400).
  - Endpoint mana yang paling sering mengalami error.

### **3. Pemantauan Performa**
- Pada tab **Metrics**, cek metrik berikut:
  - **Rata-rata durasi transaksi.**
  - **Permintaan per detik (requests per second).**
  - **Beban server atau infrastruktur.**

### **4. Ketergantungan Layanan**
- Gunakan tab **Dependencies** untuk memetakan apakah ada layanan atau database yang memengaruhi performa.

### **5. Deteksi Anomali**
- Gunakan fitur **Anomaly Detection** untuk menemukan pola yang tidak biasa, seperti lonjakan transaksi atau peningkatan error secara tiba-tiba.
## **Tips Optimasi**
1. **Percepat Query yang Lambat:**
   - Periksa log dari query GraphQL yang lambat.
   - Optimalkan dengan index database atau caching.
2. **Setup Alerts:**
   - Buat alert jika transaksi melebihi waktu yang diharapkan atau jika terjadi lonjakan error.
3. **Gunakan Dashboard Khusus:**
   - Buat visualisasi khusus untuk memantau endpoint `/v1/graphql` secara real-time.


---

![image](https://github.com/user-attachments/assets/356cb994-512a-4b5f-983b-c2cf87aea444)

---
Grafik diatas menampilkan dua metrik utama dari endpoint **`/v1/graphql`** dalam Elastic APM:

### **1. Latency (Keterlambatan)**
- **Sumbu Y:** Rata-rata latensi dalam milidetik (ms).
- **Sumbu X:** Waktu pengamatan.
- **Garis Biru:** Rata-rata latensi pada hari ini.
- **Garis Biru Muda:** Data latensi pada hari sebelumnya (sebagai perbandingan).
- **Observasi:**
  - Latensi rata-rata cenderung **stabil** di sekitar **3-4 ms**.
  - Tidak ada peningkatan besar atau lonjakan signifikan pada metrik latensi.

---

### **2. Throughput (Lalu Lintas Transaksi)**
- **Sumbu Y:** Jumlah transaksi per menit (tpm).
- **Sumbu X:** Waktu pengamatan.
- **Garis Hijau:** Throughput pada hari ini.
- **Garis Hijau Muda:** Throughput pada hari sebelumnya.
- **Observasi:**
  - Terjadi lonjakan throughput mendekati **600 tpm**, menunjukkan peningkatan jumlah transaksi pada waktu tertentu.
  - Throughput mencapai puncak stabil, lalu menurun kembali.

---

## **Analisis dan Tindakan**
### **1. Hubungan Latency dan Throughput**
- **Latensi stabil meskipun throughput meningkat.** Ini menunjukkan bahwa sistem Anda mampu menangani beban lalu lintas tambahan tanpa memperlambat waktu respons.
- **Tindakan:** Tetap pantau latensi jika throughput terus meningkat, terutama jika mendekati batas kapasitas server.

### **2. Potensi Bottleneck**
- Jika ada peningkatan throughput mendadak:
- Pastikan infrastruktur backend mampu menangani permintaan besar.
- Periksa kapasitas server, database, atau cache yang digunakan.

### **3. Optimasi Performa**
- **Caching:** Gunakan caching pada query yang sering dipanggil untuk mengurangi beban.
- **Load Testing:** Lakukan pengujian beban untuk memahami batas kapasitas sistem.
- **Autoscaling:** Jika menggunakan cloud, pastikan autoscaling diaktifkan untuk menangani lonjakan throughput.

---

![image](https://github.com/user-attachments/assets/944c6c5b-e503-43c7-8bce-56e14b8c204a)
![image](https://github.com/user-attachments/assets/bd6c7880-69c6-40cb-86bc-c52e96ad5533)
![image](https://github.com/user-attachments/assets/778030ad-de26-48d4-8848-9e0c1f05266f)
![image](https://github.com/user-attachments/assets/bfdfd32d-ed8c-409a-a874-5f9c3386e34d)
![WhatsApp Image 2024-12-10 at 15 19 51_df53304e](https://github.com/user-attachments/assets/3d938d55-3bab-4cce-b6a1-ec4d39a0bfa5)
![image](https://github.com/user-attachments/assets/7124ec56-4ce4-4bd5-9be4-aeddf715050b)
![image](https://github.com/user-attachments/assets/b5f84d99-8cb9-4b40-81eb-2ad7ee065c55)
![image](https://github.com/user-attachments/assets/b0d79b6d-1abe-4523-b954-e09c3cdb0f19)



