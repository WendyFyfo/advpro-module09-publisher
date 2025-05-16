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