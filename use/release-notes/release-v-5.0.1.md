# Release V 5.0.1

### Document Release Version <a href="#document-release-version" id="document-release-version"></a>

| Project | Release Date | Version |
| ------- | ------------ | ------- |
| Lern    | 29 Nov 22    | V 5.0.1 |

### Details of Released Tag

| Components        | Tags                                                                                                                         |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Batch Service     | <p>sunbird-course-service : </p><p>cert-service : </p><p>certficate-registry : <strong></strong> </p><p>data-pipeline : </p> |
| User\&Org Service | sunbird-lms-service : [ **** ](https://github.com/Sunbird-Lern/sunbird-lms-service/releases/tag/release-5.0.0\_RC1)          |
| Data Products     | data-products :                                                                                                              |

### **Summary of the Changes** <a href="#1.-summary-of-the-changes" id="1.-summary-of-the-changes"></a>

* Making SB Lern Cloud agnostic

### Details of the Changes

[LR-262 ](https://project-sunbird.atlassian.net/browse/LR-262)OCI and Open stack support analysis

[LR-263 ](https://project-sunbird.atlassian.net/browse/LR-263)CSP integration testing in Non-Ed env

[LR-254 ](https://project-sunbird.atlassian.net/browse/LR-254)BatchService: CSP Data migration for certificate obj data in RC



Configurations:

The below environment variable needs to be configured in the devops repo.

cloud\_storage\_base\_url: https://sunbirddev.blob.core.windows.net
