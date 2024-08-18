**WHAT ?**
- A **message queue** is a queue of messages sent between applications. It includes a sequence of work objects that are waiting to be processed.
- The basic architecture of a **message queue** is simple: there are client applications called **producers** that create messages and deliver them to the message queue. Another application, called a **consumer**, connects to the queue and gets the messages to be processed. Messages placed onto the queue are stored until the consumer retrieves them.

**WHY ?**
- It is a mechanism for applications to communicate asynchronously, by sending messages to each other via a queue. A message queue provides temporary storage between the sender and the receiver so that the sender can keep operating without interruption when the destination program is busy or not connected. ***Asynchronous processing allows a task to call a service and move on to the next task while the service process the request at its own pace.***
- The queue can provide protection from service outages and failures.
- Examples of queues: Kafka, Heron, real-time streaming, Amazon SQS, and RabbitMQ.

**Example**
![[Screenshot 2024-06-17 at 17.11.50.png]]


#### The role of message queuing in a microservice architecture

- In a microservice architecture, there are different functionalities divided across different services, that offer various functionalities. These services are coupled together to form a complete software application.
- Typically, in a microservice architecture, there are cross-dependencies, which entail that no single service can perform its functionalities without getting help from other services. **This is where it’s crucial for your system to have a mechanism in place which allows services to keep in touch with each other without getting blocked by responses.**
- Message queuing fulfills this purpose by providing a means for services to push messages to a queue asynchronously and ensure that they get delivered to the correct destination. To implement a message queue between services, you need a **message broker, think of it as a mailman**, who takes mail from a sender and delivers it to the correct destination.

# Kafka

**WHAT ?**
Apache Kafka is an open-source distributed streaming platform designed to handle high-volume, real-time data feeds. It is often used for messaging, log aggregation, stream processing, and commit logs. Kafka is a highly scalable and fault-tolerant platform, making it a popular choice for mission-critical applications.

It lets you publish and subscribe to real-time streams of information, enabling various applications to communicate and react instantly. At its core, Kafka operates with:

- **Topics:** Categorized channels for data streams.
- **Partitions:** Subdivisions within topics for parallel processing.
- **Producers:** Applications pushing data to topics.
- **Consumers:** Applications subscribing to topics to receive data.
- **Brokers:** Servers storing and managing data partitions.

**WHY ?**
Kafka boasts several advantages that make it a popular choice for various use cases:

- **Scalability:** Designed to handle massive data volumes with ease.
- **Fault Tolerance:** Built for resilience, so data loss is minimal even with node failures.
- **Performance:** High-throughput data processing with low latency.
- **Real-time Capabilities:** Handles data streams as they occur, ideal for real-time analytics and application updates.
- **Flexibility:** Integrates seamlessly with various technologies and systems.

**WHERE ?**
- **Microservices Communication:** Enables efficient communication between microservices for building robust and responsive applications.
- **Event-Driven Architectures:** Reacts to events in real-time, streamlining processes and improving agility.
- **Real-time Analytics:** Feeds data pipelines for continuous analysis and insights.
- **Log Aggregation and Processing:** Collects and processes logs from various sources for centralized monitoring and analysis.
- **Data Integration and Streaming:** Integrates data from different sources and enables real-time data analysis.