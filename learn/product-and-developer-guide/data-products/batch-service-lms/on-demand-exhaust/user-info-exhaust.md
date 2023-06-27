# User Info Exhaust

User personal info exhaust contains the additional information of the users that have joined the course batch. The information contains personal details such as Email, Phone number etc and all such personal information is provided only with explicit consent by the user. Each record represents user details of the enrolled users in the course batch.Mail id and phone number are encrypted and will be decrypted based on consent

<figure><img src="../../../../../.gitbook/assets/userinfo exhaust.png" alt=""><figcaption></figcaption></figure>

The UserInfoExhaustJob processes the data, applies consent rules, decrypts user information, and generates a user information exhaust report based on the provided user enrolment data and collection batch information.The encryption key is mandatory only for user info exhaust\
\
**Data provider:**\
**cassandra**

1. user redis
2. user\_enrolments
3. user\_consent

**postgres**

1. job\_request table

\
\
**File Structure**

| **Format**                       | **Nomenclature**                                                                     | **Example**                                                  |
| -------------------------------- | ------------------------------------------------------------------------------------ | ------------------------------------------------------------ |
| **CSV zip (Password protected)** | **user-info-exhaust/{request\_id}/**_**\<batch\_id>\_userinfo\_\<updatedDate>.zip**_ | _**do\_1130264512015646721166\_userinfo\_26\_08\_2020.zip**_ |

#### File Contents <a href="#file-contents.1" id="file-contents.1"></a>

<table data-header-hidden><thead><tr><th width="260"></th><th></th><th></th><th></th></tr></thead><tbody><tr><td><strong>Column Label</strong></td><td><strong>Column Type</strong></td><td><strong>Data Type</strong></td><td><strong>Description</strong></td></tr><tr><td>Collection Id</td><td>Static</td><td>String</td><td>Unique Collection Identifier.</td></tr><tr><td>Collection Name</td><td>Static</td><td>String</td><td>Collection Title</td></tr><tr><td>Batch Id</td><td>Static</td><td>String</td><td>Batch Id</td></tr><tr><td>Batch Name</td><td>Static</td><td>String</td><td>Batch Title</td></tr><tr><td>User UUID</td><td>Static</td><td>String</td><td>The system generated unique user ID</td></tr><tr><td>User Name</td><td>Static</td><td>String</td><td>Name of the user</td></tr><tr><td>User Type</td><td>Static</td><td>String</td><td>Type of the user</td></tr><tr><td>User Sub Type</td><td>Static</td><td>String</td><td>Sub Type of the user</td></tr><tr><td>State</td><td>Static</td><td>String</td><td>User declared state for self signed up users. If the user is a org validated user then the state as passed from org SSO or derived from sub-org ID.</td></tr><tr><td>District</td><td>Static</td><td>String</td><td>User declared district for self signed up users. If the user is a org validated user then the district as passed from org SSO or derived from sub-org ID.</td></tr><tr><td>Org Name</td><td>Static</td><td>String</td><td>Name of user org - Custodian for self signed up users and respective org name for org validated users</td></tr><tr><td>Sub-Org Id</td><td>Static</td><td>String</td><td>If user is org validated user then the sub-org ID mapped to this user. If user is self declared user then the user declared sub-org ID.</td></tr><tr><td>Sub-Org Name</td><td>Static</td><td>String</td><td>If user is org validated user then the sub-org name mapped to this user. If user is self declared user then the user declared org/sub-org name.</td></tr><tr><td>Block Name</td><td>Static</td><td>String</td><td>Block name mapped to the user’s org/sub-org id</td></tr><tr><td>Declared Board</td><td>Static</td><td>String</td><td>The board selected by the user during onboarding.</td></tr><tr><td>Declared Org</td><td>Static</td><td>String</td><td>If the user is a self signed up user then this is the value filled by the user in the 'With' part of the self signed up declaration.</td></tr><tr><td>Mobile Number</td><td>Static</td><td>String</td><td>User declared unmasked mobile number</td></tr><tr><td>Email ID</td><td>Static</td><td>String</td><td>User declared unmasked email ID</td></tr><tr><td>Consent Provided</td><td>Static</td><td>String</td><td>Yes/No. Flag to denote whether user has consented to the data sharing.</td></tr><tr><td>Consent Provided Date</td><td>Static</td><td>Date</td><td>Date when the user has consented to share the data</td></tr></tbody></table>

#### Consent Fields <a href="#consent-fields" id="consent-fields"></a>

Following are the fields/columns that will be available in the file only when the user consented for the data sharing.

| Sub-org ID    |
| ------------- |
| Sub-org Name  |
| Block Name    |
| Mobile number |
| Email ID      |

**Sample Data**

```csv
Collection Id,Collection Name,Batch Id,Batch Name,User UUID,User Name,User Type,User Sub Type,State,District,Block,Cluster,Sub-org Id,Sub-org Name,Org Name,Email ID,Mobile Number,Consent Provided,Consent Provided Date
do_21364005085239705611078,Copy of course with merit cert testing,BatchId_01364005724219801651,batch123,91a81041-bbbd-4bd7-947f-09f9e469213c,newtncr,administrator,"hm,asst_als_coordinator,meo",Andhra Pradesh,EAST GODAVARI,ADDATEEGALA,"",28140306106,APTWRS ADDATEEGALA,DR B R OMNI INTERNATIONAL2,newtncr@yopmail.com,"",true,06/10/2022
do_21364005085239705611078,Copy of course with merit cert testing,BatchId_01364005724219801651,batch123,2f97ee31-c190-4adc-8ca1-129f641858e2,bgm,administrator,"chm,meo,diet_lecturer,lib_bdc",Andhra Pradesh,ANANTAPUR,AGALI,"",28226200605,MPPS P.BYADAGERA,Staging Custodian Organization,bgm@yopmail.com,"",true,06/10/2022// Some code
```
