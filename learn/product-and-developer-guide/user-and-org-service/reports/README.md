# Reports

There are two reports which comes under ‘MANAGE’ page in Sunbird Ed for 'ORG\_ADMIN' role. There reports are fetched from azure blob and details are displayed. Also allows to download in .csv format.

UserOrg service jobs include:

* State Admin Geo Report
* State Admin Report or User Consent Report
* User Cache Indexer Job

#### Configuration and setup:

These can be configured as cron jobs.

\#Ansible: sunbirdstaging-admin-user-reports-3AMIST\
30 21 \* \* \* /mount/data/analytics/scripts/run-job.sh admin-user-reports\
\#Ansible: sunbirdstaging-admin-user-reports-2PMIST\
30 8 \* \* \* /mount/data/analytics/scripts/run-job.sh admin-user-reports\
\#Ansible: sunbirdstaging-admin-geo-reports-3PMIST\
30 9 \* \* \* /mount/data/analytics/scripts/run-job.sh admin-geo-reports\
\#Ansible: sunbirdstaging-admin-geo-reports-4AMIST\
30 22 \* \* \* /mount/data/analytics/scripts/run-job.sh admin-geo-reports



Also can be run explicitly by using below jenkins job :&#x20;

Deploy/DataPipeline/AnalyticsReplayJobs

set Job\_type : run-job

set job\_id :&#x20;

admin-user-reports → for running User-Consent report

admin-geo-reports → for running Geo-report
