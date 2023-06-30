---
description: List of tables in Cassandra database used in Notification service
---

# Notification Service



### sunbird\_notifications.notification\_feed \[PRIMARY KEY (userid,id)]



<table><thead><tr><th width="167.33333333333331">Column Name</th><th width="124">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>action</td><td>text</td><td></td></tr><tr><td>expireon</td><td>timestamp</td><td></td></tr><tr><td>priority</td><td>int</td><td></td></tr><tr><td>status</td><td>text</td><td></td></tr><tr><td>updatedby</td><td>text</td><td></td></tr><tr><td>updatedon</td><td>timestamp</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr><tr><td>version</td><td>text</td><td></td></tr></tbody></table>



### sunbird.notification\_template \[PRIMARY KEY((templateId,language))]



<table><thead><tr><th width="184.33333333333331">Column Name</th><th width="113">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>templateId</td><td>text</td><td></td></tr><tr><td>lang</td><td>text</td><td></td></tr><tr><td>type</td><td>text</td><td></td></tr><tr><td>ver</td><td>text</td><td></td></tr><tr><td>template</td><td>text</td><td></td></tr><tr><td>template_schema</td><td>text</td><td></td></tr><tr><td>createdOn</td><td>timestamp</td><td></td></tr><tr><td>lastUpdatedOn</td><td>timestamp</td><td></td></tr><tr><td>createdBy</td><td>text</td><td></td></tr><tr><td>lastUpdatedBy</td><td>text</td><td></td></tr></tbody></table>

