Golang Kafka Microservice Templates
=====

A group of [GoLang](https://golang.org/) example templates for writing [Apache Kafka](https://kafka.apache.org/) production ready applications. The templates were created to be used a starting point for [microservices](https://martinfowler.com/articles/microservices.html) that utilize Kafka for [Event Sourcing](https://martinfowler.com/eaaDev/EventSourcing.html) as an eventstore to persist events. An event store is the backbone of an event-sourced mircroservice architecture. Utilizing best practices in GoLang for [producers](https://kafka.apache.org/documentation/#producerapi) and [consumers](https://kafka.apache.org/documentation/#consumerapi) is therefore critical to a successful project.    

Each template does not have any domain specific logic. The goal is that new developers can leverage the boiler plate code examples to add additional functionality to an application.

### Example Templates
- [consumer-minimal](./consumer-minimal/) is a minimal implementation of a kafka consumer that provides:
  - Graceful shutdown to avoid data loss and unexpected behavior
  - Configuration via environment variables
  - Syslog logging of information and issues

### Usage
It assumed that you have an understanding of [Apache Kafka](https://kafka.apache.org/) and have a version of Kafka running that you can connect to for development. The Kafka [quickstart](https://kafka.apache.org/quickstart) tutorial can assist you in running a local copy.   

On macOS with [Homebrew](https://brew.sh/) installed the following starts a local copy of Kafka

'''shell
localhost:~ me$ Brew install Kafka
localhost:~ me$ zookeeper-server-start /usr/local/etc/kafka/zookeeper.properties & kafka-server-start /usr/local/etc/kafka/server.properties
'''

The code requires [Sarama](https://github.com/Shopify/sarama) an MIT-licensed Go client library for Apache Kafka. We utilize this library because it takes advantage of [consumer groups](http://kafka.apache.org/documentation.html#impl_zkconsumers) which ensures that for replicated consumers duplicated execution of published messages doesn't occur.

'''shell
localhost:~ me$ go get github.com/Shopify/sarama
'''

All [logs](https://golang.org/pkg/log/syslog/) are sent to [syslog](https://en.wikipedia.org/wiki/Syslog)

Please do not fork the repository unless you are submitting a pull request to update the template. For your own usage please [mirror](https://help.github.com/articles/duplicating-a-repository/) the repo.

### Design Assumptions
These templates follow [The Twelve Factors](https://12factor.net/) a popular and widely used methodology for building web applications.


### Thank you
This work is built on top of the incredible blog posts from [Oscar Oranagwa](https://medium.com/@Oskarr3)

- [Building Scalable Applications Using Event Sourcing and CQRS](https://medium.com/technology-learning/event-sourcing-and-cqrs-a-look-at-kafka-e0c1b90d17d8)
- [Implementing CQRS using Kafka and Sarama Library in Golang](https://medium.com/@Oskarr3/implementing-cqrs-using-kafka-and-sarama-library-in-golang-da7efa3b77fe)