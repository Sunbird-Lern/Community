---
description: API for ownership transfer
---

# Ownership Transfer API

### Overview

The Ownership Transfer API allows authorized users to transfer ownership of roles and assets from one user to another within an organization.

### Delete a new user

<mark style="color:green;">`POST`</mark> /api/user/v1/ownership/transfer

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
        "context": "User Deletion",
        "organisationId": "organisation-id-of-deleted-user",
        "actionBy": {
            "userId": "org-admin-user-id"
        },
        "fromUser": {
            "userId": "deleted-user-id",
            "roles": [
                {
                    "role": "role-1",
                    "scope": [
                        {
                            "organisationId": "organisation-id-of-role-1"
                        }
                    ]
                },
                {
                    "role": "role-2",
                    "scope": [
                        {
                            "organisationId": "organisation-id-of-role-2"
                        }
                    ]
                }
            ]
        },
        "toUser": {
            "userId": "new-user-id",
            "roles": [
                {
                    "role": "role-1",
                    "scope": [
                        {
                            "organisationId": "organisation-id-of-role-1"
                        }
                    ]
                },
                {
                    "role": "role-2",
                    "scope": [
                        {
                            "organisationId": "organisation-id-of-role-2"
                        }
                    ]
                }
            ]
        },
        "objects": [{
            "objectType": "asset-object-type",
            "identifier": "asset-identifier",
            "primaryCategory": "asset-category",
            "name": "asset-name"
        }]
    }
}
```
{% endtab %}

{% tab title="Schema" %}
#### Parameters

<table><thead><tr><th width="336">Parameter</th><th width="84">Type</th><th width="60">Required</th><th>Description</th></tr></thead><tbody><tr><td>context</td><td>string</td><td>Yes</td><td>The context of the transfer, typically "User Deletion".</td></tr><tr><td>organisationId<mark style="color:red;">*</mark></td><td>string</td><td>Yes</td><td>The ID of the organization associated with the deleted user.</td></tr><tr><td>actionBy.userId<mark style="color:red;">*</mark></td><td>string</td><td>Yes</td><td>The ID of the organization admin performing the transfer.</td></tr><tr><td>fromUser.userId<mark style="color:red;">*</mark></td><td>string</td><td>Yes</td><td>The ID of the deleted user.</td></tr><tr><td>fromUser.roles<mark style="color:red;">*</mark></td><td>array</td><td>Yes</td><td>The roles to be transferred.</td></tr><tr><td>fromUser.roles[].role</td><td>string</td><td>Yes</td><td>The role name.</td></tr><tr><td>fromUser.roles[].scope</td><td>array</td><td>Yes</td><td>The scope of the role.</td></tr><tr><td>fromUser.roles[].scope[].organisationId</td><td>string</td><td>Yes</td><td>The ID of the organization associated with the role.</td></tr><tr><td>toUser.userId<mark style="color:red;">*</mark></td><td>string</td><td>Yes</td><td>The ID of the user receiving the ownership transfer.</td></tr><tr><td>toUser.roles<mark style="color:red;">*</mark></td><td>array</td><td>Yes</td><td>The roles being transferred.</td></tr><tr><td>toUser.roles[].role</td><td>string</td><td>Yes</td><td>The role name.</td></tr><tr><td>toUser.roles[].scope</td><td>array</td><td>Yes</td><td>The scope of the role.</td></tr><tr><td>toUser.roles[].scope[].organisationId</td><td>string</td><td>Yes</td><td>The ID of the organization associated with the role.</td></tr><tr><td>objects</td><td>array</td><td>Yes</td><td>The assets to be transferred.</td></tr><tr><td>objects[].objectType</td><td>string</td><td>Yes</td><td>The type of the asset.</td></tr><tr><td>objects[].identifier</td><td>string</td><td>Yes</td><td>The identifier of the asset.</td></tr><tr><td>objects[].primaryCategory</td><td>string</td><td>Yes</td><td>The category of the asset.</td></tr><tr><td>objects[].name</td><td>string</td><td>Yes</td><td>The name of the asset.</td></tr></tbody></table>
{% endtab %}
{% endtabs %}

### **Response**

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
    "id": "api.user.ownership.transfer",
    "ver": "v1",
    "ts": "2024-05-20 10:36:04:695+0000",
    "params": {
        "resmsgid": "b681b51992d3833bd500323585629b33",
        "msgid": "b681b51992d3833bd500323585629b33",
        "err": null,
        "status": "SUCCESS",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "status": "Ownership transfer process is submitted successfully!"
    }
}
```
{% endtab %}

{% tab title="400" %}
```json
{
    "id": "api.user.ownership.transfer",
    "ver": "v1",
    "ts": "2024-05-20 10:36:21:087+0000",
    "params": {
        "resmsgid": "92e62ce028dc5912e88edd8ef43c9a3b",
        "msgid": "92e62ce028dc5912e88edd8ef43c9a3b",
        "err": "UOS_UOWNTRANS0028",
        "status": "FAILED",
        "errmsg": "Organization ID is mandatory in the request."
    },
    "responseCode": "CLIENT_ERROR",
    "result": {}
}
```
{% endtab %}

{% tab title="401" %}
```json
{
    "id": "api.user.ownership.transfer",
    "ver": "v1",
    "ts": "2024-05-20 10:37:12:052+0000",
    "params": {
        "resmsgid": "0f5d442e3e19232cf5176cb2b8ee63a9",
        "msgid": "0f5d442e3e19232cf5176cb2b8ee63a9",
        "err": "UOS_0070",
        "status": "FAILED",
        "errmsg": "You are not authorized."
    },
    "responseCode": "UNAUTHORIZED",
    "result": {}
}
```
{% endtab %}
{% endtabs %}
