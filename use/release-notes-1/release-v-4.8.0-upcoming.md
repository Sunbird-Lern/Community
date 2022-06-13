# Release V 4.8.0

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date  | Version |
| ------- | ------------- | ------- |
| Lern    | 28 April 2022 | V 4.8.0 |

### Details of Released Tag:

| Component                  | Tag                                                                                                                 |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Batch Service              | [**release-4.8.0\_RC2**](https://github.com/project-sunbird/sunbird-course-service/releases/tag/release-4.8.0\_RC2) |
| CertRegistry               | release-4.8.5\_RC7                                                                                                  |
| kp flink                   | release-4.8.5\_RC4                                                                                                  |
| Sunbird-Rc/CertificateApi  |                                                                                                                     |
| Sunbird-Rc/CertificateSign |                                                                                                                     |
| Sunbird-Rc/Registry        |                                                                                                                     |

### **Summary of the Changes** <a href="#1.-summary-of-the-changes" id="1.-summary-of-the-changes"></a>

* Certificate Registry Integration with RC
* Update Lern BB Microsite
* Build and Deployment automation of Sunbird RC
* Contribute to RC on QR code generation with a specific type
*   Certificate Generator Job Integration with RC to re-issue the certificate

    ***

### **Details of the Changes** <a href="#2.-details-of-the-changes" id="2.-details-of-the-changes"></a>

{% tabs %}
{% tab title="Batch Service" %}
| JIRA ID                                                           | Descriptions                                                                                                                 |
| ----------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| [SB-29268](https://project-sunbird.atlassian.net/browse/SB-29268) | v1 RC create certificate API request is passed with valid parameters.                                                        |
| [SB-29262](https://project-sunbird.atlassian.net/browse/SB-29262) | \[Certificate key API] Certificate Key search API with Invalid osid                                                          |
| [SB-29126](https://project-sunbird.atlassian.net/browse/SB-29126) | Contribute to RC on QR code genration with specific type                                                                     |
| [SB-29124](https://project-sunbird.atlassian.net/browse/SB-29124) | Script to migrate templates in new format to support certificate generation using RC                                         |
| [SB-28980](https://project-sunbird.atlassian.net/browse/SB-28980) | Added validation to Certificate SignatoryList attributes                                                                     |
| [SB-28969](https://project-sunbird.atlassian.net/browse/SB-28969) | Enable flag for validate Certificate SignatoryList                                                                           |
| [SB-28746](https://project-sunbird.atlassian.net/browse/SB-28746) | Configuring and setting up sunbird-RC instance                                                                               |
| [SB-28733](https://project-sunbird.atlassian.net/browse/SB-28733) | Certificate Generator Job Integration with RC to re-issue certificate                                                        |
| [SB-28732](https://project-sunbird.atlassian.net/browse/SB-28732) | Certificate Generator Job Integration with RC to issue certificate and store certificate type, id and issue date in passbook |
| [SB-29068](https://project-sunbird.atlassian.net/browse/SB-29068) | Certificate Registry Integration with RC for download and search certificate                                                 |
| [SB-29118](https://project-sunbird.atlassian.net/browse/SB-29118) | API to store and fetch public key from RC                                                                                    |
{% endtab %}

{% tab title="Notification Service" %}
| JIRA ID                                                           | Descriptions                                     |
| ----------------------------------------------------------------- | ------------------------------------------------ |
| [SB-29311](https://project-sunbird.atlassian.net/browse/SB-29311) | Redirection on onclick of notification bell icon |
{% endtab %}
{% endtabs %}

Detailed Information is present in the [JIRA](https://project-sunbird.atlassian.net/issues/?filter=12417) list.

Environment Changes:

| Variable Names                                              | Env                       | value                                                                                                                                                                                                                                                                                                                                  |
| ----------------------------------------------------------- | ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| enable\_suppress\_exception                                 | kp flink                  |                                                                                                                                                                                                                                                                                                                                        |
| enable\_rc\_certificate                                     | kp flink                  |                                                                                                                                                                                                                                                                                                                                        |
| CERTIFICATE\_PRIVATE\_KEY                                   | CertificateSign           | <p>add cert private key variable in secrets.yml<br>https://www.scottbrady91.com/openssl/creating-rsa-keys-using-openssl<a href="https://github.com/Sunbird-RC/community/discussions/200"><br></a><a href="https://github.com/Sunbird-RC/community/discussions/200">https://github.com/Sunbird-RC/community/discussions/20</a>0<br></p> |
| collection\_certificate\_generator\_enable\_rc\_certificate | sunbird-learning-platform | [https://github.com/project-sunbird/sunbird-learning-platform](https://github.com/project-sunbird/sunbird-learning-platform)                                                                                                                                                                                                           |

Manual Configurations:

| <p>Template migration for sunbirdRc integration, please follow the wiki for the same<br><br></p> | [https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3107749898/SB-29124+SVG+Template+migration](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/3107749898/SB-29124+SVG+Template+migration) |
| ------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>Run curl command from registry service pod<br>and share response id with dev team</p>         | <p>curl --location --request POST 'http://localhost:8081/api/v1/PublicKey' &#x3C;br>--header 'Content-Type: application/json' &#x3C;br>--data-raw '{<br>"value": "",<br>"alg": "RSA"<br>}'</p>                 |
| Create sunbird-RC inventory folder(soft link to core common.yml, host, secrets.yml               |                                                                                                                                                                                                                |
| Create database in postgress kong (CREATE DATABASE registry;)                                    |                                                                                                                                                                                                                |
| Upload\_RC\_Schema                                                                               |                                                                                                                                                                                                                |
