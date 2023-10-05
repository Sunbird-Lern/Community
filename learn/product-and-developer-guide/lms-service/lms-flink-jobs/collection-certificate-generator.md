# Collection Certificate Generator

_**'collection-certificate-generator'**_ job is used to generate certificates.

<div data-full-width="true">

<figure><img src="../../../../.gitbook/assets/Cert Generator.drawio.png" alt=""><figcaption></figcaption></figure>

</div>

**Configuration variables:**

<table><thead><tr><th width="246">Variable</th><th>Default Value</th><th>Purpose</th></tr></thead><tbody><tr><td>kafka.input.topic</td><td>{{env}}.generate.certificate.request</td><td>Kafka topic from which messages/events are read to be processed.</td></tr><tr><td>kafka.output.failed.topic</td><td>{{env}}.generate.certificate.failed</td><td>Kafka topic to which message is written when an exception occurs while processing an event.</td></tr><tr><td>kafka.output.audit.topic</td><td>{{env}}.telemetry.raw</td><td>Kakfa topic to which and audit message is written to.</td></tr><tr><td>kafka.groupId</td><td>{{env}}-certificate-generator-group</td><td>Kafka input topic group Id</td></tr><tr><td>lms-cassandra.keyspace</td><td>sunbird_courses</td><td>Cassandra keyspace name</td></tr><tr><td>lms-cassandra.course_batch.table</td><td>course_batch</td><td>Cassandra table used to store batch details of a collection. Batch status, start date , end date , batch enrolment end date, enrolment type (open/invite-only), certificate templates etc are stored in this table.</td></tr><tr><td>lms-cassandra.user_enrolments.table</td><td>user_enrolments</td><td>Cassandra table used to store user enrolment data in a collection of a particular batch. This also holds the consumption progress, enrolment status and issued certificate details</td></tr><tr><td>lms-cassandra.sbkeyspace</td><td>sunbird</td><td>Sunbird Keyspace</td></tr><tr><td>lms-cassandra.certreg.table</td><td>cert_registry</td><td>Cassandra table used to store user certificates (old format)</td></tr><tr><td>task.rc.badcharlist</td><td>\x00,\\aaa,\aaa,Ø,Ý</td><td></td></tr><tr><td>service.content.basePath</td><td></td><td>Content service URL</td></tr><tr><td>service.learner.basePath</td><td></td><td>User-Org service URL</td></tr><tr><td>service.enc.basePath</td><td></td><td>Encryption service base path</td></tr><tr><td>service.rc.basePath</td><td></td><td>Sunbird RC base path</td></tr><tr><td>service.rc.entity</td><td>TrainingCertificate</td><td>variable used to specify sunbird RC API endpoint for certificate</td></tr><tr><td>enable.rc.certificate</td><td>true</td><td>variable used to enable RC certificate generation</td></tr><tr><td>enable.suppress.exception</td><td>true</td><td>Variable used to suppress exception if the signatory list is empty</td></tr><tr><td>cloud_storage_base_url</td><td></td><td>variable to identify the cloud storage base url. Used to replace the base url with variable mentioned in cloud_store_base_path_placeholder while storing to databases</td></tr><tr><td>cloud_store_base_path_placeholder</td><td>CLOUD_BASE_PATH</td><td>relative variable used to replace cloud storage base urls and stored in database</td></tr><tr><td>content_cloud_storage_container</td><td></td><td>cloud storage container name</td></tr><tr><td>cloud_storage_cname_url</td><td></td><td>variable used to replace 'cloud_store_base_path_placeholder' value with cname or cloud storage url while reading data from database.</td></tr></tbody></table>

**Sample event:**

```json
{
  "eid": "BE_JOB_REQUEST",
  "ets": 1563788371969,
  "mid": "LMS.1563788371969.590c5fa0-0ce8-46ed-bf6c-681c0a1fdac8",
  "actor": {
    "type": "System",
    "id": "Certificate Generator"
  },
  "context": {
    "pdata": {
      "ver": "1.0",
      "id": "org.sunbird.platform"
    }
  },
  "object": {
    "type": "GenerateCertificate",
    "id": "874ed8a5-782e-4f6c-8f36-e0288455901e"
  },
  "edata": {
    "userId": "user001",
    "svgTemplate": "https://ntpstagingall.blob.core.windows.net/user/cert/File-01311849840255795242.svg",
    "templateId": "template_01_dev_001",
    "courseName": "new course may23",
    "data": [
      {
        "recipientName": "Creation ",
        "recipientId": "user001"
      }
    ],
    "name": "100PercentCompletionCertificate",
    "tag": "0125450863553740809",
    "issuer": {
      "name": "Gujarat Council of Educational Research and Training",
      "url": "https://gcert.gujarat.gov.in/gcert/",
      "publicKey": [
        "1",
        "2"
      ]
    },
    "signatoryList": [
      {
        "name": "CEO Gujarat",
        "id": "CEO",
        "designation": "CEO",
        "image": "https://cdn.pixabay.com/photo/2014/11/09/08/06/signature-523237__340.jpg"
      }
    ],
    "criteria": {
      "narrative": "course completion certificate"
    },
    "basePath": "https://dev.sunbirded.org/certs",
    "related": {
      "type": "course",
      "batchId": "0131000245281587206",
      "courseId": "do_11309999837886054415"
    }
  }
}
```

**Source code:**

{% embed url="https://github.com/Sunbird-Lern/data-pipeline/tree/release-5.3.0/lms-jobs/credential-generator/collection-certificate-generator" %}
