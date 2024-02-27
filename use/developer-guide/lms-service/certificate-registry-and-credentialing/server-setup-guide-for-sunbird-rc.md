# Server Setup guide for Sunbird-RC

### Required jobs to build and deployed

Since APIs intercommunicated with other services, deploy the services in below order

<table><thead><tr><th width="165">Component</th><th>Build Job</th><th>Deploy Job</th></tr></thead><tbody><tr><td>CertificateAPI</td><td>Build/Sunbird-RC/CertificateApi</td><td>Deploy/Sunbird-RC/CertificateApi</td></tr><tr><td>Uploading Schema files to Cloud</td><td></td><td>Deploy/Sunbird-RC/Upload_RC_Schema</td></tr><tr><td>CertificateSign</td><td>Build/Sunbird-RC/CertificateSign</td><td>Deploy/Sunbird-RC/CertificateSign</td></tr><tr><td>Registry</td><td>Build/Sunbird-RC/Registry</td><td>Deploy/Sunbird-RC/Registry</td></tr></tbody></table>

### **Steps to update certificate schema**

**Step 1 : Upload updated schema files.**\
Deploy Jenkins job: **Deploy/dev/Sunbird-RC/Upload\_RC\_Schema**

**Note**: Since certificate signer service will cache the templates. please ensure the template is updated in the respective path as per the files below.

[https://github.com/project-sunbird/sunbird-devops/blob/release-5.3.0-lern/kubernetes/helm\_charts/sunbird-RC/registry/schemas/TrainingCertificate.json](https://github.com/project-sunbird/sunbird-devops/blob/release-5.3.0-lern/kubernetes/helm\_charts/sunbird-RC/registry/schemas/TrainingCertificate.json)

[https://github.com/project-sunbird/sunbird-devops/blob/release-5.3.0-lern/utils/sunbird-RC/schema/credential\_template.json](https://github.com/project-sunbird/sunbird-devops/blob/release-5.3.0-lern/utils/sunbird-RC/schema/credential\_template.json)

**Step 2 : Deploy certificate signer service**

Jenkins Job: **Deploy/dev/Sunbird-RC/CertificateSign**
