# Organisation

### sunbird.organisation (**PRIMARY KEY: id)**

Table used for storing Tenants/Organisations and Sub-Organisations

<table><thead><tr><th width="177.33333333333331">Column Name</th><th width="187">Data Type</th><th>Description</th><th>Sample Value</th></tr></thead><tbody><tr><td>id</td><td>text</td><td>Id of the organisation</td><td>0126796199493140480</td></tr><tr><td>channel</td><td>text</td><td>Abbreviation of the Tenant Organisation name</td><td>TN , AP, CBSE etc if Tenant Org Name is Tamil Nadu, Andra Pradesh, Central Board of Secondary Education etc</td></tr><tr><td><del>contactdetail</del></td><td>text</td><td>Not Used</td><td></td></tr><tr><td>createdby</td><td>text</td><td>UUID of the created user</td><td>7c784c71-9034-4de7-aa38-5382fc673b14</td></tr><tr><td>createddate</td><td>text</td><td>Date on which Organisation detail as added to the table</td><td></td></tr><tr><td>description</td><td>text</td><td>Description on the Organisation</td><td></td></tr><tr><td>email</td><td>text</td><td>Email Id f the Organisation</td><td></td></tr><tr><td>externalid</td><td>text</td><td>Unique identifier or registered Organisation Code which is used  for reference externally</td><td>3453456 or something unique to the org</td></tr><tr><td>hashtagid</td><td>text</td><td>Same as organisation id</td><td>0126796199493140480</td></tr><tr><td><del>isrootorg</del></td><td>boolean</td><td>Not Used</td><td></td></tr><tr><td>isssoenabled</td><td>boolean</td><td>If the login from tenant site is enabled to sunbird system.</td><td>True or False</td></tr><tr><td>istenant</td><td>boolean</td><td>To indicate whether Organisation is a Tenant ORg or  Sub- Org under the Tenant Org</td><td>True or False</td></tr><tr><td>keys</td><td>map&#x3C;text, frozen&#x3C;list&#x3C;text>>></td><td>Public key shared by the Organisation</td><td></td></tr><tr><td><del>locationids</del></td><td>list&#x3C;text></td><td>Not used</td><td></td></tr><tr><td>organisationtype</td><td>int</td><td>Type of the Organisation</td><td>2, 5 etc</td></tr><tr><td>orglocation</td><td>text</td><td>Location details of the organisation. This is  validated against the configuration of location types in properties file "sunbird_valid_location_types" </td><td><p>[ { "code": "32", "type": "state" }, { "code": "3210", "type": "district" },</p><p>{"code": "321001", "type": "block"} ,{"code": "32100123", "type": "cluster"]</p></td></tr><tr><td>orgname</td><td>text</td><td>Name of the Organisation</td><td></td></tr><tr><td>provider</td><td>text</td><td>Same as channel. </td><td></td></tr><tr><td>rootorgid</td><td>text</td><td>null in case of Tenant Orgs and Tenant Org id incase of sub-orgs.</td><td>null or 0126796199493140480 </td></tr><tr><td>slug</td><td>text</td><td>Slug and channel are abbrevations of organisation name, where slug is URL compatable, while channel is not.</td><td>tn, ap etc</td></tr><tr><td>status</td><td>int</td><td>Active or not. '1' means active, '0' is inactive</td><td>1 or 0</td></tr><tr><td>updatedby</td><td>text</td><td>UUID of the user who updated the organisation detail.</td><td></td></tr><tr><td>updateddate</td><td>text</td><td>Date in which this table record is updated last.</td><td></td></tr></tbody></table>

### sunbird.org\_external\_identity \[PRIMARY KEY: (provider, externalid)]

<table><thead><tr><th width="162.33333333333331">Column Name</th><th width="117">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>provider</td><td>text</td><td></td></tr><tr><td>externalid</td><td>text</td><td></td></tr><tr><td>orgid</td><td>text</td><td></td></tr></tbody></table>
