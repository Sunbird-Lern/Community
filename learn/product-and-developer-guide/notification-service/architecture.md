# Architecture

#### **Architecture Diagram:**

<figure><img src="../../../.gitbook/assets/Notification-Architecture.png" alt=""><figcaption></figcaption></figure>

Flow Diagram:

<figure><img src="../../../.gitbook/assets/NotificationFlowDiagram-Overall-FlowDiagram.drawio.png" alt=""><figcaption></figcaption></figure>

Code Flow Diagram:

<figure><img src="../../../.gitbook/assets/NotificationFlowDiagram-Code Flow Diagram.drawio (1).png" alt=""><figcaption></figcaption></figure>

1. From Notification Service **Sync AP**I call is sent to the **SMS/email** provider and **Async API** call is sent to the **Kafka cluster**.
2. If processing the notification is failed then the same message is pushed to the topic **Kafka** and then it is processed by the notification flink job in Lern data-pipeline.
