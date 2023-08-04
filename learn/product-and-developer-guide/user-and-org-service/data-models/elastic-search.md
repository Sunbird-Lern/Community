# Elastic Search

Elastic Search indexes used by UserOrg :&#x20;

* [userv3](https://github.com/project-sunbird/sunbird-devops/blob/release-5.3.0-lern/ansible/roles/es-mapping/files/indices/userv3.json) - This index is used to store user data.
* [userfeed](https://github.com/project-sunbird/sunbird-devops/blob/release-5.3.0-lern/ansible/roles/es-mapping/files/indices/userfeed.json) - This index is used to store userfeed data.
* [usernotes](https://github.com/project-sunbird/sunbird-devops/blob/release-5.3.0-lern/ansible/roles/es-mapping/files/indices/usernotes.json) - This index is used to store usernotes data.
* [orgv3](https://github.com/project-sunbird/sunbird-devops/blob/release-5.3.0-lern/ansible/roles/es-mapping/files/indices/orgv3.json) - This index is used to store org data.
* [location](https://github.com/project-sunbird/sunbird-devops/blob/release-5.3.0-lern/ansible/roles/es-mapping/files/indices/location.json) - This index is used to store location data.

**Note:** userv3 index is mapped to user\_alias and orgv3 index mapped to org\_alias.&#x20;

#### Elastic Search Indices and Mappings Setup

{% embed url="https://github.com/Sunbird-Lern/userorg-service#elastic-search-indices-and-mappings-setup" %}
