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

<table data-header-hidden><thead><tr><th width="174"></th><th width="125"></th><th width="99"></th><th></th></tr></thead><tbody><tr><td><strong>Column Label</strong></td><td><strong>Column Type</strong></td><td><strong>Data Type</strong></td><td><strong>Description</strong></td></tr><tr><td>Name</td><td>Static</td><td>String</td><td>Name of the user</td></tr><tr><td>Diksha UUID</td><td>Static</td><td>String</td><td>The system generated DIKSHA unique user ID</td></tr><tr><td>State</td><td>Static</td><td>String</td><td>User declared state for self signed up users. If the user is a state validated user then the state as passed from state SSO or derived from school ID.</td></tr><tr><td>District</td><td>Static</td><td>String</td><td>User declared district for self signed up users. If the user is a state validated user then the district as passed from state SSO or derived from school ID.</td></tr><tr><td>Block</td><td>Static</td><td>String</td><td>User declared block for self signed up users. If the user is a state validated user then the block as passed from state SSO or derived from school ID.</td></tr><tr><td>Cluster</td><td>Static</td><td>String</td><td>User declared cluster for self signed up users. If the user is a state validated user then the cluster as passed from state SSO or derived from school ID.</td></tr><tr><td>School Name</td><td>Static</td><td>String</td><td>If user is state validated teacher then the school name mapped to this user. If user is self declared user then the user declared org/school name.</td></tr><tr><td>School UDISE ID</td><td>Static</td><td>String</td><td>If user is state validated teacher then the school UDISE ID mapped to this user. If user is self declared user then the user declared org/school UDISE ID.</td></tr><tr><td>State provided ext. ID</td><td>Static</td><td>Number</td><td>Self declared users this is their declared ID. For state validated users this is their Teacher ID</td></tr><tr><td>Profile Email</td><td>Static</td><td>String</td><td>User declared unmasked email ID from user profile</td></tr><tr><td>Profile Phone number</td><td>Static</td><td>String</td><td>User declared unmasked mobile number from user profile</td></tr><tr><td>Org Phone</td><td>Static</td><td>String</td><td>User declared unmasked mobile number from consent declaration</td></tr><tr><td>Org Email ID</td><td>Static</td><td>String</td><td>User declared unmasked email ID from consent declaration</td></tr><tr><td>User Type</td><td>Static</td><td>String</td><td>User type from user profile</td></tr><tr><td>User-Sub Type</td><td>Static</td><td>String</td><td>User sub type from user profile</td></tr><tr><td>Root Org of user</td><td>Static</td><td>String</td><td>Root/Tenant Org the user belongs to</td></tr></tbody></table>

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
