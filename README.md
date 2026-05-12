# Publisher

## Pertanyaan

### a. How much data will the publisher send to the message broker in one run?
Dalam satu kali run, publisher akan mengirimkan **5 event** ke message broker. Setiap event berisi data berupa `user_id` dan `user_name`. Kelima event tersebut adalah:
- user_id: 1, user_name: 2106750925-Amir
- user_id: 2, user_name: 2106750925-Budi
- user_id: 3, user_name: 2106750925-Cica
- user_id: 4, user_name: 2106750925-Dira
- user_id: 5, user_name: 2106750925-Emir

### b. The URL `amqp://guest:guest@localhost:5672` is the same as in the subscriber program, what does it mean?
URL yang sama pada publisher dan subscriber berarti keduanya terhubung ke **message broker yang sama**, yaitu RabbitMQ yang berjalan di komputer lokal (`localhost`) pada port `5672`. Publisher mengirimkan event ke broker tersebut, dan subscriber mengambil/mengkonsumsi event dari broker yang sama. Inilah yang memungkinkan komunikasi tidak langsung (indirect) antara publisher dan subscriber melalui RabbitMQ sebagai perantara.

## Running RabbitMQ as Message Broker

Berikut adalah tampilan RabbitMQ yang berhasil dijalankan melalui Docker:

![RabbitMQ Running](images/rabbitmq-running.png)