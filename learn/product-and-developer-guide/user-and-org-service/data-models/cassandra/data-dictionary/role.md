# Role

### sunbird.role \[PRIMARY KEY: id]

<table><thead><tr><th width="158.33333333333331">Column Name</th><th width="115">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>name</td><td>text</td><td></td></tr><tr><td>rolegroupid</td><td>list&#x3C;text></td><td></td></tr><tr><td>status</td><td>int</td><td></td></tr></tbody></table>

### sunbird.role\_group \[PRIMARY KEY: id]

<table><thead><tr><th width="158.33333333333331">Column Name</th><th width="115">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>name</td><td>text</td><td></td></tr><tr><td>url_action_ids</td><td>list&#x3C;text></td><td></td></tr></tbody></table>

### sunbird.url\_action \[PRIMARY KEY: id]

<table><thead><tr><th width="158.33333333333331">Column Name</th><th width="115">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>name</td><td>text</td><td></td></tr><tr><td>url</td><td>list&#x3C;text></td><td></td></tr></tbody></table>

### sunbird.user\_roles \[PRIMARY KEY (userid, role)]

<table><thead><tr><th width="161.33333333333331">Column Name</th><th width="124">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>userid</td><td>text</td><td></td></tr><tr><td>role</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createddate</td><td>text</td><td></td></tr><tr><td>scope</td><td>text</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updateddate</td><td>text</td><td></td></tr></tbody></table>

