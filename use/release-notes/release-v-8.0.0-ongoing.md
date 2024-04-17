# Release V 8.0.0 (Ongoing)

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date | Version |
| ------- | ------------ | ------- |
| Lern    |              | V 8.0.0 |

### Details of Released Tag

<table data-full-width="false"><thead><tr><th width="166">Components</th><th width="167">Build Jenkins Job</th><th width="140">Build Tag</th><th width="192">Deploy Jenkins Job</th><th width="137">Deploy Tag</th><th width="197">Comment</th></tr></thead><tbody><tr><td>OnboardAPIs</td><td>NA</td><td>NA</td><td>Deploy/Kubernetes/OnboardAPIs</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td>To onboard the delete user API</td></tr><tr><td>Cassandra Migration</td><td>Build/Core/Cassandra</td><td><a href="https://github.com/Sunbird-Lern/sunbird-utils/tree/release-7.0.0_RC3">release-7.0.0_RC3</a></td><td>Deploy/Kubernetes/Cassandra</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td><p>Select the <strong>sunbird</strong> in <strong>cassandra_keyspace_to_migrate</strong> while deploying</p><p>script_repo_branch_or_tag: release-7.0.0_RC3</p></td></tr><tr><td>ES mapping</td><td></td><td></td><td>Provision/Core/ESMapping</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td>Updates the es mapping to accept dynamic framework category to index user data</td></tr><tr><td>UserOrg Service</td><td>Build/Core/UserOrg</td><td><a href="https://github.com/Sunbird-Lern/userorg-service/tree/release-7.0.0_RC5">release-7.0.0_RC5</a></td><td>Deploy/Kubernetes/UserOrg</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td></td></tr><tr><td>LMS Servive</td><td>Build/Core/LMS</td><td><a href="https://github.com/Sunbird-Lern/lms-service/tree/release-7.0.0_RC2">release-7.0.0_RC2</a></td><td>Deploy/Kubernetes/LMS</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td></td></tr><tr><td>Group Service</td><td>Build/Core/Groups</td><td><a href="https://github.com/Sunbird-Lern/groups-service/tree/release-7.0.0_RC1">release-7.0.0_RC1</a></td><td>Deploy/Kubernetes/Groups</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td></td></tr><tr><td>Notification service</td><td>Build/Core/Notification</td><td><a href="https://github.com/Sunbird-Lern/notification-service/tree/release-7.0.0_RC2">release-7.0.0_RC2</a></td><td>Deploy/Kubernetes/Notification</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td></td></tr><tr><td>Kafka Setup</td><td>NA</td><td>NA</td><td>Deploy/Lern/KafkaSetup</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0_RC6">release-7.0.0_RC6</a></td><td></td></tr><tr><td>DataPipeline</td><td>Build/Lern/LernFlinkJobs</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0_RC6">release-7.0.0_RC6</a></td><td>Deploy/Lern/LernFlinkJobs</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0_RC6">release-7.0.0_RC6</a></td><td>Define the <em><strong>core_vault_sunbird_keycloak_user_federation_provider_id</strong></em> in Lern inventory secret. Add <strong>user-deletion-cleanup</strong> and <strong>ml-user-delete</strong> into job list and deploy it.</td></tr><tr><td>Data Product</td><td>Build/Lern/LernDataProducts</td><td><a href="https://github.com/Sunbird-Lern/data-products/tree/release-7.0.0_RC5">release-7.0.0_RC5</a></td><td>Deploy/Lern/LernDataProducts</td><td><a href="https://github.com/Sunbird-Lern/data-products/tree/release-7.0.0_RC5">release-7.0.0_RC5</a></td><td></td></tr><tr><td>Discussions Middleware</td><td>Build/Core/DiscussionsMiddleware</td><td><a href="https://github.com/Sunbird-Lern/discussions-middleware/tree/release-7.0.0_RC1">release-7.0.0_RC1</a></td><td>Deploy/Kubernetes/DiscussionsMW</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td>Removed the unwanted logs</td></tr></tbody></table>

### [**Summary of the Changes**](https://project-sunbird.atlassian.net/issues/?filter=12863) <a href="#id-1.-summary-of-the-changes" id="id-1.-summary-of-the-changes"></a>

**Details of the Changes:**

[LR-676](https://project-sunbird.atlassian.net/browse/LR-676) - \<Description>\
[LR-722](https://project-sunbird.atlassian.net/browse/LR-722) - Ownership Transfer API\
[LR-685](https://project-sunbird.atlassian.net/browse/LR-685) - Ownership Transfer Flink Job\
[LR-748](https://project-sunbird.atlassian.net/browse/LR-748) - Ownership Transfer delete user assets report

[LR-309](https://project-sunbird.atlassian.net/browse/LR-309) - Keycloak version is upgraded with 21.1.2 from 7.0.1. , we are supporting the existing features.\
Migration activity details are mentioned [https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3356000303/Keycloak+Migration+7.0.1+to+21.x+Design](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3356000303/Keycloak+Migration+7.0.1+to+21.x+Design)

### Configurations

### &#x20;**LR-722 - Ownership Transfer API**

1. Added the below configuration in the user org service application.conf file of user org service

```properties
       "/user_ownership_transfer_actor"
             {
               router = smallest-mailbox-pool
               nr-of-instances = 5
               dispatcher = brr-usr-dispatcher
             }
           "/user_ownership_transfer_actor/*"
              {
                dispatcher = akka.actor.brr-usr-dispatcher
              }
```

2. Added the below property in external resource.properties  related to ownership transfer kafka topic in user org service

```properties
user-ownership-transfer-topic={{env_name}}.user.ownership.transfer
```

3. Added the below configuration in **ansible/roles/kong-api/defaults/main.yml** for ownership transfer API in sunbird devops repository.

```properties
- name: ownershipTransfer
  uris: "{{ user_service_prefix }}/v1/ownership/transfer"
  upstream_url: "{{ userorg_service_url }}/v1/user/ownership/transfer"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - userUpdate
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false
```

4. Added the user ownership transfer topic to the userorgservice.env file in Sunbird DevOps repository.

```properties
user-ownership-transfer-topic={{env_name}}.user.ownership.transfer
```

**LR-685 Ownership transfer Flink job**

1. Added below partition related settings and replication\_factor related settings in **ansible/roles/setup-lern-kafka/defaults/main.yml** file of data pipeline repository.

```properties
  - name: user.ownership.transfer
    num_of_partitions: 2
    replication_factor: 1
    
    - name: user.ownership.transfer
    retention_time: 172800000
    replication_factor: 1
```

2. Added below ownership transfer flinkjob related configuration in **kubernetes/helm\_charts/datapipeline\_jobs/values.j2** file of data pipeline repository.

```properties
user-ownership-transfer:
  user-ownership-transfer: |+
    include file("/data/flink/conf/base-config.conf")
    kafka {
      input.topic = ${job.env}".user.ownership.transfer"
      groupId = ${job.env}"-user-ownership-transfer-group"
    }
    task {
      user.ownership.transfer.parallelism = {{ user_ownership_transfer_job_parallelism }}
    }
    lms-cassandra {
      course_batch.table = "{{ middleware_course_batch_table }}"
      keyspace = "{{ middleware_course_keyspace }}"
    }
    service {
         lms {
             basePath = "{{ lms_service_base_url }}"
         }
         userorg {
             basePath = "{{ userorg_service_base_url }}"
         }
    }
    user_read_api = "/private/user/v1/read/"
    batch_search_api = "/v1/course/batch/search"
    threshold.batch.write.size = {{ user_ownership_transfer_batch_write_size }}

  flink-conf: |+
    jobmanager.memory.flink.size: {{ flink_job_names['user-ownership-transfer'].jobmanager_memory }}
    taskmanager.memory.flink.size: {{ flink_job_names['user-ownership-transfer'].taskmanager_memory }}
    taskmanager.numberOfTaskSlots: {{ flink_job_names['user-ownership-transfer'].taskslots }}
    parallelism.default: 1
    jobmanager.execution.failover-strategy: region
    taskmanager.memory.network.fraction: 0.1
```

3. Added below ownership transfer flinkjob related configuration in kubernetes/ansible/roles/flink-jobs-deploy/defaults/main.yml of data pipeline repository

```properties
user_ownership_transfer_job_parallelism: 1
user_ownership_transfer_batch_write_size: 10


  user-ownership-transfer:
    job_class_name: 'org.sunbird.job.ownershiptransfer.task.UserOwnershipTransferStreamTask'
    replica: 1
    jobmanager_memory: 1024m
    taskmanager_memory: 1024m
    taskslots: 1
    cpu_requests: 0.3
```

**LR-748 Ownership transfer delete user assets report:**

1. Added below ownership transfer delete user assets report related configuration in **ansible/roles/lern-data-products-deploy/templates/lern-model-config.j2** of data products repository.

<pre class="language-properties"><code class="lang-properties">if [ ! -z "$3" ]; then specificUserId=$3; configuredUserId=$3; fi #used as specfic user id in usercacheindxerjob,used as configured user id in deleteusersassetsreportjob
if [ ! -z "$5" ]; then refreshUserData=$5; configuredChannel=$5;fi #used as refreshUserData flag in usercacheindxerjob,used as configured channel flag in deleteusersassetsreportjob
<strong>
</strong><strong>
</strong><strong>"delete-users-assets-report-job")
</strong>echo '{"search":{"type":"none"},"model":"org.sunbird.userorg.job.report.DeletedUsersAssetsReportJob","modelParams":{"store":"{{dp_object_store_type}}","storageKeyConfig":"storage.key.config","storageSecretConfig":"storage.secret.config","storageContainer":"{{reports_container}}","storageEndpoint":"{{dp_storage_endpoint_config}}","configuredUserId":'$configuredUserId',"configuredOrganisationId":[],"configuredChannel":'$configuredChannel', "sparkCassandraConnectionHost":"{{ core_cassandra_host }}"}}'
;;
</code></pre>

2. Added below ownership transfer delete user assets report related configuration in **ansible/roles/lern-data-products-deploy/templates/lern-run-job.j2** of data products repository

```properties
"delete-users-assets-report-job") echo 'org.sunbird.userorg.job.report.DeletedUsersAssetsReportJob'
;;
```

3. Added below ownership transfer delete user assets report related configuration in **lern-data-products/src/main/resources/application.conf**  of data products repository.

```properties
content.search.url="http://10.246.3.3/search/v3/search" 
course.batch.search.url="http://10.246.3.3/lms/v1/course/batch/search"
sunbird_instance_name="Sunbird" 
delete.user.cloud.objectKey="reports/"
```

#### Flink Job Configurations for Lern: <a href="#flink-job-configurations-for-lern" id="flink-job-configurations-for-lern"></a>

<details>

<summary><strong>user-ownership-transfer</strong></summary>

Flink **build** Jenkins job name: **/Build/job/Lern/job/FlinkJobs**

Flink **deploy** Jenkins job name:

**/Deploy/job/\<environment>/job/Lern/job/FlinkJobs/user-ownership-transfer**

</details>

**Data Product Configurations for Lern:**

<details>

<summary><strong>delete-users-assets-report-job</strong></summary>

Data products jenkins **build** job name: **/Build/job/Lern/job/LernDataProducts/**

Data products jenkins **deploy** job name: **/Deploy/job/\<environment>/job/Lern/job/LernDataProducts/LernAnalyticsReplayJobs/delete-users-assets-report-job**

</details>

### Release Notes: Dependent building blocks

Sunbird-Knowlg: [Release notes](https://knowlg.sunbird.org/use/release-notes/release-5.7.0-latest) (V 5.7.0)\
Sunbird-Obsrv: [Release notes](https://obsrv.sunbird.org/use/release-notes/release-v-5.1.0) (V 5.1.0)\
Sunbird-Ed: [Release notes](https://ed.sunbird.org/use/release/updating-sunbird-releases/5.2.0-to-6.0.0) (V 8.0.0)\
Sunbird-Inquiry: [Release notes](https://inquiry.sunbird.org/use/release-notes/inquiry-release-v5.7.0) (V 5.7.0)\
Sunbird-Telemetry: [Documentation](https://telemetry.sunbird.org/)\
Sunbird-RC: [Documentation](https://docs.sunbirdrc.dev/learn/readme)
