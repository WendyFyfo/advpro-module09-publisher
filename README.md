# ADVPRO - SOFTWARE ARCHITECTURE

## TUTORIAL
### PUBLISHER - STEP 7
a. How much data your publisher program will send to the message broker in one run?

= Program publisher mengirimkan 5 message ke message broker setiap dijalankan. Hal tersebut dapat terlihat dari jumlah method publish_event() yang dipanggil. 

b. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?

= URL `amqp://guest:guest@localhost:5672` yang digunakan dalam program publisher sama dengan yang ada dalam program subscriber menunjukkan keduanya terhubung ke instance RabbitMQ yang sama.

### Preparing Message Broker (RabbitMQ)
1. Running RabbitMQ
![Running and opening RabbitMQ](/image/run-rabbitmq.png)

2. Sending and Processing Event
![Sending and Processing Event](/image/sending-proccesing-event.png)

3. Monitoring chart based on publisher

a. Publish (Rate at which messages are entering the server.)
![Publish](/image/image.png)
Spike kuning di gambar menunjukkan laju pesan yang dikirim oleh publisher ke Rabbit MQ. spike kecil menunjukkan ketika publisher dijalankan sekali (hanya mengirim 5 pesan), sedangkan spike besar menunjukkan ketika publisher dijalankan berkali-kali (mengirimkan banyak pesan). 


b. Deliver [manual ack] (Rate at which messages are delivered to consumers that use manual acknowledgements.)
![Deliver (manual ack)](/image/image%20copy.png)
Spike merah pada grafik menunjukkan laju pesan yang dikirim oleh RabbitMQ ke subscriber yang menggunakan manual acknowledgment. Spike kecil terjadi saat hanya sedikit pesan dikirimkan dari publisher dan langsung diteruskan ke consumer. Jika publisher dijalankan berkali-kali, maka spike ini akan tampak lebih besar karena lebih banyak pesan dikirim dan dikonsumsi.


c. Consumer ack (Rate at which messages are being acknowledged by consumers.)
![Consumer ack](/image/image%20copy%202.png)
Spike ungu menunjukkan laju pengakuan (acknowledgment) pesan oleh subscriber. Artinya, subscriber berhasil menerima dan memproses pesan tersebut lalu mengirimkan sinyal acknowledgement ke RabbitMQ. Spike yang muncul bersamaan/beriringan dengan spike pada Deliver [manual ack] menunjukkan consumer memproses pesan secara real-time, tanpa ada penundaan.