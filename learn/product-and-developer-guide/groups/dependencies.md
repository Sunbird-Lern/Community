# Dependencies

### Dependency Services:

{% tabs %}
{% tab title="Sunbird Lern - Notification Service" %}
Group Service connects to UserOrg Service to fetch user/member information. Any other service which has user information in a similar schema can be plugged in instead of this dependency.
{% endtab %}

{% tab title="Sunbird Lern - UserOrg Service" %}
Group Service connects to UserOrg Service to fetch user/member information. Any other service which has user information in a similar schema can be plugged in instead of this dependency.
{% endtab %}

{% tab title="Sunbird Knowledge -Content Service" %}
There is a dependency with Content Service to fetch the activities that need to be added to the group. Activity types are configurable in activityConfig.json. Other services can be plugged in here to fetch activities from different sources...
{% endtab %}
{% endtabs %}

#### References:

[User and Groups in Schooling@Home](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/1416200208/User+and+Groups+in+Schooling+Home)

[\[Design\] Groups as NPM module](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/2956099585)
