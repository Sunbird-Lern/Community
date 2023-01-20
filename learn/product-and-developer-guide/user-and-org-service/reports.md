# Reports

There are two reports which comes under ‘MANAGE’ page in Sunbird Ed for 'ORG\_ADMIN' role. There reports are fetched from azure blob and details are displayed. Also allows to download in .csv format.

### **1. Geo-report:**

* geo-summary shows the number of schools, districts and blocks in a particular channel.
* geo-summary-district shows the data with respect to district.

StateAdminGeoReportJob generates three folders in azure blob : geo-detail, geo-summary, geo-summary-district&#x20;

**geo-detail** contains csv reports with channel name and geo-summary, geo-summary-district contains json reports with channel name.

\
**geo-summary** shows the number of schools, districts and blocks in a particular channel. Example: \[{"index":1,"districtName":"CHITTOOR","blocks":1,"schools":1}].

\
**geo-summary-district** provides the data with respect to district. Example: \[{"index":1,"districtName":"ARIYALUR","blocks":6,"schools":796},{"index":2,"districtName":"CHENNAI","blocks":10,"schools":1472},]

### 2. User-consent report:

Consent Report gives the user info channel-wise as per the consent given by user. StateAdminReportJob generates a folder declared\_user\_detail which contains the user declared consent and user details. It is generated in csv format with respect to channel name.

Consent report CSV content:

| **Column Label**       | **Column Type** | **Data Type** | **Description**                                                                                                                                              |
| ---------------------- | --------------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Name                   | Static          | String        | Name of the user                                                                                                                                             |
| Diksha UUID            | Static          | String        | The system generated DIKSHA unique user ID                                                                                                                   |
| State                  | Static          | String        | User declared state for self signed up users. If the user is a state validated user then the state as passed from state SSO or derived from school ID.       |
| District               | Static          | String        | User declared district for self signed up users. If the user is a state validated user then the district as passed from state SSO or derived from school ID. |
| Block                  | Static          | String        | User declared block for self signed up users. If the user is a state validated user then the block as passed from state SSO or derived from school ID.       |
| Cluster                | Static          | String        | User declared cluster for self signed up users. If the user is a state validated user then the cluster as passed from state SSO or derived from school ID.   |
| School Name            | Static          | String        | If user is state validated teacher then the school name mapped to this user. If user is self declared user then the user declared org/school name.           |
| School UDISE ID        | Static          | String        | If user is state validated teacher then the school UDISE ID mapped to this user. If user is self declared user then the user declared org/school UDISE ID.   |
| State provided ext. ID | Static          | Number        | Self declared users this is their declared ID. For state validated users this is their Teacher ID                                                            |
| Profile Email          | Static          | String        | User declared unmasked email ID from user profile                                                                                                            |
| Profile Phone number   | Static          | String        | User declared unmasked mobile number from user profile                                                                                                       |
| Org Phone              | Static          | String        | User declared unmasked mobile number from consent declaration                                                                                                |
| Org Email ID           | Static          | String        | User declared unmasked email ID from consent declaration                                                                                                     |
| User Type              | Static          | String        | User type from user profile                                                                                                                                  |
| User-Sub Type          | Static          | String        | User sub type from user profile                                                                                                                              |
| Root Org of user       | Static          | String        | Root/Tenant Org the user belongs to                                                                                                                          |

Configuration and setup:

Both the reports are present in&#x20;

[https://github.com/Sunbird-Lern/data-products/tree/master/lern-data-products/src/main/scala/org/sunbird/userorg/job/report](https://github.com/Sunbird-Lern/data-products/tree/master/lern-data-products/src/main/scala/org/sunbird/userorg/job/report)

These can be configured as cron jobs.

\#Ansible: sunbirdstaging-admin-user-reports-3AMIST\
30 21 \* \* \* /mount/data/analytics/scripts/run-job.sh admin-user-reports\
\#Ansible: sunbirdstaging-admin-user-reports-2PMIST\
30 8 \* \* \* /mount/data/analytics/scripts/run-job.sh admin-user-reports\
\#Ansible: sunbirdstaging-admin-geo-reports-3PMIST\
30 9 \* \* \* /mount/data/analytics/scripts/run-job.sh admin-geo-reports\
\#Ansible: sunbirdstaging-admin-geo-reports-4AMIST\
30 22 \* \* \* /mount/data/analytics/scripts/run-job.sh admin-geo-reports

Also can be run explicitly by using below jenkins job : [https://10.20.0.14/jenkins/job/Deploy/job/staging/job/DataPipeline/job/AnalyticsReplayJobs/](https://10.20.0.14/jenkins/job/Deploy/job/staging/job/DataPipeline/job/AnalyticsReplayJobs/)

set Job\_type : run-job

set job\_id :&#x20;

admin-user-reports → for running User-Consent report

admin-geo-reports → for running Geo-report
