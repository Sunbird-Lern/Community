# Redis

Redis is used for caching the user details metadata. Redis key is \<uuid> of the user. (dbIndex: 12)

Redis data is updated by user cache updater flink job and also user cache indexer data product.&#x20;

{% embed url="https://lern.sunbird.org/learn/product-and-developer-guide/data-products/userorg/other-jobs/user-cache-indexer-job" %}

#### Sample Data:

```
HGETALL user:08631a74-4b94-4cf7-a818-831135248a4a
 1) "usersubtype"
 2) ""
 3) "board"
 4) "State (Tamil Nadu)"
 5) "subject"
 6) "[]"
 7) "email"
 8) "mqfHvB25AM9v+F86DWgPjE9tDNkvu6n6u1pqKAS9BqT9U4TkpKJju5BgSFzLp2VlxqPrgzDT5J\nhlKFh45G+E77Q53w5xYOrsbUoABF4Vci58JJHbN4Wzb2fV8/5Fl+T5ZUuUNdJcoZQazqPM4rCkTZ\nilMv5S3xBPGCQxJxIp8="
 9) "phone"
10) "lRpq1LqQ69CQ1SzAWRLuyEA7F1VH53KfAkxcXvCR22QKUkb2TdKftlbD1GltiFLBvHCrxqsOsl\n3eoQuhF0P+C2h4oA83Y+obFB6eagd2T5iGFTQ4RsFjBUMhUsdDrBT6a+wzaAmCWueMEdPmZuRg=="
11) "framework"
12) "tn_k-12_5"
13) "language"
14) ""
15) "userlogintype"
16) "teacher"
17) "district"
18) "CHITTOOR"
19) "orgname"
20) "Tamil Nadu"
21) "state"
22) "Andhra Pradesh"
23) "usersignintype"
24) "Validated"
25) "grade"
26) "[\"Class 1\",\"Class 2\",\"Class 10\",\"Class 11\",\"Class 12\"]"
27) "lastname"
28) ""
29) "rootorgid"
30) "01269878797503692810"
31) "profileusertypes"
32) "\\[{\"type\":\"teacher\"}\\]"
33) "medium"
34) "[\"Tamil\"]"
35) "firstname"
36) "content reviewer"
37) "userid"
38) "08631a74-4b94-4cf7-a818-831135248a4a"
39) "usertype"
40) "teacher"
```
