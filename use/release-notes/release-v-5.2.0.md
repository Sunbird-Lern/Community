# Release V 5.2.0

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date | Version |
| ------- | ------------ | ------- |
| Lern    | 27 MAR 23    | V 5.2.0 |

### Details of Released Tag

| Components        | Jenkins Job                          | Deploy Tags (Devops) | Build Tags (Github Repo Tags)               | Github Repository                                                                                                | Comments |
| ----------------- | ------------------------------------ | -------------------- | ------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | -------- |
| Batch Service     | Build/Core/Lms                       | release-5.2.0        | <p>sunbird-course-service : </p><p><br></p> | [https://github.com/Sunbird-Lern/sunbird-course-service](https://github.com/Sunbird-Lern/sunbird-course-service) |          |
| Batch Service     | Build/job/Lern/job/FlinkJobs         | release-5.2.0        | data-pipeline :                             | [https://github.com/Sunbird-Lern/data-pipeline](https://github.com/Sunbird-Lern/data-pipeline)                   |          |
| User\&Org Service | Build/Core/Learner                   | release-5.2.0        | sunbird-lms-service :                       | [https://github.com/Sunbird-Lern/sunbird-lms-service](https://github.com/Sunbird-Lern/sunbird-lms-service)       |          |
| Data Products     | Build/job/Lern/job/LernDataProducts/ | release-5.2.0        | data-products :                             | [https://github.com/Sunbird-Lern/data-products](https://github.com/Sunbird-Lern/data-products)                   |          |

### **Summary of the Changes** <a href="#1.-summary-of-the-changes" id="1.-summary-of-the-changes"></a>

* **Refactoring of Dial code dependency**: An API was developed to fetch QR code image URLs and resolve relative paths from the DIAL service instead of the current connection to the Cassandra table.
* **The Course Progress Exhaust is enhanced to capture the number of attempts**
* **Refactoring of Druid dependency:** The LERN Batch Service will decouple from direct connection with Druid data store and instead use the API service owned by obsrvBB to fetch collection summary aggregate data.
* **Repo and Pod Name Correction**
* **API automation using Postman for P0 APIs**
* **Movement of UserCache and UserCacheIndexer in Data Pipeline to Lern**
* **Test Automation for CSP**
* **Migration of existing certificate into RC**
* **Certificate font change after CSP migration**

****\
**Affected Areas:**\
****\
****UserOrg Service - Repo and pod name correction in the whole microservice\
Batch service - Refactoring of Dialcode and druid dependency\
****Exhaust Reports - Course Progress Exhaust\
Addition of user cache and user cache indexer job to data products\
\
**Details of the Changes:**\
****[LR-301](https://project-sunbird.atlassian.net/browse/LR-301) API automation using Postman for P0 APIs\
[LR-302](https://project-sunbird.atlassian.net/browse/LR-302) Movement of UserCacheIndexer Data Product to Lern \
[LR-303](https://project-sunbird.atlassian.net/browse/LR-303) Movement of UserCache in Data Pipeline to Lern\
[LR-306](https://project-sunbird.atlassian.net/browse/LR-306) Test Automation for CSP \
[LR-322](https://project-sunbird.atlassian.net/browse/LR-322) API automation using Newman for P0 APIs\
[LR-324](https://project-sunbird.atlassian.net/browse/LR-324) BatchService: Refactoring of SB Lern Batch Service - Druid Dependency\
[LR-325](https://project-sunbird.atlassian.net/browse/LR-325) BatchService: Refactoring of SB Lern Batch Service - DialCode Dependency \
[LR-328](https://project-sunbird.atlassian.net/browse/LR-328) POC on OIDC support using keycloak \
[LR-330](https://project-sunbird.atlassian.net/browse/LR-330) Certificate font change after CSP migration \
[LR-323](https://project-sunbird.atlassian.net/browse/LR-323) Course Progress Exhaust to capture the number of attempts \
[LR-360](https://project-sunbird.atlassian.net/browse/LR-360) CLONE - Migration of existing certificate into RC\
[LR-101](https://project-sunbird.atlassian.net/browse/LR-101) Bring in cassandra migration and csqls to respective component repos

[LR-122](https://project-sunbird.atlassian.net/browse/LR-122) Lern repo and pod name correction to match the component name
