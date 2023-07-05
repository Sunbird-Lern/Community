# API Documentation

#### API Documentation:

[http://docs.sunbird.org/latest/apis/notificationapi/](http://docs.sunbird.org/latest/apis/notificationapi/)

Detailed API information present in this Reference - [API Document](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/2847178765/SB-24361+Group+Notification+Design)

**Example**:

Group Notification will use the new notification create API to create notifications as defined in the document [Notification Design Discussion](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/2632613972/SB-24321+Group+Notification+Design+Discussion).



{% swagger src="../../../.gitbook/assets/notification.yaml" path="/notification/v2/send" method="post" %}
[notification.yaml](../../../.gitbook/assets/notification.yaml)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/notification.yaml" path="/notification/v1/feed/read/{userId}" method="get" %}
[notification.yaml](../../../.gitbook/assets/notification.yaml)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/notification.yaml" path="/notification/v1/feed/update" method="patch" %}
[notification.yaml](../../../.gitbook/assets/notification.yaml)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/notification.yaml" path="/notification/v1/feed/delete" method="patch" %}
[notification.yaml](../../../.gitbook/assets/notification.yaml)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/notification.yaml" path="/notification/v1/template/create" method="post" %}
[notification.yaml](../../../.gitbook/assets/notification.yaml)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/notification.yaml" path="/notification/v1/template/update" method="patch" %}
[notification.yaml](../../../.gitbook/assets/notification.yaml)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/notification.yaml" path="/notification/v1/template/delete" method="patch" %}
[notification.yaml](../../../.gitbook/assets/notification.yaml)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/notification.yaml" path="/notification/v1/template/list" method="get" %}
[notification.yaml](../../../.gitbook/assets/notification.yaml)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/notification.yaml" path="/notification/v1/template/action/update" method="patch" %}
[notification.yaml](../../../.gitbook/assets/notification.yaml)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/notification.yaml" path="/notification/v1/template/{action}" method="get" %}
[notification.yaml](../../../.gitbook/assets/notification.yaml)
{% endswagger %}



