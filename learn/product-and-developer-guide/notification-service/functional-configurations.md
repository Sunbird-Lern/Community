# Functional Configurations

### **Configuration Restriction**

**Max Batch Limit:** MAX\_BATCH\_LIMIT needs to be configured so that will be the max ids can be passed in a single notification object.

{% tabs %}
{% tab title="Functional Config" %}
```
version_support_config_enable=True
feed_limit=31
sunbird_notification_default_country_code=91
sunbird_notification_msg_default_sender=TesSun
sunbird_msg_91_route=4
sunbird_notification_otp_length=4
sunbird_notification_otp_expiry_in_minute=30
notification_category_type_config=certificateUpload,member-added
```
{% endtab %}

{% tab title="System Config" %}
| JSON Key                                      | Key                                                            | Default Value                                                                |
| --------------------------------------------- | -------------------------------------------------------------- | ---------------------------------------------------------------------------- |
|                                               | ENV\_NAME                                                      | sunbirdstaging                                                               |
| USER\_SERVICE\_BASE\_URL                      | LEARNER\_SERVICE\_PORT                                         | [http://learner-service:9000](http://learner-service:9000)                   |
| SUNBIRD\_KAFKA\_URL                           | SUNBIRD\_KAFKA\_URL                                            | 11.3.2.16:9092,11.3.2.15:9092,11.3.2.14:9092                                 |
| ACCESS\_TOKEN\_PUBLICKEY\_BASEPATH            | accesstoken.publickey.basepath                                 | /keys/                                                                       |
| NOTIFICATION\_CATEGORY\_TYPE\_CONFIG          | notification\_category\_type\_config                           | certificateUpdate                                                            |
| SUNBIRD\_CASSANDRA\_CONSISTENCY\_LEVEL        | sunbird\_cassandra\_consistency\_level                         | quorum                                                                       |
| SUNBIRD\_CASSANDRA\_IP                        | sunbird\_cassandra\_host                                       | 11.3.2.4,11.3.2.5,11.3.2.6                                                   |
| Not there                                     | sunbird\_cassandra\_notification\_keyspace                     | sunbird\_notifications                                                       |
| Not there                                     | sunbird\_cassandra\_password                                   | password                                                                     |
| Not there                                     | sunbird\_cassandra\_port                                       | 9042,9042,9042                                                               |
| Not there                                     | sunbird\_cassandra\_username                                   | cassandra                                                                    |
| Not there                                     | sunbird\_keycloak\_required\_action\_link\_expiration\_seconds | 2592000                                                                      |
| Not there                                     | sunbird\_keycloak\_user\_federation\_provider\_id              | provider\_id                                                                 |
| EMAIL\_SERVER\_FROM                           | sunbird\_mail\_server\_from\_email                             | support@staging.sunbirded.org                                                |
| EMAIL\_SERVER\_HOST                           | sunbird\_mail\_server\_host                                    | smtp.sendgrid.net                                                            |
| EMAIL\_SERVER\_PASSWORD                       | sunbird\_mail\_server\_password                                | eg: password                                                                 |
| EMAIL\_SERVER\_PORT                           | sunbird\_mail\_server\_port                                    | 589                                                                          |
| EMAIL\_SERVER\_USERNAME                       | sunbird\_mail\_server\_username                                | apikey                                                                       |
| SUNBIRD\_MSG\_91\_AUTH                        | sunbird\_msg\_91\_auth                                         | auth                                                                         |
| sunbird\_notification\_kafka\_servers\_config | sunbird\_notification\_kafka\_servers\_config                  | 11.3.2.16:9092,11.3.2.15:9092,11.3.2.14:9092                                 |
| sunbird\_notification\_kafka\_topic           | sunbird\_notification\_kafka\_topic                            | sunbirdstaging.lms.notification                                              |
| sunbird\_notification\_msg\_default\_sender   | sunbird\_notification\_msg\_default\_sender                    | DKSAPP                                                                       |
| sunbird\_sso\_client\_id                      | sunbird\_sso\_client\_id                                       | lms                                                                          |
| Not there                                     | sunbird\_sso\_client\_secret                                   | eg: id                                                                       |
| sunbird\_sso\_password                        | sunbird\_sso\_password                                         | eg: password                                                                 |
| Not there                                     | sunbird\_sso-publickey                                         | eg: public key                                                               |
| SUNBIRD\_SSO\_REALM                           | sunbird\_sso\_realm                                            | sunbird                                                                      |
| SUNBIRD\_SSO\_URL                             | sunbird\_sso\_url                                              | [ https://staging.sunbirded.org/auth/ ](https://staging.sunbirded.org/auth/) |
| sunbird\_sso\_username                        | sunbird\_sso\_username                                         | sunbird-staging-new-admi                                                     |
| USER\_SERVICE\_ORG\_READ\_URL                 | sunbird\_us\_org\_read\_url                                    | /v1/org/read                                                                 |
| USER\_SERVICE\_SYSTEM\_SETTING\_URL           | sunbird\_us\_system\_setting\_url                              | /api/data/v1/system/settings/list                                            |
|                                               |                                                                |                                                                              |


{% endtab %}
{% endtabs %}
