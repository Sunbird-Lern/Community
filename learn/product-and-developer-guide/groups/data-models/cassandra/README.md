# Cassandra

Cassandra is the primary data store for groups and Redis is used for caching the group API response.

### **Cassandra** Database \[keyspace : sunbird\_groups] <a href="#database" id="database"></a>

**ER diagram**

![](../../../../../.gitbook/assets/sunbird\_groups.png)

#### Groups Keyspace:

```
CREATE KEYSPACE IF NOT EXISTS sunbird_groups WITH replication = {'class':'SimpleStrategy','replication_factor':1};CREATE TABLE IF NOT EXISTS  sunbird.user(id text,userId text,userName text, email text,phone text,aadhaarNo text,createdDate text,updatedDate text,updatedBy text,
ode
```

**Group Table**

```
CREATE TABLE sunbird_groups.group (
    id text PRIMARY KEY,
    activities list<frozen<map<text, text>>>,
    createdby text,
    createdon timestamp,
    description text,
    membershiptype text,
    name text,
    status text,
    updatedby text,
    updatedon timestamp
);

CREATE INDEX idx_group_status ON sunbird_groups.group (status);
```

**Group\_Member**

```
CREATE TABLE sunbird_groups.group_member (
    groupid text,
    userid text,
    createdby text,
    createdon timestamp,
    removedby text,
    removedon timestamp,
    role text,
    status text,
    updatedby text,
    updatedon timestamp,
    visited boolean,
    PRIMARY KEY (groupid, userid)
);
CREATE INDEX idx_group_member_status ON sunbird_groups.group_member (status);
```

***

**User\_Group**

```
CREATE TABLE sunbird_groups.user_group (
    userid text PRIMARY KEY,
    groupid set<text>
);
```

***
