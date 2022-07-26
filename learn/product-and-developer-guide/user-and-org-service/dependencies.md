# Dependencies

### External Dependencies

{% tabs %}
{% tab title="Sunbird Knowlg" %}
Content service APIs to read and update channel details and to do framework validation.\
[https://github.com/project-sunbird/knowledge-platform](https://github.com/project-sunbird/knowledge-platform)\
\
**Dependency API:**\
****\
****/content/content/v1/search?orgdetails=orgName,email\
/channel/v1/read/_\{{channelid\}}_\
__/framework/v1/read/_\{{frameworkid\}}_\
/data/v1/location/search\



{% endtab %}

{% tab title="Sunbird Ed" %}
Form APIs to validate the profile information of the user.

[https://github.com/Sunbird-Ed/SunbirdEd-portal](https://github.com/Sunbird-Ed/SunbirdEd-portal/pulls)\
\
**Dependency API:**\
****\
****/device/profile/_\{{id\}}_
{% endtab %}

{% tab title="Kafka" %}
Configure Kafka setup for sending telemetry events. Sunbird Telemetry is a specification to instrument all the key events.
{% endtab %}
{% endtabs %}
