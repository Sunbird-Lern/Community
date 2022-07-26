# System Configurations



{% tabs %}
{% tab title="LMS-Batch Service Config " %}


| JSON Key                                             | Key                                                            | Value                                                                         |
| ---------------------------------------------------- | -------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| ACCESS\_TOKEN\_PUBLICKEY\_BASEPATH                   | accesstoken.publickey.basepath                                 |  /keys/                                                                       |
| API\_ACTOR\_PROVIDER                                 | api\_actor\_provider                                           | local                                                                         |
| BACKGROUND\_ACTOR\_PROVIDER                          | background\_actor\_provider                                    | local                                                                         |
| <p><br></p>                                          | collection\_summary\_agg\_cache\_ttl                           | 21600                                                                         |
| <p><br></p>                                          | collection\_summary\_agg\_data\_source                         | audit-rollup-syncts                                                           |
| <p><br></p>                                          | druid\_proxy\_api\_endpoint                                    | /druid/v2/                                                                    |
| <p><br></p>                                          | druid\_proxy\_api\_host                                        | 11.3.2.25                                                                     |
| <p><br></p>                                          | druid\_proxy\_api\_port                                        | 8082                                                                          |
| EKSTEP\_BASE\_URL                                    | ekstep\_api\_base\_url                                         | http://content-service:9000                                                   |
| EKSTEP\_AUTHORIZATION                                | ekstep\_authorization                                          | eg: key                                                                       |
| <p><br></p>                                          | enrollment\_list\_size                                         | 1000                                                                          |
| <p><br></p>                                          | group\_activity\_agg\_cache\_enable                            | False                                                                         |
| <p><br></p>                                          | group\_activity\_agg\_cache\_ttl                               | 3600                                                                          |
| <p><br></p>                                          | kafka\_assessment\_topic                                       | sunbirdstaging.telemetry.assess                                               |
| <p><br></p>                                          | kafka\_enrolment\_sync\_topic                                  | sunbirdstaging.batch.enrolment.sync.request                                   |
| <p><br></p>                                          | kafka\_topics\_certificate\_instruction                        | sunbirdstaging.issue.certificate.request                                      |
| <p><br></p>                                          | kafka\_topics\_contentstate\_invalid                           | sunbirdstaging.contentstate.invalid                                           |
| <p><br></p>                                          | kafka\_topics\_instruction                                     | sunbirdstaging.coursebatch.job.request                                        |
| <p><br></p>                                          | kafka\_urls                                                    | 11.3.2.16:9092,11.3.2.15:9092,11.3.2.14:9092                                  |
| CONTENT\_PROPS\_TO\_ADD                              | learning.content.props.to.add                                  | mimeType,contentType,name,code,description,keywords,framework,copyright,topic |
| LEARNING\_SERVICE\_BASE\_URL                         | learning\_service\_base\_url                                   | http://11.3.3.22:8080/learning-service                                        |
| <p><br></p>                                          | redis.connection.idle.max                                      | 32                                                                            |
| <p><br></p>                                          | redis.connection.idle.min                                      | 1                                                                             |
| <p><br></p>                                          | redis.connection.max                                           | 64                                                                            |
| <p><br></p>                                          | redis.connection.minEvictableIdleTimeSeconds                   | 120                                                                           |
| <p><br></p>                                          | redis.connection.timeBetweenEvictionRunsSeconds                | 300                                                                           |
| <p><br></p>                                          | redis.dbIndex                                                  | 2                                                                             |
| <p><br></p>                                          | redis.experimentIndex                                          | 10                                                                            |
| ACCOUNT\_KEY                                         | sunbird\_account\_key                                          | eg: key                                                                       |
| ACCOUNT\_NAME                                        | sunbird\_account\_name                                         | sunbirdstagingpublic                                                          |
| ANALYTICS\_API\_BASE\_URL                            | sunbird\_analytics\_api\_base\_url                             | http://analytics-service.staging.svc.cluster.local:9000                       |
| ANALYTICS\_ACCOUNT\_KEY                              | sunbird\_analytics\_blob\_account\_key                         | eg: account\_key                                                              |
| <p>ANALYTICS_ACCOUNT_NAME<br></p>                    | sunbird\_analytics\_blob\_account\_name                        | eg: private\_name                                                             |
| SUNBIRD\_API\_BASE\_URL                              | sunbird\_api\_base\_url                                        | http://knowledge-mw-service:5000                                              |
| SUNBIRD\_API\_MGR\_BASE\_URL                         | sunbird\_api\_mgr\_base\_url                                   | http://knowledge-mw-service:5000                                              |
| SUNBIRD\_APP\_NAME                                   | sunbird\_app\_name                                             | Sunbird                                                                       |
| SUNBIRD\_AUTHORIZATION                               | sunbird\_authorization                                         | eg: key                                                                       |
| <p><br></p>                                          | sunbird\_badger\_baseurl                                       | http://badger-service:8004                                                    |
| SUNBIRD\_CACHE\_ENABLE                               | sunbird\_cache\_enable                                         | True                                                                          |
| SUNBIRD\_CASSANDRA\_CONSISTENCY\_LEVEL               | sunbird\_cassandra\_consistency\_level                         | quorum                                                                        |
| SUNBIRD\_CASSANDRA\_IP                               | sunbird\_cassandra\_host                                       | 11.3.2.4,11.3.2.5,11.3.2.6                                                    |
| SUNBIRD\_CASSANDRA\_PASSWORD                         | sunbird\_cassandra\_password                                   | Eg: password                                                                  |
| SUNBIRD\_CASSANDRA\_PORT                             | sunbird\_cassandra\_port                                       | 9042,9042,9042                                                                |
| SUNBIRD\_CASSANDRA\_USER\_NAME                       | sunbird\_cassandra\_username                                   | cassandra                                                                     |
| SUNBIRD\_CERT\_SERVICE\_BASE\_URL                    | sunbird\_cert\_service\_base\_url                              | http://cert-service:9000                                                      |
| CONTENT\_AZURE\_STORAGE\_CONTAINER                   | sunbird\_content\_azure\_storage\_container                    | sunbird-content-staging                                                       |
| SUNBIRD\_COURSE\_BATCH\_NOTIFICATIONS\_ENABLED       | sunbird\_course\_batch\_notification\_enabled                  | true                                                                          |
| SUNBIRD\_COURSE\_BATCH\_NOTIFICATION\_SIGNATURE      | sunbird\_course\_batch\_notification\_signature                | <p><br></p>                                                                   |
| SUNBIRD\_CS\_BASE\_URL                               | sunbird\_cs\_base\_url                                         | http://knowledge-mw-service:5000                                              |
| SUNBIRD\_CS\_SEARCH\_PATH                            | sunbird\_cs\_search\_path                                      | /v1/search                                                                    |
| SUNBIRD\_DEFAULT\_CHANNEL                            | sunbird\_default\_channel                                      | ntp                                                                           |
| SUNBIRD\_EMAIL\_MAX\_RECEPIENT\_LIMIT                | sunbird\_email\_max\_recipients\_limit                         | 100                                                                           |
| ENCRYPTION\_KEY                                      | sunbird\_encryption\_key                                       | eg: key                                                                       |
| <p><br></p>                                          | sunbird\_encryption\_mode                                      | local                                                                         |
| SUNBIRD\_ENV\_LOGO\_URL                              | sunbird\_env\_logo\_url                                        | https://staging.sunbirded.org/tenant/ntp/logo.png                             |
| <p><br></p>                                          | sunbird\_environment                                           | staging                                                                       |
| SUNBIRD\_ES\_IP                                      | sunbird\_es\_host                                              | 11.3.2.8                                                                      |
| SUNBIRD\_ES\_PORT                                    | sunbird\_es\_port                                              | 9300                                                                          |
| GROUP\_SERVICE\_API\_BASE\_URL                       | sunbird\_group\_service\_api\_base\_url                        | http://groups-service:9000                                                    |
| SUNBIRD\_GZIP\_ENABLE                                | sunbird\_gzip\_enable                                          | True                                                                          |
| SUNBIRD\_GZIP\_SIZE\_THRESHOLD                       | sunbird\_gzip\_size\_threshold                                 | 262144                                                                        |
| SUNBIRD\_HEALTH\_CHECK\_ENABLE                       | sunbird\_health\_check\_enable                                 | false                                                                         |
| SUNBIRD\_INSTALLATION                                | sunbird\_installation                                          | Sunbird\_Stage                                                                |
| SUNBIRD\_INSTALLATION\_DISPLAY\_NAME                 | sunbird\_installation\_display\_name                           | SUNBIRDSTAGE                                                                  |
|                                                      | sunbird\_installation\_email                                   | dummy@dummy.org                                                               |
| <p>SUNBIRD_KEYCLOAK_LINK_EXPIRATION_TIME<br></p>     | sunbird\_keycloak\_required\_action\_link\_expiration\_seconds | 2592000                                                                       |
| SUNBIRD\_KEYCLOAK\_USER\_FEDERATION\_PROVIDER\_ID    | sunbird\_keycloak\_user\_federation\_provider\_id              | eg: user\_id                                                                  |
| EMAIL\_SERVER\_FROM                                  | sunbird\_mail\_server\_from\_email                             | support@staging.sunbirded.org                                                 |
| EMAIL\_SERVER\_HOST                                  | sunbird\_mail\_server\_host                                    | smtp.sendgrid.net                                                             |
| EMAIL\_SERVER\_PASSWORD                              | sunbird\_mail\_server\_password                                | eg: password                                                                  |
| EMAIL\_SERVER\_PORT                                  | sunbird\_mail\_server\_port                                    | 587                                                                           |
| EMAIL\_SERVER\_USERNAME                              | sunbird\_mail\_server\_username                                | apikey                                                                        |
| <p><br></p>                                          | sunbird\_msg\_91\_auth                                         | eg: key                                                                       |
| <p><br></p>                                          | sunbird\_msg\_sender                                           | DKSAPP                                                                        |
| MW\_SYSTEM\_HOST                                     | sunbird\_mw\_system\_host                                      | lms-service                                                                   |
| MW\_SYSTEM\_PORT                                     | sunbird\_mw\_system\_port                                      | 8088                                                                          |
| SUNBIRD\_OPENSABER\_BRIDGE\_ENABLE                   | sunbird\_open\_saber\_bridge\_enable                           | false                                                                         |
| SUNBIRD\_OTP\_EXPIRATION                             | sunbird\_otp\_expiration                                       | 1800                                                                          |
| SUNBIRD\_OTP\_LENGTH                                 | sunbird\_otp\_length                                           | 6                                                                             |
| SUNBIRD\_PG\_DB                                      | sunbird\_pg\_db                                                | quartz                                                                        |
| SUNBIRD\_PG\_HOST                                    | sunbird\_pg\_host                                              | staging-pg11.postgres.database.azure.com                                      |
| SUNBIRD\_PG\_PASSWORD                                | sunbird\_pg\_password                                          | eg: password                                                                  |
| SUNBIRD\_PG\_PORT                                    | sunbird\_pg\_port                                              | 5432                                                                          |
| SUNBIRD\_PG\_USER                                    | sunbird\_pg\_user                                              | sunbirdstaging@staging-pg11                                                   |
| SUNBIRD\_QUARTZ\_MODE                                | sunbird\_quartz\_mode                                          | cluster                                                                       |
| <p><br></p>                                          | sunbird\_redis\_host                                           | 11.3.2.18                                                                     |
| <p><br></p>                                          | sunbird\_redis\_port                                           | 6379                                                                          |
| <p><br></p>                                          | sunbird\_remote\_bg\_req\_router\_path                         | akka.tcp://SunbirdMWSystem@actor-service:8088/user/BackgroundRequestRouter    |
| <p><br></p>                                          | sunbird\_remote\_req\_router\_path                             | akka.tcp://SunbirdMWSystem@actor-service:8088/user/RequestRouter              |
| SEARCH\_SERVICE\_API\_BASE\_URL                      | sunbird\_search\_service\_api\_base\_url                       | http://search-service:9000                                                    |
| SUNBIRD\_SSO\_CLIENT\_ID                             | sunbird\_sso\_client\_id                                       | lms                                                                           |
| SUNBIRD\_SSO\_CLIENT\_SECRET                         | sunbird\_sso\_client\_secret                                   | eg: id                                                                        |
| SUNBIRD\_SSO\_PASSWORD                               | sunbird\_sso\_password                                         | eg: password                                                                  |
| SSO\_PUBLIC\_KEY                                     | sunbird\_sso\_publickey                                        | eg: key                                                                       |
| SUNBIRD\_SSO\_RELAM                                  | sunbird\_sso\_realm                                            | sunbird                                                                       |
| SUNBIRD\_SSO\_URL                                    | sunbird\_sso\_url                                              | https://staging.sunbirded.org/auth/                                           |
| SUNBIRD\_SSO\_USERNAME                               | sunbird\_sso\_username                                         | sunbird-staging-new-admin                                                     |
| SUNBIRD\_TELEMETRY\_BASE\_URL                        | sunbird\_telemetry\_base\_url                                  | http://telemetry-service:9001                                                 |
| SUNBIRD\_TIMEZONE                                    | sunbird\_time\_zone                                            | Asia/Kolkata                                                                  |
| <p><br></p>                                          | sunbird\_url\_shortner\_access\_token                          | Eg:key                                                                        |
| SUNBIRD\_URL\_SHORTNER\_ENABLE                       | sunbird\_url\_shortner\_enable                                 | True                                                                          |
| BULK\_UPLOAD\_USER\_DATA\_SIZE                       | sunbird\_user\_bulk\_upload\_size                              | 1001                                                                          |
| SUNBIRD\_USER\_ORG\_API\_BASE\_URL                   | sunbird\_user\_org\_api\_base\_url                             | http://learner-service.staging.svc.cluster.local:9000                         |
| SUNBIRD\_USER\_PROFILE\_FIELD\_DEFAULT\_VISIBILITY = | sunbird\_user\_profile\_field\_default\_visibility             | private                                                                       |
| SUNBIRD\_QRCODE\_COURSES\_LIMIT                      | sunbird\_user\_qrcode\_courses\_limit                          | 5000                                                                          |
| CREATOR\_DETAILS\_FIELDS                             | sunbird\_user\_search\_cretordetails\_fields                   | id,firstName,lastName                                                         |
| USER\_SEARCH\_BASE\_URL                              | sunbird\_user\_service\_api\_base\_url                         | http://learner-service.staging.svc.cluster.local:9000                         |
| SUNBIRD\_WEB\_URL                                    | sunbird\_web\_url                                              | https://staging.sunbirded.org                                                 |
| PDATA\_ID                                            | telemetry\_pdata\_id                                           | staging.sunbird.learning.service                                              |
| PDATA\_PID                                           | telemetry\_pdata\_pid                                          | lms-service                                                                   |
| TELEMETRY\_QUEUE\_THRESHOLD\_VALUE                   | telemetry\_queue\_threshold\_value                             | 100                                                                           |
| <p><br></p>                                          | user\_enrolments\_response\_cache\_enable                      | True                                                                          |
| <p><br></p>                                          | user\_enrolments\_response\_cache\_ttl                         | 300                                                                           |
{% endtab %}

{% tab title="Cert-Registery Config" %}


| JSON Key                                 | Key                                      | Value                        |
| ---------------------------------------- | ---------------------------------------- | ---------------------------- |
| CERT\_SERVICE\_BASE\_URL                 | cert\_service\_base\_url                 | http://cert-service:9000     |
| RC\_ENTITY                               | rc\_entity                               | TrainingCertificate          |
| REGISTRY\_CREDENTIAL\_SERVICE\_BASE\_URL | registry\_credential\_service\_base\_url | http://registry-service:8081 |
| SUNBIRD\_CASSANDRA\_CONSISTENCY\_LEVEL   | sunbird\_cassandra\_consistency\_level   | quorum                       |
| SUNBIRD\_CASSANDRA\_IP                   | sunbird\_cassandra\_host                 | 11.3.2.4,11.3.2.5,11.3.2.6   |
| SUNBIRD\_CASSANDRA\_PASSWORD             | sunbird\_cassandra\_password             | password                     |
| SUNBIRD\_CASSANDRA\_PORT                 | sunbird\_cassandra\_port                 | 9042                         |
| SUNBIRD\_CASSANDRA\_USER\_NAME           | sunbird\_cassandra\_username             | cassandra                    |
| SUNBIRD\_ES\_IP                          | sunbird\_es\_host                        | 11.3.2.8                     |
| SUNBIRD\_ES\_PORT                        | sunbird\_es\_port                        | 9300                         |
{% endtab %}

{% tab title="Registry Batch Service Config" %}


| JSON Key    | Key                                | Value                                                                    |
| ----------- | ---------------------------------- | ------------------------------------------------------------------------ |
| <p><br></p> | auditTaskExecutor\_queueCapacity   | 100                                                                      |
| <p><br></p> | connectionInfo\_maxPoolSize        | 200                                                                      |
| <p><br></p> | connectionInfo\_password           | XrL59KdMXM                                                               |
| <p><br></p> | connectionInfo\_uri                | jdbc:postgresql://staging-pg11.postgres.database.azure.com:5432/registry |
| <p><br></p> | connectionInfo\_username           | sunbirdstaging@staging-pg11                                              |
| <p><br></p> | elastic\_search\_connection\_url   | 11.3.2.8:9200,11.3.2.9:9200,11.3.2.10:9200                               |
| <p><br></p> | elastic\_search\_enabled           | true                                                                     |
| <p><br></p> | enable\_external\_templates        | true                                                                     |
| <p><br></p> | pdf\_url                           | http://certificateapi-service:8078/api/v1/certificatePDF                 |
| <p><br></p> | search\_provider                   | dev.sunbirdrc.registry.service.ElasticSearchService                      |
| <p><br></p> | search\_providerName               | dev.sunbirdrc.registry.service.ElasticSearchService                      |
| <p><br></p> | sign\_url                          | http://certificatesign-service:8079/sign                                 |
| <p><br></p> | c                                  | true                                                                     |
| <p><br></p> | taskExecutor\_index\_queueCapacity | 100                                                                      |
| <p><br></p> | template\_base\_url                | http://registry-service:8081/api/v1/templates/                           |
| <p><br></p> | workflow.enable                    | false                                                                    |
{% endtab %}

{% tab title="Certificate Sign Config" %}


| JSON Key         | Key                      | Value          |
| ---------------- | ------------------------ | -------------- |
| PUBLIC\_KEY\_URL | CERTIFICATE\_PUBLIC\_KEY | eg:public\_key |
{% endtab %}

{% tab title="CertificateAPIConfig" %}


| JSON Key         | Key                      | Default Value                 |
| ---------------- | ------------------------ | ----------------------------- |
| DOMAIN\_URL      | CERTIFICATE\_DOMAIN\_URL | https://staging.sunbirded.org |
| PUBLIC\_KEY\_URL | CERTIFICATE\_PUBLIC\_KEY | <p><br></p>                   |
{% endtab %}

{% tab title="Certificate Config" %}


| JSON Key                        | Key                              | Value                                      |
| ------------------------------- | -------------------------------- | ------------------------------------------ |
| AZURE\_STORAGE\_KEY             | AZURE\_STORAGE\_KEY              | sunbirdstagingprivate                      |
| AZURE\_STORAGE\_SECRET          | AZURE\_STORAGE\_SECRET           | eg: secret\_key                            |
| CLOUD\_STORAGE\_TYPE            | CLOUD\_STORAGE\_TYPE             | azure                                      |
| CONTAINER\_NAME                 | CONTAINER\_NAME                  | sunbird-staging-e-credentials              |
| PUBLIC\_AZURE\_STORAGE\_KEY     | PUBLIC\_AZURE\_STORAGE\_KEY      | sunbirdstagingpublic                       |
| PUBLIC\_AZURE\_STORAGE\_SECRET  | PUBLIC\_AZURE\_STORAGE\_SECRET   | eg: secret\_key                            |
| PUBLIC\_CONTAINER\_NAME         | PUBLIC\_CONTAINER\_NAME          | certqr                                     |
| DOWNLOAD\_LINK\_EXPIRY\_TIMEOUT | download\_link\_expiry\_timeout  | 600                                        |
| es\_conn\_info                  | es\_conn\_info                   | 11.3.2.9:9200,11.3.2.8:9200,11.3.2.10:9200 |
| DOMAIN\_URL                     | sunbird\_cert\_domain\_url       | https://staging.sunbirded.org              |
| ENC\_SERVICE\_URL               | sunbird\_cert\_enc\_service\_url | http://enc-service:8013                    |


{% endtab %}
{% endtabs %}
