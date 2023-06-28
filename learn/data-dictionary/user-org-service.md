---
description: List of tables in Cassandra database used in User-Org service
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



### sunbird.rate\_limit \[PRIMARY KEY: (key, unit)]



<table><thead><tr><th width="159.33333333333331">Column Name</th><th width="112">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>key</td><td>text</td><td></td></tr><tr><td>unit</td><td>text</td><td></td></tr><tr><td>count</td><td>int</td><td></td></tr><tr><td>rate</td><td>int</td><td></td></tr></tbody></table>



### sunbird.report\_tracking \[PRIMARY KEY: id]



<table><thead><tr><th width="156.33333333333331">Column Name</th><th width="119">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>createddate</td><td>text</td><td></td></tr><tr><td>data</td><td>text</td><td></td></tr><tr><td>email</td><td>text</td><td></td></tr><tr><td>fileurl</td><td>text</td><td></td></tr><tr><td>firstname</td><td>text</td><td></td></tr><tr><td>format</td><td>text</td><td></td></tr><tr><td>period</td><td>text</td><td></td></tr><tr><td>resourceid</td><td>text</td><td></td></tr><tr><td>resourcename</td><td>text</td><td></td></tr><tr><td>status</td><td>int</td><td></td></tr><tr><td>trycount</td><td>int</td><td></td></tr><tr><td>type</td><td>text</td><td></td></tr><tr><td>updateddate</td><td>text</td><td></td></tr><tr><td>uploadeddate</td><td>text</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr><tr><td></td><td></td><td></td></tr></tbody></table>



### sunbird.role \[PRIMARY KEY: id]



<table><thead><tr><th width="158.33333333333331">Column Name</th><th width="115">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>name</td><td>text</td><td></td></tr><tr><td>rolegroupid</td><td>list&#x3C;text></td><td></td></tr><tr><td>status</td><td>int</td><td></td></tr></tbody></table>



### sunbird.role\_group \[PRIMARY KEY: id]



<table><thead><tr><th width="158.33333333333331">Column Name</th><th width="115">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>name</td><td>text</td><td></td></tr><tr><td>url_action_ids</td><td>list&#x3C;text></td><td></td></tr></tbody></table>



### sunbird.shadow\_user \[PRIMARY KEY (channel, userextid)]



<table><thead><tr><th width="170.33333333333331">Column Name</th><th width="113">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>channel</td><td></td><td></td></tr><tr><td>userextid</td><td></td><td></td></tr><tr><td>addedby</td><td></td><td></td></tr><tr><td>attemptedcount</td><td>int</td><td></td></tr><tr><td>claimedon</td><td>timestamp</td><td></td></tr><tr><td>claimstatus</td><td>int</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>email</td><td></td><td></td></tr><tr><td>name</td><td></td><td></td></tr><tr><td>orgextid</td><td></td><td></td></tr><tr><td>phone</td><td></td><td></td></tr><tr><td>processid</td><td></td><td></td></tr><tr><td>updatedon</td><td>timestamp</td><td></td></tr><tr><td>userid</td><td></td><td></td></tr><tr><td>userids</td><td>list&#x3C;text></td><td></td></tr><tr><td>userstatus</td><td>int</td><td></td></tr></tbody></table>



### sunbird.tenant\_preference \[PRIMARY KEY: id]&#x20;



<table><thead><tr><th width="170.33333333333331">Column Name</th><th width="111">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>data</td><td>text</td><td></td></tr><tr><td>key</td><td>text</td><td></td></tr><tr><td>orgid</td><td>text</td><td></td></tr><tr><td>role</td><td>text</td><td></td></tr><tr><td>tenantname</td><td>text</td><td></td></tr></tbody></table>



### sunbird.tenant\_preference\_v2 \[PRIMARY KEY (orgid, key)]



<table><thead><tr><th width="165.33333333333331">Column Name</th><th width="116">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>orgid</td><td>text</td><td></td></tr><tr><td>key</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>data</td><td>text</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updatedon</td><td>timestamp</td><td></td></tr></tbody></table>



### sunbird.url\_action \[PRIMARY KEY: id]



<table><thead><tr><th width="158.33333333333331">Column Name</th><th width="115">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>name</td><td>text</td><td></td></tr><tr><td>url</td><td>list&#x3C;text></td><td></td></tr></tbody></table>



### sunbird.user\_action\_role \[PRIMARY KEY: id]



<table><thead><tr><th width="152.33333333333331">Column Name</th><th width="115">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>roleid</td><td>text</td><td></td></tr><tr><td>actiongroupid</td><td>list&#x3C;text></td><td></td></tr></tbody></table>



### sunbird.user\_cert \[PRIMARY KEY: id]



<table><thead><tr><th width="172.33333333333331">Column Name</th><th width="159">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>accesscode</td><td>text</td><td></td></tr><tr><td>createdat</td><td>timestamp</td><td></td></tr><tr><td>isdeleted</td><td>boolean</td><td></td></tr><tr><td>oldid</td><td>text</td><td></td></tr><tr><td>store</td><td>map&#x3C;text, text></td><td></td></tr><tr><td>updatedat</td><td>timestamp</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr></tbody></table>



### sunbird.user\_consent \[PRIMARY KEY (user\_id, consumer\_id, object\_id)]



<table><thead><tr><th width="172.33333333333331">Column Name</th><th width="124">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>user_id</td><td>text</td><td></td></tr><tr><td>consumer_id</td><td>text</td><td></td></tr><tr><td>object_id</td><td>text</td><td></td></tr><tr><td>categories</td><td>list&#x3C;text></td><td></td></tr><tr><td>consent_data</td><td>text</td><td></td></tr><tr><td>consumer_type</td><td>text</td><td></td></tr><tr><td>created_on</td><td>timestamp</td><td></td></tr><tr><td>expiry</td><td>timestamp</td><td></td></tr><tr><td>id</td><td>text</td><td></td></tr><tr><td>last_updated_on</td><td>timestamp</td><td></td></tr><tr><td>object_type</td><td>text</td><td></td></tr><tr><td>status</td><td>text</td><td></td></tr></tbody></table>



### sunbird.user\_declarations \[PRIMARY KEY (userid, orgid, persona)]



<table><thead><tr><th width="169.33333333333331">Column Name</th><th width="160">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>userid</td><td>text</td><td></td></tr><tr><td>orgid</td><td>text</td><td></td></tr><tr><td>persona</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>errortype</td><td>text</td><td></td></tr><tr><td>status</td><td>text</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updatedon</td><td>timestamp</td><td></td></tr><tr><td>userinfo</td><td>map&#x3C;text, text></td><td></td></tr></tbody></table>



### sunbird.user\_feed \[PRIMARY KEY: id]



<table><thead><tr><th width="179.33333333333331">Column Name</th><th width="127">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>category</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>data</td><td>text</td><td></td></tr><tr><td>expireon</td><td>timestamp</td><td></td></tr><tr><td>priority</td><td>int</td><td></td></tr><tr><td>status</td><td>text</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updatedon</td><td>timestamp</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr></tbody></table>



### sunbird.user\_lookup \[PRIMARY KEY (type, value)]



<table><thead><tr><th width="163.33333333333331">Column Name</th><th width="118">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td>text</td><td></td></tr><tr><td>value</td><td>text</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr></tbody></table>



### sunbird.user\_notes \[PRIMARY KEY: id]



<table><thead><tr><th width="166.33333333333331">Column Name</th><th width="126">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>contentid</td><td>text</td><td></td></tr><tr><td>courseid</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createddate</td><td>text</td><td></td></tr><tr><td>isdeleted</td><td>boolean</td><td></td></tr><tr><td>note</td><td>text</td><td></td></tr><tr><td>tags</td><td>list&#x3C;text></td><td></td></tr><tr><td>title</td><td>text</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updateddate</td><td>text</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr></tbody></table>



### sunbird.user\_org \[PRIMARY KEY: id]



<table><thead><tr><th width="170.33333333333331">Column Name</th><th width="115">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>addedby</td><td>text</td><td></td></tr><tr><td>addedbyname</td><td>text</td><td></td></tr><tr><td>approvaldate</td><td>text</td><td></td></tr><tr><td>approvedby</td><td>text</td><td></td></tr><tr><td>hashtagid</td><td>text</td><td></td></tr><tr><td>isapproved</td><td>boolean</td><td></td></tr><tr><td>isdeleted</td><td>boolean</td><td></td></tr><tr><td>isrejected</td><td>boolean</td><td></td></tr><tr><td>organisationid</td><td>text</td><td></td></tr><tr><td>orgjoindate</td><td>text</td><td></td></tr><tr><td>orgleftdate</td><td>text</td><td></td></tr><tr><td>position</td><td>text</td><td></td></tr><tr><td>roles</td><td>list&#x3C;text></td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updateddate</td><td>text</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr></tbody></table>



### sunbird.user\_organisation \[PRIMARY KEY (userid, organisationid)]



<table><thead><tr><th width="172.33333333333331">Column Name</th><th width="125">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>userid</td><td>text</td><td></td></tr><tr><td>organisationid</td><td>text</td><td></td></tr><tr><td>addedby</td><td>text</td><td></td></tr><tr><td>addedbyname</td><td>text</td><td></td></tr><tr><td>approvaldate</td><td>text</td><td></td></tr><tr><td>approvedby</td><td>text</td><td></td></tr><tr><td>associationtype</td><td>int</td><td></td></tr><tr><td>hashtagid</td><td>text</td><td></td></tr><tr><td>id</td><td>text</td><td></td></tr><tr><td>isapproved</td><td>boolean</td><td></td></tr><tr><td>isdeleted</td><td>boolean</td><td></td></tr><tr><td>isrejected</td><td>boolean</td><td></td></tr><tr><td>orgjoindate</td><td>text</td><td></td></tr><tr><td>orgleftdate</td><td>text</td><td></td></tr><tr><td>position</td><td>text</td><td></td></tr><tr><td>roles</td><td>list&#x3C;text></td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updateddate</td><td>text</td><td></td></tr></tbody></table>



### sunbird.user\_roles \[PRIMARY KEY (userid, role)]



<table><thead><tr><th width="161.33333333333331">Column Name</th><th width="124">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>userid</td><td>text</td><td></td></tr><tr><td>role</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createddate</td><td>text</td><td></td></tr><tr><td>scope</td><td>text</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updateddate</td><td>text</td><td></td></tr></tbody></table>



### sunbird.user\_skills \[PRIMARY KEY: id]



<table><thead><tr><th width="211.33333333333331">Column Name</th><th width="161">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>endorsementcount</td><td>int</td><td></td></tr><tr><td>endorserslist</td><td>frozen&#x3C;list&#x3C;frozen&#x3C;map&#x3C;text, text>>>></td><td></td></tr><tr><td>lastupdatedby</td><td>text</td><td></td></tr><tr><td>lastupdatedon</td><td>timestamp</td><td></td></tr><tr><td>skillname</td><td>text</td><td></td></tr><tr><td>skillnametolowercase</td><td>text</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr></tbody></table>



### sunbird.usr\_external\_identity \[PRIMARY KEY (provider, idtype, externalid)]



<table><thead><tr><th width="186">Column Name</th><th width="125.33333333333331">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>provider</td><td>text</td><td></td></tr><tr><td>idtype</td><td>text</td><td></td></tr><tr><td>externalid</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>lastupdatedby</td><td>text</td><td></td></tr><tr><td>lastupdatedon</td><td>timestamp</td><td></td></tr><tr><td>originalexternalid</td><td>text</td><td></td></tr><tr><td>originalidtype</td><td>text</td><td></td></tr><tr><td>originalprovider</td><td>text</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr></tbody></table>

