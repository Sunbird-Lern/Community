# System Settings

### sunbird.system\_settings (**PRIMARY KEY: id)**

Table used for storing system level configuration values used by LERN and other sunbird BBs.

<table><thead><tr><th width="159.33333333333331">Column Name</th><th width="114">Data Type</th><th>Description</th><th>Sample Value</th></tr></thead><tbody><tr><td>id</td><td>text</td><td>Unique code for identifying the settings or configuration</td><td>custodianOrgId, tncConfig etc</td></tr><tr><td>field</td><td>text</td><td>As of now same as id itself</td><td>custodianOrgId, tncConfig etc</td></tr><tr><td>value</td><td>text</td><td>Value of the configuration. This can be a string or a json string</td><td><p>0126796199493140480 or </p><p>"{"latestVersion":"v13","v13":{"url":"https://obj.stage.sunbirded.org/privacy-policy/terms-of-use.html"}}"  </p></td></tr></tbody></table>

