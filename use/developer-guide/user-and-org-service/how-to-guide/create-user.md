# Create User

### Scenario <a href="#scenario" id="scenario"></a>

A company, XYZ Corp, is a global conglomerate with over ten thousand employees, spread across 5 locations. Employee training and enablement is one of the core values of the organisation. To ensure that employees are regularly trained and up-skilled, XYZ Corp has decided to use Sunbird for its learning and training solution on 3 topics, namely Life Science, eCommerce and Archaeology (Indian, Greek, Mayan). Gita is the XYZ Corp’s Sunbird administrator and has created the necessary structure (root organisation called Archaeology and sub-organisations - Indian Archaeology, Mayan Archaeology and Greek Archaeology). She needs to create user(s) within this root organisation and assign specific roles such as write research articles, review, publish.

#### Taskflow <a href="#taskflow" id="taskflow"></a>

For each user to be created, Gita needs to prepare the API request headers and body, as shown in the example below and invoke the API. Upon successful completion, she notes down the **userID** of each one respectively.

**Request Header**

| HEADER        | TYPE   | DESCRIPTION                | SAMPLE                                                         |
| ------------- | ------ | -------------------------- | -------------------------------------------------------------- |
| Content-type  | String | Mime type of the request   | application/json                                               |
| Authorization | String | Authorization key received | abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890 |

**Request Body**

```
  curl -X POST \
https://staging.open-sunbird.org/api/user/v1/create \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890' \
-d '{
        "request":
        {
        "email": "writer01@xyzcorp.com",
        "firstName": "writer01",
        "password": "writer12301",
        "channel": "xyzCorpLifeArcheologyChannel",
        }
    }'

```

**Response Body**

```
  {
    "id": "api.user.create",
    "ver": "v1",
    "ts": "2018-11-12 16:25:43:292+0000",
    "params": {
        "resmsgid": null,
        "msgid": "93cd9372-62aa-43dd-91a0-fe43db2c218b",
        "err": null,
        "status": "success",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "response": "SUCCESS",
        "userId": "bd25215d-663e-4c78-49ef-4c2331e814cd"
    }
}

```

This concludes the topic of creating users in an organisation, in a Sunbird instance. Typically, the next activity would be to assign roles to these users, within their organisations.

#### Concepts Covered <a href="#concepts-covered" id="concepts-covered"></a>

**User**: These are entities created within an organisation, who can login into their Sunbird portal and perform tasks that are specifically assigned to them. Users cannot have the same email ID. In the absence of an email ID, a unique phone number must be provided in the request.

During user creation, if the **channel** is not provided, Sunbird attempt to create that user in the existing default organisation.
