# Release V 5.0.1

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date | Version |
| ------- | ------------ | ------- |
| Lern    | 29 Nov 22    | V 5.0.1 |

### Details of Released Tag

| Components        | Jenkins Job                          | Deploy Tags (Devops) | Build Tags (Github Repo Tags)                                                                                                                                                                                                | Github Repository                                                                                                | Comments                                                                                 |
| ----------------- | ------------------------------------ | -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| Batch Service     | Build/Core/Lms                       | release-5.1.0\_RC1   | sunbird-course-service : [release-5.0.1\_RC2](https://github.com/Sunbird-Lern/sunbird-course-service/releases/tag/release-5.0.1\_RC2)                                                                                        | [https://github.com/Sunbird-Lern/sunbird-course-service](https://github.com/Sunbird-Lern/sunbird-course-service) |                                                                                          |
| Batch Service     | Build/Core/Cert                      | release-5.1.0\_RC1   | cert-service : [release-5.0.1\_RC2](https://github.com/Sunbird-Lern/cert-service/releases/tag/release-5.0.1\_RC2)                                                                                                            | [https://github.com/Sunbird-Lern/cert-service](https://github.com/Sunbird-Lern/cert-service)                     |                                                                                          |
| Batch Service     | Build/job/Lern/job/FlinkJobs         | release-5.1.0\_RC1   | data-pipeline : [release-5.0.1\_RC1](https://github.com/Sunbird-Lern/data-pipeline/releases/tag/release-5.0.1\_RC1)                                                                                                          | [https://github.com/Sunbird-Lern/data-pipeline](https://github.com/Sunbird-Lern/data-pipeline)                   | Collection-cert-pre-processor, Collection-certificate-generator jobs need to be deployed |
| User\&Org Service | Build/Core/Learner                   | release-5.1.0\_RC1   | sunbird-lms-service : [ **** ](https://github.com/Sunbird-Lern/sunbird-lms-service/releases/tag/release-5.0.0\_RC1)[release-5.0.1\_RC1](https://github.com/Sunbird-Lern/sunbird-lms-service/releases/tag/release-5.0.1\_RC1) | [https://github.com/Sunbird-Lern/sunbird-lms-service](https://github.com/Sunbird-Lern/sunbird-lms-service)       |                                                                                          |
| Data Products     | Build/job/Lern/job/LernDataProducts/ | release-5.1.0\_RC1   | data-products : [release-5.0.1\_RC1](https://github.com/Sunbird-Lern/data-products/releases/tag/release-5.0.1\_RC1)                                                                                                          | [https://github.com/Sunbird-Lern/data-products](https://github.com/Sunbird-Lern/data-products)                   |                                                                                          |

### **Summary of the Changes** <a href="#1.-summary-of-the-changes" id="1.-summary-of-the-changes"></a>

* Making SB Lern Cloud agnostic

#### Affected Areas:

* Textbook upload and download&#x20;
* QRCode list download from workspace
* Old certificate download
* New certificate generation and download
* Exhaust Reports - UserInfo, Progress and Reponse Exhausts
* OrgAdmin Reports - Org Consent Report and Geo Reports

### Details of the Changes

[LR-262 ](https://project-sunbird.atlassian.net/browse/LR-262)OCI and Open stack support analysis

[LR-263 ](https://project-sunbird.atlassian.net/browse/LR-263)CSP integration testing in Non-Ed env

[LR-254 ](https://project-sunbird.atlassian.net/browse/LR-254)BatchService: CSP Data migration for certificate obj data in RC



### Env Configurations (Needs to be done before service deployment):

The below environment variable needs to be configured in the devops repo.

| Variable Name             | Values                                   | Comments                   |
| ------------------------- | ---------------------------------------- | -------------------------- |
| cloud\_storage\_base\_url | https://sunbirddev.blob.core.windows.net | To store the CSP base path |



### DB Data Migrations: (Run these scripts after service deployment)

1. This script is to update the variable based relative url for cloud resources to course\_batch(cassandra) and job\_request(postgres) database tables.                        [https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3238723588/CSP+changes+in+Lern+related+tables](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3238723588/CSP+changes+in+Lern+related+tables)&#x20;
2. Update blob URL  or CNAME URL in ES ad RC DB

To change actual URL to CNAME URL  or In case of opting new CSP provider, to change to new       blob URL execute below scripts :&#x20;

RC PostgreSQL DB table V\_TrainingCertificate data migration: [https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3256877067/Training+certificate+migration](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3256877067/Training+certificate+migration)&#x20;

ES Migrations(course-batch index, trainingcertificate index)[ : ](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3231449089/CSP+Changes+for+Course+Batch+and+RC)[https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3231449089/CSP+Changes+for+Course+Batch+and+](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3231449089/CSP+Changes+for+Course+Batch+and+RC)RC

