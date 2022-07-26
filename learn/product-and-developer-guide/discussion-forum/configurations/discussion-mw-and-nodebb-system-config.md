# Discussion MW & Nodebb System Config

### System Config:

{% tabs %}
{% tab title="DMW Config" %}
| JSON Key                       | Value                                                          |
| ------------------------------ | -------------------------------------------------------------- |
| API\_AUTH\_TOKEN               |                                                                |
| TELEMETRY\_EVENTS\_BATCH\_SIZE | 1                                                              |
| TELEMETRY\_SERVICE\_API\_SLUG  | /v1/telemetry                                                  |
| TELEMETRY\_SERVICE\_URL        | [http://telemetry-service:9001](http://telemetry-service:9001) |
| authorization\_token           | eg: auth\_token                                                |
| enable\_audit\_even            | true                                                           |
| moderation\_flag               | false                                                          |
| nodebb\_api\_slug              | /discussion/api                                                |
| nodebb\_service\_url           | [http://nodebb-service:4567](http://nodebb-service:4567)       |
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
