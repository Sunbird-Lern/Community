# Ownership Transfer Flink Job

The **`UserOwnershipTransferFunction`** job facilitates the transfer of course batch ownership from one user to another. It achieves this by performing database and search updates to ensure consistent data. The job interacts with several data sources, including Cassandra and Elasticsearch, to locate the relevant information and update it accordingly. Here's what the job does in simpler terms:

* **Identify Ownership Transfers**:
  * This job takes an event indicating an ownership transfer between users.
  * It processes the event to determine the source user (`fromUserId`) and the target user (`toUserId`).
* **Database Operations**:
  * It connects to Cassandra and retrieves information about course batches created by the source user and where they act as a mentor.
  * The job creates Cassandra update queries to change the ownership from the source user to the target user in the appropriate fields.
  * It executes these updates in batches to ensure efficient processing.
* **Search Operations**:
  * It interacts with Elasticsearch to find the corresponding course batch documents.
  * The job updates the documents to reflect the new ownership, replacing the source user with the target user in the appropriate fields.
* **Metrics and Logging**:
  * The job maintains metrics to track the number of processed events, successful operations, and database updates.
  * It logs detailed information for auditing and error handling.

In summary, this job facilitates the smooth transfer of course ownership, updating relevant data in multiple locations to maintain consistency across the system. It plays a crucial role in ensuring that the information in both the database and search systems accurately reflects the ownership transfer.\
\
**Configuration variables:**

| Variable                            | Default value                                          | purpose                                                                                                                                                                                                             |
| ----------------------------------- | ------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| kafka.input.topic                   | \{{env\}}.user.ownership.transfer                      | Kafka topic from which messages/events are read to be processed                                                                                                                                                     |
| kafka.groupId                       | \{{env\}}-user-ownership-transfer-group                | Kafka input topic group Id                                                                                                                                                                                          |
| lms-cassandra.keyspace              | sunbird\_courses                                       | Cassandra keyspace name                                                                                                                                                                                             |
| lms-cassandra.course\_batch.table   | course\_batch                                          | Cassandra table used to store batch details of a collection. Batch status, start date , end date , batch enrolment end date, enrolment type (open/invite-only), certificate templates etc are stored in this table. |
| threshold.batch.write.size          | 10                                                     | Property used to specify batch size of the database update queries while updating a specific cassandra table in batch format                                                                                        |
| service.lms.basePath                | [https://dev.sunbirded.org](https://dev.sunbirded.org) | lms base url                                                                                                                                                                                                        |
| service.userorg.basePath            | [https://dev.sunbirded.org](https://dev.sunbirded.org) | User-Org service URL                                                                                                                                                                                                |
| user\_read\_api                     | /private/user/v1/read/                                 | API route for fetching user profile details                                                                                                                                                                         |
| batch\_search\_api                  | /v1/course/batch/search                                | API route for fetching batch details                                                                                                                                                                                |
| user.ownership.transfer.parallelism | 1                                                      | Degree of parallelism for the user ownership                                                                                                                                                                        |

**Sample event:**

```json
{
    "eid": "BE_JOB_REQUEST",
    "ets": 1712750750956,
    "mid": "LP.1712750750956.07a0a24d-37ef-462c-a614-b76ad2a6a6ac",
    "actor": {
        "type": "System",
        "id": "ownership-transfer"
    },
    "context": {
        "pdata": {
            "ver": "1.0",
            "id": "org.sunbird.platform"
        }
    },
    "object": {
        "type": "user",
        "id": "72d8cd69-2469-4234-82e7-6b849e0a28d9"
    },
    "edata": {
        "organisationId": "01394517023437619214_1111",
        "actionBy": {
            "userId": "ad8c3adf-2447-4559-af15-f6d1057a0b8a",
            "userName": "gtest-user-007"
        },
        "context": "User Deletion",
        "action": "ownership-transfer",
        "fromUserProfile": {
            "userId": "72d8cd69-2469-4234-82e7-6b849e0a28d9",
            "userName": "gtest-user-005",
            "channel": "",
            "organisationId": "",
            "roles": [
                "BOOK_CREATOR",
                "CONTENT_CREATOR"
            ]
        },
        "iteration": 1,
        "assetInformation": {
            "name": "TestContent",
            "identifier": "do_123",
            "primaryCategory": "Practice Question Set",
            "objectType": "QuestionSet"
        },
        "toUserProfile": {
            "userId": "4c009ce1-b069-4d27-879b-605c55ff4ef9",
            "userName": "gtest-user-006",
            "firstName": "G-Test",
            "lastName": "User-006",
            "roles": [
                "BOOK_CREATOR",
                "CONTENT_CREATOR"
            ]
        }
    }
}
```

**Source code:**

{% embed url="https://github.com/Sunbird-Lern/data-pipeline/tree/release-8.0.0/user-org-jobs/user-ownership-transfer" %}
