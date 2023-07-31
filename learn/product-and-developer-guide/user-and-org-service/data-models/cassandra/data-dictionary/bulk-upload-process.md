# Bulk Upload Process

### sunbird.bulk\_upload\_process (**PRIMARY KEY: id)**

<table><thead><tr><th width="177.33333333333331">Column Name</th><th width="157">Data Type</th><th>Decription</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>data</td><td>text</td><td></td></tr><tr><td>failureresult</td><td>text</td><td></td></tr><tr><td>lastupdatedon</td><td>timestamp</td><td></td></tr><tr><td>objecttype</td><td>text</td><td></td></tr><tr><td>organisationid</td><td>text</td><td></td></tr><tr><td>processendtime</td><td>text</td><td></td></tr><tr><td>processstarttime</td><td>text</td><td></td></tr><tr><td>retrycount</td><td>int</td><td></td></tr><tr><td>status</td><td>int</td><td></td></tr><tr><td>storagedetails</td><td>text</td><td></td></tr><tr><td>successresult</td><td>text</td><td></td></tr><tr><td>taskcount</td><td>int</td><td></td></tr><tr><td>telemetrycontext</td><td>map&#x3C;text, text></td><td></td></tr><tr><td>uploadedby</td><td>text</td><td></td></tr><tr><td>uploadeddate</td><td>text</td><td></td></tr></tbody></table>

### sunbird.bulk\_upload\_process\_task (PRIMARY KEY: processid, sequenceid)

<table><thead><tr><th width="167.33333333333331">Column Name</th><th width="117">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>processid</td><td>text</td><td></td></tr><tr><td>sequenceid</td><td>int</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>data</td><td>text</td><td></td></tr><tr><td>failureresult</td><td>text</td><td></td></tr><tr><td>iterationid</td><td>int</td><td></td></tr><tr><td>lastupdatedon</td><td>timestamp</td><td></td></tr><tr><td>status</td><td>int</td><td></td></tr><tr><td>successresult</td><td>text</td><td></td></tr></tbody></table>

