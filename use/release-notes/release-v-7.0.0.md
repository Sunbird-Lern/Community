# Release V 7.0.0

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date | Version |
| ------- | ------------ | ------- |
| Lern    | 30-Dec-2023  | V 7.0.0 |

### <mark style="color:blue;">**Hot-fix:  5.3.1**</mark>** (24-04-2024)**

<table data-full-width="false"><thead><tr><th width="166">Components</th><th width="167">Build Jenkins Job</th><th width="140">Build Tag</th><th width="192">Deploy Jenkins Job</th><th width="137">Deploy Tag</th><th width="197">Comment</th></tr></thead><tbody><tr><td>Group Service</td><td>Build/Core/Groups</td><td><a href="https://github.com/Sunbird-Lern/groups-service/tree/release-7.0.0_RC2">release-7.0.0_RC2</a></td><td>Deploy/Kubernetes/Groups</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td><a href="https://project-sunbird.atlassian.net/browse/LR-776">LR-776</a></td></tr></tbody></table>

### Details of Released Tag

<table data-full-width="false"><thead><tr><th width="166">Components</th><th width="167">Build Jenkins Job</th><th width="140">Build Tag</th><th width="192">Deploy Jenkins Job</th><th width="137">Deploy Tag</th><th width="197">Comment</th></tr></thead><tbody><tr><td>OnboardAPIs</td><td>NA</td><td>NA</td><td>Deploy/Kubernetes/OnboardAPIs</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td>To onboard the delete user API</td></tr><tr><td>Cassandra Migration</td><td>Build/Core/Cassandra</td><td><a href="https://github.com/Sunbird-Lern/sunbird-utils/tree/release-7.0.0_RC3">release-7.0.0_RC3</a></td><td>Deploy/Kubernetes/Cassandra</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td><p>Select the <strong>sunbird</strong> in <strong>cassandra_keyspace_to_migrate</strong> while deploying</p><p>script_repo_branch_or_tag: release-7.0.0_RC3</p></td></tr><tr><td>ES mapping</td><td></td><td></td><td>Provision/Core/ESMapping</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td>Updates the es mapping to accept dynamic framework category to index user data</td></tr><tr><td>UserOrg Service</td><td>Build/Core/UserOrg</td><td><a href="https://github.com/Sunbird-Lern/userorg-service/tree/release-7.0.0_RC5">release-7.0.0_RC5</a></td><td>Deploy/Kubernetes/UserOrg</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td></td></tr><tr><td>LMS Servive</td><td>Build/Core/LMS</td><td><a href="https://github.com/Sunbird-Lern/lms-service/tree/release-7.0.0_RC2">release-7.0.0_RC2</a></td><td>Deploy/Kubernetes/LMS</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td></td></tr><tr><td>Group Service</td><td>Build/Core/Groups</td><td><a href="https://github.com/Sunbird-Lern/groups-service/tree/release-7.0.0_RC1">release-7.0.0_RC1</a></td><td>Deploy/Kubernetes/Groups</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td></td></tr><tr><td>Notification service</td><td>Build/Core/Notification</td><td><a href="https://github.com/Sunbird-Lern/notification-service/tree/release-7.0.0_RC2">release-7.0.0_RC2</a></td><td>Deploy/Kubernetes/Notification</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td></td></tr><tr><td>Kafka Setup</td><td>NA</td><td>NA</td><td>Deploy/Lern/KafkaSetup</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0_RC6">release-7.0.0_RC6</a></td><td></td></tr><tr><td>DataPipeline</td><td>Build/Lern/LernFlinkJobs</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0_RC7">release-7.0.0_RC7</a></td><td>Deploy/Lern/LernFlinkJobs</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0_RC7">release-7.0.0_RC7</a></td><td>Define the <em><strong>core_vault_sunbird_keycloak_user_federation_provider_id</strong></em> in Lern inventory secret. Add <strong>user-deletion-cleanup</strong> and <strong>ml-user-delete</strong> into job list and deploy it.</td></tr><tr><td>Data Product</td><td>Build/Lern/LernDataProducts</td><td><a href="https://github.com/Sunbird-Lern/data-products/tree/release-7.0.0_RC6">release-7.0.0_RC6</a></td><td>Deploy/Lern/LernDataProducts</td><td><a href="https://github.com/Sunbird-Lern/data-products/tree/release-7.0.0_RC6">release-7.0.0_RC6</a></td><td></td></tr><tr><td>Discussions Middleware</td><td>Build/Core/DiscussionsMiddleware</td><td><a href="https://github.com/Sunbird-Lern/discussions-middleware/tree/release-7.0.0_RC1">release-7.0.0_RC1</a></td><td>Deploy/Kubernetes/DiscussionsMW</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td>Removed the unwanted logs</td></tr></tbody></table>

### [**Summary of the Changes**](https://project-sunbird.atlassian.net/issues/?filter=12863) <a href="#id-1.-summary-of-the-changes" id="id-1.-summary-of-the-changes"></a>

**Details of the Changes:**

[LR-676](https://project-sunbird.atlassian.net/browse/LR-676) - User PII Information and account deletion from LERN DBs

[LR-699](https://project-sunbird.atlassian.net/browse/LR-699) - \[LERN] Making BMGS configurable

[LR-687](https://project-sunbird.atlassian.net/browse/LR-687) - Removal of Adopter specific keywords from LERN repos

[LR-637](https://project-sunbird.atlassian.net/browse/LR-637) - Postman API automation development for user-org micro-service.

[LR-660](https://project-sunbird.atlassian.net/browse/LR-660) - Postman API automation development for LMS micro-service.

[LR-662](https://project-sunbird.atlassian.net/browse/LR-662) - Postman API automation development for groups micro-service.

[LR-664](https://project-sunbird.atlassian.net/browse/LR-664) - Postman API automation development for notification micro-service.

[LR-756](https://project-sunbird.atlassian.net/browse/LR-756) - Adding a "status" column to Admin reports.

### Configurations

To know more about the configuration of Delete user functionality visit [here](https://lern.sunbird.org/use/learn-more/delete-user-functionality)

### Release Notes: Dependent building blocks

Sunbird-Knowlg: [Release notes](https://knowlg.sunbird.org/use/release-notes/release-5.7.0-latest) (V 5.7.0)\
Sunbird-Obsrv: [Release notes](https://obsrv.sunbird.org/previous-versions/sb-5.0-version/use/release-notes/release-v-5.1.3) (V 5.1.3)\
Sunbird-Ed: [Release notes](https://ed.sunbird.org/use/release/updating-sunbird-releases/5.2.0-to-6.0.0) (V 7.0.0)\
Sunbird-Inquiry: [Release notes](https://inquiry.sunbird.org/use/release-notes/inquiry-release-v5.7.0) (V 5.7.0)\
Sunbird-Telemetry: [Documentation](https://telemetry.sunbird.org/)\
Sunbird-RC: [Documentation](https://docs.sunbirdrc.dev/learn/readme)

### Steps to update user's cache in Redis

As part of making framework categories configurable, framework category details in the user's cache are updated. To support the new data-product, the existing Redis user's data should be updated through the Usercache indexer job. Run the below job with the below params to update the same.

Job : `Deploy/Lern/LernAnalyticsReplayJobs`

Kindly refer the below image for params

<figure><img src="../../.gitbook/assets/Screenshot 2024-01-04 at 12.21.28 PM (2).png" alt=""><figcaption></figcaption></figure>

In this release, a new column called **"status"** has been added to the user data frame (`userDF`) of [**UsercacheindexerJob**](https://github.com/Sunbird-Lern/data-products/blob/release-7.0.0/lern-data-products/src/main/scala/org/sunbird/userorg/job/report/UserCacheIndexerJob.scala) of dataproducts. inorder to cache the status column from the Cassandra DB to Redis. Also same has been added to usercacheupdater config to make sure it is fetched from Redis to the state admin report and user info report. This will help the admin understand whether the user is active/inactive or deleted.\
Rerun the user cache-updater-v2 job(**/Deploy/job/\<environment>/job/Lern/job/FlinkJobs/user-cache-updater-v2**) and a user-cache-index job(**/job/\<environment>/job/Deploy/Lern/LernAnalyticsReplayJobs/user-cache-indexer-job**) once so that the status column is fetched correctly.
