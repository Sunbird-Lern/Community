# Cassandra Migration Version

### sunbird.cassandra\_migration\_version (**PRIMARY KEY: version)**

<table><thead><tr><th width="180.33333333333331">Column Name</th><th width="122">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>version</td><td>text</td><td></td></tr><tr><td>checksum</td><td>int</td><td></td></tr><tr><td>description</td><td>text</td><td></td></tr><tr><td>execution_time</td><td>int</td><td></td></tr><tr><td>installed_by</td><td>text</td><td></td></tr><tr><td>installed_on</td><td>timestamp</td><td></td></tr><tr><td>installed_rank</td><td>int</td><td></td></tr><tr><td>script</td><td>text</td><td></td></tr><tr><td>success</td><td>boolean</td><td></td></tr><tr><td>type</td><td>text</td><td></td></tr><tr><td>version_rank</td><td>int</td><td></td></tr></tbody></table>

### sunbird.cassandra\_migration\_version\_counts (PRIMARY KEY: name)



<table><thead><tr><th width="167.33333333333331">Column Name</th><th width="120">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>name</td><td>text</td><td></td></tr><tr><td>count</td><td>counter</td><td></td></tr></tbody></table>

