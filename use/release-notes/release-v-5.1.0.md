# Release V 5.1.0

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date | Version |
| ------- | ------------ | ------- |
| Lern    | 31 Jan 23    | V 5.1.0 |

### Details of Released Tag

| Components        | Jenkins Job                          | Deploy Tags (Devops) | Build Tags (Github Repo Tags)                                                                                                                                                                                                   | Github Repository                                                                                                | Comments                                                                                 |
| ----------------- | ------------------------------------ | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| Batch Service     | Build/Core/Lms                       | release-5.1.0\_RC1   | <p>sunbird-course-service : <a href="https://github.com/Sunbird-Lern/sunbird-course-service/releases/tag/release-5.1.0_RC1">release-5.1.0_RC</a>1</p><p><br></p>                                                                | [https://github.com/Sunbird-Lern/sunbird-course-service](https://github.com/Sunbird-Lern/sunbird-course-service) |                                                                                          |
| Batch Service     | Build/job/Lern/job/FlinkJobs         | release-5.1.0\_RC1   | <p>data-pipeline : <a href="https://github.com/Sunbird-Lern/data-pipeline/releases/tag/release-5.0.1_RC5">release-5.0.1_RC5</a></p><p><br></p>                                                                                  | [https://github.com/Sunbird-Lern/data-pipeline](https://github.com/Sunbird-Lern/data-pipeline)                   | relational-cache-updater, avtivity-aggregate-updater jobs need to be deployed |
| User\&Org Service | Build/Core/Learner                   | release-5.1.0\_RC1   | sunbird-lms-service : [\*\*\*\* ](https://github.com/Sunbird-Lern/sunbird-lms-service/releases/tag/release-5.1.0\_RC1)[release-5.0.1\_RC1](https://github.com/Sunbird-Lern/sunbird-lms-service/releases/tag/release-5.1.0\_RC1) | [https://github.com/Sunbird-Lern/sunbird-lms-service](https://github.com/Sunbird-Lern/sunbird-lms-service)       |                                                                                          |
| Data Products     | Build/job/Lern/job/LernDataProducts/ | release-5.1.0\_RC1   | <p>data-products : <a href="https://github.com/Sunbird-Lern/data-products/releases/tag/release-5.1.0_RC1">release-5.1.0_RC1</a></p><p></p>                                                                                      | [https://github.com/Sunbird-Lern/data-products](https://github.com/Sunbird-Lern/data-products)                   |                                                                                          |

### **Summary of the Changes** <a href="#1.-summary-of-the-changes" id="1.-summary-of-the-changes"></a>

*  SB Lern

#### Affected Areas:

* Flink Jobs - RelationCacheUpdate, ActivityAggregateUpdater for removing optional contents from course complete caluculation
* Keyclock made optional for authentication related api's
* Exhaust Reports - Progress Exhaust

### Details of the Changes

[LR-1 ](https://project-sunbird.atlassian.net/browse/LR-1)Backend :: Support for optional material in a course

[LR-4 ](https://project-sunbird.atlassian.net/browse/LR-4)Design on Migration of existing certificate in to RC

[LR-241 ](https://project-sunbird.atlassian.net/browse/LR-241)UserOrg: Identity manager should be optional for setup

[LR-251 ](https://project-sunbird.atlassian.net/browse/LR-251)BatchService : Identity manager should be optional for setup

### Env Configurations (Needs to be done before service deployment):

The below environment variable needs to be configured in the devops repo.

| Variable Name              | Values                                   | Comments                          |
| -------------------------- | ---------------------------------------- | --------------------------------- |
| cloud\_storage\_base\_url  | https://sunbirddev.blob.core.windows.net | To store the CSP base path        |
| cloud\_storage\_cname\_url | https://obj.dev.sunbirded.org            | To store the cname url of the CSP |

<details>

<summary>Ansible Changes need to be updated in Common.yml, secrets.yml, hosts.yml</summary>

```
sunbird-devops-private/ansible/inventory/{{env}}/KnowledgePlatform

hosts:

## Lern dataproducts
[learning]

[raw-broker]

[report-cassandra]

[raw-coordinator]

[redis]

[raw-overlord]

[lp-cassandra]



common:

## Lern dataproducts
dp_vault_artifacts_container: 
db_admin_password: 
db_password: 
postgres:                                                                                         
  db_url:       #"{{ groups['postgres'][0] }}"
  db_username:  #analytics
  db_name: 
  db_password: 
  db_table_name: 
  db_port: 5432
  db_admin_user: 
  db_admin_password: 
data_exhaust_webhook_url: 
data_exhaust_Channel: 
data_exhaust_name:
user_port: 6379

secrets:

## Lern dataproducts
dp_vault_data_exhaust_token: 
dp_vault_pgdb_admin_password: 
dp_vault_pgdb_password: 
dp_vault_druid_postgress_pass: 
core_vault_sunbird_api_auth_token:
core_vault_sunbird_encryption_key:   ### This variable added for admin user reports which is bein used to encrypt and decrypt data in cassandra.
```

</details>

### Data Migrations: (Run these scripts after service deployment)

* **This script is to migrating existing certificate in to RC.**

Design Document:

[https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3117416449/LR-4+Design+of+migrating+existing+certificate+in+to+RC](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3117416449/LR-4+Design+of+migrating+existing+certificate+in+to+RC)

Script path will be update later
