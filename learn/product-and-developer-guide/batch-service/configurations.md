# Functional Configurations

There are various configurations that can be made via the Batch Service:

* Batch type: Open (users can enroll by themselves)
* Batch Start date and End date and Enrolment End date
* Certificate generation for batch
* Criteria for earning a certificate (minimum score for the course assessment)

Following are the functional configurations

| Property                                       | Description                                                        | Default Value                   |
| ---------------------------------------------- | ------------------------------------------------------------------ | ------------------------------- |
| batch\_type                                    | Open (users can enrol by themselves) or                            | 0                               |
| quartz\_course\_batch\_timer                   | cron expression for scheduling batch job                           | 0 0 0/4 1/1 \* ? \*             |
| quartz\_upload\_timer                          | cron expression for scheduling batch job                           | 0 0 23 1/1 \* ? \*              |
| quartz\_course\_publish\_timer                 | cron expression for scheduling batch job                           | 0 0 0/1 1/1 \* ? \*             |
| quartz\_matrix\_report\_timer                  | cron expression for scheduling batch job                           | 0 0 0/4 1/1 \* ? \*             |
| quartz\_shadow\_user\_migration\_timer         | cron expression for scheduling batch job                           | 0 0 2 1/1 \* ? \*               |
| download\_link\_expiry\_timeout                | Duration of the download link in seconds                           | 300                             |
| quartz\_metrics\_timer                         | cron expression for scheduling batch job                           | 0 0 0/4 \* \* ? \*              |
| sunbird\_user\_bulk\_upload\_size              | size of user bulk upload data is 1001 including header in csv file | 1001                            |
| bulk\_upload\_org\_data\_size                  | size of org bulk upload data                                       | 300                             |
| bulk\_upload\_batch\_data\_size                | size of batch bulk upload data                                     | 200                             |
| default\_date\_range                           | Date range defaults to 7 days                                      | 7                               |
| sunbird\_default\_country\_code                | Country Code                                                       | +91                             |
| quartz\_update\_user\_count\_timer             | cron expression for scheduling batch job                           | 0 0 2 1/1 \* ? \*               |
| sunbird\_otp\_allowed\_attempt                 | Default limit of OTP attempts                                      | 2                               |
| searchTopN                                     | elastic search top n result count for telemetry                    | 5                               |
| telemetry\_queue\_threshold\_value             | telemetry threshold                                                | 200                             |
| file\_upload\_max\_size                        | Bulk upload file max size in MB                                    | 10MB                            |
| cassandra\_write\_batch\_size                  | Batch size for cassandra batch operation                           | 100                             |
| textbook\_toc\_max\_csv\_rows                  | Textbook TOC                                                       | 6500                            |
| sunbird\_texbook\_toc\_csv\_ttl                | Textbook TOC                                                       | 86400                           |
| sunbird\_toc\_max\_first\_level\_units         | Textbook TOC Api                                                   | 30                              |
| sunbird\_otp\_expiration                       | OTP expiration duration in seconds                                 | 1800                            |
| sunbird\_otp\_length                           | length of the OTP                                                  | 6                               |
| sunbird\_otp\_hour\_rate\_limit                | In a hour, 5 configured OTPs were allowed                          | 5                               |
| sunbird\_otp\_day\_rate\_limit                 | In a day, 20 configured OTPs were allowed                          | 20                              |
| sunbird\_sync\_read\_wait\_time                | wait time in seconds                                               | 1500                            |
| sunbird\_course\_completion\_certificate\_name | Certificate name                                                   | 100PercentCompletionCertificate |
| enrollment\_list\_size                         | number of enrolmen                                                 | 1000                            |

