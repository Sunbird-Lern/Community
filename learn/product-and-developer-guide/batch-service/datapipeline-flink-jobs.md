---
description: This page details about the Flink Jobs created as part of LERN Building block.
---

# Datapipeline (Flink Jobs)

Flink Jobs in LERN have been to developed to support LMS (Learning Management System) journey of a user. Jobs are used to compute data necessary to calculate user's progress and validate the same against certificate issuance criteria and then trigger Sunbird RC to create and issue certificate to the user.&#x20;

&#x20;

<figure><img src="../../../.gitbook/assets/OVERVIEW - LERN JOBS.drawio.png" alt=""><figcaption><p><strong>Data Flow Overview Diagram</strong></p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/V3 LERN - CERTIFICATE GENERATION FLOW.drawio.png" alt=""><figcaption></figcaption></figure>





1\. [Merge User Courses Job](https://project-sunbird.atlassian.net/wiki/spaces/SLBB/pages/3129704449/SB-28061+Migrate+Merge-User-Courses+samza+to+flink+job)

2\. [Relation Cache Updater](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/1520042020/Course+Infra+-+Async+Jobs+-+Implementation+Design)

When publish-pipeline job(Sunbird-Knowlg BB) complete processing a content publishing, it pushes an event to post-publish-processor topic.

Relation Cache updater use this “post-publish-processor” as input and generate the below relation-cache **which is complex to compute and use** by many micro-services of the platform at runtime. Sample data stored by this job in redis:

| **Key**                                     | **Value**     | **Sample**                                                     |
| ------------------------------------------- | ------------- | -------------------------------------------------------------- |
| \<collectionId>:leafnodes                   | List\<String> | courseunit1:leafnodes: \[“resource1”,”resource2”,]             |
| \<rootCollectionId>:\<resourceId>:ancestors | List\<String> | democourse:resource1:ancestors: \[“courseunit1”, “democourse”] |

3\. Assessment Aggregator ([Courses Infra - Design](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/1493041222/Courses+Infra+-+Design))

4\. Activity Aggregate Updater

5\. Certificate Processor ([Flink jobs for certificates generation and processing](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/1782087720/Flink+jobs+for+certificates+generation+and+processing))

6\. Collection Cert Pre-Processor

7\. Collection Certificate Generator&#x20;



