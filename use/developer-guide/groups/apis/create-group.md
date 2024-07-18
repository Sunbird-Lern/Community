# Create Group



## Create a new group

<mark style="color:green;">`POST`</mark> `/group/v1/create`

This API is used to create a group&#x20;

* The endpoint for **Create Group** is `/group/v1/create`
* The fields marked with an asterisk (\*) are mandatory. They cannot be null or empty.

**Headers**

| Name                                                         | Value                     |
| ------------------------------------------------------------ | ------------------------- |
| Content-Type<mark style="color:red;">\*</mark>               | `application/json`        |
| Authorization<mark style="color:red;">\*</mark>              | `Bearer <token>`          |
| X-Authenticated-User-token<mark style="color:red;">\*</mark> | `<keycloak-access-token>` |

**Body**

{% tabs %}
{% tab title="Example" %}
```json
{
    "request": {
        "userId": "user id to be deleted"
    }
}
```
{% endtab %}

{% tab title="Schema" %}
| Name                                     | Type   | Description                        |
| ---------------------------------------- | ------ | ---------------------------------- |
| userId<mark style="color:red;">\*</mark> | string | User id  of the user to be deleted |
{% endtab %}
{% endtabs %}

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
  "id": "api.group.create",
  "ver": "v1",
  "ts": "2020-12-01 20:52:25:226+0000",
  "params": null,
  "result": {
    "groupId": "682473c2-12ba-4a89-b8db-67c2c65ca97a"
  },
  "responseCode": 200
}
```
{% endtab %}

{% tab title="400" %}
```json
{
  "id": "api.group.create",
  "ver": null,
  "ts": "2020-12-02 11:09:52:748+0530",
  "params": {
    "resmsgid": null,
    "msgid": "6da747d8-c19f-40cb-9938-fcf0913e301f",
    "err": "GS_CRT02",
    "status": "failed",
    "errmsg": "Failed to create group, fields are missing in the request. Enter the required values and resend the request."
  },
  "result": {},
  "responseCode": 400
}
```
{% endtab %}

{% tab title="401" %}
```json
{
  "id": "api.group.create",
  "ver": null,
  "ts": "2020-12-02 05:53:25:361+0000",
  "params": {
    "resmsgid": null,
    "msgid": "f5e58ea069e93de16e721d0312a195dc",
    "err": "GS_UNAUTHORIZED",
    "status": "failed",
    "errmsg": "You are an unauthorized.Contact your system administrator"
  },
  "result": {},
  "responseCode": 401
}
```
{% endtab %}

{% tab title="500" %}

{% endtab %}
{% endtabs %}
