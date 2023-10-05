# Relation Cache Updater

_**'relation-cache-updater'**_ job is used to perform one time compute and cache information such as leafNodes, optionalNodes, unitsMap and ancestorsMap of a collection to **Redis** when the collection is published. This data is utilised by other jobs and services.&#x20;

| Key                                         | Data format   | Sample                                                           |
| ------------------------------------------- | ------------- | ---------------------------------------------------------------- |
| \<collectionId>:leafnodes                   | List\<String> | collectionId:leafnodes: \[“resource1”,”resource2”]               |
| \<collectionId>:optionalnodes               | List\<String> | collectionId:optionalnodes: \[“resource1”,”resource2”]           |
| \<rootCollectionId>:\<resourceId>:ancestors | List\<String> | collectionId:resource1:ancestors: \[“courseunit1”, “democourse”] |

<div data-full-width="true">

<figure><img src="../../../../.gitbook/assets/relation-cache-updater.drawio (1).png" alt=""><figcaption></figcaption></figure>

</div>

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
