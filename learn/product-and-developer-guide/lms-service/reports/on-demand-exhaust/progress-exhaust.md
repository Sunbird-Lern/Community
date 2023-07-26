# Progress Exhaust

Progress exhaust contains the progress-related information for the collection and the nested collections including the assessment-related scores of the collection. The nested collections and the assessments within the collection will be transposed as columns and hence the columns for each collection exhaust file would vary. The progress exhaust report is for the enrolled user and the course batch.

<figure><img src="../../../../../.gitbook/assets/progress_Exhaust_report.png" alt=""><figcaption></figcaption></figure>

**Data Provider:**\
\
**cassandra**

1. user redis
2. user\_enrolments
3. assessment\_aggregator
4. user\_activity\_agg

**postgres**

1. job\_request table

**and Content search API**\


**Sample Job request:**

```
                                 tag                                  |            request_id            |      job_id      | status  |            request_data             |             requested_by             |  requested_channel   |    dt_job_submitted     |                                          download_urls                                          | dt_file_created |    dt_job_completed     | execution_time | err_message | iteration | encryption_key | batch_number |                                                                                                                      processed_batches                                                                                                                      
----------------------------------------------------------------------+----------------------------------+------------------+---------+-------------------------------------+--------------------------------------+----------------------+-------------------------+-------------------------------------------------------------------------------------------------+-----------------+-------------------------+----------------+-------------+-----------+----------------+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 do_2133074736487792641239_013307481768378368112:01269878797503692810 | 778A3669531143769B5E8C98D42E1CAD | progress-exhaust | SUCCESS | {"batchId":"013307481768378368112"} | fca2925f-1eee-4654-9177-fece3fd6afc9 | 01269878797503692810 | 2022-09-27 07:26:12.845 | {progress-exhaust/778A3669531143769B5E8C98D42E1CAD/013307481768378368112_progress_20220927.zip} |                 | 2022-09-27 08:02:20.728 |          29872 |             |         0 |                |              | [{"channel":"01269878797503692810","batchId":"013307481768378368112","filePath":"","fileSize":
```

\
\
**File Structure**

| **Format** | **Nomenclature**                                                                    | **Example**                                                      |
| ---------- | ----------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| **CSV**    | **progress-exhaust/{request\_id}/**_**\<batch\_id>\_progress\_\<updatedDate>.csv**_ | _**do\_1130264512015646721166\_\_progress\_\_26\_08\_2020.csv**_ |

#### File Contents <a href="#file-contents" id="file-contents"></a>

| **Column Label**   | **Column Type** | **Data Type** | **Description**                                                                                                                                           |
| ------------------ | --------------- | ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Collection Id      | Static          | String        | Id of the collection.                                                                                                                                     |
| Collection Name    | Static          | String        | Collection Title                                                                                                                                          |
| Batch Id           | Static          | String        | Batch Id                                                                                                                                                  |
| Batch Name         | Static          | String        | Batch Title                                                                                                                                               |
| User UUID          | Static          | String        | The system generated unique user ID                                                                                                                       |
| User Name          | Static          | String        | Name of the user                                                                                                                                          |
| State              | Static          | String        | User declared state for self signed up users. If the user is a org validated user then the state as passed from org SSO or derived from Sub-Org ID.       |
| District           | Static          | String        | User declared district for self signed up users. If the user is a org validated user then the district as passed from Org SSO or derived from Sub-Org ID. |
| Enrolment Date     | Static          | Date          | Collection enrolment date (for nested courses/collections it will be the parent collection enrolment date)                                                |
| Completion Date    | Static          | Date          | Collection completion date (for nested courses/collections it will be the parent collection completion date)                                              |
| Progress           | Static          | Number        | Collection progress (for nested courses/collections this will be the parent collection progress)                                                          |
| Certificate Status | Static          | String        | Issued - if the certificate is issued. Blank - if it is not issued and. Failed - if issue has failed                                                      |
| Total Score        | Static          | Number        | Total Score received by the user across all assessments within the collection with category type as “SelfAssess”                                          |

#### Sample Data <a href="#sample-data" id="sample-data"></a>

```csv
Collection Id,Collection Name,Batch Id,Batch Name,User UUID,User Name,State,District,Enrolment Date,Completion Date,Progress,Certificate Status,Total Score
do_1130934466492252161819,Test Course,1.3093449510953E+017,Batch1,f703de4e-d47a-4adb-856c-de122e6a0b32,Mathew Pallan,Kerala,Thrissur,2020-08-25 13:45:54:150+0000,2020-08-27 13:45:54:150+0000,100,Issued,7
do_1130934466492252161819,Test Course,1.3093449510953E+017,Batch1,587204af-41db-4313-b3ab-cf022d3055c6,Krishna Jampana,Andhra Pradesh,Vizag,2020-08-25 02:15:58:691+0000,,57,,6
```

\
