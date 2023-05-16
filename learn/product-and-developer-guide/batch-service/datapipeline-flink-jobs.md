---
description: This page details about the Flink Jobs present as part of LERN Building block.
---

# Data-pipeline (Flink Jobs)

Flink Jobs in LERN have been to developed to support LMS (Learning Management System) journey of a user. Jobs are used to compute data necessary to calculate user's progress and validate the same against certificate issuance criteria and then trigger Sunbird RC to create and issue certificate to the user.&#x20;

&#x20;

<figure><img src="../../../.gitbook/assets/OVERVIEW - LERN JOBS.drawio (1).png" alt=""><figcaption><p><strong>Data-pipeline Overview Diagram</strong></p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Untitled Diagram-V2 LERN - CERTIFICATE GENERATION FLOW.drawio.png" alt=""><figcaption><p><strong>Certificate Generation jobs execution flow diagram</strong></p></figcaption></figure>

### Merge User Courses

'merge-user-courses' job will permit a user who owns multiple accounts on a sunbird platform (one on an Organisation tenant and one on the custodian tenant), to merge the course related usage history (course batch enrolments, course content consumption, course progress) into one primary account.&#x20;

This job performs following tasks:

* Merges the content consumption details from an account to primary account.
* Merges the user batches from an account to primary account.
* Merges the user activity aggregate data from an account to primary account.
* Performs a `batch-enrolment-sync` to primary account

<figure><img src="../../../.gitbook/assets/Untitled Diagram-merge-user-courses.drawio.png" alt=""><figcaption></figcaption></figure>

**Configuration variables:**

| Variable                                 | Default Value                     | Purpose                                                                                                                                                                            |
| ---------------------------------------- | --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| kafka.input.topic                        | \{{env\}}.lms.user.account.merge  | Kafka topic from which messages/events are read to be processed.                                                                                                                   |
| kafka.output.failed.topic                | \{{env\}}.learning.events.failed  | Kafka topic to which message is written when an exception occurs while processing an event.                                                                                        |
| kafka.groupId                            |                                   | Kafka input topic group Id                                                                                                                                                         |
| kafka.output.course.batch.updater.topic  | \{{env\}}.coursebatch.job.request | Kafka topic to which output message/event is inserted to perform user course progress activity reconciliation to merged Id                                                         |
| lms-cassandra.keyspace                   | sunbird\_courses                  | Cassandra keyspace name                                                                                                                                                            |
| lms-cassandra.content\_consumption.table | user\_content\_consumption        | Cassandra table used to store content wise data for a collection of a batch by a user. Content progress, status etc                                                                |
| lms-cassandra.user\_enrolments.table     | user\_enrolments                  | Cassandra table used to store user enrolment data in a collection of a particular batch. This also holds the consumption progress, enrolment status and issued certificate details |
| lms-cassandra.user\_activity\_agg.table  | user\_activity\_agg               | Cassandra table used to store user consumption aggregate details of a collection in a batch. Aggregates like the consumption completed content count                               |

**Sample event:**

```json
{
  "eid": "BE_JOB_REQUEST",
  "ets": 1648720639981,
  "mid": "LP.1648720639981.d6b1d8c8-7a4a-483a-b83a-b752bede648c",
  "actor": {
    "id": "Merge User Courses and Cert",
    "type": "System"
  },
  "context": {
    "pdata": {
      "ver": "1.0",
      "id": "org.sunbird.platform"
    },
    "channel": "0123221758376673287017",
    "env": "staging"
  },
  "object": {
    "type": "MergeUserCoursesAndCert",
    "id": "68b764efd14bb3b534984649"
  },
  "edata": {
    "action": "merge-user-courses-and-cert",
    "fromAccountId": "b964d83a-c40f-4b3c-85e7-68b764efd14b",
    "toAccountId": "191e6b5a-8581-46bd-b779-b3b534984649",
    "rootOrgId": "0123221758376673287017",
    "iteration": 1
  }
}
```

**Source Code:**

{% embed url="https://github.com/Sunbird-Lern/data-pipeline/tree/release-5.3.0/lms-jobs/merge-user-courses" %}

### Relation Cache Updater

'relation-cache-updater' job is used to perform one time compute and cache information such as leafNodes, optionalNodes, unitsMap and ancestorsMap of a collection to **Redis** when the collection is published. This data is utilised by other jobs and services.&#x20;

| Key                                         | Data format   | Sample                                                           |
| ------------------------------------------- | ------------- | ---------------------------------------------------------------- |
| \<collectionId>:leafnodes                   | List\<String> | collectionId:leafnodes: \[“resource1”,”resource2”]               |
| \<collectionId>:optionalnodes               | List\<String> | collectionId:optionalnodes: \[“resource1”,”resource2”]           |
| \<rootCollectionId>:\<resourceId>:ancestors | List\<String> | collectionId:resource1:ancestors: \[“courseunit1”, “democourse”] |

<figure><img src="../../../.gitbook/assets/relation-cache-updater.drawio (1).png" alt=""><figcaption></figcaption></figure>

**Configuration variables:**

| Variable                | Default Value                          | Purpose                                                                                                                                                 |
| ----------------------- | -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| kafka.input.topic       | \{{env\}}.lms.user.account.merge       | Kafka topic from which messages/events are read to be processed.                                                                                        |
| kafka.groupId           | \{{env\}}-relation-cache-updater-group | Kafka input topic group Id                                                                                                                              |
| lms-cassandra.keyspace  | \{{env\}}\_hierarchy\_store            | Cassandra keyspace name                                                                                                                                 |
| lms-cassandra.table     | content\_hierarchy                     | Cassandra table used to read collection hierarchy.                                                                                                      |
| redis.database.index    | 10                                     | Redis index to which computed data like **leafnodes** and **optionalnodes** is stored                                                                   |
| dp-redis.host           | IP should be same as lp-redis host     | dp-redis (data-pipeline redis) IP should be kept same as lp-redis (learning-platform) redis in order to be able to read pulished collection information |
| dp-redis.port           | port should be same as lp-redis port   | dp-redis port                                                                                                                                           |
| dp-redis.database.index | 5                                      | Redis index to which computed data 'units map' is stored                                                                                                |

**Sample event:**

```json
{
  "eid": "BE_JOB_REQUEST",
  "ets": 1649170015935,
  "mid": "LP.1649170015935.2a7382ff-8bc9-4ff5-8620-2d467cf8990a",
  "actor": {
    "id": "Post Publish Processor",
    "type": "System"
  },
  "context": {
    "pdata": {
      "ver": "1.0",
      "id": "org.sunbird.platform"
    },
    "channel": "01272777697873100812",
    "env": "sunbirdstaging"
  },
  "object": {
    "ver": "1649169952265",
    "id": "do_21350999965318348811690"
  },
  "edata": {
    "action": "post-publish-process",
    "iteration": 1,
    "identifier": "do_21350999965318348811690",
    "channel": "01272777697873100812",
    "mimeType": "application/vnd.ekstep.content-collection",
    "contentType": "Course",
    "pkgVersion": 1,
    "status": "Live",
    "name": "CourseMTimmothy",
    "trackable": {
      "enabled": "Yes",
      "autoBatch": "No"
    }
  }
}
```

**Source code:**

{% embed url="https://github.com/Sunbird-Lern/data-pipeline/tree/release-5.3.0/lms-jobs/relation-cache-updater" %}

### Activity Aggregate Updater

'activity-aggregate-updater' job updates the Course progress of the enrolled users and upon completion pushes an event to certificate pre-processor job to validate and issue certificate.

<figure><img src="../../../.gitbook/assets/Untitled Diagram-activity-aggregate-updater.drawio (1).png" alt=""><figcaption></figcaption></figure>

| Variable                                 | Default Value                              | Purpose                                                                                                                                                                                                                                           |
| ---------------------------------------- | ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| kafka.input.topic                        | \{{env\}}.coursebatch.job.request          | Kafka topic from which messages/events are read to be processed.                                                                                                                                                                                  |
| kafka.output.failed.topic                | \{{env\}}.activity.agg.failed              | Kafka topic to which message is written when an exception occurs while processing an event.                                                                                                                                                       |
| kafka.audit.topic                        | \{{env\}}.telemetry.raw                    | Kakfa topic to which and audit message is written to.                                                                                                                                                                                             |
| kafka.certissue.topic                    | \{{env\}}.issue.certificate.request        | Kafka topic used to trigger certificate issue pre-processor job                                                                                                                                                                                   |
| kafka.groupId                            | \{{env\}}-activity-aggregate-updater-group | Kafka input topic group Id                                                                                                                                                                                                                        |
| lms-cassandra.keyspace                   | sunbird\_courses                           | Cassandra keyspace name                                                                                                                                                                                                                           |
| lms-cassandra.content\_consumption.table | user\_content\_consumption                 | Cassandra table used to store content wise data for a collection of a batch by a user. Content progress, status etc                                                                                                                               |
| lms-cassandra.user\_enrolments.table     | user\_enrolments                           | Cassandra table used to store user enrolment data in a collection of a particular batch. This also holds the consumption progress, enrolment status and issued certificate details                                                                |
| lms-cassandra.user\_activity\_agg.table  | user\_activity\_agg                        | Cassandra table used to store user consumption aggregate details of a collection in a batch. Aggregates like the consumption completed content count                                                                                              |
| redis.database.relationCache.id          | 10                                         | Redis index from which computed data like leafnodes and optionalnodes is read.                                                                                                                                                                    |
| dedup-redis.host                         | IP of deduplicate Redis host               | De-duplication Redis is used to remove duplicate events possibly part of the events list in kafka input topic which is fetched in batch size of 'threshold.batch.read.size' parameter mentioned below.                                            |
| dedup-redis.port                         | port                                       | port of deduplicate Redis                                                                                                                                                                                                                         |
| dedup-redis.database.index               | 13                                         | De-duplication Redis index                                                                                                                                                                                                                        |
| dedup-redis.database.expiry              | 604800                                     | De-duplication Redis Expiry time                                                                                                                                                                                                                  |
| threshold.batch.read.interval            |                                            | NOT USED                                                                                                                                                                                                                                          |
| threshold.batch.read.size                | 1000                                       | Flink stream window size                                                                                                                                                                                                                          |
| threshold.batch.write.size               | 10                                         | Property used to specify batch size of the database update queries while updating a specific cassandra table in batch format                                                                                                                      |
| activity.module.aggs.enabled             | true                                       | Used to configure if the consumption aggregation calculation is to be enabled on course leaf nodes                                                                                                                                                |
| activity.input.dedup.enabled             | true                                       | Used to configure if the aggregation job is to run in De-duplication mode                                                                                                                                                                         |
| activity.filter.processed.enrolments     | true                                       | Used to configure if the activity aggregation process is to be skipped for user enrolments with status 2 (completed courses)                                                                                                                      |
| activity.collection.status.cache.expiry  | 3600 (in seconds)                          | Expiry time of TTL cache set  to read or store latest collection 'status' information. If latest TTL cache doesnt have collection 'status' information, then the same is read from Search service configured below and TTL cache will be updated. |
| service.search.basePath                  | IP of the search service                   | IP of the search service                                                                                                                                                                                                                          |

**Sample event:**

```json
{
  "eid": "BE_JOB_REQUEST",
  "ets": 1683617553712,
  "mid": "LP.1683617553712.b5899054-aabf-4a4c-b4e1-749f8721a276",
  "actor": {
    "type": "System",
    "id": "Course Batch Updater"
  },
  "context": {
    "pdata": {
      "ver": "1.0",
      "id": "org.sunbird.platform"
    }
  },
  "object": {
    "type": "CourseBatchEnrolment",
    "id": "01379148663062528012_9c559542-9bb0-40bd-92e2-3230aebcb3a5"
  },
  "edata": {
    "contents": [
      {
        "contentId": "do_21310354322092851214725",
        "status": 2
      }
    ],
    "action": "batch-enrolment-update",
    "iteration": 1,
    "batchId": "01379148663062528012",
    "userId": "9c559542-9bb0-40bd-92e2-3230aebcb3a5",
    "courseId": "do_2137914724998758401207"
  }
}
```

{% embed url="https://github.com/Sunbird-Lern/data-pipeline/tree/release-5.3.0/lms-jobs/assessment-aggregator" %}

### Assessment Aggregator

'assessment-aggregator' job is used to compute the course assessment content progress present as part of the Course. Job calculates the scores secured by the user during consumption against each Course Assessment Content.

<figure><img src="../../../.gitbook/assets/Untitled Diagram-assessment-aggregator.drawio.png" alt=""><figcaption></figcaption></figure>

**Configuration variables:**

| Variable                        | Default Value                         | Purpose                                                                                                                                                                                                             |
| ------------------------------- | ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| kafka.input.topic               | \{{env\}}.telemetry.assess            | Kafka topic from which messages/events are read to be processed.                                                                                                                                                    |
| kafka.output.failed.topic       | \{{env\}}.telemetry.assess.failed     | Kafka topic to which message is written when an exception occurs while processing an event.                                                                                                                         |
| kafka.output.certissue.topic    | \{{env\}}.issue.certificate.request   | Kafka topic used to trigger certificate issue pre-processor job                                                                                                                                                     |
| kafka.groupId                   | \{{env\}}-assessment-aggregator-group | Kafka input topic group Id                                                                                                                                                                                          |
| lms-cassandra.keyspace          | sunbird\_courses                      | Cassandra keyspace name                                                                                                                                                                                             |
| lms-cassandra.table             | assessment\_aggregator                | Cassandra table used to store attempt wise data for each assessment in a collection of a batch by a user. Answer for each question in the assessment is also recorded.                                              |
| lms-cassandra.enrolmentstable   | user\_enrolments                      | Cassandra table used to store user enrolment data in a collection of a particular batch. This also holds the consumption progress, enrolment status and issued certificate details                                  |
| lms-cassandra.activityytable    | user\_activity\_agg                   | Cassandra table used to store user consumption aggregate details of a collection in a batch. Aggregates like the consumption completed content count                                                                |
| lms-cassandra.questionudttype   | question                              | Cassandra table used to store each question information.                                                                                                                                                            |
| redis.database.relationCache.id | 10                                    | Redis index from which computed data like leafnodes and optionalnodes is read.                                                                                                                                      |
| redis.database.contentCache.id  | 5                                     | Redis index from which Content metadata is read from.                                                                                                                                                               |
| assessment.skip.missingRecords  | false                                 | Variable used to mention if the event processing is to be skipped in case of 'the totalQuestions Count value is not matching with the event size then job should skip those events and increase the metrics value'. |
| user.activity.agg.type          | attempt\_metrics                      |                                                                                                                                                                                                                     |
| content.read.api                | Endpoint URL of content read API      | Endpoint URL of content read API part of content-service                                                                                                                                                            |

**Sample event:**

```json
{
  "assessmentTs": 1683606904796,
  "batchId": "013625297374085120185",
  "courseId": "do_2136252863013273601715",
  "userId": "95c1f00b-c033-4ea2-acf6-e368e2a56bdb",
  "attemptId": "9b6908cad37c83e53582354e1b971bb9",
  "contentId": "do_21362528320146636811198",
  "events": []
}  
```

**Source code:**

{% embed url="https://github.com/Sunbird-Lern/data-pipeline/tree/release-5.3.0/lms-jobs/activity-aggregate-updater" %}

### Enrolment Reconciliation

'enrolment-reconciliation' job syncs the progress of the enrolled user. This job perform same tasks as 'activity-aggregator-updater' flink job. This is triggered by the user if the progress is not updated during course consumption.

<figure><img src="../../../.gitbook/assets/Untitled Diagram-enrolment-reconciliation.drawio.png" alt=""><figcaption></figcaption></figure>

**Configuration variables:**

| Variable                                 | Default Value                             | Purpose                                                                                                                                                                                                                                           |
| ---------------------------------------- | ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| kafka.input.topic                        | \{{env\}}.batch.enrolment.sync.request    | Kafka topic from which messages/events are read to be processed.                                                                                                                                                                                  |
| kafka.output.failed.topic                | \{{env\}}.enrolment.reconciliation.failed | Kafka topic to which message is written when an exception occurs while processing an event.                                                                                                                                                       |
| kafka.audit.topic                        | \{{env\}}.telemetry.raw                   | Kakfa topic to which and audit message is written to.                                                                                                                                                                                             |
| kafka.certissue.topic                    | \{{env\}}.issue.certificate.request       | Kafka topic used to trigger certificate issue pre-processor job                                                                                                                                                                                   |
| kafka.groupId                            | \{{env\}}-enrolment-reconciliation-group  | Kafka input topic group Id                                                                                                                                                                                                                        |
| lms-cassandra.keyspace                   | sunbird\_courses                          | Cassandra keyspace name                                                                                                                                                                                                                           |
| lms-cassandra.content\_consumption.table | user\_content\_consumption                | Cassandra table used to store content wise data for a collection of a batch by a user. Content progress, status etc                                                                                                                               |
| lms-cassandra.user\_enrolments.table     | user\_enrolments                          | Cassandra table used to store user enrolment data in a collection of a particular batch. This also holds the consumption progress, enrolment status and issued certificate details                                                                |
| lms-cassandra.user\_activity\_agg.table  | user\_activity\_agg                       | Cassandra table used to store user consumption aggregate details of a collection in a batch. Aggregates like the consumption completed content count                                                                                              |
| redis.database.relationCache.id          | 10                                        | Redis index from which computed data like leafnodes and optionalnodes is read.                                                                                                                                                                    |
| threshold.batch.write.size               | 10                                        | Property used to specify batch size of the database update queries while updating a specific cassandra table in batch format                                                                                                                      |
| activity.module.aggs.enabled             | true                                      | Used to configure if the consumption aggregation calculation is to be enabled on course leaf nodes                                                                                                                                                |
| activity.filter.processed.enrolments     | true                                      | Used to configure if the activity aggregation process is to be skipped for user enrolments with status 2 (completed courses)                                                                                                                      |
| activity.collection.status.cache.expiry  | 3600 (in seconds)                         | Expiry time of TTL cache set  to read or store latest collection 'status' information. If latest TTL cache doesnt have collection 'status' information, then the same is read from Search service configured below and TTL cache will be updated. |
| service.search.basePath                  | IP of the search service                  | IP of the search service                                                                                                                                                                                                                          |

**Sample event:**

```json
{
  "eid": "BE_JOB_REQUEST",
  "ets": 1683556693275,
  "mid": "LP.1683556693275.a18caaec-50ac-4c19-bcfe-84e2ad9aa5eb",
  "actor": {
    "type": "System",
    "id": "Course Batch Updater"
  },
  "context": {
    "pdata": {
      "ver": "1.0",
      "id": "org.sunbird.platform"
    }
  },
  "object": {
    "type": "CourseBatchEnrolment",
    "id": "0131029098223779842_fbe926ac-a395-40e4-a65b-9b4f711d7642"
  },
  "edata": {
    "action": "user-enrolment-sync",
    "iteration": 1,
    "batchId": "0131029098223779842",
    "userId": "fbe926ac-a395-40e4-a65b-9b4f711d7642",
    "courseId": "do_21310287978188800014457"
  }
}
```

**Source code:**

{% embed url="https://github.com/Sunbird-Lern/data-pipeline/tree/release-5.3.0/lms-jobs/enrolment-reconciliation" %}

### Collection Certificate Pre-Processor

'collection-cert-pre-processor' job is used to perform the validation of certificate issuance criteria.&#x20;

<figure><img src="../../../.gitbook/assets/Cert Pre-processor.drawio.png" alt=""><figcaption></figcaption></figure>

**Configuration variables:**

| Variable                                   | Default Value                                 | Purpose                                                                                                                                                                                                             |
| ------------------------------------------ | --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| kafka.input.topic                          | \{{env\}}.issue.certificate.request           | Kafka topic from which messages/events are read to be processed.                                                                                                                                                    |
| kafka.output.failed.topic                  | \{{env\}}.issue.certificate.failed            | Kafka topic to which message is written when an exception occurs while processing an event.                                                                                                                         |
| kafka.output.topic                         | \{{env\}}.generate.certificate.request        | Kafka topic used to trigger certificate generator job                                                                                                                                                               |
| kafka.groupId                              | \{{env\}}-collection-cert-pre-processor-group | Kafka input topic group Id                                                                                                                                                                                          |
| lms-cassandra.keyspace                     | sunbird\_courses                              | Cassandra keyspace name                                                                                                                                                                                             |
| lms-cassandra.course\_batch.table          | course\_batch                                 | Cassandra table used to store batch details of a collection. Batch status, start date , end date , batch enrolment end date, enrolment type (open/invite-only), certificate templates etc are stored in this table. |
| lms-cassandra.user\_enrolments.table       | user\_enrolments                              | Cassandra table used to store user enrolment data in a collection of a particular batch. This also holds the consumption progress, enrolment status and issued certificate details                                  |
| lms-cassandra.assessment\_aggregator.table | assessment\_aggregator                        | Cassandra table used to store attempt wise data for each assessment in a collection of a batch by a user. Answer for each question in the assessment is also recorded.                                              |
| lms-cassandra.user\_activity\_agg.table    | user\_activity\_agg                           | Cassandra table used to store user consumption aggregate details of a collection in a batch. Aggregates like the consumption completed content count                                                                |
| cert\_domain\_url                          |                                               |                                                                                                                                                                                                                     |
| user\_read\_api                            | /private/user/v1/read                         | API route for fetching user profile details                                                                                                                                                                         |
| content\_read\_api                         | /content/v4/read                              | API route for fetching content metadata                                                                                                                                                                             |
| service.content.basePath                   |                                               | Content service URL                                                                                                                                                                                                 |
| service.learner.basePath                   |                                               | User-Org service URL                                                                                                                                                                                                |
| assessment.metrics.supported.contenttype   | \["SelfAssess"]                               | variable used to identify assessment type of contents in a Course                                                                                                                                                   |
| enable.suppress.exception                  | true                                          | Variable used to suppress exception if the content metadata is not available in Redis cache                                                                                                                         |
| cloud\_storage\_base\_url                  |                                               | variable to identify the cloud storage base url. Used to replace the base url with variable mentioned in cloud\_store\_base\_path\_placeholder while storing to databases                                           |
| cloud\_store\_base\_path\_placeholder      | CLOUD\_BASE\_PATH                             | relative variable used to replace cloud storage base URLs and stored in database                                                                                                                                    |
| content\_cloud\_storage\_container         |                                               | cloud storage container name                                                                                                                                                                                        |
| cloud\_storage\_cname\_url                 |                                               | variable used to replace 'cloud\_store\_base\_path\_placeholder' value with cname or cloud storage url while reading data from database.                                                                            |

**Sample event:**

```json
{
  "eid": "BE_JOB_REQUEST",
  "ets": 1683609537232,
  "mid": "LP.1683609537232.f04270f4-7d8b-4fc6-9315-dc5c495fb059",
  "actor": {
    "id": "Course Certificate Generator",
    "type": "System"
  },
  "context": {
    "pdata": {
      "ver": "1.0",
      "id": "org.sunbird.platform"
    }
  },
  "object": {
    "id": "013625297374085120185_do_2136252863013273601715",
    "type": "CourseCertificateGeneration"json
  },
  "edata": {
    "userIds": [
      "95c1f00b-c033-4ea2-acf6-e368e2a56bdb"
    ],
    "action": "issue-certificate",
    "iteration": 1,
    "trigger": "auto-issue",
    "batchId": "013625297374085120185",
    "reIssue": false,
    "courseId": "do_2136252863013273601715"
  }
}
```

**Source code:**

{% embed url="https://github.com/Sunbird-Lern/data-pipeline/tree/release-5.3.0/lms-jobs/credential-generator/collection-cert-pre-processor" %}

### Collection Certificate Generator&#x20;

'collection-certificate-generator' job is used to generate certificates.

<figure><img src="../../../.gitbook/assets/Cert Generator.drawio.png" alt=""><figcaption></figcaption></figure>

**Configuration variables:**

| Variable                              | Default Value                          | Purpose                                                                                                                                                                                                             |
| ------------------------------------- | -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| kafka.input.topic                     | \{{env\}}.generate.certificate.request | Kafka topic from which messages/events are read to be processed.                                                                                                                                                    |
| kafka.output.failed.topic             | \{{env\}}.generate.certificate.failed  | Kafka topic to which message is written when an exception occurs while processing an event.                                                                                                                         |
| kafka.output.audit.topic              | \{{env\}}.telemetry.raw                | Kakfa topic to which and audit message is written to.                                                                                                                                                               |
| kafka.groupId                         | \{{env\}}-certificate-generator-group  | Kafka input topic group Id                                                                                                                                                                                          |
| lms-cassandra.keyspace                | sunbird\_courses                       | Cassandra keyspace name                                                                                                                                                                                             |
| lms-cassandra.course\_batch.table     | course\_batch                          | Cassandra table used to store batch details of a collection. Batch status, start date , end date , batch enrolment end date, enrolment type (open/invite-only), certificate templates etc are stored in this table. |
| lms-cassandra.user\_enrolments.table  | user\_enrolments                       | Cassandra table used to store user enrolment data in a collection of a particular batch. This also holds the consumption progress, enrolment status and issued certificate details                                  |
| lms-cassandra.sbkeyspace              | sunbird                                | Sunbird Keyspace                                                                                                                                                                                                    |
| lms-cassandra.certreg.table           | cert\_registry                         | Cassandra table used to store user certificates (old format)                                                                                                                                                        |
| task.rc.badcharlist                   | \x00,\\\aaa,\aaa,Ø,Ý                   |                                                                                                                                                                                                                     |
| service.content.basePath              |                                        | Content service URL                                                                                                                                                                                                 |
| service.learner.basePath              |                                        | User-Org service URL                                                                                                                                                                                                |
| service.enc.basePath                  |                                        | Encryption service base path                                                                                                                                                                                        |
| service.rc.basePath                   |                                        | Sunbird RC base path                                                                                                                                                                                                |
| service.rc.entity                     | TrainingCertificate                    | variable used to specify sunbird RC API endpoint for certificate                                                                                                                                                    |
| enable.rc.certificate                 | true                                   | variable used to enable RC certificate generation                                                                                                                                                                   |
| enable.suppress.exception             | true                                   | Variable used to suppress exception if the signatory list is empty                                                                                                                                                  |
| cloud\_storage\_base\_url             |                                        | variable to identify the cloud storage base url. Used to replace the base url with variable mentioned in cloud\_store\_base\_path\_placeholder while storing to databases                                           |
| cloud\_store\_base\_path\_placeholder | CLOUD\_BASE\_PATH                      | relative variable used to replace cloud storage base urls and stored in database                                                                                                                                    |
| content\_cloud\_storage\_container    |                                        | cloud storage container name                                                                                                                                                                                        |
| cloud\_storage\_cname\_url            |                                        | variable used to replace 'cloud\_store\_base\_path\_placeholder' value with cname or cloud storage url while reading data from database.                                                                            |

**Sample event:**

```json
{
  "eid": "BE_JOB_REQUEST",
  "ets": 1563788371969,
  "mid": "LMS.1563788371969.590c5fa0-0ce8-46ed-bf6c-681c0a1fdac8",
  "actor": {
    "type": "System",
    "id": "Certificate Generator"
  },
  "context": {
    "pdata": {
      "ver": "1.0",
      "id": "org.sunbird.platform"
    }
  },
  "object": {
    "type": "GenerateCertificate",
    "id": "874ed8a5-782e-4f6c-8f36-e0288455901e"
  },
  "edata": {
    "userId": "user001",
    "svgTemplate": "https://ntpstagingall.blob.core.windows.net/user/cert/File-01311849840255795242.svg",
    "templateId": "template_01_dev_001",
    "courseName": "new course may23",
    "data": [
      {
        "recipientName": "Creation ",
        "recipientId": "user001"
      }
    ],
    "name": "100PercentCompletionCertificate",
    "tag": "0125450863553740809",
    "issuer": {
      "name": "Gujarat Council of Educational Research and Training",
      "url": "https://gcert.gujarat.gov.in/gcert/",
      "publicKey": [
        "1",
        "2"
      ]
    },
    "signatoryList": [
      {
        "name": "CEO Gujarat",
        "id": "CEO",
        "designation": "CEO",
        "image": "https://cdn.pixabay.com/photo/2014/11/09/08/06/signature-523237__340.jpg"
      }
    ],
    "criteria": {
      "narrative": "course completion certificate"
    },
    "basePath": "https://dev.sunbirded.org/certs",
    "related": {
      "type": "course",
      "batchId": "0131000245281587206",
      "courseId": "do_11309999837886054415"
    }
  }
}
```

**Source code:**

{% embed url="https://github.com/Sunbird-Lern/data-pipeline/tree/release-5.3.0/lms-jobs/credential-generator/collection-certificate-generator" %}

### Notification Job

'notification-job' is used to send notifications in an asynchronous mode via SMS, eMail and FCM channels.

Additional Reading: [https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/1057980431/Notification+service](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/1057980431/Notification+service)

**Configuration variables:**

| Variable                  | Default Value                    | Purpose                                                          |
| ------------------------- | -------------------------------- | ---------------------------------------------------------------- |
| kafka.input.topic         | \{{env\}}.lms.notification       | Kafka topic from which messages/events are read to be processed. |
| kafka.groupId             | \{{env\}}.lms.notification.group | Kafka input topic group Id                                       |
| fcm\_account\_key         |                                  | Firebase Cloud Messaging                                         |
| sms\_auth\_key            |                                  | SMS Service Authentication key                                   |
| sms\_default\_sender      |                                  | SMS sender name (it must be 6 character only)                    |
| mail\_server\_from\_email |                                  | eMail Server                                                     |
| mail\_server\_username    |                                  | eMail server username                                            |
| mail\_server\_password    |                                  | eMail server password                                            |
| mail\_server\_host        |                                  | eMail server host Ip                                             |
| mail\_server\_port        |                                  | eMail server port                                                |

**Sample event:**

```json
SAMPLE EVENT 1:
{
  "actor": {
    "id": "BroadCast Topic Notification",
    "type": "System"
  },
  "eid": "BE_JOB_REQUEST",
  "edata": {
    "request": {
      "notification": {
        "config": {
          "sender": "support@sunbird.com",
          "subject": "Completion certificate"
        },
        "deliveryType": "message",
        "mode": "email",
        "template": {
          "data": "Hi",
          "params": {
            "body": "email body",
            "stateImgUrl": "https://sunbirddev.blob.core.windows.net/orgemailtemplate/img/File-0128212938260643843.png",
            "firstName": "Hari",
            "regards": "Minister of Humar Resources",
            "TraningName": "test-cert-notification",
            "regardsperson": "Chairperson",
            "heldDate": "16-12-2019"
          }
        },
        "ids": [
          "harip@test.in"
        ]
      }
    },
    "action": "broadcast-topic-notification-all",
    "iteration": 2
  },
  "trace": {
    "X-Request-ID": null,
    "X-Trace-Enabled": "false"
  },
  "context": {
    "pdata": {
      "ver": "1.0",
      "id": "org.sunbird.platform"
    }
  },
  "mid": "NS.1646230422793.70c10f26-631b-4d55-8aaa-fbe52b79cbc1",
  "object": {
    "id": "93a06b829d13c9fa797ea641f484e5d38ce28868fbd75014852cbe413515177c",
    "type": "TopicNotifyAll"
  }
}

SAMPLE EVENT 2:
{
  "actor": {
    "id": "BroadCast Topic Notification",
    "type": "System"
  },
  "eid": "BE_JOB_REQUEST",
  "mid": "NS.1657555782237.a0603d3a-f668-47e1-940f-4620786f029b",
  "trace": {
    "X-Request-ID": null,
    "X-Trace-Enabled": "false"
  },
  "ets": 1657555782237,
  "edata": {
    "action": "broadcast-topic-notification-all",
    "iteration": 1,
    "request": {
      "notification": {
        "mode": "phone",
        "deliveryType": "message",
        "config": {
          "sender": null,
          "topic": null,
          "otp": null,
          "subject": null
        },
        "ids": [
          "8050688698"
        ],
        "template": {
          "id": null,
          "data": "You have successfully completed Sunbird training.",
          "params": {
            "courseName": "Sunbird training"
          }
        },
        "rawData": null
      }
    }
  },
  "context": {
    "pdata": {
      "ver": "1.0",
      "id": "org.sunbird.platform"
    }
  },
  "object": {
    "id": "f5e7243feabb343b029f154341c2d55dacb92febb0c1b0349ee0676a02c9b816",
    "type": "TopicNotifyAll"
  }
}
```

**Source code:**

{% embed url="https://github.com/Sunbird-Lern/data-pipeline/tree/release-5.3.0/notification/notification-job" %}

### User cache updater

'user-cache-updater-2.0' job is used to generate the user-metadata information which is complied by fetching information from various Cassandra tables and are stored into the Redis cache. This user-metadata information is used by few exhaust reports.

Additional Reading: [https://project-sunbird.atlassian.net/wiki/spaces/AN/pages/1520074753/Design+Denormalise+User+Metadata](https://project-sunbird.atlassian.net/wiki/spaces/AN/pages/1520074753/Design+Denormalise+User+Metadata), [https://lern.sunbird.org/learn/product-and-developer-guide/user-and-org-service/caching-and-denormalising-user-metadata/usercacheupdaterflinkjob](https://lern.sunbird.org/learn/product-and-developer-guide/user-and-org-service/caching-and-denormalising-user-metadata/usercacheupdaterflinkjob)



**Configuration variables:**

| Variable                               | Default Value                      | Purpose                                                                               |
| -------------------------------------- | ---------------------------------- | ------------------------------------------------------------------------------------- |
| kafka.input.topic                      | \{{env\}}.telemetry.audit          | Kafka topic from which messages/events are read to be processed.                      |
| kafka.groupId                          | \{{env\}}-user-cache-updater-group | Kafka input topic group Id                                                            |
| redis-meta.database.userstore.id       | 12                                 | Redis index to which user metadata is to be written to for caching                    |
| redis-meta.database.key.expiry.seconds | 3600                               | Redis cache expiry in seconds                                                         |
| user-read.api.url                      | "/learner/private/user/v1/read"    | API Endpoint for fetching User profile details                                        |
| regd.user.producer.pid                 | learner-service                    | used to specify service providing user microservice                                   |
| user.self.signin.types                 | \["google","self"]                 | used to specify self sign-in modes available in application                           |
| user.validated.types                   | \["sso"]                           | used to specify sign-in modes where user validation is signed from third party system |
| user.self.signin.key                   | "Self-Signed-In"                   |                                                                                       |
| user.valid.key                         | "Validated"                        |                                                                                       |
| user.read.url.fields                   | "locations,organisations"          | used to specify the user metadata properties that are to be cached to Redis           |
| user.read.api.error                    | \["CLIENT\_ERROR"]                 |                                                                                       |

**Sample event:**

```json
{
  "eid": "AUDIT",
  "ets": 1573121861118,
  "ver": "3.0",
  "mid": "1573121861118.40f9136b-1cc3-458d-a04a-4459606df",
  "actor": {
    "id": "5609876543234567890987654345678",
    "type": "Request"
  },
  "context": {
    "channel": "01285019302823526477",
    "pdata": {
      "id": "dev.sunbird.portal",
      "pid": "learner-service",
      "ver": "2.5.0"
    },
    "env": "User",
    "did": "user-3",
    "cdata": [
      {
        "id": "google",
        "type": "SignupType"
      }
    ],
    "rollup": {
      "l1": "01285019302823526477"
    }
  },
  "object": {
    "id": "user-1",
    "type": "user"
  },
  "edata": {
    "state": "Update",
    "props": [
      "recoveryEmail",
      "recoveryPhone",
      "userId",
      "id",
      "externalIds",
      "updatedDate",
      "updatedBy"
    ]
  },
  "syncts": 1573121861125,
  "@timestamp": "2019-11-07T10:17:41.125Z",
  "flags": {
    "tv_processed": true,
    "dd_processed": true
  },
  "type": "events",
  "ts": "2019-11-07T10:17:41.118+0000"
}
```

**Source code:**

{% embed url="https://github.com/Sunbird-Lern/data-pipeline/tree/release-5.3.0/user-org-jobs/user-cache-updater-2.0" %}

### Additional Reading

{% embed url="https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/1520042020/Course+Infra+-+Async+Jobs+-+Implementation+Design" %}

{% embed url="https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/1782087720/Flink+jobs+for+certificates+generation+and+processing" %}

