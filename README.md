1. How much data your publisher program will send to the message broker in one run?  

Dalam satu kali dijalankan, program publisher akan mengirim **5 data pesan** ke message broker. Setiap pesan berupa `UserCreatedEventMessage` yang berisi `user_id` dan `user_name`. Semua pesan tersebut dikirim ke event atau queue bernama `user_created`.

2. The url of `amqp://guest:guest@localhost:5672` is the same as in the subscriber program, what does it mean?  

URL `amqp://guest:guest@localhost:5672` yang sama pada publisher dan subscriber berarti keduanya terhubung ke message broker yang sama. Publisher mengirim pesan ke RabbitMQ di komputer lokal, sedangkan subscriber mendengarkan pesan dari broker yang sama. Dengan begitu, pesan yang dikirim oleh publisher dapat diterima oleh subscriber.

## Running RabbitMQ

![alt text](images/image.png)