# HOW TO USE

Run docker compose:

```bash
docker compose -f docker-compose-single.yml down
```

Create a topic:

```bash
docker-compose -f docker-compose-single.yml exec kafka kafka-topics --create --topic my-topic --bootstrap-server kafka:9092 --replication-factor 1 --partitions 1
```

Execute a consumer:

```bash
docker-compose -f docker-compose-single.yml exec kafka bash
" In container
$ kafka-console-consumer --topic my-topic --bootstrap-server kafka:9092
```

Execute a producer:
```bash
docker-compose -f docker-compose-single.yml exec kafka bash
" In container
$ kafka-console-producer --topic my-topic --broker-list kafka:9092

>hello
>this is producer
```

Consumer Output:

```bash
hello
this is producer
```
