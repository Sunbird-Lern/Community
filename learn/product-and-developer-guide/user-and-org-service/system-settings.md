# System Settings

This page explains how a System Administrator can configure some settings in the system for different purposes.

#### Configurable Parameters <a href="#configurable-parameters" id="configurable-parameters"></a>

| S NO. | PARAMETER            | DESCRIPTION                                                                                     | EXAMPLE |
| ----- | -------------------- | ----------------------------------------------------------------------------------------------- | ------- |
| 1     | custodianOrgChannel  | set default channel into system. The self sign-up or Google sign up user are under this channel | sunbird |
| 2     | custodianRootOrgId   | set org id of custodianOrgChannel created earlier                                               |         |
| 3     | contentComingSoonMsg | message for the rootOrgs whose content is being created or they don’t have content yet          |         |
| 4     | courseFrameworkId    | framework ID for course creation, this framework needs to be created first                      | TPD     |
| 5     | tncConfig            | terms and condition page                                                                        |         |
| 6     | consumptionFaqs      | public page url for consumption FAQ                                                             |         |

### Read Values that are Already Set <a href="#read-values-that-are-already-set" id="read-values-that-are-already-set"></a>

Use the following curl command to check the value that is already set for a particular parameter. Replace the value in the {key} with the required ID. The key refers to the ID to be configured using the cURL command.

```
  curl -X GET \
  /data/v1/system/settings/get/{key} \
  -H 'Authorization: Bearer ' \
  -H 'Content-Type: application/json'
```

\
Configure Custodian Channel

Configure the Sunbird LMS custodian channel ID using the following cURL command.

```
  curl -X POST \
  /data/v1/system/settings/set \
  -H 'Authorization: Bearer ' \
  -H 'Content-Type: application/json' \
  -H 'X-Authenticated-User-Token: ' \
  -d '{
  "request": {
                "id": "custodianOrgChannel",
                "field": "custodianOrgChannel",
                "value": ""
            }
}'

```

### Configure Custodian Org ID <a href="#configure-custodian-org-id" id="configure-custodian-org-id"></a>

Configure the Sunbird LMS custodian Org ID using the following cURL command. Use the Org ID for the custodian channel set earlier. The custodian channel ID and the custodian Org ID work as a pair.

```
  curl -X POST \
  /data/v1/system/settings/set \
  -H 'Authorization: Bearer ' \
  -H 'Content-Type: application/json' \
  -H 'X-Authenticated-User-Token: ' \
  -d '{
  "request": {
                "id": "custodianRootOrgId",
                "field": "custodianRootOrgId",
                "value": ""
            }
}'

```

### Configure the Content Coming Soon Page <a href="#configure-the-content-coming-soon-page" id="configure-the-content-coming-soon-page"></a>

Configure the message on the Content Coming Soon page using the following cURL command. This message is used by those root organizations that do not have any content, as on date.

```
  curl -X POST \
  /data/v1/system/settings/set \
  -H 'Authorization: Bearer ' \
  -H 'Content-Type: application/json' \
  -H 'X-Authenticated-User-Token: ' \
  -d '{
  "request": {
                "id": "contentComingSoonMsg",
                "field": "contentComingSoonMsg",
                "value": "[{\"rootOrgId\":\"{RootOrgId}\",\"value\":\"Org specific coming soon message\",\"translations\":\"{\\\"en\\\":\\\"Coming soon message\\\"}\"}\"}]"
            }
}'

```

### Configure Course Framework ID <a href="#configure-course-framework-id" id="configure-course-framework-id"></a>

Configure the Sunbird LMS Course Framework ID using the following cURL command. Create the same framework in the Knowledge Platform sub system.

```
  curl -X POST \
  /data/v1/system/settings/set \
  -H 'Authorization: Bearer ' \
  -H 'Content-Type: application/json' \
  -H 'X-Authenticated-User-Token: ' \
  -d '{
  "request": {
                "id": "courseFrameworkId",
                "field": "courseFrameworkId",
                "value": ""
            }
}'

```

### Configure the Terms and Conditions page <a href="#configure-the-terms-and-conditions-page" id="configure-the-terms-and-conditions-page"></a>

Configure the Sunbird LMS Terms and Conditions page configuration using the following cURL command.

```
  curl -X POST \
  /data/v1/system/settings/set \
  -H 'Authorization: Bearer ' \
  -H 'Content-Type: application/json' \
  -H 'X-Authenticated-User-Token: ' \
  -d '{
  "request": {
                "id": "tncConfig",
                "field": "tncConfig",
                "value": "{"latestVersion":"v1","v1":{"url":"{public url for config html page}"}}"
            }
}'

```

### Configure FAQs for User Consumption <a href="#configure-faqs-for-user-consumption" id="configure-faqs-for-user-consumption"></a>

Confifure the Sunbird LMS FAQs for users using the following cURL command.

```
  curl -X POST \
  /data/v1/system/settings/set \
  -H 'Authorization: Bearer ' \
  -H 'Content-Type: application/json' \
  -H 'X-Authenticated-User-Token: ' \
  -d '{
  "request": {
                "id": "consumptionFaqs",
                "field": "consumptionFaqs",
                "value": "{consumption faq public html page url}"
            }
}'
```

\
