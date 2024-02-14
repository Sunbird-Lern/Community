# Collection Certificate Pre-Processor

_**'collection-cert-pre-processor'**_ job is used to perform the validation of certificate issuance criteria.&#x20;

<div data-full-width="true">

<figure><img src="../../../../.gitbook/assets/Cert Pre-processor.drawio.png" alt=""><figcaption></figcaption></figure>

</div>

**Configuration variables:**

<table><thead><tr><th width="246">Variable</th><th>Default Value</th><th>Purpose</th></tr></thead><tbody><tr><td>kafka.input.topic</td><td>{{env}}.issue.certificate.request</td><td>Kafka topic from which messages/events are read to be processed.</td></tr><tr><td>kafka.output.failed.topic</td><td>{{env}}.issue.certificate.failed</td><td>Kafka topic to which message is written when an exception occurs while processing an event.</td></tr><tr><td>kafka.output.topic</td><td>{{env}}.generate.certificate.request</td><td>Kafka topic used to trigger certificate generator job</td></tr><tr><td>kafka.groupId</td><td>{{env}}-collection-cert-pre-processor-group</td><td>Kafka input topic group Id</td></tr><tr><td>lms-cassandra.keyspace</td><td>sunbird_courses</td><td>Cassandra keyspace name</td></tr><tr><td>lms-cassandra.course_batch.table</td><td>course_batch</td><td>Cassandra table used to store batch details of a collection. Batch status, start date , end date , batch enrolment end date, enrolment type (open/invite-only), certificate templates etc are stored in this table.</td></tr><tr><td>lms-cassandra.user_enrolments.table</td><td>user_enrolments</td><td>Cassandra table used to store user enrolment data in a collection of a particular batch. This also holds the consumption progress, enrolment status and issued certificate details</td></tr><tr><td>lms-cassandra.assessment_aggregator.table</td><td>assessment_aggregator</td><td>Cassandra table used to store attempt wise data for each assessment in a collection of a batch by a user. Answer for each question in the assessment is also recorded.</td></tr><tr><td>lms-cassandra.user_activity_agg.table</td><td>user_activity_agg</td><td>Cassandra table used to store user consumption aggregate details of a collection in a batch. Aggregates like the consumption completed content count</td></tr><tr><td>redis.database.contentCache.id</td><td>5</td><td>Content cache is used to get assessment details from redis  to compute the score details. This content cache is gettig updated by using content-cache-updater flink job </td></tr><tr><td>redis.database.collectionCache.id</td><td>0</td><td>Collection cache is used to get the course details. This collection cache is gettig updated by using content-service.</td></tr><tr><td>cert_domain_url</td><td></td><td></td></tr><tr><td>user_read_api</td><td>/private/user/v1/read</td><td>API route for fetching user profile details</td></tr><tr><td>content_read_api</td><td>/content/v4/read</td><td>API route for fetching content metadata</td></tr><tr><td>service.content.basePath</td><td></td><td>Content service URL</td></tr><tr><td>service.learner.basePath</td><td></td><td>User-Org service URL</td></tr><tr><td>assessment.metrics.supported.contenttype</td><td>["SelfAssess"]</td><td>variable used to identify assessment type of contents in a Course</td></tr><tr><td>enable.suppress.exception</td><td>true</td><td>Variable used to suppress exception if the content metadata is not available in Redis cache</td></tr><tr><td>cloud_storage_base_url</td><td></td><td>variable to identify the cloud storage base url. Used to replace the base url with variable mentioned in cloud_store_base_path_placeholder while storing to databases</td></tr><tr><td>cloud_store_base_path_placeholder</td><td>CLOUD_BASE_PATH</td><td>relative variable used to replace cloud storage base URLs and stored in database</td></tr><tr><td>content_cloud_storage_container</td><td></td><td>cloud storage container name</td></tr><tr><td>cloud_storage_cname_url</td><td></td><td>variable used to replace 'cloud_store_base_path_placeholder' value with cname or cloud storage url while reading data from database.</td></tr></tbody></table>

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
