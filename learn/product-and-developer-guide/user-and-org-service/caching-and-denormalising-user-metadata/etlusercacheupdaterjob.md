# ETLUserCacheUpdaterJob

**Introduction:**

The three exhaust reports depends on the user-metadata information which are generated from user-cache-updater flink job by fetching informations from different core cassandra tables and are stored into the redis cache. There is one time spark ETL script which populates the user data to redis cache after having the . From Release-3.7.0 new fields have been introduced and few field’s formulae have been modified. Following are the modules needs to be touched upon for this ticket:

1. User-cache-updater flink job
2. ETLUserCacheUpdater Job (one time script to populate users)
3. Exhaust Jobs (To introduce new fields)
   1. Progress Exhaust
   2. Userinfo Exhaust\
      \


JIRA Link: [![](https://project-sunbird.atlassian.net/rest/api/2/universal\_avatar/view/type/issuetype/avatar/10315?size=medium)SB-21691: All Reports (course level etc.) to include the new fields being addedRELEASED](https://project-sunbird.atlassian.net/browse/SB-21691)

Reference Wiki Links:\
1\. User Table Changes: [SC-2184 : Data model changes to user schema to store location, persona, subpersona in generic way](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/2110881881)\
2\. Org Table Changes: [SC-2190 : Data model changes to organisation schema to store schools as organisations](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/2260074547)

**Table Schema Changes:**

<details>

<summary>User table schema changes</summary>

CREATE TABLE sunbird.user ( id text PRIMARY KEY, accesscode text, alltncaccepted map\<text, text>, avatar text, channel text, countrycode text, createdby text, createddate text, currentlogintime text, dob text, email text, emailverified boolean, firstname text, flagsvalue int, framework map\<text, frozen\<list>>, gender text, grade list, isdeleted boolean, language list, lastlogintime text, lastname text, location text, locationids list, loginid text, managedby text, maskedemail text, maskedphone text, password text, phone text, phoneverified boolean, prevusedemail text, prevusedphone text, profilesummary text, profilevisibility map\<text, text>, recoveryemail text, recoveryphone text, registryid text, roles list, rootorgid text, status int, subject list, temppassword text, thumbnail text, tncacceptedon timestamp, tncacceptedversion text, updatedby text, updateddate text, userid text, username text, usersubtype text, usertype text, webpages list\<frozen\<map\<text, text>>>, profilelocation text, //new field profileusertype text //new field )

</details>

<details>

<summary>Organisation table schema changes</summary>

CREATE TABLE sunbird.organisation ( id text PRIMARY KEY, addressid text, approvedby text, approveddate text, channel text, communityid text, contactdetail text, createdby text, createddate text, datetime timestamp, description text, email text, externalid text, hashtagid text, homeurl text, imgurl text, isapproved boolean, isdefault boolean, isrootorg boolean, isssoenabled boolean, keys map\<text, frozen\<list>>, locationid text, locationids list, noofmembers int, orgcode text, orgname text, orgtype text, // Update orgtype value as board/school/contentorg orgtypeid text, parentorgid text, // parent id need to be nullified, to remove suborg association preferredlanguage text, provider text, rootorgid text, slug text, status int, theme text, thumbnail text, updatedby text, updateddate text, istenant boolean, //new field, update isrootorg column value in this field orglocation text //new field )

</details>

&#x20;

|                 | Field Name            |  Type         | Table Name                                                                                   | Description                                                                                                                                |
| --------------- | --------------------- | ------------- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| <p><br><br></p> | ****                  | ****          | ****                                                                                         |                                                                                                                                            |
| 1               | **Block Name**        | String        | <p>USER - get locationids from USER.profilelocation[*].id</p><p>LOCATION - LOCATION.name</p> | <p>User’s Block Name.<br>USER.profilelocation.{id}=LOCATION.id and LOCATION.type='block' and fetch the { name } as block_name</p>          |
| 2               | Board                 | String        | USER.framework.{ board }                                                                     | <p>User’s board<br>Assumption: It is single valued</p>                                                                                     |
| 3               | **Cluster Name**      | String        | <p>USER - get locationids from USER.profilelocation[*].id</p><p>LOCATION - LOCATION.name</p> | <p>User’s Cluster Name.<br>USER.profilelocation.{id}=LOCATION.id and LOCATION.type='cluster' and fetch the { name } as cluster_name</p>    |
| 4               | **District Name**     | String        | <p>USER - get locationids from USER.profilelocation[*].id</p><p>LOCATION - LOCATION.name</p> | <p>User’s District Name.<br>USER.profilelocation.{id}=LOCATION.id and LOCATION.type='district' and fetch the { name } as district_name</p> |
| 5               | **Email ID**          | String        | USER.email                                                                                   | User mail id in an encrypted format                                                                                                        |
| 6               | First Name            | String        | USER.firstname                                                                               | User first name                                                                                                                            |
| 7               | framework             | String        | USER.[framework.id](http://framework.id/)                                                    | <p>User’s framework id<br>Assumption: It is single valued</p>                                                                              |
| 8               | Grade                 | List\[String] | USER.framework.{ gradeLevel }                                                                | User grades                                                                                                                                |
| 9               | Language              | List\[String] | USER.language                                                                                | User Language                                                                                                                              |
| 10              | Last Name             | String        | USER.lastname                                                                                | User Last Name                                                                                                                             |
| 11              | Medium                | List\[String] | USER.framework.{ medium }                                                                    | User medium                                                                                                                                |
| 12              | **Mobile Number**     | String        | USER.phone                                                                                   | User phone number in an encrypted format                                                                                                   |
| 13              | **Orgname**           | String        | ORGANISATION.orgname                                                                         | <p>User’s Org Name<br>1. Select { orgname } from ORGANISATION where UserOrg.organisationid = ORG.id</p>                                    |
| 14              | Rootorgid             | String        | USER.rootorgid                                                                               | User root org id (can be used to differentiate between custodian and state user)                                                           |
| 15              | **School Name**       | String        | ORGANISATION                                                                                 | <p>User’s School Name.<br>Select externalid from ORGANISATION where ORG.id=USER_ORG.organisationid and orgtype=school</p>                  |
| 16              | **School UDISE Code** | String        | ORGANISATION                                                                                 | <p>User’s School UDISE Code.<br>Select orgname from ORGANISATION where ORG.id=USER_ORG.organisation and orgtype=school</p>                 |
| 17              | **State Name**        | String        | <p>USER - get locationids from USER.profilelocation[*].id</p><p>LOCATION - LOCATION.name</p> | <p>User’s State Name.<br>USER.profilelocation.{id}=LOCATION.id and LOCATION.type='state' and fetch the { name } as state_name</p>          |
| 18              | Subject               | List\[String] | USER.framework.{ subject }                                                                   | User subjects                                                                                                                              |
| 19              | usersignintype        | String        | <p>if custodianRootorgId = rootorgid then ‘Self-Signed-In’</p><p>else 'Validated'</p>        | User’s sign-in type                                                                                                                        |
| 20              | **UserSubType**       | String        | USER.profileUserType.subType                                                                 | User’s Sub Type                                                                                                                            |
| 21              | **UserType**          | String        | USER.profileUserType.type                                                                    | User Type                                                                                                                                  |

**Properties to be Deleted:**

| Field Namee | Type   | Table Name        | Description                                                     |
| ----------- | ------ | ----------------- | --------------------------------------------------------------- |
| Externalid  | String | user\_declaration | The **externalid** will be removed from userinfo-exhaust report |

\
