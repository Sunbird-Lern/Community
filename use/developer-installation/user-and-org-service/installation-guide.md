# Installation Guide

### How To Setup

This section describes how to install and start User\&Org Service and set up the default organisation & user creation.

#### **Installation Configuration:**

User\&Org service requires few configurations to be set in properties file. Some of these properties can also be set as environment variables.

* Application functional configurations and dependency service configurations has to be mentioned in externalresource.properties file\
  \
  **\<Project base path>/sunbird-lms-service/core/platformcommon/src/main/resources/externalresource.properties**

#### Environment Variables Setup:

`sudo vi ~/.bashrc` (To use nano editor then replace vi with nano)\
Add the below variables as given below and then fire the below command\
`source ~/.bashrc`\
``**Please kindly check the latest environment properties file to ensure any new properties that needs to be added in profile,**\
If you use a ubuntu system then same has to be added in environment as well,\
`sudo nano /etc/environment`(To use nano editor then replace vi with nano)\
Add the same set of variables in the below section without the word **export** in the **start**,i.e sunbird\_cassandra\_host="127.0.0.1"

Paste below values and save:-

```
// environment variables to be set,

export sunbird_cassandra_host="127.0.0.1"
export sunbird_cassandra_port="9042"
export sunbird_cassandra_username="cassandra"
export sunbird_cassandra_password="cassandra"
export sunbird_cassandra_keyspace="sunbird"
export sunbird="sunbird"
export sunbird_es_host="0.0.0.0"
export sunbird_es_port="9200"
export sunbird_es_cluster="test"
export sunbird_sso_url="http://localhost:8081/auth/"
#export sunbird_sso_realm="master"
export sunbird_sso_username="admin"
export sunbird_sso_password="admin@123"
export sunbird_sso_client_id="admin-cli"
export sunbird_encryption_key="encKeyValue"
export sunbird_encryption_mode="local"
#export sunbird_sso_publickey= (for this value is copied from keycloak service)
# user platform -- Below settings are not needed.
export sunbird_environment="local"
export sunbird_instance="sunbird"
export sunbird_default_channel="sunbird"
export sunbird_default_channel="ORG_003"
export sunbird_default_tenant="sunbird"
export sunbird_encryption_key="SunBird"
export sunbird_cs_base_url="http://localhost:9000"
export sunbird_installation="127.0.0.1"
export sunbird_quartz_mode="embedded"
export sunbird_es_index="searchindex"
export sunbird_es_rest_api_port="9200"
#export ekstep_api_base_url="https://staging.open-sunbird.org/api"
export ekstep_api_base_url="http://11.2.6.6/content"
export ekstep_content_search_base_url="https://qa.ekstep.in/api"
export ekstep_authorization=""
export sunbird_mail_server_host="smtp.sendgrid.net"
export sunbird_mail_server_port="587"
export sunbird_mail_server_username="azure_886153b1defb14e38ecc9c7301625aba@azure.com"
export sunbird_mail_server_password="3uJbXaB5BkqNyL6L"
export sunbird_mail_server_from_email="support@sunbird.com"
export sunbird_account_name="sunbirddev"
export sunbird_account_key=""
export orgImageUrl="http://www.paramountias.com/media/images/current-affairs/diksha-portal.jpg"
export orgServerFromName="Diksha Gov"
export sunird_web_url="https://diksha.gov.in"
export sunbird_app_url="https://play.google.com/store?hl=en"
export sunbird_fcm_account_key="key="
export sunbird_test_base_url="http://localhost:9000"
export sunbird_installation="Sunbird_Dev"
export sunbird_username="admin"
export sunbird_user_password="password"
export sunbird_open_saber_bridge_enable="false"
export sunbird_sso_publickey=""
export sunbird_pg_host="127.0.0.1"
export sunbird_pg_port="5432"
export sunbird_pg_db="badgrDB"
export sunbird_pg_user="postgres"
export sunbird_pg_password="postgres"
export badging_authorization_key="4771d05cd46f7a28099c3217cf9c159db7425a18"
export content_store_api_base_url="https://dev.ekstep.in/api"
export content_store_api_key=""
export sunbird_authorization=""
export sunbird_api_base_url="https://sunbirdintl-qa.stackroute.com/api"
export sunbird_channel_read_api="/channel/v1/read"
export sunbird_framework_read_api="/framework/v1/read"
export sunbird_store_api_base_url="https://dev.open-sunbird.org/api"
export sunbird_channel_api="/channel/v1/read"
export sunbird_content_id="do_1125535199417548801180"
export sunbird_test_email_address_1="someemail1@emailid.com"
export sunbird_test_email_address_2="someemail2@emailid.com"
export sunbird_allowed_login="You can use your cellphone number to login"
export sunbird_user_framework_board="CBSE"
export sunbird_user_framework_grade_level="KG"
export sunbird_user_framework_medium="English"
export sunbird_user_framework_id="NCF"
export sunbird_user_framework_subject="English"
export sunbird_api_mgr_base_url="https://dev.open-sunbird.org/api"
export issuerId="issuerslug-16"
export badgeId="badgeslug-28"
export sunbird_keycloak_user_federation_provider_id="872382fa-9161-48f0-99ad-7148abb3492d"
export sunbird_gzip_enable=true
export sunbird_gzip_size_threshold=18000
export sunbird_redis_host="127.0.0.1"
export sunbird_redis_port="6379"
export sunbird_cache_enable="True"
export cassandra_host="127.0.0.1"
export custodianOrgId="0127765641642967041"
export sunbird_api_key=""
export sunbird_notification_kafka_topic="local.notification.all"
export sunbird_notification_kafka_servers_config="localhost:9092"
export user_alias=user
export org_alias=org
export sunbird_dbs_path="~/sunbird-dbs"
export sunbird_remote_req_router_path=""
export sunbird_remote_bg_req_router_path="path"
export domain_name="dev.sunbirded.org"
```

### Cassandra Setup:

```
//Install cassandra using docker

docker pull cassandra:3.11.8
docker run --name sunbird_cassandra -d -p 9042:9042 \
-v ~/sunbird-dbs/cassandra/data:/var/lib/cassandra \
-v ~/sunbird-dbs/cassandra/logs:/opt/cassandra/logs \
-v ~/sunbird-dbs/cassandra/backups:/mnt/backups \
--network bridge cassandra:3.11.8
```

Before proceeding with migration,fork the below projects and clone it from git,

`git clone` [`https://github.com/project-sunbird/sunbird-lms-service`](https://github.com/project-sunbird/sunbird-lms-service) **(latest release branch)**

`git clone` [`https://github.com/project-sunbird/sunbird-utils`](https://github.com/project-sunbird/sunbird-utils)

Run,\
`mvn clean install -DskipTests` in[ sunbird-utils](https://github.com/project-sunbird/sunbird-utils) & in[ sunbird-lms-service](https://github.com/project-sunbird/sunbird-lms-service)\
\
**Cassandra** **Migration**:

Before starting with migration please ensure to set the env variables In terminal, \
execute following commands for cassandra migration: \
\
`sudo docker exec -it sunbird_cassandra sh` \
`cqlsh -f /sunbird-lms-service/service/src/main/resources/cassandra.cql` \
\
If Can't open 'cassandra.cql' due to this error, \[Errno 13] Permission denied: 'cassandra.cql'&#x20;

then manually run all queries under cqlsh window \
after above command you may get errors, ignore those for now

open a new Terminal In the path **\<Project base path>**/sunbird-utils,\
Run the below command,\
`mvn clean install -DskipTests`&#x20;

Make sure the build is **success** and then,\
open a new Terminal In the path, **\<Project base path>/sunbird-utils/sunbird-cassandra-migration/cassandra-migration**,\
Run below command,\
`mvn clean install -DskipTests` \
`mvn exec:java`

If you face any error saying migration failed then,\
In terminal, open cassandra console again,\
`sudo docker exec -it sunbird_cassandra sh`\
`cqlsh` \
Then select the sunbird db using below command: \
`use sunbird;` \
`expand on;`&#x20;

`select * from cassandra_migration_version;` \
\
In the console see which migration version has failed and update the success flag to true for that version using below query, \
`update cassandra_migration_version set success = True where version='1.86';` **//Give the failed version number here**\
``Once the migration is done successfully, check for the below success message,\
**sunbird is up to date. No migration necessary.** \
**Migration Completed at ==1672910353402**

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Migration successful message</p></figcaption></figure>

### Elastic Search:

```
// Install elastic search using docker

docker run --name sunbird_es -d -p 9200:9200 -p 9300:9300 \
-v ~/sunbird-dbs/es/data:/usr/share/elasticsearch/data \
-v ~/sunbird-dbs/es/logs://usr/share/elasticsearch/logs \
-v ~/sunbird-dbs/es/backups:/opt/elasticsearch/backup \
-e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:6.8.22
```

Note : To resolve ElasticSearch Below Error :\
\
<img src="https://lh4.googleusercontent.com/u1RbEHP3bJ9AH4cWNqWOr_De8IvOI_HcKekRxXgY_1MTnPQwAcChUSW4LkRs4Av3qiPRC2vX6nOwUAZINSA6q-cLFf6zN0CmNtXIFv4UvX_cQUzK7J7jLD_DZl5chL20VFG6Sn5LwH09Nb7TrEqgnPrudeSsn_7RmXOtPbAeY7BnCdsstq4B52Om3niOzQ" alt="" data-size="original">\
\
\
Give Permission es/data and es/logs folder, before docker run --name sunbird\_es …\
\
mkdir -p \~/sunbird-dbs/es/data \~/sunbird-dbs/es/logs\
\
sudo chown -R 1000:1000 \~/sunbird-dbs/es/data

sudo chown -R 1000:1000 \~/sunbird-dbs/es/logs

Post installation, Elastic search needs to be setup with indices and mappings from [sunbird-utils](https://github.com/project-sunbird/sunbird-utils).

Pick all the indices and mappings from \*\* \*\*<mark style="color:green;">**sunbird-utils/sunbird-es-utils/src/main/resources**</mark> folders and create index and mapping using postman.

Create index and mapping mainly for **user, userfeed, usernotes, org,** and **location** JSON files.

{% embed url="https://github.com/project-sunbird/sunbird-utils/tree/master/sunbird-es-utils/src/main/resources" %}

PUT http://localhost:9200/\<indices\_name> Body : \<indices\_json\_content>

PUT http://localhost:9200/\<indices\_name>/\_mapping/\_doc Body : \<mapping\_json\_content>

After creating the indices and mappings, add respective org index to org\_alias (if using lms-service release-3.8.0 or above) and respective user index to user\_alias (if using lms-service release-3.7.0 or above)

Elastic search details need to be configured in elasticsearch.config.properties

#### Steps to follow before deploying and running user org service in your system:

1. Go to **\<Project base path> /service/src/main/java/org/sunbird/actor/organisation/OrganisationManagementActor.java** \
   In the **OrganisationManagementActor.java** find for the line,\
   `boolean bool = orgService.registerChannel(request, JsonKey.CREATE, actorMessage.getRequestContext());`\
   ``**We have to replace this line with,**\
   `boolean bool = true;`
2. **Follow this step only if you are using the release version prior to 5.1.0,** Go to **\<Project base path>/controller/app/util/RequestInterceptor.java** \
   In the **RequestInterceptor.java** find paste below lines in the apiHeaderIgnoreMap section of the code,\
   `apiHeaderIgnoreMap.put("/v1/org/create", var);`\
   `apiHeaderIgnoreMap.put("/v1/system/settings/set", var);`
3. Post 5.1.0 just go to **application.conf** and make the flag **AuthenticationEnabled** as **false** as below\
   `AuthenticationEnabled = false`\
   this will enable you to access all API's locally by declaring you as anonymous.
4. Go to **\<Project base path>/src/main/resources/externalresource.properties** and \
   Replace the values of the properties **user\_index\_alias** and **org\_index\_alias** with respect to the cassandra table name of the same respective table in your local system.

**Steps to Deploy and Run user org service in your system:**\
****\
****1. Open a new command line terminal in your system in the path,\
**\<Project base path>/sunbird-lms-service** and fire the below command,\
`mvn clean install -DskipTests`\
``Please ensure the build is success before firing the below command, if the build is not success then the project might not be imported properly and there is some configuration issues, fix the same and rebuild until it is successful.

2\. Then go to the path,\
**\<Project base path>/sunbird-lms-service/controller** and fire the below command,\
`mvn play2:run`

Once the Application started successfully Please check the health of all services to be true before proceeding further,

3\. To check the health status of service, Just hit the below url in your browser,\
[http://localhost:9000/health](http://localhost:9000/health) or run the below curl in your terminal.

```
 curl --location --request GET 'http://localhost:9000/health' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json'
```

The response should be something as below showing all services is up and healthy,

{% code overflow="wrap" %}
```json
// Success response of a health check API.

{
    "id": "api.all.health",
    "ver": "health",
    "ts": "2023-01-05 11:41:06:735+0530",
    "params": {
        "resmsgid": "8a11b6c3-d0b5-41d9-852e-6ab9e3ec2968",
        "msgid": "8a11b6c3-d0b5-41d9-852e-6ab9e3ec2968",
        "err": null,
        "status": "SUCCESS",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "response": {
            "checks": [
                {
                    "err": "",
                    "healthy": true,
                    "name": "Learner service",
                    "errmsg": ""
                },
                {
                    "err": "",
                    "healthy": true,
                    "name": "Actor service",
                    "errmsg": ""
                },
                {
                    "err": "",
                    "healthy": true,
                    "name": "Cassandra service",
                    "errmsg": ""
                },
                {
                    "err": "",
                    "healthy": true,
                    "name": "Elastic search service",
                    "errmsg": ""
                }
            ],
            "healthy": true,
            "name": "Complete health check api"
        }
    }
}
```
{% endcode %}

#### Frequently obtained errors previously at this Point:

1.  If the cassandra is not up and running then, when we hit the health check URL it would show a **Not initialised** error. So if you see this error, then make sure your cassandra is up and running properly, A screenshot for your reference,\


    <figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption><p>Not Initalised Error Sample screenshot</p></figcaption></figure>

2\. If the elastic search has some connectivity issues, then check for Below points,\
\
2.1. Check whether the **Host**,**Port** and **Cluster** for ES has been configured properly in the environment Variables or bash profile as given in the previous section of the document. Also ensure the same has been configured in, **\<Project base path>/sunbird-lms-service/core/platform/common/src/main/resources/externalresource.properties**\
****\
****2**.**2. **** Check whether the values of the properties **user\_index\_alias** and **org\_index\_alias** is with respect to the same cassandra table name in your local system.\
\
2.3 If the above two are correct and still elastic search is not connecting then sometimes the elastic search might take a little time to respond so go to, **\<Project base path>/sunbird-lms-service/core/es-utils/src/main/java/org/sunbird/common/ElasticSearchHelper.java**

#### Pre-required Configuration to Make User/Org service Completely working:

Creating a new custodian/root organisation is mandatory. so please ensure you get a <mark style="color:green;">**200 OK**</mark> response after creation.

```json
// To create a new Organisation

{
    "request": {
        "orgName": "localrootorg",
        "channel": "Channel",
        "description": "Description",
        "externalId": "localrootorg",
        "email": "info@org.org",
        "isSSOEnabled": true,
        "organisationType": "school",
        "isTenant": true
    }
}
```

```json
// Curl command to create a new Organisation in your local system
// ensure both of your cassandra and es is up and running

curl --location --request POST 'localhost:9000/v1/org/create' \
--header 'Content-Type: application/json' \
--data-raw '{
    "request": {
        "orgName": "localrootorg",
        "channel": "Channel",
        "description": "Description",
        "externalId": "localrootorg",
        "email": "info@org.org",
        "isSSOEnabled": true,
        "organisationType": "school",
        "isTenant": true
    }
}'
```

\
Use below **request body/curl** to setup the pre-required system settings like **custodian channel**, **custodian org id** , **user profile config** and **org profile config.**Please ensure you get a <mark style="color:green;">**200 OK**</mark> response after creation.

{% code overflow="wrap" %}
```json
// to set custodian channel
//Here the "value" column is given as Channel which is to be replaced with the Channel id which was given from your respective system's ORG CREATE request
{
    "request": {
        "id": "custodianOrgChannel",
        "field": "custodianOrgChannel",
        "value": "Channel"
    }
}
```
{% endcode %}

```json
//curl command to set custodian channel in local
//Here the "value" column is given as Channel which is to be replaced with the Channel id which was given from your respective system's ORG CREATE request

curl --location --request POST 'localhost:9000/v1/system/settings/set' \
--header 'Content-Type: application/json' \
--data-raw '{
    "request": {
        "id": "custodianOrgChannel",
        "field": "custodianOrgChannel",
        "value": "Channel"
    }
}'
```

{% code overflow="wrap" %}
```json
// to set custodian org id
//Here the "value" column is given as 0137038836873134080 which is to be replaced with the id generated from your respective system's ORG CREATE response

{
    "request": {
        "id": "custodianOrgId",
        "field": "custodianOrgId",
        "value": "0137038836873134080"
    }
}
```
{% endcode %}

{% code overflow="wrap" %}
```json
//curl command to set custodian org id in local
//Here the "value" column is given as 0137038836873134080 which is to be replaced with the id generated from your local system's ORG CREATE response

curl --location --request POST 'localhost:9000/v1/system/settings/set' \
--header 'Content-Type: application/json' \
--data-raw '{
    "request": {
        "id": "custodianOrgId",
        "field": "custodianOrgId",
        "value": "0137038836873134080"
    }
}'
```
{% endcode %}

{% code overflow="wrap" %}
```json
// to set User Profile Config

{
    "request": {
        "id": "userProfileConfig",
        "field": "userProfileConfig",
        "value": "{\"fields\":[\"firstName\",\"lastName\",\"profileSummary\",\"avatar\",\"countryCode\",\"dob\",\"email\",\"gender\",\"grade\",\"language\",\"location\",\"phone\",\"subject\",\"userName\",\"webPages\",\"jobProfile\",\"address\",\"education\",\"skills\",\"badgeAssertions\"],\"publicFields\":[\"firstName\",\"lastName\",\"profileSummary\",\"userName\"],\"privateFields\":[\"email\",\"phone\"],\"csv\":{\"supportedColumns\":{\"NAME\":\"firstName\",\"MOBILE PHONE\":\"phone\",\"EMAIL\":\"email\",\"SCHOOL ID\":\"orgId\",\"USER_TYPE\":\"userType\",\"ROLES\":\"roles\",\"USER ID\":\"userId\",\"SCHOOL EXTERNAL ID\":\"orgExternalId\"},\"outputColumns\":{\"userId\":\"USER ID\",\"firstName\":\"NAME\",\"phone\":\"MOBILE PHONE\",\"email\":\"EMAIL\",\"orgId\":\"SCHOOL ID\",\"orgName\":\"SCHOOL NAME\",\"userType\":\"USER_TYPE\",\"orgExternalId\":\"SCHOOL EXTERNAL ID\"},\"outputColumnsOrder\":[\"userId\",\"firstName\",\"phone\",\"email\",\"organisationId\",\"orgName\",\"userType\",\"orgExternalId\"],\"mandatoryColumns\":[\"firstName\",\"userType\",\"roles\"]},\"read\":{\"excludedFields\":[\"avatar\",\"jobProfile\",\"address\",\"education\",\"webPages\",\"skills\"]},\"framework\":{\"fields\":[\"board\",\"gradeLevel\",\"medium\",\"subject\",\"id\"],\"mandatoryFields\":[\"id\"]}}"
    }
}
```
{% endcode %}

{% code overflow="wrap" %}
```json
//Curl command for setting the user profile configuration in local environment

curl --location --request POST 'localhost:9000/v1/system/settings/set' \
--header 'Content-Type: application/json' \
--data-raw '{
    "request": {
        "id": "userProfileConfig",
        "field": "userProfileConfig",
        "value": "{\"fields\":[\"firstName\",\"lastName\",\"profileSummary\",\"avatar\",\"countryCode\",\"dob\",\"email\",\"gender\",\"grade\",\"language\",\"location\",\"phone\",\"subject\",\"userName\",\"webPages\",\"jobProfile\",\"address\",\"education\",\"skills\",\"badgeAssertions\"],\"publicFields\":[\"firstName\",\"lastName\",\"profileSummary\",\"userName\"],\"privateFields\":[\"email\",\"phone\"],\"csv\":{\"supportedColumns\":{\"NAME\":\"firstName\",\"MOBILE PHONE\":\"phone\",\"EMAIL\":\"email\",\"SCHOOL ID\":\"orgId\",\"USER_TYPE\":\"userType\",\"ROLES\":\"roles\",\"USER ID\":\"userId\",\"SCHOOL EXTERNAL ID\":\"orgExternalId\"},\"outputColumns\":{\"userId\":\"USER ID\",\"firstName\":\"NAME\",\"phone\":\"MOBILE PHONE\",\"email\":\"EMAIL\",\"orgId\":\"SCHOOL ID\",\"orgName\":\"SCHOOL NAME\",\"userType\":\"USER_TYPE\",\"orgExternalId\":\"SCHOOL EXTERNAL ID\"},\"outputColumnsOrder\":[\"userId\",\"firstName\",\"phone\",\"email\",\"organisationId\",\"orgName\",\"userType\",\"orgExternalId\"],\"mandatoryColumns\":[\"firstName\",\"userType\",\"roles\"]},\"read\":{\"excludedFields\":[\"avatar\",\"jobProfile\",\"address\",\"education\",\"webPages\",\"skills\"]},\"framework\":{\"fields\":[\"board\",\"gradeLevel\",\"medium\",\"subject\",\"id\"],\"mandatoryFields\":[\"id\"]}}"
    }
}'
```
{% endcode %}

{% code overflow="wrap" %}
```json
// to set org profile config 

{
    "request": {
        "id": "orgProfileConfig",
        "field": "orgProfileConfig",
        "value": "{\"csv\":{\"supportedColumns\":{\"SCHOOL NAME\":\"orgName\",\"BLOCK CODE\":\"locationCode\",\"STATUS\":\"status\",\"SCHOOL ID\":\"organisationId\",\"EXTERNAL ID\":\"externalId\",\"DESCRIPTION\":\"description\",\"ORGANISATION TYPE\":\"organisationType\"}, \"outputColumns\": {\"organisationId\":\"SCHOOL ID\",\"orgName\":\"SCHOOL NAME\",\"locationCode\":\"BLOCK CODE\",\"locationName\":\"BLOCK NAME\",\"externalId\":\"EXTERNAL ID\",\"organisationType\":\"ORGANISATION TYPE\"}, \"outputColumnsOrder\":[\"organisationId\",\"orgName\",\"locationCode\", \"locationName\",\"externalId\",\"organisationType\"],\"mandatoryColumns\":[\"orgName\",\"locationCode\",\"status\",\"organisationType\"]}}"
    }
}
```
{% endcode %}

{% code overflow="wrap" %}
```json
//Curl command for setting the org profile configuration in local environment

curl --location --request POST 'localhost:9000/v1/system/settings/set' \
--header 'Content-Type: application/json' \
--data-raw '{
    "request": {
        "id": "orgProfileConfig",
        "field": "orgProfileConfig",
        "value": "{\"csv\":{\"supportedColumns\":{\"SCHOOL NAME\":\"orgName\",\"BLOCK CODE\":\"locationCode\",\"STATUS\":\"status\",\"SCHOOL ID\":\"organisationId\",\"EXTERNAL ID\":\"externalId\",\"DESCRIPTION\":\"description\",\"ORGANISATION cTYPE\":\"organisationType\"}, \"outputColumns\": {\"organisationId\":\"SCHOOL ID\",\"orgName\":\"SCHOOL NAME\",\"locationCode\":\"BLOCK CODE\",\"locationName\":\"BLOCK NAME\",\"externalId\":\"EXTERNAL ID\",\"organisationType\":\"ORGANISATION TYPE\"}, \"outputColumnsOrder\":[\"organisationId\",\"orgName\",\"locationCode\", \"locationName\",\"externalId\",\"organisationType\"],\"mandatoryColumns\":[\"orgName\",\"locationCode\",\"status\",\"organisationType\"]}}"
    }
}'
```
{% endcode %}



Once the setup done, create user using below APIs

{% embed url="http://docs.sunbird.org/latest/apis/userapi" %}
