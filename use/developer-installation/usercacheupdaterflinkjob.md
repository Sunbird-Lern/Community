# UserCacheUpdaterFlinkJob

The three exhaust reports depend on the user metadata information which is generated from the user-cache-updater flink job by fetching information from different core Cassandra tables and are stored in the Redis cache. From Release-3.7.0 the design for the flink job has been changed and now the information will be fetched from the User Read API.

JIRA Link: [https://project-sunbird.atlassian.net/browse/SB-21691](https://project-sunbird.atlassian.net/browse/SB-21691)

Reference Wiki Links:

1. User Table Changes: [https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/2110881881](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/2110881881)
2. Org Table Changes: [https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/2260074547](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/2260074547)

**Current Design Implementation:**

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

**Proposed Design Implementation:**

<figure><img src="../../.gitbook/assets/image (24).png" alt="usercacheupdaterflinkdesign"><figcaption></figcaption></figure>

![](blob:https://project-sunbird.atlassian.net/4576cfc6-d4bf-4cad-b0a5-b217e77358ed#media-blob-url=true\&id=2da0751c-f2f3-4ec6-9a84-917fce115f47\&collection=contentId-1520074753\&contextId=1520074753\&height=551\&width=501\&alt=)Design for the fields to be fetched:

| Field Name            | Type          | Logic to fetch                                         | Description                                                                      |
| --------------------- | ------------- | ------------------------------------------------------ | -------------------------------------------------------------------------------- |
| **User-ID**           | String        | userId                                                 | It indicates user unique Identifier                                              |
| **Mobile Number**     | String        | encPhone                                               | User phone number in an encrypted format                                         |
| **Email ID**          | String        | encEmail                                               | User mail id in an encrypted format                                              |
| First Name            | String        | firstName                                              | User first name                                                                  |
| Last Name             | String        | lastName                                               | User Last Name                                                                   |
| Rootorgid             | String        | rootOrgId                                              | User root org id (can be used to differentiate between custodian and state user) |
| Board                 | String        | framework.board                                        | <p>User’s board<br>Assumption: It is single valued</p>                           |
| Medium                | List\[String] | framework.medium                                       | User medium                                                                      |
| Subject               | List\[String] | framework.subject                                      | User subjects                                                                    |
| Language              | List\[String] | language                                               | User Language                                                                    |
| Grade                 | List\[String] | framework.gradeLevel                                   | User grades                                                                      |
| framework             | String        | framework.id                                           | <p>User’s framework id<br>Assumption: It is single valued</p>                    |
| **UserType**          | String        | profileUserType.type                                   | User Type                                                                        |
| **UserSubType**       | String        | profileUserType.subType                                | User’s Sub Type                                                                  |
| **Orgname**           | String        | rootOrg.orgName                                        | <p>User’s Org Name<br>It is fetched from rootOrg Map.</p>                        |
| **School Name**       | String        | Fetch {name} where userLocation\[\*].type = 'school'   | <p>User’s School Name.<br>It is fetched from the userLocation Map</p>            |
| **School UDISE Code** | String        | Fetch {code} where userLocation\[\*].type = 'school'   | <p>User’s School UDISE Code.<br>It is fetched from the userLocation Map</p>      |
| **State Name**        | String        | Fetch {name} where userLocation\[\*].type = 'state'    | <p>User’s State Name.<br>It is fetched from the userLocation Map</p>             |
| **District Name**     | String        | Fetch {name} where userLocation\[\*].type = 'district' | <p>User’s District Name.<br>It is fetched from the userLocation Map</p>          |
| **Block Name**        | String        | Fetch {name} where userLocation\[\*].type = 'block'    | <p>User’s Block Name.<br>It is fetched from the userLocation Map</p>             |
| **Cluster Name**      | String        | Fetch {name} where userLocation\[\*].type = 'cluster'  | <p>User’s Cluster Name.<br>It is fetched from the userLocation Map</p>           |

**User Read API Request**\
\
curl --location --request GET 'http://{Private LB}/learner/private/user/v1/read/:uuid?fields=locations'\
\
**User Read API Response**

```
{
  "id": ".private.user.v1.read.123456",
  "ver": "private",
  "ts": "2021-03-09 11:33:42:061+0530",
  "params": {
    "resmsgid": null,
    "msgid": "06ff91d6-043e-4714-b002-6f8b90a04723",
    "err": null,
    "status": "success",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "response": {
      "webPages": [],
      "maskedPhone": null,
      "subject": [],
      "channel": "root2",
      "language": [],
      "updatedDate": null,
      "password": null,
      "managedBy": null,
      "flagsValue": 2,
      "id": "a962a4ff-b5b5-46ad-a9fa-f54edf1bcccb",
      "recoveryEmail": "",
      "identifier": "a962a4ff-b5b5-46ad-a9fa-f54edf1bcccb",
      "thumbnail": null,
      "updatedBy": null,
      "accesscode": null,
      "locationIds": [
        "8db3345c-1bfc-4276-aef1-7ea0f3183211",
        "d087424e-18cb-49b0-865c-98f265c73ed3",
        "13087424e-18cb-49b0-865c-98f265c73ed3",
        "43087424e-18cb-49b0-865c-98f265c73ed3"
      ],
      "externalIds": [
        {
          "idType": "root2",
          "provider": "root2",
          "id": "123456"
        }
      ],
      "registryId": null,
      "rootOrgId": "0127738024883077121",
      "prevUsedEmail": "",
      "firstName": "Creator",
      "tncAcceptedOn": null,
      "allTncAccepted": {},
      "phone": "",
      "dob": null,
      "grade": [],
      "currentLoginTime": null,
      "userType": null,
      "status": 1,
      "lastName": "test",
      "tncLatestVersion": "v1",
      "gender": null,
      "roles": [
        "PUBLIC"
      ],
      "prevUsedPhone": "",
      "stateValidated": false,
      "isDeleted": false,
      "organisations": [
        {
          "organisationId": "0127738024883077121",
          "updatedBy": null,
          "addedByName": null,
          "addedBy": null,
          "roles": [
            "PUBLIC"
          ],
          "approvedBy": null,
          "updatedDate": null,
          "userId": "a962a4ff-b5b5-46ad-a9fa-f54edf1bcccb",
          "approvaldate": null,
          "isDeleted": false,
          "hashTagId": "0127738024883077121",
          "isRejected": null,
          "id": "0132322953313320960",
          "position": null,
          "isApproved": null,
          "orgjoindate": "2021-03-09 11:31:31:930+0530",
          "orgLeftDate": null
        }
      ],
      "profileUserType": {
        "usertype": "administrator",
        "usersubtype": "deo"
      },
      "userLocations": [
        {
          "code": "21",
          "name": "Odisha",
          "id": "8db3345c-1bfc-4276-aef1-7ea0f3183211",
          "type": "state",
          "parentId": null
        },
        {
          "code": "2112",
          "name": "CUTTACK",
          "id": "d087424e-18cb-49b0-865c-98f265c73ed3",
          "type": "district",
          "parentId": "8db3345c-1bfc-4276-aef1-7ea0f3183211"
        },
        {
          "code": "211",
          "name": "BLOCK1",
          "id": "13087424e-18cb-49b0-865c-98f265c73ed3",
          "type": "block",
          "parentId": "8db3345c-1bfc-4276-aef1-7ea0f3183211"
        },
        {
          "code": "211",
          "name": "CLUSTER1",
          "id": "43087424e-18cb-49b0-865c-98f265c73ed3",
          "type": "cluster",
          "parentId": "8db3345c-1bfc-4276-aef1-7ea0f3183211"
        },
        {
          "name": "DPS, MATHURA",
          "id": "63087424e-18cb-49b0-865c-98f265c73ed3",
          "type": "school",
          "externalid": "3183211"
        }
      ],
      "countryCode": null,
      "tncLatestVersionUrl": "https://dev-sunbird-temp.azureedge.net/portal/terms-and-conditions-v1.html",
      "maskedEmail": "am******@yopmail.com",
      "tempPassword": null,
      "email": "am******@yopmail.com",
      "rootOrg": {
        "dateTime": null,
        "preferredLanguage": "English",
        "keys": {},
        "approvedBy": null,
        "channel": "root2",
        "description": "Root Org2",
        "updatedDate": null,
        "addressId": null,
        "orgType": null,
        "provider": null,
        "locationId": null,
        "orgCode": null,
        "theme": null,
        "id": "0127738024883077121",
        "communityId": null,
        "isApproved": null,
        "email": null,
        "slug": "root2",
        "isSSOEnabled": null,
        "thumbnail": null,
        "orgName": "Root Org2",
        "updatedBy": null,
        "locationIds": [],
        "externalId": null,
        "isRootOrg": true,
        "rootOrgId": "0127738024883077121",
        "approvedDate": null,
        "imgUrl": null,
        "homeUrl": null,
        "orgTypeId": null,
        "isDefault": null,
        "createdDate": "2019-05-31 16:41:29:485+0530",
        "createdBy": null,
        "parentOrgId": null,
        "hashTagId": "0127738024883077121",
        "noOfMembers": null,
        "status": 1
      },
      "phoneVerified": false,
      "profileSummary": null,
      "recoveryPhone": "",
      "avatar": null,
      "userName": "creatortest_72yz",
      "userId": "a962a4ff-b5b5-46ad-a9fa-f54edf1bcccb",
      "userSubType": null,
      "promptTnC": true,
      "emailVerified": true,
      "lastLoginTime": null,
      "createdDate": "2021-03-09 11:31:23:189+0530",
      "framework": {
        "board": [
          "IGOT-Health"
        ],
        "gradeLevel": [
          "Volunteers"
        ],
        "id": [
          "igot_health"
        ],
        "medium": [
          "English"
        ],
        "subject": [
          "IRCS"
        ]
      },
      "createdBy": null,
      "location": null,
      "tncAcceptedVersion": null
    }
  }
}
```

**Queries:**

1. Should we fetch extra information eg webpage, createdBy, createdFor, etc? Fetch only if required for denorm job
2. Should we fetch externalid from now or not? Fetch only if required for denorm job
3. Should we directly fetch username or have a logic of firstname+lastname? firstname+lastname should be the username for reports
