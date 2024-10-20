### 1. Pengertian Blackbox 
***Blackbox Prometheus Exporter*** adalah alat untuk memantau/monitoring sistem dan layanan agar dapat mengatasi masalah dengan segera. Sistem ini menggunakan protokol seperti
HTTP, HTTPS, ICMP, DNS, dan TCP. Dengan penggunanaan Blackbox Exporter dapat mengumpulkan metriks tentang kesehatan dan responsivitasnya.
Informasi ini kemudian dapat diintegrasikan ke dalam sistem pemantauan Prometheus, dan memberikan tampilan tentang kinerja seluruh infrastruktur.

Berikut adalah cara kerja protokol yang dapat dilakukan oleh Blackbox Exporter:
* **HTTP/HTTPS** : Mengirimkan permintaan HTTP atau HTTPS lalu memeriksa status, header, dan konten dari respons yang diterima.
* **ICMP**     : Menggunakan ping untuk memeriksa apakah server dapat dijangkau dan berapa lama waktu yang dibutuhkan untuk merespons.
* **TCP**       : Memeriksa apakah port tertentu pada server terbuka dan dapat menerima koneksi.
* **DNS**     : Melakukan query DNS untuk memriksa apakah nama domain dapat di-resolve menjadi alamat IP.
