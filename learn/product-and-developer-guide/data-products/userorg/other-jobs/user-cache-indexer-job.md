# User Cache Indexer Job

The User Cache Indexer job reads user data from Cassandra, performs transformations and joins, and stores the processed data in Redis for caching and indexing purposes.&#x20;



<figure><img src="../../../../../.gitbook/assets/user_cache_indexer_job.png" alt=""><figcaption></figcaption></figure>

**Data provider:**

\
**Cassandra**

1. user
2. location

**User Redis**
