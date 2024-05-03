# Asset Ownership Transfer

## **Overview**

The user deletion requirement in Lern has originated from the below requirement.

PRD: [\[PRD\] Asset Ownership Transfer](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/3365863425/Design+Transfer+Ownership)

## What is changing? <a href="#what-is-changing" id="what-is-changing"></a>

The user can request for deletion of their account in Sunbird, this means two primary actions to happen.

1. The user's Personal Identifiable Information (PII) needs to be removed
2. The assets created by this user (such as questions, question sets, content, etc.) need to be transferred to an identified user.

## Changes on Lern: <a href="#scope-for-inquiry" id="scope-for-inquiry"></a>

1. A user deletion API which produces a kafka event on **\<env>.user.ownership.transfer** topic.
2. For more details on the Ownership transfer flink job, please [visit](https://lern.sunbird.org/use/developer-guide/user-and-org-service/userorg-flink-job/ownership-transfer-flink-job)

## **Release Tags:**

<table data-full-width="false"><thead><tr><th width="166">Components</th><th width="167">Build Jenkins Job</th><th width="140">Build Tag</th><th width="192">Deploy Jenkins Job</th><th width="137">Deploy Tag</th><th width="197">Comment</th></tr></thead><tbody><tr><td>OnboardAPIs</td><td>NA</td><td>NA</td><td>Deploy/Kubernetes/OnboardAPIs</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td>To onboard the delete user API</td></tr><tr><td>Cassandra Migration</td><td>Build/Core/Cassandra</td><td><a href="https://github.com/Sunbird-Lern/sunbird-utils/tree/release-7.0.0_RC3">release-7.0.0_RC3</a></td><td>Deploy/Kubernetes/Cassandra</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td><p>Select the <strong>sunbird</strong> in <strong>cassandra_keyspace_to_migrate</strong> while deploying</p><p>script_repo_branch_or_tag: release-7.0.0_RC3</p></td></tr><tr><td>UserOrg Service</td><td>Build/Core/UserOrg</td><td><a href="https://github.com/Sunbird-Lern/userorg-service/tree/release-7.0.0_RC5">release-7.0.0_RC5</a></td><td>Deploy/Kubernetes/UserOrg</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0">release-7.0.0</a></td><td></td></tr><tr><td>Kafka Setup</td><td>NA</td><td>NA</td><td>Deploy/Lern/KafkaSetup</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0_RC6">release-7.0.0_RC6</a></td><td></td></tr><tr><td>DataPipeline</td><td>Build/Lern/LernFlinkJobs</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0_RC6">release-7.0.0_RC6</a></td><td>Deploy/Lern/LernFlinkJobs</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0_RC6">release-7.0.0_RC6</a></td><td>Define the <em><strong>core_vault_sunbird_keycloak_user_federation_provider_id</strong></em> in Lern inventory secret. Add <strong>user-deletion-cleanup</strong> and <strong>ml-user-delete</strong> into job list and deploy it.</td></tr><tr><td>Data Product</td><td>Build/Lern/LernDataProducts</td><td><a href="https://github.com/Sunbird-Lern/data-products/tree/release-7.0.0_RC5">release-7.0.0_RC5</a></td><td>Deploy/Lern/LernDataProducts</td><td><a href="https://github.com/Sunbird-Lern/data-products/tree/release-7.0.0_RC5">release-7.0.0_RC5</a></td><td></td></tr></tbody></table>

### Configurations

### Adoption of the feature Through Flink Job

#### **Ownership transfer Flink job**

{% hint style="danger" %}
This flink job was introduced as part of the 7.0.0 release, if any adopter wants to use this feature before the release have to configure and use this flink job.
{% endhint %}

1. Added below partition related settings and replication\_factor related settings in [**ansible/roles/setup-lern-kafka/defaults/main.yml**](https://github.com/AmiableAnil/lern-data-pipeline/blob/0a106fa18133c715d0cd5cf311491f172bfb76b4/ansible/roles/setup-lern-kafka/defaults/main.yml#L66) file of data pipeline repository.

```properties
  - name: user.ownership.transfer
    num_of_partitions: 2
    replication_factor: 1
    
    - name: user.ownership.transfer
    retention_time: 172800000
    replication_factor: 1
```

2. Added below ownership transfer flinkjob related configuration in [**kubernetes/helm\_charts/datapipeline\_jobs/values.j2**](https://github.com/BharathwajShankar/data-pipeline/blob/b7798dcc482b7bcd12040181e997b78c0ad256f5/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L713) file of data pipeline repository.

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

3. Added below ownership transfer flinkjob related configuration in[ kubernetes/ansible/roles/flink-jobs-deploy/defaults/main.yml ](https://github.com/BharathwajShankar/data-pipeline/blob/b7798dcc482b7bcd12040181e997b78c0ad256f5/kubernetes/ansible/roles/flink-jobs-deploy/defaults/main.yml#L248)of data pipeline repository

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

**Jenkins Job Details For the deployment of the above flink job:**

<details>

<summary><strong>user-ownership-transfer</strong></summary>

Flink **build** Jenkins job name: **/**[**Build/job/Lern/job/FlinkJobs**](http://10.20.0.14:8080/jenkins/job/Build/job/Lern/job/LernFlinkJobs/)

Flink **deploy** Jenkins job name:

[**/Deploy/job/\<environment>/job/Lern/job/FlinkJobs/user-ownership-transfer**](http://10.20.0.14:8080/jenkins/job/Deploy/job/dev/job/Lern/job/LernFlinkJobs/build?delay=0sec)

</details>

### Adoption of the feature Through API

{% hint style="danger" %}
This API was introduced as part of the 8.0.0 release and can be used directly from this release. Before this release adopters have to use either the flink job or extend this logic
{% endhint %}

**Ownership Transfer API**

1. Added the below configuration in the user org service [application.conf ](https://github.com/Sunbird-Lern/userorg-service/blob/9b9ba14f38d8ed26e3e4d4a94bfad7b148c01cf3/controller/conf/application.conf#L118)file of user org service

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

2. Added the below property in [external resource.properties](https://github.com/Sunbird-Lern/userorg-service/blob/9b9ba14f38d8ed26e3e4d4a94bfad7b148c01cf3/core/platform-common/src/main/resources/externalresource.properties#L112)  related to ownership transfer kafka topic in user org service

```properties
user-ownership-transfer-topic={{env_name}}.user.ownership.transfer
```

3. Added the below configuration in [**ansible/roles/kong-api/defaults/main.yml**](https://github.com/project-sunbird/sunbird-devops/pull/3969/files#diff-0ee5a2ff6501d6e8fc33eff9ad8844f490abfcae4f10597790399ced589484d5) for ownership transfer API in sunbird devops repository.

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

4. Added the user ownership transfer topic to the [userorgservice.env](https://github.com/project-sunbird/sunbird-devops/pull/3969/files#diff-a3b1fa3f7ba85e038caa90e6dd9cd445b9fc7241ddff502767adc8c21377bc77) file in Sunbird DevOps repository.

```properties
user-ownership-transfer-topic={{env_name}}.user.ownership.transfer
```
