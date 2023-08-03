# Architecture

## Notification Service **Architecture**

<div data-full-width="true">

<figure><img src="../../../../.gitbook/assets/LMS-ServiceFlowDiagram-Notification Service.drawio.png" alt=""><figcaption><p>Notification Service Architecture</p></figcaption></figure>

</div>

## Flow Diagram

<div data-full-width="true">

<figure><img src="../../../../.gitbook/assets/NotificationFlowDiagram-Overall-FlowDiagram.drawio.png" alt=""><figcaption><p>Notification Service Flow Diagram</p></figcaption></figure>

</div>

1. From Notification Service **Sync AP**I call is sent to the **SMS/email** provider and **Async API** call is sent to the **Kafka cluster**.
2. If processing the notification is failed then the same message is pushed to the topic **Kafka** and then it is processed by the notification flink job in Lern data-pipeline.
