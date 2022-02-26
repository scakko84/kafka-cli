# kafka-cli
Kafka CLI cheat sheet

## kafka-topics

List available topics
```console
kafka-topics --bootstrap-server localhost:9092 --list
```

Create topic named first_topic with 3 partitions and a replicator factor of 3
```console
kafka-topics --bootstrap-server localhost:9092 --topic first_topic --create --partitions 3 --replication-factor 3
```

Describe topic named first_topic
```console
kafka-topics --bootstrap-server localhost:9092 --topic first_topic --describe
```

Delete topic named first_topic
```console
kafka-topics --bootstrap-server localhost:9092 --topic first_topic --delete
```

## kafka-console-producer

Produce events on topic first_topic (Ctrl-C to end)
```console
kafka-console-producer --bootstrap-server localhost:9092 --topic first_topic
```

Produce events on topic first_topic with an all-acknowledgement policy (explicit acknowledge from all partitions needed on write) (Ctrl-C to end)
```console
kafka-console-producer --bootstrap-server localhost:9092 --topic first_topic --producer-property acks=all
```
