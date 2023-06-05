---
description: This guide helps to deploy in local and server.
---

# Installation Guide

## Setup of data-products in local machine

Each data-product is an independent spark job used for generating reports and data migrations, so each has different sets of data provider dependencies. So the data-products can be tested locally with the test cases. Kindly find the local setup guide from the below link.

{% embed url="https://github.com/Sunbird-Lern/data-products/tree/release-5.4.0" %}
README.md
{% endembed %}

## Setup and execution of data-products in the server

Each data-product is an independent spark job that runs in a spark-submit mode for generating reports and data migrations. So it requires, all the data sources and dependency libraries to be present before executing data-product.

### Building data-product

Job Path: <mark style="color:green;">Build/Lern/LernDataProducts</mark>

### **Deploying data-product**

Job Path: <mark style="color:green;">Deploy/\{{env\}}/Lern/LernDataProducts</mark>

Params:

* **`module`** - this parameter used to deploy respective process of data-products deployment
  1. `lern-dataproducts` - to deploy data-products
  2. &#x20;`lern-dataproducts-spark-cluster` - to deploy data-products in spark cluster (such as hd insight cluster)
  3. `cronjobs` - to update cronjobs in server
* `remote` - to which spark server to deploy the above module

### **Cron jobs**

Data-product is running in demon mode which is getting triggered based on schedule by using cronjobs.

```
## Cron job list for LERN data-products

#Ansible: sunbird-job-manager
30 2 * * * /mount/data/analytics/scripts/start-jobmanager.sh
#Ansible: sunbird-course-batch-status-updater
*/60 * * * * /mount/data/analytics/scripts/lern-run-job.sh course-batch-status-updater
#Ansible: sunbird-admin-user-reports-2PMIST
30 8 * * * /mount/data/analytics/scripts/lern-run-job.sh admin-user-reports
#Ansible: sunbird-admin-user-reports-3AMIST
30 21 * * * /mount/data/analytics/scripts/lern-run-job.sh admin-user-reports
#Ansible: sunbird-admin-geo-reports-3PMIST
30 9 * * * /mount/data/analytics/scripts/lern-run-job.sh admin-geo-reports
#Ansible: sunbird-admin-geo-reports-4AMIST
30 22 * * * /mount/data/analytics/scripts/lern-run-job.sh admin-geo-reports
#Ansible: sunbird-progress-exhaust
0 08 * * * /mount/data/analytics/scripts/lern-run-job.sh progress-exhaust
#Ansible: sunbird-response-exhaust
0 09 * * * /mount/data/analytics/scripts/lern-run-job.sh response-exhaust
#Ansible: sunbird-cassandra-migration
15 19 * * * /mount/data/analytics/scripts/lern-run-job.sh cassandra-migration
#Ansible: sunbird-userinfo-exhaust
0 10 * * * /mount/data/analytics/scripts/lern-run-job.sh userinfo-exhaust
#Ansible: sunbird-collection-summary
30 09 * * * /mount/data/analytics/scripts/lern-run-job.sh collection-summary-report
```

### Provisioning Postgres DB for exhaust job execution

In data-products, exhaust jobs are using job\_request table from postgres DB for maintaining the exhaust job requests.&#x20;

Job Path: <mark style="color:green;">Provision/\{{env\}}/DataPipeline/PostgresDbUpdate</mark>

### Running a data-product

Data-product is running in server using cronjobs. For development and testing purpose, below Jenkins job can be used to trigger the job with respective job id.

Job Path: <mark style="color:green;">Deploy/\{{env\}}/Lern/LernAnalyticsReplayJobs</mark>

Params:

* job\_type - `run-job`
* job\_id - specific job id such as (admin-user-reports, progress-exhaust)
* batch\_identifier - specific batch id
* start\_date - Data consumption start date. not required for LERN data-products
* end\_date - Data consumption end date. not required for LERN data-products
* private\_branch - specific private branch
* branch\_or\_tag - public branch

### Logs for Data-products

In the server, the spark execution log can be found in the below location.

```
/mount/data/analytics/logs/lern-data-products/{{date}}-job-execution.log
```

Also, from the job we are having logs for identifying the status of the job. This type of log configurable to put either in log file or kafka topic based on below config.

```
log.appender.kafka.enable="{{ boolean }}"
log.appender.kafka.broker_host="{{ host }}:9092"
log.appender.kafka.topic="{{ env }}.druid.events.log"
```

If `log.appender.kafka.enable` is `false`, the log goes into the below file.

```
/mount/data/analytics/scripts/logs/joblog.log
```
