# OTP

### sunbird.otp \[PRIMARY KEY: (type, key)]

Table used to store OTP information

<table><thead><tr><th width="171.33333333333331">Column Name</th><th width="117">Data Type</th><th>Description</th><th>Sample Data</th></tr></thead><tbody><tr><td>type</td><td>text</td><td>OTP Communication mode</td><td>EMAIL/PHONE</td></tr><tr><td>key</td><td>text</td><td>Email/Phone of the user</td><td>98******10</td></tr><tr><td>attemptedcount</td><td>int</td><td>Number of times OTP mismatch was identified </td><td>2</td></tr><tr><td>createdon</td><td>timestamp</td><td>record created on timestamp</td><td></td></tr><tr><td>otp</td><td>text</td><td>OTP</td><td>254789</td></tr></tbody></table>

### sunbird.rate\_limit \[PRIMARY KEY: (key, unit)]

Table used to store rate limit information (number of requests per hour/day)

<table><thead><tr><th width="159.33333333333331">Column Name</th><th width="112">Data Type</th><th width="159">Description</th><th>Sample Data</th></tr></thead><tbody><tr><td>key</td><td>text</td><td>Email/Phone of the user</td><td>testaugustuser@yopmail.com</td></tr><tr><td>unit</td><td>text</td><td>DAY/HOUR</td><td>DAY</td></tr><tr><td>count</td><td>int</td><td></td><td>1</td></tr><tr><td>rate</td><td>int</td><td>Number of notifications that can be sent as per limit</td><td>20</td></tr></tbody></table>

