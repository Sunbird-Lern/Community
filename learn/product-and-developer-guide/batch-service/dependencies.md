# Dependencies

{% tabs %}
{% tab title="Sunbird Knowlg : Content service" %}
There is a dependency with Content Service to read the course metadata by using the API calls.\
\
**Dependency API:**\
/content/v3/read\
/content/v3/search\
/content/v3/hierarchy/\
/content/v3/publish\
/system/v3/content/update/\

{% endtab %}

{% tab title="Sunbird Knowlg : Search service" %}
There is a dependency with Search Service in order to perform a composite search by using the **search** API call. Search will be performed on the Elastic Search database.\
\
**Dependency API:**\
****\
****composite/v3/search\
\

{% endtab %}

{% tab title="Sunbird Inquiry" %}
There is a dependency with Inquiry for fetching the metadata of QuestionSet. There is a dependency with Content Service to read the course metadata by using the API calls.\
There is a dependency with Content Service to read the course metadata by using the API calls.\

{% endtab %}

{% tab title="Sunbird Lern : User&Org Service" %}
There is a dependency with User and Org Service to fetch user information for validating the Batch creator and Mentor (**user/v1/read**)\
\
**Dependency API:**\
****

user/v1/read
{% endtab %}

{% tab title="Druid Service" %}
There is a dependency on Druid Service  API calls.\


**Dependency API:**\
****

/druid/v2/
{% endtab %}

{% tab title="Notification Service" %}
There is a dependency with Notification Service to trigger the email notifications by using the API calls.\


**Dependency API:**\
\
/v1/notification/email
{% endtab %}

{% tab title="Certificate Registry Service" %}
There is a dependency with Certificate Registry Service to download the certificates by using the API calls.

\
**Dependency API:**\
****\
****/cert/v1/template/read
{% endtab %}
{% endtabs %}
