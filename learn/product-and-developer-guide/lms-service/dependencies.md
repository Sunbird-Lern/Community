# Dependencies

{% tabs %}
{% tab title="Sunbird Knowlg : Content service" %}
There is a dependency with Content Service to read the course metadata by using the API calls.\
\
**Dependency API:**\
[/content/v3/read](https://documenter.getpostman.com/view/25463377/2s935hRnae#0b46ef2d-7a2a-4e46-ad22-b96295ac170a)\
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

[/content/v3/search](https://documenter.getpostman.com/view/25463377/2s935hRnae#53a9e9d0-eb1a-4136-9b82-8d0f36c74b9b)\
API Method: **POST**

<details>

<summary>Sample Request Payload</summary>

```json
{
  "request": {
    "filters": {
      "objectType": "Content",
      "status": []
    },
    "limit": 1
  }
}
```

</details>

<details>

<summary>Sample Response Payload</summary>

```json
{
  "id": "api.content.search",
  "ver": "1.0",
  "ts": "2020-12-22T06:24:45.025Z",
  "params": {
    "resmsgid": "62160510-441e-11eb-9b0c-abcfbdf41bc3",
    "msgid": "620ae180-441e-11eb-9b0c-abcfbdf41bc3",
    "status": "successful",
    "err": null,
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "count": 480465,
    "content": [
      {
        "code": "org.ekstep.jun16.story.test05",
        "subject": [
          "literacy"
        ],
        "flags": [
          "Test case"
        ],
        "channel": "in.ekstep",
        "downloadUrl": "https://ekstep-public-dev.s3-ap-south-1.amazonaws.com/ecar_files/org.ekstep.jun16.story.test05/vrgaatiil-upkrmclassroom-activities_1498725323304_org.ekstep.jun16.story.test05_1.0.ecar",
        "description": "शेर का साथी हाथी",
        "lastFlaggedOn": "2017-12-27T13:30:48.942+0000",
        "language": [
          "English"
        ],
        "variants": {
          "spine": {
            "ecarUrl": "https://ekstep-public-dev.s3-ap-south-1.amazonaws.com/ecar_files/org.ekstep.jun16.story.test05/vrgaatiil-upkrmclassroom-activities_1498725324677_org.ekstep.jun16.story.test05_1.0_spine.ecar",
            "size": 851
          }
        },
        "mimeType": "application/vnd.ekstep.ecml-archive",
        "flaggedBy": [
          "Test case"
        ],
        "idealScreenSize": "normal",
        "createdOn": "2017-06-29T07:44:15.875+0000",
        "objectType": "Content",
        "collections": [
          "do_11228062262625075214"
        ],
        "appId": "ekstep_portal",
        "contentDisposition": "inline",
        "contentEncoding": "gzip",
        "artifactUrl": "https://ekstep-public-dev.s3-ap-south-1.amazonaws.com/content/org.ekstep.jun16.story.test05/artifact/1485166711340_do_30102464_1498725273215.zip",
        "lastUpdatedOn": "2017-12-27T13:30:48.968+0000",
        "SYS_INTERNAL_LAST_UPDATED_ON": "2018-01-09T18:41:32.368+0000",
        "primaryCategory": "Story",
        "owner": "EkStep",
        "lastUpdatedBy": "Test case",
        "identifier": "org.ekstep.jun16.story.test05",
        "audience": [
          "Learner"
        ],
        "flagReasons": [
          "Copyright Violation"
        ],
        "visibility": "default",
        "os": [
          "All"
        ],
        "consumerId": "72e54829-6402-4cf0-888e-9b30733c1b88",
        "mediaType": "content",
        "osId": "org.ekstep.quiz.app",
        "graph_id": "domain",
        "nodeType": "DATA_NODE",
        "pkgVersion": 1,
        "versionKey": "1515523292368",
        "prevState": "Draft",
        "idealScreenDensity": "hdpi",
        "dialcodes": [
          "DAKDF",
          "FSDFDSA"
        ],
        "s3Key": "ecar_files/org.ekstep.jun16.story.test05/vrgaatiil-upkrmclassroom-activities_1498725323304_org.ekstep.jun16.story.test05_1.0.ecar",
        "size": 9983654,
        "lastPublishedOn": "2017-06-29T08:35:23.302+0000",
        "compatibilityLevel": 1,
        "name": "\tवर्गातील उपक्रम(Classroom Activities)",
        "resourceType": "Story",
        "status": "Flagged",
        "node_id": 105761
      }
    ]
  }
}
```

</details>

\
[/content/v3/hierarchy/](https://documenter.getpostman.com/view/25463377/2s8ZDa32au#5d9279c0-6002-4b52-b62e-12d767c59d2a)\
API Method: **GET**

<details>

<summary>Sample Response Payload</summary>

```json
{
  "id": "api.collection.hierarchy.get",
  "ver": "4.0",
  "ts": "2022-01-04T12:28:17ZZ",
  "params": {
    "resmsgid": "0541c308-4754-4b0c-8e0e-47467c3cc35c",
    "status": "successful"
  },
  "responseCode": "OK",
  "result": {
    "content": {
      "ownershipType": [
        "createdBy"
      ],
      "copyright": "NIT123",
      "keywords": [
        "Collection Test"
      ],
      "subject": [
        "Mathematics"
      ],
      "channel": "sunbird",
      "organisation": [
        "NIT"
      ],
      "language": [
        "English"
      ],
      "mimeType": "application/vnd.ekstep.content-collection",
      "objectType": "Collection",
      "chapterCountForContribution": 1,
      "gradeLevel": [
        "Class 1"
      ],
      "appIcon": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/content/do_11293020669537484811928/artifact/001_1578394365141.png",
      "primaryCategory": "Digital Textbook",
      "children": [
        {
          "ownershipType": [
            "createdBy"
          ],
          "parent": "do_1134445959309803521184",
          "code": "do_1132167447297474561289",
          "credentials": {
            "enabled": false
          },
          "origin": "do_1132167447297474561289",
          "channel": "sunbird",
          "language": [
            "English"
          ],
          "mimeType": "application/vnd.ekstep.content-collection",
          "idealScreenSize": "normal",
          "createdOn": "2022-01-03T05:00:26.831+0000",
          "objectType": "Content",
          "primaryCategory": "Content Playlist",
          "children": [
            {
              "ownershipType": [
                "createdBy"
              ],
              "parent": "do_1134445959317995521185",
              "code": "do_113333485887143936169",
              "credentials": {
                "enabled": false
              },
              "origin": "do_113333485887143936169",
              "channel": "sunbird",
              "language": [
                "English"
              ],
              "mimeType": "application/vnd.ekstep.content-collection",
              "idealScreenSize": "normal",
              "createdOn": "2022-01-03T05:00:26.834+0000",
              "objectType": "Content",
              "primaryCategory": "Textbook Unit",
              "contentDisposition": "inline",
              "lastUpdatedOn": "2022-01-03T05:00:26.834+0000",
              "contentEncoding": "gzip",
              "originData": {
                "channel": 1309282781705830400
              },
              "generateDIALCodes": false,
              "contentType": "TextBookUnit",
              "dialcodeRequired": false,
              "identifier": "do_1134445959318241281187",
              "lastStatusChangedOn": "2022-01-03T05:00:26.834+0000",
              "audience": [
                "Student"
              ],
              "os": [
                "All"
              ],
              "visibility": "Parent",
              "discussionForum": {
                "enabled": true
              },
              "index": 1,
              "mediaType": "content",
              "osId": "org.ekstep.launcher",
              "languageCode": [
                "en"
              ],
              "version": 2,
              "versionKey": "1641186026834",
              "allowedContentTypes": [
                "Demo Practice Question Set",
                "Content Playlist",
                "Course Assessment",
                "eTextbook",
                "Explanation Content",
                "Learning Resource",
                "Practice Question Set",
                "Teacher Resource"
              ],
              "license": "CC BY 4.0",
              "idealScreenDensity": "hdpi",
              "depth": 2,
              "compatibilityLevel": 1,
              "name": "Part 1",
              "openForContribution": true,
              "timeLimits": {},
              "programId": "fae8bbf0-6c51-11ec-ad7a-853bd8da76ad",
              "status": "Draft",
              "children": [
                {
                  "ownershipType": [
                    "createdBy"
                  ],
                  "unitIdentifiers": [
                    "do_1134445959318241281187"
                  ],
                  "parent": "do_1134445959318241281187",
                  "subject": [
                    "Mathematics"
                  ],
                  "channel": 1309282781705830400,
                  "language": [
                    "English"
                  ],
                  "mimeType": "application/pdf",
                  "objectType": "Content",
                  "gradeLevel": [
                    "Class 1"
                  ],
                  "primaryCategory": "eTextbook",
                  "contentEncoding": "identity",
                  "contentType": "eTextBook",
                  "identifier": "do_1134453165632552961201",
                  "audience": [
                    "Student"
                  ],
                  "subjectIds": [
                    "ekstep_ncert_k-12_subject_mathematics"
                  ],
                  "visibility": "Default",
                  "author": "anusha",
                  "index": 1,
                  "mediaType": "content",
                  "osId": "org.ekstep.quiz.app",
                  "languageCode": [
                    "en"
                  ],
                  "version": 2,
                  "license": "CC BY 4.0",
                  "name": "Untitled",
                  "mediumIds": [
                    "ekstep_ncert_k-12_medium_english"
                  ],
                  "status": "Draft",
                  "code": "b1ef1747-b33a-d91a-93f0-7a0064f1f802",
                  "interceptionPoints": {},
                  "credentials": {
                    "enabled": false
                  },
                  "medium": [
                    "English"
                  ],
                  "idealScreenSize": "normal",
                  "createdOn": "2022-01-04T05:26:34.539+0000",
                  "contentDisposition": "inline",
                  "lastUpdatedOn": "2022-01-04T05:26:34.989+0000",
                  "collectionId": "do_1134445959309803521184",
                  "dialcodeRequired": false,
                  "lastStatusChangedOn": "2022-01-04T05:26:34.539+0000",
                  "creator": "anusha",
                  "os": [
                    "All"
                  ],
                  "versionKey": "1641273994989",
                  "idealScreenDensity": "hdpi",
                  "framework": "ekstep_ncert_k-12",
                  "boardIds": [
                    "ekstep_ncert_k-12_board_cbse"
                  ],
                  "depth": 3,
                  "createdBy": "19ba0e4e-9285-4335-8dd0-f674bf03fa4d",
                  "compatibilityLevel": 1,
                  "gradeLevelIds": [
                    "ekstep_ncert_k-12_gradelevel_class1"
                  ],
                  "board": "CBSE",
                  "programId": "fae8bbf0-6c51-11ec-ad7a-853bd8da76ad",
                  "downloadUrl": "https://dockstorage.blob.core.windows.net/sunbird-content-dock/content/assets/do_1134453165632552961201/sample.pdf",
                  "artifactUrl": "https://dockstorage.blob.core.windows.net/sunbird-content-dock/content/assets/do_1134453165632552961201/sample.pdf",
                  "size": 3028
                },
                {
                  "ownershipType": [
                    "createdBy"
                  ],
                  "unitIdentifiers": [
                    "do_1134445959318241281187"
                  ],
                  "parent": "do_1134445959318241281187",
                  "copyright": "2021",
                  "subject": [
                    "Mathematics"
                  ],
                  "channel": 1309282781705830400,
                  "downloadUrl": "https://dockstorage.blob.core.windows.net/sunbird-content-dock/content/assets/do_1134455063866736641416/sample.pdf",
                  "language": [
                    "English"
                  ],
                  "mimeType": "application/pdf",
                  "objectType": "Content",
                  "gradeLevel": [
                    "Class 1"
                  ],
                  "primaryCategory": "eTextbook",
                  "contentEncoding": "identity",
                  "artifactUrl": "https://dockstorage.blob.core.windows.net/sunbird-content-dock/content/assets/do_1134455063866736641416/sample.pdf",
                  "contentType": "eTextBook",
                  "identifier": "do_1134455063866736641416",
                  "audience": [
                    "Student"
                  ],
                  "subjectIds": [
                    "ekstep_ncert_k-12_subject_mathematics"
                  ],
                  "visibility": "Default",
                  "author": "anusha",
                  "index": 2,
                  "mediaType": "content",
                  "osId": "org.ekstep.quiz.app",
                  "languageCode": [
                    "en"
                  ],
                  "version": 2,
                  "license": "CC BY 4.0",
                  "size": 3028,
                  "name": "test content",
                  "mediumIds": [
                    "ekstep_ncert_k-12_medium_english"
                  ],
                  "status": "Draft",
                  "code": "9ab1557b-ea67-c31b-be52-e4073c5d8f1b",
                  "interceptionPoints": {},
                  "credentials": {
                    "enabled": false
                  },
                  "medium": [
                    "English"
                  ],
                  "idealScreenSize": "normal",
                  "createdOn": "2022-01-04T11:52:46.343+0000",
                  "contentDisposition": "inline",
                  "lastUpdatedOn": "2022-01-04T11:53:13.077+0000",
                  "collectionId": "do_1134445959309803521184",
                  "dialcodeRequired": false,
                  "lastStatusChangedOn": "2022-01-04T11:52:46.343+0000",
                  "creator": "anusha",
                  "os": [
                    "All"
                  ],
                  "versionKey": "1641297193077",
                  "idealScreenDensity": "hdpi",
                  "framework": "ekstep_ncert_k-12",
                  "boardIds": [
                    "ekstep_ncert_k-12_board_cbse"
                  ],
                  "depth": 3,
                  "createdBy": "19ba0e4e-9285-4335-8dd0-f674bf03fa4d",
                  "compatibilityLevel": 1,
                  "gradeLevelIds": [
                    "ekstep_ncert_k-12_gradelevel_class1"
                  ],
                  "board": "CBSE",
                  "programId": "fae8bbf0-6c51-11ec-ad7a-853bd8da76ad"
                }
              ]
            }
          ],
          "contentDisposition": "inline",
          "lastUpdatedOn": "2022-01-03T05:00:26.831+0000",
          "contentEncoding": "gzip",
          "originData": {
            "channel": 1309282781705830400
          },
          "contentType": "Collection",
          "dialcodeRequired": false,
          "trackable": {
            "enabled": false,
            "autoBatch": false
          },
          "identifier": "do_1134445959317995521185",
          "lastStatusChangedOn": "2022-01-03T05:00:26.831+0000",
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
          "versionKey": "1641186026831",
          "allowedContentTypes": [
            "Demo Practice Question Set",
            "Content Playlist",
            "Course Assessment",
            "eTextbook",
            "Explanation Content",
            "Learning Resource",
            "Practice Question Set",
            "Teacher Resource"
          ],
          "license": "CC BY 4.0",
          "idealScreenDensity": "hdpi",
          "depth": 1,
          "compatibilityLevel": 1,
          "name": "Textbook Unit 1",
          "openForContribution": true,
          "timeLimits": {},
          "programId": "fae8bbf0-6c51-11ec-ad7a-853bd8da76ad",
          "status": "Draft"
        }
      ],
      "contentEncoding": "gzip",
      "collaborators": [
        "88ffb6eb-33bf-4f96-ad3a-75c15e5a04ff",
        "a4b4a783-d686-4f67-b079-512329c77f5e",
        "ce7f4172-f13a-47b7-804d-f194a2275538"
      ],
      "contentType": "Collection",
      "trackable": {
        "enabled": false,
        "autoBatch": false
      },
      "identifier": "do_1134445959309803521184",
      "audience": [
        "Student"
      ],
      "subjectIds": [
        "ekstep_ncert_k-12_subject_mathematics"
      ],
      "visibility": "Default",
      "consumerId": "028d6fb1-2d6f-4331-86aa-f7cf491a41e0",
      "childNodes": [
        "do_1134445959318241281187",
        "do_1134445959317995521185",
        "do_1134453165632552961201",
        "do_1134455063866736641416"
      ],
      "mediaType": "content",
      "osId": "org.ekstep.quiz.app",
      "languageCode": [
        "en"
      ],
      "version": 2,
      "allowedContentTypes": [
        "Demo Practice Question Set",
        "Content Playlist",
        "Course Assessment",
        "eTextbook",
        "Explanation Content",
        "Learning Resource",
        "Practice Question Set",
        "Teacher Resource"
      ],
      "license": "CC BY 4.0",
      "name": "Collection Test",
      "mediumIds": [
        "ekstep_ncert_k-12_medium_english"
      ],
      "attributions": [
        "Collection Test"
      ],
      "status": "Draft",
      "code": "do_1132167446143959041288",
      "credentials": {
        "enabled": false
      },
      "origin": "do_1132167446143959041288",
      "description": "Enter description for Collection",
      "medium": [
        "English"
      ],
      "idealScreenSize": "normal",
      "createdOn": "2022-01-03T05:00:26.734+0000",
      "copyrightYear": 2021,
      "contentDisposition": "inline",
      "additionalCategories": [
        "Textbook"
      ],
      "lastUpdatedOn": "2022-01-04T11:54:05.627+0000",
      "originData": {
        "channel": 1309282781705830400
      },
      "dialcodeRequired": false,
      "lastStatusChangedOn": "2022-01-03T05:00:26.734+0000",
      "createdFor": [
        1309282781705830400
      ],
      "creator": "N11",
      "os": [
        "All"
      ],
      "chapterCount": 1,
      "versionKey": "1641297245627",
      "idealScreenDensity": "hdpi",
      "framework": "ekstep_ncert_k-12",
      "depth": 0,
      "boardIds": [
        "ekstep_ncert_k-12_board_cbse"
      ],
      "createdBy": "5a587cc1-e018-4859-a0a8-e842650b9d64",
      "compatibilityLevel": 1,
      "userConsent": true,
      "openForContribution": true,
      "timeLimits": "{}",
      "gradeLevelIds": [
        "ekstep_ncert_k-12_gradelevel_class1"
      ],
      "board": "CBSE",
      "programId": "fae8bbf0-6c51-11ec-ad7a-853bd8da76ad",
      "resourceType": "Collection"
    }
  }
}
```

</details>

\
\
[/content/v3/publish\
](https://documenter.getpostman.com/view/25463377/2s935hRnae#ad1a1dee-3d98-4c63-bb15-8063dd445235)API Method: **GET**

<details>

<summary>Sample Response Payload</summary>

```json
{
  "id": "api.v3.publish",
  "ver": "1.0",
  "ts": "2020-12-10T21:41:23.491Z",
  "params": {
    "resmsgid": "72c4ef30-3b30-11eb-b0a2-8d5c9f561887",
    "msgid": "72979da0-3b30-11eb-b0a2-8d5c9f561887",
    "status": "successful",
    "err": null,
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "content_id": "do_21316975736724684813479",
    "publishStatus": "Publish Operation for Content Id 'do_21316975736724684813479' Started Successfully!"
  }
}
```

</details>

[/system/v3/content/update/\
](https://documenter.getpostman.com/view/25463377/2s935hRnae#4b7e384c-4e99-433f-ae85-725268a31d09)API Method: **PATCH**

<details>

<summary>Sample Request Payload</summary>

```json
{
  "request": {
    "content": {
      "versionKey": "1607631400608",
      "description": "Updated description"
    }
  }
}
```

</details>

<details>

<summary>Sample Response Payload</summary>

```json
{
  "id": "api.content.update",
  "ver": "4.0",
  "ts": "2020-12-10T20:26:07ZZ",
  "params": {
    "resmsgid": "80aa9310-b749-411c-a13b-8d9f25af389f",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "identifier": "do_1131697204035993601314",
    "node_id": "do_1131697204035993601314",
    "versionKey": "1607631967842"
  }
}
```

</details>

\

{% endtab %}

{% tab title="Sunbird Knowlg : Search service" %}
There is a dependency with Search Service in order to perform a composite search by using the **search** API call. Search will be performed on the Elastic Search database.\
\
**Dependency API:**\
\
[composite/v3/search\
](https://documenter.getpostman.com/view/25463377/2s8ZDa3MP7)API Method: **POST**

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
  "request": {
    "filters": {
      "objectType": "Content",
      "status": []
    },
    "limit": 1
  }
}
```

</details>


{% endtab %}

{% tab title="Sunbird Inquiry" %}
There is a dependency with Inquiry for fetching the metadata of QuestionSet. There is a dependency with Content Service to read the course metadata by using the API calls.\
There is a dependency with Content Service to read the course metadata by using the API calls.\

{% endtab %}

{% tab title="Sunbird Lern : User&Org Service" %}
There is a dependency with User and Org Service to fetch user information for validating the Batch creator and Mentor (**user/v1/read**)\
\
**Dependency API:**\
API Method: **GET**

[user/v1/read](../user-and-org-service/apis/user-management.md#user-v1-read-userid)

<details>

<summary>Sample Response Payload</summary>

```json
{
    "id": "api.user.read",
    "ver": "v1",
    "ts": "2020-11-23 13:21:57:692+0000",
    "params": {
        "resmsgid": null,
        "msgid": "af801330-0dcb-42c6-b76b-cedaa6212118",
        "err": null,
        "status": "success",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "response": {
            "webPages": [],
            "tcStatus": null,
            "maskedPhone": null,
            "rootOrgName": "Pre-prod Custodian Organization",
            "subject": [],
            "channel": "dikshapreprodcustodian",
            "language": [],
            "updatedDate": null,
            "managedBy": null,
            "flagsValue": 2,
            "id": "ec8deeb2-4ded-4fa2-ac48-023ad8298d92",
            "recoveryEmail": "",
            "identifier": "ec8deeb2-4ded-4fa2-ac48-023ad8298d92",
            "thumbnail": null,
            "updatedBy": null,
            "accesscode": null,
            "locationIds": [],
            "registryId": null,
            "rootOrgId": "0126796199493140480",
            "prevUsedEmail": "",
            "firstName": "selfdeclaredev4",
            "tncAcceptedOn": null,
            "allTncAccepted": {},
            "phone": "",
            "dob": null,
            "grade": [],
            "currentLoginTime": null,
            "userType": "OTHER",
            "status": 1,
            "lastName": "selfdeclaredev4",
            "tncLatestVersion": "v8",
            "gender": null,
            "roles": [
                "PUBLIC"
            ],
            "prevUsedPhone": "",
            "stateValidated": false,
            "isDeleted": false,
            "organisations": [
                {
                    "updatedBy": null,
                    "organisationId": "0126796199493140480",
                    "orgName": "Pre-prod Custodian Organization",
                    "addedByName": null,
                    "addedBy": null,
                    "roles": [
                        "PUBLIC"
                    ],
                    "approvedBy": null,
                    "updatedDate": null,
                    "userId": "ec8deeb2-4ded-4fa2-ac48-023ad8298d92",
                    "approvaldate": null,
                    "isDeleted": false,
                    "hashTagId": "0126796199493140480",
                    "isRejected": null,
                    "position": null,
                    "id": "0131573015167221767",
                    "orgjoindate": "2020-11-23 07:02:43:194+0000",
                    "isApproved": null,
                    "orgLeftDate": null
                }
            ],
            "provider": null,
            "countryCode": null,
            "tncLatestVersionUrl": "https://preprodall.blob.core.windows.net/termsandcond/terms-and-conditions-v8.html",
            "maskedEmail": "se*************@yopmail.com",
            "tempPassword": null,
            "email": "se*************@yopmail.com",
            "rootOrg": {
                "dateTime": null,
                "preferredLanguage": null,
                "keys": {
                    "encKeys": [
                        "456"
                    ],
                    "signKeys": [
                        "456"
                    ]
                },
                "channel": "dikshapreprodcustodian",
                "approvedBy": null,
                "description": "Pre-prod Custodian Organization",
                "updatedDate": "2020-08-28 10:12:01:096+0000",
                "addressId": null,
                "orgType": null,
                "provider": null,
                "orgCode": null,
                "locationId": null,
                "theme": null,
                "id": "0126796199493140480",
                "isApproved": null,
                "communityId": null,
                "slug": "dikshapreprodcustodian",
                "email": null,
                "isSSOEnabled": null,
                "thumbnail": null,
                "updatedBy": null,
                "orgName": "Pre-prod Custodian Organization",
                "locationIds": [
                    "027f81d8-0a2c-4fc6-96ac-59fe4cea3abf",
                    "8250d58d-f1a2-4397-bfd3-b2e688ba7141"
                ],
                "externalId": null,
                "isRootOrg": true,
                "rootOrgId": "0126796199493140480",
                "imgUrl": null,
                "approvedDate": null,
                "orgTypeId": null,
                "homeUrl": null,
                "isDefault": true,
                "createdDate": "2019-01-18 09:48:13:428+0000",
                "contactDetail": null,
                "parentOrgId": null,
                "createdBy": "system",
                "hashTagId": "0126796199493140480",
                "noOfMembers": null,
                "status": 1
            },
            "profileSummary": null,
            "phoneVerified": false,
            "tcUpdatedDate": null,
            "recoveryPhone": "",
            "avatar": null,
            "userName": "selfdeclaredev4",
            "promptTnC": true,
            "lastLoginTime": null,
            "emailVerified": true,
            "framework": {},
            "createdDate": "2020-11-23 07:02:36:155+0000",
            "createdBy": null,
            "location": null,
            "tncAcceptedVersion": null
        }
    }
}
```

</details>
{% endtab %}

{% tab title="Druid Service" %}
There is a dependency on Druid Service  API calls.\


**Dependency API:**\


/druid/v2/
{% endtab %}

{% tab title="Notification Service" %}
There is a dependency with Notification Service to trigger the email notifications by using the API calls.\


**Dependency API:**\
\
[/v1/notification/email](http://docs.sunbird.org/1.8/apis/notificationapi/#operation/%7B%7Bhost%7D%7D%2Fuser%2Fv1%2Fnotification%2Femail%20)\
API Method: **POST**&#x20;

<details>

<summary>Sample Request Payload</summary>

```json
{
  "request": {
    "name": "Amit",
    "subject": "test email",
    "body": "Hello Amit.",
    "downloadUrl": "https://www.google.com/",
    "recipientEmails": [
      "john@gmail.com"
      
    ],
    "mode": "sms",   
    "recipientUserIds": [
      "5ee4a77c-4600-46de-a938-dsdsdsdb"
    ],
    "recipentSearchQuery": {
      "filters": {
        "channel": "nameof channel",
        "rootOrgId": "rootOrgIds",
        "organisations.roles": [
          "valid roles"
        ]
      }
    }
  }
}
```

</details>

<details>

<summary>Sample Response Payload</summary>

```json
{
    "id": "api.notification.email",
    "ver": "v1",
    "ts": "2020-12-06 21:05:11:142+0530",
    "params": {
        "resmsgid": null,
        "msgid": "3c8bd215-4b02-4b9a-a419-7462fc525a73",
        "err": null,
        "status": "success",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "response": "SUCCESS"
    }
}
```

</details>
{% endtab %}

{% tab title="Certificate Registry Service" %}
There is a dependency with Certificate Registry Service to download the certificates by using the API calls.

\
**Dependency API:**\
\
[/cert/v1/template/read](http://docs.sunbird.org/latest/apis/certificatetemplateapi/#operation/GetCertificateTemplate)\
API Method: **GET**

<details>

<summary>Sample Response Payload</summary>

```json
{
  "id": null,
  "ver": null,
  "ts": null,
  "params": null,
  "responseCode": "OK",
  "result": {
    "certificate": {
      "template": {
        "template": "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/content/test_template_stag/artifact/cbse-certificate.zip",
        "identifier": "template_01_pdf_stag",
        "name": "",
        "params": [
          "issuer.name",
          "issuer.url"
        ]
      }
    }
  }
}
```

</details>
{% endtab %}
{% endtabs %}
