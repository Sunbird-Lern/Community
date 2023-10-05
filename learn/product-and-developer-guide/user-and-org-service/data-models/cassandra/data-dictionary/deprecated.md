# Deprecated

### Sunbird.action\_group (**PRIMARY KEY: id)**

<table><thead><tr><th width="167.33333333333331">Column Name</th><th width="111">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>actionid</td><td>text</td><td></td></tr><tr><td>groupname</td><td>text</td><td></td></tr></tbody></table>

### sunbird.user\_action\_role \[PRIMARY KEY: id]

<table><thead><tr><th width="152.33333333333331">Column Name</th><th width="115">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>roleid</td><td>text</td><td></td></tr><tr><td>actiongroupid</td><td>list&#x3C;text></td><td></td></tr></tbody></table>

### sunbird.user\_skills \[PRIMARY KEY: id]

<table><thead><tr><th width="211.33333333333331">Column Name</th><th width="161">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>endorsementcount</td><td>int</td><td></td></tr><tr><td>endorserslist</td><td>frozen&#x3C;list&#x3C;frozen&#x3C;map&#x3C;text, text>>>></td><td></td></tr><tr><td>lastupdatedby</td><td>text</td><td></td></tr><tr><td>lastupdatedon</td><td>timestamp</td><td></td></tr><tr><td>skillname</td><td>text</td><td></td></tr><tr><td>skillnametolowercase</td><td>text</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr></tbody></table>

### sunbird.user\_org \[PRIMARY KEY: id]

<table><thead><tr><th width="170.33333333333331">Column Name</th><th width="115">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>addedby</td><td>text</td><td></td></tr><tr><td>addedbyname</td><td>text</td><td></td></tr><tr><td>approvaldate</td><td>text</td><td></td></tr><tr><td>approvedby</td><td>text</td><td></td></tr><tr><td>hashtagid</td><td>text</td><td></td></tr><tr><td>isapproved</td><td>boolean</td><td></td></tr><tr><td>isdeleted</td><td>boolean</td><td></td></tr><tr><td>isrejected</td><td>boolean</td><td></td></tr><tr><td>organisationid</td><td>text</td><td></td></tr><tr><td>orgjoindate</td><td>text</td><td></td></tr><tr><td>orgleftdate</td><td>text</td><td></td></tr><tr><td>position</td><td>text</td><td></td></tr><tr><td>roles</td><td>list&#x3C;text></td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updateddate</td><td>text</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr></tbody></table>

### sunbird.user\_cert \[PRIMARY KEY: id]

<table><thead><tr><th width="172.33333333333331">Column Name</th><th width="159">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>accesscode</td><td>text</td><td></td></tr><tr><td>createdat</td><td>timestamp</td><td></td></tr><tr><td>isdeleted</td><td>boolean</td><td></td></tr><tr><td>oldid</td><td>text</td><td></td></tr><tr><td>store</td><td>map&#x3C;text, text></td><td></td></tr><tr><td>updatedat</td><td>timestamp</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr></tbody></table>

### sunbird.user\_feed \[PRIMARY KEY: id]

<table><thead><tr><th width="179.33333333333331">Column Name</th><th width="127">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>category</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>data</td><td>text</td><td></td></tr><tr><td>expireon</td><td>timestamp</td><td></td></tr><tr><td>priority</td><td>int</td><td></td></tr><tr><td>status</td><td>text</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updatedon</td><td>timestamp</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr></tbody></table>

### sunbird.tenant\_preference \[PRIMARY KEY: id]&#x20;

<table><thead><tr><th width="170.33333333333331">Column Name</th><th width="111">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>data</td><td>text</td><td></td></tr><tr><td>key</td><td>text</td><td></td></tr><tr><td>orgid</td><td>text</td><td></td></tr><tr><td>role</td><td>text</td><td></td></tr><tr><td>tenantname</td><td>text</td><td></td></tr></tbody></table>

### Sunbird.address (**PRIMARY KEY: id)**

<table><thead><tr><th width="160.33333333333331">Column Name</th><th width="118">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>addressline1</td><td>text</td><td></td></tr><tr><td>addressline2</td><td>text</td><td></td></tr><tr><td>addtype</td><td>text</td><td></td></tr><tr><td>city</td><td>text</td><td></td></tr><tr><td>country</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createddate</td><td>text</td><td></td></tr><tr><td>isdeleted</td><td>boolean</td><td></td></tr><tr><td>state</td><td>text</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updateddate</td><td>text</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr><tr><td>zipcode</td><td>text</td><td></td></tr></tbody></table>

### sunbird.cert\_registry (PRIMARY KEY: id)

<table><thead><tr><th width="162.33333333333331">Column Name</th><th width="124">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>accesscode</td><td>text</td><td></td></tr><tr><td>createdat</td><td>timestamp</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>data</td><td>text</td><td></td></tr><tr><td>isrevoked</td><td>boolean</td><td></td></tr><tr><td>jsonurl</td><td>text</td><td></td></tr><tr><td>pdfurl</td><td>text</td><td></td></tr><tr><td>reason</td><td>text</td><td></td></tr><tr><td>recipient</td><td>text</td><td></td></tr><tr><td>related</td><td>text</td><td></td></tr><tr><td>updatedat</td><td>timestamp</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr></tbody></table>

### sunbird.config\_path\_audit (PRIMARY KEY: ((id, cloud\_store\_type), created\_date))

<table><thead><tr><th width="219.33333333333331">Column Name</th><th width="125">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>cloud_store_type</td><td>text</td><td></td></tr><tr><td>created_date</td><td>bigint</td><td></td></tr><tr><td>cloud_store_account</td><td>text</td><td></td></tr><tr><td>cloud_store_container</td><td>text</td><td></td></tr><tr><td>cloud_store_path</td><td>text</td><td></td></tr><tr><td>version</td><td>bigint</td><td></td></tr></tbody></table>

### sunbird.geo\_location (PRIMARY KEY: id)

<table><thead><tr><th width="159.33333333333331">Column Name</th><th width="114">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createddate</td><td>text</td><td></td></tr><tr><td>location</td><td>text</td><td></td></tr><tr><td>rootorgid</td><td>text</td><td></td></tr><tr><td>topic</td><td>text</td><td></td></tr><tr><td>type</td><td>text</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updateddate</td><td>text</td><td></td></tr><tr><td>usercount</td><td>int</td><td></td></tr><tr><td>usercountttl</td><td>text</td><td></td></tr></tbody></table>

### sunbird.master\_action (PRIMARY KEY: id)

<table><thead><tr><th width="160.33333333333331">Column Name</th><th width="111">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>name</td><td>text</td><td></td></tr></tbody></table>

### sunbird.media\_type

<table><thead><tr><th width="160.33333333333331">Column Name</th><th width="111">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>name</td><td>text</td><td></td></tr></tbody></table>

### sunbird.report\_tracking \[PRIMARY KEY: id]

<table><thead><tr><th width="156.33333333333331">Column Name</th><th width="119">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>createddate</td><td>text</td><td></td></tr><tr><td>data</td><td>text</td><td></td></tr><tr><td>email</td><td>text</td><td></td></tr><tr><td>fileurl</td><td>text</td><td></td></tr><tr><td>firstname</td><td>text</td><td></td></tr><tr><td>format</td><td>text</td><td></td></tr><tr><td>period</td><td>text</td><td></td></tr><tr><td>resourceid</td><td>text</td><td></td></tr><tr><td>resourcename</td><td>text</td><td></td></tr><tr><td>status</td><td>int</td><td></td></tr><tr><td>trycount</td><td>int</td><td></td></tr><tr><td>type</td><td>text</td><td></td></tr><tr><td>updateddate</td><td>text</td><td></td></tr><tr><td>uploadeddate</td><td>text</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr><tr><td></td><td></td><td></td></tr></tbody></table>

### sunbird.shadow\_user \[PRIMARY KEY (channel, userextid)]

<table><thead><tr><th width="170.33333333333331">Column Name</th><th width="113">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>channel</td><td></td><td></td></tr><tr><td>userextid</td><td></td><td></td></tr><tr><td>addedby</td><td></td><td></td></tr><tr><td>attemptedcount</td><td>int</td><td></td></tr><tr><td>claimedon</td><td>timestamp</td><td></td></tr><tr><td>claimstatus</td><td>int</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>email</td><td></td><td></td></tr><tr><td>name</td><td></td><td></td></tr><tr><td>orgextid</td><td></td><td></td></tr><tr><td>phone</td><td></td><td></td></tr><tr><td>processid</td><td></td><td></td></tr><tr><td>updatedon</td><td>timestamp</td><td></td></tr><tr><td>userid</td><td></td><td></td></tr><tr><td>userids</td><td>list&#x3C;text></td><td></td></tr><tr><td>userstatus</td><td>int</td><td></td></tr></tbody></table>

