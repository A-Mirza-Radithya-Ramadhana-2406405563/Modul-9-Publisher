1. How much data your publisher program will send to the message broker in one run?  

Dalam satu kali dijalankan, program publisher akan mengirim **5 data pesan** ke message broker. Setiap pesan berupa `UserCreatedEventMessage` yang berisi `user_id` dan `user_name`. Semua pesan tersebut dikirim ke event atau queue bernama `user_created`.

2. The url of `amqp://guest:guest@localhost:5672` is the same as in the subscriber program, what does it mean?  

URL `amqp://guest:guest@localhost:5672` yang sama pada publisher dan subscriber berarti keduanya terhubung ke message broker yang sama. Publisher mengirim pesan ke RabbitMQ di komputer lokal, sedangkan subscriber mendengarkan pesan dari broker yang sama. Dengan begitu, pesan yang dikirim oleh publisher dapat diterima oleh subscriber.

## Running RabbitMQ

![alt text](images/image.png)

## Sending and Processing Event

![alt text](images/console.png)

Publisher mengirim beberapa event `UserCreatedEventMessage` ke RabbitMQ. Setiap message berisi data `user_id` dan `user_name`, seperti `2406405563-Amir`, `2406405563-Budi`, dan lainnya.

Subscriber kemudian melakukan listening pada queue RabbitMQ dan menerima setiap message yang dikirim oleh publisher. Output pada console membuktikan bahwa proses pengiriman message dari publisher ke subscriber berhasil berjalan.

## Monitoring chart based on publisher

![alt text](images/Chart1.png)

Pada grafik kedua, yaitu bagian **Message rates**, terlihat adanya spike atau lonjakan pada saat publisher dijalankan. Spike tersebut muncul karena publisher mengirim beberapa message ke RabbitMQ dalam waktu singkat.

Setiap kali publisher dijalankan, RabbitMQ menerima message baru sehingga nilai **Publish** naik sementara. Setelah message berhasil dikirim ke queue dan diterima oleh subscriber, grafik seperti **Deliver** dan **Consumer ack** juga dapat ikut naik.

Setelah semua message selesai diproses, rate kembali turun ke `0.00/s`. Hal ini menunjukkan bahwa RabbitMQ hanya aktif memproses message ketika publisher mengirim data, lalu kembali idle setelah semua message selesai dikonsumsi oleh subscriber.
