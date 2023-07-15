# Simple Kafka Producer and Consumer with Typescript and KafkaJS

### Before proceeding, ensure that you have access to an Apache Kafka instance from your local machine.

## Key Dependencies

## KafkaJS
[KafkaJS](https://kafka.js.org/) is a node.js library to integrate with the apache Kafka message bus.

## readlineSync
[readlineSync](https://www.npmjs.com/package/readline-sync) Synchronous Readline for interactively running to have a conversation with the user via a console(TTY).

### Clone the repository and add the dependencies.

### Navigate to the path created & run:
```bash
> npm i
```

## Implementation
Let’s review the consumer and producer implementation.

### Kafka
Before creating a producer and a consumer, you’ll need to create a kafka which will hold all the information necessary to create a producer and consumer that will be integrated with it.
```bash
const kafka = new Kafka({});
```

### Producer
The producer will be in charge of sending your messages to Kafka, first you’ll need to connect, then send. The only case you’ll need to disconnect is when the app needs to switch off.
```bash
const producer = kafka.producer({});
```

### Consumer
For the customer, it comes from the kafka object and can connect and disconnect, its main feature is to handle the message it will receive on the subscribed topics.
```bash
const consumer = kafka.consumer({});
```

### You can start the producer using:  
```bash
> npm run start-producer
```

### To start the consumer, in a new terminal window run:
```bash
> npm run start-consumer
```


### Go back to the producer, and start typing your data. 

### Also you can see topics and messages in Kafka using [kafdrop](https://github.com/obsidiandynamics/kafdrop) or [kafkacat](https://github.com/edenhill/kcat)
