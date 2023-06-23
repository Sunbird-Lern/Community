# Functional Configurations

### **Configuration Restriction**

{% tabs %}
{% tab title="Functional Config" %}
```
version_support_config_enable=True
feed_limit=31
sunbird_notification_default_country_code=91
sunbird_msg_91_route=4
sunbird_notification_otp_length=4
sunbird_notification_otp_expiry_in_minute=30
notification_category_type_config=certificateUpload,member-added
```
{% endtab %}

{% tab title="System Config" %}
<table><thead><tr><th width="233">JSON Key</th><th width="232.66666666666666">Key</th><th>Default Value</th></tr></thead><tbody><tr><td></td><td>ENV_NAME</td><td>sunbirdstaging</td></tr><tr><td>USER_SERVICE_BASE_URL</td><td>LEARNER_SERVICE_PORT</td><td>http://userorg-service:9000</td></tr><tr><td>SUNBIRD_KAFKA_URL</td><td>SUNBIRD_KAFKA_URL</td><td>&#x3C;ip>:9092,1&#x3C;ip>:9092,&#x3C;ip>:9092</td></tr><tr><td>ACCESS_TOKEN_PUBLICKEY_BASEPATH</td><td>accesstoken.publickey.basepath</td><td>/keys/</td></tr><tr><td>SUNBIRD_CASSANDRA_CONSISTENCY_LEVEL</td><td>sunbird_cassandra_consistency_level</td><td>quorum</td></tr><tr><td>SUNBIRD_CASSANDRA_IP</td><td>sunbird_cassandra_host</td><td>ip1,ip2,ip3</td></tr><tr><td>EMAIL_SERVER_FROM</td><td>sunbird_mail_server_from_email</td><td>support@staging.sunbirded.org</td></tr><tr><td>EMAIL_SERVER_HOST</td><td>sunbird_mail_server_host</td><td>smtp.sendgrid.net</td></tr><tr><td>EMAIL_SERVER_PASSWORD</td><td>sunbird_mail_server_password</td><td>eg: password</td></tr><tr><td>EMAIL_SERVER_PORT</td><td>sunbird_mail_server_port</td><td>589</td></tr><tr><td>EMAIL_SERVER_USERNAME</td><td>sunbird_mail_server_username</td><td>apikey</td></tr><tr><td>SUNBIRD_MSG_91_AUTH</td><td>sunbird_msg_91_auth</td><td>auth</td></tr><tr><td>sunbird_notification_kafka_servers_config</td><td>sunbird_notification_kafka_servers_config</td><td>&#x3C;ip>:9092,1&#x3C;ip>:9092,&#x3C;ip>:9092</td></tr><tr><td>sunbird_notification_kafka_topic</td><td>sunbird_notification_kafka_topic</td><td>{env}.lms.notification</td></tr><tr><td>SUNBIR_MSG_DEFAULT_SENDER</td><td>sunbird_notification_msg_default_sender</td><td>sender id registered with SMS provider. Eg: TesSun</td></tr><tr><td>SUNBIRD_SSO_REALM</td><td>sunbird_sso_realm</td><td>sunbird</td></tr><tr><td>SUNBIRD_SSO_URL</td><td>sunbird_sso_url</td><td> Keycloak URL sample : https://staging.sunbirded.org/auth/ </td></tr><tr><td>USER_SERVICE_ORG_READ_URL</td><td>sunbird_us_org_read_url</td><td>/v1/org/read</td></tr><tr><td>USER_SERVICE_SYSTEM_SETTING_URL</td><td>sunbird_us_system_setting_url</td><td>/api/data/v1/system/settings/list</td></tr><tr><td>SUNBIRD_MSG_91_BASEURL</td><td>sunbird_msg_91_baseurl</td><td><a href="http://api.msg91.com/">http://api.msg91.com/</a></td></tr><tr><td>SUNBIRD_MSG_91_GET_URL</td><td>sunbird_msg_91_get_url</td><td>api/sendhttp.php?</td></tr><tr><td>SUNBIRD_MSG_91_POST_URL</td><td>sunbird_msg_91_post_url</td><td>api/v2/sendsms</td></tr><tr><td></td><td>sunbird_fcm_url</td><td><a href="https://fcm.googleapis.com/fcm/send">https://fcm.googleapis.com/fcm/send</a></td></tr><tr><td>IS_MULTI_DC_ENABLED</td><td>isMultiDCEnabled</td><td>False</td></tr><tr><td>SUNBIRD_FCM_ACCOUNT_KEY</td><td>sunbird_notification_fcm_account_key</td><td></td></tr><tr><td></td><td></td><td></td></tr></tbody></table>


{% endtab %}
{% endtabs %}
