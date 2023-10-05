# Location

### Sunbird.location (**PRIMARY KEY: id)**

Table is used for storing locations.&#x20;

<table><thead><tr><th width="159.33333333333331">Column Name</th><th width="113">Data Type</th><th>Description</th><th>Sample Value</th></tr></thead><tbody><tr><td>id</td><td>text</td><td>UUID of the location</td><td>0c0391ba-610b-4796-8645-338d047b1e28</td></tr><tr><td>code</td><td>text</td><td>Unique code with which location is identified externally or outside sunbird system</td><td>4021</td></tr><tr><td>name</td><td>text</td><td>Name of the location</td><td></td></tr><tr><td>parentid</td><td>text</td><td>Parent location id in sunbird system</td><td>91d9baae-14f1-477a-955c-f91bd9037f0b </td></tr><tr><td>type</td><td>text</td><td>Type of the location. This is  validated against the configuration of location types in properties file "sunbird_valid_location_types" . This can be changed</td><td>state, district, block, cluster </td></tr></tbody></table>

