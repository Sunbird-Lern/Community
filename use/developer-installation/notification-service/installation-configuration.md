# Installation Configuration

### Cassandra Config

```
coreConnectionsPerHostForLocal=4
coreConnectionsPerHostForRemote=2
maxConnectionsPerHostForLocal=10
maxConnectionsPerHostForRemote=4
maxRequestsPerConnection=32768
heartbeatIntervalSeconds=60
poolTimeoutMillis=0
contactPoint=127.0.0.1
port=9042
userName=cassandra
password=password
queryLoggerConstantThreshold=300
keyspace=sunbird_notifications  
```

### Cassandra Table Column Config

```
id=id
userid=userId
createdon=createdOn
createdby=createdBy
updatedon=updatedOn
updatedby=updatedBy
templateid=templateId
expireon=expireOn
feedid=feedId
```

### Telemetry Config

```
telemetry_pdata_id=dev.sunbird.notifications.service
telemetry_pdata_pid=notification-service
telemetry_pdata_ver=4.5.0
```

### Keyclock Config

```
sunbird_sso_client_id=
sunbird_sso_username=
sunbird_sso_password=
sunbird_sso_url=
sunbird_sso_realm=
```

### UserOrg Config

```
sunbird_us_system_setting_url=/api/data/v1/system/settings/list
sunbird_us_org_read_url=/v1/org/read
LEARNER_SERVICE_PORT=
```

### SMS Config

{% content-ref url="../../../learn/product-and-developer-guide/user-and-org-service/configuration/sms-configuration.md" %}
[sms-configuration.md](../../../learn/product-and-developer-guide/user-and-org-service/configuration/sms-configuration.md)
{% endcontent-ref %}

### Email Config

{% content-ref url="../../../learn/product-and-developer-guide/user-and-org-service/configuration/email-notification-configuration.md" %}
[email-notification-configuration.md](../../../learn/product-and-developer-guide/user-and-org-service/configuration/email-notification-configuration.md)
{% endcontent-ref %}

### Other Config

```
sunbird_fcm_url=https://fcm.googleapis.com/fcm/send
sunbird_notification_otp_default_message=Your verification code is ##OTP##

```
