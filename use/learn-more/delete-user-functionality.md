---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Delete User Functionality

## **Overview**

The user deletion requirement in Lern has originated from the below requirement.

PRD: [\[PRD\] Delete Account functionality](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/3351969808)

BE Design Lern - [\[Design\] Delete Account Functionality](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/3354492949)

FE Design Lern - [\[Design\] \[Front-end\]Delete User Functionality](https://project-sunbird.atlassian.net/wiki/spaces/SUN/pages/3359146039)

## What is changing? <a href="#what-is-changing" id="what-is-changing"></a>

The user can request for deletion of their account in Sunbird, this means two primary actions to happen.

1. The user's Personal Identifiable Information (PII) needs to be removed
2. The assets created by this user (such as questions, question sets, content, etc.) need to be transferred to an identified user.

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

## **Release Tags:**

<table data-full-width="false"><thead><tr><th width="166">Components</th><th width="167">Build Jenkins Job</th><th width="140">Build Tag</th><th width="192">Deploy Jenkins Job</th><th width="137">Deploy Tag</th><th width="197">Comment</th></tr></thead><tbody><tr><td>OnboardAPIs</td><td>NA</td><td>NA</td><td>Deploy/Kubernetes/OnboardAPIs</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td>To onboard the delete user API</td></tr><tr><td>Cassandra Migration</td><td>Build/Core/Cassandra</td><td><a href="https://github.com/Sunbird-Lern/sunbird-utils/tree/release-7.0.0_RC3">release-7.0.0_RC3</a></td><td>Deploy/Kubernetes/Cassandra</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td><p>Select the <strong>sunbird</strong> in <strong>cassandra_keyspace_to_migrate</strong> while deploying</p><p>script_repo_branch_or_tag: release-7.0.0_RC3</p></td></tr><tr><td>UserOrg Service</td><td>Build/Core/UserOrg</td><td><a href="https://github.com/Sunbird-Lern/userorg-service/tree/release-7.0.0_RC5">release-7.0.0_RC5</a></td><td>Deploy/Kubernetes/UserOrg</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td></td></tr><tr><td>Kafka Setup</td><td>NA</td><td>NA</td><td>Deploy/Lern/KafkaSetup</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0_RC6">release-7.0.0_RC6</a></td><td></td></tr><tr><td>DataPipeline</td><td>Build/Lern/LernFlinkJobs</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0_RC6">release-7.0.0_RC6</a></td><td>Deploy/Lern/LernFlinkJobs</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0_RC6">release-7.0.0_RC6</a></td><td>Define the <em><strong>core_vault_sunbird_keycloak_user_federation_provider_id</strong></em> in Lern inventory secret. Add <strong>user-deletion-cleanup</strong> and <strong>ml-user-delete</strong> into job list and deploy it.</td></tr><tr><td>Data Product</td><td>Build/Lern/LernDataProducts</td><td><a href="https://github.com/Sunbird-Lern/data-products/tree/release-7.0.0_RC5">release-7.0.0_RC5</a></td><td>Deploy/Lern/LernDataProducts</td><td><a href="https://github.com/Sunbird-Lern/data-products/tree/release-7.0.0_RC5">release-7.0.0_RC5</a></td><td></td></tr></tbody></table>

### Adoption of the feature Through Flink Job

#### **Code changes**

[https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0/user-org-jobs/user-deletion-cleanup](https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0/user-org-jobs/user-deletion-cleanup)

* For making the delete user functionality work through the flink job, the adapter needs to trigger the kafka event, For more details about that refer the below link,

{% embed url="https://lern.sunbird.org/use/developer-guide/user-and-org-service/userorg-flink-job/user-deletion-cleanup-flink-job#sample-event" %}
Event
{% endembed %}

* For more details on the user deletion cleanup flink job, please [visit](https://lern.sunbird.org/use/developer-guide/user-and-org-service/userorg-flink-job/user-deletion-cleanup-flink-job)

#### &#x20;**User delete Flink job**

{% hint style="danger" %}
This flink job was introduced as part of the 7.0.0 release, if any adopter wants to use this feature before the release have to configure and use this flink job.
{% endhint %}

1. Added below partition related settings and replication\_factor related settings in [**ansible/roles/setup-lern-kafka/defaults/main.yml**](https://github.com/AmiableAnil/lern-data-pipeline/blob/32087ed4e6f1b09842f903ce50a8c6c3b89270c4/ansible/roles/setup-lern-kafka/defaults/main.yml#L63) file of data pipeline repository.

```properties
   - name: delete.user
    retention_time: 172800000
    replication_factor: 1
    
   - name: delete.user
    num_of_partitions: 2
    replication_factor: 1
```

2. Added below user delete flinkjob related configuration in [**kubernetes/helm\_charts/datapipeline\_jobs/values.j2**](https://github.com/BharathwajShankar/data-pipeline/blob/b7798dcc482b7bcd12040181e997b78c0ad256f5/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L713)[ ](https://github.com/BharathwajShankar/data-pipeline/blob/7c6c0eb6258a44ef8cf7b224acd8f5ffff20785f/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L653)file of data pipeline repository.

```properties
user-deletion-cleanup:
  user-deletion-cleanup: |+
    include file("/data/flink/conf/base-config.conf")
    kafka {
      input.topic = ${job.env}".delete.user"
      groupId = ${job.env}"-delete-user-group"
    }
    task {
      user.deletion.cleanup.parallelism = {{ user_deletion_cleanup_job_parallelism }}
    }

    service {
        lms {
            basePath = "{{ lms_service_base_url }}"
        }
        userorg {
            basePath = "{{ userorg_service_base_url }}"
        }
    }

    sunbird_keycloak_user_federation_provider_id={{core_vault_sunbird_keycloak_user_federation_provider_id}}
    user_read_api = "/user/v5/read/"
    batch_search_api = "/course/v1/batch/list"

    user {
        keyspace = "sunbird"
        lookup.table = "user_lookup"
        table = "user"
        externalIdentity.table = "usr_external_identity"
        org.table = "user_organisation"
    }
    

  flink-conf: |+
    jobmanager.memory.flink.size: {{ flink_job_names['user-deletion-cleanup'].jobmanager_memory }}
    taskmanager.memory.flink.size: {{ flink_job_names['user-deletion-cleanup'].taskmanager_memory }}
    taskmanager.numberOfTaskSlots: {{ flink_job_names['user-deletion-cleanup'].taskslots }}
    parallelism.default: 1
    jobmanager.execution.failover-strategy: region
    taskmanager.memory.network.fraction: 0.1
```

3. Added below user delete flinkjob related configuration in [kubernetes/ansible/roles/flink-jobs-deploy/defaults/main.yml](https://github.com/BharathwajShankar/data-pipeline/blob/7c6c0eb6258a44ef8cf7b224acd8f5ffff20785f/kubernetes/ansible/roles/flink-jobs-deploy/defaults/main.yml#L230) of data pipeline repository

```properties
user_deletion_cleanup_job_consumer_parallelism: 1
user_deletion_cleanup_job_parallelism: 1
  
  user-deletion-cleanup:
    job_class_name: 'org.sunbird.job.deletioncleanup.task.UserDeletionCleanupStreamTask'
    replica: 1
    jobmanager_memory: 1024m
    taskmanager_memory: 1024m
    taskslots: 1
    cpu_requests: 0.3
```

#### **Ownership transfer delete user assets report:**

{% hint style="danger" %}
This report was introduced as part of the 8.0.0 release, if any adopter wants to use this feature before the release have to use the above flink job
{% endhint %}

1. Added below ownership transfer delete user assets report related configuration in [**ansible/roles/lern-data-products-deploy/templates/lern-model-config.j2**](https://github.com/Sunbird-Lern/data-products/pull/102/files#diff-a0a9e8125a5048e7b06cfdd96ac06e45d557714ece40b77e61f1528a09845662) of data products repository.

<pre class="language-properties"><code class="lang-properties">if [ ! -z "$3" ]; then specificUserId=$3; configuredUserId=$3; fi #used as specfic user id in usercacheindxerjob,used as configured user id in deleteusersassetsreportjob
if [ ! -z "$5" ]; then refreshUserData=$5; configuredChannel=$5;fi #used as refreshUserData flag in usercacheindxerjob,used as configured channel flag in deleteusersassetsreportjob
<strong>
</strong><strong>
</strong><strong>"delete-users-assets-report-job")
</strong>echo '{"search":{"type":"none"},"model":"org.sunbird.userorg.job.report.DeletedUsersAssetsReportJob","modelParams":{"store":"{{dp_object_store_type}}","storageKeyConfig":"storage.key.config","storageSecretConfig":"storage.secret.config","storageContainer":"{{reports_container}}","storageEndpoint":"{{dp_storage_endpoint_config}}","configuredUserId":'$configuredUserId',"configuredOrganisationId":[],"configuredChannel":'$configuredChannel', "sparkCassandraConnectionHost":"{{ core_cassandra_host }}"}}'
;;
</code></pre>

2. Added below ownership transfer delete user assets report related configuration in [**ansible/roles/lern-data-products-deploy/templates/lern-run-job.j2**](https://github.com/Sunbird-Lern/data-products/pull/102/files#diff-326e18859ae62cf3f434eec4f573b68938a4fae1f48f4460215cca3424d9941d) of data products repository

```properties
"delete-users-assets-report-job") echo 'org.sunbird.userorg.job.report.DeletedUsersAssetsReportJob'
;;
```

3. Added below ownership transfer delete user assets report related configuration in [**lern-data-products/src/main/resources/application.conf**](https://github.com/Sunbird-Lern/data-products/pull/102/files#diff-235f55a28945452241a414994268a904be05928b6a78ebe26d64d918df2da4a4)  of data products repository.

```properties
content.search.url="http://10.246.3.3/search/v3/search" 
course.batch.search.url="http://10.246.3.3/lms/v1/course/batch/search"
sunbird_instance_name="Sunbird" 
delete.user.cloud.objectKey="reports/"
```

To learn more about Delete user Assets report visit [here](../developer-guide/user-and-org-service/reports/other-jobs/state-admin-geo-report.md)\
\
**Jenkins Job Details For the deployment of the above flink job:**

<details>

<summary><strong>delete-users-assets-report-job</strong></summary>

Data products jenkins **build** job name: [**/Build/job/Lern/job/LernDataProducts/**](http://10.20.0.14:8080/jenkins/job/Build/job/Lern/job/LernDataProducts/)

Data products jenkins **deploy** job name: [**/Deploy/job/\<environment>/job/Lern/job/LernDataProducts/LernAnalyticsReplayJobs/delete-users-assets-report-job**](http://10.20.0.14:8080/jenkins/job/Deploy/job/dev/job/Lern/job/LernAnalyticsReplayJobs/build?delay=0sec)

</details>

### Adoption of the feature Through API

{% hint style="danger" %}
This API was introduced as part of the 7.0.0 release and can be used directly from this release. Before to this release adopters have to use either the flink job or extend this logic
{% endhint %}

**Delete user API**

1. Added the below configuration in the user org service [application.conf ](https://github.com/Sunbird-Lern/userorg-service/blob/0d513befe7e6dc8b39b4975e9a21bbdc0e139497/controller/conf/application.conf#L107)file of user org service

```properties
      "/user_deletion_background_job_actor"
      {
        router = smallest-mailbox-pool
        nr-of-instances = 5
        dispatcher = brr-usr-dispatcher
      }
    "/user_deletion_background_job_actor/*"
       {
         dispatcher = akka.actor.brr-usr-dispatcher
       }
```

2. Added the below property in [external resource.properties](https://github.com/Sunbird-Lern/userorg-service/blob/0d513befe7e6dc8b39b4975e9a21bbdc0e139497/core/platform-common/src/main/resources/externalresource.properties#L113)  related to user delete kafka topic in user org service

```properties
user-deletion-roles=public
user-deletion-broadcast-topic={{env_name}}.delete.user
```

3. Added the below configuration in [**ansible/roles/kong-api/defaults/main.yml**](https://github.com/project-sunbird/sunbird-devops/blob/788217ec28d99636e4fd2271a74fef482c41feaf/ansible/roles/kong-api/defaults/main.yml#L9226) for owuser delete API in sunbird devops repository.

```properties
- name: deleteUser
  uris: "{{ user_service_prefix }}/v1/delete"
  upstream_url: "{{ userorg_service_url }}/v1/user/delete"
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
    config.required: true
    config.enabled: true
```

4. Added the user delete topic to the [userorgservice.env](https://github.com/project-sunbird/sunbird-devops/blob/788217ec28d99636e4fd2271a74fef482c41feaf/ansible/roles/stack-sunbird/templates/userorg-service.env#L138) file in Sunbird DevOps repository.

```properties
user-deletion-roles=public
user-deletion-broadcast-topic={{env_name}}.delete.user
```
