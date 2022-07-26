# Functional Configurations

{% tabs %}
{% tab title="Functional Config" %}
| Property                     | Description                                                        | Default Value |
| ---------------------------- | ------------------------------------------------------------------ | ------------- |
| max\_group\_limit            | Maximum number of groups a user can create                         | 50            |
| max\_group\_members\_limit   | Maximum number of members a group can have                         | 150           |
| max\_activity\_limit         | Maximum number of activities a group can have                      | 20            |
| enable\_userid\_redis\_cache | To enable cache for groups and group details                       | true          |
| groups\_redis\_ttl           | Group details cache duration                                       | 86400         |
| user\_redis\_ttl             | User group list cache duration                                     | 3600          |
| activityConfig               | To configure various types of activities and services to fetch it. |               |


{% endtab %}

{% tab title="System Config" %}
| JSON Key                               | Key                                                            | Default Value                                                              |
| -------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------------------- |
| SUNBIRD\_CS\_BASE\_URL                 | CONTENT\_SERVICE\_PORT                                         | [http://search-service:9000](http://search-service:9000)                   |
| USER\_SERVICE\_BASE\_URL               | LEARNER\_SERVICE\_PORT                                         | [http://learner-service:9000](http://learner-service:9000)                 |
| ACCESS\_TOKEN\_PUBLICKEY\_BASEPATH     | accesstoken.publickey.basepath                                 | /keys/                                                                     |
| ENABLE\_TENANT\_CONFIGURATION          | enable\_tenant\_config                                         | \*                                                                         |
| ENABLE\_USERID\_REDIS\_CACHE           | enable\_userid\_redis\_cache                                   | true                                                                       |
| GROUPS\_REDIS\_TTL                     | groups\_redis\_ttl                                             | 864004                                                                     |
| MAX\_ACTIVITY\_LIMIT                   | max\_activity\_limi                                            | 20                                                                         |
| MAX\_GROUP\_LIMIT                      | max\_group\_limit                                              | 50                                                                         |
| MAX\_GROUP\_MEMBERS\_LIMIT             | max\_group\_members\_limit                                     | 150                                                                        |
| NOTIFICATION\_SERVICE\_API\_URL        | notification\_service\_api\_url                                | /v2/notification/send                                                      |
| NOTIFICATION\_SERVICE\_BASE\_URL       | notification\_service\_base\_url                               | [http://notification-service:9000](http://notification-service:9000)       |
| SUNBIRD\_CASSANDRA\_CONSISTENCY\_LEVEL | sunbird\_cassandra\_consistency\_level                         | quorum                                                                     |
| SUNBIRD\_CASSANDRA\_IP                 | sunbird\_cassandra\_host                                       | 11.3.2.4,11.3.2.5,11.3.2.6                                                 |
|                                        | sunbird\_cassandra\_password                                   | password                                                                   |
|                                        | sunbird\_cassandra\_port                                       | 9042,9042,9042                                                             |
|                                        | sunbird\_cassandra\_username                                   | cassandra                                                                  |
| SUNBIRD\_CS\_SEARCH\_URL               | sunbird\_cs\_search\_url                                       | /v3/search                                                                 |
|                                        | sunbird\_keycloak\_required\_action\_link\_expiration\_seconds | 2592000                                                                    |
|                                        | sunbird\_keycloak\_user\_federation\_provider\_id              | provider id                                                                |
|                                        | sunbird\_redis\_host                                           | 11.3.2.18                                                                  |
|                                        | sunbird\_redis\_port                                           | 6379                                                                       |
|                                        | sunbird\_sso\_client\_id                                       | eg: id                                                                     |
|                                        | sunbird\_sso\_client\_secret                                   | eg: id                                                                     |
|                                        | sunbird\_sso\_password                                         | eg: passowrd                                                               |
|                                        | sunbird\_sso\_publickey                                        | eg: encrypted public key                                                   |
| SUNBIRD\_SSO\_REALM                    | sunbird\_sso\_realm                                            | sunbird                                                                    |
| SUNBIRD\_SSO\_URL                      | sunbird\_sso\_url                                              | [https://staging.sunbirded.org/auth/](https://staging.sunbirded.org/auth/) |
|                                        | sunbird\_sso\_username                                         | sunbird-staging-new-admin                                                  |
| USER\_SERVICE\_SEARCH\_URL             | sunbird\_user\_service\_search\_url                            | /private/api/user/v1/search                                                |
| USER\_REDIS\_TTL                       | user\_redis\_ttl                                               | 3600                                                                       |


{% endtab %}
{% endtabs %}
