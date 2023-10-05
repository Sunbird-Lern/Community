# User Cache Indexer Job

The User Cache Indexer job reads user data from Cassandra, performs transformations and joins, and stores the processed data in Redis for caching and indexing purposes.&#x20;



<figure><img src="../../../../../.gitbook/assets/user_cache_indexer_job.png" alt=""><figcaption></figcaption></figure>

**Data provider:**

\
**Cassandra**

1. user
2. location

**User Redis**\
\
For more information please visit,\


{% content-ref url="../../caching-and-denormalising-user-metadata/usercacheupdaterflinkjob.md" %}
[usercacheupdaterflinkjob.md](../../caching-and-denormalising-user-metadata/usercacheupdaterflinkjob.md)
{% endcontent-ref %}

{% content-ref url="../../caching-and-denormalising-user-metadata/etlusercacheupdaterjob.md" %}
[etlusercacheupdaterjob.md](../../caching-and-denormalising-user-metadata/etlusercacheupdaterjob.md)
{% endcontent-ref %}
