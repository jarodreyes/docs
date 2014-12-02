# Using RabbitMQ With KONA

![alt tag](http://www.rabbitmq.com/img/rabbitmq_logo_strap.png)

## Introduction

RabbitMQ is a message broker. In essence, it accepts messages from producers, and delivers them to consumers. In-between, it can route, buffer, and persist the messages according to rules you give it.

In KONA, KONA is the (or one of) the producer, **NOT** the client

read more from rabbitmq documentation http://www.rabbitmq.com/documentation.html

## Server Provider

You can use https://www.cloudamqp.com or other RabbitMQ as a service provider.

Asuming that you are using cloudamqp, do you need to obtain the complete URL and put inside the KONA Connector

![alt tag](http://i.imgur.com/iYzH0J0.png)

Get the URL

```
url = amqp://flaqfxdb:UeNV_1Zn57KnEZzfJPvkE3hwZj3OPnNb@tiger.cloudamqp.com/flaqfxdb
```

