# Release V 5.3.0

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date | Version |
| ------- | ------------ | ------- |
| Lern    |              | V 5.3.0 |

### Details of Released Tag

| Components        | Jenkins Job                  | Deploy Tags (Devops) | Build Tags (Github Repo Tags)                         | Repository                                                                                                                     |
| ----------------- | ---------------------------- | -------------------- | ----------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Data pipeline     | Build/Lern/FlinkJobs         | release-5.3.0        | data-pipeline : release-5.3.0\_RC2                    | [https://github.com/Sunbird-Lern/data-pipeline](https://github.com/Sunbird-Lern/data-pipeline/releases/tag/release-5.3.0\_RC1) |
| Data Products     | Build/Lern/LernDataProducts/ | release-5.3.0        | data-products : release-5.3.0\_RC2                    | [https://github.com/Sunbird-Lern/data-products](https://github.com/Sunbird-Lern/data-products)                                 |
| Batch Service     | Build/Core/Lms               | release-5.3.0        | <p>sunbird-course-service : release-5.3.0_RC1<br></p> | [https://github.com/Sunbird-Lern/sunbird-course-service](https://github.com/Sunbird-Lern/sunbird-course-service)               |
| User\&Org Service | Build/Core/Learner           | release-5.3.0        | sunbird-lms-service : release-5.3.0\_RC1              | [https://github.com/Sunbird-Lern/sunbird-lms-service](https://github.com/Sunbird-Lern/sunbird-lms-service)                     |
| s                 |                              |                      |                                                       |                                                                                                                                |

**Summary of the Changes**



**Details of the Changes:**

[LR-436](https://project-sunbird.atlassian.net/browse/LR-436) OldCertificateMigration spark data-product\
[LR-437](https://project-sunbird.atlassian.net/browse/LR-437) LegacyCertificateMigrator Flink job\
[LR-438](https://project-sunbird.atlassian.net/browse/LR-438) Sunbird RC changes for updating schema for issued date\
[LR-330](https://project-sunbird.atlassian.net/browse/LR-330) Certificate template font url migration\
[LR-395](https://project-sunbird.atlassian.net/browse/LR-395), [LR-465](https://project-sunbird.atlassian.net/browse/LR-465) PII data security\
[LR-451](https://project-sunbird.atlassian.net/browse/LR-451) Local setup of Data-pipeline - Ubuntu & Mac - Github and Microsite update\
[LR-443](https://project-sunbird.atlassian.net/browse/LR-443) Local setup of UserOrg - Ubuntu & Mac - Github and Microsite update\
[LR-445](https://project-sunbird.atlassian.net/browse/LR-445) Local setup of LMS - Ubuntu & Mac - Github and Microsite update\
[LR-422](https://project-sunbird.atlassian.net/browse/LR-422) Point the channel create API to content-service instead of learning-service\
[LR-519](https://project-sunbird.atlassian.net/browse/LR-519) Textbook APIs code cleanup from Course-Batch service\
[LR-486](https://project-sunbird.atlassian.net/browse/LR-486) Microsite update with Certificate generation flow diagram\
[LR-520](https://project-sunbird.atlassian.net/browse/LR-520) Group service - activity type should be case insensitive\
[LR-556](https://project-sunbird.atlassian.net/browse/LR-556) Local setup of LMS - Ubuntu & Mac - **Mock service setup**\
[LR-456](https://project-sunbird.atlassian.net/browse/LR-456) Local setup of Sunbird-utils - Ubuntu & Mac - Github and Microsite update\


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



### Data Security Policy setup

**Configurations to be done by System admin:**

1. Execute CURL for providing link to download "Decryption Tool"

```
curl --location --request POST '{{host}}/api/data/v1/system/settings/set' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--header 'x-authenticated-user-token: {{user_token}}' \
--data-raw '{
    "request": {
        "id": "decryptionToolLink",
        "field": "decryptionToolLink",
        "value": "{\"link\":\"<link to download decryption tool>\", \"Comments\": \"To use this tool, run the command with encrypted file and key to decrypt\"}"
    }
}'
```

2. Setup **default** 'Data Security Policy' settings using tenant preference API.&#x20;

```
curl --location --request POST '{{host}}/api/org/v2/preferences/create' \
--header 'x-authenticated-user-token: {{user_authentication_token}}' \
--header 'Authorization: Bearer {{kong_api_token}}' \
--header 'Content-Type: application/json' \
--data-raw '{
    "request": {
        "orgId": "default",
        "key": "dataSecurityPolicy",
        "data": {
            "level": "PLAIN_DATASET",
            "dataEncrypted": "No",
            "comments": "Data is not encrypted",
            "job": {
                    "progress-exhaust": {
                        "level": "PASSWORD_PROTECTED_DATASET",
                        "dataEncrypted": "No",
                        "comments": "Password protected file."
                    },
                    "response-exhaust": {
                        "level": "PASSWORD_PROTECTED_DATASET",
                        "dataEncrypted": "No",
                        "comments": "Password protected file."
                    },
                    "userinfo-exhaust": {
                        "level": "PASSWORD_PROTECTED_DATASET",
                        "dataEncrypted": "No",
                        "comments": "Password protected file."
                    }
                },
            "securityLevels": {
                "PLAIN_DATASET": "Data is present in plain text/zip. Generally applicable to open datasets.",
                "PASSWORD_PROTECTED_DATASET": "Password protected zip file. Generally applicable to non PII data sets but can contain sensitive information which may not be considered open.",
                "TEXT_KEY_ENCRYPTED_DATASET": "Data encrypted with a user provided encryption key. Generally applicable to non PII data but can contain sensitive information which may not be considered open.",
                "PUBLIC_KEY_ENCRYPTED_DATASET": "Data encrypted via an org provided public/private key. Generally applicable to all PII data exhaust."
            }
        }
    }
}'
```

3. Setup **default '**PII data security settings' using tenant preference API.

```
curl --location --request POST '{{host}}/api/org/v2/preferences/create' \
--header 'x-authenticated-user-token: {{user_authentication_token}}' \
--header 'Authorization: Bearer {{kong_api_token}}' \
--header 'Content-Type: application/json' \
--data-raw '{
    "request": {
        "orgId": "default",
        "key": "userPrivateFields",
        "data": {
            "PIIFields": [
                "email",
                "phone",
                "userName",
                "prevUsedEmail",
                "prevUsedPhone",
                "recoveryEmail",
                "recoveryPhone"
            ]
        }
    }
}'
```

**Configurations that can be done by Tenants:**

1. Use Tenant preference create API to create tenant specific 'Data Security Policy' settings similar to 'default' Data Security Policy settings but with tenant orgId.&#x20;

```
Note: 
a. Tenant level security cannot be lower than 'default' Data Security Policy'.
b. Job Level security Policy in a Tenant specific configuration cannot be lower than Tenant Level configuration and cannot be lower than job level configuration in 'default' Data Security Policy'.
c. Below mapping shows the priority/grade of security policies 
"PLAIN_DATASET" < "PASSWORD_PROTECTED_DATASET" < "TEXT_KEY_ENCRYPTED_DATASET" < "PUBLIC_KEY_ENCRYPTED_DATASET"
```

2. In order to use "PUBLIC\_KEY\_ENCRYPTED\_DATASET" security configuration for an exhaust report, tenant admin should have uploaded public pem key file using below API.&#x20;

```
curl --location --request PATCH '{{host}}/api/org/v1/update/encryptionkey' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{kong_api_token}}' \
--header 'x-authenticated-user-token: {{user_authentication_token}}' \
--form 'organisationId={{org_id}}' \
--form 'encryptionKey=@path_to_public_pem_file'
```

### Steps to generate key pair for setting up Data Security policy configuration:

#### For Linux and Mac OS:

1. To generate Private Key&#x20;

```
openssl genrsa -out private.pem 4096
```

2. To generate Public Key&#x20;

```
openssl rsa -in private.pem -pubout -outform PEM -out public_key.pem
```

#### For Windows OS:

Please install GitBash: The Git installation package comes with SSH. Using Git Bash, which is the Git command line tool, you can generate SSH key pairs. Git Bash has an SSH client that enables you to connect to and interact with Triton containers on Windows.

**To install Git:**

1. Download and initiate the [Git installer](https://git-scm.com/download/win).&#x20;
2. When prompted, accept the default components by clicking Next.&#x20;
3. Choose the default text editor. If you have Notepad++ installed, select Notepad++ and click Next.&#x20;
4. Select to Use Git from the Windows Command Prompt and click Next.&#x20;
5. Select to Use OpenSSL library and click Next.&#x20;
6. Select to Checkout Windows-style, commit Unix-style line endings and click Next.&#x20;
7. Select to Use MinTTY (The default terminal of mYSYS2) and click Next.&#x20;
8. Accept the default extra option configuration by clicking Install. When the installation completes, you may need to restart Windows.

**Launching GitBash:**&#x20;

1. press Start+R to launch the Run dialog.&#x20;
2. Type C:\Program Files\Git\bin\bash.exe and press Enter.

**Generating Key pair:**

1. To generate Private Key

```
openssl genrsa -out private.pem 4096
```

2. To generate Public Key

```
openssl rsa -in private.pem -pubout -outform PEM -out public_key.pem
```
