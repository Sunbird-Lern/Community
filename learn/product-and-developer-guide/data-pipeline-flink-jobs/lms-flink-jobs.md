---
description: This page details about the Flink Jobs present as part of LERN Building block.
---

# Flink Jobs

Flink Jobs in LERN have been to developed to support LMS (Learning Management System) journey of a user. Jobs are used to compute data necessary to calculate user's progress and validate the same against certificate issuance criteria and then trigger Sunbird RC to create and issue certificate to the user.&#x20;

&#x20;

<figure><img src="../../../.gitbook/assets/OVERVIEW - LERN JOBS.drawio (1) (1).png" alt=""><figcaption><p><strong>Data-pipeline Overview Diagram</strong></p></figcaption></figure>

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

<table><thead><tr><th width="241">Variable</th><th width="273">Default Value</th><th>Purpose</th></tr></thead><tbody><tr><td>kafka.input.topic</td><td>{{env}}.lms.user.account.merge</td><td>Kafka topic from which messages/events are read to be processed.</td></tr><tr><td>kafka.output.failed.topic</td><td>{{env}}.learning.events.failed</td><td>Kafka topic to which message is written when an exception occurs while processing an event.</td></tr><tr><td>kafka.groupId</td><td></td><td>Kafka input topic group Id</td></tr><tr><td>kafka.output.course.batch.updater.topic</td><td>{{env}}.coursebatch.job.request</td><td>Kafka topic to which output message/event is inserted to perform user course progress activity reconciliation to merged Id</td></tr><tr><td>lms-cassandra.keyspace</td><td>sunbird_courses</td><td>Cassandra keyspace name</td></tr><tr><td>lms-cassandra.content_consumption.table</td><td>user_content_consumption</td><td>Cassandra table used to store content wise data for a collection of a batch by a user. Content progress, status etc</td></tr><tr><td>lms-cassandra.user_enrolments.table</td><td>user_enrolments</td><td>Cassandra table used to store user enrolment data in a collection of a particular batch. This also holds the consumption progress, enrolment status and issued certificate details</td></tr><tr><td>lms-cassandra.user_activity_agg.table</td><td>user_activity_agg</td><td>Cassandra table used to store user consumption aggregate details of a collection in a batch. Aggregates like the consumption completed content count</td></tr></tbody></table>

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

<table><thead><tr><th width="246">Variable</th><th>Default Value</th><th>Purpose</th></tr></thead><tbody><tr><td>kafka.input.topic</td><td>{{env}}.lms.user.account.merge</td><td>Kafka topic from which messages/events are read to be processed.</td></tr><tr><td>kafka.groupId</td><td>{{env}}-relation-cache-updater-group</td><td>Kafka input topic group Id</td></tr><tr><td>lms-cassandra.keyspace</td><td>{{env}}_hierarchy_store</td><td>Cassandra keyspace name</td></tr><tr><td>lms-cassandra.table</td><td>content_hierarchy</td><td>Cassandra table used to read collection hierarchy.</td></tr><tr><td>redis.database.index</td><td>10</td><td>Redis index to which computed data like <strong>leafnodes</strong> and <strong>optionalnodes</strong> is stored</td></tr><tr><td>dp-redis.host</td><td>IP should be same as lp-redis host</td><td>dp-redis (data-pipeline redis) IP should be kept same as lp-redis (learning-platform) redis in order to be able to read pulished collection information</td></tr><tr><td>dp-redis.port</td><td>port should be same as lp-redis port</td><td>dp-redis port</td></tr><tr><td>dp-redis.database.index</td><td>5</td><td>Redis index to which computed data 'units map' is stored</td></tr></tbody></table>

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

<table><thead><tr><th width="246">Variable</th><th>Default Value</th><th>Purpose</th></tr></thead><tbody><tr><td>kafka.input.topic</td><td>{{env}}.coursebatch.job.request</td><td>Kafka topic from which messages/events are read to be processed.</td></tr><tr><td>kafka.output.failed.topic</td><td>{{env}}.activity.agg.failed</td><td>Kafka topic to which message is written when an exception occurs while processing an event.</td></tr><tr><td>kafka.audit.topic</td><td>{{env}}.telemetry.raw</td><td>Kakfa topic to which and audit message is written to.</td></tr><tr><td>kafka.certissue.topic</td><td>{{env}}.issue.certificate.request</td><td>Kafka topic used to trigger certificate issue pre-processor job</td></tr><tr><td>kafka.groupId</td><td>{{env}}-activity-aggregate-updater-group</td><td>Kafka input topic group Id</td></tr><tr><td>lms-cassandra.keyspace</td><td>sunbird_courses</td><td>Cassandra keyspace name</td></tr><tr><td>lms-cassandra.content_consumption.table</td><td>user_content_consumption</td><td>Cassandra table used to store content wise data for a collection of a batch by a user. Content progress, status etc</td></tr><tr><td>lms-cassandra.user_enrolments.table</td><td>user_enrolments</td><td>Cassandra table used to store user enrolment data in a collection of a particular batch. This also holds the consumption progress, enrolment status and issued certificate details</td></tr><tr><td>lms-cassandra.user_activity_agg.table</td><td>user_activity_agg</td><td>Cassandra table used to store user consumption aggregate details of a collection in a batch. Aggregates like the consumption completed content count</td></tr><tr><td>redis.database.relationCache.id</td><td>10</td><td>Redis index from which computed data like leafnodes and optionalnodes is read. </td></tr><tr><td>dedup-redis.host</td><td>IP of deduplicate Redis host</td><td>De-duplication Redis is used to remove duplicate events possibly part of the events list in kafka input topic which is fetched in batch size of 'threshold.batch.read.size' parameter mentioned below.</td></tr><tr><td>dedup-redis.port</td><td>port</td><td>port of deduplicate Redis </td></tr><tr><td>dedup-redis.database.index</td><td>13</td><td>De-duplication Redis index</td></tr><tr><td>dedup-redis.database.expiry</td><td>604800</td><td>De-duplication Redis Expiry time</td></tr><tr><td>threshold.batch.read.interval</td><td></td><td>NOT USED</td></tr><tr><td>threshold.batch.read.size</td><td>1000</td><td>Flink stream window size</td></tr><tr><td>threshold.batch.write.size</td><td>10</td><td>Property used to specify batch size of the database update queries while updating a specific cassandra table in batch format</td></tr><tr><td>activity.module.aggs.enabled</td><td>true</td><td>Used to configure if the consumption aggregation calculation is to be enabled on course leaf nodes </td></tr><tr><td>activity.input.dedup.enabled</td><td>true</td><td>Used to configure if the aggregation job is to run in De-duplication mode</td></tr><tr><td>activity.filter.processed.enrolments</td><td>true</td><td>Used to configure if the activity aggregation process is to be skipped for user enrolments with status 2 (completed courses)</td></tr><tr><td>activity.collection.status.cache.expiry</td><td>3600 (in seconds)</td><td>Expiry time of TTL cache set  to read or store latest collection 'status' information. If latest TTL cache doesnt have collection 'status' information, then the same is read from Search service configured below and TTL cache will be updated.</td></tr><tr><td>service.search.basePath</td><td>IP of the search service</td><td>IP of the search service</td></tr></tbody></table>

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

<table><thead><tr><th width="246">Variable</th><th>Default Value</th><th>Purpose</th></tr></thead><tbody><tr><td>kafka.input.topic</td><td>{{env}}.telemetry.assess</td><td>Kafka topic from which messages/events are read to be processed.</td></tr><tr><td>kafka.output.failed.topic</td><td>{{env}}.telemetry.assess.failed</td><td>Kafka topic to which message is written when an exception occurs while processing an event.</td></tr><tr><td>kafka.output.certissue.topic</td><td>{{env}}.issue.certificate.request</td><td>Kafka topic used to trigger certificate issue pre-processor job</td></tr><tr><td>kafka.groupId</td><td>{{env}}-assessment-aggregator-group</td><td>Kafka input topic group Id</td></tr><tr><td>lms-cassandra.keyspace</td><td>sunbird_courses</td><td>Cassandra keyspace name</td></tr><tr><td>lms-cassandra.table</td><td>assessment_aggregator</td><td>Cassandra table used to store attempt wise data for each assessment in a collection of a batch by a user. Answer for each question in the assessment is also recorded.</td></tr><tr><td>lms-cassandra.enrolmentstable</td><td>user_enrolments</td><td>Cassandra table used to store user enrolment data in a collection of a particular batch. This also holds the consumption progress, enrolment status and issued certificate details</td></tr><tr><td>lms-cassandra.activityytable</td><td>user_activity_agg</td><td>Cassandra table used to store user consumption aggregate details of a collection in a batch. Aggregates like the consumption completed content count</td></tr><tr><td>lms-cassandra.questionudttype</td><td>question</td><td>Cassandra table used to store each question information.</td></tr><tr><td>redis.database.relationCache.id</td><td>10</td><td>Redis index from which computed data like leafnodes and optionalnodes is read. </td></tr><tr><td>redis.database.contentCache.id</td><td>5</td><td>Redis index from which Content metadata is read from.</td></tr><tr><td>assessment.skip.missingRecords</td><td>false</td><td>Variable used to mention if the event processing is to be skipped in case of 'the totalQuestions Count value is not matching with the event size then job should skip those events and increase the metrics value'.</td></tr><tr><td>user.activity.agg.type</td><td>attempt_metrics</td><td></td></tr><tr><td>content.read.api</td><td>Endpoint URL of content read API</td><td>Endpoint URL of content read API part of content-service</td></tr></tbody></table>

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

<table><thead><tr><th width="246">Variable</th><th>Default Value</th><th>Purpose</th></tr></thead><tbody><tr><td>kafka.input.topic</td><td>{{env}}.batch.enrolment.sync.request</td><td>Kafka topic from which messages/events are read to be processed.</td></tr><tr><td>kafka.output.failed.topic</td><td>{{env}}.enrolment.reconciliation.failed</td><td>Kafka topic to which message is written when an exception occurs while processing an event.</td></tr><tr><td>kafka.audit.topic</td><td>{{env}}.telemetry.raw</td><td>Kakfa topic to which and audit message is written to.</td></tr><tr><td>kafka.certissue.topic</td><td>{{env}}.issue.certificate.request</td><td>Kafka topic used to trigger certificate issue pre-processor job</td></tr><tr><td>kafka.groupId</td><td>{{env}}-enrolment-reconciliation-group</td><td>Kafka input topic group Id</td></tr><tr><td>lms-cassandra.keyspace</td><td>sunbird_courses</td><td>Cassandra keyspace name</td></tr><tr><td>lms-cassandra.content_consumption.table</td><td>user_content_consumption</td><td>Cassandra table used to store content wise data for a collection of a batch by a user. Content progress, status etc</td></tr><tr><td>lms-cassandra.user_enrolments.table</td><td>user_enrolments</td><td>Cassandra table used to store user enrolment data in a collection of a particular batch. This also holds the consumption progress, enrolment status and issued certificate details</td></tr><tr><td>lms-cassandra.user_activity_agg.table</td><td>user_activity_agg</td><td>Cassandra table used to store user consumption aggregate details of a collection in a batch. Aggregates like the consumption completed content count</td></tr><tr><td>redis.database.relationCache.id</td><td>10</td><td>Redis index from which computed data like leafnodes and optionalnodes is read. </td></tr><tr><td>threshold.batch.write.size</td><td>10</td><td>Property used to specify batch size of the database update queries while updating a specific cassandra table in batch format</td></tr><tr><td>activity.module.aggs.enabled</td><td>true</td><td>Used to configure if the consumption aggregation calculation is to be enabled on course leaf nodes </td></tr><tr><td>activity.filter.processed.enrolments</td><td>true</td><td>Used to configure if the activity aggregation process is to be skipped for user enrolments with status 2 (completed courses)</td></tr><tr><td>activity.collection.status.cache.expiry</td><td>3600 (in seconds)</td><td>Expiry time of TTL cache set  to read or store latest collection 'status' information. If latest TTL cache doesnt have collection 'status' information, then the same is read from Search service configured below and TTL cache will be updated.</td></tr><tr><td>service.search.basePath</td><td>IP of the search service</td><td>IP of the search service</td></tr></tbody></table>

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

<table><thead><tr><th width="246">Variable</th><th>Default Value</th><th>Purpose</th></tr></thead><tbody><tr><td>kafka.input.topic</td><td>{{env}}.issue.certificate.request</td><td>Kafka topic from which messages/events are read to be processed.</td></tr><tr><td>kafka.output.failed.topic</td><td>{{env}}.issue.certificate.failed</td><td>Kafka topic to which message is written when an exception occurs while processing an event.</td></tr><tr><td>kafka.output.topic</td><td>{{env}}.generate.certificate.request</td><td>Kafka topic used to trigger certificate generator job</td></tr><tr><td>kafka.groupId</td><td>{{env}}-collection-cert-pre-processor-group</td><td>Kafka input topic group Id</td></tr><tr><td>lms-cassandra.keyspace</td><td>sunbird_courses</td><td>Cassandra keyspace name</td></tr><tr><td>lms-cassandra.course_batch.table</td><td>course_batch</td><td>Cassandra table used to store batch details of a collection. Batch status, start date , end date , batch enrolment end date, enrolment type (open/invite-only), certificate templates etc are stored in this table.</td></tr><tr><td>lms-cassandra.user_enrolments.table</td><td>user_enrolments</td><td>Cassandra table used to store user enrolment data in a collection of a particular batch. This also holds the consumption progress, enrolment status and issued certificate details</td></tr><tr><td>lms-cassandra.assessment_aggregator.table</td><td>assessment_aggregator</td><td>Cassandra table used to store attempt wise data for each assessment in a collection of a batch by a user. Answer for each question in the assessment is also recorded.</td></tr><tr><td>lms-cassandra.user_activity_agg.table</td><td>user_activity_agg</td><td>Cassandra table used to store user consumption aggregate details of a collection in a batch. Aggregates like the consumption completed content count</td></tr><tr><td>cert_domain_url</td><td></td><td></td></tr><tr><td>user_read_api</td><td>/private/user/v1/read</td><td>API route for fetching user profile details</td></tr><tr><td>content_read_api</td><td>/content/v4/read</td><td>API route for fetching content metadata</td></tr><tr><td>service.content.basePath</td><td></td><td>Content service URL</td></tr><tr><td>service.learner.basePath</td><td></td><td>User-Org service URL</td></tr><tr><td>assessment.metrics.supported.contenttype</td><td>["SelfAssess"]</td><td>variable used to identify assessment type of contents in a Course</td></tr><tr><td>enable.suppress.exception</td><td>true</td><td>Variable used to suppress exception if the content metadata is not available in Redis cache</td></tr><tr><td>cloud_storage_base_url</td><td></td><td>variable to identify the cloud storage base url. Used to replace the base url with variable mentioned in cloud_store_base_path_placeholder while storing to databases</td></tr><tr><td>cloud_store_base_path_placeholder</td><td>CLOUD_BASE_PATH</td><td>relative variable used to replace cloud storage base URLs and stored in database</td></tr><tr><td>content_cloud_storage_container</td><td></td><td>cloud storage container name</td></tr><tr><td>cloud_storage_cname_url</td><td></td><td>variable used to replace 'cloud_store_base_path_placeholder' value with cname or cloud storage url while reading data from database.</td></tr></tbody></table>

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

<table><thead><tr><th width="246">Variable</th><th>Default Value</th><th>Purpose</th></tr></thead><tbody><tr><td>kafka.input.topic</td><td>{{env}}.generate.certificate.request</td><td>Kafka topic from which messages/events are read to be processed.</td></tr><tr><td>kafka.output.failed.topic</td><td>{{env}}.generate.certificate.failed</td><td>Kafka topic to which message is written when an exception occurs while processing an event.</td></tr><tr><td>kafka.output.audit.topic</td><td>{{env}}.telemetry.raw</td><td>Kakfa topic to which and audit message is written to.</td></tr><tr><td>kafka.groupId</td><td>{{env}}-certificate-generator-group</td><td>Kafka input topic group Id</td></tr><tr><td>lms-cassandra.keyspace</td><td>sunbird_courses</td><td>Cassandra keyspace name</td></tr><tr><td>lms-cassandra.course_batch.table</td><td>course_batch</td><td>Cassandra table used to store batch details of a collection. Batch status, start date , end date , batch enrolment end date, enrolment type (open/invite-only), certificate templates etc are stored in this table.</td></tr><tr><td>lms-cassandra.user_enrolments.table</td><td>user_enrolments</td><td>Cassandra table used to store user enrolment data in a collection of a particular batch. This also holds the consumption progress, enrolment status and issued certificate details</td></tr><tr><td>lms-cassandra.sbkeyspace</td><td>sunbird</td><td>Sunbird Keyspace</td></tr><tr><td>lms-cassandra.certreg.table</td><td>cert_registry</td><td>Cassandra table used to store user certificates (old format)</td></tr><tr><td>task.rc.badcharlist</td><td>\x00,\\aaa,\aaa,Ø,Ý</td><td></td></tr><tr><td>service.content.basePath</td><td></td><td>Content service URL</td></tr><tr><td>service.learner.basePath</td><td></td><td>User-Org service URL</td></tr><tr><td>service.enc.basePath</td><td></td><td>Encryption service base path</td></tr><tr><td>service.rc.basePath</td><td></td><td>Sunbird RC base path</td></tr><tr><td>service.rc.entity</td><td>TrainingCertificate</td><td>variable used to specify sunbird RC API endpoint for certificate</td></tr><tr><td>enable.rc.certificate</td><td>true</td><td>variable used to enable RC certificate generation</td></tr><tr><td>enable.suppress.exception</td><td>true</td><td>Variable used to suppress exception if the signatory list is empty</td></tr><tr><td>cloud_storage_base_url</td><td></td><td>variable to identify the cloud storage base url. Used to replace the base url with variable mentioned in cloud_store_base_path_placeholder while storing to databases</td></tr><tr><td>cloud_store_base_path_placeholder</td><td>CLOUD_BASE_PATH</td><td>relative variable used to replace cloud storage base urls and stored in database</td></tr><tr><td>content_cloud_storage_container</td><td></td><td>cloud storage container name</td></tr><tr><td>cloud_storage_cname_url</td><td></td><td>variable used to replace 'cloud_store_base_path_placeholder' value with cname or cloud storage url while reading data from database.</td></tr></tbody></table>

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

### Additional Reading

{% embed url="https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/1520042020/Course+Infra+-+Async+Jobs+-+Implementation+Design" %}

{% embed url="https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/1782087720/Flink+jobs+for+certificates+generation+and+processing" %}

