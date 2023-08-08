# Role

### sunbird.role \[PRIMARY KEY: id]

Table used to store Roles definition.

<table><thead><tr><th width="158.33333333333331">Column Name</th><th width="115">Data Type</th><th>Description</th><th>Sample Data</th></tr></thead><tbody><tr><td>id</td><td>text</td><td>Role Identifier</td><td>CONTENT_REVIEWER</td></tr><tr><td>name</td><td>text</td><td>Role Name</td><td>Content Reviewer</td></tr><tr><td>rolegroupid</td><td>list&#x3C;text></td><td>Role Group used for API access management</td><td>['CONTENT_CURATION']</td></tr><tr><td>status</td><td>int</td><td>status of the role</td><td>1 - Valid</td></tr></tbody></table>

### sunbird.role\_group \[PRIMARY KEY: id]

Table used to store role group information

<table><thead><tr><th width="158.33333333333331">Column Name</th><th width="115">Data Type</th><th>Description</th><th>Sample Data</th></tr></thead><tbody><tr><td>id</td><td>text</td><td>Role Group identifier</td><td>ORG_MANAGEMENT</td></tr><tr><td>name</td><td>text</td><td>Role Group Name</td><td>Org Management</td></tr><tr><td>url_action_ids</td><td>list&#x3C;text></td><td>URL action Identifiers (Refer to sunbird.url_action)</td><td>['createOrg', 'updateOrg', 'removeOrg', 'createUser', 'updateUser']</td></tr></tbody></table>

### sunbird.url\_action \[PRIMARY KEY: id]

Table used to define url action to API endpoint mapping

<table><thead><tr><th width="158.33333333333331">Column Name</th><th width="115">Data Type</th><th>Description</th><th>Sample Data</th></tr></thead><tbody><tr><td>id</td><td>text</td><td>URL action Identifier</td><td>updateOrg</td></tr><tr><td>name</td><td>text</td><td>URL action Name</td><td>updateOrg</td></tr><tr><td>url</td><td>list&#x3C;text></td><td>API endpoint list</td><td>['/v1/organisation/update']</td></tr></tbody></table>

### sunbird.user\_roles \[PRIMARY KEY (userid, role)]

Tole used to store user to role mapping

<table><thead><tr><th width="161.33333333333331">Column Name</th><th width="124">Data Type</th><th>Description</th><th>Sample Data</th></tr></thead><tbody><tr><td>userid</td><td>text</td><td>UUID of the User</td><td>5e48c2ba-cd3a-4d85-9d3b-28dc329d7dd9</td></tr><tr><td>role</td><td>text</td><td>Role Identifier</td><td>BOOK_REVIEWER</td></tr><tr><td>createdby</td><td>text</td><td>Role added By</td><td>08631a74-4b94-4cf7-a818-831135248a4a</td></tr><tr><td>createddate</td><td>text</td><td>Record creation timestamp</td><td>2021-08-11 08:53:49:662+0000</td></tr><tr><td>scope</td><td>text</td><td>Role scope - organisation to which role is defined for the user</td><td>[{"organisationId":"01334203864941363283"}]</td></tr><tr><td>updatedby</td><td>text</td><td>Role Updated By</td><td></td></tr><tr><td>updateddate</td><td>text</td><td>Last record Updated timestamp</td><td></td></tr></tbody></table>

