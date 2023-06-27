---
description: List of tables in Cassandra database used in user-org service
---

# User-Org Service

### Sunbird.user (**PRIMARY KEY: id)**

Table used for storing user profile details

<table><thead><tr><th width="201.33333333333331">Column Name</th><th width="185">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>alltncaccepted</td><td>map&#x3C;text, text></td><td></td></tr><tr><td>channel</td><td>text</td><td></td></tr><tr><td>countrycode</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createddate</td><td>text</td><td></td></tr><tr><td>dob</td><td>text</td><td></td></tr><tr><td>email</td><td>text</td><td></td></tr><tr><td>emailverified</td><td>boolean</td><td></td></tr><tr><td>firstname</td><td>text</td><td></td></tr><tr><td>flagsvalue</td><td>int</td><td></td></tr><tr><td>framework</td><td>map&#x3C;text, frozen&#x3C;list&#x3C;text>>></td><td></td></tr><tr><td>isdeleted</td><td>boolean</td><td></td></tr><tr><td>lastname</td><td>text</td><td></td></tr><tr><td>locationids</td><td>list&#x3C;text></td><td></td></tr><tr><td>loginid</td><td>text</td><td></td></tr><tr><td>managedby</td><td>text</td><td></td></tr><tr><td>maskedemail</td><td>text</td><td></td></tr><tr><td>maskedphone</td><td>text</td><td></td></tr><tr><td>phone</td><td>text</td><td></td></tr><tr><td>phoneverified</td><td>boolean</td><td></td></tr><tr><td>prevusedemail</td><td>text</td><td></td></tr><tr><td>prevusedphone</td><td>text</td><td></td></tr><tr><td>profilelocation</td><td>text</td><td></td></tr><tr><td>profileusertype</td><td>text</td><td></td></tr><tr><td>profileusertypes</td><td>text</td><td></td></tr><tr><td>recoveryemail</td><td>text</td><td></td></tr><tr><td>recoveryphone</td><td>text</td><td></td></tr><tr><td>roles</td><td>list&#x3C;text></td><td></td></tr><tr><td>rootorgid</td><td>text</td><td></td></tr><tr><td>status</td><td>int</td><td></td></tr><tr><td>tncacceptedon</td><td>timestamp</td><td></td></tr><tr><td>tncacceptedversion</td><td>text</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updateddate</td><td>text</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr><tr><td>username</td><td>text</td><td></td></tr><tr><td>usersubtype</td><td>text</td><td></td></tr><tr><td>usertype</td><td>text</td><td></td></tr></tbody></table>



### Sunbird.organisation (**PRIMARY KEY: id)**

Table used for storing Tenants/Organisations and Sub-Organisations



<table><thead><tr><th width="177.33333333333331">Column Name</th><th width="187">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>channel</td><td>text</td><td></td></tr><tr><td>contactdetail</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createddate</td><td>text</td><td></td></tr><tr><td>description</td><td>text</td><td></td></tr><tr><td>email</td><td>text</td><td></td></tr><tr><td>externalid</td><td>text</td><td></td></tr><tr><td>hashtagid</td><td>text</td><td></td></tr><tr><td>isrootorg</td><td>boolean</td><td></td></tr><tr><td>isssoenabled</td><td>boolean</td><td></td></tr><tr><td>istenant</td><td>boolean</td><td></td></tr><tr><td>keys</td><td>map&#x3C;text, frozen&#x3C;list&#x3C;text>>></td><td></td></tr><tr><td>locationids</td><td>list&#x3C;text></td><td></td></tr><tr><td>organisationtype</td><td>int</td><td></td></tr><tr><td>orglocation</td><td>text</td><td></td></tr><tr><td>orgname</td><td>text</td><td></td></tr><tr><td>provider</td><td>text</td><td></td></tr><tr><td>rootorgid</td><td>text</td><td></td></tr><tr><td>slug</td><td>text</td><td></td></tr><tr><td>status</td><td>int</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updateddate</td><td>text</td><td></td></tr></tbody></table>



### Sunbird.system\_settings (**PRIMARY KEY: id)**

Table used for storing system level configuration values used by LERN and other sunbird BBs.

<table><thead><tr><th width="159.33333333333331">Column Name</th><th width="114">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>field</td><td>text</td><td></td></tr><tr><td>value</td><td>text</td><td></td></tr></tbody></table>



### Sunbird.location (**PRIMARY KEY: id)**

Table is used for storing locations

<table><thead><tr><th width="159.33333333333331">Column Name</th><th width="113">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>code</td><td>text</td><td></td></tr><tr><td>name</td><td>text</td><td></td></tr><tr><td>parentid</td><td>text</td><td></td></tr><tr><td>type</td><td>text</td><td></td></tr></tbody></table>



### Sunbird.action\_group (**PRIMARY KEY: id)**



<table><thead><tr><th width="167.33333333333331">Column Name</th><th width="111">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>actionid</td><td>text</td><td></td></tr><tr><td>groupname</td><td>text</td><td></td></tr></tbody></table>



### Sunbird.address (**PRIMARY KEY: id)**



<table><thead><tr><th width="160.33333333333331">Column Name</th><th width="118">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>addressline1</td><td>text</td><td></td></tr><tr><td>addressline2</td><td>text</td><td></td></tr><tr><td>addtype</td><td>text</td><td></td></tr><tr><td>city</td><td>text</td><td></td></tr><tr><td>country</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createddate</td><td>text</td><td></td></tr><tr><td>isdeleted</td><td>boolean</td><td></td></tr><tr><td>state</td><td>text</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updateddate</td><td>text</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr><tr><td>zipcode</td><td>text</td><td></td></tr></tbody></table>



### Sunbird.bulk\_upload\_process (**PRIMARY KEY: id)**



<table><thead><tr><th width="177.33333333333331">Column Name</th><th width="157">Data Type</th><th>Decription</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>data</td><td>text</td><td></td></tr><tr><td>failureresult</td><td>text</td><td></td></tr><tr><td>lastupdatedon</td><td>timestamp</td><td></td></tr><tr><td>objecttype</td><td>text</td><td></td></tr><tr><td>organisationid</td><td>text</td><td></td></tr><tr><td>processendtime</td><td>text</td><td></td></tr><tr><td>processstarttime</td><td>text</td><td></td></tr><tr><td>retrycount</td><td>int</td><td></td></tr><tr><td>status</td><td>int</td><td></td></tr><tr><td>storagedetails</td><td>text</td><td></td></tr><tr><td>successresult</td><td>text</td><td></td></tr><tr><td>taskcount</td><td>int</td><td></td></tr><tr><td>telemetrycontext</td><td>map&#x3C;text, text></td><td></td></tr><tr><td>uploadedby</td><td>text</td><td></td></tr><tr><td>uploadeddate</td><td>text</td><td></td></tr></tbody></table>



### Sunbird.bulk\_upload\_process\_task (PRIMARY KEY: processid, sequenceid)



<table><thead><tr><th width="167.33333333333331">Column Name</th><th width="117">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>processid</td><td>text</td><td></td></tr><tr><td>sequenceid</td><td>int</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>data</td><td>text</td><td></td></tr><tr><td>failureresult</td><td>text</td><td></td></tr><tr><td>iterationid</td><td>int</td><td></td></tr><tr><td>lastupdatedon</td><td>timestamp</td><td></td></tr><tr><td>status</td><td>int</td><td></td></tr><tr><td>successresult</td><td>text</td><td></td></tr></tbody></table>



### sunbird.cassandra\_migration\_version (**PRIMARY KEY: version)**



<table><thead><tr><th width="180.33333333333331">Column Name</th><th width="122">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>version</td><td>text</td><td></td></tr><tr><td>checksum</td><td>int</td><td></td></tr><tr><td>description</td><td>text</td><td></td></tr><tr><td>execution_time</td><td>int</td><td></td></tr><tr><td>installed_by</td><td>text</td><td></td></tr><tr><td>installed_on</td><td>timestamp</td><td></td></tr><tr><td>installed_rank</td><td>int</td><td></td></tr><tr><td>script</td><td>text</td><td></td></tr><tr><td>success</td><td>boolean</td><td></td></tr><tr><td>type</td><td>text</td><td></td></tr><tr><td>version_rank</td><td>int</td><td></td></tr></tbody></table>



### sunbird.cassandra\_migration\_version\_counts (PRIMARY KEY: name)



<table><thead><tr><th width="167.33333333333331">Column Name</th><th width="120">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>name</td><td>text</td><td></td></tr><tr><td>count</td><td>counter</td><td></td></tr></tbody></table>



### sunbird.cert\_registry (PRIMARY KEY: id)



<table><thead><tr><th width="162.33333333333331">Column Name</th><th width="124">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>accesscode</td><td>text</td><td></td></tr><tr><td>createdat</td><td>timestamp</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>data</td><td>text</td><td></td></tr><tr><td>isrevoked</td><td>boolean</td><td></td></tr><tr><td>jsonurl</td><td>text</td><td></td></tr><tr><td>pdfurl</td><td>text</td><td></td></tr><tr><td>reason</td><td>text</td><td></td></tr><tr><td>recipient</td><td>text</td><td></td></tr><tr><td>related</td><td>text</td><td></td></tr><tr><td>updatedat</td><td>timestamp</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr></tbody></table>



### sunbird.config\_path\_audit (PRIMARY KEY: ((id, cloud\_store\_type), created\_date))



<table><thead><tr><th width="219.33333333333331">Column Name</th><th width="125">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>cloud_store_type</td><td>text</td><td></td></tr><tr><td>created_date</td><td>bigint</td><td></td></tr><tr><td>cloud_store_account</td><td>text</td><td></td></tr><tr><td>cloud_store_container</td><td>text</td><td></td></tr><tr><td>cloud_store_path</td><td>text</td><td></td></tr><tr><td>version</td><td>bigint</td><td></td></tr></tbody></table>



### sunbird.email\_template (PRIMARY KEY: name)



<table><thead><tr><th width="174.33333333333331">Column Name</th><th width="147">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>name</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>lastupdatedby</td><td>text</td><td></td></tr><tr><td>lastupdatedon</td><td>timestamp</td><td></td></tr><tr><td>template</td><td>text</td><td></td></tr></tbody></table>



### sunbird.geo\_location (PRIMARY KEY: id)



<table><thead><tr><th width="159.33333333333331">Column Name</th><th width="114">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createddate</td><td>text</td><td></td></tr><tr><td>location</td><td>text</td><td></td></tr><tr><td>rootorgid</td><td>text</td><td></td></tr><tr><td>topic</td><td>text</td><td></td></tr><tr><td>type</td><td>text</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updateddate</td><td>text</td><td></td></tr><tr><td>usercount</td><td>int</td><td></td></tr><tr><td>usercountttl</td><td>text</td><td></td></tr></tbody></table>



### sunbird.master\_action (PRIMARY KEY: id)



<table><thead><tr><th width="160.33333333333331">Column Name</th><th width="111">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>name</td><td>text</td><td></td></tr></tbody></table>



### sunbird.media\_type



<table><thead><tr><th width="160.33333333333331">Column Name</th><th width="111">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>name</td><td>text</td><td></td></tr></tbody></table>



### sunbird.org\_external\_identity \[PRIMARY KEY: (provider, externalid)]



<table><thead><tr><th width="162.33333333333331">Column Name</th><th width="117">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>provider</td><td>text</td><td></td></tr><tr><td>externalid</td><td>text</td><td></td></tr><tr><td>orgid</td><td>text</td><td></td></tr></tbody></table>



### sunbird.otp \[PRIMARY KEY: (type, key)]



<table><thead><tr><th width="171.33333333333331">Column Name</th><th width="117">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td>text</td><td></td></tr><tr><td>key</td><td>text</td><td></td></tr><tr><td>attemptedcount</td><td>int</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>otp</td><td>text</td><td></td></tr></tbody></table>



### sunbird.page\_management \[PRIMARY KEY: id]



<table><thead><tr><th width="165.33333333333331">Column Name</th><th width="118">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>appmap</td><td>text</td><td></td></tr><tr><td>created_date</td><td>timestamp</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createddate</td><td>text</td><td></td></tr><tr><td>name</td><td>text</td><td></td></tr><tr><td>organisationid</td><td>text</td><td></td></tr><tr><td>portalmap</td><td>text</td><td></td></tr><tr><td>updated_date</td><td>timestamp</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updateddate</td><td>text</td><td></td></tr></tbody></table>



### sunbird.page\_section \[PRIMARY KEY: id]



<table><thead><tr><th width="171.33333333333331">Column Name</th><th width="118">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>alt</td><td>text</td><td></td></tr><tr><td>created_date</td><td>timestamp</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createddate</td><td>text</td><td></td></tr><tr><td>datasource</td><td>text</td><td></td></tr><tr><td>description</td><td>text</td><td></td></tr><tr><td>display</td><td>text</td><td></td></tr><tr><td>dynamicfilters</td><td>text</td><td></td></tr><tr><td>imgurl</td><td>text</td><td></td></tr><tr><td>name</td><td>text</td><td></td></tr><tr><td>searchquery</td><td>text</td><td></td></tr><tr><td>sectiondatatype</td><td>text</td><td></td></tr><tr><td>status</td><td>int</td><td></td></tr><tr><td>updated_date</td><td>timestamp</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updateddate</td><td>text</td><td></td></tr></tbody></table>

















