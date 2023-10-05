# UI Telemetry Events

### List of Sample Events

<details>

<summary>Impression Event</summary>

```
{
  "eid": "IMPRESSION",
  "ets": 1594273993053,
  "ver": "3.0",
  "mid": "IMPRESSION:b9adb59d49eefbe975f2df9bcc3af7d4",
  "actor": {
    "id": "c1526b161339fe4fc544be6b78f2ae66",
    "type": "User"
  },
  "context": {
    "channel": "0123166374296453124",
    "pdata": {
      "id": "dev.sunbird.portal",
      "ver": "3.1.0",
      "pid": "sunbird-portal"
    },
    "env": "groups",
    "sid": "aecad6ce-e969-c9c4-dd49-ac6b390207e5",
    "did": "c1526b161339fe4fc544be6b78f2ae66",
    "cdata": [
      {
        "id": "Desktop",
        "type": "Device"
      }
    ],
    "rollup": {
      "l1": "0123166374296453124"
    }
  },
  "object": {},
  "tags": [
    "0123166374296453124"
  ],
  "edata": {
    "type": "view",
    "pageid": "explore-groups",
    "subtype": "paginate",
    "uri": "/explore-groups",
    "duration": 1.113
  }
}
```

</details>

<details>

<summary>Interact Event</summary>

```
{
  "eid": "INTERACT",
  "ets": 1594279207141,
  "ver": "3.0",
  "mid": "INTERACT:2a44e5e066c7438ddde627aba350d6d3",
  "actor": {
    "id": "c1526b161339fe4fc544be6b78f2ae66",
    "type": "User"
  },
  "context": {
    "channel": "0123166374296453124",
    "pdata": {
      "id": "dev.sunbird.portal",
      "ver": "3.1.0",
      "pid": "sunbird-portal"
    },
    "env": "home",
    "sid": "dfb26f00-33c6-6240-f65b-24e90b7147bc",
    "did": "c1526b161339fe4fc544be6b78f2ae66",
    "cdata": [
      {
        "id": "Desktop",
        "type": "Device"
      }
    ],
    "rollup": {
      "l1": "0123166374296453124"
    }
  },
  "object": {},
  "tags": [
    "0123166374296453124"
  ],
  "edata": {
    "id": "groups-tab",
    "type": "click",
    "pageid": "groups"
  }
}
```

</details>

<details>

<summary>Error Event</summary>

```
{
  "eid": "ERROR",
  "ets": 1615201298658,
  "ver": "3.0",
  "mid": "ERROR:e21d6112329634a20e7f168736a2bfed",
  "actor": {
    "id": "anonymous",
    "type": "user"
  },
  "context": {
    "channel": "b00bc992ef25f1a9a8d63291e20efc8d",
    "pdata": {
      "id": "dev.sunbird.portal",
      "ver": "3.7.0"
    },
    "env": "groups",
    "sid": "AaT0pEut3m_7Xm2sEyDBZKtnhZnKLZpH",
    "did": "1726023c0f4e4f17b2c956c412fd5859",
    "cdata": [],
    "rollup": {
      "l1": "ORG_001",
      "l2": "b00bc992ef25f1a9a8d63291e20efc8d"
    }
  },
  "object": {},
  "tags": [
    "ORG_001",
    "b00bc992ef25f1a9a8d63291e20efc8d"
  ],
  "edata": {
    "err": "SERVER_ERROR",
    "errtype": "SERVER_ERROR",
    "stacktrace": "unhandled error",
    "requestid": "4c41c808-c5eb-48a8-a44d-cdaa78589195",
    "errmsg": [
      "GROUPS Error while fetching group members record."
    ]
  }
}
```

</details>
