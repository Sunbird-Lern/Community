# Response Exhaust

The response exhaust report captures the user's responses to each question in the assessment. The response exhaust report contains data only if an assessment or question set is present. For each batch of users, a distinct response exhaust report is created. Each user's attempt at a particular question is exhaustively recorded, resulting in multiple rows for each attempt.\
m

<figure><img src="../../../../../.gitbook/assets/Response exhaust.png" alt=""><figcaption></figcaption></figure>

Overall, the code represents the job that processes user enrolment data and collects batch information. It retrieves assessment data, performs necessary transformations, joins with content data, and organizes the resulting DataFrame as a response exhaust report.

#### Data provider: <a href="#file-structure.2" id="file-structure.2"></a>

**cassandra**

1. user redis
2. user\_enrolments
3. assessment\_aggregator
4. user\_activity\_agg

**postgres**

1. job\_request table

**Content search API**

#### File Structure <a href="#file-structure.2" id="file-structure.2"></a>

| **Format** | **Nomenclature**                                                                    | **Example**                                                  |
| ---------- | ----------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| **CSV**    | **response-exhaust/{request\_id}/**_**\<batch\_id>\_response\_\<updatedDate>.csv**_ | _**do\_1130264512015646721166\_response\_26\_08\_2020.csv**_ |

#### File Contents <a href="#file-contents.2" id="file-contents.2"></a>

| **Column Label**     | **Column Type** | **Data Type** | **Description**                                                                 |
| -------------------- | --------------- | ------------- | ------------------------------------------------------------------------------- |
| Collection Id        | Static          | String        | Unique Collection Identifier                                                    |
| Collection Name      | Static          | String        | Collection Title                                                                |
| Batch Id             | Static          | String        | Batch Id                                                                        |
| Batch Name           | Static          | String        | Batch Title                                                                     |
| User UUID            | Static          | String        | The system generated unique user ID                                             |
| User Name            | Static          | String        | Name of the user                                                                |
| QuestionSet Id       | Static          | String        | Id of the question set                                                          |
| QuestionSet Title    | Static          | String        | Title of the question set                                                       |
| Attempt Id           | Static          | String        | Id of the attempt. There can be more than one attempt for the same question set |
| Attempted On         | Static          | DateTime      | Date on which the last attempt happened for this attempt id                     |
| Question Id          | Static          | String        | Question id                                                                     |
| Question Type        | Static          | String        | Question type - mcq/mtf/mmcq/ftb                                                |
| Question Title       | Static          | String        | Title of the question                                                           |
| Question Description | Static          | String        | Description of the question                                                     |
| Question Duration    | Static          | Number        | Time taken to answer the question                                               |
| Question Score       | Static          | Number        | Score received for the question                                                 |
| Question Max Score   | Static          | Number        | Max applicable score for the question                                           |
| Question Options     | Static          | JSON          | Options shown to the user                                                       |
| Question Response    | Static          | JSON          | Responses given by the user                                                     |

**Consent Fields**

* Question Response

**Sample Data**

```csv
Collection Id,Collection Name,Batch Id,Batch Name,User UUID,QuestionSet Id,QuestionSet Title,Attempt Id,Attempted On,Question Id,Question Type,Question Title,Question Description,Question Duration,Question Score,Question Max Score,Question Options,Question Response
do_1130934466492252161819,Test Course,1.3093449510953E+017,Batch1,f703de4e-d47a-4adb-856c-de122e6a0b32,do_1126980913198940161169,Test Questionset,85b32814c2680581f9447c0b792dc2a3,2020-01-09 05:47:44,do_2129194942597447681595,mcq,Which planet has the most Moons?\n,,3,0,1,"[{'1': '{""text"":""Venus\n""}'}]","[{'1': '{""text"":""Venus\n""}'}, {'2': '{""text"":""Jupiter\n""}'}, {'3': '{""text"":""Mercury\n""}'}, {'4': '{""text"":""None of the above\n""}'}, {'answer': '{""correct"":[""2""]}'}]"
do_1130934466492252161819,Test Course,1.3093449510953E+017,Batch1,587204af-41db-4313-b3ab-cf022d3055c6,do_1126980913198940161169,Test Questionset,85b328331c2680581f9447c0b792dc2a4,2020-01-09 05:47:44,do_2129194942597447681595,mcq,Which planet has the most Moons?\n,,4,1,1,"[{'2': '{""text"":""Jupiter\n""}'}]","[{'1': '{""text"":""Venus\n""}'}, {'2': '{""text"":""Jupiter\n""}'}, {'3': '{""text"":""Mercury\n""}'}, {'4': '{""text"":""None of the above\n""}'}, {'answer': '{""correct"":[""2""]}'}]"
```
