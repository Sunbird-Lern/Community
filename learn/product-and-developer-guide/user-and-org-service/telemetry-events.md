# Telemetry Events

Telemetry is a specification to instrument all the key events. Using this specification reference applications & services will generate telemetry events. For more info [here](https://telemetry.sunbird.org/)

### List of Events <a href="#list-of-events" id="list-of-events"></a>

<details>

<summary>Audit Event</summary>

```
{
   "eid":"AUDIT",
   "ets":1649247985143,
   "ver":"3.0",
   "mid":"d808691c-e253-43a6-a8a0-aa03bc67b6ce",
   "actor":{
      "id":"50792198-c6d7-4964-8d4c-da6891ceed0a",
      "type":"User"
   },
   "context":{
      "channel":"0126796199493140480",
      "pdata":{
         "id":"staging.sunbird.learning.service",
         "pid":"learner-service",
         "ver":"4.7.0"
      },
      "env":"User",
      "cdata":[
         {
            "id":"d808691c-e253-43a6-a8a0-aa03bc67b6ce",
            "type":"Request"
         }
      ],
      "rollup":{
         "l1":"0126796199493140480"
      }
   },
   "object":{
      "type":"User"
   },
   "edata":{
      "state":"Update",
      "props":[
         "identifier",
         "tncAcceptedOn",
         "id",
         "tncAcceptedVersion"
      ]
   }
}
```

</details>

<details>

<summary>Search Event</summary>

```
{
   "eid":"SEARCH",
   "ets":1649247379860,
   "ver":"3.0",
   "mid":"4e0e50ed-92c0-5c80-ff29-b3a194a1911f",
   "actor":{
      "id":"86fe48dd-72d5-4f27-a9b4-c55580878ec4",
      "type":"User"
   },
   "context":{
      "channel":"0126796199493140480",
      "pdata":{
         "id":"staging.dock.portal",
         "pid":"learner-service",
         "ver":"4.7.0"
      },
      "env":"User",
      "did":"487975adbe74ea73faea476eab1ebb31",
      "cdata":[
         {
            "id":"4e0e50ed-92c0-5c80-ff29-b3a194a1911f",
            "type":"Request"
         }
      ],
      "rollup":{
         "l1":"0126796199493140480"
      }
   },
   "edata":{
      "size":1,
      "query":"",
      "filters":{
         "id":[
            "0126796199493140480"
         ]
      },
      "sort":{
         
      },
      "type":"Org_alias",
      "topn":[
         {
            "id":"0126796199493140480"
         }
      ]
   }
}
```

</details>

<details>

<summary>Error Event</summary>

```
{
   "eid":"ERROR",
   "ets":1649248112302,
   "ver":"3.0",
   "mid":"31eab671-1395-4135-8723-15ffa5d349cb",
   "actor":{
      "id":"internal",
      "type":"Consumer"
   },
   "context":{
      "channel":"0126796199493140480",
      "pdata":{
         "id":"staging.sunbird.learning.service",
         "pid":"learner-service",
         "ver":"4.7.0"
      },
      "env":"Organisation",
      "cdata":[
         {
            "id":"31eab671-1395-4135-8723-15ffa5d349cb",
            "type":"Request"
         }
      ],
      "rollup":{
         
      }
   },
   "edata":{
      "err":"UOS_ORGSER0017",
      "stacktrace":"Invalid value null for parameter hashTagId. Please provide a valid value. org.sunbird.validator.BaseRequestValidator.lambda$validateListValues$6(BaseRequestValidator.java:291)java.base/java.util.ArrayList.forEach(ArrayList.java:1541)org.sunbird.validator.BaseRequestValidator.validateListValues",
      "errtype":"api_access",
      "requestid":"31eab671-1395-4135-8723-15ffa5d349cb"
   }
}
```

</details>

<details>

<summary>Log Event</summary>

```
{
   "eid":"LOG",   
   "actor":{
      "id":"internal",
      "type":"Consumer"
   },
   "edata":{
      "level":"info",
      "type":"Api_access",
      "message":"",
      "params":[
         {
            "method":"POST"
         },
         {
            "url":"/v1/org/search"
         },
         {
            "duration":0
         },
         {
            "status":"OK"
         }
      ]
   },
   "ver":"3.0",
   "syncts":1649247488365,
   "@timestamp":"2022-04-06T12:18:08.365Z",
   "ets":1649247476273,
   "context":{
      "channel":"0126796199493140480",
      "pdata":{
         "id":"staging.sunbird.learning.service",
         "pid":"learner-service",
         "ver":"4.7.0"
      },
      "env":"Organisation",
      "cdata":[
         {
            "id":"9c158007-345b-44d7-a128-6c36f7a42cfb",
            "type":"Request"
         }
      ],
      "rollup":{
         
      }
   },
   "flags":{
      "pp_validation_processed":true
   },
   "mid":"9c158007-345b-44d7-a128-6c36f7a42cfb",
   "type":"events"
}
```

</details>

### Sample Telemetry Data

<details>

<summary>Audit Event Data</summary>

```
{
  "eid": "AUDIT",
  "ets": 1566563420660,
  "ver": "3.0",
  "mid": "1566563420660.f46c14d1-8c9a-417f-82b8-f125ba32b828",
  "actor": {
    "id": "internal",
    "type": "Consumer"
  },
  "context": {
    "channel": "0128220189818880000",
    "pdata": {
      "id": "staging.diksha.learning.service", // Producer ID.
      "ver": "1.15", // Version of the App
      "pid": "learner-service"// Optional. In case the component is distributed, then which instance of that component
    },
    "env": "User",
    "cdata": [
      {
        "id": "4e2afe8e-fb44-4788-9f49-0ef61c5c808b",
        "type": "User"
      },
      {
        "id": "11166",
        "type": "Certificate"
      }
    ],
    "rollup": {
      "l1": "0128220189818880000"
    }
  },
  "object": {
    "id": "11166",
    "type": "Certificate"
  },
  "edata": {
    "state": "Create", // defines the state i.e: Mergecert, Mergeuser
    "props": [
      "certId", // certificate Id
      "userId"  // user Id
    ]
  }
}
```

</details>
