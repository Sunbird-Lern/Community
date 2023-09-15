# Activity Aggregate Updater

'activity-aggregate-updater' job updates the Course progress of the enrolled users and upon completion of the course, pushes an event to certificate pre-processor job to validate and issue certificate.

<div data-full-width="true">

<figure><img src="../../../../.gitbook/assets/Untitled Diagram-activity-aggregate-updater.drawio (1).png" alt=""><figcaption></figcaption></figure>

</div>

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
