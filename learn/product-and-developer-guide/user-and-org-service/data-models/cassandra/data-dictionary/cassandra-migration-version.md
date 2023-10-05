# Cassandra Migration Version

### sunbird.cassandra\_migration\_version (**PRIMARY KEY: version)**

Table used to capture cassandra CQL script version status during LERN release deployment

<table><thead><tr><th width="180.33333333333331">Column Name</th><th width="122">Data Type</th><th>Description</th><th>Sample Data</th></tr></thead><tbody><tr><td>version</td><td>text</td><td>Current CQL script  version deployed</td><td>1.113</td></tr><tr><td>checksum</td><td>int</td><td></td><td>-1988945306</td></tr><tr><td>description</td><td>text</td><td>Not Used</td><td>cassandra</td></tr><tr><td>execution_time</td><td>int</td><td>Time taken in milliseconds to execute the cql script</td><td>2323</td></tr><tr><td>installed_by</td><td>text</td><td>Not Used</td><td></td></tr><tr><td>installed_on</td><td>timestamp</td><td>Timestamp on which the cql script was executed</td><td>2020-12-18 11:04:46.095000+0000</td></tr><tr><td>installed_rank</td><td>int</td><td>The order in which this migration was applied amongst all others. (For out of order detection)</td><td>226</td></tr><tr><td>script</td><td>text</td><td>CQL script name</td><td>V1.113_cassandra.cql</td></tr><tr><td>success</td><td>boolean</td><td>Indicator to mention whether CQL script was run successfully or not</td><td>True</td></tr><tr><td>type</td><td>text</td><td>The type of migration (CQL, JAVA_DRIVER, ...)</td><td>CQL</td></tr><tr><td>version_rank</td><td>int</td><td>The position of this version amongst all others. (For easy order by sorting)</td><td>112</td></tr></tbody></table>

### sunbird.cassandra\_migration\_version\_counts (PRIMARY KEY: name)

Table used to store information about the last run CQL migration script data

<table><thead><tr><th width="167.33333333333331">Column Name</th><th width="120">Data Type</th><th>Description</th><th>Sample Data</th></tr></thead><tbody><tr><td>name</td><td>text</td><td>Field Name</td><td>installed_rank</td></tr><tr><td>count</td><td>counter</td><td>Field Value</td><td>257</td></tr></tbody></table>

