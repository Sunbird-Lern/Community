# Installation Guide

### How To Setup

Please refer to the github readme document.

{% embed url="https://github.com/sunbird-lern/sunbird-notification-service/blob/master/README.md" %}

### **Installation Configuration:**

Notification service requires few configurations to be set in properties file. Some of these properties can also be set as environment variables.

{% embed url="https://github.com/sunbird-lern/sunbird-notification-service/tree/release-4.5.0/sb-utils/src/main/resources" %}

{% embed url="https://github.com/sunbird-lern/sunbird-notification-service/tree/master/notification-sdk/src/main/resources" %}

Cassandra Migration in sunbird-utils needs to be run before notification service run to create necessary table required by the notification service.

Database details need to be configured in [cassandra.config.properties](https://github.com/sunbird-lern/sunbird-notification-service/blob/release-4.5.0/sb-utils/src/main/resources/cassandra.config.properties) file.

There is no dependency when sending notifications in sync mode. But while sending async notifications, application needs notification flink job to run. This need to be setup along with kafka.

Repository for sunbird jobs(Before 5.0.0): [https://github.com/project-sunbird/sunbird-lms-jobs](https://github.com/project-sunbird/sunbird-lms-jobs)

Repository for sunbird jobs(After 5.0.0): [https://github.com/Sunbird-Lern/data-pipeline/tree/master/lms-jobs](https://github.com/Sunbird-Lern/data-pipeline/tree/master/lms-jobs)

**Steps for setting up notification flink job:**

[https://github.com/Sunbird-Lern/data-pipeline/blob/master/README.md](https://github.com/Sunbird-Lern/data-pipeline/blob/master/README.md)
