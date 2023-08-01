# User cache updater

'user-cache-updater-2.0' job is used to generate the user-metadata information which is complied by fetching information from various Cassandra tables and are stored into the Redis cache. This user-metadata information is used by few exhaust reports.

#### Additional Reading:&#x20;

[https://project-sunbird.atlassian.net/wiki/spaces/AN/pages/1520074753/Design+Denormalise+User+Metadata](https://project-sunbird.atlassian.net/wiki/spaces/AN/pages/1520074753/Design+Denormalise+User+Metadata),&#x20;

#### Design guide:&#x20;

[https://lern.sunbird.org/learn/product-and-developer-guide/user-and-org-service/caching-and-denormalising-user-metadata/usercacheupdaterflinkjob](https://lern.sunbird.org/learn/product-and-developer-guide/user-and-org-service/caching-and-denormalising-user-metadata/usercacheupdaterflinkjob)

**Configuration variables:**

<table><thead><tr><th width="246">Variable</th><th>Default Value</th><th>Purpose</th></tr></thead><tbody><tr><td>kafka.input.topic</td><td>{{env}}.telemetry.audit</td><td>Kafka topic from which messages/events are read to be processed.</td></tr><tr><td>kafka.groupId</td><td>{{env}}-user-cache-updater-group</td><td>Kafka input topic group Id</td></tr><tr><td>redis-meta.database.userstore.id</td><td>12</td><td>Redis index to which user metadata is to be written to for caching</td></tr><tr><td>redis-meta.database.key.expiry.seconds</td><td>3600</td><td>Redis cache expiry in seconds</td></tr><tr><td>user-read.api.url</td><td>"/learner/private/user/v1/read"</td><td>API Endpoint for fetching User profile details</td></tr><tr><td>regd.user.producer.pid</td><td>learner-service</td><td>used to specify service providing user microservice</td></tr><tr><td>user.self.signin.types</td><td>["google","self"]</td><td>used to specify self sign-in modes available in application</td></tr><tr><td>user.validated.types</td><td>["sso"]</td><td>used to specify sign-in modes where user validation is signed from third party system</td></tr><tr><td>user.self.signin.key</td><td>"Self-Signed-In"</td><td></td></tr><tr><td>user.valid.key</td><td>"Validated"</td><td></td></tr><tr><td>user.read.url.fields</td><td>"locations,organisations"</td><td>used to specify the user metadata properties that are to be cached to Redis</td></tr><tr><td>user.read.api.error</td><td>["CLIENT_ERROR"]</td><td></td></tr></tbody></table>

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
