# Dependencies

{% tabs %}
{% tab title="Sunbird Knowlg : Content service" %}
There is a dependency with Content Service to read the course metadata by using the **content/v1/read** API call
{% endtab %}

{% tab title="Sunbird Knowlg : Search service" %}
There is a dependency with Search Service in order to perform composite search by using the **composite/v3/search** API call. Search will be performed on the Elastic Search database
{% endtab %}

{% tab title="Sunbird Inquiry" %}
There is a dependency with Inquiry for fetching the metadata of QuestionSet.
{% endtab %}

{% tab title="Sunbird Lern : User&Org Service" %}
There is a dependency with User and Org Service to fetch user information for validating the Batch creator and Mentor (**user/v1/read**)
{% endtab %}
{% endtabs %}
