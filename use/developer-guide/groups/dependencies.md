# Dependencies

### Dependency Services:

{% tabs %}
{% tab title="Sunbird Lern - Notification Service" %}
Group Service connects to Notification Service to fetch all the notifications for the particular user by using notification feed APIs.\
\
**Dependency API:**\
[/notification/v1/feed/_\{{CRUD-operation\}}_](../notification-service/apis.md)
{% endtab %}

{% tab title="Sunbird Lern - UserOrg Service" %}
Group Service connects to UserOrg Service to fetch user/member information. Any other service which has user information in a similar schema can be plugged in instead of this dependency.\
\
**Dependency API:**\
\
[/api/user/v5/read/\{{userId\}}](http://docs.sunbird.org/latest/apis/userapi/#operation/Read\_User\_V5)\
API Method: **GET**

<details>

<summary>Sample Response Payload</summary>

```json
{
  "id": "api.user.read",
  "ver": "v4",
  "ts": "2021-04-09 21:09:05:331+0530",
  "params": {
    "resmsgid": null,
    "msgid": "a1d3d756-0f9b-4ec6-95a6-6560896d5294",
    "err": null,
    "status": "success",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "response": {
      "maskedPhone": null,
      "tcStatus": null,
      "channel": "channel1",
      "updatedDate": "2021-04-07 05:09:45:607+0000",
      "managedBy": null,
      "flagsValue": 2,
      "id": "96102c3f-2c22-4614-8dcc-6b130cefe586",
      "recoveryEmail": "co**************@yopmail.com",
      "identifier": "96102c3f-2c22-4614-8dcc-6b130cefe586",
      "updatedBy": "96102c3f-2c22-4614-8dcc-6b130cefe586",
      "externalIds": [],
      "rootOrgId": "0126796199493140480",
      "prevUsedEmail": null,
      "firstname": "first name",
      "tncAcceptedOn": 1617265216047,
      "allTncAccepted": {},
      "phone": null,
      "dob": null,
      "userType": "student",
      "status": 1,
      "lastName": null,
      "tncLatestVersion": "3.5.0",
      "roles": [
        {
          "role": "COURSE_CREATOR",
          "userId": "96102c3f-2c22-4614-8dcc-6b130cefe586",
          "scope": [
            {
              "organisationId": "0126796199493140480"
            }
          ],
          "createdDate": "2021-06-07 11:29:41:606+0530",
          "updatedBy": null,
          "createdBy": "96102c3f-2c22-4614-8dcc-6b130cefe586",
          "updatedDate": null
        }
      ],
      "prevUsedPhone": null,
      "stateValidated": false,
      "isDeleted": false,
      "organisations": [
        {
          "organisationId": "0126796199493140480",
          "updatedBy": null,
          "orgName": "org1",
          "addedByName": null,
          "addedBy": null,
          "approvedBy": null,
          "channel": "channel1",
          "locationIds": "027f81d8-0a2c-4fc6-96ac-59fe4cea3abf 8250d58d-f1a2-4397-bfd3-b2e688ba7141",
          "orgLocation": [
            {
              "type": "state",
              "id": "027f81d8-0a2c-4fc6-96ac-59fe4cea3abf"
            },
            {
              "type": "district",
              "id": "8250d58d-f1a2-4397-bfd3-b2e688ba7141"
            }
          ],
          "externalId": 101010,
          "updatedDate": null,
          "isSelfDeclared": true,
          "associationtype": 2,
          "isSystemUpload": false,
          "isSSO": false,
          "userId": "96102c3f-2c22-4614-8dcc-6b130cefe586",
          "approvaldate": null,
          "isSchool": false,
          "isDeleted": false,
          "hashTagId": "0126796199493140480",
          "isRejected": null,
          "locations": [
            {
              "code": 29,
              "name": "state1",
              "id": "027f81d8-0a2c-4fc6-96ac-59fe4cea3abf",
              "type": "state",
              "parentId": null
            },
            {
              "code": 2901,
              "name": "district1",
              "id": "8250d58d-f1a2-4397-bfd3-b2e688ba7141",
              "type": "district",
              "parentId": "027f81d8-0a2c-4fc6-96ac-59fe4cea3abf"
            }
          ],
          "id": "01324864401294131212",
          "position": null,
          "isApproved": null,
          "orgjoindate": "2021-04-01 08:19:53:343+0000",
          "orgLeftDate": null
        },
        {
          "organisationId": "0127419693630996481321",
          "updatedBy": "96102c3f-2c22-4614-8dcc-6b130cefe586",
          "orgName": "org2",
          "addedByName": null,
          "addedBy": "96102c3f-2c22-4614-8dcc-6b130cefe586",
          "approvedBy": null,
          "channel": "tn",
          "locationIds": "91d9baae-14f1-477a-955c-f91bd9037f0b 107c9472-a950-4768-bcd6-f882910177c4 ba31e7c2-fac9-472a-8867-1582c73bcca8 5c8876b5-981c-4c6a-b23d-20c9e17428e1",
          "orgLocation": [
            {
              "id": "91d9baae-14f1-477a-955c-f91bd9037f0b",
              "type": "state"
            },
            {
              "id": "107c9472-a950-4768-bcd6-f882910177c4",
              "type": "district"
            },
            {
              "id": "ba31e7c2-fac9-472a-8867-1582c73bcca8",
              "type": "block"
            },
            {
              "id": "5c8876b5-981c-4c6a-b23d-20c9e17428e1",
              "type": "cluster"
            }
          ],
          "externalId": 33100800608,
          "updatedDate": "2021-04-07 05:09:38:366+0000",
          "userId": "96102c3f-2c22-4614-8dcc-6b130cefe586",
          "approvaldate": null,
          "isSchool": true,
          "isDeleted": false,
          "hashTagId": "0127419693630996481321",
          "isRejected": false,
          "locations": [
            {
              "code": 31,
              "name": "state2",
              "id": "91d9baae-14f1-477a-955c-f91bd9037f0b",
              "type": "state",
              "parentId": null
            },
            {
              "code": 3110,
              "name": "district2",
              "id": "107c9472-a950-4768-bcd6-f882910177c4",
              "type": "district",
              "parentId": "91d9baae-14f1-477a-955c-f91bd9037f0b"
            },
            {
              "code": 31100169,
              "name": "block1",
              "id": "ba31e7c2-fac9-472a-8867-1582c73bcca8",
              "type": "block",
              "parentId": "107c9472-a950-4768-bcd6-f882910177c4"
            },
            {
              "code": 3110016901,
              "name": "block1 Cluster",
              "id": "5c8876b5-981c-4c6a-b23d-20c9e17428e1",
              "type": "cluster",
              "parentId": "ba31e7c2-fac9-472a-8867-1582c73bcca8"
            }
          ],
          "id": "0132527931586969602",
          "position": null,
          "isApproved": false,
          "orgjoindate": "2021-04-07 05:09:45:655+0000",
          "orgLeftDate": "2021-04-07 05:09:38:366+0000"
        }
      ],
      "provider": null,
      "countryCode": null,
      "tncLatestVersionUrl": "https://organisation2.blob.core.windows.net/termsandcondtions/terms-and-conditions-v9.html#termsOfUse",
      "maskedEmail": "k1**@yopmail.com",
      "email": "k1**@yopmail.com",
      "rootOrg": {
        "dateTime": null,
        "preferredLanguage": null,
        "keys": null,
        "approvedBy": null,
        "channel": "channel1",
        "description": "org3",
        "updatedDate": "2021-03-31 17:31:19:346+0000",
        "addressId": null,
        "organisationType": 5,
        "orgType": null,
        "isTenant": true,
        "provider": null,
        "locationId": null,
        "orgCode": null,
        "theme": null,
        "id": "0126796199493140480",
        "communityId": null,
        "isApproved": null,
        "email": null,
        "slug": "channel1",
        "isSSOEnabled": null,
        "orgName": "org1",
        "updatedBy": null,
        "locationIds": "027f81d8-0a2c-4fc6-96ac-59fe4cea3abf 8250d58d-f1a2-4397-bfd3-b2e688ba7141",
        "externalId": 101010,
        "orgLocation": [
          {
            "type": "state",
            "id": "027f81d8-0a2c-4fc6-96ac-59fe4cea3abf"
          },
          {
            "type": "district",
            "id": "8250d58d-f1a2-4397-bfd3-b2e688ba7141"
          }
        ],
        "isRootOrg": true,
        "rootOrgId": "0126796199493140480",
        "approvedDate": null,
        "imgUrl": null,
        "homeUrl": null,
        "orgTypeId": null,
        "isDefault": null,
        "createdDate": "2019-01-18 09:48:13:428+0000",
        "createdBy": "system",
        "parentOrgId": null,
        "hashTagId": "0126796199493140480",
        "noOfMembers": null,
        "status": 1
      },
      "phoneVerified": false,
      "tcUpdatedDate": null,
      "userLocations": [
        {
          "code": 3110,
          "name": "district2",
          "id": "107c9472-a950-4768-bcd6-f882910177c4",
          "type": "district",
          "parentId": "91d9baae-14f1-477a-955c-f91bd9037f0b"
        },
        {
          "code": 3110016901,
          "name": "block1 Cluster",
          "id": "5c8876b5-981c-4c6a-b23d-20c9e17428e1",
          "type": "cluster",
          "parentId": "ba31e7c2-fac9-472a-8867-1582c73bcca8"
        },
        {
          "code": 31,
          "name": "state2",
          "id": "91d9baae-14f1-477a-955c-f91bd9037f0b",
          "type": "state",
          "parentId": null
        },
        {
          "code": 31100169,
          "name": "block1",
          "id": "ba31e7c2-fac9-472a-8867-1582c73bcca8",
          "type": "block",
          "parentId": "107c9472-a950-4768-bcd6-f882910177c4"
        },
        {
          "identifier": "2e4a420e-a6b8-4688-b12e-0e5f5141d175",
          "code": 31100800608,
          "name": "org2",
          "id": "2e4a420e-a6b8-4688-b12e-0e5f5141d175",
          "type": "school",
          "parentId": "5c8876b5-981c-4c6a-b23d-20c9e17428e1"
        }
      ],
      "recoveryPhone": null,
      "userName": "username 2",
      "userId": "96102c3f-2c22-4614-8dcc-6b130cefe586",
      "userSubType": null,
      "promptTnC": false,
      "emailVerified": true,
      "createdDate": "2021-04-01 08:19:50:971+0000",
      "framework": {
        "board": "State state3",
        "gradeLevel": "Class 1",
        "id": "ap_k-12_1",
        "medium": "English",
        "subject": "English"
      },
      "createdBy": null,
      "profileUserType": {
        "subType": null,
        "type": "student"
      },
      "profileUserTypes": [
        {
          "subType": null,
          "type": "student"
        }
      ],
      "tncAcceptedVersion": "3.5.0"
    }
  }
}
```

</details>

[/api/course/v1/batch/list\
](http://docs.sunbird.org/latest/apis/coursebatchmanapi/#operation/CourseBatchSearchhttp://docs.sunbird.org/latest/apis/coursebatchmanapi/#operation/CourseBatchSearch)API Method: **GET**

<details>

<summary>Sample Request Payload</summary>

```json
{
  "request": {
    "filters": {
      "courseId": "{{course-id}}"
    },
    "limit": 2
  }
}
```

</details>

<details>

<summary>Sample Response Payload</summary>

```json
{
  "id": "api.course.batch.search",
  "ver": "v1",
  "ts": "2020-11-23 15:31:47:895+0000",
  "params": {
    "resmsgid": null,
    "msgid": "3b07f74d-59af-494c-8d41-c8b665fa75ea",
    "err": null,
    "status": "success",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "response": {
      "count": 15,
      "content": [
        {
          "identifier": "0131440087048683528",
          "createdFor": [],
          "endDate": "2020-11-30",
          "description": "batch description1",
          "updatedDate": null,
          "cert_templates": {
            "Test_Template_prad": {
              "identifier": "Test_Template_prad",
              "criteria": {
                "enrollment": {
                  "status": 2
                }
              },
              "name": "Updated Asset",
              "notifyTemplate": {
                "emailTemplateType": "defaultCertTemp",
                "subject": "Completion certificate",
                "stateImgUrl": "https://sunbirddev.blob.core.windows.net/orgemailtemplate/img/File-0128212938260643843.png",
                "regards": "Minister of Gujarat",
                "regardsperson": "Chairperson"
              },
              "issuer": {
                "name": "Gujarat Council of Educational Research and Training",
                "url": "https://gcert.gujarat.gov.in/gcert/"
              },
              "url": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/content/test_template_prad/artifact/file-0130860005482086401.svg",
              "signatoryList": [
                {
                  "image": "https://cdn.pixabay.com/photo/2014/11/09/08/06/signature-523237__340.jpg",
                  "name": "CEO Gujarat",
                  "id": "CEO",
                  "designation": "CEO"
                }
              ]
            }
          },
          "batchId": "0131440087048683528",
          "tandc": null,
          "createdDate": "2020-11-04 12:26:38:668+0000",
          "createdBy": "95e4942d-cbe8-477d-aebd-ad8e6de4bfc8",
          "mentors": [],
          "name": "test cert scalability",
          "id": "0131440087048683528",
          "enrollmentType": "open",
          "enrollmentEndDate": null,
          "courseId": "do_1131396442662912001425",
          "collectionId": "do_1131396442662912001425",
          "startDate": "2020-11-04",
          "status": 1
        },
        {
          "identifier": "0131439524674273284",
          "createdFor": [],
          "endDate": "2020-12-30",
          "description": "batch description1",
          "updatedDate": null,
          "cert_templates": {
            "Test_Template_prad": {
              "identifier": "Test_Template_prad",
              "criteria": {
                "enrollment": {
                  "status": 2
                }
              },
              "name": "Updated Asset",
              "notifyTemplate": {
                "emailTemplateType": "defaultCertTemp",
                "subject": "Completion certificate",
                "stateImgUrl": "https://sunbirddev.blob.core.windows.net/orgemailtemplate/img/File-0128212938260643843.png",
                "regards": "Minister of Gujarat",
                "regardsperson": "Chairperson"
              },
              "issuer": {
                "name": "Gujarat Council of Educational Research and Training",
                "url": "https://gcert.gujarat.gov.in/gcert/"
              },
              "url": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/content/test_template_prad/artifact/file-0130860005482086401.svg",
              "signatoryList": [
                {
                  "image": "https://cdn.pixabay.com/photo/2014/11/09/08/06/signature-523237__340.jpg",
                  "name": "CEO Gujarat",
                  "id": "CEO",
                  "designation": "CEO"
                }
              ]
            }
          },
          "batchId": "0131439524674273284",
          "tandc": null,
          "createdDate": "2020-11-04 10:24:25:778+0000",
          "createdBy": "95e4942d-cbe8-477d-aebd-ad8e6de4bfc8",
          "mentors": [],
          "name": "test cert scalability",
          "id": "0131439524674273284",
          "enrollmentType": "open",
          "enrollmentEndDate": null,
          "courseId": "do_1131396442662912001425",
          "collectionId": "do_1131396442662912001425",
          "startDate": "2020-11-04",
          "status": 1
        }
      ]
    }
  }
}
```

</details>

\
[/api/user/v3/search](http://docs.sunbird.org/latest/apis/userapi/#operation/User\_Search\_V3)\
API Method: **GET**

<details>

<summary>Sample Request Payload</summary>

```json
{
  "request": {
    "filters": {
      "email": "neworgadmin@yopmail.com"
    }
  }
}
```

</details>

<details>

<summary>Sample Response Payload</summary>

```json
{
  "id": "api.user.search",
  "ver": "v2",
  "ts": "2020-11-23 09:16:58:628+0000",
  "params": {
    "resmsgid": null,
    "msgid": "ad7135b8-ef64-44bd-adaa-0b131a657689",
    "err": null,
    "status": "success",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "response": {
      "count": 1,
      "content": [
        {
          "maskedPhone": null,
          "tcStatus": null,
          "channel": "channel1",
          "updatedDate": "2021-04-07 05:09:45:607+0000",
          "managedBy": null,
          "flagsValue": 2,
          "id": "96102c3f-2c22-4614-8dcc-6b130cefe586",
          "recoveryEmail": "co**************@yopmail.com",
          "identifier": "96102c3f-2c22-4614-8dcc-6b130cefe586",
          "updatedBy": "96102c3f-2c22-4614-8dcc-6b130cefe586",
          "externalIds": [],
          "rootOrgId": "0126796199493140480",
          "prevUsedEmail": null,
          "firstname": "first name",
          "tncAcceptedOn": 1617265216047,
          "allTncAccepted": {},
          "phone": null,
          "dob": null,
          "userType": "student",
          "status": 1,
          "lastName": null,
          "tncLatestVersion": "3.5.0",
          "roles": [
            {
              "role": "COURSE_CREATOR",
              "userId": "96102c3f-2c22-4614-8dcc-6b130cefe586",
              "scope": [
                {
                  "organisationId": "0126796199493140480"
                }
              ],
              "createdDate": "2021-06-07 11:29:41:606+0530",
              "updatedBy": null,
              "createdBy": "96102c3f-2c22-4614-8dcc-6b130cefe586",
              "updatedDate": null
            }
          ],
          "prevUsedPhone": null,
          "stateValidated": false,
          "isDeleted": false,
          "organisations": [
            {
              "organisationId": "0126796199493140480",
              "updatedBy": null,
              "orgName": "org1",
              "addedByName": null,
              "addedBy": null,
              "approvedBy": null,
              "channel": "channel1",
              "locationIds": "027f81d8-0a2c-4fc6-96ac-59fe4cea3abf 8250d58d-f1a2-4397-bfd3-b2e688ba7141",
              "orgLocation": [
                {
                  "type": "state",
                  "id": "027f81d8-0a2c-4fc6-96ac-59fe4cea3abf"
                },
                {
                  "type": "district",
                  "id": "8250d58d-f1a2-4397-bfd3-b2e688ba7141"
                }
              ],
              "externalId": 101010,
              "updatedDate": null,
              "userId": "96102c3f-2c22-4614-8dcc-6b130cefe586",
              "approvaldate": null,
              "isSchool": false,
              "isDeleted": false,
              "hashTagId": "0126796199493140480",
              "isRejected": null,
              "locations": [
                {
                  "code": 29,
                  "name": "state1",
                  "id": "027f81d8-0a2c-4fc6-96ac-59fe4cea3abf",
                  "type": "state",
                  "parentId": null
                },
                {
                  "code": 2901,
                  "name": "district1",
                  "id": "8250d58d-f1a2-4397-bfd3-b2e688ba7141",
                  "type": "district",
                  "parentId": "027f81d8-0a2c-4fc6-96ac-59fe4cea3abf"
                }
              ],
              "id": "01324864401294131212",
              "position": null,
              "isApproved": null,
              "orgjoindate": "2021-04-01 08:19:53:343+0000",
              "orgLeftDate": null
            },
            {
              "organisationId": "0127419693630996481321",
              "updatedBy": "96102c3f-2c22-4614-8dcc-6b130cefe586",
              "orgName": "org2",
              "addedByName": null,
              "addedBy": "96102c3f-2c22-4614-8dcc-6b130cefe586",
              "approvedBy": null,
              "channel": "tn",
              "locationIds": "91d9baae-14f1-477a-955c-f91bd9037f0b 107c9472-a950-4768-bcd6-f882910177c4 ba31e7c2-fac9-472a-8867-1582c73bcca8 5c8876b5-981c-4c6a-b23d-20c9e17428e1",
              "orgLocation": [
                {
                  "id": "91d9baae-14f1-477a-955c-f91bd9037f0b",
                  "type": "state"
                },
                {
                  "id": "107c9472-a950-4768-bcd6-f882910177c4",
                  "type": "district"
                },
                {
                  "id": "ba31e7c2-fac9-472a-8867-1582c73bcca8",
                  "type": "block"
                },
                {
                  "id": "5c8876b5-981c-4c6a-b23d-20c9e17428e1",
                  "type": "cluster"
                }
              ],
              "externalId": 33100800608,
              "updatedDate": "2021-04-07 05:09:38:366+0000",
              "userId": "96102c3f-2c22-4614-8dcc-6b130cefe586",
              "approvaldate": null,
              "isSchool": true,
              "isDeleted": false,
              "hashTagId": "0127419693630996481321",
              "isRejected": false,
              "locations": [
                {
                  "code": 31,
                  "name": "state2",
                  "id": "91d9baae-14f1-477a-955c-f91bd9037f0b",
                  "type": "state",
                  "parentId": null
                },
                {
                  "code": 3110,
                  "name": "district2",
                  "id": "107c9472-a950-4768-bcd6-f882910177c4",
                  "type": "district",
                  "parentId": "91d9baae-14f1-477a-955c-f91bd9037f0b"
                },
                {
                  "code": 31100169,
                  "name": "block1",
                  "id": "ba31e7c2-fac9-472a-8867-1582c73bcca8",
                  "type": "block",
                  "parentId": "107c9472-a950-4768-bcd6-f882910177c4"
                },
                {
                  "code": 3110016901,
                  "name": "block1 Cluster",
                  "id": "5c8876b5-981c-4c6a-b23d-20c9e17428e1",
                  "type": "cluster",
                  "parentId": "ba31e7c2-fac9-472a-8867-1582c73bcca8"
                }
              ],
              "id": "0132527931586969602",
              "position": null,
              "isApproved": false,
              "orgjoindate": "2021-04-07 05:09:45:655+0000",
              "orgLeftDate": "2021-04-07 05:09:38:366+0000"
            }
          ],
          "provider": null,
          "countryCode": null,
          "tncLatestVersionUrl": "https://organisation2.blob.core.windows.net/termsandcondtions/terms-and-conditions-v9.html#termsOfUse",
          "maskedEmail": "k1**@yopmail.com",
          "email": "k1**@yopmail.com",
          "rootOrg": {
            "dateTime": null,
            "preferredLanguage": null,
            "keys": null,
            "approvedBy": null,
            "channel": "channel1",
            "description": "org3",
            "updatedDate": "2021-03-31 17:31:19:346+0000",
            "addressId": null,
            "organisationType": 5,
            "orgType": null,
            "isTenant": true,
            "provider": null,
            "locationId": null,
            "orgCode": null,
            "theme": null,
            "id": "0126796199493140480",
            "communityId": null,
            "isApproved": null,
            "email": null,
            "slug": "channel1",
            "isSSOEnabled": null,
            "orgName": "org1",
            "updatedBy": null,
            "locationIds": "027f81d8-0a2c-4fc6-96ac-59fe4cea3abf 8250d58d-f1a2-4397-bfd3-b2e688ba7141",
            "externalId": 101010,
            "orgLocation": [
              {
                "type": "state",
                "id": "027f81d8-0a2c-4fc6-96ac-59fe4cea3abf"
              },
              {
                "type": "district",
                "id": "8250d58d-f1a2-4397-bfd3-b2e688ba7141"
              }
            ],
            "isRootOrg": true,
            "rootOrgId": "0126796199493140480",
            "approvedDate": null,
            "imgUrl": null,
            "homeUrl": null,
            "orgTypeId": null,
            "isDefault": null,
            "createdDate": "2019-01-18 09:48:13:428+0000",
            "createdBy": "system",
            "parentOrgId": null,
            "hashTagId": "0126796199493140480",
            "noOfMembers": null,
            "status": 1
          },
          "phoneVerified": false,
          "tcUpdatedDate": null,
          "userLocations": [
            {
              "code": 3110,
              "name": "district2",
              "id": "107c9472-a950-4768-bcd6-f882910177c4",
              "type": "district",
              "parentId": "91d9baae-14f1-477a-955c-f91bd9037f0b"
            },
            {
              "code": 3110016901,
              "name": "block1 Cluster",
              "id": "5c8876b5-981c-4c6a-b23d-20c9e17428e1",
              "type": "cluster",
              "parentId": "ba31e7c2-fac9-472a-8867-1582c73bcca8"
            },
            {
              "code": 31,
              "name": "state2",
              "id": "91d9baae-14f1-477a-955c-f91bd9037f0b",
              "type": "state",
              "parentId": null
            },
            {
              "code": 31100169,
              "name": "block1",
              "id": "ba31e7c2-fac9-472a-8867-1582c73bcca8",
              "type": "block",
              "parentId": "107c9472-a950-4768-bcd6-f882910177c4"
            },
            {
              "identifier": "2e4a420e-a6b8-4688-b12e-0e5f5141d175",
              "code": 31100800608,
              "name": "org2",
              "id": "2e4a420e-a6b8-4688-b12e-0e5f5141d175",
              "type": "school",
              "parentId": "5c8876b5-981c-4c6a-b23d-20c9e17428e1"
            }
          ],
          "recoveryPhone": null,
          "userName": "username 2",
          "userId": "96102c3f-2c22-4614-8dcc-6b130cefe586",
          "userSubType": null,
          "promptTnC": false,
          "emailVerified": true,
          "createdDate": "2021-04-01 08:19:50:971+0000",
          "framework": {
            "board": "State state3",
            "gradeLevel": "Class 1",
            "id": "ap_k-12_1",
            "medium": "English",
            "subject": "English"
          },
          "createdBy": null,
          "profileUserType": {
            "subType": null,
            "type": "student"
          },
          "profileUserTypes": [
            {
              "subType": null,
              "type": "student"
            }
          ],
          "tncAcceptedVersion": "3.5.0"
        }
      ]
    }
  }
}
```

</details>

\
[/api/course/v1/hierarchy/\{{content\_id\}}](http://docs.sunbird.org/latest/apis/coursehierarchyapi/index.html#operation/GetCourseHierarchy)\
API Method: **GET**

<details>

<summary>Sample Response Payload</summary>

```json
{
  "id": "api.course.hierarchy",
  "ver": 1,
  "ts": "2020-12-31T05:40:05.182Z",
  "params": {
    "resmsgid": "a27e2de0-4b2a-11eb-9b0c-abcfbdf41bc3",
    "msgid": "a27c5920-4b2a-11eb-9b0c-abcfbdf41bc3",
    "status": "successful",
    "err": null,
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "content": {
      "ownershipType": [
        "createdBy"
      ],
      "copyright": "Sunbird",
      "keywords": [
        "Traingle Inequality",
        "Perimeter"
      ],
      "channel": "b00bc992ef25f1a9a8d63291e20efc8d",
      "downloadUrl": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/ecar_files/do_1131680608828047361113/test-course-8-dec_1607429540479_do_1131680608828047361113_1.0_spine.ecar",
      "organisation": [
        "Sunbird"
      ],
      "language": [
        "English"
      ],
      "mimeType": "application/vnd.ekstep.content-collection",
      "variants": {
        "online": {
          "ecarUrl": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/ecar_files/do_1131680608828047361113/test-course-8-dec_1607429540833_do_1131680608828047361113_1.0_online.ecar",
          "size": 6598
        },
        "spine": {
          "ecarUrl": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/ecar_files/do_1131680608828047361113/test-course-8-dec_1607429540479_do_1131680608828047361113_1.0_spine.ecar",
          "size": 109650
        }
      },
      "leafNodes": [
        "do_1126972421999820801361",
        "do_1126972168312832001322",
        "do_112835336960000000152"
      ],
      "c_sunbird_dev_private_batch_count": 0,
      "objectType": "Content",
      "appIcon": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/content/do_1131680608828047361113/artifact/indian-home-as-per-vastu-1366x768.thumb.jpg",
      "children": [
        {
          "ownershipType": [
            "createdBy"
          ],
          "parent": "do_1131680608828047361113",
          "code": "92a1e47b-36d7-407c-9dbd-1d5277a58b1b",
          "credentials": {
            "enabled": "No"
          },
          "channel": "b00bc992ef25f1a9a8d63291e20efc8d",
          "language": [
            "English"
          ],
          "mimeType": "application/vnd.ekstep.content-collection",
          "idealScreenSize": "normal",
          "createdOn": "2020-12-08T12:12:03.749Z",
          "objectType": "Content",
          "primaryCategory": "Course Unit",
          "children": [
            {
              "ownershipType": [
                "createdBy"
              ],
              "copyright": "Sunbird",
              "previewUrl": "https://www.youtube.com/watch?v=dQxczxQmV_k",
              "subject": [
                "Math"
              ],
              "downloadUrl": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/ecar_files/do_112835336960000000152/basic-geometrical-ideas_1566813767133_do_112835336960000000152_1.0.ecar",
              "channel": "b00bc992ef25f1a9a8d63291e20efc8d",
              "questions": [],
              "organisation": [
                "Sunbird"
              ],
              "showNotification": true,
              "language": [
                "English"
              ],
              "variants": {
                "spine": {
                  "ecarUrl": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/ecar_files/do_112835336960000000152/basic-geometrical-ideas_1566813767294_do_112835336960000000152_1.0_spine.ecar",
                  "size": 38726
                }
              },
              "mimeType": "video/x-youtube",
              "apoc_text": "APOC",
              "gradeLevel": [
                "Grade 6"
              ],
              "appIcon": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/content/do_112835336960000000152/artifact/06_maths_book_1566813333849.thumb.jpg",
              "primaryCategory": "Explanation Content",
              "appId": "dev.sunbird.portal",
              "usesContent": [],
              "artifactUrl": "https://www.youtube.com/watch?v=dQxczxQmV_k",
              "contentEncoding": "identity",
              "me_totalPlaySessionCount": "{\"portal\":5}",
              "lockKey": "6ed43a33-b998-4df0-aac6-2b763c016c13",
              "contentType": "Resource",
              "apoc_num": 1,
              "lastUpdatedBy": "874ed8a5-782e-4f6c-8f36-e0288455901e",
              "identifier": "do_112835336960000000152",
              "audience": [
                "Student"
              ],
              "visibility": "Default",
              "author": "b00bc992ef25f1a9a8d63291e20efc8d",
              "consumerId": "4e525af6-2362-4edc-acf5-9ef9d3f72b3b",
              "mediaType": "content",
              "itemSets": [],
              "osId": "org.ekstep.quiz.app",
              "lastPublishedBy": "95e4942d-cbe8-477d-aebd-ad8e6de4bfc8",
              "version": 1,
              "pragma": [
                "external"
              ],
              "prevState": "Review",
              "license": "Standard YouTube License",
              "size": 38726,
              "lastPublishedOn": "2019-08-26T10:02:47.128Z",
              "concepts": [],
              "name": "Basic Geometrical ideas",
              "status": "Live",
              "code": "6a3b478c-0665-4069-b7a4-d93902e4c721",
              "apoc_json": "{\"batch\": true}",
              "methods": [],
              "streamingUrl": "https://www.youtube.com/watch?v=dQxczxQmV_k",
              "medium": [
                "English"
              ],
              "posterImage": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/content/do_112835334818643968148/artifact/06_maths_book_1566813333849.jpg",
              "idealScreenSize": "normal",
              "createdOn": "2019-08-26T09:59:53.750Z",
              "contentDisposition": "online",
              "lastUpdatedOn": "2019-08-26T10:02:46.685Z",
              "SYS_INTERNAL_LAST_UPDATED_ON": "2020-02-25T12:33:40.719Z",
              "dialcodeRequired": "No",
              "creator": "Creation",
              "lastStatusChangedOn": "2019-08-26T10:02:47.592Z",
              "createdFor": [
                "ORG_001"
              ],
              "os": [
                "All"
              ],
              "libraries": [],
              "pkgVersion": 1,
              "versionKey": 1566813766685,
              "me_totalTimeSpent": "{\"portal\":137}",
              "idealScreenDensity": "hdpi",
              "s3Key": "ecar_files/do_112835336960000000152/basic-geometrical-ideas_1566813767133_do_112835336960000000152_1.0.ecar",
              "framework": "NCFCOPY",
              "lastSubmittedOn": "2019-08-26T10:00:23.026Z",
              "createdBy": "874ed8a5-782e-4f6c-8f36-e0288455901e",
              "compatibilityLevel": 4,
              "board": "CBSE",
              "resourceType": "Learn",
              "index": 1,
              "depth": 2,
              "parent": "do_1131680626585518081116",
              "objectType": "Content"
            }
          ],
          "contentDisposition": "inline",
          "lastUpdatedOn": "2020-12-08T12:12:19.561Z",
          "contentEncoding": "gzip",
          "contentType": "CourseUnit",
          "dialcodeRequired": "No",
          "trackable": {
            "enabled": "No",
            "autoBatch": "No"
          },
          "identifier": "do_1131680626585518081116",
          "lastStatusChangedOn": "2020-12-08T12:12:03.749Z",
          "audience": [
            "Student"
          ],
          "os": [
            "All"
          ],
          "visibility": "Parent",
          "index": 1,
          "mediaType": "content",
          "osId": "org.ekstep.launcher",
          "languageCode": [
            "en"
          ],
          "version": 2,
          "versionKey": 1607429523749,
          "license": "CC BY 4.0",
          "idealScreenDensity": "hdpi",
          "framework": "NCFCOPY",
          "depth": 1,
          "compatibilityLevel": 1,
          "name": "Untitled Course Unit",
          "status": "Live",
          "lastPublishedOn": "2020-12-08T12:12:20.303Z",
          "pkgVersion": 1,
          "leafNodesCount": 1,
          "leafNodes": [
            "do_112835336960000000152"
          ],
          "downloadUrl": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/ecar_files/do_1131680608828047361113/test-course-8-dec_1607429540479_do_1131680608828047361113_1.0_spine.ecar",
          "variants": "{\"online\":{\"ecarUrl\":\"https://sunbirddev.blob.core.windows.net/sunbird-content-dev/ecar_files/do_1131680608828047361113/test-course-8-dec_1607429540833_do_1131680608828047361113_1.0_online.ecar\",\"size\":6598.0},\"spine\":{\"ecarUrl\":\"https://sunbirddev.blob.core.windows.net/sunbird-content-dev/ecar_files/do_1131680608828047361113/test-course-8-dec_1607429540479_do_1131680608828047361113_1.0_spine.ecar\",\"size\":109650.0}}"
        },
        {
          "ownershipType": [
            "createdBy"
          ],
          "parent": "do_1131680608828047361113",
          "copyright": "Sunbird",
          "code": "b409d492-97ec-484c-bcb1-a51bbae9c917",
          "credentials": {
            "enabled": "No"
          },
          "channel": "b00bc992ef25f1a9a8d63291e20efc8d",
          "language": [
            "English"
          ],
          "mimeType": "application/vnd.ekstep.content-collection",
          "idealScreenSize": "normal",
          "createdOn": "2020-12-08T12:12:03.748Z",
          "objectType": "Content",
          "primaryCategory": "Course Unit",
          "children": [
            {
              "ownershipType": [
                "createdFor"
              ],
              "previewUrl": "https://www.youtube.com/watch?v=BiagrTl2y4o",
              "keywords": [
                "Traingle Inequality"
              ],
              "subject": [
                "Mathematics"
              ],
              "downloadUrl": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/ecar_files/do_1126972168312832001322/traingle-inequality_1549953441448_do_1126972168312832001322_1.0.ecar",
              "channel": "b00bc992ef25f1a9a8d63291e20efc8d",
              "questions": [],
              "organisation": [
                "Sunbird",
                "QA ORG"
              ],
              "showNotification": true,
              "language": [
                "English"
              ],
              "variants": {
                "spine": {
                  "ecarUrl": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/ecar_files/do_1126972168312832001322/traingle-inequality_1549953441719_do_1126972168312832001322_1.0_spine.ecar",
                  "size": 17143
                }
              },
              "mimeType": "video/x-youtube",
              "apoc_text": "APOC",
              "appIcon": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/content/do_1126972168312832001322/artifact/math_1549943542752.thumb.jpg",
              "gradeLevel": [
                "Grade 3"
              ],
              "primaryCategory": "Explanation Content",
              "appId": "dev.sunbird.portal",
              "usesContent": [],
              "artifactUrl": "https://www.youtube.com/watch?v=BiagrTl2y4o",
              "contentEncoding": "identity",
              "lockKey": "9cb2c75d-6712-4829-853b-ce2a0714dca3",
              "contentType": "Resource",
              "apoc_num": 1,
              "lastUpdatedBy": "874ed8a5-782e-4f6c-8f36-e0288455901e",
              "identifier": "do_1126972168312832001322",
              "audience": [
                "Student"
              ],
              "visibility": "Default",
              "author": "b00bc992ef25f1a9a8d63291e20efc8d",
              "consumerId": "9393568c-3a56-47dd-a9a3-34da3c821638",
              "mediaType": "content",
              "itemSets": [],
              "osId": "org.ekstep.quiz.app",
              "lastPublishedBy": "95e4942d-cbe8-477d-aebd-ad8e6de4bfc8",
              "pragma": [
                "external"
              ],
              "prevState": "Review",
              "license": "Standard YouTube License",
              "lastPublishedOn": "2019-02-12T06:37:21.448Z",
              "size": 17141,
              "concepts": [],
              "name": "Traingle Inequality",
              "status": "Live",
              "code": "6aeb10a0-3333-4214-a834-ed98c32ab5eb",
              "apoc_json": "{\"batch\": true}",
              "methods": [],
              "streamingUrl": "https://www.youtube.com/watch?v=BiagrTl2y4o",
              "medium": [
                "English"
              ],
              "posterImage": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/content/do_1126971374955151361222/artifact/math_1549943542752.jpg",
              "idealScreenSize": "normal",
              "createdOn": "2019-02-12T06:33:46.475Z",
              "contentDisposition": "online",
              "lastUpdatedOn": "2019-02-12T06:37:20.761Z",
              "SYS_INTERNAL_LAST_UPDATED_ON": "2019-02-12T06:37:22.237Z",
              "dialcodeRequired": "No",
              "owner": "QA ORG",
              "creator": "Creation",
              "createdFor": [
                "ORG_001",
                "0123653943740170242"
              ],
              "os": [
                "All"
              ],
              "libraries": [],
              "pkgVersion": 1,
              "versionKey": 1549953440766,
              "idealScreenDensity": "hdpi",
              "s3Key": "ecar_files/do_1126972168312832001322/traingle-inequality_1549953441448_do_1126972168312832001322_1.0.ecar",
              "framework": "NCFCOPY",
              "lastSubmittedOn": "2019-02-12T06:34:32.580Z",
              "createdBy": "874ed8a5-782e-4f6c-8f36-e0288455901e",
              "compatibilityLevel": 4,
              "ownedBy": "0123653943740170242",
              "board": "CBSE",
              "resourceType": "Learn",
              "index": 1,
              "depth": 2,
              "parent": "do_1131680626585436161114",
              "objectType": "Content"
            }
          ],
          "contentDisposition": "inline",
          "lastUpdatedOn": "2020-12-08T12:12:19.561Z",
          "contentEncoding": "gzip",
          "contentType": "CourseUnit",
          "dialcodeRequired": "No",
          "trackable": {
            "enabled": "No",
            "autoBatch": "No"
          },
          "identifier": "do_1131680626585436161114",
          "lastStatusChangedOn": "2020-12-08T12:12:03.748Z",
          "audience": [
            "Student"
          ],
          "os": [
            "All"
          ],
          "visibility": "Parent",
          "index": 2,
          "mediaType": "content",
          "osId": "org.ekstep.launcher",
          "languageCode": [
            "en"
          ],
          "version": 2,
          "versionKey": 1607429523748,
          "license": "CC BY 4.0",
          "idealScreenDensity": "hdpi",
          "framework": "NCFCOPY",
          "depth": 1,
          "compatibilityLevel": 1,
          "name": "Untitled Course Unit",
          "status": "Live",
          "lastPublishedOn": "2020-12-08T12:12:20.303Z",
          "pkgVersion": 1,
          "leafNodesCount": 1,
          "leafNodes": [
            "do_1126972168312832001322"
          ],
          "downloadUrl": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/ecar_files/do_1131680608828047361113/test-course-8-dec_1607429540479_do_1131680608828047361113_1.0_spine.ecar",
          "variants": "{\"online\":{\"ecarUrl\":\"https://sunbirddev.blob.core.windows.net/sunbird-content-dev/ecar_files/do_1131680608828047361113/test-course-8-dec_1607429540833_do_1131680608828047361113_1.0_online.ecar\",\"size\":6598.0},\"spine\":{\"ecarUrl\":\"https://sunbirddev.blob.core.windows.net/sunbird-content-dev/ecar_files/do_1131680608828047361113/test-course-8-dec_1607429540479_do_1131680608828047361113_1.0_spine.ecar\",\"size\":109650.0}}"
        },
        {
          "ownershipType": [
            "createdBy"
          ],
          "parent": "do_1131680608828047361113",
          "copyright": "Sunbird",
          "code": "cbb27b2a-5e52-4e7e-b22a-e90e388b7a4d",
          "credentials": {
            "enabled": "No"
          },
          "channel": "b00bc992ef25f1a9a8d63291e20efc8d",
          "language": [
            "English"
          ],
          "mimeType": "application/vnd.ekstep.content-collection",
          "idealScreenSize": "normal",
          "createdOn": "2020-12-08T12:12:03.750Z",
          "objectType": "Content",
          "primaryCategory": "Course Unit",
          "children": [
            {
              "ownershipType": [
                "createdFor"
              ],
              "previewUrl": "https://www.youtube.com/watch?v=JAy_CETEyUM",
              "keywords": [
                "Perimeter"
              ],
              "subject": [
                "Mathematics"
              ],
              "downloadUrl": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/ecar_files/do_1126972421999820801361/perimeter_1549956428598_do_1126972421999820801361_1.0.ecar",
              "channel": "b00bc992ef25f1a9a8d63291e20efc8d",
              "questions": [],
              "organisation": [
                "Sunbird",
                "QA ORG"
              ],
              "showNotification": true,
              "language": [
                "English"
              ],
              "variants": {
                "spine": {
                  "ecarUrl": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/ecar_files/do_1126972421999820801361/perimeter_1549956428849_do_1126972421999820801361_1.0_spine.ecar",
                  "size": 17132
                }
              },
              "mimeType": "video/x-youtube",
              "apoc_text": "APOC",
              "appIcon": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/content/do_1126972421999820801361/artifact/math_1549943542752.thumb.jpg",
              "gradeLevel": [
                "Grade 7"
              ],
              "primaryCategory": "Explanation Content",
              "appId": "dev.sunbird.portal",
              "usesContent": [],
              "artifactUrl": "https://www.youtube.com/watch?v=JAy_CETEyUM",
              "contentEncoding": "identity",
              "lockKey": "a16c52b4-35c3-473b-a678-fedf12ef8dcc",
              "contentType": "Resource",
              "apoc_num": 1,
              "lastUpdatedBy": "874ed8a5-782e-4f6c-8f36-e0288455901e",
              "identifier": "do_1126972421999820801361",
              "audience": [
                "Student"
              ],
              "visibility": "Default",
              "author": "b00bc992ef25f1a9a8d63291e20efc8d",
              "consumerId": "9393568c-3a56-47dd-a9a3-34da3c821638",
              "mediaType": "content",
              "itemSets": [],
              "osId": "org.ekstep.quiz.app",
              "lastPublishedBy": "95e4942d-cbe8-477d-aebd-ad8e6de4bfc8",
              "pragma": [
                "external"
              ],
              "prevState": "Review",
              "license": "Standard YouTube License",
              "size": 17132,
              "lastPublishedOn": "2019-02-12T07:27:08.597Z",
              "concepts": [],
              "name": "Perimeter",
              "status": "Live",
              "code": "ad588332-34e1-4b49-a419-9226980bd19c",
              "apoc_json": "{\"batch\": true}",
              "methods": [],
              "streamingUrl": "https://www.youtube.com/watch?v=JAy_CETEyUM",
              "medium": [
                "English"
              ],
              "posterImage": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/content/do_1126971374955151361222/artifact/math_1549943542752.jpg",
              "idealScreenSize": "normal",
              "createdOn": "2019-02-12T07:25:23.239Z",
              "contentDisposition": "online",
              "lastUpdatedOn": "2019-02-12T07:27:07.975Z",
              "SYS_INTERNAL_LAST_UPDATED_ON": "2019-02-12T07:27:09.330Z",
              "dialcodeRequired": "No",
              "owner": "QA ORG",
              "creator": "Creation",
              "createdFor": [
                "ORG_001",
                "0123653943740170242"
              ],
              "os": [
                "All"
              ],
              "libraries": [],
              "pkgVersion": 1,
              "versionKey": 1549956427975,
              "idealScreenDensity": "hdpi",
              "s3Key": "ecar_files/do_1126972421999820801361/perimeter_1549956428598_do_1126972421999820801361_1.0.ecar",
              "framework": "NCFCOPY",
              "lastSubmittedOn": "2019-02-12T07:25:59.766Z",
              "createdBy": "874ed8a5-782e-4f6c-8f36-e0288455901e",
              "compatibilityLevel": 4,
              "ownedBy": "0123653943740170242",
              "board": "CBSE",
              "resourceType": "Learn",
              "index": 1,
              "depth": 2,
              "parent": "do_1131680626585600001118",
              "objectType": "Content"
            }
          ],
          "contentDisposition": "inline",
          "lastUpdatedOn": "2020-12-08T12:12:19.561Z",
          "contentEncoding": "gzip",
          "contentType": "CourseUnit",
          "dialcodeRequired": "No",
          "trackable": {
            "enabled": "No",
            "autoBatch": "No"
          },
          "identifier": "do_1131680626585600001118",
          "lastStatusChangedOn": "2020-12-08T12:12:03.750Z",
          "audience": [
            "Student"
          ],
          "os": [
            "All"
          ],
          "visibility": "Parent",
          "index": 3,
          "mediaType": "content",
          "osId": "org.ekstep.launcher",
          "languageCode": [
            "en"
          ],
          "version": 2,
          "versionKey": 1607429523750,
          "license": "CC BY 4.0",
          "idealScreenDensity": "hdpi",
          "framework": "NCFCOPY",
          "depth": 1,
          "compatibilityLevel": 1,
          "name": "Untitled Course Unit",
          "status": "Live",
          "lastPublishedOn": "2020-12-08T12:12:20.303Z",
          "pkgVersion": 1,
          "leafNodesCount": 1,
          "leafNodes": [
            "do_1126972421999820801361"
          ],
          "downloadUrl": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/ecar_files/do_1131680608828047361113/test-course-8-dec_1607429540479_do_1131680608828047361113_1.0_spine.ecar",
          "variants": "{\"online\":{\"ecarUrl\":\"https://sunbirddev.blob.core.windows.net/sunbird-content-dev/ecar_files/do_1131680608828047361113/test-course-8-dec_1607429540833_do_1131680608828047361113_1.0_online.ecar\",\"size\":6598.0},\"spine\":{\"ecarUrl\":\"https://sunbirddev.blob.core.windows.net/sunbird-content-dev/ecar_files/do_1131680608828047361113/test-course-8-dec_1607429540479_do_1131680608828047361113_1.0_spine.ecar\",\"size\":109650.0}}"
        }
      ],
      "primaryCategory": "Course",
      "appId": "dev.dock.portal",
      "contentEncoding": "gzip",
      "collaborators": [
        "8454cb21-3ce9-4e30-85b5-fade097880d8"
      ],
      "lockKey": "d5b2627c-1aea-479b-8970-ad2af62eba58",
      "totalCompressedSize": 72999,
      "mimeTypesCount": "{\"application/vnd.ekstep.content-collection\":3,\"video/x-youtube\":3}",
      "contentType": "Course",
      "contentCredits": [
        {
          "id": "0123653943740170242",
          "name": "QA ORG",
          "type": "user"
        }
      ],
      "trackable": {
        "enabled": "Yes",
        "autoBatch": "Yes"
      },
      "identifier": "do_1131680608828047361113",
      "lastUpdatedBy": "8454cb21-3ce9-4e30-85b5-fade097880d8",
      "audience": [
        "Student"
      ],
      "toc_url": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/content/do_1131680608828047361113/artifact/do_1131680608828047361113_toc.json",
      "visibility": "Default",
      "contentTypesCount": "{\"CourseUnit\":3,\"Resource\":3}",
      "consumerId": "273f3b18-5dda-4a27-984a-060c7cd398d3",
      "childNodes": [
        "do_1131680626585600001118",
        "do_1126972421999820801361",
        "do_1126972168312832001322",
        "do_112835336960000000152",
        "do_1131680626585518081116",
        "do_1131680626585436161114"
      ],
      "mediaType": "content",
      "osId": "org.ekstep.quiz.app",
      "lastPublishedBy": "Ekstep",
      "version": 2,
      "license": "CC BY 4.0",
      "prevState": "Draft",
      "size": 109650,
      "lastPublishedOn": "2020-12-08T12:12:20.303Z",
      "name": "Test Course - 8 Dec",
      "status": "Live",
      "code": "org.sunbird.F9fB1d",
      "credentials": {
        "enabled": "Yes"
      },
      "prevStatus": "Processing",
      "description": "Enter description for Course",
      "posterImage": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/content/do_113115644844154880184/artifact/indian-home-as-per-vastu-1366x768.jpg",
      "idealScreenSize": "normal",
      "createdOn": "2020-12-08T12:08:26.985Z",
      "batches": [
        {
          "createdFor": [
            "ORG_001"
          ],
          "endDate": null,
          "name": "Test Course - 8 Dec",
          "batchId": "0131680642631516160",
          "enrollmentType": "open",
          "enrollmentEndDate": null,
          "startDate": "2020-12-08T00:00:00.000Z",
          "status": 1
        },
        {
          "createdFor": [],
          "endDate": "2021-12-30T00:00:00.000Z",
          "name": "test cert scalability",
          "batchId": "0131680712715878401",
          "enrollmentType": "open",
          "enrollmentEndDate": "2021-12-29T00:00:00.000Z",
          "startDate": "2020-12-08T00:00:00.000Z",
          "status": 1
        }
      ],
      "copyrightYear": 2020,
      "contentDisposition": "inline",
      "lastUpdatedOn": "2020-12-08T12:12:19.561Z",
      "SYS_INTERNAL_LAST_UPDATED_ON": "2020-12-08T12:12:21.180Z",
      "dialcodeRequired": "No",
      "lastStatusChangedOn": "2020-12-08T12:12:21.173Z",
      "createdFor": [
        "ORG_001"
      ],
      "creator": "Mentor First User",
      "os": [
        "All"
      ],
      "pkgVersion": 1,
      "versionKey": 1607429539561,
      "idealScreenDensity": "hdpi",
      "framework": "NCFCOPY",
      "depth": 0,
      "s3Key": "ecar_files/do_1131680608828047361113/test-course-8-dec_1607429540479_do_1131680608828047361113_1.0_spine.ecar",
      "createdBy": "8454cb21-3ce9-4e30-85b5-fade097880d8",
      "compatibilityLevel": 4,
      "leafNodesCount": 3,
      "userConsent": "Yes",
      "board": "NCERT",
      "resourceType": "Course",
      "c_sunbird_dev_open_batch_count": 2
    }
  }
}
```

</details>
{% endtab %}

{% tab title="Sunbird Knowledge -Content Service" %}
There is a dependency with Content Service to fetch the activities that need to be added to the group. Activity types are configurable in activityConfig.json. Other services can be plugged in here to fetch activities from different sources...

**Dependency API:**\
\
[/api/content/v1/read/\{{userId\}}](https://documenter.getpostman.com/view/25463377/2s935hRnae#0b46ef2d-7a2a-4e46-ad22-b96295ac170a)\
API Method: **GET**

<details>

<summary>Sample Response Payload</summary>

```json
{
  "id": "api.content.read",
  "ver": "1.0",
  "ts": "2020-12-10T20:38:32.510Z",
  "params": {
    "resmsgid": "ab16e5e0-3b27-11eb-b0a2-8d5c9f561887",
    "msgid": "ab131550-3b27-11eb-b0a2-8d5c9f561887",
    "status": "successful",
    "err": null,
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "content": {
      "ownershipType": [
        "createdBy"
      ],
      "code": "org.sunbird.EHdZir",
      "credentials": {
        "enabled": "No"
      },
      "channel": "channel-1",
      "language": [
        "English"
      ],
      "mimeType": "application/vnd.ekstep.h5p-archive",
      "idealScreenSize": "normal",
      "createdOn": "2020-12-10T20:38:13.315+0000",
      "objectType": "Content",
      "primaryCategory": "Learning Resource",
      "contentDisposition": "inline",
      "lastUpdatedOn": "2020-12-10T20:38:13.315+0000",
      "contentEncoding": "gzip",
      "dialcodeRequired": "No",
      "trackable": {
        "enabled": "No",
        "autoBatch": "No"
      },
      "identifier": "do_21316972702362828813477",
      "lastStatusChangedOn": "2020-12-10T20:38:13.315+0000",
      "audience": [
        "Student"
      ],
      "os": [
        "All"
      ],
      "visibility": "Default",
      "consumerId": "2eaff3db-cdd1-42e5-a611-bebbf906e6cf",
      "mediaType": "content",
      "osId": "org.ekstep.quiz.app",
      "languageCode": [
        "en"
      ],
      "version": 2,
      "versionKey": "1607632693315",
      "license": "CC BY 4.0",
      "idealScreenDensity": "hdpi",
      "framework": "NCF",
      "createdBy": "874ed8a5-782e-4f6c-8f36-e0288455901e",
      "compatibilityLevel": 1,
      "name": "Test_h5p",
      "status": "Draft"
    }
  }
}
```

</details>
{% endtab %}

{% tab title="Discussion Forum" %}
There is a  dependency with the discussion service as to get the forum is enabled for this group or not.\
\
**Dependency API:**\
\
[/discussion/forum/v2/read](http://docs.sunbird.org/latest/apis/discussionForum/#tag/Forum)\
API Method: **POST**

<details>

<summary>Sample Request Payload</summary>

```json
{
  "request": {
    "type": "course",
    "identifier": "do_12345678996312"
  }
}
```

</details>

<details>

<summary>Sample Response Payload</summary>

```json
[
  {
    "identifier": "identifier",
    "type": "type",
    "cid": 0
  }
]
```

</details>
{% endtab %}
{% endtabs %}

### References:

[User and Groups in Schooling@Home](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/1416200208/User+and+Groups+in+Schooling+Home)

[\[Design\] Groups as NPM module](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/2956099585)
