# Discussion MW & Nodebb System Config

### System Config:

{% tabs %}
{% tab title="DMW Config" %}
<table><thead><tr><th width="359.0654205607477">JSON Key</th><th>Value</th></tr></thead><tbody><tr><td>API_AUTH_TOKEN</td><td></td></tr><tr><td>TELEMETRY_EVENTS_BATCH_SIZE</td><td>1</td></tr><tr><td>TELEMETRY_SERVICE_API_SLUG</td><td>/v1/telemetry</td></tr><tr><td>TELEMETRY_SERVICE_URL</td><td><a href="http://telemetry-service:9001">http://telemetry-service:9001</a></td></tr><tr><td>authorization_token</td><td>eg: auth_token</td></tr><tr><td>enable_audit_even</td><td>true</td></tr><tr><td>moderation_flag</td><td>false</td></tr><tr><td>nodebb_api_slug</td><td>/discussion/api</td></tr><tr><td>nodebb_service_url</td><td><a href="http://nodebb-service:4567">http://nodebb-service:4567</a></td></tr></tbody></table>
{% endtab %}

{% tab title="Nodebb Config" %}


| Key                  | Value                                |
| -------------------- | ------------------------------------ |
| NODE\_OPTIONS        | 1024                                 |
| admin\_\_password    | mySuperSecretNodebbPassword          |
| admin\_\_username    | nodebb                               |
| database             | redis                                |
| isCluster            | true                                 |
| redis\_\_database    | 10                                   |
| redis\_\_host        | 11.3.2.18                            |
| redis\_\_password    | <p><br></p>                          |
| redis\_\_port        | 6379                                 |
| redis\_\_secondarydb | 11                                   |
| redis\_\_username    | <p><br></p>                          |
| secret               | 1d57ba64-86d4-43ff-bd10-f6e9e0782899 |
| url                  | http://0.0.0.0:4567/discussions/     |
{% endtab %}
{% endtabs %}
