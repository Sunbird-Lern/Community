# Release V 4.9.0

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date | Version |
| ------- | ------------ | ------- |
| Lern    | 18 May 2022  | V 4.9.0 |

### Details of Released Tag:

| Component         | Tag                                                                                                                 |
| ----------------- | ------------------------------------------------------------------------------------------------------------------- |
| Batch Service     | [**release-4.9.0\_RC4**](https://github.com/project-sunbird/sunbird-course-service/releases/tag/release-4.9.0\_RC4) |
| User\&Org Service | [**release-4.9.0\_RC1**](https://github.com/project-sunbird/sunbird-lms-service/releases/tag/release-4.9.0\_RC1)    |

### **Summary of the Changes** <a href="#1.-summary-of-the-changes" id="1.-summary-of-the-changes"></a>

* Enhancements for User and Org Data required for iGOT
* Enhancements in Course Service
* Enhanced Org Type Management
* Extended User Profile

### **Details of the Changes** <a href="#2.-details-of-the-changes" id="2.-details-of-the-changes"></a>

{% tabs %}
{% tab title="Batch Service" %}
| JIRA ID                                                           | Descriptions                                    |
| ----------------------------------------------------------------- | ----------------------------------------------- |
| [SB-29551](https://project-sunbird.atlassian.net/browse/SB-29551) | Enhancements in Course Service                  |
| [SB-29362](https://project-sunbird.atlassian.net/browse/SB-29362) | Storing RC context JSON in azure for deployment |
{% endtab %}

{% tab title="User&Org Service" %}
| JIRA ID                                                           | Descriptions                                         |
| ----------------------------------------------------------------- | ---------------------------------------------------- |
| [SB-29553](https://project-sunbird.atlassian.net/browse/SB-29553) | Enhancements for User and Org Data required for iGOT |
| [SB-29490](https://project-sunbird.atlassian.net/browse/SB-29490) | New feature - Enhanced Org Type Management           |
| [SB-29489](https://project-sunbird.atlassian.net/browse/SB-29489) | New feature - Extended User Profile                  |
{% endtab %}
{% endtabs %}

Detailed Information is present in the [JIRA](https://project-sunbird.atlassian.net/issues/?filter=12456) list.

**Manual Configuration**

| <p>Add soft link to Core/keys directory<br>in private repo for Sunbird-RC directory</p> | ln -s ../Core/keys/ keys |
| --------------------------------------------------------------------------------------- | ------------------------ |
