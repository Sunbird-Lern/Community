# Release V 8.0.0 (Ongoing)

## Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date | Version |
| ------- | ------------ | ------- |
| Lern    |              | V 8.0.0 |

## Overview

This release contains software upgrade and ownership transfer functionality.

## New Features

### Ownership Transfer

[LR-722](https://project-sunbird.atlassian.net/browse/LR-722) - Ownership Transfer API\
[LR-685](https://project-sunbird.atlassian.net/browse/LR-685) - Ownership Transfer Flink Job\
[LR-748](https://project-sunbird.atlassian.net/browse/LR-748) - Ownership Transfer delete user assets report

## Enhancements / Technical Tasks

[LR-309](https://project-sunbird.atlassian.net/browse/LR-309) - The Keycloak version is upgraded with 21.1.2 from 7.0.1. , we are supporting the existing features.\
Migration activity details are mentioned [https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3356000303/Keycloak+Migration+7.0.1+to+21.x+Design](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3356000303/Keycloak+Migration+7.0.1+to+21.x+Design)

[LR-766](https://project-sunbird.atlassian.net/browse/LR-766) - Elasticsearch upgrade 6.8.22 to 7.17.13. Steps to upgrade Elasticsearch are available [here](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/3494182916/Elasticsearch+Version+Upgrade+6.8.22+to+7.17.13).

[LR-738](https://project-sunbird.atlassian.net/browse/LR-738) - Scala upgrade from 2.11 to 2.12 for userorg, course, notification and group service.

## Bug Fixes

[LR-759](https://project-sunbird.atlassian.net/browse/LR-759) - After deleting a user, and when tried to login to the same user immediately, we are getting "Access denied" error

## Details of Released Tag

_Upgrade Sunbird Lern from 7.0.0 to 8.0.0_

<table data-full-width="false"><thead><tr><th width="166">Components</th><th width="167">Build Jenkins Job</th><th width="140">Build Tag</th><th width="192">Deploy Jenkins Job</th><th width="137">Deploy Tag</th><th width="197">Comment</th></tr></thead><tbody><tr><td>OnboardAPIs</td><td>NA</td><td>NA</td><td>Deploy/Kubernetes/OnboardAPIs</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td>To onboard the delete user API</td></tr><tr><td>Cassandra Migration</td><td>Build/Core/Cassandra</td><td><a href="https://github.com/Sunbird-Lern/sunbird-utils/tree/release-7.0.0_RC3">release-7.0.0_RC3</a></td><td>Deploy/Kubernetes/Cassandra</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td><p>Select the <strong>sunbird</strong> in <strong>cassandra_keyspace_to_migrate</strong> while deploying</p><p>script_repo_branch_or_tag: release-7.0.0_RC3</p></td></tr><tr><td>ES mapping</td><td></td><td></td><td>Provision/Core/ESMapping</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td>Updates the es mapping to accept dynamic framework category to index user data</td></tr><tr><td>UserOrg Service</td><td>Build/Core/UserOrg</td><td><a href="https://github.com/Sunbird-Lern/userorg-service/tree/release-7.0.0_RC5">release-7.0.0_RC5</a></td><td>Deploy/Kubernetes/UserOrg</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td></td></tr><tr><td>LMS Servive</td><td>Build/Core/LMS</td><td><a href="https://github.com/Sunbird-Lern/lms-service/tree/release-7.0.0_RC2">release-7.0.0_RC2</a></td><td>Deploy/Kubernetes/LMS</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td></td></tr><tr><td>Group Service</td><td>Build/Core/Groups</td><td><a href="https://github.com/Sunbird-Lern/groups-service/tree/release-7.0.0_RC1">release-7.0.0_RC1</a></td><td>Deploy/Kubernetes/Groups</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td></td></tr><tr><td>Notification service</td><td>Build/Core/Notification</td><td><a href="https://github.com/Sunbird-Lern/notification-service/tree/release-7.0.0_RC2">release-7.0.0_RC2</a></td><td>Deploy/Kubernetes/Notification</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td></td></tr><tr><td>Kafka Setup</td><td>NA</td><td>NA</td><td>Deploy/Lern/KafkaSetup</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0_RC6">release-7.0.0_RC6</a></td><td></td></tr><tr><td>DataPipeline</td><td>Build/Lern/LernFlinkJobs</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0_RC6">release-7.0.0_RC6</a></td><td>Deploy/Lern/LernFlinkJobs</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0_RC6">release-7.0.0_RC6</a></td><td>Define the <em><strong>core_vault_sunbird_keycloak_user_federation_provider_id</strong></em> in Lern inventory secret. Add <strong>user-deletion-cleanup</strong> and <strong>ml-user-delete</strong> into job list and deploy it.</td></tr><tr><td>Data Product</td><td>Build/Lern/LernDataProducts</td><td><a href="https://github.com/Sunbird-Lern/data-products/tree/release-7.0.0_RC5">release-7.0.0_RC5</a></td><td>Deploy/Lern/LernDataProducts</td><td><a href="https://github.com/Sunbird-Lern/data-products/tree/release-7.0.0_RC5">release-7.0.0_RC5</a></td><td></td></tr><tr><td>Discussions Middleware</td><td>Build/Core/DiscussionsMiddleware</td><td><a href="https://github.com/Sunbird-Lern/discussions-middleware/tree/release-7.0.0_RC1">release-7.0.0_RC1</a></td><td>Deploy/Kubernetes/DiscussionsMW</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td>Removed the unwanted logs</td></tr></tbody></table>

## Configurations

* To know more about the configuration of delete user assets report visit [here](https://app.gitbook.com/o/-Mi9QwJlsfb7xuxTBc0J/s/4ZKyfmmhMWpPkD6iYvKF/\~/changes/598/use/learn-more/delete-user-functionality/\~/page#configurations)
* To know more about the configuration of ownership transfer functionality visit [here](../learn-more/asset-ownership-transfer.md)

## Release Notes: Dependent building blocks

Sunbird-Knowlg: [Release notes](https://knowlg.sunbird.org/use/release-notes/release-5.7.0-latest) (V 5.7.0)\
Sunbird-Obsrv: [Release notes](https://obsrv.sunbird.org/use/release-notes/release-v-5.1.0) (V 5.1.0)\
Sunbird-Ed: [Release notes](https://ed.sunbird.org/use/release/updating-sunbird-releases/5.2.0-to-6.0.0) (V 8.0.0)\
Sunbird-Inquiry: [Release notes](https://inquiry.sunbird.org/use/release-notes/inquiry-release-v5.7.0) (V 5.7.0)\
Sunbird-Telemetry: [Documentation](https://telemetry.sunbird.org/)\
Sunbird-RC: [Documentation](https://docs.sunbirdrc.dev/learn/readme)
