## 1. Pengertian Blackbox 
***Blackbox Prometheus Exporter*** adalah alat untuk memantau/monitoring sistem dan layanan agar dapat mengatasi masalah dengan segera. Sistem ini menggunakan protokol seperti
HTTP, HTTPS, ICMP, DNS, dan TCP. Dengan penggunanaan Blackbox Exporter dapat mengumpulkan metriks tentang kesehatan dan responsivitasnya.
Informasi ini kemudian dapat diintegrasikan ke dalam sistem pemantauan Prometheus, dan memberikan tampilan tentang kinerja seluruh infrastruktur.

Berikut adalah cara kerja protokol yang dapat dilakukan oleh Blackbox Exporter:
* **HTTP/HTTPS** : Mengirimkan permintaan HTTP atau HTTPS lalu memeriksa status, header, dan konten dari respons yang diterima.
* **ICMP**     : Menggunakan ping untuk memeriksa apakah server dapat dijangkau dan berapa lama waktu yang dibutuhkan untuk merespons.
* **TCP**       : Memeriksa apakah port tertentu pada server terbuka dan dapat menerima koneksi.
* **DNS**     : Melakukan query DNS untuk memriksa apakah nama domain dapat di-resolve menjadi alamat IP.

## 2. Cara umum melihat **latency per query**
Untuk melihat **latency per query** di Grafana, langkah-langkah yang perlu dilakukan bergantung pada sumber data yang digunakan, seperti **Prometheus**, **Elasticsearch**, atau sistem pemantauan lainnya yang mendukung pengambilan metrik query latency. Secara umum, Grafana memungkinkan kamu untuk mengukur dan menampilkan latensi per query jika data tersebut tersedia dari sumber pemantauan.

Berikut adalah cara umum untuk melihat **latency per query** menggunakan **Prometheus** sebagai contoh sumber data:

### 1. **Memastikan Metrik Latency Tersedia**:
   - Pertama, pastikan bahwa sistem atau aplikasi yang kita monitor sudah mengekspor metrik yang mencatat latensi dari setiap query. Di Prometheus, metrik ini biasanya disediakan oleh server aplikasi atau database yang mendukung monitoring latensi.
   - Contoh metrik yang umum untuk latensi:
     - **`http_request_duration_seconds`** (untuk aplikasi web yang menggunakan HTTP)
     - **`query_duration_seconds`** (untuk database query latencies)
     - **`grpc_server_handling_seconds`** (untuk latensi gRPC query)
   
   - Metrik ini biasanya memiliki label seperti `method`, `endpoint`, atau `status` yang bisa digunakan untuk mengelompokkan data berdasarkan query tertentu.

### 2. **Membuat Panel Baru di Grafana**:
   - Di Grafana, buat **panel baru** untuk menampilkan latensi. Kamu bisa menggunakan jenis panel seperti **Time Series** (untuk grafik linier), **Bar Chart** (untuk histogram), atau **Table** (untuk detail query per query).
   
   Langkah-langkah:
   - Klik **+** (Add panel), lalu pilih **New Panel**.
   - Pilih jenis visualisasi yang sesuai. Untuk latensi per query, umumnya **Time Series** paling umum digunakan.

### 3. **Menulis Query di Panel Grafana**:
   - Di bagian **Query**, tulis query PromQL untuk menampilkan latensi per query dari metrik yang tersedia. Misalnya, jika menggunakan Prometheus, berikut adalah beberapa contoh query:

   #### Contoh 1: **Menghitung Latency Rata-rata per Endpoint**
   ```promql
   avg by (method, endpoint) (rate(http_request_duration_seconds_sum[5m]) / rate(http_request_duration_seconds_count[5m]))
   ```
   - Query di atas menghitung rata-rata latensi per **endpoint** dan **method** HTTP dalam interval 5 menit, menggunakan data dari metrik `http_request_duration_seconds`.

   #### Contoh 2: **Mengukur Percentile Latency (p95 atau p99)**
   Jika ingin melihat latensi pada tingkat persentil tertentu (misalnya **p95** atau **p99**):
   ```promql
   histogram_quantile(0.95, sum by (le, endpoint) (rate(http_request_duration_seconds_bucket[5m])))
   ```
   - Query ini menampilkan latensi **p95** untuk tiap endpoint dalam periode 5 menit. Kamu juga bisa mengganti `0.95` dengan `0.99` untuk **p99 latency**.

   #### Contoh 3: **Query Latency untuk Database**
   Jika memantau database seperti PostgreSQL dengan **pg_exporter**, bisa menulis query seperti berikut untuk melihat latensi query SQL:
   ```promql
   rate(pg_stat_statements_total_time_sum[5m]) / rate(pg_stat_statements_calls[5m])
   ```
   - Query ini menghitung rata-rata waktu eksekusi per query SQL dalam PostgreSQL dalam interval 5 menit.

### 4. **Konfigurasi Visualisasi**:
   Setelah query ditulis, sesuaikan visualisasi panel di Grafana agar menampilkan latensi dengan jelas:
   
   - **Axis**: Atur sumbu vertikal (Y-axis) untuk mewakili latensi dalam satuan yang sesuai, misalnya dalam detik atau milidetik.
   - **Legend**: Tampilkan label seperti `method`, `endpoint`, atau `query` agar lebih mudah melihat perbedaan latensi antar query.
   - **Thresholds**: Jika kamu ingin menyorot latensi yang terlalu tinggi, kamu bisa menambahkan **thresholds** (misalnya 500ms atau 1 detik) dengan warna yang berbeda untuk menandakan latensi yang mungkin dianggap lambat.

### 5. **Alerting (Opsional)**:
   -   Bisa menambahkan **alert** jika latensi melebihi ambang batas tertentu. Misalnya, jika latensi melebihi **500ms**, kita dapat mengonfigurasi alert di Grafana untuk memberi notifikasi.
   - Pergi ke tab **Alert** di panel tersebut dan atur kondisi serta notifikasi alert jika latensi query terlalu tinggi.

### 6. **Menganalisis Latency per Query**:
   - Dengan visualisasi yang dihasilkan, kita dapat menganalisis fluktuasi latensi berdasarkan query spesifik, endpoint, atau metode tertentu.
   - Misalnya, jika memantau aplikasi web, kamu bisa melihat query mana yang memakan waktu lebih lama untuk diproses atau endpoint mana yang sering mengalami latensi tinggi.

### **Contoh Lain Sumber Data dan Alat yang Digunakan**:
Jika menggunakan **Elasticsearch** untuk log analysis atau **MySQL** untuk database query, perlu menyesuaikan query sesuai dengan sistem tersebut. 

- **Elasticsearch**: Bisa mengekstrak latency query dari index yang memuat informasi tentang respon waktu query log.
- **MySQL**: Jika menggunakan MySQL, metrik seperti `mysql_global_status_query_time` bisa digunakan untuk melacak latensi query SQL.

### Kesimpulan:
Untuk melihat **latency per query** di Grafana, perlu memastikan metrik latensi tersedia dari sumber data (seperti Prometheus), kemudian menulis query yang sesuai di panel Grafana untuk menampilkan latensi rata-rata, persentil, atau data spesifik lainnya. Grafana menyediakan alat yang kuat untuk memvisualisasikan latensi dan membantu dalam analisis performa query.
