# Flink Jobs

Notification Service has a flink job which helps in sending asynchronous notifications.

### Notification Job

'notification-job' is used to send notifications in an asynchronous mode via SMS, eMail and FCM channels.

Additional Reading: [https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/1057980431/Notification+service](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/1057980431/Notification+service)

**Configuration variables:**

<table><thead><tr><th width="246">Variable</th><th>Default Value</th><th>Purpose</th></tr></thead><tbody><tr><td>kafka.input.topic</td><td>{{env}}.lms.notification</td><td>Kafka topic from which messages/events are read to be processed.</td></tr><tr><td>kafka.groupId</td><td>{{env}}.lms.notification.group</td><td>Kafka input topic group Id</td></tr><tr><td>fcm_account_key</td><td></td><td>Firebase Cloud Messaging</td></tr><tr><td>sms_auth_key</td><td></td><td>SMS Service Authentication key</td></tr><tr><td>sms_default_sender</td><td></td><td>SMS sender name (it must be 6 character only)</td></tr><tr><td>mail_server_from_email</td><td></td><td>eMail Server</td></tr><tr><td>mail_server_username</td><td></td><td>eMail server username</td></tr><tr><td>mail_server_password</td><td></td><td>eMail server password</td></tr><tr><td>mail_server_host</td><td></td><td>eMail server host Ip</td></tr><tr><td>mail_server_port</td><td></td><td>eMail server port</td></tr></tbody></table>

**Sample event:**

```json
SAMPLE EVENT 1:
{
  "actor": {
    "id": "BroadCast Topic Notification",
    "type": "System"
  },
  "eid": "BE_JOB_REQUEST",
  "edata": {
    "request": {
      "notification": {
        "config": {
          "sender": "support@sunbird.com",
          "subject": "Completion certificate"
        },
        "deliveryType": "message",
        "mode": "email",
        "template": {
          "data": "Hi",
          "params": {
            "body": "email body",
            "stateImgUrl": "https://sunbirddev.blob.core.windows.net/orgemailtemplate/img/File-0128212938260643843.png",
            "firstName": "Hari",
            "regards": "Minister of Humar Resources",
            "TraningName": "test-cert-notification",
            "regardsperson": "Chairperson",
            "heldDate": "16-12-2019"
          }
        },
        "ids": [
          "harip@test.in"
        ]
      }
    },
    "action": "broadcast-topic-notification-all",
    "iteration": 2
  },
  "trace": {
    "X-Request-ID": null,
    "X-Trace-Enabled": "false"
  },
  "context": {
    "pdata": {
      "ver": "1.0",
      "id": "org.sunbird.platform"
    }
  },
  "mid": "NS.1646230422793.70c10f26-631b-4d55-8aaa-fbe52b79cbc1",
  "object": {
    "id": "93a06b829d13c9fa797ea641f484e5d38ce28868fbd75014852cbe413515177c",
    "type": "TopicNotifyAll"
  }
}

SAMPLE EVENT 2:
{
  "actor": {
    "id": "BroadCast Topic Notification",
    "type": "System"
  },
  "eid": "BE_JOB_REQUEST",
  "mid": "NS.1657555782237.a0603d3a-f668-47e1-940f-4620786f029b",
  "trace": {
    "X-Request-ID": null,
    "X-Trace-Enabled": "false"
  },
  "ets": 1657555782237,
  "edata": {
    "action": "broadcast-topic-notification-all",
    "iteration": 1,
    "request": {
      "notification": {
        "mode": "phone",
        "deliveryType": "message",
        "config": {
          "sender": null,
          "topic": null,
          "otp": null,
          "subject": null
        },
        "ids": [
          "8050688698"
        ],
        "template": {
          "id": null,
          "data": "You have successfully completed Sunbird training.",
          "params": {
            "courseName": "Sunbird training"
          }
        },
        "rawData": null
      }
    }
  },
  "context": {
    "pdata": {
      "ver": "1.0",
      "id": "org.sunbird.platform"
    }
  },
  "object": {
    "id": "f5e7243feabb343b029f154341c2d55dacb92febb0c1b0349ee0676a02c9b816",
    "type": "TopicNotifyAll"
  }
}
```

**Source code:**

{% embed url="https://github.com/Sunbird-Lern/data-pipeline/tree/release-5.3.0/notification/notification-job" %}
