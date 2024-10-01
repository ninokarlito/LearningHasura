
# Analisis V1/Metrics dari Postman 

1. Metric Berikut adalah bagian dari histogram dalam Prometheus, yang digunakan untuk mengukur waktu yang dibutuhkan Hasura untuk mengambil sekumpulan event

`hasura_event_fetch_time_per_batch_seconds_bucket{le="1.0e-4"} 0`
`hasura_event_fetch_time_per_batch_seconds_bucket{le="3.0e-4"} 0`

Berikut Rincian metrics nya:
- **Nama Metrik (`hasura_event_fetch_time_per_batch_seconds_bucket`)**:  
  Ini adalah metrik histogram yang menunjukkan waktu yang dibutuhkan untuk mengambil batch (sekumpulan) event dalam hitungan detik.
- **Bucket (`{le="1.0e-4"}`)**:  
  Ini menunjukkan bucket (kategori) dalam histogram. `le="1.0e-4"` berarti waktu pengambilan event yang kurang dari atau sama dengan \(1 \times 10^{-4}\) detik (0,0001 detik).
- **Nilai (`0`)**:  
  Nilai ini menunjukkan bahwa tidak ada event yang waktu pengambilannya kurang dari atau sama dengan 0,0001 detik.
Dan belum ada event yang waktu pengambilannya tercatat di bawah atau sama dengan 0,0001 detik dalam bucket ini.

2. `hasura_graphql_execution_time_seconds_bucket{operation_type="mutation",le="1.0e-2"} 0 `
menggambarkan performa eksekusi GraphQL di Hasura.

3. `hasura_graphql_execution_time_seconds_sum{operation_type="mutation"} 0.0` 
metrics diatas menunjukkan total waktu eksekusi dari semua operasi **mutasi** di Hasura. 
Berikut rinciannya:
- **Nama Metrik (`hasura_graphql_execution_time_seconds_sum`)**:  
  Ini adalah metrik yang menjumlahkan total waktu eksekusi operasi GraphQL dalam detik.
- **Label (`{operation_type="mutation"}`)**:  
  Ini menunjukkan bahwa metrik ini hanya mengukur operasi **mutasi** (bukan query atau subscription).
- **Nilai (`0.0`)**:  
  Ini berarti total waktu eksekusi semua operasi mutasi hingga saat ini adalah **0 detik**.
Di metrics tsb tidak ada waktu eksekusi yang tercatat untuk mutasi, atau belum ada operasi mutasi yang dilakukan dalam periode pengukuran ini.

4. `hasura_graphql_execution_time_seconds_sum{operation_type="query"} 0.382292266`
Metrik diatas menunjukkan total waktu yang dihabiskan untuk mengeksekusi semua operasi **query** di Hasura.
Berikut penjelasannya:
- **Nama Metrik (`hasura_graphql_execution_time_seconds_sum`)**:  
  Ini adalah metrik yang menjumlahkan seluruh waktu eksekusi operasi GraphQL, khususnya untuk operasi **query**, dalam detik.
- **Label (`{operation_type="query"}`)**:  
  Ini menunjukkan bahwa metrik ini hanya mengukur waktu eksekusi untuk operasi **query**.
- **Nilai (`0.382292266`)**:  
 berarti total waktu yang telah dihabiskan untuk mengeksekusi semua operasi query hingga saat ini adalah **0,382 detik** (sekitar 382 milidetik).
Di metrics tsb seluruh query yang dijalankan sejauh ini telah menghabiskan waktu sekitar 0,38 detik secara total.

5. `hasura_postgres_connection_init_time_bucket{conn_info="HASURA_GRAPHQL_DATABASE_URL",source_name="default",le="1.0e-6",role="primary"} 0` 
Metrik diatas memberikan informasi tentang waktu inisialisasi koneksi ke database PostgreSQL oleh Hasura. 
Berikut penjelasannya:
- **Nama Metrik (`hasura_postgres_connection_init_time_bucket`)**:  
  Ini adalah metrik histogram yang mengukur waktu yang dibutuhkan untuk menginisialisasi koneksi ke database PostgreSQL.
- **Label**:  
  - `conn_info="HASURA_GRAPHQL_DATABASE_URL"`: Menunjukkan bahwa koneksi dibuat menggunakan URL yang dikonfigurasi untuk Hasura (`HASURA_GRAPHQL_DATABASE_URL`).
  - `source_name="default"`: Menandakan bahwa sumber data yang digunakan adalah sumber default dalam konfigurasi Hasura.
  - `role="primary"`: Menyiratkan bahwa koneksi ini terkait dengan peran utama (primary) dalam database.
  - `le="1.0e-6"`: Mengacu pada bucket yang mengukur waktu inisialisasi koneksi yang kurang dari atau sama dengan \(1 \times 10^{-6}\) detik (1 mikrodetik).
- **Nilai (`0`)**:  
  Ini berarti tidak ada inisialisasi koneksi ke database PostgreSQL yang tercatat memiliki waktu inisialisasi kurang dari atau sama dengan 1 mikrodetik.
Di metrics tidak ada koneksi yang diinisialisasi dalam waktu kurang dari 1 mikrodetik dalam periode pengukuran ini.
