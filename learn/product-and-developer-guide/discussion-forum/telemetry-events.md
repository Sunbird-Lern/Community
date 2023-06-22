# Telemetry Events

Telemetry is a specification to instrument all the key events. Using this specification reference applications & services will generate telemetry events. For more info refer Sunbird-Telemetry documentation [here](https://telemetry.sunbird.org/). Also to know how telemetry is processed refer to Telemetry Processing Documentation in [https://lern.sunbird.org/learn/telemetry-processing](https://lern.sunbird.org/learn/telemetry-processing).

### List of Events <a href="#list-of-events" id="list-of-events"></a>

**UI Telemetry Events**

<details>

<summary>Impression Event</summary>

```
{
  "eid": "IMPRESSION",
  "ets": 1615443539430,
  "ver": "3.0",
  "mid": "IMPRESSION:da1c716378dbd91db8355ea1f7853f72",
  "actor": {
    "id": "fca2925f-1eee-4654-9177-fece3fd6afc9",
    "type": "User"
  },
  "context": {
    "channel": "01269878797503692810",
    "pdata": {
      "id": "dev.sunbird.portal",
      "ver": "3.8.0",
      "pid": "sunbird-portal"
    },
    "env": "discussion",
    "sid": "NroMG4d_vaHatKFIwLK7Ehfz6wwMCDD8",
    "did": "1726023c0f4e4f17b2c956c412fd5859",
    "cdata": [
      {
        "id": "ce84f532-cfcf-4f68-829a-24a1eea5aaa0",
        "type": "Group"
      },
      {
        "id": "NroMG4d_vaHatKFIwLK7Ehfz6wwMCDD8",
        "type": "UserSession"
      },
      {
        "id": "Desktop",
        "type": "Device"
      },
      {
        "id": "default",
        "type": "Theme"
      }
    ],
    "rollup": {
      "l1": "01269878797503692810"
    },
    "uid": "fca2925f-1eee-4654-9177-fece3fd6afc9"
  },
  "object": {},
  "tags": [
    "01269878797503692810"
  ],
  "edata": {
    "type": "view",
    "pageid": "discussion-home",
    "uri": "/discussion-forum?categories=%7B%22result%22:%5B57%5D%7D&userName=cctn1350",
    "duration": 0.34
  }
}
```

</details>

<details>

<summary>Intract Event</summary>

```
{
  "eid": "INTERACT",
  "ets": 1615533000656,
  "ver": "3.0",
  "mid": "INTERACT:241870d0300b523c89cb4cafe4050330",
  "actor": {
    "id": "fca2925f-1eee-4654-9177-fece3fd6afc9",
    "type": "User"
  },
  "context": {
    "channel": "01269878797503692810",
    "pdata": {
      "id": "dev.sunbird.portal",
      "ver": "3.8.0",
      "pid": "sunbird-portal"
    },
    "env": "discussion",
    "sid": "NroMG4d_vaHatKFIwLK7Ehfz6wwMCDD8",
    "did": "1726023c0f4e4f17b2c956c412fd5859",
    "cdata": [
      {
        "id": "ce84f532-cfcf-4f68-829a-24a1eea5aaa0",
        "type": "Group"
      },
      {
        "id": "NroMG4d_vaHatKFIwLK7Ehfz6wwMCDD8",
        "type": "UserSession"
      },
      {
        "id": "Desktop",
        "type": "Device"
      },
      {
        "id": "default",
        "type": "Theme"
      }
    ],
    "rollup": {
      "l1": "01269878797503692810"
    },
    "uid": "fca2925f-1eee-4654-9177-fece3fd6afc9"
  },
  "object": {},
  "tags": [
    "01269878797503692810"
  ],
  "edata": {
    "id": "d.route",
    "type": "CLICK",
    "pageid": "discussion-home"
  }
}
```

</details>

<details>

<summary>Error Event</summary>

```
{
  "eid": "ERROR",
  "ets": 1616052502447,
  "ver": "3.0",
  "mid": "ERROR:e0e65a6f43ea674e508cfcdb00f85d79",
  "actor": {
    "id": "anonymous",
    "type": "user"
  },
  "context": {
    "channel": "in.ekstep",
    "pdata": {
      "id": "discussion-middleware",
      "ver": "1.0.0"
    },
    "env": "discussion-middleware",
    "sid": "",
    "did": "",
    "cdata": [],
    "rollup": {}
  },
  "object": {},
  "tags": [],
  "edata": {
    "err": 400,
    "errtype": "DMW_FGCRT09",
    "requestid": "5f36c090-2eee-11eb-80ed-6bb70096c082",
    "errmsg": "Generalization of api failed"
  }
}
```

</details>

<details>

<summary>Trace Event</summary>

```
{
  "eid": "LOG",
  "ets": 1633931801927,
  "ver": "3.0",
  "mid": "LOG:ef8d3d0f662dbc5516b54abb98acd3ff",
  "actor": {
    "id": "anonymous",
    "type": "user"
  },
  "context": {
    "channel": "in.ekstep",
    "pdata": {
      "id": "discussion-middleware",
      "pid": "dev.sunbird.portal",
      "ver": "1.0.0"
    },
    "env": "discussion-middleware",
    "sid": "0ebkLX6MhVjhTsjJtoFaFhl5nZiPOnp2",
    "did": "1726023c0f4e4f17b2c956c412fd5859",
    "cdata": [],
    "rollup": {}
  },
  "object": {},
  "tags": [],
  "edata": {
    "type": "api_call",
    "level": "TRACE",
    "message": "{\"title\":\"API Log\",\"url\":\"/discussion/tags\"}",
    "params": "[{\"title\":\"discussion-middleware\"},{\"category\":\"ENTRY LOG\"},{\"url\":\"/discussion/tags\"},{\"duration\":null},{\"status\":\"200\"},{\"protocol\":\"https\"},{\"method\":\"GET\"},{},{},{\"size\":15}]"
  }
}
```

</details>

#### Service Events

<details>

<summary>Audit Event</summary>

```
{
  "eid": "AUDIT",
  "ets": "2022-01-04 03:23:26:681+0000",
  "ver": "1.0",
  "mid": "c86d6e107c3ac5d876e03619f2251552",
  "actor": {
    "id": "public",
    "type": "User"
  },
  "context": {
    "channel": "01269878797503692810",
    "pdata": {
      "id": "discussion-middleware",
      "pid": "staging.sunbird.portal",
      "ver": "4.6.0"
    },
    "env": "discussion-forum",
    "cdata": [],
    "rollup": {
      "l1": "01269878797503692810"
    }
  },
  "object": {},
  "edata": {
    "type": "downvote",
    "props": [
      "delta",
      "_uid"
    ]
  }
}
```

</details>
