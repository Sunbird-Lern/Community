# Reports

Following are the various exhaust files available and more details can be found [here](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/1666154523/Trackable+Collections+-+Exhaust)

<details>

<summary>Progress Exhaust</summary>

Progress exhaust contains the progress related information for the collection and the nested collections including the assessment related scores of the collection. The nested collections and the assessments within the collection will be transposed as columns and hence the columns for each collection exhaust file would vary

**File Structure - CSV (**_**\<batch\_id>\_progress\_\<updatedDate>.csv**_**)**

**File Contents**

* Collection Id
* Collection Name
* Batch Id
* Batch Name
* User UUID
* User Name
* State
* District
* Enrolment Date
* Completion Date
* Progress
* Certificate Status
* Total Score
* \<nested\_collection\_id> - Progress
* \<nested\_collection\_id> - Level
* \<assessment\_id> - Score

**Sample Data**

```
Collection Id,Collection Name,Batch Id,Batch Name,User UUID,User Name,State,District,Enrolment Date,Completion Date,Progress,Certificate Status,Total Score,do_1130934418641469441813 - Progress,do_1130934418641469441813 - Level,do_1130934445218283521816 - Progress,do_1130934445218283521816 - Level,do_1130934418641469441786-score
do_1130934466492252161819,Test Course,0130934495109529602,Batch1,f703de4e-d47a-4adb-856c-de122e6a0b32,Mathew Pallan,"Kerala","Thrissur",2020-08-25 13:45:54:150+0000,2020-08-27 13:45:54:150+0000,100,"Issued",7,100,"1.1",100,"1.2",7
do_1130934466492252161819,Test Course,0130934495109529602,Batch1,587204af-41db-4313-b3ab-cf022d3055c6,Krishna Jampana,"Andhra Pradesh","Vizag",2020-08-25 02:15:58:691+0000,"",57,"",6,50,"1.1",60,"1.2",6
```

</details>

<details>

<summary>User Personal Info Exhaust</summary>

User personal info exhaust contains the additional information of the users that have joined the collection. The information contains personal details such as Email, Phone number etc and all such personal information is provided only on explicit consent by the user.

**File Structure - CSV zip password protected (**_**\<batch\_id>\_userinfo\_\<updatedDate>.zip**_**)**

**File Contents**

* Collection Id
* Collection Name
* Batch Id
* Batch Name
* User UUID
* User Name
* State
* District
* Org Name
* External ID
* School Id
* School Name
* Block Name
* Declared Board
* Declared Org
* Mobile Number
* Email ID
* Consent Provided
* Consent Provided Date

**Consent Fields**

* External ID
* School ID
* School Name
* Block Name
* Mobile number
* Email ID

**Sample Data**

```
Collection Id,Collection Name,Batch Id,Batch Name,DIKSHA UUID,User Name,State,District,Persona,Org Name,External ID,School Id,School Name,Block Name,Declared Board,Mobile number,Email ID,Consent Provided,Consent Provided Date
do_1130934466492252161819,Test Course,0130934495109529602,Batch1,f703de4e-d47a-4adb-856c-de122e6a0b32,Mathew Pallan,"Kerala","Thrissur","Other",CustROOTOrg10,"","","","","Kerala","","","No",""
do_1130934466492252161819,Test Course,0130934495109529602,Batch1,587204af-41db-4313-b3ab-cf022d3055c6,Krishna Jampana,"Andhra Pradesh","Vizag",Apekx,"apekx1234","1234","Kendriya Vidyalaya","Block1","AP","1234567890","test@test.com","Yes",2020-08-25 13:45:54:150+0000
```

</details>

<details>

<summary>Response Exhaust</summary>

Response exhaust contains the user responses to each question for all question sets in a trackable collection.

**File Structure - CSV (**_**\<batch\_id>\_response\_\<updatedDate>.csv**_**)**

**File Contents**

* Collection Id
* Collection Name
* Batch Id
* Batch Name
* User UUID
* User Name
* QuestionSet Id
* QuestionSet Title
* Attempt Id
* Attempted On
* Question Id
* Question Type
* Question Title
* Question Description
* Question Duration
* Question Score
* Question Max Score
* Question Options
* Question Response

**Consent Fields**

* Question Response

**Sample Data**

```
Collection Id,Collection Name,Batch Id,Batch Name,DIKSHA UUID,User Name,QuestionSet Id,QuestionSet Title,Attempt Id,Attempted On,Question Id,Question Type,Question Title,Question Description,Question Duration,Question Score,Question Max Score,Question Options,Question Response
do_1130934466492252161819,Test Course,0130934495109529602,Batch1,f703de4e-d47a-4adb-856c-de122e6a0b32,Mathew Pallan,do_1126980913198940161169,"Test Questionset",85b32814c2680581f9447c0b792dc2a3,2020-01-09 05:47:44,do_2129194942597447681595,mcq,"Which planet has the most Moons?\n","",3.0,0,1,"[{'1': '{""text"":""Venus\n""}'}]","[{'1': '{""text"":""Venus\n""}'}, {'2': '{""text"":""Jupiter\n""}'}, {'3': '{""text"":""Mercury\n""}'}, {'4': '{""text"":""None of the above\n""}'}, {'answer': '{""correct"":[""2""]}'}]"
do_1130934466492252161819,Test Course,0130934495109529602,Batch1,587204af-41db-4313-b3ab-cf022d3055c6,Krishna Jampana,do_1126980913198940161169,"Test Questionset",85b328331c2680581f9447c0b792dc2a4,2020-01-09 05:47:44,do_2129194942597447681595,mcq,"Which planet has the most Moons?\n","",4.0,1,1,"[{'2': '{""text"":""Jupiter\n""}'}]","[{'1': '{""text"":""Venus\n""}'}, {'2': '{""text"":""Jupiter\n""}'}, {'3': '{""text"":""Mercury\n""}'}, {'4': '{""text"":""None of the above\n""}'}, {'answer': '{""correct"":[""2""]}'}]"
```

</details>
