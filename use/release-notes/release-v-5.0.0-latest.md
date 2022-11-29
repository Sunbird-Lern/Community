# Release V 5.0.0

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date | Version |
| ------- | ------------ | ------- |
| Lern    | 18 Aug 22    | V 5.0.0 |

### Details of Released Tag

| Components               | Tags                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Batch Service            | <p>sunbird-course-service : <a href="https://github.com/Sunbird-Lern/sunbird-course-service/tree/release-5.0.0_RC6">release-5.0.0_RC6</a></p><p>cert-service : <a href="https://github.com/Sunbird-Lern/cert-service/tree/release-5.0.0_RC4">release-5.0.0_RC4</a></p><p>certficate-registry : <strong></strong> <a href="https://github.com/Sunbird-Lern/certificate-registry/releases/tag/release-5.0.0_RC1">release-5.0.0_RC1</a></p><p>data-pipeline : <a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-5.0.0_RC6">release-5.0.0_RC6</a></p> |
| User\&Org Service        | sunbird-lms-service : [ **** ](https://github.com/Sunbird-Lern/sunbird-lms-service/releases/tag/release-5.0.0\_RC1)[release-5.0.0\_RC5](https://github.com/Sunbird-Lern/sunbird-lms-service/tree/release-5.0.0\_RC5)                                                                                                                                                                                                                                                                                                                                                |
| Group Service            | groups-service : [release-5.0.0\_RC3](https://github.com/Sunbird-Lern/groups-service/tree/release-5.0.0\_RC3)                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Discussion Forum Service | <p>discussions-middleware : <a href="https://github.com/Sunbird-Lern/discussions-middleware/tree/release-5.0.0_RC2">release-5.0.0_RC2</a></p><p>sunbird-nodebb : <a href="https://github.com/Sunbird-Lern/sunbird-nodebb/releases/tag/release-5.0.0_RC1">release-5.0.0_RC1</a></p>                                                                                                                                                                                                                                                                                  |
| Notification Service     | sunbird-notification-service : [release-5.0.0\_RC6 ](https://github.com/Sunbird-Lern/sunbird-notification-service/releases/tag/release-5.0.0\_RC6)                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Data Products            | data-products : [release-5.0.0\_RC4](https://github.com/Sunbird-Lern/data-products/tree/release-5.0.0\_RC4)                                                                                                                                                                                                                                                                                                                                                                                                                                                         |

### **Summary of the Changes** <a href="#1.-summary-of-the-changes" id="1.-summary-of-the-changes"></a>

* Migrating component repositories in to Lern organisation in GitHub as a first step in making the installation and setup easy for adopters and contributors
* Increasing code coverage and unit test cases of all the components in Lern as part of stabilising the components
* Refactoring of the provisioning and deployment scripts of Lern BB
* Making SB Lern Cloud agnostic

### **Details of the Changes** <a href="#2.-details-of-the-changes" id="2.-details-of-the-changes"></a>

{% tabs %}
{% tab title="User&Org Service" %}
| JIRA ID                                                           | Descriptions                                                                                                                                                                 |
| ----------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [SB-30076](https://project-sunbird.atlassian.net/browse/SB-30076) | UserOrg - increase code coverage and unit test cases                                                                                                                         |
| [SB-30067](https://project-sunbird.atlassian.net/browse/SB-30067) | UserOrg - Deployment and Release processes                                                                                                                                   |
| [SB-29842](https://project-sunbird.atlassian.net/browse/SB-29842) | UserOrg Dataproducts Migration to Lern                                                                                                                                       |
| [SB-29826](https://project-sunbird.atlassian.net/browse/SB-29826) | Sunbird-apimanager-util migration to Lern                                                                                                                                    |
| [SB-29825](https://project-sunbird.atlassian.net/browse/SB-29825) | Sunbird-auth migration to Lern                                                                                                                                               |
| [SB-29824](https://project-sunbird.atlassian.net/browse/SB-29824) | Sunbird-utils - DB Migration to Lern                                                                                                                                         |
| [SB-29823](https://project-sunbird.atlassian.net/browse/SB-29823) | UserOrg Migration to Lern                                                                                                                                                    |
| [SB-29813](https://project-sunbird.atlassian.net/browse/SB-29813) | OrgSearch to allow partial search and fuzzy Search                                                                                                                           |
| [LR-103](https://project-sunbird.atlassian.net/browse/LR-103)     | Making SB Lern Cloud agnostic : Code changes to generalise CSP support in UserOrg                                                                                            |
| [LR-124](https://project-sunbird.atlassian.net/browse/LR-124)     | Cassandra related changes for supporting multiple Data Centers                                                                                                               |
| [LR-232](https://project-sunbird.atlassian.net/browse/LR-232)     | CSP changes for cert, learner & course service                                                                                                                               |
| [LR-128](https://project-sunbird.atlassian.net/browse/LR-128)     | [Data Migration related to CSP changes : Report url in Job\_request table needs to be updated](https://project-sunbird.atlassian.net/browse/LR-128)                          |
| [LR-125](https://project-sunbird.atlassian.net/browse/LR-125)     | [Data Migration related to CSP changes : Template url in DB Certificate Objects needs to be updated - batch tables](https://project-sunbird.atlassian.net/browse/LR-125)     |
| [LR-113](https://project-sunbird.atlassian.net/browse/LR-113)     | [Data Migration related to CSP changes : Existing reports need to be migrated](https://project-sunbird.atlassian.net/browse/LR-113)                                          |
| [LR-112](https://project-sunbird.atlassian.net/browse/LR-112)     | [Data Migration related to CSP changes : Credential template, context files to be stored in to new CSP](https://project-sunbird.atlassian.net/browse/LR-112)                 |
| [LR-111](https://project-sunbird.atlassian.net/browse/LR-111)     | [Data Migration related to CSP changes : Old Certificates in Azure needs to be migrated](https://project-sunbird.atlassian.net/browse/LR-111)                                |
| [LR-110](https://project-sunbird.atlassian.net/browse/LR-110)     | [Data Migration related to CSP changes : Template url in DB Certificate Objects needs to be updated - RC tables and ES](https://project-sunbird.atlassian.net/browse/LR-110) |
| [LR-109](https://project-sunbird.atlassian.net/browse/LR-109)     | [Data Migration related to CSP changes:Exisisting Certificate templates needs to be migrated.](https://project-sunbird.atlassian.net/browse/LR-109)                          |

Configurations:

```
Sunbird-lms-service:

isMultiDCEnabled={{cassandra_isMultiDCEnabled}}
sunbird_cassandra_consistency_level={{sunbird_cassandra_consistency_level}}
sunbird_user_cert_kafka_topic={{kafka_topic_lms_user_account}}
sunbird_cloud_service_provider={{cloud_service_provider}}
sunbird_account_name={{sunbird_public_storage_account_name}}
sunbird_account_key={{sunbird_public_storage_account_key}}
```
{% endtab %}

{% tab title="Batch Service" %}
| JIRA ID                                                           | Description                                                                             |
| ----------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| [SB-30075](https://project-sunbird.atlassian.net/browse/SB-30075) | Batch service - increase code coverage and unit test cases                              |
| [SB-29843](https://project-sunbird.atlassian.net/browse/SB-29843) | Batch service Dataproducts Migration to Lern                                            |
| [SB-30068](https://project-sunbird.atlassian.net/browse/SB-30068) | Batch service - Deployment and Release processes                                        |
| [SB-29841](https://project-sunbird.atlassian.net/browse/SB-29841) | assessment aggregate updater Migration to Lern                                          |
| [SB-29840](https://project-sunbird.atlassian.net/browse/SB-29840) | activity aggregate updater Migration to Lern                                            |
| [SB-29839](https://project-sunbird.atlassian.net/browse/SB-29839) | course-service migration to Lern                                                        |
| [SB-29837](https://project-sunbird.atlassian.net/browse/SB-29837) | enrolment-reconciliation Migration to Lern                                              |
| [SB-29836](https://project-sunbird.atlassian.net/browse/SB-29836) | relation cache updater Migration to Lern                                                |
| [SB-29835](https://project-sunbird.atlassian.net/browse/SB-29835) | colletion-certificate-generator Migration to Lern                                       |
| [SB-29834](https://project-sunbird.atlassian.net/browse/SB-29834) | collection-cert-pre-processor Migration to Lern                                         |
| [SB-29833](https://project-sunbird.atlassian.net/browse/SB-29833) | certificate processor Migration to Lern                                                 |
| [SB-29832](https://project-sunbird.atlassian.net/browse/SB-29832) | certificate-registry migration to Lern                                                  |
| [SB-29831](https://project-sunbird.atlassian.net/browse/SB-29831) | cert-service migration to Lern                                                          |
| [LR-104](https://project-sunbird.atlassian.net/browse/LR-104)     | Making SB Lern Cloud agnostic : Code changes to generalise CSP support in BatchService  |
| [LR-105](https://project-sunbird.atlassian.net/browse/LR-105)     | Making SB Lern Cloud agnostic : Code changes to generalise CSP support in datapipeline  |
| [LR-106](https://project-sunbird.atlassian.net/browse/LR-106)     | Making SB Lern Cloud agnostic : Code changes to generalise CSP support in data products |
| [LR-108](https://project-sunbird.atlassian.net/browse/LR-108)     | Signed URL Generation for old certificates - cert-service                               |
| [LR-107](https://project-sunbird.atlassian.net/browse/LR-107)     | RC deploy helm chart changes to upload Credential template, context files               |

Configurations:



```
https://github.com/project-sunbird/sunbird-devops/blob/learn-bb/ansible/roles/stack-sunbird/templates/
Sunbird-course-service:
isMultiDCEnabled={{cassandra_isMultiDCEnabled}}

# Add proper cloud service provider (azure,aws,gcloud)
sunbird_cloud_service_provider={{cloud_service_provider}}
sunbird_account_name={{sunbird_public_storage_account_name}}
sunbird_account_key={{sunbird_public_storage_account_key}}

#deleted the below variable
sunbird_content_azure_storage_container=sunbird-content-dev
# Added below variable for supporting multiple cloud service providers
# Provide corresponding cloud service provider(azure,aws,gcloud) container name here 
sunbird_content_cloud_storage_container=sunbird-content-dev
```

<pre><code>Cert-service:
CONTAINER_NAME={{cert_service_container_name}}
# Add proper cloud service provider (azure,aws,gcloud)
CLOUD_STORAGE_TYPE={{cloud_service_provider}}
PRIVATE_CLOUD_STORAGE_SECRET={{sunbird_private_storage_account_key}}
PRIVATE_CLOUD_STORAGE_KEY={{sunbird_private_storage_account_name}}
<strong>PUBLIC_CLOUD_STORAGE_KEY={{sunbird_public_storage_account_name}}
</strong>PUBLIC_CLOUD_STORAGE_SECRET={{sunbird_public_storage_account_key}}</code></pre>



```
Certificate-registry:
isMultiDCEnabled={{cassandra_isMultiDCEnabled}}
```



```
Data-pipeline:
isMultiDCEnabled={{cassandra_isMultiDCEnabled}}
# Add proper cloud service provider (azure,aws,gcloud)
cloud_storage_type :azure/aws/gcloud

```

```
data-products:
cloud_storage_type :azure/aws/gcloud
```
{% endtab %}

{% tab title="Discussion Forum" %}
| JIRA ID                                                           | Descriptions                                    |
| ----------------------------------------------------------------- | ----------------------------------------------- |
| [SB-30070](https://project-sunbird.atlassian.net/browse/SB-30070) | DF - Deployment and Release processes           |
| [SB-29820](https://project-sunbird.atlassian.net/browse/SB-29820) | DF Migration to Lern and deployment setup       |
| [SB-30073](https://project-sunbird.atlassian.net/browse/SB-30073) | DF - increase code coverage and unit test cases |
{% endtab %}

{% tab title="Group Service" %}
| JIRA ID                                                           | Description                                                |
| ----------------------------------------------------------------- | ---------------------------------------------------------- |
| [SB-30074](https://project-sunbird.atlassian.net/browse/SB-30074) | Group service - increase code coverage and unit test cases |
| [SB-30069](https://project-sunbird.atlassian.net/browse/SB-30069) | Group service - Deployment and Release processes           |
| [SB-29819](https://project-sunbird.atlassian.net/browse/SB-29819) | Group-service Migration to Lern and deployment setup       |

Configurations:

```
groups-service:
File Path:
cassandra-utils/src/main/resources/cassandra.config.properties
Changes:
isMultiDCEnabled=false

File Path:
sb-utils/src/main/resources/cassandra.config.properties
Changes:
isMultiDCEnabled=false
```
{% endtab %}

{% tab title="Notification Service" %}
| JIRA ID                                                           | Description                                                               |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------- |
| [SB-30077](https://project-sunbird.atlassian.net/browse/SB-30077) | Sunbird-notification-service - increase code coverage and unit test cases |
| [SB-29828](https://project-sunbird.atlassian.net/browse/SB-29828) | Sunbird-notification-jobs migration to Lern                               |
| [SB-29827](https://project-sunbird.atlassian.net/browse/SB-29827) | Sunbird-notification-service migration to Lern                            |
| [SB-30071](https://project-sunbird.atlassian.net/browse/SB-30071) | Sunbird-notification-service - Deployment and Release processes           |

Configurations:

```
Sunbird-notification-service:
File path:
sb-utils/src/main/resources/cassandra.config.properties
Changes:
isMultiDCEnabled=false
```
{% endtab %}
{% endtabs %}

Detailed Information is present in the [JIRA](https://project-sunbird.atlassian.net/issues/?filter=12509) list.

**Configurations:**

1. Nodebb upstream branch: v1.18.6
2. Jenkins build, deploy and upload related changes for Flink jobs are present in below link:&#x20;



{% embed url="https://github.com/Sunbird-Lern/data-pipeline/tree/release-5.0.0/kubernetes/pipelines" %}

3\. There is a new variable added in devops repo to configure the bb name for kafka topics of flink jobs. This variable should be appended after the env name.

{% embed url="https://github.com/Sunbird-Lern/data-pipeline/blob/release-5.0.0/ansible/inventory/env/group_vars/all.yml#L10" %}

```
List of Lern Flink jobs:

collection-cert-pre-processor
collection-certificate-generator
activity-aggregate-updater
relation-cache-updater
merge-user-courses
assessment-aggregator
enrolment-reconciliation
notification-job
```

```
env variable changes are listed below: 
kubernetes/ansible/roles/flink-jobs-deploy/defaults/main.yml

###  Merge User Courses Job related Vars
merge_user_courses_consumer_parallelism: 1
merge_user_courses_parallelism: 1
merge_user_courses_course_batch_parallelism: 1
merge_user_courses_course_date_format: "yyyy-MM-dd HH:mm:ss:SSSZ"

###  Notification Job related Vars
notification_job_consumer_parallelism: 1
notification_job_parallelism: 1

### assessment-aggregator related vars
assessaggregator_parallelism: 1
assessaggregator_consumer_parallelism: 1
assessaggregator_downstream_parallelism: 1
assessaggregator_scoreaggregator_parallelism: 1
middleware_cassandra_courses_keyspace: sunbird_courses
middleware_cassandra_assessment_aggregator_table: assessment_aggregator
middleware_cassandra_assessment_question_type : question
middleware_cassandra_user_enrolments_table: user_enrolments
middleware_cassandra_user_activity_agg_table: user_activity_agg
content_read_api_host: "http://dev.sunbirded.org"
content_read_api_endpoint: "/api/content/v1/read/"

merge-user-courses:
    job_class_name: 'org.sunbird.job.merge.user.courses.task.MergeUserCoursesStreamTask'
    replica: 1
    jobmanager_memory: 1024m
    taskmanager_memory: 1024m
    taskslots: 1
    cpu_requests: 0.3
  assessment-aggregator:
    job_class_name: 'org.sunbird.dp.assessment.task.AssessmentAggregatorStreamTask'
    replica: 1
    jobmanager_memory: 1024m
    taskmanager_memory: 1024m
    taskmanager_process_memory: 1700m
    jobmanager_process_memory: 1600m
    taskslots: 1
    cpu_requests: 0.3
    scale_enabled: false
  notification-job:
    job_class_name: 'org.sunbird.job.notification.task.NotificationStreamTask'
    replica: 1
    jobmanager_memory: 1024m
    taskmanager_memory: 1024m
    taskslots: 1
    cpu_requests: 0.3

Stop the existing Samza jobs - (merge-user-courses and notification-job)
Stop the assessment-aggregator job from sunbird-data-pipeline and remove it from the corresponding Jenkins job as well
All these 3 jobs will be running from LERN repo now
```

4\. Jenkins build, deploy and upload related changes for data products are in below link:

{% embed url="https://github.com/Sunbird-Lern/data-products/tree/release-5.0.0/pipelines" %}

```
LERN data-products list
  exhaust / progressexhaustjob
  exhaust / responseexhaust
  exhaust / userinfoexhaust
  job / course consumption
  job / course enrolment
  job / stateadminreport
  job / stateadmingeoreport
  job / collectionsummaryjobv2
  audit / collection reconcilation
  audit / coursebatch status updater
  updater / Cassandramigrator

```

5\. Jenkins build, deploy and upload related changes for microservices are in below link:

{% embed url="https://github.com/project-sunbird/sunbird-devops/tree/learn-bb" %}

**Devops config changes:**

{% code overflow="wrap" %}
```
File Path: 
ansible/inventory/env/group_vars/all.yml
### Release-5.0.0 cloud service provider changes for supporting multiple providers ###
### cloud_service_provider value should be either (azure, aws, gcloud) as per cloud sdk dependency ###
cloud_service_provider: "azure"

## modified consistency levels from quorum to local_quorum for multiple data centers support
File Path: 
ansible/roles/stack-sunbird/templates/sunbird_cert-registry-service.env
Changes:
sunbird_cassandra_consistency_level=local_quorum

File Path: 
ansible/roles/stack-sunbird/templates/sunbird_groups-service.env
Changes:
sunbird_cassandra_consistency_level=local_quorum

File Path: 
ansible/roles/stack-sunbird/templates/sunbird_learner-service.env
Changes:
sunbird_cassandra_consistency_level=local_quorum
sunbird_user_cert_kafka_topic={{env_name}}{{bb}}.lms.user.account.merge

File Path: 
ansible/roles/stack-sunbird/templates/sunbird_lms-service.env
Changes:
sunbird_cassandra_consistency_level=local_quorum

File Path: 
ansible/roles/stack-sunbird/templates/sunbird_notification-service.env
Changes:
sunbird_cassandra_consistency_level=local_quorum
sunbird_notification_kafka_topic={{env_name}}{{bb}}.lms.notification

File Path:
kubernetes/helm_charts/sunbird-RC/registry/schemas/TrainingCertificate.json
Changes:
"credentialTemplate": "https://{{upstream_url}}/schema/credential_template.json"

File Path:
utils/sunbird-RC/schema/credential_template.json
Changes:
"https://{{upstream_url}}/schema/v1_context.json",
 "https://{{upstream_url}}/schema/sunbird_context.json"
```
{% endcode %}

Design Documentation:

{% embed url="https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3077767171/Sunbird-Lern+Code+Flink+Jobs+and+Data+Products" %}
Sunbird-Lern Code, Flink Jobs and Data Products
{% endembed %}

{% embed url="https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3149922315/Lern+BB+repositories" %}
Lern BB repositories
{% endembed %}

{% embed url="https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3156869136/Sunbird-Lern+existing+jenkins+jobs" %}
Sunbird-Lern existing jenkins jobs
{% endembed %}
