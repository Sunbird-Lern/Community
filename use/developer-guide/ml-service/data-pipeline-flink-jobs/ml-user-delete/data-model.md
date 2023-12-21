# Data Model

### Sample Kafka Event

<pre><code><strong>{
</strong>  "eid": "BE_JOB_REQUEST",
  "ets": 1669196680963,
  "mid": "LP.1669196680963.0e6ac196-e57d-40bb-ab39-f5ec479da3e6",
  "actor": {
    "id": "Sunbird Flink Job",
    "type": "System"
  },
  "context": {
    "pdata": {
      "ver": "1.0",
      "id": "org.sunbird.platform"
    },
    "channel": "01309282781705830427",
    "env": "sunbirdstaging"
  },
  "object": {
    "ver": "1669196652993",
    "id": "02c4e0dc-3e25-4f7d-b811-242c73e24a01"
  },
  "edata": {
    "action": "delete-user",
    "iteration": 1,
    "userId": "5deed393-6e04-449a-b98d-7f0fbf88f22e",
    "organisationId": "01309282781705830427"
  }
}
</code></pre>

### Mongo DB Update Logic

The following collections from the database **ml-service** will be updated in order to fully remove user PII data from mongoDB.

* observations&#x20;
* surveySubmissions&#x20;
* observationSubmissions&#x20;
* projects&#x20;
* programUsers
* solutions

## Observations

The following [table fields](data-model.md#table-fields) from the observation collection will be updated when **createdBy** key in observation collection is equal to the Kafka event **userId**.&#x20;

## surveySubmissions

The following [table fields](data-model.md#table-fields) from the surveySubmissions collection will be updated when **createdBy** key in surveySubmissions collection is equal to the Kafka event **userId**.&#x20;

## projects

The following [table fields](data-model.md#table-fields) from the projects collection will be updated when **userId** key in projects collection is equal to the Kafka event **userId**.&#x20;

## programUsers

The following [table fields](data-model.md#table-fields) from the programUsers collection will be updated when **userId** key in programUsers collection is equal to the Kafka event **userId**.&#x20;

#### Table fields

<table data-full-width="true"><thead><tr><th>Key</th><th>Value</th></tr></thead><tbody><tr><td>userProfile.firstName</td><td>Deleted User</td></tr><tr><td>userProfile.lastName</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.dob</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.email</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.maskedEmail</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.recoveryEmail</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.prevUsedEmail</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.encEmail</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.phone</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.maskedPhone</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.recoveryPhone</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.prevUsedPhone</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.encPhone</td><td>This key will be unset (deleted)</td></tr></tbody></table>

## solutions

The following fields from the solutions collection will be updated when **author** key in solutions collection is equal to the Kafka event **userId**.&#x20;

| Key             | Value        |
| --------------- | ------------ |
| creator         | Deleted User |
| license.author  | Deleted User |
| license.creator | Deleted User |

## observationSubmissions

The following fields from the observationSubmissions collection will be updated when **createdBy** key in observation collection is equal to the Kafka event **userId**.&#x20;

<table data-full-width="true"><thead><tr><th>Key</th><th>Value</th></tr></thead><tbody><tr><td>userProfile.firstName</td><td>Deleted User</td></tr><tr><td>observationInformation.userProfile.firstName</td><td>Deleted User</td></tr><tr><td>userProfile.lastName</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.dob</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.email</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.maskedEmail</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.recoveryEmail</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.prevUsedEmail</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.encEmail</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.phone</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.maskedPhone</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.recoveryPhone</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.prevUsedPhone</td><td>This key will be unset (deleted)</td></tr><tr><td>userProfile.encPhone</td><td>This key will be unset (deleted)</td></tr><tr><td>observationInformation.userProfile.lastName</td><td>This key will be unset (deleted)</td></tr><tr><td>observationInformation.userProfile.dob</td><td>This key will be unset (deleted)</td></tr><tr><td>observationInformation.userProfile.email</td><td>This key will be unset (deleted)</td></tr><tr><td>observationInformation.userProfile.maskedEmail</td><td>This key will be unset (deleted)</td></tr><tr><td>observationInformation.userProfile.recoveryEmail</td><td>This key will be unset (deleted)</td></tr><tr><td>observationInformation.userProfile.prevUsedEmail</td><td>This key will be unset (deleted)</td></tr><tr><td>observationInformation.userProfile.encEmail</td><td>This key will be unset (deleted)</td></tr><tr><td>observationInformation.userProfile.phone</td><td>This key will be unset (deleted)</td></tr><tr><td>observationInformation.userProfile.maskedPhone</td><td>This key will be unset (deleted)</td></tr><tr><td>observationInformation.userProfile.recoveryPhone</td><td>This key will be unset (deleted)</td></tr><tr><td>observationInformation.userProfile.prevUsedPhone</td><td>This key will be unset (deleted)</td></tr><tr><td>observationInformation.userProfile.encPhone</td><td>This key will be unset (deleted)</td></tr></tbody></table>
