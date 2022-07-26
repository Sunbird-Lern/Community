# Dependencies

### Dependency Services:

{% tabs %}
{% tab title="Sunbird Lern - Notification Service" %}
Group Service connects to Notification Service to fetch all the notifications for the particular user by using notification feed APIs.\
\
**Dependency API:**\
****\
****/notification/v1/feed/_\{{CRUD-operation\}}_
{% endtab %}

{% tab title="Sunbird Lern - UserOrg Service" %}
Group Service connects to UserOrg Service to fetch user/member information. Any other service which has user information in a similar schema can be plugged in instead of this dependency.\
\
**Dependency API:**\
****\
****/api/user/v5/read/\{{userId\}}\
/api/course/v1/batch/list\
/api/user/v3/search\
/api/course/v1/hierarchy/\{{content\_id\}}
{% endtab %}

{% tab title="Sunbird Knowledge -Content Service" %}
There is a dependency with Content Service to fetch the activities that need to be added to the group. Activity types are configurable in activityConfig.json. Other services can be plugged in here to fetch activities from different sources...

**Dependency API:**\
****\
****/api/content/v1/read/\{{userId\}}
{% endtab %}

{% tab title="Discussion Forum" %}
There is a  dependency with the discussion service as to get the forum is enabled for this group or not.\
\
**Dependency API:**\
****\
****/discussion/forum/v2/read
{% endtab %}
{% endtabs %}

### References:

[User and Groups in Schooling@Home](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/1416200208/User+and+Groups+in+Schooling+Home)

[\[Design\] Groups as NPM module](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/2956099585)
