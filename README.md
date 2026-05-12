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

## Sending and Processing Event

Berikut adalah tampilan ketika publisher mengirimkan event dan subscriber menerimanya:

![Subscriber Console](images/subscriber-console.png)
![Publisher Console](images/publisher-console.png)

Ketika publisher dijalankan dengan `cargo run`, publisher mengirimkan 5 event `UserCreatedEventMessage` ke message broker RabbitMQ. Event-event tersebut kemudian dikonsumsi dan diproses oleh subscriber, yang mencetak pesan ke console. Hal ini menunjukkan bahwa komunikasi antara publisher dan subscriber berhasil dilakukan secara tidak langsung melalui RabbitMQ sebagai perantara.

## Monitoring Chart Based on Publisher

Berikut adalah tampilan grafik RabbitMQ setelah publisher dijalankan:

![RabbitMQ Chart](images/rabbitmq-chart.png)

Spike yang terlihat pada grafik "Message rates" terjadi karena publisher mengirimkan 5 event sekaligus ke message broker. Setiap kali `cargo run` dijalankan pada publisher, akan muncul lonjakan (spike) pada grafik yang menunjukkan adanya pesan yang dipublish dan langsung dikonsumsi oleh subscriber. Semakin sering publisher dijalankan, semakin banyak spike yang muncul pada grafik.