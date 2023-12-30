# HOW TO USE

Run docker compose:

```bash
docker compose -f docker-compose-multi.yml up
```

Create a topic:

```bash
docker-compose -f docker-compose-multi.yml exec kafka-1 kafka-topics --create --topic my-topic --bootstrap-server kafka-1:9092 --replication-factor 3 --partitions 2
```

Check the topic:

```bash
docker-compose -f docker-compose-multi.yml exec kafka-1 kafka-topics --describe --topic my-topic --bootstrap-server kafka-1:9092

Topic: my-topic	TopicId: rsMigKSSQRGRTd0mx4Revg	PartitionCount: 2	ReplicationFactor: 3	Configs:
	Topic: my-topic	Partition: 0	Leader: 3	Replicas: 3,1,2	Isr: 3,1,2
	Topic: my-topic	Partition: 1	Leader: 1	Replicas: 1,2,3	Isr: 1,2,3
```

Execute a consumer:

```bash
docker-compose -f docker-compose-multi.yml exec kafka-1 bash
" In container
$ kafka-console-consumer --topic my-topic --bootstrap-server kafka-1:9092
```

Execute a producer:
```bash
docker-compose -f docker-compose-multi.yml exec kafka-2 bash
" In container
$ kafka-console-producer --topic my-topic --broker-list kafka-2:9092

>hello
>this is producer
```

Consumer Output:

```bash
hello
this is producer
```
