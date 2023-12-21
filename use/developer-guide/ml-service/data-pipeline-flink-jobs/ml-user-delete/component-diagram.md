# Component Diagram



<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-12-15 at 5.09.19 PM.png" alt=""><figcaption></figcaption></figure>

The Ml User Delete service is constructed upon the framework of Flink, Kafka and Mongo, a powerful approach for updating and managing data in a scalable and real-time manner.

1. **Apache Kafka** is a distributed event streaming platform that is designed for handling high volumes of real-time data. In this service, Kafka generates user data (userId, organisationId) as a JSON event when a user chooses to remove their account from the Sunbird platform.
2. **Apache Flink** is a stream processing framework that provides high-throughput, low-latency, and exactly-once processing of streaming data. Flink uses the Kafka event and establishes a connection with the Mongo database to update documents from various collections.
3. **Mongo Database** is a distributed NoSQL database that is designed to handle massive amounts of data across many commodity servers, ensuring high availability and fault tolerance. User data containing user personally identifiable information will be updated.

**Configuration variables:**

<table><thead><tr><th width="246">Variable</th><th>Default Value</th><th>Purpose</th></tr></thead><tbody><tr><td>kafka.input.topic</td><td>{{env}}.delete.user</td><td>Kafka topic from which messages/events are read to be processed.</td></tr><tr><td>kafka.groupId</td><td>{{env}}ml-user-delete-group</td><td>Kafka input topic group Id</td></tr></tbody></table>
