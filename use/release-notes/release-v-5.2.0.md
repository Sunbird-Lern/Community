# Release V 5.2.0

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date | Version |
| ------- | ------------ | ------- |
| Lern    | 27 MAR 23    | V 5.2.0 |

### Details of Released Tag

| Components          | Jenkins Job                  | Deploy Tags (Devops) | Build Tags (Github Repo Tags)                                                                                                                                                 | Github Repository                                                                                                |
| ------------------- | ---------------------------- | -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Batch Service       | Build/Core/Lms               | release-5.2.0        | <p>sunbird-course-service : <a href="https://github.com/Sunbird-Lern/sunbird-course-service/releases/tag/release-5.2.0_RC2">release-5.2.0_RC2</a></p><p><br></p>              | [https://github.com/Sunbird-Lern/sunbird-course-service](https://github.com/Sunbird-Lern/sunbird-course-service) |
| Data pipeline       | Build/Lern/FlinkJobs         | release-5.2.0        | <p>data-pipeline : <br><a href="https://github.com/Sunbird-Lern/data-pipeline/releases/tag/release-5.2.0_RC1">release-5.2.0_RC1</a></p>                                       | [https://github.com/Sunbird-Lern/data-pipeline](https://github.com/Sunbird-Lern/data-pipeline)                   |
| User\&Org Service   | Build/Core/Learner           | release-5.2.0        | sunbird-lms-service : [release-5.2.0\_RC1](http://localhost:5000/s/aQ7wCJOT0ZaejHUiD6sb/about/product-and-developer-guide/adapters/file-adapter/excel-ftp-and-sftp-handler)   | [https://github.com/Sunbird-Lern/sunbird-lms-service](https://github.com/Sunbird-Lern/sunbird-lms-service)       |
| Data Products       | Build/Lern/LernDataProducts/ | release-5.2.0        | <p>data-products : <br><a href="https://github.com/Sunbird-Lern/data-products/releases/tag/release-5.2.0_RC1">release-5.2.0_RC1</a></p>                                       | [https://github.com/Sunbird-Lern/data-products](https://github.com/Sunbird-Lern/data-products)                   |
| Cassandra Migration | Build/Core/Cassandra         | release-5.2.0        | sunbird-utils : [release-5.2.0\_RC1](https://github.com/Sunbird-Lern/sunbird-utils/releases/tag/release-5.2.0\_RC1)                                                           | [https://github.com/Sunbird-Lern/sunbird-utils](https://github.com/Sunbird-Lern/sunbird-utils)                   |

**Summary of the Changes**

* **Refactoring of Dial code dependency**: An API was developed to fetch QR code image URLs and resolve relative paths from the DIAL service instead of the current connection to the Cassandra table.
* **API automation using Postman for P0 APIs**
* **Movement of UserCache and UserCacheIndexer in Data Pipeline to Lern**
* **Test Automation for CSP**
* **Cassandra migration and grouping cql scripts with respect to keyspaces**
* **User detail report for programs**

\
**Bug Fixes** - click [here](https://project-sunbird.atlassian.net/browse/LR-405?jql=created%20%3E%3D%202023-02-22%20AND%20created%20%3C%3D%202023-03-22%20AND%20project%20%3D%20LR%20AND%20issuetype%20%3D%20Bug%20AND%20status%20in%20\(%22Failed%20Validation%22%2C%20%22In%20Development%22%2C%20%22In%20Validation%22%2C%20Open%2C%20%22Selected%20for%20Contribution%22\)%20AND%20affectedVersion%20in%20\(5.2.0%2C%205.2.0.0\)%20AND%20labels%20%3D%20External\_BB\_Issue%20ORDER%20BY%20created%20DESC) to see the list of bugs fixed as a part of this release.\
\
**Details of the Changes:**\
[LR-301](https://project-sunbird.atlassian.net/browse/LR-301) API automation using Postman for P0 APIs\
[LR-302](https://project-sunbird.atlassian.net/browse/LR-302) Movement of UserCacheIndexer Data Product to Lern \
[LR-303](https://project-sunbird.atlassian.net/browse/LR-303) Movement of UserCache in Data Pipeline to Lern\
[LR-306](https://project-sunbird.atlassian.net/browse/LR-306) Test Automation for CSP \
[LR-322](https://project-sunbird.atlassian.net/browse/LR-322) API automation using Newman for P0 APIs\
[LR-325](https://project-sunbird.atlassian.net/browse/LR-325) BatchService: Refactoring of SB Lern Batch Service - DialCode Dependency \
[LR-101](https://project-sunbird.atlassian.net/browse/LR-101) Cassandra migration and grouping cql scripts with respect to keyspaces\
[LR-307](https://project-sunbird.atlassian.net/browse/LR-307) Setting up a complete testing env for Lern with all other BBs\
[LR-285](https://project-sunbird.atlassian.net/browse/LR-285) User detail report for programs\
[LR-122](https://project-sunbird.atlassian.net/browse/LR-122) Lern repo and pod name correction to match the component name

### Env Configurations (Needs to be done before service deployment):

The below environment variable needs to be configured in the dev ops repo.

| Variable Name                       | Values                                                                    | Comments                                    |
| ----------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------- |
| sunbird\_dial\_service\_base\_url   | [https://sunbirddev.blob.core.windows.net](https://dev.lern.sunbird.org/) | To store the dial service base path         |
| sunbird\_dial\_service\_search\_url | /api/dialcode/v1/search                                                   | To store the search url of the dial service |

{% hint style="warning" %}
**Note: **<mark style="color:red;">**Only For the adopters who are migrating from the previous versions to 5.2.0, need to follow the following steps:**</mark>

* Create the cassandra\_migration\_version and cassandra\_migration\_version\_counts tables in respective keyspaces by using the below queries.
* Replace \<keyspace> with the below keyspace names,

&#x20;                   sunbird\_groups&#x20;

&#x20;                   sunbird\_notifications&#x20;

&#x20;                   sunbird\_courses

```sql
CREATE TABLE <keyspace>.cassandra_migration_version ( version text PRIMARY KEY, checksum int, description text, execution_time int, installed_by text, installed_on timestamp, installed_rank int, script text, success boolean, type text, version_rank int ) WITH bloom_filter_fp_chance = 0.01 AND caching = {'keys': 'ALL', 'rows_per_partition': 'NONE'} AND comment = '' AND compaction = {'class': 'org.apache.cassandra.db.compaction.SizeTieredCompactionStrategy', 'max_threshold': '32', 'min_threshold': '4'} AND compression = {'chunk_length_in_kb': '64', 'class': 'org.apache.cassandra.io.compress.LZ4Compressor'} AND crc_check_chance = 1.0 AND dclocal_read_repair_chance = 0.1 AND default_time_to_live = 0 AND gc_grace_seconds = 864000 AND max_index_interval = 2048 AND memtable_flush_period_in_ms = 0 AND min_index_interval = 128 AND read_repair_chance = 0.0 AND speculative_retry = '99PERCENTILE';
CREATE TABLE <keyspace>.cassandra_migration_version_counts ( name text PRIMARY KEY, count counter ) WITH bloom_filter_fp_chance = 0.01 AND caching = {'keys': 'ALL', 'rows_per_partition': 'NONE'} AND comment = '' AND compaction = {'class': 'org.apache.cassandra.db.compaction.SizeTieredCompactionStrategy', 'max_threshold': '32', 'min_threshold': '4'} AND compression = {'chunk_length_in_kb': '64', 'class': 'org.apache.cassandra.io.compress.LZ4Compressor'} AND crc_check_chance = 1.0 AND dclocal_read_repair_chance = 0.1 AND default_time_to_live = 0 AND gc_grace_seconds = 864000 AND max_index_interval = 2048 AND memtable_flush_period_in_ms = 0 AND min_index_interval = 128 AND read_repair_chance = 0.0 AND speculative_retry = '99PERCENTILE';
```

* To export cassandra\_migration\_version table COPY,

```sql
sunbird.cassandra_migration_version TO '/tmp/cassandra_migration_version.csv';
```

* To import cassandra\_migration\_version table COPY&#x20;

```
<keyspace>.cassandra_migration_version FROM '/tmp/cassandra_migration_version.csv';
```

* To export cassandra\_migration\_version\_count table COPY&#x20;

```
sunbird.cassandra_migration_version TO '/tmp/cassandra_migration_version_count.csv';
```

* To import cassandra\_migration\_version\_count table COPY&#x20;

```
<keyspace>.cassandra_migration_version_count FROM '/tmp/cassandra_migration_version_count.csv';
```
{% endhint %}

### Flink Job Configurations for Lern:

| Name of the Flink Job added |
| --------------------------- |
| **user-cache-updater-v2**   |
| **program-user-info**       |

<details>

<summary><a href="https://project-sunbird.atlassian.net/browse/LR-303">LR-303</a> - Movement of UserCache in Data Pipeline to Lern - setup/configuration details</summary>

Flink **build** Jenkins job name: **/Build/job/Lern/job/FlinkJobs**

Flink **deploy** Jenkins job name:&#x20;

**/Deploy/job/\<environment>/job/Lern/job/FlinkJobs/user-cache-updater-v2**\
\


</details>

<details>

<summary>LR-285 - User detail flink job for ML-programs - setup/configuration details:</summary>

For this ticket, we have only done unit testing with the help of simulated events. Integration testing has not been done as the required workflows concerning this will only be enabled after Ed 6.0 release. As part of this ticket we have enabled new Flink jobs and they in no way impact any existing workflows\
\
**Job name: program-user-info**

The purpose of this job is to record the user's information when the user submits the program. Whenever a program is submitted, this job receives an event with the user's information as JSON data and then it parses and stores it as respective key-value pairs in Cassandra.

**Keyspace name**: sunbird\_program

**Schema of the Kafka Topic:**\
**Kafka Topic Name**: `{{envName}}.ml.programUsers.raw`\
**Event** **Structure:-**

<pre class="language-json" data-overflow="wrap"><code class="lang-json"><strong>{
</strong>      programId: {
        type : "ObjectId",
        required : true,
        index: true
      },
      programName: String,
      programExternalId: String,
      noOfResourcesStarted: {
        type:Number,
        index: true
        }
      userId: {
        type: String,
        index: true
      },
      requestForPIIConsent:true/false
      userProfile: Object,
      userRoleInformation: Object,
      appInformation: Object,
      createdAt: Date,
      updatedAt: Date,
      deleted:Boolean
}
</code></pre>

**Job Configurations:**&#x20;

<pre><code><strong>kafka {
</strong> input.topic = ${job.env}".programuser.info"
 groupId = ${job.env}"-programuser-group"
}
task {
 consumer.parallelism = 1
 downstream.parallelism = 1
 programUser{
  parallelism = 1
 }
}
ml-cassandra {
 keyspace = "sunbird_programs"
 table = "program_enrollment"
 port = "9042"
 host =
 }
</code></pre>

Flink **build** Jenkins job name: **/Build/job/Lern/job/FlinkJobs**

Flink **deploy** Jenkins job name: **/Deploy/job/\<environment>/job/Lern/job/FlinkJobs/program-user-info**

Jenkins job for **building** Cassandra: **/Build/job/Core/job/Cassandra/**

Jenkins job for **deploying** Cassandra: **/Deploy/job/\<environment>/job/Kubernetes/job/Cassandra**

</details>

### **Data Product Configurations for Lern:**

| DataProduct Name |
| ---------------- |
| UserCacheIndexer |

<details>

<summary><a href="https://project-sunbird.atlassian.net/browse/LR-302">LR-302</a> <a href="https://project-sunbird.atlassian.net/browse/LR-302">Movement of UserCacheIndexer Data Product to Lern</a> - setup/configuration details</summary>

Please define the below configuration in Dataproducts (lern-data-products/src/main/resources/application.conf) for the UserCacheIndexerJob data product to work,

```
redis.host=__redis_host__
redis.port="6379"
redis.connection.max=20
location.db.redis.key.expiry.seconds=3600
redis.connection.idle.max=20
redis.connection.idle.min=10
redis.connection.minEvictableIdleTimeSeconds=120
redis.connection.timeBetweenEvictionRunsSeconds=300
redis.max.pipeline.size="100000"
#CassandraToRedis Config
spark.cassandra.connection.host="localhost"
cassandra.user.keyspace="sunbird"
cassandra.user.table="user"
redis.user.database.index="12"
redis.user.input.index="4"
redis.user.backup.dir="src/mount/data/analytics/content-snapshot/redisbackup"
redis.scan.count="100000"
redis.user.index.source.key="id" # this will be used as key for redis
cassandra.read.timeoutMS="500000"
cassandra.query.retry.count="100"
cassandra.input.consistency.level="LOCAL_QUORUM"
```

</details>