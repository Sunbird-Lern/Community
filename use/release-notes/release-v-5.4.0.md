# Release V 5.4.0

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date | Version |
| ------- | ------------ | ------- |
| Lern    | 11-Jul-2023  | V 5.4.0 |

### Details of Released Tag

<table data-full-width="false"><thead><tr><th width="166">Components</th><th width="167">Build Jenkins Job</th><th width="140">Build Tag</th><th width="192">Deploy Jenkins Job</th><th width="137">Deploy Tag</th><th width="197">Comment</th></tr></thead><tbody><tr><td>Proxy</td><td>Build/Core/Proxy</td><td></td><td><p>Deploy/Kubernetes/nginx-private-ingress</p><p></p><p>/Deploy/Kubernetes/nginx-public-ingress</p></td><td></td><td></td></tr><tr><td>OnboardAPIs</td><td></td><td></td><td>Deploy/Kubernetes/OnboardAPIs</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-5.4.0-lern">release-5.4.0-lern</a></td><td></td></tr><tr><td>UserOrg Service</td><td>Build/Core/UserOrg</td><td><a href="https://github.com/Sunbird-Lern/userorg-service/tree/release-5.4.0_RC1">release-5.4.0_RC1</a></td><td>Deploy/Kubernetes/UserOrg</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-5.4.0-lern">release-5.4.0-lern</a></td><td>Learner service is renamed as UserOrg now.</td></tr><tr><td>LMS Servive</td><td>Build/Core/LMS</td><td><a href="https://github.com/Sunbird-Lern/lms-service/tree/release-5.4.0_RC1">release-5.4.0_RC1</a></td><td>Deploy/Kubernetes/LMS</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-5.4.0-lern">release-5.4.0-lern</a></td><td></td></tr><tr><td>Group Service</td><td>Build/Core/Groups</td><td>release-5.4.0_RC1</td><td>Deploy/Kubernetes/Groups</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-5.4.0-lern">release-5.4.0-lern</a></td><td></td></tr><tr><td>Notification service</td><td>Build/Core/Notification</td><td>release-5.4.0_RC1</td><td>Deploy/Kubernetes/Notification</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-5.4.0-lern">release-5.4.0-lern</a></td><td></td></tr><tr><td>Analytics Service</td><td></td><td></td><td>Deploy/Kubernetes/Analytics</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-5.4.0-lern">release-5.4.0-lern</a></td><td></td></tr><tr><td>DataPipeline</td><td>Build/Lern/LernFlinkJobs</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-5.4.0_RC1">release-5.4.0_RC1</a></td><td>Deploy/Lern/LernFlinkJobs</td><td><a href="https://github.com/Sunbird-Lern/data-pipeline/tree/release-5.4.0_RC1">release-5.4.0_RC1</a></td><td></td></tr><tr><td>Data Product</td><td>Build/Lern/LernDataProducts</td><td><a href="https://github.com/Sunbird-Lern/data-products/tree/release-5.4.0_RC1">release-5.4.0_RC1</a></td><td>Deploy/Lern/LernDataProducts</td><td><a href="https://github.com/Sunbird-Lern/data-products/tree/release-5.4.0_RC1">release-5.4.0_RC1</a></td><td></td></tr><tr><td>Keycloak</td><td></td><td></td><td>Deploy/Kubernetes/Keycloak</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-5.4.0-lern">release-5.4.0-lern</a></td><td></td></tr><tr><td>Knowledge-MW</td><td></td><td></td><td>Deploy/Kubernetes/KnowledgeMW</td><td>release-7.0.0</td><td></td></tr></tbody></table>

### **Summary of the Changes** <a href="#id-1.-summary-of-the-changes" id="id-1.-summary-of-the-changes"></a>

**Details of the Changes:**

[LR-122](https://project-sunbird.atlassian.net/browse/LR-122) Lern repo and pod name correction to match the component name - Development\
[LR-588](https://project-sunbird.atlassian.net/browse/LR-588) PII Enhancement\
[LR-102](https://project-sunbird.atlassian.net/browse/LR-102) UserOrg: Ability for Lern to connect to shared instances of Cassandra, ES, Postgres, and Redis with lern specific keyspace and indexes\
[LR-511](https://project-sunbird.atlassian.net/browse/LR-511) Ability for Lern to connect to shared instances of Cassandra, ES, Postgres, and Redis with lern specific keyspace and indexes in BatchService \
[LR-512](https://project-sunbird.atlassian.net/browse/LR-512) Ability for Lern to connect to shared instances of Cassandra, and Redis with lern specific keyspace and indexes in GroupService \
[LR-513](https://project-sunbird.atlassian.net/browse/LR-513) Ability for Lern to connect to shared instances of Cassandra with lern specific keyspace and indexes in NotificationService \
[LR-394](https://project-sunbird.atlassian.net/browse/LR-394) \[Feed API] Update feed API with deleted feed id is giving 200k response and read is also giving feed details

#### Github repositories name updates&#x20;

```
old: https://github.com/Sunbird-Lern/sunbird-lms-service 
new: https://github.com/Sunbird-Lern/userorg-service

old: https://github.com/Sunbird-Lern/sunbird-course-service 
new: https://github.com/Sunbird-Lern/lms-service

old: https://github.com/Sunbird-Lern/sunbird-notification-service 
new: https://github.com/Sunbird-Lern/notification-service
```

### Configurations

Rename all the endpoints from **/learner** to **/userorg**

Renamed the below variables.

<table><thead><tr><th width="367">old</th><th width="350">new</th></tr></thead><tbody><tr><td><ul><li>learner_replicas </li><li>learner_reservation_memory </li><li>learner_limit_memory </li><li>learner_reservation_cpu</li><li>learner_limit_cpu </li><li>learner_java_mem_limit</li><li>learner_replicacount </li><li>learner_repository </li><li>learner_cpu_req </li><li>learner_mem_req </li><li>learner_cpu_limit </li><li>learner_mem_limit </li><li>learner_maxsurge </li><li>learner_maxunavailable </li><li>learner_liveness_readiness </li><li>learner_envoy_cpu_req</li><li>learner_envoy_mem_req </li><li>learner_envoy_cpu_limit </li><li>learner_envoy_mem_limit </li><li>learner_opa_cpu_req </li><li>learner_opa_mem_req </li><li>learner_opa_cpu_limit </li><li>learner_opa_mem_limit</li><li>learner_initcontainer_cpu_req</li><li>learner_initcontainer_mem_req</li><li>learner_initcontainer_cpu_limit</li><li>learner_initcontainer_mem_limit</li><li>learner_autoscaling_enabled</li><li>learner_autoscaling_minReplicas</li><li>learner_autoscaling_maxReplicas</li><li>learner_autoscaling_targetCPUUtilizationPercentage</li><li>learner_autoscaling_targetMemoryUtilizationPercentage</li><li>learner_opa_enabled</li><li>learner_access_basepath</li><li>deploy_learner</li><li>learner_opa_decision_logs</li></ul></td><td><ul><li>userorg_replicas</li><li>userorg_reservation_memory </li><li>userorg_limit_memory </li><li>userorg_reservation_cpu </li><li>userorg_limit_cpu </li><li>userorg_java_mem_limit</li><li>userorg_replicacount </li><li>userorg_repository </li><li>userorg_cpu_req </li><li>userorg_mem_req </li><li>userorg_cpu_limit </li><li>userorg_mem_limit </li><li>userorg_maxsurge </li><li>userorg_maxunavailable </li><li>userorg_liveness_readiness </li><li>userorg_envoy_cpu_req </li><li>userorg_envoy_mem_req </li><li>userorg_envoy_cpu_limit </li><li>userorg_envoy_mem_limit </li><li>userorg_opa_cpu_req </li><li>userorg_opa_mem_req </li><li>userorg_opa_cpu_limit </li><li>userorg_opa_mem_limit </li><li>userorg_initcontainer_cpu_req</li><li>userorg_initcontainer_mem_req</li><li>userorg_initcontainer_cpu_limit</li><li>userorg_initcontainer_mem_limit</li><li>userorg_autoscaling_enabled</li><li>userorg_autoscaling_minReplicas</li><li>userorg_autoscaling_maxReplicas</li><li>userorg_autoscaling_targetCPUUtilizationPercentage</li><li>userorg_autoscaling_targetMemoryUtilizationPercentage</li><li>userorg_opa_enabled</li><li>userorg_access_basepath</li><li>deploy_user_org</li><li>userorg_opa_decision_logs</li></ul></td></tr></tbody></table>

### Release Notes: Dependent building blocks

Sunbird-Knowlg: [Release notes](https://knowlg.sunbird.org/use/release-notes/release-5.5.0-latest) (V 5.5.0)\
Sunbird-Obsrv: [Release notes](https://knowlg.sunbird.org/use/release-notes/release-5.5.0-latest) (V 5.1.0)\
Sunbird-Ed: [Release notes ](https://ed.sunbird.org/use/releases/release-notes/release-5.2.0)(V 5.2.0)\
Sunbird-Inquiry: [Release notes](https://inquiry.sunbird.org/use/release-notes/inquiry-release-v5.7.0) (V 5.7.0)\
Sunbird-Telemetry: [Documentation](https://telemetry.sunbird.org/)\
Sunbird-RC: [Documentation](https://docs.sunbirdrc.dev/learn/readme)

