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

[LR-738](https://project-sunbird.atlassian.net/browse/LR-738) - Scala upgrade from 2.11 to 2.12 for userorg, course, notification and group service.

[LR-766](https://project-sunbird.atlassian.net/browse/LR-766) - Elasticsearch upgrade 6.8.22 to 7.17.13. Steps to upgrade Elasticsearch are available [here](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/3494182916/Elasticsearch+Version+Upgrade+6.8.22+to+7.17.13).

## Bug Fixes

[LR-759](https://project-sunbird.atlassian.net/browse/LR-759) - After deleting a user, and when tried to login to the same user immediately, we are getting "Access denied" error

## Details of Released Tag

_Upgrade Sunbird Lern from 7.0.0 to 8.0.0_

<table data-full-width="false"><thead><tr><th width="166">Components</th><th width="167">Build Jenkins Job</th><th width="140">Build Tag</th><th width="192">Deploy Jenkins Job</th><th width="137">Deploy Tag</th><th width="197">Comment</th></tr></thead><tbody><tr><td>Elasticsearch Provisionng</td><td>NA</td><td>NA</td><td>Provision/Core/ApplicationElasticSearch</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-8.0.0">release-8.0.0</a></td><td><ul><li>To upgrade the ElasticSearch from 6.8.22 to 7.17.21</li></ul></td></tr><tr><td>Keycloak-21 Provisioning</td><td>Build/Core/Keycloak21</td><td><a href="https://github.com/Sunbird-Lern/sunbird-auth/tree/release-8.0.0_RC1">release-8.0.0_RC1</a></td><td>Deploy/Kubernetes/Keycloak21</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-8.0.0">release-8.0.0</a></td><td>Migrating keycloak from version 7.0.1 to 21.1.2</td></tr><tr><td>OnboardAPIs</td><td>NA</td><td>NA</td><td>Deploy/Kubernetes/OnboardAPIs</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-8.0.0">release-8.0.0</a></td><td>To onboard the ownership transfer API</td></tr><tr><td>UserOrg Service</td><td>Build/Core/UserOrg</td><td><a href="https://github.com/Sunbird-Lern/userorg-service/tree/release-8.0.0_RC1">release-8.0.0_RC1</a></td><td>Deploy/Kubernetes/UserOrg</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-8.0.0">release-8.0.0</a></td><td><ul><li>cloud_store_group_id: <strong>org.sunbird</strong></li><li>cloud_store_artifact_id: <strong>cloud-store-sdk_2.12</strong></li><li>cloud_store_version: <strong>1.4.7</strong></li></ul></td></tr><tr><td>LMS Servive</td><td>Build/Core/LMS</td><td><a href="https://github.com/Sunbird-Lern/lms-service/tree/release-8.0.0_RC1">release-8.0.0_RC1</a></td><td>Deploy/Kubernetes/LMS</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-8.0.0">release-8.0.0</a></td><td><ul><li>cloud_store_group_id: <strong>org.sunbird</strong></li><li>cloud_store_artifact_id: <strong>cloud-store-sdk_2.12</strong></li><li>cloud_store_version: <strong>1.4.7</strong></li></ul></td></tr><tr><td>Group Service</td><td>Build/Core/Groups</td><td><a href="https://github.com/Sunbird-Lern/groups-service/tree/release-8.0.0_RC1">release-8.0.0_RC1</a></td><td>Deploy/Kubernetes/Groups</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-8.0.0">release-8.0.0</a></td><td></td></tr><tr><td>Notification service</td><td>Build/Core/Notification</td><td><a href="https://github.com/Sunbird-Lern/notification-service/tree/release-8.0.0_RC1">release-8.0.0_RC1</a></td><td>Deploy/Kubernetes/Notification</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-8.0.0">release-8.0.0</a></td><td></td></tr><tr><td>Kafka Setup</td><td>NA</td><td>NA</td><td>Deploy/Lern/KafkaSetup</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0_RC6">release-7.0.0_RC6</a></td><td></td></tr><tr><td>DataPipeline</td><td>Build/Lern/LernFlinkJobs</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-8.0.0_RC1">release-8.0.0_RC1</a></td><td>Deploy/Lern/LernFlinkJobs</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-8.0.0_RC1">release-8.0.0_RC1</a></td><td><p>Define the <em><strong>core_vault_sunbird_keycloak_user_federation_provider_id</strong></em> in Lern inventory secret. Add <strong>user-deletion-cleanup</strong> and <strong>ml-user-delete</strong> into job list and deploy it.<br><br></p><ul><li>cloud_store_group_id: <strong>org.sunbird</strong></li><li>cloud_store_artifact_id: <strong>cloud-store-sdk_2.12</strong></li><li>cloud_store_version: <strong>1.4.6</strong></li></ul></td></tr><tr><td>Data Product</td><td>Build/Lern/LernDataProducts</td><td><a href="https://github.com/Sunbird-Lern/data-products/tree/release-8.0.0_RC1">release-8.0.0_RC1</a></td><td>Deploy/Lern/LernDataProducts</td><td><a href="https://github.com/Sunbird-Lern/data-products/tree/release-8.0.0_RC1">release-8.0.0_RC1</a></td><td><ul><li>cloud_store_group_id: <strong>org.sunbird</strong></li><li>cloud_store_artifact_id: <strong>cloud-store-sdk_2.12</strong></li><li>cloud_store_version: <strong>1.4.6</strong></li></ul></td></tr></tbody></table>

## Configurations

* To know more about the configuration of delete user assets report visit [here](https://lern.sunbird.org/use/learn-more/delete-user-functionality)
* To know more about the configuration of ownership transfer functionality visit [here](https://lern.sunbird.org/use/learn-more/asset-ownership-transfer)

## Release Notes: Dependent building blocks

Sunbird-Knowlg: [Release notes](https://knowlg.sunbird.org/use/release-notes/release-6.1.0-latest) (V 6.1.0)\
Sunbird-Obsrv: [Release notes](https://obsrv.sunbird.org/previous-versions/sb-5.0-version/use/release-notes/release-v-5.1.3) (V 5.1.3)\
Sunbird-Ed: [Release notes](https://ed.sunbird.org/use/release/updating-sunbird-releases/5.2.0-to-6.0.0) (V 8.0.0)\
Sunbird-Inquiry: [Release notes](https://inquiry.sunbird.org/use/release-notes/inquiry-release-v5.7.0) (V 5.7.0)\
Sunbird-Telemetry: [Documentation](https://telemetry.sunbird.org/)\
Sunbird-RC: [Documentation](https://docs.sunbirdrc.dev/learn/readme)
