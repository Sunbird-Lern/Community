---
description: API for deleted user
---

# User Deletion API

### Overview

The User Deletion API allows authorized users to delete a user from the system. This API requires the user ID of the user to be deleted and is accessible via an HTTP POST request.

### Delete a new user

<mark style="color:green;">`POST`</mark> /api/user/v1/delete

### **Headers**

| Name                                                         | Value                     |
| ------------------------------------------------------------ | ------------------------- |
| Content-Type<mark style="color:red;">\*</mark>               | `application/json`        |
| Authorization<mark style="color:red;">\*</mark>              | `Bearer <token>`          |
| X-Authenticated-User-token<mark style="color:red;">\*</mark> | `<keycloak-access-token>` |

### Body

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

### **Response**

{% tabs %}
{% tab title="200" %}
```json
{
    "id": "api.user.delete",
    "ver": "v1",
    "ts": "2024-05-20 10:08:56:812+0000",
    "params": {
        "resmsgid": "e413d019f31bcb2d3736b7054f1fd6e2",
        "msgid": "e413d019f31bcb2d3736b7054f1fd6e2",
        "err": null,
        "status": "SUCCESS",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "response": "SUCCESS"
    }
}
```
{% endtab %}

{% tab title="400" %}
```json
{
    "id": "api.user.delete",
    "ver": "v1",
    "ts": "2024-05-20 10:09:45:837+0000",
    "params": {
        "resmsgid": "4abb4c0bdd99feea7a7070eeade15aaa",
        "msgid": "4abb4c0bdd99feea7a7070eeade15aaa",
        "err": "UOS_USRDLT0008",
        "status": "FAILED",
        "errmsg": "User is already deleted."
    },
    "responseCode": "CLIENT_ERROR",
    "result": {}
}
```
{% endtab %}

{% tab title="403" %}
```json
You do not have permission to perform this operation
```
{% endtab %}
{% endtabs %}
