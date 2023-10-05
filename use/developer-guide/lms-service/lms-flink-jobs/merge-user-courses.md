# Merge User Courses

_**'merge-user-courses'**_ job will permit a user who owns multiple accounts on a sunbird platform (one on an Organisation tenant and one on the custodian tenant), to merge the course related usage history (course batch enrolments, course content consumption, course progress) into one primary account.&#x20;

This job performs following tasks:

* Merges the content consumption details from an account to primary account.
* Merges the user batches from an account to primary account.
* Merges the user activity aggregate data from an account to primary account.
* Performs a `batch-enrolment-sync` to primary account

<div data-full-width="true">

<figure><img src="../../../../.gitbook/assets/Untitled Diagram-merge-user-courses.drawio.png" alt=""><figcaption></figcaption></figure>

</div>

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
