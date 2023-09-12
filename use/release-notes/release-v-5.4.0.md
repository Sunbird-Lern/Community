# Release V 5.4.0 (Ongoing)

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date | Version |
| ------- | ------------ | ------- |
| Lern    | 11-Jul-2023  | V 5.4.0 |

### Details of Released Tag

<table data-full-width="false"><thead><tr><th width="166">Components</th><th width="167">Build Jenkins Job</th><th width="140">Build Tag</th><th width="192">Deploy Jenkins Job</th><th width="137">Deploy Tag</th><th width="197">Comment</th></tr></thead><tbody><tr><td>Proxy</td><td>Build/Core/Proxy</td><td></td><td><p>Deploy/Kubernetes/nginx-private-ingress</p><p></p><p>/Deploy/Kubernetes/nginx-public-ingress</p></td><td></td><td></td></tr><tr><td>OnboardAPIs</td><td></td><td></td><td>Deploy/Kubernetes/OnboardAPIs</td><td></td><td></td></tr><tr><td>UserOrg Service</td><td>Build/Core/UserOrg</td><td></td><td>Deploy/Kubernetes/UserOrg</td><td></td><td>Learner service is renamed as UserOrg now.</td></tr><tr><td>LMS Servive</td><td>Build/Core/LMS</td><td></td><td>Deploy/Kubernetes/LMS</td><td></td><td></td></tr><tr><td>Group Service</td><td>Build/Core/Groups</td><td></td><td>Deploy/Kubernetes/Groups</td><td></td><td></td></tr><tr><td>Notification service</td><td>Build/Core/Notification</td><td></td><td>Deploy/Kubernetes/Notification</td><td></td><td></td></tr><tr><td>Analytics Service</td><td></td><td></td><td>Deploy/Kubernetes/Analytics</td><td></td><td></td></tr><tr><td>Data Product</td><td>Build/Lern/LernDataProducts</td><td></td><td>Deploy/Lern/LernDataProducts</td><td></td><td></td></tr><tr><td>Keycloak</td><td></td><td></td><td>Deploy/Kubernetes/Keycloak</td><td></td><td></td></tr></tbody></table>

### **Summary of the Changes** <a href="#1.-summary-of-the-changes" id="1.-summary-of-the-changes"></a>

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

### Release Notes: Dependent building blocks

Sunbird-Knowlg: [Release notes](https://knowlg.sunbird.org/use/release-notes/release-5.5.0-latest) (V 5.5.0)\
Sunbird-Obsrv: [Release notes](https://knowlg.sunbird.org/use/release-notes/release-5.5.0-latest) (V 5.1.0)\
Sunbird-Ed: [Release notes ](https://ed.sunbird.org/use/releases/release-notes/release-5.2.0)(V 5.2.0)\
Sunbird-Inquiry: [Release notes](https://inquiry.sunbird.org/use/release-notes/inquiry-release-v5.7.0) (V 5.7.0)\
Sunbird-Telemetry: [Documentation](https://telemetry.sunbird.org/)\
Sunbird-RC: [Documentation](https://docs.sunbirdrc.dev/learn/readme)

