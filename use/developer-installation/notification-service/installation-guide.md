# Installation Guide

### How To Setup

Please refer to the github readme document.

{% embed url="https://github.com/sunbird-lern/sunbird-notification-service/blob/master/README.md" %}

### **Installation Configuration:**

Notification service requires few configurations to be set in properties file. Some of these properties can also be set as environment variables.

{% embed url="https://github.com/sunbird-lern/sunbird-notification-service/tree/release-4.5.0/sb-utils/src/main/resources" %}

{% embed url="https://github.com/sunbird-lern/sunbird-notification-service/tree/master/notification-sdk/src/main/resources" %}

Cassandra Migration in sunbird-utils needs to be run before group service run to create necessary table required by the group service.

Database details need to be configured in [cassandra.config.properties](https://github.com/sunbird-lern/sunbird-notification-service/blob/release-4.5.0/sb-utils/src/main/resources/cassandra.config.properties) file.

There is no dependency when sending notifications in sync mode. But while sending async notifications, application needs notification samza job to run. This need to be setup along with kafka and hadoop.

Repository for sunbird jobs(Before 5.0.0): [https://github.com/project-sunbird/sunbird-lms-jobs](https://github.com/project-sunbird/sunbird-lms-jobs)

Repository for sunbird jobs(After 5.0.0): [https://github.com/Sunbird-Lern/data-pipeline/tree/master/lms-jobs](https://github.com/Sunbird-Lern/data-pipeline/tree/master/lms-jobs)

**Steps for running notification samza job:**

The following wiki page contains steps to run notification samza job.

{% embed url="https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/1087307787/How+to+Set+up+kafka+hadoop+samza+in+local" %}
notification-job
{% endembed %}
