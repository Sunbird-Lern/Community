# Installation Configuration

### Cassandra Config

```
coreConnectionsPerHostForLocal=4
coreConnectionsPerHostForRemote=2
maxConnectionsPerHostForLocal=10
maxConnectionsPerHostForRemote=4
maxRequestsPerConnection=32768
heartbeatIntervalSeconds=60
poolTimeoutMillis=0
contactPoint=127.0.0.1
port=9042
userName=cassandra
password=password
queryLoggerConstantThreshold=300
keyspace=sunbird
```

### Redis Config

```
groups_redis_ttl=864004
user_redis_ttl=3600
sso.connection.pool.size=20
```

### DB Config

```
db.ip=127.0.0.1
db.port=9042
db.username=cassandra
db.password=password
db.keyspace=sunbird
```

### Keyclock Config

```
sso.url=
sso.realm=sunbird
sso.enabled=true
```

### Notification Service

```
notification_service_base_url=
notification_service_api_url=/v2/notification/send
enable_tenant_config=custchannel,tc
```

### UserOrg Service

```
LEARNER_SERVICE_PORT=
sunbird_user_service_search_url=/private/api/user/v1/search
sunbird_us_system_setting_url=/api/data/v1/system/settings/list
sunbird_us_org_read_url=/v1/org/read
```

### Content Service

```
CONTENT_SERVICE_PORT=
sunbird_cs_search_url=
```
