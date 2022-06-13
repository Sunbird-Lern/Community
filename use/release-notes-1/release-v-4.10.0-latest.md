# Release V 4.10.0 (Latest)

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date           | Version  |
| ------- | ---------------------- | -------- |
| Lern    | 10 June 22 (tentative) | V 4.10.0 |

### Details of Released Tag

| Component           | Tag                                          |
| ------------------- | -------------------------------------------- |
| Cassandra migration | sunbird-utils : release-4.10.0\_RC1          |
| User\&Org Service   | sunbird-lms-service : release-4.10.0\_RC1    |
| Discussion Forum    | discussions-middleware : release-4.10.0\_RC1 |

### **Summary of the Changes** <a href="#1.-summary-of-the-changes" id="1.-summary-of-the-changes"></a>

* DF Moderation changes
* OrgSearch to allow partial search and fuzzy Search

### **Details of the Changes** <a href="#2.-details-of-the-changes" id="2.-details-of-the-changes"></a>

{% tabs %}
{% tab title="User&Org Service" %}
| JIRA ID                                                           | Descriptions                                       |
| ----------------------------------------------------------------- | -------------------------------------------------- |
| [SB-27866](https://project-sunbird.atlassian.net/browse/SB-27866) | User accounts without Phone or Email Issue Fix     |
| [SB-29813](https://project-sunbird.atlassian.net/browse/SB-29813) | OrgSearch to allow partial search and fuzzy Search |
{% endtab %}

{% tab title="Discussion Forum" %}
| JIRA ID                                                           | Descriptions                           |
| ----------------------------------------------------------------- | -------------------------------------- |
| [SB-29794](https://project-sunbird.atlassian.net/browse/SB-29794) | Discussion forum >> Moderation changes |

**New Environment variables**

```
enable_audit_event={{ enable_audit_event | default(true) }}
moderation_flag={{ moderation_flag | default(false) }}
```
{% endtab %}
{% endtabs %}

Detailed Information is present in the [JIRA](https://project-sunbird.atlassian.net/issues/?filter=12500) list.

### Manual Configurations

| Manual Tasks                            | Details                                                                                                                                                                                                                            | Comments               |
| --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- |
| Reindex Org ES Index in UserOrg Service | [https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/2346156058/SC-2190+ES+scaling+-+reindexing+Org+index](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/2346156058/SC-2190+ES+scaling+-+reindexing+Org+index) | New index name - orgv3 |
