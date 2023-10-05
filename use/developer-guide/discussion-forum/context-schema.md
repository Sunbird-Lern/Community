# Context Schema

We can attach the discussion forum for any context, with that we can start context based discussions. We are storing the context in separate redis db.

For example, While doing nodebb setup in local, we have provide redis database number (db:0).

and successive db number (db:1) should be a context database.

```
Nodebb database : db:0
context database: db:1
```

### **Context schema**

```
{
    sbType: String,
    sbIdentifier: String,
    cid: string // nodebb category id,
    data: JSON Object
}
```

Example:

| sbType | sbIdentifier                         | cid | data   |
| ------ | ------------------------------------ | --- | ------ |
| Course | do\_11317805943810457614592          | 4   | {JSON} |
| Batch  | 01316730820300800028                 | 5   | {JSON} |
| Group  | 123475d2-c299-45f6-992e-a22d081431bd | 6   | {JSON} |

Refer this link to attach a discussion forum for a context [link](../../../use/developer-installation/discussion-forum/installation-guide/discussion-forum-integration-with-any-application.md)
