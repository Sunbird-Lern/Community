# Reports

Following are the various exhaust files available and more details can be found [here](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/1666154523/Trackable+Collections+-+Exhaust)\
\
**Content creator** (Allowed to create course and batch for their own course.)

**Creator + Course Mentor** (Will be allowed to create a open batch only if the course is created by themselves.).

Note: **Course mentor** (Role alone will not be able to create the batch, instead he can be added as one of the show watcher for the Open batches created by creator)\


<details>

<summary>Progress Exhaust</summary>

Progress exhaust contains the progress related information for the collection and the nested collections including the assessment related scores of the collection. The nested collections and the assessments within the collection will be transposed as columns and hence the columns for each collection exhaust file would vary

**File Structure - CSV (**_**\<batch\_id>\_progress\_\<updatedDate>.csv**_**)**

**File Contents**

* Collection Id&#x20;
* Collection Name&#x20;
* Batch Id&#x20;
* Batch Name&#x20;
* User UUID&#x20;
* State&#x20;
* District&#x20;
* Org Name&#x20;
* School Id&#x20;
* School Name&#x20;
* Block Name&#x20;
* Cluster Name&#x20;
* User Type&#x20;
* User Sub Type&#x20;
* Declared Board&#x20;
* Enrolment Date&#x20;
* Completion Date&#x20;
* Certificate Status
* Progress
* Total Score
* \<nested\_collection\_id> - Progress
* \<nested\_collection\_id> - Level
* \<assessment\_id> - Score

**Sample Data**

```
Collection Id,Collection Name,Batch Id,Batch Name,User UUID,State,District,Org Name,School Id,School Name,Block Name,Cluster Name,User Type,User Sub Type,Declared Board,Enrolment Date,Completion Date,Certificate Status,Progress,Total Score,do_21337188080177971211 - Score,do_2133470331565588481240 - Score
do_21364005085239705611078,Copy of course with merit cert testing,BatchId_01364005724219801651,batch123,91a81041-bbbd-4bd7-947f-09f9e469213c,Andhra Pradesh,EAST GODAVARI,DR B R OMNI INTERNATIONAL2,28140306106,APTWRS ADDATEEGALA,ADDATEEGALA,"",administrator,"hm,asst_als_coordinator,meo",State (Tamil Nadu),06/10/2022,06/10/2022,Issued,100,67%,80%,50%
do_21364005085239705611078,Copy of course with merit cert testing,BatchId_01364005724219801651,batch123,5d0262be-bab5-4764-9c3e-82c3c433cd9d,Andhra Pradesh,ANANTAPUR,Staging Custodian Organization,"","","","",teacher,"",State (Uttarakhand),06/10/2022,06/10/2022,Issued,100,89%,100%,75%
do_21364005085239705611078,Copy of course with merit cert testing,BatchId_01364005724219801651,batch123,2f97ee31-c190-4adc-8ca1-129f641858e2,Andhra Pradesh,ANANTAPUR,Staging Custodian Organization,28226200605,MPPS P.BYADAGERA,AGALI,"",administrator,"chm,meo,diet_lecturer,lib_bdc",State (Tamil Nadu),06/10/2022,06/10/2022,Issued,100,89%,100%,75%
do_21364005085239705611078,Copy of course with merit cert testing,BatchId_01364005724219801651,batch123,b225fe80-eeed-4cd4-ad90-5cdcdda73ace,Telangana,JANGAON,Staging Custodian Organization,"","","","",administrator,"",CBSE,06/10/2022,"","",0,"","",""
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
* User Type&#x20;
* User Sub Type&#x20;
* Block&#x20;
* Cluster

**Consent Fields**

* School ID
* School Name
* Block Name
* Mobile number
* Email ID

**Sample Data**

```
Collection Id,Collection Name,Batch Id,Batch Name,User UUID,User Name,User Type,User Sub Type,State,District,Block,Cluster,School Id,School Name,Org Name,Email ID,Mobile Number,Consent Provided,Consent Provided Date
do_21364005085239705611078,Copy of course with merit cert testing,BatchId_01364005724219801651,batch123,91a81041-bbbd-4bd7-947f-09f9e469213c,newtncr,administrator,"hm,asst_als_coordinator,meo",Andhra Pradesh,EAST GODAVARI,ADDATEEGALA,"",28140306106,APTWRS ADDATEEGALA,DR B R OMNI INTERNATIONAL2,newtncr@yopmail.com,"",true,06/10/2022
do_21364005085239705611078,Copy of course with merit cert testing,BatchId_01364005724219801651,batch123,2f97ee31-c190-4adc-8ca1-129f641858e2,bgm,administrator,"chm,meo,diet_lecturer,lib_bdc",Andhra Pradesh,ANANTAPUR,AGALI,"",28226200605,MPPS P.BYADAGERA,Staging Custodian Organization,bgm@yopmail.com,"",true,06/10/2022
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

<!---->

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
Collection Id,Collection Name,Batch Id,Batch Name,DIKSHA UUID,QuestionSet Id,QuestionSet Title,Attempt Id,Attempted On,Question Id,Question Type,Question Title,Question Description,Question Duration,Question Score,Question Max Score,Question Options,Question Response
do_1130934466492252161819,Test Course,1.3093449510953E+017,Batch1,f703de4e-d47a-4adb-856c-de122e6a0b32,do_1126980913198940161169,Test Questionset,85b32814c2680581f9447c0b792dc2a3,2020-01-09 05:47:44,do_2129194942597447681595,mcq,Which planet has the most Moons?\n,,3,0,1,"[{'1': '{""text"":""Venus\n""}'}]","[{'1': '{""text"":""Venus\n""}'}, {'2': '{""text"":""Jupiter\n""}'}, {'3': '{""text"":""Mercury\n""}'}, {'4': '{""text"":""None of the above\n""}'}, {'answer': '{""correct"":[""2""]}'}]"
do_1130934466492252161819,Test Course,1.3093449510953E+017,Batch1,587204af-41db-4313-b3ab-cf022d3055c6,do_1126980913198940161169,Test Questionset,85b328331c2680581f9447c0b792dc2a4,2020-01-09 05:47:44,do_2129194942597447681595,mcq,Which planet has the most Moons?\n,,4,1,1,"[{'2': '{""text"":""Jupiter\n""}'}]","[{'1': '{""text"":""Venus\n""}'}, {'2': '{""text"":""Jupiter\n""}'}, {'3': '{""text"":""Mercury\n""}'}, {'4': '{""text"":""None of the above\n""}'}, {'answer': '{""correct"":[""2""]}'}]"
```

</details>
