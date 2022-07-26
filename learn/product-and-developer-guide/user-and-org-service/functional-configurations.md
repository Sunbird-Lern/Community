# Functional Configurations

{% tabs %}
{% tab title="Functional Config" %}


```
sunbird_username_num_digits=4
download_link_expiry_timeout=300
sunbird_default_country_code=+91
sunbird_encryption_key=SunBird
sunbird_encryption=ON
sunbird_otp_allowed_attempt=2
```

### Bulk Upload Config

```
#size of bulk upload data is 1001 including header in csv file
sunbird_user_bulk_upload_size=1001
bulk_upload_org_data_size=300
# Bulk upload file max size in MB
file_upload_max_size=10
```

### Batch Service Config

```
# Batch size for cassandra batch operation
cassandra_write_batch_size=100
```

### OTP Config

```
sunbird_otp_expiration=1800
sunbird_otp_length=6
sunbird_otp_hour_rate_limit=5
sunbird_otp_day_rate_limit=20
```

### Other Config

```
managed_user_limit=30
sunbird_api_request_lower_case_fields=source,externalId,userName,provider,loginId,email,prevUsedEmail
sunbird_rate_limit_enabled=true
sunbird_health_check_enable=true
sunbird_sync_read_wait_time=1500
sunbird_gzip_size_threshold=262144
sunbird_fuzzy_search_threshold=0.5
ekstep_authorization=
```
{% endtab %}

{% tab title="UserOrg System Config" %}


| JSON Key                                          | Key                                                            | Default Value                                                                  |
| ------------------------------------------------- | -------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| ENV\_NAME                                         | ENV\_NAME                                                      | sunbirdstaging                                                                 |
| <p><br>PORTAL_SERVICE_PORT</p>                    | PORTAL\_SERVICE\_PORT                                          | http://player.staging.svc.cluster.local:3000                                   |
| <p>SUNBIRD_KAFKA_URL<br></p>                      | sunbird\_KAFKA\_URL                                            | 11.3.2.16:9092,11.3.2.15:9092,11.3.2.14:9092                                   |
| <p><br></p>                                       | accesstoken.publickey.basepath                                 | /keys/                                                                         |
| <p><br></p>                                       | api\_actor\_provider                                           | local (off)                                                                    |
| <p><br></p>                                       | background\_actor\_provider                                    | local (remote)                                                                 |
| <p><br>EKSTEP_BASE_URL</p>                        | ekstep\_api\_base\_url                                         | http://11.3.3.22:8080/learning-service                                         |
| <p><br>EKSTEP_AUTHORIZATION</p>                   | ekstep\_authorization                                          | eg: public\_key                                                                |
| <p><br></p>                                       | feed\_limit                                                    | 30                                                                             |
| <p><br>FORM_API_ENDPOINT</p>                      | form\_api\_endpoint                                            | /plugin/v1/form/read                                                           |
| <p><br>GOOGLE_CAPTCHA_PRIVATE_KEY</p>             | google\_captcha\_mobile\_private\_key                          | eg: mbl\_private\_key                                                          |
| <p>GOOGLE_CAPTCHA_PRIVATE_KEY<br></p>             | google\_captcha\_private\_key                                  | eg: private\_key                                                               |
| <p>SUNBIRD_KAFKA_URL<br></p>                      | kafka\_urls                                                    | 11.3.2.16:9092,11.3.2.15:9092,11.3.2.14:9092                                   |
|                                                   | learner\_in\_memory\_cache\_ttl                                | 600                                                                            |
| NOTIFICATION\_SERVICE\_BASE\_URL                  | notification\_service\_base\_url                               | http://notification-service:9000                                               |
| <p><br></p>                                       | org\_index\_alias                                              | org\_alias                                                                     |
| <p><br></p>                                       | quartz\_shadow\_user\_migration\_timer                         | 0 0/10 \* 1/1 \* ? \*                                                          |
| ACCOUNT\_KEY                                      | sunbird\_account\_key                                          | eg: key                                                                        |
| ACCOUNT\_NAME                                     | sunbird\_account\_name                                         | sunbirdstagingpublic                                                           |
| <p>ANALYTICS_API_BASE_URL<br></p>                 | sunbird\_analytics\_api\_base\_url                             | http://analytics-service.staging.svc.cluster.local:9000                        |
| ANALYTICS\_ACCOUNT\_KEY                           | sunbird\_analytics\_blob\_account\_key                         | eg: key                                                                        |
| ANALYTICS\_ACCOUNT\_NAME                          | sunbird\_analytics\_blob\_account\_name                        | sunbirdstagingprivate                                                          |
| SUNBIRD\_API\_BASE\_URL                           | sunbird\_api\_base\_url                                        | http://knowledge-mw-service:5000                                               |
| SUNBIRD\_AUTHORIZATION                            | sunbird\_authorization                                         | eg: key                                                                        |
|                                                   | sunbird\_badger\_baseurl                                       | http://badger-service:8004                                                     |
| <p><br>SUNBIRD_CASSANDRA_CONSISTENCY_LEVEL</p>    | sunbird\_cassandra\_consistency\_level                         | quorum                                                                         |
| SUNBIRD\_CASSANDRA\_IP                            | sunbird\_cassandra\_host                                       | 11.3.2.4,11.3.2.5,11.3.2.6                                                     |
| <p><br></p>                                       | sunbird\_cassandra\_password                                   | password                                                                       |
| <p><br></p>                                       | sunbird\_cassandra\_port                                       | 9042, 9042, 9042                                                               |
| <p><br></p>                                       | sunbird\_cassandra\_username                                   | cassandra                                                                      |
| <p><br></p>                                       | sunbird\_default\_channel                                      | ntp                                                                            |
| SUNBIRD\_EMAIL\_MAX\_RECEPIENT\_LIMIT             | sunbird\_email\_max\_recipients\_limit                         | 100                                                                            |
| ENCRYPTION\_KEY                                   | sunbird\_encryption\_key                                       | eg: key                                                                        |
| <p><br></p>                                       | sunbird\_encryption\_mode                                      | local                                                                          |
| SUNBIRD\_ENV\_LOGO\_URL                           | sunbird\_env\_logo\_url                                        | https://staging.sunbirded.org/tenant/ntp/logo.png                              |
| SUNBIRD\_ES\_IP                                   | sunbird\_es\_host                                              | 11.3.2.811.3.2.8,11.3.2.9,11.3.2.10                                            |
| SUNBIRD\_ES\_PORT                                 | sunbird\_es\_port                                              | 9300,9300,93009300                                                             |
| SUNBIRD\_FUZZY\_SEARCH\_THRESHOLD                 | sunbird\_fuzzy\_search\_threshold                              | 0.5                                                                            |
| SUNBIRD\_HEALTH\_CHECK\_ENABLE                    | sunbird\_health\_check\_enable                                 | false                                                                          |
| SUNBIRD\_INSTALLATION                             | sunbird\_installation                                          | sunbird\_Stage                                                                 |
| SUNBIRD\_INSTALLATION\_DISPLAY\_NAME              | sunbird\_installation\_display\_name\_for\_sms                 | DIKSHA                                                                         |
| <p><br></p>                                       | sunbird\_installation\_email                                   | dummy@dummy.org                                                                |
| SUNBIRD\_KEYCLOAK\_LINK\_EXPIRATION\_TIME         | sunbird\_keycloak\_required\_action\_link\_expiration\_seconds | 2592000                                                                        |
| SUNBIRD\_KEYCLOAK\_USER\_FEDERATION\_PROVIDER\_ID | sunbird\_keycloak\_user\_federation\_provider\_id              | eg: id                                                                         |
| EMAIL\_SERVER\_FROM                               | sunbird\_mail\_server\_from\_email                             | support@staging.sunbirded.org                                                  |
| EMAIL\_SERVER\_HOST                               | sunbird\_mail\_server\_host                                    | smtp.sendgrid.net                                                              |
| EMAIL\_SERVER\_PASSWORD                           | sunbird\_mail\_server\_password                                | eg: password                                                                   |
| EMAIL\_SERVER\_PORT                               | sunbird\_mail\_server\_port                                    | 587                                                                            |
| EMAIL\_SERVER\_USERNAME                           | sunbird\_mail\_server\_username                                | apikey                                                                         |
| <p><br></p>                                       | sunbird\_msg\_91\_auth                                         | eg: key                                                                        |
| <p><br></p>                                       | sunbird\_msg\_sender                                           | DKSAPP                                                                         |
| <p><br></p>                                       | sunbird\_mw\_system\_host                                      | learner-service                                                                |
| <p><br></p>                                       | sunbird\_mw\_system\_port                                      | 8088                                                                           |
| SUNBIRD\_OTP\_ALLOWED\_ATTEMPT                    | sunbird\_otp\_allowed\_attempt                                 | 2                                                                              |
| SUNBIRD\_OTP\_EXPIRATION                          | sunbird\_otp\_expiration                                       | 1800                                                                           |
| SUNBIRD\_OTP\_LENGTH                              | sunbird\_otp\_length                                           | 6                                                                              |
| <p><br></p>                                       | sunbird\_pg\_db                                                | quartz                                                                         |
| <p><br></p>                                       | sunbird\_pg\_host                                              | staging-pg11.postgres.database.azure.com                                       |
| <p><br></p>                                       | sunbird\_pg\_password                                          | eg: password                                                                   |
| <p><br></p>                                       | sunbird\_pg\_port                                              | 5432                                                                           |
| <p><br></p>                                       | sunbird\_pg\_user                                              | sunbirdstaging@staging-pg11                                                    |
| <p><br></p>                                       | sunbird\_quartz\_mode                                          | cluster                                                                        |
| <p><br></p>                                       | sunbird\_remote\_bg\_req\_router\_path                         | akka.tcp://SunbirdMWSystem@actor-service:8088/user/BackgroundRequestRouter     |
| <p><br></p>                                       | sunbird\_remote\_req\_router\_path                             | akka.tcp://SunbirdMWSystem@actor-service:8088/user/RequestRouter               |
| <p><br></p>                                       | sunbird\_reset\_pass\_msg                                      | You have requested to reset password. Click on the link to set a password: {0} |
| SUNBIRD\_SSO\_CLIENT\_ID                          | sunbird\_sso\_client\_id                                       | lms                                                                            |
| SUNBIRD\_SSO\_CLIENT\_SECRET                      | sunbird\_sso\_client\_secret                                   | eg: key                                                                        |
| SUNBIRD\_SSO\_LB\_IP                              | sunbird\_sso\_lb\_ip                                           | http://11.3.0.17                                                               |
| SUNBIRD\_SSO\_PASSWORD                            | sunbird\_sso\_password                                         | eg: password                                                                   |
| SSO\_PUBLIC\_KEY                                  | sunbird\_sso\_publickey                                        | eg: key                                                                        |
| SSO\_REALM                                        | sunbird\_sso\_realm                                            | sunbird                                                                        |
| SSO\_URL                                          | sunbird\_sso\_url                                              | https://staging.sunbirded.org/auth/                                            |
| SSO\_USERNAME                                     | sunbird\_sso\_username                                         | sunbird-staging-new-admin                                                      |
| SUNBIRD\_SUBDOMAIN\_KEYCLOAK\_BASE\_URL           | sunbird\_subdomain\_keycloak\_base\_url                        | https://merge.staging.sunbirded.org/auth/                                      |
|                                                   | sunbird\_url\_shortner\_access\_token                          | eg: token                                                                      |
| SUNBIRD\_URL\_SHORTNER\_ENABLE                    | sunbird\_url\_shortner\_enable                                 | True                                                                           |
| BULK\_UPLOAD\_USER\_DATA\_SIZE                    | sunbird\_user\_bulk\_upload\_size                              | 1001                                                                           |
| SUNBIRD\_USER\_CERT\_KAFKA\_TOPIC                 | sunbird\_user\_cert\_kafka\_topic                              | sunbirdstaging.lms.user.account.merge                                          |
| SUNBIRD\_WEB\_URL                                 | sunbird\_web\_url                                              | https://staging.sunbirded.org                                                  |
| PDATA\_ID                                         | telemetry\_pdata\_id                                           | staging.sunbird.learning.service                                               |
| PDATA\_PID                                        | telemetry\_pdata\_pid                                          | learner-service                                                                |
| <p><br></p>                                       | user\_index\_alias                                             | user\_alias                                                                    |
{% endtab %}

{% tab title="Admin Utils System Config" %}


| Key                                          | Default Value                                                            |
| -------------------------------------------- | ------------------------------------------------------------------------ |
| ACCESS\_TOKEN\_VALIDITY                      | 86400                                                                    |
| AM\_ADMIN\_API\_ACCESS\_BASEPATH             | /keys/                                                                   |
| AM\_ADMIN\_API\_ACCESS\_KEYCOUNT             | 10                                                                       |
| AM\_ADMIN\_API\_ACCESS\_KEYPREFIX            | accessv1\_key                                                            |
| AM\_ADMIN\_API\_ACCESS\_KEYSTART             | 1                                                                        |
| AM\_ADMIN\_API\_DESKTOP\_DEVICE\_BASEPATH    | /keys/                                                                   |
| AM\_ADMIN\_API\_DESKTOP\_DEVICE\_KEYCOUNT    | 10                                                                       |
| AM\_ADMIN\_API\_DESKTOP\_DEVICE\_KEYPREFIX   | desktop\_devicev2\_key                                                   |
| AM\_ADMIN\_API\_DESKTOP\_DEVICE\_KEYSTART    | 1                                                                        |
| AM\_ADMIN\_API\_ENDPOINT                     | http://kong.staging.svc.cluster.local:8001                               |
| AM\_ADMIN\_API\_KEYS                         | mobile\_device,desktop\_device,portal\_anonymous,portal\_loggedin,access |
| AM\_ADMIN\_API\_MOBILE\_DEVICE\_BASEPATH     | /keys/                                                                   |
| AM\_ADMIN\_API\_MOBILE\_DEVICE\_KEYCOUNT     | 10                                                                       |
| AM\_ADMIN\_API\_MOBILE\_DEVICE\_KEYPREFIX    | mobile\_devicev2\_key                                                    |
| AM\_ADMIN\_API\_MOBILE\_DEVICE\_KEYSTART     | 11                                                                       |
| AM\_ADMIN\_API\_PORTAL\_ANONYMOUS\_BASEPATH  | /keys/                                                                   |
| AM\_ADMIN\_API\_PORTAL\_ANONYMOUS\_KEYCOUNT  | 10                                                                       |
| AM\_ADMIN\_API\_PORTAL\_ANONYMOUS\_KEYPREFIX | portal\_anonymous\_key                                                   |
| AM\_ADMIN\_API\_PORTAL\_ANONYMOUS\_KEYSTART  | 1                                                                        |
| AM\_ADMIN\_API\_PORTAL\_LOGGEDIN\_BASEPATH   | /keys/                                                                   |
| AM\_ADMIN\_API\_PORTAL\_LOGGEDIN\_KEYCOUNT   | 10                                                                       |
| AM\_ADMIN\_API\_PORTAL\_LOGGEDIN\_KEYPREFIX  | portal\_loggedin\_key                                                    |
| AM\_ADMIN\_API\_PORTAL\_LOGGEDIN\_KEYSTART   | 1                                                                        |
| DEFAULT\_CONSUMER\_GROUP                     | contentUser                                                              |
| EMBED\_ROLE                                  | true                                                                     |
| ENDPOINTS\_HEALTH\_ID                        | apihealth                                                                |
| ENDPOINTS\_HEALTH\_SENSITIVE                 | false                                                                    |
| ENDPOINTS\_METRICS\_ID                       | metrics                                                                  |
| ENDPOINTS\_METRICS\_SENSITIVE                | false                                                                    |
| JAVA\_OPTS                                   | -Xms256m -Xmx256m                                                        |
| LEARNER\_API\_AUTH\_KEY                      | eg: key                                                                  |
| LEARNER\_BASE\_API\_URL                      | http://kong:8000                                                         |
| REFRESH\_TOKEN\_DOMAIN                       | https://staging.sunbirded.org/auth/realms/sunbird                        |
| REFRESH\_TOKEN\_KID                          | eg: token                                                                |
| REFRESH\_TOKEN\_LOG\_OLDER\_THAN             | 30                                                                       |
| REFRESH\_TOKEN\_OFFLINE\_VALIDITY            | 15552000                                                                 |
| REFRESH\_TOKEN\_PRELOAD                      | true                                                                     |
| REFRESH\_TOKEN\_PUBLIC\_BASEPATH             | /keys/                                                                   |
| REFRESH\_TOKEN\_PUBLIC\_KEYPREFIX            | refresh\_token\_public\_key                                              |
| REFRESH\_TOKEN\_SECRET\_KEY                  | eg:key                                                                   |
| SERVER\_PORT                                 | 4000                                                                     |
| SPRING\_PROFILES\_ACTIVE                     | production                                                               |
{% endtab %}
{% endtabs %}
