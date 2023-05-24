# Release V 5.3.0

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date | Version |
| ------- | ------------ | ------- |
| Lern    |              | V 5.3.0 |

### Details of Released Tag

| Components        | Jenkins Job                  | Deploy Tags (Devops) | Build Tags (Github Repo Tags)                                                                                       | Repository                                                                                                                     |
| ----------------- | ---------------------------- | -------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Data pipeline     | Build/Lern/FlinkJobs         | release-5.3.0        | data-pipeline : [release-5.3.0\_RC1](https://github.com/Sunbird-Lern/data-pipeline/releases/tag/release-5.3.0\_RC1) | [https://github.com/Sunbird-Lern/data-pipeline](https://github.com/Sunbird-Lern/data-pipeline/releases/tag/release-5.3.0\_RC1) |
| Data Products     | Build/Lern/LernDataProducts/ | release-5.3.0        | data-products : [release-5.3.0\_RC1](https://github.com/Sunbird-Lern/data-products/releases/tag/release-5.3.0\_RC1) | [https://github.com/Sunbird-Lern/data-products](https://github.com/Sunbird-Lern/data-products)                                 |
| Batch Service     | Build/Core/Lms               | release-5.3.0        | <p>sunbird-course-service : <br></p>                                                                                | [https://github.com/Sunbird-Lern/sunbird-course-service](https://github.com/Sunbird-Lern/sunbird-course-service)               |
| User\&Org Service | Build/Core/Learner           | release-5.3.0        | sunbird-lms-service                                                                                                 | [https://github.com/Sunbird-Lern/sunbird-lms-service](https://github.com/Sunbird-Lern/sunbird-lms-service)                     |

**Summary of the Changes**



**Details of the Changes:**

[LR-436](https://project-sunbird.atlassian.net/browse/LR-436) OldCertificateMigration spark data-product\
[LR-437](https://project-sunbird.atlassian.net/browse/LR-437) LegacyCertificateMigrator Flink job\
[LR-438](https://project-sunbird.atlassian.net/browse/LR-438) Sunbird RC changes for updating schema for issued date\
[LR-330](https://project-sunbird.atlassian.net/browse/LR-330) Certificate template font url migration\
[LR-465](https://project-sunbird.atlassian.net/browse/LR-465) PII data security

### Env Configurations (Needs to be done before service deployment):

The below environment variable needs to be configured in the dev ops repo.

| Variable Name                  | Values                                                                                                        | Comments                                     |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| exhaust\_api\_base\_url        | \{{ analytics\_service\_url \| default('[http://analytics-service:9000](http://analytics-service:9000/)') \}} | Obsrv exhaust API endpoint for batch service |
| exhaust\_api\_submit\_endpoint | /request/submit                                                                                               | To submit job request from batch service     |
| exhaust\_api\_list\_endpoint   | /request/list/                                                                                                | To list job request from batch service       |

### Flink Job Configurations for Lern:

| Name of the Flink Job added     |
| ------------------------------- |
| **legacy-certificate-migrator** |

### Prerequired deployments for RC migration

<details>

<summary><a href="https://project-sunbird.atlassian.net/browse/LR-436">LR-436</a> - Deploy Data-product</summary>

Data-product build Jenkins job: **Build/Lern/LernDataProducts**

Deploy Jenkins job: **Deploy/\{{env\}}/Lern/LernDataProducts**

</details>

<details>

<summary><a href="https://project-sunbird.atlassian.net/browse/LR-437">LR-437</a> - Deploy legacy-certificate-migrator Flink job</summary>

Build Jenkins job: **/Build/job/Lern/job/FlinkJobs**

Deploy Jenkins job:  **/Deploy/job/\<environment>/job/Lern/job/FlinkJobs**

</details>

<details>

<summary><a href="https://project-sunbird.atlassian.net/browse/LR-438">LR-438</a> - Update RC schema</summary>

**Step 1 : Upload updated schema files.**\
Deploy Jenkins job: **Deploy/dev/Sunbird-RC/Upload\_RC\_Schema**

**Note**: Since certificate signer service will cache the credential template. please make sure the credential template is updated in the respective path as per below file.

[https://github.com/project-sunbird/sunbird-devops/blob/release-5.3.0-lern/utils/sunbird-RC/schema/credential\_template.json](https://github.com/project-sunbird/sunbird-devops/blob/release-5.3.0-lern/utils/sunbird-RC/schema/credential\_template.json)

**Step 2 : Deploy certificate signer service**

Jenkins Job: **Deploy/dev/Sunbird-RC/CertificateSign**





</details>

## Step to migrate old certificates to RC

Sunbird Lern BB is using Sunbird RC for generating & issuing e-credentials in its use cases (e.g.: course completion certificate) for all the latest completed courses (post March-2022). All the old certificates were custom generated and stored in Cassandra and cloud storage.

Once we migrate these certificates then we no longer need to store certificates in Cassandra and all the certificates will be using Sunbird RC going forward.

Reference Link: [https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3117416449/LR-4+Design+of+migrating+existing+certificate+in+to+RC](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3117416449/LR-4+Design+of+migrating+existing+certificate+in+to+RC)

**Step 1**

Create Kafka topic for only the purpose of this migration process

**Topic name:** \{{env\}}.legacy.certificate.migrate

**Step 2**

In the spark machine, update the **`old-certificate-migration-job`** model config in **`mount/data/analytics/scripts/lern-model-config.sh`** with correct values.

Sample model config:&#x20;

{% code overflow="wrap" %}
```
{"search":{"type":"none"},"model":"org.sunbird.lms.audit.OldCertificateMigrationJob","modelParams":{"mode":"execute","store":"azure","sparkCassandraConnectionHost":"10.5.3.17", "cert_base_path": "https://dev.lern.sunbird.org", "cloud_storage_base_url": "https://sunbirddev.blob.core.windows.net", "cloud_store_base_path_placeholder": "CLOUD_BASE_PATH","content_cloud_storage_container": "sunbird-content-staging", "cloud_storage_cname_url": "https://obj.stage.sunbirded.org", "batchId": "01320961460024934435", "kafka_broker": "localhost:9092", "kafka_topic": "sunbirddevlern.legacy.certificate.migrate","output_file_path":"./reports/"},"parallelization":8,"appName":"OldCertificateMigrationJob"}
```
{% endcode %}

Note: migration job can be run single batch with `"batchId": "01320961460024934435"` and multiple batches with `"batchId": "01320961460024934435,01220961460024934536"` and for all batches with `"batchId": "all"` .&#x20;

**Step 3**

Run the job with the below command in the spark machine.

```
/mount/data/analytics/scripts/lern-run-job.sh old-certificate-migration-job &
```

_Note:_ logs can be found in below locations,

Joblog: `/mount/data/analytics/scripts/logs/joblog.log`

Execution log: `/mount/data/analytics/logs/lern-data-products/{current_date}-job-execution.log`

**Note:**&#x20;

Verification steps can be found in the design page: [https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3117416449/LR-4+Design+of+migrating+existing+certificate+in+to+RC#Verification-steps-for-the-certificate-migration-process](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3117416449/LR-4+Design+of+migrating+existing+certificate+in+to+RC#Verification-steps-for-the-certificate-migration-process)

## Steps to Font URL migration

All the templates are having dev URLs configured for Fonts in all the environments as per our observation. All these font URLs have to be migrated to the new cname URL

**Note:** Before font url migration, make sure all the font files are available at cname mapped account or cloud storage container. To verify, where the font files are available, open any svg template file in editor and check the font URL's host.

Please use java 11 for running the scripts

#### Step 1:

Download SVG file migrator and uploader jars by below command,

```
cd ~
mkdir svg_template_migration
cd svg_template_migration
wget "https://github.com/kumarks1122/sunbird-utils/raw/release-5.3.0-font-url-migration/svg_template_migration/template-migration/svg-migrator.jar"
wget "https://github.com/kumarks1122/sunbird-utils/raw/release-5.3.0-font-url-migration/svg_template_migration/template-upload/svg-uploader.jar"
```

#### Step 2:

Download the svg template files and update the font URLs in the template files.

```
java -jar svg-migrator.jar "{{ content search host }}" "0" "1000" "font_migration" "{{ Old URL }}" "{{ cname url }}"

#EXAMPLE
#java -jar svg-migrator.jar "dev.lern.sunbird.org" "0" "1000" "font_migration" "https://sunbirddev.blob.core.windows.net" "https://obj.diksha.gov.in"
```

_**Note**:_ Before moving to next step, please verify atleast one svg file for whether the font URL got updated.

#### Step 3:

Upload the svg template files back to the cloud storage by below command.

```
java -jar svg-uploader.jar "{{ content search host }}" "0" "1000" "{{ storage key}}" "{{ storage secret }}" "{{svg file path}}" "{{storage type: (azure,..)}}" "{{ CSP endpoint (based on CSP it is optional) }}" "{{ region (based on CSP it is optional) }}"

#EXAMPLE
#java -jar svg-uploader.jar "dev.lern.sunbird.org" "0" "5" "sunbirddevbbpublic" "{{ secret }}" "/Users/{{username}}/svg_template_migration" "azure"
```
