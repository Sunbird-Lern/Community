# Functional Configurations

{% tabs %}
{% tab title="Functional Config" %}
<table><thead><tr><th width="268.7935222672064">Property</th><th>Description</th><th>Default Value</th></tr></thead><tbody><tr><td>max_group_limit</td><td>Maximum number of groups a user can create</td><td>50</td></tr><tr><td>max_group_members_limit</td><td>Maximum number of members a group can have</td><td>150</td></tr><tr><td>max_activity_limit</td><td>Maximum number of activities a group can have</td><td>20</td></tr><tr><td>enable_userid_redis_cache</td><td>To enable cache for groups and group details</td><td>true</td></tr><tr><td>groups_redis_ttl</td><td>Group details cache duration</td><td>86400</td></tr><tr><td>user_redis_ttl</td><td>User group list cache duration</td><td>3600</td></tr><tr><td>activityConfig</td><td>To configure various types of activities and services to fetch it.</td><td></td></tr></tbody></table>


{% endtab %}

{% tab title="System Config" %}
<table><thead><tr><th width="242.66666666666666">JSON Key</th><th>Key</th><th>Default Value</th></tr></thead><tbody><tr><td>SUNBIRD_CS_BASE_URL</td><td>CONTENT_SERVICE_PORT</td><td><a href="http://search-service:9000">http://search-service:9000</a></td></tr><tr><td>USER_SERVICE_BASE_URL</td><td>LEARNER_SERVICE_PORT</td><td><a href="http://learner-service:9000">http://learner-service:9000</a></td></tr><tr><td>ACCESS_TOKEN_PUBLICKEY_BASEPATH</td><td>accesstoken.publickey.basepath</td><td>/keys/</td></tr><tr><td>ENABLE_TENANT_CONFIGURATION</td><td>enable_tenant_config</td><td>*</td></tr><tr><td>ENABLE_USERID_REDIS_CACHE</td><td>enable_userid_redis_cache</td><td>true</td></tr><tr><td>GROUPS_REDIS_TTL</td><td>groups_redis_ttl</td><td>864004</td></tr><tr><td>MAX_ACTIVITY_LIMIT</td><td>max_activity_limi</td><td>20</td></tr><tr><td>MAX_GROUP_LIMIT</td><td>max_group_limit</td><td>50</td></tr><tr><td>MAX_GROUP_MEMBERS_LIMIT</td><td>max_group_members_limit</td><td>150</td></tr><tr><td>NOTIFICATION_SERVICE_API_URL</td><td>notification_service_api_url</td><td>/v2/notification/send</td></tr><tr><td>NOTIFICATION_SERVICE_BASE_URL</td><td>notification_service_base_url</td><td><a href="http://notification-service:9000">http://notification-service:9000</a></td></tr><tr><td>SUNBIRD_CASSANDRA_CONSISTENCY_LEVEL</td><td>sunbird_cassandra_consistency_level</td><td>quorum</td></tr><tr><td>SUNBIRD_CASSANDRA_IP</td><td>sunbird_cassandra_host</td><td>11.3.2.4,11.3.2.5,11.3.2.6</td></tr><tr><td></td><td>sunbird_cassandra_password</td><td>password</td></tr><tr><td></td><td>sunbird_cassandra_port</td><td>9042,9042,9042</td></tr><tr><td></td><td>sunbird_cassandra_username</td><td>cassandra</td></tr><tr><td>SUNBIRD_CS_SEARCH_URL</td><td>sunbird_cs_search_url</td><td>/v3/search</td></tr><tr><td></td><td>sunbird_keycloak_required_action_link_expiration_seconds</td><td>2592000</td></tr><tr><td></td><td>sunbird_keycloak_user_federation_provider_id</td><td>provider id</td></tr><tr><td></td><td>sunbird_redis_host</td><td>11.3.2.18</td></tr><tr><td></td><td>sunbird_redis_port</td><td>6379</td></tr><tr><td></td><td>sunbird_sso_client_id</td><td>eg: id</td></tr><tr><td></td><td>sunbird_sso_client_secret</td><td>eg: id</td></tr><tr><td></td><td>sunbird_sso_password</td><td>eg: passowrd</td></tr><tr><td></td><td>sunbird_sso_publickey</td><td>eg: encrypted public key</td></tr><tr><td>SUNBIRD_SSO_REALM</td><td>sunbird_sso_realm</td><td>sunbird</td></tr><tr><td>SUNBIRD_SSO_URL</td><td>sunbird_sso_url</td><td><a href="https://staging.sunbirded.org/auth/">https://staging.sunbirded.org/auth/</a></td></tr><tr><td></td><td>sunbird_sso_username</td><td>sunbird-staging-new-admin</td></tr><tr><td>USER_SERVICE_SEARCH_URL</td><td>sunbird_user_service_search_url</td><td>/private/api/user/v1/search</td></tr><tr><td>USER_REDIS_TTL</td><td>user_redis_ttl</td><td>3600</td></tr></tbody></table>


{% endtab %}
{% endtabs %}