## 1. Dashboard Hasura GraphQL

Berikut untuk tampilan Query GraphQL di Hasura yang telah disiapkan.
![image](https://github.com/user-attachments/assets/e39e970d-fb69-4a72-a91b-6b73cfd9db0f)
### Query 1: Input 
```
query MyQuery {
  TABEL1 {
    id
    isi1
    isi2
    isi3
  }
} 
```
### Query 2: Output 
```
{
  "data": {
    "TABEL1": [
      {
        "id": 1,
        "isi1": "abc",
        "isi2": "abc",
        "isi3": "abc"
      },
      {
        "id": 2,
        "isi1": "abc",
        "isi2": "abc",
        "isi3": "abc"
      },
      {
        "id": 3,
        "isi1": "abc",
        "isi2": "abc",
        "isi3": "abc"
      },
      {
        "id": 4,
        "isi1": "abc",
        "isi2": "abc",
        "isi3": "abc"
      },
      {
        "id": 5,
        "isi1": "abc",
        "isi2": "abc",
        "isi3": "abc"
      },
      {
        "id": 6,
        "isi1": "abc",
        "isi2": "abc",
        "isi3": "abc"
      },
      {
        "id": 7,
        "isi1": "abc",
        "isi2": "abc",
        "isi3": "abc"
      },
      {
        "id": 8,
        "isi1": "abc",
        "isi2": "abc",
        "isi3": "abc"
      },
      {
        "id": 9,
        "isi1": "abc",
        "isi2": "abc",
        "isi3": "abc"
      },
      {
        "id": 10,
        "isi1": "abc",
        "isi2": "abc",
        "isi3": "abc"
      }
    ]
  }
}
```

## 2. Anaisis Dashboard Grafana 
### A. Hasura HTTP GraphQL
Dibawah ini adalah dashboard dari Grafana di input dengan source Prometheus untuk memonitor performa Hasura HTTP GraphQL, Beserta rincian dari data gambar agar dapat dipahami:

![image](https://github.com/user-attachments/assets/c3d51d41-f8f0-443e-9d55-5aee08716d8a)

![image](https://github.com/user-attachments/assets/109bd0ae-ec84-4539-970d-066679e76d41)

- **Total Queries (Total Kuery)**: 5
- **Query Latency (P95)**: 9.50 ms
- **Total Mutations (Total Mutasi)**: 0
- **Mutation Latency (Latensi Mutasi)**: 0 ms
  
1. **Total Queries: 5**
   - Ini berarti selama periode pengamatan (terakhir 30 menit, sesuai pengaturan di kanan atas), terdapat 5 kuery GraphQL yang dijalankan melalui Hasura.
   - Penting untuk memantau apakah jumlah kuery meningkat secara signifikan atau konsisten rendah. Jika ada lonjakan tiba-tiba dalam kuery, itu bisa menandakan peningkatan trafik atau masalah performa pada aplikasi.

2. **Query Latency (P95): 9.50 ms**
   - P95 (Percentile 95) berarti 95% dari kuery yang dijalankan memiliki latensi di bawah 9.5 milidetik, sementara 5% dari kuery bisa lebih lambat.
   - Latensi 9.50 ms sangat cepat, yang menunjukkan bahwa sistem saat ini responsif dan efisien untuk kuery yang dilakukan.
   - Jika nilai ini meningkat, mungkin perlu ditinjau dari sisi optimisasi kuery atau performa infrastruktur (seperti database atau server).

3. **Total Mutations: 0**
   - Tidak ada mutasi (insert, update, atau delete) yang terjadi selama periode waktu yang ditampilkan. Jika aplikasi seharusnya melakukan banyak mutasi, dan angka ini tetap nol, bisa ada masalah di sisi klien atau server yang mencegah mutasi terjadi.
   - Jika mutasi sering terjadi dan diperlukan, ini harus dipantau secara berkala untuk memastikan aplikasi berfungsi seperti yang diharapkan.

4. **Mutation Latency: 0 ms**
   - Karena tidak ada mutasi yang terjadi, tidak ada latensi yang bisa diukur. Jika mutasi terjadi di masa depan, latensi ini akan mengukur seberapa cepat Hasura dapat memprosesnya.
   - Sama halnya dengan kuery, jika latensi mutasi tinggi, bisa menandakan masalah performa yang perlu diinvestigasi lebih lanjut.
 
5. **Top Queiries**
Pada bagian ini service yang paling sering berjalan yaitu "hasuraferdy" dengan 3 kali tercatat.

6. **Top Mutation** 

7. **Top Error Rate**
  untuk memantau dan mengidentifikasi layanan, query, atau mutasi yang paling sering mengalami kesalahan (error).



### B. Hasura Health
![image](https://github.com/user-attachments/assets/2995b352-b845-4a25-bb0d-1d508990ec56)

* Metadata Status: CONSISTENT
  
  Menunjukkan bahwa metadata yang diawasi dalam sistem dalam keadaan konsisten, tanpa masalah.

* Health Check using Infinity: OK

  Menunjukkan data "OK" yang berarti pengecekan kesehatan sistem menggunakan Infinity sudah berjalan dan tidak ada masalah.

* Health Check using BlackBox : NO DATA

  Pada bagian ini di tunjukkan bahwa "No Data" dan berwarna merah yang berarti tidak ada pengecekan kesehatan sistem yang sudah dijalankan menggunakan Blackbox.

* Source Health Check : OK

  Pada bagian ini berguna untuk menunjukkan dua sumber hasura yaitu defaukt(hasuraferdy) dan testsejuta(hasuraferdy) yang keduanya berstatus OK.

* Metadata Version : 292

  Pada bagian ini hanya menunjukkan versi dari metadata yang digunakan yaitu versi 292.

* Health Check Latency : NO DATA

  Pada bagian ini untuk memastikan bahwa suatu layanan, sistem, atau aplikasi berfungsi dengan baik dan sesuai. Untuk Latency pada 
  bagian ini berarti untuk mengukur seberapa cepat atau lambat 
  pemeriksaan tersebut diselesaikan, yang bisa memberikan indikasi performa sistem.



* Postgres Connection

  Pada bagian ini menunjukkan grafik penggunaan koneksi postgress dari Graphql Engine.

