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

Produce messages on topic first_topic (Ctrl-C to end)
```console
kafka-console-producer --bootstrap-server localhost:9092 --topic first_topic
```

Produce messages on topic first_topic with an all-acknowledgement policy (explicit acknowledge from all partitions needed on write) (Ctrl-C to end)
```console
kafka-console-producer --bootstrap-server localhost:9092 --topic first_topic --producer-property acks=all
```

## kafka-console-consumer

Read new messages from topic first_topic
```console
kafka-console-consumer --bootstrap-server localhost:9092 --topic first_topic
```

Read all messages from topic first_topic
```console
kafka-console-consumer --bootstrap-server localhost:9092 --topic first_topic --from-beginning
```

Read new messages from topic first_topic as consumer group first-application
> Each consumer within a consumer group reads from an exclusive partition
> 
> If more consumer than partitions are created, some consumers will be inactive
```console
kafka-console-consumer --bootstrap-server localhost:9092 --group first-application
```

Read all messages from topic first_topic as consumer group second-application
> each consumer within a consumer group reads from an exclusive partion
> 
> if more consumer than partitions are created, some consumers will be inactive
```console
kafka-console-consumer --bootstrap-server localhost:9092 --group second-application --from-beginning
```

## kafka-consumer-groups

List consumer groups
```console
kafka-consumer-groups --bootstrap-server localhost:9092 --list
```

Describe consumer group named first-application
```console
kafka-consumer-groups --bootstrap-server localhost:9092 --describe --group first-application
```

Resets the offset of consumer group first-application for all topics to the earliest message
```console
kafka-consumer-groups --bootstrap-server localhost:9092 --group first-application --reset-offsets --all-topics --to-earliest --execute
```

Resets the offset of consumer group first-application for topic first_topic to the earliest message
```console
kafka-consumer-groups --bootstrap-server localhost:9092 --group first-application --topic first_topic --to-earliest --execute
```

Shifts forward by 10 the offset of consumer group first-application for topic first_topic
```console
kafka-consumer-groups --bootstrap-server localhost:9092 --group first-application --topic first_topic --shift-by 10 --execute
```

Shifts backward by 10 the offset of consumer group first-application for topic first_topic
```console
kafka-consumer-groups --bootstrap-server localhost:9092 --group first-application --topic first_topic --shift-by -10 --execute
```
