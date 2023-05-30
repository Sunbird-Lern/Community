# Collection Summary Job

The 'Collection Summary Snapshot' data source in Druid serves as a repository for extracting metrics used in various reports. This Collection Summary Job captures information from user data and courses, saving it as a blob. The blob data is then indexed into the 'Collection Summary Snapshot' within Druid for further analysis and retrieval.



<figure><img src="../../../../../.gitbook/assets/collection_Summary.png" alt=""><figcaption></figcaption></figure>

**Data provider:**

**Cassandra**

1. user\_enrolments
2. course\_batch

**API**

1. Druid ingestion task trigger API
2. Content search API

<details>

<summary><strong>Collection Summary Ingestion Spec:</strong></summary>

```json
{
  "type": "index",
  "spec": {
    "dataSchema": {
      "dataSource": "collection-summary-snapshot",
      "parser": {
        "type": "string",
        "parseSpec": {
          "format": "json",
          "flattenSpec": {
            "useFieldDiscovery": false,
            "fields": [
              {
                "type": "root",
                "name": "content_org",
                "expr": "contentorg"
              },
              {
                "type": "root",
                "name": "user_org",
                "expr": "orgname"
              },
              {
                "type": "root",
                "name": "batch_start_date",
                "expr": "startdate"
              },
              {
                "type": "root",
                "name": "batch_end_date",
                "expr": "enddate"
              },
              {
                "type": "root",
                "name": "has_certificate",
                "expr": "hascertified"
              },
              {
                "type": "root",
                "name": "collection_id",
                "expr": "courseid"
              },
              {
                "type": "root",
                "name": "batch_id",
                "expr": "batchid"
              },
              {
                "type": "root",
                "name": "collection_name",
                "expr": "collectionname"
              },
              {
                "type": "root",
                "name": "batch_name",
                "expr": "batchname"
              },
              {
                "type": "root",
                "name": "total_enrolment",
                "expr": "enrolleduserscount"
              },
              {
                "type": "root",
                "name": "total_completion",
                "expr": "completionuserscount"
              },
              {
                "type": "root",
                "name": "total_certificates_issued",
                "expr": "certificateissuedcount"
              },
              {
                "type": "root",
                "name": "content_status",
                "expr": "contentstatus"
              },
              {
                "type": "root",
                "name": "user_state",
                "expr": "state"
              },
              {
                "type": "root",
                "name": "user_district",
                "expr": "district"
              },
              {
                "type": "root",
                "name": "content_channel",
                "expr": "channel"
              },
              {
                "type": "root",
                "name": "keywords",
                "expr": "keywords"
              },
              {
                "type": "root",
                "name": "timestamp",
                "expr": "timestamp"
              },
              {
                "type": "root",
                "name": "medium",
                "expr": "medium"
              },
              {
                "type": "root",
                "name": "subject",
                "expr": "subject"
              },
              {
                "type": "root",
                "name": "created_for",
                "expr": "createdfor"
              },
              {
                "type": "root",
                "name": "user_type",
                "expr": "usertype"
              },
              {
                "type": "root",
                "name": "user_subtype",
                "expr": "usersubtype"
              }
            ]
          },
          "dimensionsSpec": {
            "dimensions": [
              {
                "name": "content_org"
              },
              {
                "name": "user_org"
              },
              {
                "type": "string",
                "name": "batch_id"
              },
              {
                "type": "string",
                "name": "batch_start_date"
              },
              {
                "type": "string",
                "name": "batch_end_date"
              },
              {
                "type": "string",
                "name": "collection_id"
              },
              {
                "type": "string",
                "name": "collection_name"
              },
              {
                "type": "string",
                "name": "batch_name"
              },
              {
                "type": "long",
                "name": "total_enrolment"
              },
              {
                "type": "long",
                "name": "total_completion"
              },
              {
                "type": "long",
                "name": "total_certificates_issued"
              },
              {
                "type": "string",
                "name": "content_status"
              },
              {
                "type": "string",
                "name": "user_state"
              },
              {
                "type": "string",
                "name": "user_district"
              },
              {
                "name": "keywords"
              },
              {
                "name": "has_certificate"
              },
              {
                "type": "string",
                "name": "content_channel"
              },
              {
                "name": "medium"
              },
              {
                "name": "subject"
              },
              {
                "name": "created_for"
              },
              {
                "type": "string",
                "name": "user_type"
              },
              {
                "type": "string",
                "name": "user_subtype"
              }
            ],
            "dimensionsExclusions": []
          },
          "timestampSpec": {
            "column": "timestamp",
            "format": "auto"
          }
        }
      },
      "metricsSpec": [],
      "granularitySpec": {
        "type": "uniform",
        "segmentGranularity": "day",
        "queryGranularity": "none",
        "rollup": true
      }
    },
    "ioConfig": {
      "type": "index",
      "firehose": {
        "type": "static-azure-blobstore",
        "blobs": [
          {
            "container": "reports",
            "path": "/collection-summary-reports-v2/collection-summary-report-latest.json"
          }
        ],
        "fetchTimeout": 300000
      }
    },
    "tuningConfig": {
      "type": "index",
      "targetPartitionSize": 5000000,
      "maxRowsInMemory": 25000,
      "forceExtendableShardSpecs": false,
      "logParseExceptions": true
    }
  }
}
```

</details>

#### Collection Summary Snapshot Spec:

| **Dimension In Druid** | **Field In Report**         | **Description**        | **Data Type**                                          |               |
| ---------------------- | --------------------------- | ---------------------- | ------------------------------------------------------ | ------------- |
| 1                      | content\_org                | organisation           | Published By or Course Publisher Name or tenant        | String        |
| 2                      | user\_org                   | orgname                | User Organisation name                                 | String        |
| 3                      | batch\_id                   | batchid                | Unique Batch Identifier                                | String        |
| 4                      | collection\_id              | courseid               | Unique Collection Identifier                           | String        |
| 5                      | batch\_start\_date          | startdate              | Start Date of the Batch                                | String        |
| 6                      | batch\_end\_date            | enddate                | End Date of the Batch                                  | String        |
| 7                      | collection\_name            | collectionname         | Name of Course                                         | String        |
| 8                      | batch\_name                 | batchname              | Name of the batch                                      | String        |
| 9                      | total\_enrolment            | enrolleduserscount     | The number of users are enrolled for the course.       | Long          |
| 10                     | total\_completion           | completionuserscount   | The number of users have completed the course          | Long          |
| 11                     | total\_certificates\_issued | certificateissuedcount | The number of users received the certificate in course | Long          |
| 12                     | content\_status             | contentstatus          | State of Course. Ex: Live, Draft, etc.                 | String        |
| 13                     | user\_state                 | state                  | Name of The State                                      | String        |
| 14                     | user\_district              | district               | Name of the District                                   | String        |
| 15                     | content\_channel            | channel                | Name of the Channel                                    | String        |
| 16                     | keywords                    | keywords               | Keywords/Tags which are assigned to course             | List\[String] |
| 17                     | timestamp                   | timestamp              | TimeStamp of when the report is generated.             | Long          |
| 18                     | content\_channel            | channel                | Channel of the collection/course                       | String        |
| 19                     | has\_certificate            | hascertified           | Whether batch is certified or not                      | Boolean       |
