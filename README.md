# kafka-node-example

Playground setup for kafka and node js. It is using the fantastic `spotify/kafka` docker image to get things up and running.

# Getting start

You must have node / nvm installed, and also docker.

```
nvm use

# install dependencies
yarn // npm
```

## Running kafka

To run kafka

```
yarn kafka:start
```

This will install and run the docker image and add in a topic called test. This is running a single broker and a single partition for the specified topic. To add more you can run

```
docker exec kafkatest /opt/kafka_2.11-0.10.1.0/bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic [topic name]
```

To stop kafka simple run

```
yarn kafka:stop
```

## Running node examples

We have a setup for a single kafka topic `test` so the consumer will listen to all messages from that topic.

```
yarn consumer:start

// npm

npm run consumer:start
```

Then in a seperate console

```
yarn producer:start 'message'

// npm

npm run consumer:start -- 'message'
```

You should see an output in the consumer process window.
