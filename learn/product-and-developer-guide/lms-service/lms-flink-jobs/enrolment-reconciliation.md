# Enrolment Reconciliation

_**'enrolment-reconciliation'**_ job syncs the progress of the enrolled user. This job perform same tasks as 'activity-aggregator-updater' flink job. This is triggered by the user if the progress is not updated during course consumption.

<div data-full-width="true">

<figure><img src="../../../../.gitbook/assets/Untitled Diagram-enrolment-reconciliation.drawio.png" alt=""><figcaption></figcaption></figure>

</div>

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
