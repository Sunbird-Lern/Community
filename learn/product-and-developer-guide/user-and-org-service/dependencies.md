# Dependencies

### External Dependencies

{% tabs %}
{% tab title="Sunbird Knowlg" %}
Content service APIs to read and update channel details and to do framework validation.\
[https://github.com/project-sunbird/knowledge-platform](https://github.com/project-sunbird/knowledge-platform)\
\
**Dependency API:**\
\
[/content/content/v1/search?orgdetails=orgName,email\
](http://docs.sunbird.org/1.8/apis/content/#operation/Search%20Content)API Method: **POST**

<details>

<summary>Sample Request Payload</summary>

```json
{
  "request": {
    "filters": {
      "channel": "string",
      "objectType": [
        "string"
      ],
      "contentType": [
        "string"
      ],
      "status": [
        "string"
      ]
    },
    "sort_by": {
      "createdOn": "string"
    },
    "fields": [
      "string"
    ]
  }
}
```

</details>

<details>

<summary>Sample Response Payload</summary>

```json
{
  "result": {
    "count": 0,
    "content": [
      {}
    ]
  },
  "id": "string",
  "ver": "string",
  "ts": "string",
  "params": {
    "resmsgid": "string",
    "msgid": "string",
    "err": "string",
    "status": "string",
    "errmsg": "string"
  },
  "responseCode": {}
}
```

</details>

[/channel/v1/read/_\{{channelid\}}_](http://docs.sunbird.org/latest/apis/framework/#operation/ChannelV1ReadGet)\
API Method: **GET**

<details>

<summary>Sample Response Payload</summary>

```json
{
  "id": "api.channel.read",
  "ver": "3.0",
  "ts": "2020-12-14T08:33:50ZZ",
  "params": {
    "resmsgid": "02c742d2-57e1-4441-aa31-0ce339c3917b",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "channel": {
      "identifier": "channel-405",
      "lastStatusChangedOn": "2020-12-14T08:27:49.490+0000",
      "code": "channel-405",
      "consumerId": "7411b6bd-89f3-40ec-98d1-229dc64ce77d",
      "assetAdditionalCategories": [],
      "autoCreateBatch": "Enabled",
      "languageCode": [],
      "suggested_frameworks": [
        {
          "identifier": "NCF",
          "code": "NCF",
          "name": "NCF",
          "objectType": "Framework"
        }
      ],
      "createdOn": "2020-12-14T08:27:49.490+0000",
      "objectType": "Channel",
      "versionKey": "1607934825088",
      "collectionPrimaryCategories": [
        "Content Playlist",
        "Course",
        "Digital Textbook",
        "Explanation Content"
      ],
      "contentPrimaryCategories": [
        "Course Assessment",
        "eTextbook",
        "Explanation Content",
        "Learning Resource",
        "Practice Question Set",
        "Teacher Resource"
      ],
      "name": "Channel without Default License",
      "lastUpdatedOn": "2020-12-14T08:33:45.088+0000",
      "defaultCourseFramework": "TPD",
      "collectionAdditionalCategories": [
        "Textbook",
        "Lesson Plan",
        "TV Lesson"
      ],
      "assetPrimaryCategories": [
        "Asset",
        "CertAsset",
        "Certificate Template"
      ],
      "contentAdditionalCategories": [
        "Classroom Teaching Video",
        "Concept Map",
        "Curiosity Question Set",
        "Experiential Resource",
        "Explanation Video",
        "Focus Spot",
        "Learning Outcome Definition",
        "Lesson Plan",
        "Marking Scheme Rubric",
        "Pedagogy Flow",
        "Previous Board Exam Papers",
        "TV Lesson",
        "Textbook"
      ],
      "status": "Live",
      "defaultFramework": "NCF"
    }
  }
}
```

</details>

[/framework/v1/read/_\{{frameworkid\}}_\
](http://docs.sunbird.org/latest/apis/framework/#operation/FrameworkV1ReadGet)API Method: **GET**

<details>

<summary>Sample Response Payload</summary>

```json
{
  "id": "api.framework.read",
  "ver": "1.0",
  "ts": "2020-12-14T19:51:24ZZ",
  "params": {
    "resmsgid": "28f10a2a-ce6c-4dbe-a733-4c193013e84b",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "framework": {
      "identifier": "dummy_framework",
      "code": "Dumy framework updated",
      "name": "Framework Name",
      "description": "Dumy framework updated",
      "categories": [
        {
          "identifier": "dummy_framework_subject",
          "code": "subject",
          "terms": [
            {
              "identifier": "dummy_framework_subject_english",
              "code": "english",
              "translations": null,
              "name": "English",
              "description": "English",
              "index": 1,
              "category": "subject",
              "status": "Live"
            }
          ],
          "translations": null,
          "name": "Subject",
          "description": "Updated description",
          "index": 1,
          "status": "Live"
        },
        {
          "identifier": "dummy_framework_medium",
          "code": "medium",
          "translations": null,
          "name": "Medium",
          "description": "Medium",
          "index": 2,
          "status": "Live"
        }
      ],
      "type": "K-12",
      "objectType": "Framework"
    }
  }
}
```

</details>

[/data/v1/location/search\
](http://docs.sunbird.org/latest/apis/locationapi/#operation/Search-Location)API Method: **POST**

<details>

<summary>Sample Request Payload</summary>

```json
{
  "request": {
    "filters": {
      "code": "APCODE1"
    }
  }
}
```

</details>

<details>

<summary>Sample Response Payload</summary>

```json
{
  "id": "api.location.search",
  "ver": "v1",
  "ts": "2020-11-20 07:20:43:770+0000",
  "params": {
    "resmsgid": null,
    "msgid": "2d12c998-96c4-43d6-8937-4ebbb8b68d02",
    "err": null,
    "status": "success",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "response": [
      {
        "identifier": "6824e3d3-5512-4344-a481-7bac011edaa8",
        "code": "APCODE",
        "name": "APSTATE",
        "id": "6824e3d3-5512-4344-a481-7bac011edaa8",
        "type": "state"
      }
    ],
    "count": 1
  }
}
```

</details>
{% endtab %}

{% tab title="Sunbird Ed" %}
Form APIs to validate the profile information of the user.

[https://github.com/Sunbird-Ed/SunbirdEd-portal](https://github.com/Sunbird-Ed/SunbirdEd-portal/pulls)\
\
**Dependency API:**\
[/device/profile/_\{{id\}}_](http://docs.sunbird.org/3.6.0/apis/deviceapi/#tag/Device-Profile-API\(s\))\
API Method: **GET**

<details>

<summary>Sample Response Payload</summary>

```json
{
  "id": "analytics.device-profile",
  "ver": "1.0",
  "ts": "2020-11-27T12:33:27.115+00:00",
  "params": {
    "resmsgid": "93aa54f5-03b2-4c82-af3a-acc3ee4071f7",
    "status": "successful"
  },
  "responseCode": "OK",
  "result": {
    "userDeclaredLocation": {
      "state": "Karnataka",
      "district": "BENGALURU URBAN SOUTH"
    },
    "ipLocation": {
      "state": "Karnataka",
      "district": "BENGALURU URBAN SOUTH"
    }
  }
}
```

</details>
{% endtab %}

{% tab title="Kafka" %}
Configure Kafka setup for sending telemetry events. Sunbird Telemetry is a specification to instrument all the key events
{% endtab %}
{% endtabs %}
