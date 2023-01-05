# API Management Service

The API management microservice provides services to create, manage and validate API tokens to register mobile and desktop apps, and to issue and refresh API tokens of registered mobile and desktop app devices.

{% swagger src="../../../../.gitbook/assets/kongcredentialregisterapiv1.yml" path="/api-manager/v1/consumer/{consumer}/credential/register" method="post" %}
[kongcredentialregisterapiv1.yml](../../../../.gitbook/assets/kongcredentialregisterapiv1.yml)
{% endswagger %}

{% swagger src="../../../../.gitbook/assets/kongcredentialregisterapiv2.yml" path="/api-manager/v2/consumer/{consumer}/credential/register" method="post" %}
[kongcredentialregisterapiv2.yml](../../../../.gitbook/assets/kongcredentialregisterapiv2.yml)
{% endswagger %}

{% swagger src="../../../../.gitbook/assets/refreshtokenapi.yml" path="/auth/v1/refresh/token" method="post" %}
[refreshtokenapi.yml](../../../../.gitbook/assets/refreshtokenapi.yml)
{% endswagger %}

{% swagger src="../../../../.gitbook/assets/deviceregistry.yaml" path="/api-manager/v2/consumer/desktop_device/credential/register" method="post" %}
[deviceregistry.yaml](../../../../.gitbook/assets/deviceregistry.yaml)
{% endswagger %}
