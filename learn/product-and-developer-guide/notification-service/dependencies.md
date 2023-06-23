# Dependencies

{% tabs %}
{% tab title="Sunbird Lern - UserOrg Service" %}
Notification Service has dependency to UserOrg service. It fetches the custodian org id from UserOrg using system settings API. This custodian org id is added to the channel value and then to request context. This in turn gets injected into telemetry data and logs.

**Dependency API:**

/api/data/v1/system/settings/list

/v1/org/read
{% endtab %}

{% tab title="Sunbird Lern - Data-pipeline" %}
Notification Service is dependent on Notification Flink Job in Lern data-pipeline to process Async Notifications.

Kafka Topic : {env}.lms.notification
{% endtab %}
{% endtabs %}



The Notification service requires a few configurations to be set in the properties file. Some of these properties can also be set as environment variables.

{% embed url="https://github.com/sunbird-lern/sunbird-notification-service/tree/release-4.5.0/sb-utils/src/main/resources" %}

{% embed url="https://github.com/sunbird-lern/sunbird-notification-service/tree/master/notification-sdk/src/main/resources" %}

