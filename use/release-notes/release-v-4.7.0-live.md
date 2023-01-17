# Release V 4.7.0

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date  | Version |
| ------- | ------------- | ------- |
| Lern    | 01 March 2022 | V 4.7.0 |

### Details of Released Tag:

| Component         | Tag                                                                                                                 |
| ----------------- | ------------------------------------------------------------------------------------------------------------------- |
| User\&Org Service | [**release-4.9.0\_RC4**](https://github.com/sunbird-lern/sunbird-course-service/releases/tag/release-4.9.0\_RC4) |
| Discussion Forum  | [**release-4.7.0\_RC4**](https://github.com/Sunbird-Lern/discussions-middleware/releases/tag/release-4.7.0\_RC4)    |

### **Summary of the Changes** <a href="#1.-summary-of-the-changes" id="1.-summary-of-the-changes"></a>

In 4.7.0, the following changes were implemented by the Lern BB,

* Fixed course enrolment list API issue, while fetching more than 1000 enrolments
* Sorted enrolment API list response as per last access date
* Added log4j vulnerability fix
* Standardized Error code implementation in userOrg service
* Extensive updates to the Lern microsite documentation ([https://inquiry.sunbird.org/](https://inquiry.sunbird.org/))

### **Details of the Changes** <a href="#2.-details-of-the-changes" id="2.-details-of-the-changes"></a>

{% tabs %}
{% tab title="UserOrg Service" %}
| JIRA ID                                                           | Descriptions                                   |
| ----------------------------------------------------------------- | ---------------------------------------------- |
| [SB-28201](https://project-sunbird.atlassian.net/browse/SB-28201) | Error Code implementation                      |
| [SB-27875](https://project-sunbird.atlassian.net/browse/SB-27875) | Consent report data validation and corrections |
| [SB-28039](https://project-sunbird.atlassian.net/browse/SB-28039) | Log4j vulnerability Fix                        |
| [SB-28560](https://project-sunbird.atlassian.net/browse/SB-28560) | Deprecated FLAG\_REVIEWER role                 |
{% endtab %}

{% tab title="Batch Service" %}
| JIRA ID                                                           | Descriptions                                                                 |
| ----------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| [SB-28497](https://project-sunbird.atlassian.net/browse/SB-28497) | Fixed enrolment API sorting issue                                            |
| [SB-28560](https://project-sunbird.atlassian.net/browse/SB-28560) | ES-client upgrade to 6.8.22. Error code updation for UserOrgService API call |
| [SB-28064](https://project-sunbird.atlassian.net/browse/SB-28064) | Log4j vulnerability Fix                                                      |
{% endtab %}

{% tab title="Discussion Forum" %}
| JIRA ID                                                           | Description                         |
| ----------------------------------------------------------------- | ----------------------------------- |
| [SB-28567](https://project-sunbird.atlassian.net/browse/SB-28567) | DF audit events configuration check |
| [SB-28743](https://project-sunbird.atlassian.net/browse/SB-28743) | <p>pdata version update<br></p>     |
{% endtab %}
{% endtabs %}

Detailed Information is present in the [JIRA](https://project-sunbird.atlassian.net/issues/?filter=12362) list.
