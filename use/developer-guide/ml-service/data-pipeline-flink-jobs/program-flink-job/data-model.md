# Data Model

### Sample Kafka Event

```
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
           "type": "administrator",
           "subType": "hm"
        },
        {
           "type": "administrator",
           "subType": "crp"
         },
         {
            "type": "administrator",
            "subType": "chm"
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

### DB Schema

The schema serves as a blueprint for creating and maintaining the Cassandra database that supports the Program User Info Services data storage and retrieval operations under sunbird\_programs keyspace.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-08-14 at 6.41.25 PM.png" alt="" width="321"><figcaption></figcaption></figure>

#### An example of _program\_enrollment_ table under _sunbird\_programs_ keyspace

<table><thead><tr><th width="157">program_id</th><th width="158">user_id</th><th width="140">created_at</th><th width="152">organisation_id</th><th width="185">organisation_name</th><th width="187">pii_consent_required</th><th width="181">program_externalid</th><th width="144">program_name</th><th width="127">updated_at</th><th width="372">user_locations</th><th width="154">user_sub_type</th><th>user_type</th></tr></thead><tbody><tr><td>5f362b78af0a4decfa9a106f</td><td>ba9aa220-ff1b-4717-b6ea-ace55f04f11</td><td>2022-01-12</td><td>0126796199493140480</td><td>Staging Custodian Organization</td><td>True</td><td>0126796199493140480</td><td>Staging Custodian</td><td>2023-01-12</td><td>{'block_code': '282262', 'block_id': '966c3be4-c125-467d-aaff-1eb1cd525923', 'block_name': 'AGALI', 'cluster_code': '2822620004', 'cluster_id': 'beb0bcf4-d7cd-4a72-8f35-be8e5b03c0d1', 'cluster_name': 'ZPHS AGALI', 'district_code': '2822', 'district_id': '2f76dcf5-e43b-4f71-a3f2-c8f19e1fce03', 'district_name': 'ANANTAPUR', 'school_code': '28226200816', 'school_id': '01337588247832985613211', 'school_name': 'SMT PRAMEELAMMA AND SRI KGA GUPTA EM UP SCHOOL', 'state_code': '28', 'state_id': 'bc75cc99-9205-463e-a722-5326857838f8', 'state_name': 'Andhra Pradesh'}</td><td>deo</td><td>administrator</td></tr></tbody></table>
