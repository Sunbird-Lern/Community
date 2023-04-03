# Release V 5.2.0

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date | Version |
| ------- | ------------ | ------- |
| Lern    | 27 MAR 23    | V 5.2.0 |

### Details of Released Tag

| Components        | Jenkins Job                          | Deploy Tags (Devops) | Build Tags (Github Repo Tags)               | Github Repository                                                                                                | Comments |
| ----------------- | ------------------------------------ | -------------------- | ------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | -------- |
| Batch Service     | Build/Core/Lms                       | release-5.2.0        | <p>sunbird-course-service : </p><p><br></p> | [https://github.com/Sunbird-Lern/sunbird-course-service](https://github.com/Sunbird-Lern/sunbird-course-service) |          |
| Batch Service     | Build/job/Lern/job/FlinkJobs         | release-5.2.0        | <p>data-pipeline : <br></p>                 | [https://github.com/Sunbird-Lern/data-pipeline](https://github.com/Sunbird-Lern/data-pipeline)                   |          |
| User\&Org Service | Build/Core/Learner                   | release-5.2.0        | sunbird-lms-service :                       | [https://github.com/Sunbird-Lern/sunbird-lms-service](https://github.com/Sunbird-Lern/sunbird-lms-service)       |          |
| Data Products     | Build/job/Lern/job/LernDataProducts/ | release-5.2.0        | data-products :                             | [https://github.com/Sunbird-Lern/data-products](https://github.com/Sunbird-Lern/data-products)                   |          |
|                   |                                      |                      |                                             |                                                                                                                  |          |

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
<keyspace>.cassandra_migration_version TO '/tmp/cassandra_migration_version.csv';
```

* To import cassandra\_migration\_version table COPY&#x20;

```
<keyspace>.cassandra_migration_version FROM '/tmp/cassandra_migration_version.csv';
```

* To export cassandra\_migration\_version\_count table COPY&#x20;

```
<keyspace>.cassandra_migration_version TO '/tmp/cassandra_migration_version_count.csv';
```

* To import cassandra\_migration\_version\_count table COPY&#x20;

```
<keyspace>.cassandra_migration_version_count FROM '/tmp/cassandra_migration_version_count.csv';
```
{% endhint %}

Please define the below variables in data pipeline(lern-data-products/src/main/resources/application.conf) for the UserCacheIndexerJob to work,

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

****

**Summary of the Changes**

* **Refactoring of Dial code dependency**: An API was developed to fetch QR code image URLs and resolve relative paths from the DIAL service instead of the current connection to the Cassandra table.
* **API automation using Postman for P0 APIs**
* **Movement of UserCache and UserCacheIndexer in Data Pipeline to Lern**
* **Test Automation for CSP**
* **Bringing in Cassandra migration and cqls to respective component repos**

****\
**Affected Areas:**\
****\
****Batch service - Refactoring of Dialcode dependency\
****Addition of user cache and user cache indexer job to data products\
\
**Bug Fixes** - click [here](https://project-sunbird.atlassian.net/browse/LR-405?jql=created%20%3E%3D%202023-02-22%20AND%20created%20%3C%3D%202023-03-22%20AND%20project%20%3D%20LR%20AND%20issuetype%20%3D%20Bug%20AND%20status%20in%20\(%22Failed%20Validation%22%2C%20%22In%20Development%22%2C%20%22In%20Validation%22%2C%20Open%2C%20%22Selected%20for%20Contribution%22\)%20AND%20affectedVersion%20in%20\(5.2.0%2C%205.2.0.0\)%20AND%20labels%20%3D%20External\_BB\_Issue%20ORDER%20BY%20created%20DESC) to see the list of bugs fixed as a part of this release.\
\
**Details of the Changes:**\
****[LR-301](https://project-sunbird.atlassian.net/browse/LR-301) API automation using Postman for P0 APIs\
[LR-302](https://project-sunbird.atlassian.net/browse/LR-302) Movement of UserCacheIndexer Data Product to Lern \
[LR-303](https://project-sunbird.atlassian.net/browse/LR-303) Movement of UserCache in Data Pipeline to Lern\
[LR-306](https://project-sunbird.atlassian.net/browse/LR-306) Test Automation for CSP \
[LR-322](https://project-sunbird.atlassian.net/browse/LR-322) API automation using Newman for P0 APIs\
[LR-325](https://project-sunbird.atlassian.net/browse/LR-325) BatchService: Refactoring of SB Lern Batch Service - DialCode Dependency \
[LR-101](https://project-sunbird.atlassian.net/browse/LR-101) Bring in Cassandra migration and cqls to respective component repos\
[LR-307](https://project-sunbird.atlassian.net/browse/LR-307) Setting up a complete testing env for Lern with all other BBs\
[LR-285](https://project-sunbird.atlassian.net/browse/LR-285) User detail report for programs\
\


[LR-122](https://project-sunbird.atlassian.net/browse/LR-122) Lern repo and pod name correction to match the component name
