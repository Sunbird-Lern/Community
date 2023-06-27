# Program Flink Job

### Program User Info Job

'program-user-info' is used to record the user's information when the user submits the program. Whenever a program is submitted, this job receives an event with the user's information as JSON data and then it parses and stores it as respective key-value pairs in Cassandra.

<figure><img src="../../../.gitbook/assets/programUser_Flink-Page-1 (1).jpg" alt=""><figcaption></figcaption></figure>

Additional Reading: [https://project-sunbird.atlassian.net/wiki/spaces/AN/pages/3266675098/Cassandra+Approach+for+PII+data](https://project-sunbird.atlassian.net/wiki/spaces/AN/pages/3266675098/Cassandra+Approach+for+PII+data)

**Configuration variables:**

<table><thead><tr><th width="246">Variable</th><th>Default Value</th><th>Purpose</th></tr></thead><tbody><tr><td>kafka.input.topic</td><td>{{env}}.programuser.info</td><td>Kafka topic from which messages/events are read to be processed.</td></tr><tr><td>kafka.groupId</td><td>{{env}}-programuser-group</td><td>Kafka input topic group Id</td></tr><tr><td>ml-cassandra.keyspace</td><td>sunbird_programs</td><td>Cassandra keyspace name</td></tr><tr><td>ml-cassandra.table</td><td>program_enrollment</td><td>Cassandra table used to store user data</td></tr></tbody></table>

**Sample event:**

```json
{
    "_id" : "63bfa8f173f6368ebde21bbe",
    "deleted" : false,
    "programId" : "5f362b78af0a4decfa9a106f",
    "programName": "$prorgramName",
    "programExternalId": "$programExternalId",
    "requestForPIIConsent":true,
    "userRoleInformation" : {
        "role" : "HM,DEO",
        "state" : "db331a8c-b9e2-45f8-b3c0-7ec1e826b6df",
        "district" : "1dcbc362-ec4c-4559-9081-e0c2864c2931",
        "school" : "c5726207-4f9f-4f45-91f1-3e9e8e84d824"
    },
    "userId" : "ba9aa220-ff1b-4717-b6ea-ace55f04fc16",
    "appInformation" : {
        "appName" : "Diksha",
        "appVersion" : "5.2"
    },
    "userProfile": {
      "userLocations" :[
        {
          "code" : "2822",
          "name" : "ANANTAPUR",
          "id" : "2f76dcf5-e43b-4f71-a3f2-c8f19e1fce03",
          "type" : "district",
          "parentId" : "bc75cc99-9205-463e-a722-5326857838f8"
        },
        {
          "code" : "282262",
          "name" : "AGALI",
          "id" : "966c3be4-c125-467d-aaff-1eb1cd525923",
          "type" : "block",
          "parentId" : "2f76dcf5-e43b-4f71-a3f2-c8f19e1fce03"
        },
        {
          "code" : "28",
          "name" : "Andhra Pradesh",
          "id" : "bc75cc99-9205-463e-a722-5326857838f8",
          "type" : "state",
          "parentId" : null
        },
        {
          "code" : "2822620004",
          "name" : "ZPHS AGALI",
          "id" : "beb0bcf4-d7cd-4a72-8f35-be8e5b03c0d1",
          "type" : "cluster",
          "parentId" : "966c3be4-c125-467d-aaff-1eb1cd525923"
        },
        {
          "code" : "28226200816",
          "name" : "SMT PRAMEELAMMA AND SRI KGA GUPTA EM UP SCHOOL",
          "id" : "01337588247832985613211",
          "type" : "school",
          "parentId" : ""
        }
      ],
      "profileUserTypes": [
        {
          "subType" : "deo",
          "type" : "administrator"
        }
       ],
      "framework" : {
        "board" : [ 
          "CBSE"
        ],
        ...
      },
      ...
      "rootOrg":{
      "id": "0126796199493140480",
      "orgName": "Staging Custodian Organization"
      },
    },
    "noOfResourcesStarted": 3,
    "updatedAt" : ISODate("2023-01-12T06:30:56.829Z"),
    "createdAt" : ISODate("2023-01-12T06:30:09.476Z"),
    "__v" : 0
}
```

**Source code:**

{% embed url="https://github.com/Sunbird-Lern/data-pipeline/tree/release-5.3.0/ml-jobs/program-user-info" %}
