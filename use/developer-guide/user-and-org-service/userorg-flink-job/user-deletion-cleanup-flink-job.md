# User Deletion Cleanup Flink Job

The **`UserDeletionCleanupFunction`** job handles the cleanup and deletion of user-related data from various storage systems when users are deleted. It ensures that all related information is removed or masked appropriately in multiple data sources, including Cassandra and Keycloak. Here's what the job does in simpler terms:

* **Identify User Deletion Events**:
  * The job listens for events indicating that a user is to be deleted.
  * It retrieves user information from a user organization service to validate the deletion event.
* **Keycloak User Removal**:
  * The job connects to Keycloak to remove the user credentials.
  * If removal fails, it masks sensitive information (e.g., email, phone) to ensure user data is not exposed.
* **Database Operations**:
  * The job connects to Cassandra and updates the user lookup table to remove entries related to the user (like email, phone, external ID, and username).
  * It updates the main user table in Cassandra to reflect the deletion status by clearing or masking personal information.
  * It also removes user entries from the external identity table in Cassandra.
  * The job updates the organization table to mark the user as deleted and record the date of deletion.
* **Audit Events and Logging**:
  * The job generates audit events to track the cleanup process for telemetry and auditing purposes.
  * It logs detailed information during the deletion process for troubleshooting and error handling.

In summary, this job ensures that when a user is deleted, all related data is appropriately removed or masked across multiple storage systems, maintaining data privacy and consistency. It plays a crucial role in the cleanup process, ensuring that user data is properly handled upon deletion.

### **Configuration Variables:**

| Variable                                          | Default value                                     | purpose                                                         |
| ------------------------------------------------- | ------------------------------------------------- | --------------------------------------------------------------- |
| kafka.input.topic                                 | \{{env\}}.delete.user                             | Kafka topic from which messages/events are read to be processed |
| kafka.groupId                                     | \{{env\}}-delete-user-group                       | Kafka input topic group Id                                      |
| user.keyspace                                     | sunbird                                           | Cassandra keyspace name                                         |
| user.lookup.table                                 | user\_lookup                                      | Cassandra table used to store user lookup data                  |
| user.table                                        | user                                              | Cassandra table used to store user details                      |
| user.externalIdentity.table                       | usr\_external\_identity                           | Cassandra table used to store user extrenal identity details    |
| user.org.table                                    | user\_organisation                                | Cassandra table used to store organisation details              |
| service.lms.basePath                              |                                                   | lms base url                                                    |
| service.userorg.basePath                          |                                                   | User-Org service URL                                            |
| sunbird\_keycloak\_user\_federation\_provider\_id | sunbird\_keycloak\_user\_federation\_provider\_id | fedaration provider id for key cloak.                           |
| user\_read\_api                                   |                                                   | API route for fetching user profile details                     |
| batch\_search\_api                                |                                                   | API route for fetching batch details                            |
| user.ownership.transfer.parallelism               | 1                                                 | Degree of parallelism for the user ownership                    |

### **Sample event:**

```json
{
  "eid": "BE_JOB_REQUEST",
  "ets": 1619527882745,
  "mid": "LP.1619527882745.32dc378a-430f-49f6-83b5-bd73b767ad36",
  "actor": {
    "id": "delete-user",
    "type": "System"
  },
  "context": {
    "pdata": {
      "id": "org.sunbird.platform",
      "ver": "1.0"
    }
  },
  "object": {
    "id": "<deleted-userId>",
    "type": "User"
  },
  "edata": {
    "organisationId": "<organisationId>"
    "userId": "<deleted-userId>",
    "suggested_users": [
    	{
    		"role": "ORG_ADMIN",
    		"users": ["<orgAdminUserId>"]
    	},
    	{
    		"role": "CONTENT_CREATOR",
    		"users": ["<contentCreatorUserId>"]
    	},
    	{
    		"role": "COURSE_MENTOR",
    		"users": ["<courseMentorUserId>"]
    	}
    ],
    "action": "delete-user",
    "iteration": 1
  }
}
```
