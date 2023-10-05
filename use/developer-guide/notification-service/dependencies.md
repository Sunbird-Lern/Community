# Dependencies

{% tabs %}
{% tab title="Sunbird Lern - UserOrg Service" %}
Notification Service has dependency to UserOrg service. It fetches the custodian org id from UserOrg using system settings API. This custodian org id is added to the channel value and then to request context. This in turn gets injected into telemetry data and logs.

**Dependency API:**

[/api/data/v1/system/settings/list\
](http://docs.sunbird.org/latest/apis/systemsettingsapi/#operation/list)API Method: **GET**

<details>

<summary>Sample Response Payload</summary>

```json
{
  "id": "api.system.settings.list",
  "ver": "v1",
  "ts": "2020-12-01 12:21:46:829+0000",
  "params": {
    "resmsgid": null,
    "msgid": "f11acda288889cf47ecdf8812e623387",
    "err": null,
    "status": "success",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "response": [
      {
        "id": "uniqueField",
        "field": "uniqueField",
        "value": false
      },
      {
        "id": "custodianRootOrgId",
        "field": "custodianRootOrgId",
        "value": "01285019302823526477"
      },
      {
        "id": "tncConfigtest",
        "field": "tncConfigtest",
        "value": "test"
      },
      {
        "id": "userTnc",
        "field": "userTnc",
        "value": "{\"latestVersion\":\"3.5.0\"}"
      },
      {
        "id": "test",
        "field": "test",
        "value": "@test"
      },
      {
        "id": "userTnc",
        "field": "userTnc",
        "value": "{\"latestVersion\":\"3.5.0\"}"
      },
      {
        "id": "channelRegStatus",
        "field": "channelRegStatus",
        "value": false
      },
      {
        "id": "phoneUnique",
        "field": "phoneUnique",
        "value": true
      },
      {
        "id": "systemInitialisationStatus",
        "field": "systemInitialisationStatus",
        "value": "CUSTODIAN_ORG_CREATED"
      },
      {
        "id": "courseFrameworkId",
        "field": "courseFrameworkId",
        "value": "tpd"
      },
      {
        "id": "consumptionFaqs",
        "field": "consumptionFaqs",
        "value": "https://dev.sunbirded.org/faq.html"
      },
      {
        "id": "ssoCourseSection",
        "field": "ssoCourseSection",
        "value": "0129795520637419527"
      },
      {
        "id": "emailUnique",
        "field": "emailUnique",
        "value": true
      },
      {
        "id": "tn",
        "field": "tn",
        "value": "{'helpdeskEmail':'abc@abc.com','playstoreLink':'play.google.com/appid=123'}"
      },
      {
        "id": "emailUniqueAndPhone",
        "field": "emailUniqueAndPhone",
        "value": true
      }
    ]
  }
}
```

</details>

[/v1/org/read](http://docs.sunbird.org/latest/apis/orgapi/#operation/Organisation%20Get)\
API Method: **GET**

<details>

<summary>Sample Response Payload</summary>

```json
{
  "result": {
    "id": "api.org.read",
    "ver": "v1",
    "ts": "2020-11-23 10:03:39:935+0000",
    "params": {
      "resmsgid": null,
      "msgid": "5398bdd7-f80d-4a9e-9c13-90ae3c6bbcb0",
      "err": null,
      "status": "success",
      "errmsg": null
    },
    "responseCode": "OK",
    "result": {
      "dateTime": null,
      "preferredLanguage": null,
      "keys": {},
      "channel\"": "ChannelNew",
      "approvedBy": null,
      "description": "Updated Description",
      "updatedDate": "2020-12-01 10:29:49:496+0000",
      "addressId": "0131630420489011201",
      "provider": "channelnew",
      "orgCode": null,
      "locationId": null,
      "theme": null,
      "id": "0131630445447741440",
      "isApproved": null,
      "communityId": null,
      "slug": "channelnew",
      "email": "info@org.org",
      "isSSOEnabled": false,
      "identifier": "0131630445447741440",
      "thumbnail": null,
      "updatedBy\"": null,
      "orgName": "Org Name",
      "address": {},
      "externalId": "extid",
      "rootOrgId": "0131630445447741440",
      "imgUrl": null,
      "approvedDate": null,
      "homeUrl": null,
      "isDefault": null,
      "createdDate": "2020-12-01 09:52:46:962+0000",
      "createdBy": null,
      "hashTagId": "0131630445447741440",
      "noOfMembers": null,
      "status": 0,
      "orgLocation": [
        {
          "id": "9541f516-4c01-4322-aa06-4062687a0ce5",
          "type": "block"
        },
        {
          "id": "6dd69f1c-ba40-4b3b-8981-4fb6813c5e71",
          "type": "district"
        },
        {
          "id": "e9207c22-41cf-4a0d-81fb-1fbe3e34ae24",
          "type": "cluster"
        },
        {
          "id": "ccc7be29-8e40-4d0a-915b-26ec9228ac4a",
          "type": "state"
        }
      ],
      "isTenant": true,
      "isSchool": true,
      "organisationType": 2
    }
  }
}
```

</details>
{% endtab %}

{% tab title="Sunbird Lern - Data-pipeline" %}
Notification Service is dependent on Notification Flink Job in Lern data-pipeline to process Async Notifications.

Kafka Topic : {env}.lms.notification
{% endtab %}
{% endtabs %}



The Notification service requires a few configurations to be set in the properties file. Some of these properties can also be set as environment variables.

{% embed url="https://github.com/sunbird-lern/sunbird-notification-service/tree/release-4.5.0/sb-utils/src/main/resources" %}

{% embed url="https://github.com/sunbird-lern/sunbird-notification-service/tree/master/notification-sdk/src/main/resources" %}

