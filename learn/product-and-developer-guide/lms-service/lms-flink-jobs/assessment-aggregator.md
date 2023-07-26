# Assessment Aggregator

_**'assessment-aggregator'**_ job is used to compute the course assessment content progress present as part of the Course. Job calculates the scores secured by the user during consumption against each Course Assessment Content.

<div data-full-width="true">

<figure><img src="../../../../.gitbook/assets/Untitled Diagram-assessment-aggregator.drawio.png" alt=""><figcaption></figcaption></figure>

</div>

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
