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

<table><thead><tr><th width="80"></th><th width="151">Field Name</th><th width="74"> Type</th><th width="125">Table Name</th><th>Description</th></tr></thead><tbody><tr><td><br><br></td><td></td><td></td><td></td><td></td></tr><tr><td>1</td><td><strong>Block Name</strong></td><td>String</td><td><p>USER - get locationids from USER.profilelocation[*].id</p><p>LOCATION - LOCATION.name</p></td><td>User’s Block Name.<br>USER.profilelocation.{id}=LOCATION.id and LOCATION.type='block' and fetch the { name } as block_name</td></tr><tr><td>2</td><td>Board</td><td>String</td><td>USER.framework.{ board }</td><td>User’s board<br>Assumption: It is single valued</td></tr><tr><td>3</td><td><strong>Cluster Name</strong></td><td>String</td><td><p>USER - get locationids from USER.profilelocation[*].id</p><p>LOCATION - LOCATION.name</p></td><td>User’s Cluster Name.<br>USER.profilelocation.{id}=LOCATION.id and LOCATION.type='cluster' and fetch the { name } as cluster_name</td></tr><tr><td>4</td><td><strong>District Name</strong></td><td>String</td><td><p>USER - get locationids from USER.profilelocation[*].id</p><p>LOCATION - LOCATION.name</p></td><td>User’s District Name.<br>USER.profilelocation.{id}=LOCATION.id and LOCATION.type='district' and fetch the { name } as district_name</td></tr><tr><td>5</td><td><strong>Email ID</strong></td><td>String</td><td>USER.email</td><td>User mail id in an encrypted format</td></tr><tr><td>6</td><td>First Name</td><td>String</td><td>USER.firstname</td><td>User first name</td></tr><tr><td>7</td><td>framework</td><td>String</td><td>USER.<a href="http://framework.id/">framework.id</a></td><td>User’s framework id<br>Assumption: It is single valued</td></tr><tr><td>8</td><td>Grade</td><td>List[String]</td><td>USER.framework.{ gradeLevel }</td><td>User grades</td></tr><tr><td>9</td><td>Language</td><td>List[String]</td><td>USER.language</td><td>User Language</td></tr><tr><td>10</td><td>Last Name</td><td>String</td><td>USER.lastname</td><td>User Last Name</td></tr><tr><td>11</td><td>Medium</td><td>List[String]</td><td>USER.framework.{ medium }</td><td>User medium</td></tr><tr><td>12</td><td><strong>Mobile Number</strong></td><td>String</td><td>USER.phone</td><td>User phone number in an encrypted format</td></tr><tr><td>13</td><td><strong>Orgname</strong></td><td>String</td><td>ORGANISATION.orgname</td><td>User’s Org Name<br>1. Select { orgname } from ORGANISATION where UserOrg.organisationid = ORG.id</td></tr><tr><td>14</td><td>Rootorgid</td><td>String</td><td>USER.rootorgid</td><td>User root org id (can be used to differentiate between custodian and state user)</td></tr><tr><td>15</td><td><strong>School Name</strong></td><td>String</td><td>ORGANISATION</td><td>User’s School Name.<br>Select externalid from ORGANISATION where ORG.id=USER_ORG.organisationid and orgtype=school</td></tr><tr><td>16</td><td><strong>School UDISE Code</strong></td><td>String</td><td>ORGANISATION</td><td>User’s School UDISE Code.<br>Select orgname from ORGANISATION where ORG.id=USER_ORG.organisation and orgtype=school</td></tr><tr><td>17</td><td><strong>State Name</strong></td><td>String</td><td><p>USER - get locationids from USER.profilelocation[*].id</p><p>LOCATION - LOCATION.name</p></td><td>User’s State Name.<br>USER.profilelocation.{id}=LOCATION.id and LOCATION.type='state' and fetch the { name } as state_name</td></tr><tr><td>18</td><td>Subject</td><td>List[String]</td><td>USER.framework.{ subject }</td><td>User subjects</td></tr><tr><td>19</td><td>usersignintype</td><td>String</td><td><p>if custodianRootorgId = rootorgid then ‘Self-Signed-In’</p><p>else 'Validated'</p></td><td>User’s sign-in type</td></tr><tr><td>20</td><td><strong>UserSubType</strong></td><td>String</td><td>USER.profileUserType.subType</td><td>User’s Sub Type</td></tr><tr><td>21</td><td><strong>UserType</strong></td><td>String</td><td>USER.profileUserType.type</td><td>User Type</td></tr></tbody></table>

**Properties to be Deleted:**

<table><thead><tr><th width="125">Field Namee</th><th width="84">Type</th><th width="162">Table Name</th><th>Description</th></tr></thead><tbody><tr><td>Externalid</td><td>String</td><td>user_declaration</td><td>The <strong>externalid</strong> will be removed from userinfo-exhaust report</td></tr></tbody></table>

\
