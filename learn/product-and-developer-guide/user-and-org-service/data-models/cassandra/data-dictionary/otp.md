# OTP

### sunbird.otp \[PRIMARY KEY: (type, key)]

<table><thead><tr><th width="171.33333333333331">Column Name</th><th width="117">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td>text</td><td></td></tr><tr><td>key</td><td>text</td><td></td></tr><tr><td>attemptedcount</td><td>int</td><td></td></tr><tr><td>createdon</td><td>timestamp</td><td></td></tr><tr><td>otp</td><td>text</td><td></td></tr></tbody></table>

### sunbird.rate\_limit \[PRIMARY KEY: (key, unit)]

<table><thead><tr><th width="159.33333333333331">Column Name</th><th width="112">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>key</td><td>text</td><td></td></tr><tr><td>unit</td><td>text</td><td></td></tr><tr><td>count</td><td>int</td><td></td></tr><tr><td>rate</td><td>int</td><td></td></tr></tbody></table>

