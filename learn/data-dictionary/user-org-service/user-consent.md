# User Consent

### sunbird.user\_consent \[PRIMARY KEY (user\_id, consumer\_id, object\_id)]

<table><thead><tr><th width="172.33333333333331">Column Name</th><th width="124">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>user_id</td><td>text</td><td></td></tr><tr><td>consumer_id</td><td>text</td><td></td></tr><tr><td>object_id</td><td>text</td><td></td></tr><tr><td>categories</td><td>list&#x3C;text></td><td></td></tr><tr><td>consent_data</td><td>text</td><td></td></tr><tr><td>consumer_type</td><td>text</td><td></td></tr><tr><td>created_on</td><td>timestamp</td><td></td></tr><tr><td>expiry</td><td>timestamp</td><td></td></tr><tr><td>id</td><td>text</td><td></td></tr><tr><td>last_updated_on</td><td>timestamp</td><td></td></tr><tr><td>object_type</td><td>text</td><td></td></tr><tr><td>status</td><td>text</td><td></td></tr></tbody></table>

### sunbird.user\_declarations \[PRIMARY KEY (userid, orgid, persona)]

<table><thead><tr><th width="169.33333333333331">Column Name</th><th width="160">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>userid</td><td>text</td><td></td></tr><tr><td>orgid</td><td>text</td><td></td></tr><tr><td>persona</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>errortype</td><td>text</td><td></td></tr><tr><td>status</td><td>text</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updatedon</td><td>timestamp</td><td></td></tr><tr><td>userinfo</td><td>map&#x3C;text, text></td><td></td></tr></tbody></table>

