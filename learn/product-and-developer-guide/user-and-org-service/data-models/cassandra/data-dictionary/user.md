# User

### s**unbird.user (PRIMARY KEY: id)**

Table used for storing user profile details

<table><thead><tr><th width="183.33333333333331">Column Name</th><th width="132">Data Type</th><th>Description</th><th>Sample Value</th></tr></thead><tbody><tr><td>id</td><td>text</td><td>UUID</td><td>9b774c71-6034-4de7-aa38-5382fc673b14</td></tr><tr><td>alltncaccepted</td><td>map&#x3C;text, text></td><td>Terms and Conditions that the user has accepted. 1) Org Admin TNC if the user has ORG_ADMIN role  2) Report Viewer role TNC if the user has REPORT_VIEWER  role 3)Groups tnc - if the user has  groups.</td><td>"allTncAccepted": { "reportViewerTnc": { "tncAcceptedOn": "2023-01-02 05:25:21:586+0000", "version": "4.0.0" }, "orgAdminTnc": { "tncAcceptedOn": "2020-11-26 08:17:59:547+0000", "version": "3.5.0" }, "groupsTnc": { "tncAcceptedOn": "2020-12-03 09:14:47:437+0000", "version": "3.5.0" } }</td></tr><tr><td>channel</td><td>text</td><td>Tenant Organisation channel value</td><td>TN, AP</td></tr><tr><td>countrycode</td><td>text</td><td>Country code of the user</td><td>+91</td></tr><tr><td>createdby</td><td>text</td><td>uuid of the created user, null in case user has signed up by himself</td><td>8c774c71-6034-4de7-aa38-5382fc673b14</td></tr><tr><td>createddate</td><td>text</td><td>Date on which the user was created</td><td>2020-09-28 15:47:15:919+0000</td></tr><tr><td>dob</td><td>text</td><td>Date of Birth of the user. Only year is provided by the user. Month and date(12-31) is appended to it by the system</td><td>1987-12-31</td></tr><tr><td>email</td><td>text</td><td>Email id of the user in encrypted format</td><td>testdoc@yopmail.com</td></tr><tr><td><del>emailverified</del></td><td>boolean</td><td>Email is verified or not using OTP. This flag is not used anymore</td><td>true or false</td></tr><tr><td>firstname</td><td>text</td><td>First name of the user</td><td></td></tr><tr><td>flagsvalue</td><td>int</td><td>Value will by 4 , if the user is uploaded by the tenant or registered through tenant login page. ( Earlier there were different values updated as per the user email verified, phone verified and tenant verified. But currently only tenant verification is stored.)</td><td>4 </td></tr><tr><td>framework</td><td>map&#x3C;text, frozen&#x3C;list&#x3C;text>>></td><td>User chosen framework</td><td>{ "board": ["State (Tamil Nadu)"], "gradeLevel": ["Class 1"], "id": ["tn_k-12_5"], "medium": ["English"], "subject": ["Mathematics"] }</td></tr><tr><td>isdeleted</td><td>boolean</td><td>User is soft deleted or not. Scenarios: 1) Merge one user to another, then the first one gets deleted. 2) User Block will update the is_deleted flag to true and status to 0 (inactive)</td><td>true or false</td></tr><tr><td>lastname</td><td>text</td><td>Last Name of the user</td><td></td></tr><tr><td><del>locationids</del></td><td>list&#x3C;text></td><td>Not Used</td><td></td></tr><tr><td>l<del>oginid</del></td><td>text</td><td>Not Used</td><td></td></tr><tr><td>managedby</td><td>text</td><td>Logged in user/Parent uuid of the managed user. If managedby column has value( parent uuid), that means this row of record is  child user's and email and phone number will be blank for this user.</td><td>7c784c71-9034-4de7-aa38-5382fc673b14</td></tr><tr><td>maskedemail</td><td>text</td><td>Masked email id value </td><td>te*****@yopmail.com</td></tr><tr><td>maskedphone</td><td>text</td><td>Masked phone number value</td><td>98******09</td></tr><tr><td>phone</td><td>text</td><td>Phone number of the user in encrypted format</td><td></td></tr><tr><td><del>phoneverified</del></td><td>boolean</td><td>Email is verified or not using OTP. This flag is not used anymore</td><td></td></tr><tr><td>prevusedemail</td><td>text</td><td>Previously used email id in encrypted format</td><td></td></tr><tr><td>prevusedphone</td><td>text</td><td>Previously used phone number in encrypted format</td><td></td></tr><tr><td>profilelocation</td><td>text</td><td>Used to store location data of the user from release-3.9.0. This stores the location types and code from sunbird.location table. This is  validated against the configuration of location types in properties file "sunbird_valid_location_types" and also to ED form api configuration "profileconfig_v2"</td><td><p>"profileLocation": [ { "code": "32", "type": "state" }, { "code": "3210", "type": "district" },</p><p>{"code": "321001", "type": "block"} ,{"code": "32100123", "type": "cluster"]</p></td></tr><tr><td><del>profileusertype</del></td><td>text</td><td>Not Used from release-4.4.0.This field was in use from release-3.9.0 to 4.4.0.</td><td>{ "type": "administrator", "subType":"hm" }</td></tr><tr><td>profileusertypes</td><td>text</td><td>Used to store user type (role) and subusertype (subrole) from release-4.4.0. This is  validated against the ED form api configuration "profileconfig_v2"</td><td>"profileUserTypes": [ { "type": "administrator", "subType":"hm" }, { "type": "administrator", "subType":"deo" }],</td></tr><tr><td>recoveryemail</td><td>text</td><td>Recovery email of the user in encrypted form</td><td></td></tr><tr><td>recoveryphone</td><td>text</td><td>Recovery phone number of the user in encrypted form</td><td></td></tr><tr><td><del>roles</del></td><td>list&#x3C;text></td><td>Not used</td><td></td></tr><tr><td>rootorgid</td><td>text</td><td>Tenant Org id of the user</td><td>0126796199493140480</td></tr><tr><td>status</td><td>int</td><td>User is active or not. '1' means active, '0' is inactive</td><td>1</td></tr><tr><td>tncacceptedon</td><td>timestamp</td><td>terms and conditions accepted time in long format</td><td>1687933998587</td></tr><tr><td>tncacceptedversion</td><td>text</td><td>Version of the terms and conditions. If any change in terms and conditions it is added with a new version and link is updated in system configuration.</td><td>v13</td></tr><tr><td>updatedby</td><td>text</td><td>UUID of the user who updated the profile. </td><td>7c784c71-9034-4de7-aa38-5382fc673b14</td></tr><tr><td>updateddate</td><td>text</td><td>Date in which this table record is updated last.</td><td>2023-06-28 06:34:02:020+0000</td></tr><tr><td>userid</td><td>text</td><td>UUID of the user, same as the id column value</td><td>9b774c71-6034-4de7-aa38-5382fc673b14</td></tr><tr><td>username</td><td>text</td><td>Username of the user, this can be given via create api or if not given its automatically created by appending firstname and random text.</td><td></td></tr><tr><td><del>usersubtype</del></td><td>text</td><td>Not used</td><td></td></tr><tr><td><del>usertype</del></td><td>text</td><td>Not used</td><td></td></tr></tbody></table>

### sunbird.user\_lookup \[PRIMARY KEY (type, value)]

<table><thead><tr><th width="163.33333333333331">Column Name</th><th width="118">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td>text</td><td></td></tr><tr><td>value</td><td>text</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr></tbody></table>

### sunbird.usr\_external\_identity \[PRIMARY KEY (provider, idtype, externalid)

<table><thead><tr><th width="186">Column Name</th><th width="125.33333333333331">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>provider</td><td>text</td><td></td></tr><tr><td>idtype</td><td>text</td><td></td></tr><tr><td>externalid</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>lastupdatedby</td><td>text</td><td></td></tr><tr><td>lastupdatedon</td><td>timestamp</td><td></td></tr><tr><td>originalexternalid</td><td>text</td><td></td></tr><tr><td>originalidtype</td><td>text</td><td></td></tr><tr><td>originalprovider</td><td>text</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr></tbody></table>

### sunbird.user\_organisation \[PRIMARY KEY (userid, organisationid)]

<table><thead><tr><th width="172.33333333333331">Column Name</th><th width="125">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>userid</td><td>text</td><td></td></tr><tr><td>organisationid</td><td>text</td><td></td></tr><tr><td>addedby</td><td>text</td><td></td></tr><tr><td>addedbyname</td><td>text</td><td></td></tr><tr><td>approvaldate</td><td>text</td><td></td></tr><tr><td>approvedby</td><td>text</td><td></td></tr><tr><td>associationtype</td><td>int</td><td></td></tr><tr><td>hashtagid</td><td>text</td><td></td></tr><tr><td>id</td><td>text</td><td></td></tr><tr><td>isapproved</td><td>boolean</td><td></td></tr><tr><td>isdeleted</td><td>boolean</td><td></td></tr><tr><td>isrejected</td><td>boolean</td><td></td></tr><tr><td>orgjoindate</td><td>text</td><td></td></tr><tr><td>orgleftdate</td><td>text</td><td></td></tr><tr><td>position</td><td>text</td><td></td></tr><tr><td>roles</td><td>list&#x3C;text></td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updateddate</td><td>text</td><td></td></tr></tbody></table>
