# kafka-cli
Kafka CLI cheat sheet

## kafka-topics

List available topics
```console
kafka-topics --bootstrap-server localhost:9092 --list
```

Create a topic named first_topic with 3 partitions and a replicator factor of 3
```console
kafka-topics --bootstrap-server localhost:9092 --topic first_topic --create --partitions 3 --replication-factor 3
```

Describe the topic named first_topic
```console
kafka-topics --bootstrap-server localhost:9092 --topic first_topic --describe
```

Delete the topic named first_topic
```console
kafka-topics --bootstrap-server localhost:9092 --topic first_topic --delete
```
