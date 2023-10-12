# Installation Configuration

### Telemetry Config

```
#Telemetry producer related info
telemetry_pdata_id=local.sunbird.learning.service
telemetry_pdata_pid=learning-service
telemetry_pdata_ver=4.7.0
```

### KeyClock Config

```
sunbird_keycloak_required_action_link_expiration_seconds=155520000
```

### SSO Config:

```
sso.url=
sso.realm=sunbird
sso.connection.pool.size=20
sso.enabled=true
sunbird_sso_client_id=
sunbird_sso_username=
sunbird_sso_password=
sunbird_sso_url=
sunbird_sso_realm=
```

### Elastic Search Config:

```
es.cluster.name=test
es.host.name=localhost
es.host.port=9300
#elastic search top n result count for telemetry
searchTopN=5
```

### Cassandra Config

```
coreConnectionsPerHostForLocal=4
coreConnectionsPerHostForRemote=2
maxConnectionsPerHostForLocal=10
maxConnectionsPerHostForRemote=4
maxRequestsPerConnection=32768
heartbeatIntervalSeconds=60
poolTimeoutMillis=0
queryLoggerConstantThreshold=300
```

### Kafka Config

```
kafka_urls=localhost:9092
kafka_linger_ms=5
```

### Notification Config

```
notification_service_base_url=
notification_service_v2_send_url=/private/v2/notification/send
notification_service_v1_update_url=/private/v1/notification/feed/update
notification_service_v1_read_url=/private/v1/notification/feed/read
notification_service_v1_delete_url=/private/v1/notification/feed/delete
#NIC
nic_sms_gateway_provider_base_url=https://smsgw.sms.gov.in/failsafe/HttpLink
```

### Message Config

```
sunbird.msg.91.country=91
sunbird.msg.91.sender=TesSun
sunbird.msg.91.auth=
sunbird.msg.91.method=POST
sunbird.msg.91.route=4
sunbird.msg.91.baseurl=http://api.msg91.com/
sunbird.msg.91.get.url=api/sendhttp.php?
sunbird.msg.91.post.url=api/v2/sendsms
```

### Mail Template Config

```
orgName=Diksha
onboarding_mail_subject=Welcome to {0}
onboarding_welcome_message=Welcome to {0}
onboarding_welcome_mail_body=Please ensure that you change your password according to instructions when you log in for the first time.
mail_note=Note: This is an automatic alert email. Replies to this mail box will not be monitored. If you are not the intended recipient of this message, or need to communicate with the team, write to
```

### Mail Config

```
sunbird_mail_server_host=
sunbird_mail_server_port=
sunbird_mail_server_username=
sunbird_mail_server_password=
sunbird_mail_server_from_email=support@open-sunbird.org
sunbird_account_name=
sunbird_account_key=
sunbird_encryption_key=SunBird
sunbird_encryption=ON
```

### SMS Config

```
nic_sms_gateway_provider_base_url=https://smsgw.sms.gov.in/failsafe/HttpLink
sms_gateway_provider=91SMS
```

### Other Config

```
sunbird_installation=sunbird
sunbird_analytics_api_base_url=https://dev.ekstep.in/api/data/v3
ekstep_api_base_url=https://dev.ekstep.in/api
sunbird_allowed_login=You can use your cellphone number to login
sunbird_web_url=https://dev.sunbirded.org
sunbird_framework_read_api=/v1/framework/read
fcm.url=https://fcm.googleapis.com/fcm/send
#put the default evn logo url here or System Env variable with 
#same key. code will first search from EVN then here.
sunbird_env_logo_url=http://via.placeholder.com/100x50
system_settings_properties=phoneUnique,emailUnique
sunbird_default_welcome_sms=Welcome to DIKSHA.
sunbird_url_shortner_base_url=https://api-ssl.bitly.com/v3/shorten?access_token=
sunbird_url_shortner_access_token=
ekstep.channel.reg.api.url=/channel/v3/create
ekstep.channel.list.api.url=/channel/v3/list
ekstep.channel.update.api.url=/channel/v3/update
sunbird_valid_location_types=state,district,block,cluster,school;
sunbird_default_channel=
sunbird_url_shortner_enable=false
sunbird_analytics_blob_account_name=
sunbird_analytics_blob_account_key=
sunbird_state_img_url=https://sunbirddev.blob.core.windows.net/orgemailtemplate/img/File-0128212938260643843.png
sunbird_diksha_img_url=https://sunbirddev.blob.core.windows.net/orgemailtemplate/img/File-0128212989820190722.png
sunbird_cert_completion_img_url=https://sunbirddev.blob.core.windows.net/orgemailtemplate/img/File-0128212919987568641.png
sunbird_reset_pass_msg=Your have requested to reset password. Click on the link to set a password: {0}
sunbird_reset_pass_mail_subject=Reset Password
sunbird_subdomain_keycloak_base_url=https://merge.dev.sunbirded.org/auth/kafka_linger_ms=5
sunbird_user_upload_error_visualization_threshold=20001
migrate_user_template=You can now access your {0} state teacher account using {1}. Please log out and login once again to see updated details.
sunbird_account_merge_subject=Account merged successfully
sunbird_pass_regex=(?=.*[0-9])(?=.*[a-z])(?=.*[A-Z])(?=.*[!\"#$%&'()*+,-./:;<=>?@\\[\\]^_`{|}~])(?=\\S+$).{8,}
sunbird_user_create_sync_type=ES
sunbird_user_create_sync_topic=local.user.events
sigterm_stop_delay=40
limit_managed_user_creation=true
adminutil_base_url = http://adminutil:4000/
adminutil_sign_endpoint = v1/sign/payload
self_declared_mandatory_fields = Diksha UUID,Status,State provided ext. ID,Channel,Persona
self_declared_optional_fields = School Name,School UDISE ID,Email ID,Phone number,Error Type
enable_captcha=true
consent_expiry_in_days=100
feed_limit=30
learner_in_memory_cache_ttl=14400
user_index_alias=user_alias
defaultMonthDate = -12-31
org_index_alias=org_alias
stacktrace_char_length=2500
channel_registration_disabled=false
```
