# User Roles

How to assign roles to a user?

Below APIs can be used to assign roles: ([API Documentation](https://lern.sunbird.org/learn/product-and-developer-guide/user-and-org-service/api-documentation/user-management))

<pre><code>POST /v2/user/assign/role
<strong>POST /private/user/v2/assign/role</strong></code></pre>

User with ORG\_ADMIN role only can assign other roles in the specific org to a user. User need not belong to the specific org to have a role of that org. Admin can choose users in other org also. &#x20;

To assign ORG\_ADMIN role to a user, while creating the user itself the role can be passed in  (/v1/ssouser/create) request as roles array.  Otherwise /v2/user/assign/role API can be used from the pod directly without going through API gateway to avoid user role check.

Scope of the role can be chosen by the org admin. Currently in scope of the role is supporting only  organisation.

To fetch roles of a specific user, below API can be used:

```
GET /v1/user/role/read/:uid 
```

