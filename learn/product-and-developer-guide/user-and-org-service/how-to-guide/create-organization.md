# Create Organization

### Scenario <a href="#scenario" id="scenario"></a>

A company, XYZ Corp, is a global conglomerate with over ten thousand employees, spread across 5 locations. Employee training and enablement is one of the core values of the organization. To ensure that employees are regularly trained and upskilled, XYZ Corp has decided to use Sunbird for its learning and training solution on 3 topics, namely Life Science, eCommerce and Archeology (Indian, Greek, Mayan). Gita is the XYZ Corp’s Sunbird adminstrator and is tasked with setting this up in XYZCorp’s Sunbird instance.

#### Taskflow <a href="#taskflow" id="taskflow"></a>

Gita identifies the request API headers and body fields relevant for her task. She creates three tenant organizations, one for each training topic. She creates three sub-organizations for each sub-topic, under the tenant organization Archeology. Gita comes up with three distinct alphanumeric strings that is used as value of **channel**, for each of the tenant organization. Then Gita lists all existing **channel** identifiers to ensure they are not in use in XYZCorp’s Sunbird instance.

**Header Parameters**

| HEADER        | TYPE   | DESCRIPTION                | SAMPLE                                                         |
| ------------- | ------ | -------------------------- | -------------------------------------------------------------- |
| Content-type  | String | Mime type of the request   | application/json                                               |
| Authorization | String | Authorization key received | abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890 |

**Request Body**

```
  curl -X POST \
https://sunbird.xyzcorp.com/api/channel/v1/list \
    -H 'Content-type: application/json' \
    -H 'Authorization: Bearer abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890'

```

**Response Body**

> Example output contains 800+ channels. Partial response body shown for brevity.

```
  {
    "id": "api.channel.list",
    "ver": "1.0",
    "ts": "2018-10-31T03:32:00.875Z",
    "params": {
        "resmsgid": "871ffbb0-dcbd-11e8-af3b-63285e87d510",
        "msgid": "86f62c90-dcbd-11e8-8e5d-e72c97a8e618",
        "status": "successful",
        "err": null,
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "channels": [
            {
                "identifier": "channel",
                "code": "channel",
                "framewor  (or channel IDks": [],
                "consumerId": "9d8a6562-ac2d-4c10-b5fa-34dfb327aeb1",
                "channel": "in.example",
                "description": "",
                "createdOn": "2018-10-20T06:20:50.861+0000",
                "versionKey": "1513750850861",
                "appId": "example_portal",
                "name": "My Channel",
                "lastUpdatedOn": "2018-12-20T06:20:50.861+0000",
                "categories": [],
                "defaultFramework": "NCF",
                "status": "Live"
            },
            {
            .
            .
            .
            .
            {
                "owner": "xyz.corp",
                "identifier": "megalithic",
                "code": "megalithic",
                "consumerId": "dc62def7-ecfd-3959-ab2f-d98251ed83e2",
                "channel": "hyper.channel",
                "description": "Organization structure",
                "type": "Education",
                "createdOn": "2017-09-07T05:04:18.751+0000",
                "versionKey": "2873475457420",
                },
                "appId": "staging.xyz.corp",
                "name": "The XCorp",
                "lastUpdatedOn": "2018-09-07T05:04:43.807+0000",
                "categories": [],
                "status": "Live"
            }
        ],
        "count": 808
    }
}

```

In the response body, Gita inspects the value of all tokens called **code** to ensure that the **channel** identifier name she’s decided upon, does not already exist. She creates the three tenant organisations, one for each of the topics. The API request parameters and invocation is depicted in the following example:

**Header Parameters**

| HEADER                     | TYPE   | DESCRIPTION                                                                   | SAMPLE                                                                                                                                 |
| -------------------------- | ------ | ----------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Content-type               | String | Mime type of the request                                                      | application/json                                                                                                                       |
| Authorization              | String | Authorization key received                                                    | abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890                                                                         |
| x-authenticated-user-token | String | A token that identifies that the caller is authorised to invoke this REST API | eyqtUZ.Y0RU965YATAb3ws4GcJzEWblQPzUVsefMx6QqO73WwEPFDPhG28uK2z6kTcjst4oqVLNY63tUPZphE5pWRjPYQEIOJK-JxRhJ0RsR6DmJCSb3kmS14n4l5FWQBEQ0AE |

**Request Body : Tenant org creation**

```
  curl -X POST \
https://sunbird.xyzcorp.com/api/org/v1/create \
    -H 'Content-type: application/json' \
    -H 'Authorization: Bearer abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890' \
    -H 'x-authenticated-user-token: eyqtUZ.Y0RU965YATAb3ws4GcJzEWblQPzUVsefMx6QqO73WwEPFDPhG28uK2z6kTcjst4oqVLNY63tUPZphE5pWRjPYQEIOJK-JxRhJ0RsR6DmJCSb3kmS14n4l5FWQBEQ0AE' \
    -d '{
        "request": {
        "orgName": "Archeology",
        "description": "Study of really old stuff.",
        "isTenant": true,
        "channel": "xyzCorpArcheologyChannel",
        "preferredLanguage": "English, Dutch, Hindi, Cakchiquel",
        "homeUrl": "https://www.example.com/training/arch"
    }
}'

```

**Response Body**

```
  {
"id": "api.org.create",
"params":
{
    "err": null,
    "errmsg": null,
    "msgid": "56e36e85-abca-42bc-9fcd-e8a50c78a316",
    "resmsgid": null,
    "status": "success"
},
"responseCode": "OK",
"result":
{
    "organisationId": "04584469560898483465",
    "response": "SUCCESS"
},
"ts": "2018-10-30 08:24:29:856+0000",
"ver": "v1"
}

```

Gita comes up with three identifiers for each sub-organisation. These identifiers are unique across the organisation Archeology and are used as the value of **externalID** in the request body. She also make a note of the **organisationId** of the Archaeology tenant organisation, which is used as the value of **provider** in the request body. Gita provides appropriate values in the request body and invoke the organisation create API, for all three topics (Life Science, eCommerce, Archaeology). Upon each successful outcome, she makes a note of the value of **organisationId** of each sub-organisation respectively. The API request parameters and invocation are depicted in the following example:

**Header Parameters**

| HEADER                     | TYPE   | DESCRIPTION                                                                   | SAMPLE                                                                                                                                 |
| -------------------------- | ------ | ----------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Content-type               | String | Mime type of the request                                                      | application/json                                                                                                                       |
| Authorization              | String | Authorization key received                                                    | abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890                                                                         |
| x-authenticated-user-token | String | A token that identifies that the caller is authorized to invoke this REST API | eyqtUZ.Y0RU965YATAb3ws4GcJzEWblQPzUVsefMx6QqO73WwEPFDPhG28uK2z6kTcjst4oqVLNY63tUPZphE5pWRjPYQEIOJK-JxRhJ0RsR6DmJCSb3kmS14n4l5FWQBEQ0AE |

**Request Body : Request for sub-org creation**

```
  curl -X POST \
https://sunbird.xyzcorp.com/api/org/v1/create \
-H 'Content-type: application/json' \
-H 'Authorization: Bearer abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890' \
-H 'x-authenticated-user-token: eyqtUZ.Y0RU965YATAb3ws4GcJzEWblQPzUVsefMx6QqO73WwEPFDPhG28uK2z6kTcjst4oqVLNY63tUPZphE5pWRjPYQEIOJK-JxRhJ0RsR6DmJCSb3kmS14n4l5FWQBEQ0AE' \
    -d '{
        "request":
        {
            "orgName": "Indian Archeology",
            "description": "Study of ancient tea leaves in Rabdentse, Sikkim",
            "isTenant": false,
            "channel" : "channel value of tenantOrg"
            
        }
    }'

```

**Response Body**

```
  {
    "id": "api.org.create",
    "ver": "v1",
    "ts": "2018-11-12 15:52:10:333+0000",
    "params": {
        "resmsgid": null,
        "msgid": "f0f94391-b6e9-4f25-8317-fd70c2fcbae1",
        "err": null,
        "status": "success",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "organisationId": "05986338210410082051",
        "response": "SUCCESS"
    }
}

```

On successfully creating an organisation, the next step is to create users and assign roles to the users within the newly created organisation and sub-organisations.

#### Concepts Covered <a href="#concepts-covered" id="concepts-covered"></a>

**Organisation**: It is an conceptual representation of a collection, like institute or a body of individuals.

**Channel**: Unique identification number associated with a tenant organisation. No two channels can be the same, across any Sunbird instance.

**Tenant Organisation**: A tenant in any Sunbird instance. Multiple tenant organisations can co-exist in a Sunbird instance.

**Sub Organisation**: A subordinate level organisations inside a tenant organisation
