# Service Telemetry Events

### List of Events <a href="#list-of-events" id="list-of-events"></a>

<details>

<summary>Audit Event</summary>

```
{
  "eid": "AUDIT",
  "ets": 1623221114913,
  "ver": "3.0",
  "mid": "b45c38b7ac160bea1524d72614150a18",
  "actor": {
    "id": "a10d5216-6b96-404c-8d1c-cc1f720d910a",
    "type": "User"
  },
  "context": {
    "channel": "01285019302823526477",
    "pdata": {
      "id": "dev.sunbird.groups.service",
      "pid": "groups-service",
      "ver": "4.0.0"
    },
    "env": "groups",
    "cdata": [
      {
        "id": "a10d5216-6b96-404c-8d1c-cc1f720d910a",
        "type": "User"
      },
      {
        "id": "7aa56a86-c088-4d88-bddb-7f766469d063",
        "type": "Groupid"
      },
      {
        "id": "b45c38b7ac160bea1524d72614150a18",
        "type": "Request"
      }
    ],
    "rollup": {
      "l1": "01285019302823526477"
    }
  },
  "edata": {
    "type": "update-group",
    "prevstate": "active",
    "pageid": "group-detail",
    "props": [
      "groupId",
      "name"
    ],
    "currentstate": "active"
  }
}
```

</details>

<details>

<summary>Error Event</summary>

```
{
  "eid": "ERROR",
  "ets": 1623224221640,
  "ver": "3.0",
  "mid": "ddc86837f8464603b260100966574a96",
  "actor": {
    "id": "a10d5216-6b96-404c-8d1c-cc1f720d910a",
    "type": "User"
  },
  "context": {
    "channel": "01285019302823526477",
    "pdata": {
      "id": "dev.sunbird.groups.service",
      "pid": "groups-service",
      "ver": "4.0.0"
    },
    "env": "groups",
    "cdata": [
      {
        "id": "ddc86837f8464603b260100966574a96",
        "type": "Request"
      }
    ],
    "rollup": {
      "l1": "01285019302823526477"
    }
  },
  "edata": {
    "errtype": "GROUP_NOT_FOUND",
    "stackTrace": "org.sunbird.service.GroupServiceImpl.readGroup(GroupServiceImpl.java:76)org.sunbird.actors.UpdateGro",
    "error": "group does not exist with this group Id 7aa56a86-sc088-4d88-bddb-7f766469d063."
  }
}
```

</details>

<details>

<summary>Log Event</summary>

```
{
  "eid": "LOG",
  "ets": 1623220836126,
  "ver": "3.0",
  "mid": "8b0cd46b9bf618dc04fa7cc38ecf97a1",
  "actor": {
    "id": "a10d5216-6b96-404c-8d1c-cc1f720d910a",
    "type": "User"
  },
  "context": {
    "channel": "01285019302823526477",
    "pdata": {
      "id": "dev.sunbird.groups.service",
      "pid": "groups-service",
      "ver": "4.0.0"
    },
    "env": "groups",
    "cdata": [
      {
        "id": "8b0cd46b9bf618dc04fa7cc38ecf97a1",
        "type": "Request"
      }
    ],
    "rollup": {
      "l1": "01285019302823526477"
    }
  },
  "edata": {
    "level": "info",
    "type": "Api_access",
    "message": "",
    "params": [
      {
        "url": "/v1/group/create"
      },
      {
        "method": "createGroup"
      },
      {
        "status": 200
      },
      {
        "duration": 0
      }
    ]
  }
}
```

</details>
