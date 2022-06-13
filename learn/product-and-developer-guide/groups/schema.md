# Schema

### **Cassandra** Database <a href="#database" id="database"></a>

**ER diagram**

![](../../../.gitbook/assets/sunbird\_groups.png)

#### Group Keyspace:

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

\
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

**USER\_GROUP**

```
CREATE TABLE sunbird_groups.user_group (
    userid text PRIMARY KEY,
    groupid set<text>
);
```

***

**Redis Cache**

There is a separation proposed to independently scale members and activities. We could expect activities to be having content metadata (size=big) and other metadata (size=small). The member data is relatively a list of alike fields and therefore will directly be related to the count of members.

| **Identifier**   | **Data refresh when?**                                          | **TTL** | **Comments**                                                                                                                                                                                                                                                                                                                                                      |
| ---------------- | --------------------------------------------------------------- | ------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| groupId\_members | Members added/role changes/removed                              | 1d      | <p>Members of this specific group. Likely less or no changing once group is formed. Members might get added only infrequently. But when a member gets added/updated/removed from group this cache gets deleted.<br><br>The member name changes within 1d is less likely to reflect. This TTL can be tweaked as its an env var.</p>                                |
| userId           | When the user reads his groups                                  | 1h      | <p>Groups the user belongs. This is populated only after a read of this user by calling /group/v1/list. When a member gets added/updated/removed from group this cache gets deleted, along with groupId_members.</p><p>The activity info changes within 1h is less likely to reflect. This TTL can be tweaked as its an env var.</p>                              |
| groupId          | <p>Group name, description changes<br>Add/Remove activities</p> | 1d      | <p>Group name, description and activities. Likely less changing, but often in the initial days.<br>Activity data within a group - like leaf nodes etc - would it get updated within the TTL? - this was discussed with DC and found to be okay to live with.</p><p>When group information gets updated or activity is added/removed, this cache gets deleted.</p> |

\\
