# Release V 5.1.0

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date | Version |
| ------- | ------------ | ------- |
| Lern    | 31 Jan 23    | V 5.1.0 |

### Details of Released Tag

| Components        | Jenkins Job                          | Deploy Tags (Devops) | Build Tags (Github Repo Tags)                                                                                                                                    | Github Repository                                                                                                | Comments                                                                      |
| ----------------- | ------------------------------------ | -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| Batch Service     | Build/Core/Lms                       | release-5.1.0        | <p>sunbird-course-service : <a href="https://github.com/Sunbird-Lern/sunbird-course-service/releases/tag/release-5.1.0_RC1">release-5.1.0_RC</a>1</p><p><br></p> | [https://github.com/Sunbird-Lern/sunbird-course-service](https://github.com/Sunbird-Lern/sunbird-course-service) |                                                                               |
| Batch Service     | Build/job/Lern/job/FlinkJobs         | release-5.1.0        | data-pipeline : [release-5.1.0\_RC1](https://github.com/Sunbird-Lern/data-pipeline/releases/tag/release-5.1.0\_RC1)                                              | [https://github.com/Sunbird-Lern/data-pipeline](https://github.com/Sunbird-Lern/data-pipeline)                   | relational-cache-updater, avtivity-aggregate-updater jobs need to be deployed |
| User\&Org Service | Build/Core/Learner                   | release-5.1.0        | sunbird-lms-service : [release-5.1.0\_RC2](https://github.com/Sunbird-Lern/sunbird-lms-service/releases/tag/release-5.1.0\_RC2)                                  | [https://github.com/Sunbird-Lern/sunbird-lms-service](https://github.com/Sunbird-Lern/sunbird-lms-service)       |                                                                               |
| Data Products     | Build/job/Lern/job/LernDataProducts/ | release-5.1.0        | data-products : [release-5.1.0\_RC1](https://github.com/Sunbird-Lern/data-products/releases/tag/release-5.1.0\_RC1)                                              | [https://github.com/Sunbird-Lern/data-products](https://github.com/Sunbird-Lern/data-products)                   |                                                                               |

### **Summary of the Changes** <a href="#1.-summary-of-the-changes" id="1.-summary-of-the-changes"></a>

* Support for optional material in a course
* Migration of existing certificate in to RC
* Making Identity manager optional for setup

#### Affected Areas:

* Flink Jobs - RelationCacheUpdate, ActivityAggregateUpdater for removing optional contents from course completion calculation
* Identity manager made optional for local setup in UserOrg and Batch Service
* Exhaust Reports - Progress Exhaust

### Details of the Changes

[LR-1 ](https://project-sunbird.atlassian.net/browse/LR-1)Backend :: Support for optional material in a course - Consumption and reporting related changes

[LR-4 ](https://project-sunbird.atlassian.net/browse/LR-4)Design on Migration of existing certificate in to RC

[LR-6](https://project-sunbird.atlassian.net/browse/LR-6) Migration of existing certificate in to RC

[LR-241 ](https://project-sunbird.atlassian.net/browse/LR-241)UserOrg: Identity manager should be optional for setup

[LR-242](https://project-sunbird.atlassian.net/browse/LR-242) UserOrg:Decoupling the external dependencies so that installation is easier like configuring the form api validation to Sunbird Ed

[LR-251 ](https://project-sunbird.atlassian.net/browse/LR-251)BatchService : Identity manager should be optional for setup

[LR-131](https://project-sunbird.atlassian.net/browse/LR-131) BatchService: Refactoring of SB Lern Batch Service

