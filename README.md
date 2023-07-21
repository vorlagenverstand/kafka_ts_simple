# Simple Kafka Producer and Consumer with Typescript and KafkaJS

### Prerequisites 
Node & NPM – [Installing NVM on Windows 11](https://realworlddev.hashnode.dev/installing-nvm-on-windows-11)

Before proceeding, ensure that you have access to an Apache Kafka instance from your local machine (Open a console and type: `telnet 35.153.235.161 9092`). [How to enable/use Telnet](https://support.intermedia.com/app/articles/detail/a_id/25172/~/what-is-telnet%3F-how-do-i-run-it%3F)

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

### How sending messages looks:
```bash
> kafka_ts_simple@1.0.0 start-producer
> ts-node src/producer.ts

{"level":"WARN","timestamp":"2023-07-15T01:02:09.123Z","logger":"kafkajs","message":"KafkaJS v2.0.0 switched default partitioner. To retain the same partitioning behavior as in previous versions, create the producer with the option \"createPartitioner: Partitioners.LegacyPartitioner\". See the migration guide at https://kafka.js.org/docs/migration-guide-v2.0.0#producer-new-default-partitioner for details. Silence this warning by setting the environment variable \"KAFKAJS_NO_PARTITIONER_WARNING=1\""}
Data: This is a test
Data:
```
### How consuming messages looks:
```bash
> kafka_ts_simple@1.0.0 start-consumer
> ts-node src/consumer.ts

{"level":"INFO","timestamp":"2023-07-15T00:59:37.801Z","logger":"kafkajs","message":"[Consumer] Starting","groupId":"test-group"}
{"level":"INFO","timestamp":"2023-07-15T00:59:59.713Z","logger":"kafkajs","message":"[ConsumerGroup] Consumer has joined the group","groupId":"test-group","memberId":"test-app-e06312db-3ac3-43bb-a746-2d37e388ac29","leaderId":"test-app-e06312db-3ac3-43bb-a746-2d37e388ac29","isLeader":true,"memberAssignment":{"test":[0]},"groupProtocol":"RoundRobinAssigner","duration":21911}
Received:  { partition: 0, offset: '0', value: 'This is a test' }
```

### Also you can see topics and messages in Kafka using [kafdrop](https://github.com/obsidiandynamics/kafdrop) or [kafkacat](https://github.com/edenhill/kcat)
