# Release V 5.0.0 (latest)

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date          | Version |
| ------- | --------------------- | ------- |
| Lern    | 04 Sep 22 (tentative) | V 5.0.0 |

### Details of Released Tag

| Components               |
| ------------------------ |
| Batch Service            |
| User\&Org Service        |
| Group Service            |
| Discussion Forum Service |
| Notification Service     |

### **Summary of the Changes** <a href="#1.-summary-of-the-changes" id="1.-summary-of-the-changes"></a>

* Migrating component repositories in to Lern organisation in GitHub as a first step in making the installation and setup easy for adopters and contributors
* Increasing code coverage and unit test cases of all the components in Lern as part of stabilising the components
* Refactoring of the provisioning and deployment scripts of Lern BB

### **Details of the Changes** <a href="#2.-details-of-the-changes" id="2.-details-of-the-changes"></a>

{% tabs %}
{% tab title="User&Org Service" %}
| JIRA ID                                                           | Descriptions                                         |
| ----------------------------------------------------------------- | ---------------------------------------------------- |
| [SB-30076](https://project-sunbird.atlassian.net/browse/SB-30076) | UserOrg - increase code coverage and unit test cases |
| [SB-30067](https://project-sunbird.atlassian.net/browse/SB-30067) | UserOrg - Deployment and Release processes           |
| [SB-29842](https://project-sunbird.atlassian.net/browse/SB-29842) | UserOrg Dataproducts Migration to Lern               |
| [SB-29826](https://project-sunbird.atlassian.net/browse/SB-29826) | Sunbird-apimanager-util migration to Lern            |
| [SB-29825](https://project-sunbird.atlassian.net/browse/SB-29825) | Sunbird-auth migration to Lern                       |
| [SB-29824](https://project-sunbird.atlassian.net/browse/SB-29824) | Sunbird-utils - DB Migration to Lern                 |
| [SB-29823](https://project-sunbird.atlassian.net/browse/SB-29823) | UserOrg Migration to Lern                            |
| [SB-29813](https://project-sunbird.atlassian.net/browse/SB-29813) | OrgSearch to allow partial search and fuzzy Search   |
{% endtab %}

{% tab title="Course Service" %}
| JIRA ID                                                           | Description                                                |
| ----------------------------------------------------------------- | ---------------------------------------------------------- |
| [SB-30075](https://project-sunbird.atlassian.net/browse/SB-30075) | Batch service - increase code coverage and unit test cases |
| [SB-29843](https://project-sunbird.atlassian.net/browse/SB-29843) | Batch service Dataproducts Migration to Lern               |
| [SB-30068](https://project-sunbird.atlassian.net/browse/SB-30068) | Batch service - Deployment and Release processes           |
| [SB-29841](https://project-sunbird.atlassian.net/browse/SB-29841) | assessment aggregate updater Migration to Lern             |
| [SB-29840](https://project-sunbird.atlassian.net/browse/SB-29840) | activity aggregate updater Migration to Lern               |
| [SB-29839](https://project-sunbird.atlassian.net/browse/SB-29839) | course-service migration to Lern                           |
| [SB-29837](https://project-sunbird.atlassian.net/browse/SB-29837) | enrolment-reconciliation Migration to Lern                 |
| [SB-29836](https://project-sunbird.atlassian.net/browse/SB-29836) | relation cache updater Migration to Lern                   |
| [SB-29835](https://project-sunbird.atlassian.net/browse/SB-29835) | colletion-certificate-generator Migration to Lern          |
| [SB-29834](https://project-sunbird.atlassian.net/browse/SB-29834) | collection-cert-pre-processor Migration to Lern            |
| [SB-29833](https://project-sunbird.atlassian.net/browse/SB-29833) | certificate processor Migration to Lern                    |
| [SB-29832](https://project-sunbird.atlassian.net/browse/SB-29832) | certificate-registry migration to Lern                     |
| [SB-29831](https://project-sunbird.atlassian.net/browse/SB-29831) | cert-service migration to Lern                             |


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


{% endtab %}

{% tab title="Notification Service" %}
| JIRA ID                                                           | Description                                                               |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------- |
| [SB-30077](https://project-sunbird.atlassian.net/browse/SB-30077) | Sunbird-notification-service - increase code coverage and unit test cases |
| [SB-29828](https://project-sunbird.atlassian.net/browse/SB-29828) | Sunbird-notification-jobs migration to Lern                               |
| [SB-29827](https://project-sunbird.atlassian.net/browse/SB-29827) | Sunbird-notification-service migration to Lern                            |
| [SB-30071](https://project-sunbird.atlassian.net/browse/SB-30071) | Sunbird-notification-service - Deployment and Release processes           |


{% endtab %}
{% endtabs %}

Detailed Information is present in the [JIRA](https://project-sunbird.atlassian.net/issues/?filter=12509) list.

Configurations:

1. Jenkins build, deploy and upload related changes for Flink jobs are present in below link:&#x20;

{% embed url="https://github.com/Sunbird-Lern/data-pipeline/tree/release-5.0.0/kubernetes/pipelines" %}

2\. There is a new variable added in devops repo to configure the bb name for kafka topics of flink jobs. This variable should be appended after the env name.

{% embed url="https://github.com/Sunbird-Lern/data-pipeline/blob/release-5.0.0/ansible/inventory/env/group_vars/all.yml#L10" %}

Topics with new variable appended are listed below:

```
kafka_assessment_topic: "{{env_name}}{{bb}}.telemetry.assess"
kafka_topics_instruction: "{{env_name}}{{bb}}.coursebatch.job.request"
kafka_topics_certificate_instruction: "{{env_name}}{{bb}}.issue.certificate.request"
kafka_topics_contentstate_invalid: "{{env_name}}{{bb}}.contentstate.invalid"
kafka_enrolment_sync_topic: "{{env_name}}{{bb}}.batch.enrolment.sync.request"
```

3\. Jenkins build, deploy and upload related changes for data products are in below link:

{% embed url="https://github.com/Sunbird-Lern/data-products/tree/release-5.0.0/pipelines" %}

4\. Jenkins build, deploy and upload related changes for microservices are in below link:

{% embed url="https://github.com/project-sunbird/sunbird-devops/tree/learn-bb" %}

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
