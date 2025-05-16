# Refleksi

Nama: Muhammad Naufal Ramadhan <br>
NPM: 2306241700 <br>
Kelas: B
<hr>

1. What is amqp? <br>
AMQP (Advanced Message Queuing Protocol) adalah protokol komunikasi standar terbuka yang dirancang khusus untuk pertukaran pesan antar aplikasi. Protokol ini memungkinkan aplikasi untuk berkomunikasi secara asynchronous melalui message queuing. Protokol ini sangat penting dalam arsitektur microservices karena memungkinkan komponen-komponen sistem untuk berkomunikasi secara terpisah dan handal.

2. What does it mean? guest:guest@localhost:5672 , what is the first guest, and what is the second guest, and what is localhost:5672 is for? <br>
String koneksi guest:guest@localhost:5672 adalah format standar untuk menghubungkan aplikasi dengan server AMQP. Bagian pertama yaitu guest merupakan username yang digunakan untuk autentikasi ke server AMQP, sementara guest kedua adalah password untuk autentikasi tersebut. Bagian localhost menunjukkan bahwa server AMQP berjalan di mesin lokal, sedangkan 5672 adalah nomor port yang digunakan oleh protokol AMQP untuk komunikasi. Keseluruhan string koneksi ini memungkinkan aplikasi untuk terhubung dan berinteraksi dengan message broker seperti RabbitMQ yang mengelola pertukaran pesan dalam sistem.

## Simulation slow subscriber
![slow](/assets/images/slow_subs.png)
Karena telah ditambahkan semacam delay pada subscribernya dalam memproses pesan, ketika di publisher dijalankan cargo run sebanyak 6-7 kali (mengirim data 6-7x dimana masing-masingnya ada 5 pesan), maka terlihat messages queuenya meningkat hingga menyentuh angka 30.

## Running at least three subscribers
![threesubs](/assets/images/3_subs.png)
Pada gambar ini saya menjalankan 3 subscriber, dan pada publisher saya mengirim jumlah pesan yang sama yaitu 7x (35 pesan), tetapi bisa terlihat pada Queued Messages nya hanya menyentuh tidak menyentuh angka 20, dimana sebelumnya sampai 30. Karena subscribernya lebih banyak yaitu 3, maka ketika publisher mengirim 5 pesan tersebut akan dipecah dan diterima oleh 3 subscriber dalam memprosesnya.