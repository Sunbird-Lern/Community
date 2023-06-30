---
description: List of tables in Cassandra database used in Groups service
---

# Groups Service



### sunbird\_groups.group \[PRIMARY KEY: id]



<table><thead><tr><th width="176.33333333333331">Column Name</th><th width="120">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>activities</td><td>list&#x3C;frozen&#x3C;map&#x3C;text, text>>></td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>description</td><td>text</td><td></td></tr><tr><td>membershiptype</td><td>text</td><td></td></tr><tr><td>name</td><td>text</td><td></td></tr><tr><td>status</td><td>text</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updatedon</td><td>timestamp</td><td></td></tr></tbody></table>



### sunbird\_groups.group\_member \[PRIMARY KEY (groupid, userid)]



<table><thead><tr><th width="165.33333333333331">Column Name</th><th width="131">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>groupid</td><td>text</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>removedby</td><td>text</td><td></td></tr><tr><td>removedon</td><td>timestamp</td><td></td></tr><tr><td>role</td><td>text</td><td></td></tr><tr><td>status</td><td>text</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updatedon</td><td>timestamp</td><td></td></tr><tr><td>visited</td><td>boolean</td><td></td></tr></tbody></table>



### sunbird\_groups.user\_group \[PRIMARY KEY: userid]



<table><thead><tr><th width="158.33333333333331">Column Name</th><th width="116">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>userid</td><td>text</td><td></td></tr><tr><td>groupid</td><td>set&#x3C;text></td><td></td></tr><tr><td></td><td></td><td></td></tr></tbody></table>







