# State Admin Report

The consent Report gives the user info organization-wise as per the consent given by the user. StateAdminReportJob generates a folder declared\_user\_detail which contains the user-declared consent and user details. It is generated in CSV format with respect to the organization name. It also provides organisation-wise consent details.

<figure><img src="../../../../../.gitbook/assets/state_Admin_Report.png" alt=""><figcaption></figcaption></figure>

**Data Provider:**

1. user\_declaration
2. user\_consent
3. organization
4. location
5. user

**Consent report CSV content:**

<table data-header-hidden><thead><tr><th width="174"></th><th width="125"></th><th width="99"></th><th></th></tr></thead><tbody><tr><td><strong>Column Label</strong></td><td><strong>Column Type</strong></td><td><strong>Data Type</strong></td><td><strong>Description</strong></td></tr><tr><td>Name</td><td>Static</td><td>String</td><td>Name of the user</td></tr><tr><td>User UUID</td><td>Static</td><td>String</td><td>The system generated unique user ID</td></tr><tr><td>State</td><td>Static</td><td>String</td><td>User declared state for self signed up users. If the user is a org validated user then the state as passed from org SSO or derived from Sub-Org ID.</td></tr><tr><td>District</td><td>Static</td><td>String</td><td>User declared district for self signed up users. If the user is a org validated user then the district as passed from org SSO or derived from Sub-Org ID.</td></tr><tr><td>Block</td><td>Static</td><td>String</td><td>User declared block for self signed up users. If the user is a org validated user then the block as passed from org SSO or derived from Sub-Org ID.</td></tr><tr><td>Cluster</td><td>Static</td><td>String</td><td>If the user is a org validated user then the cluster as passed from org SSO or derived from Sub-Org ID.<br>User declared cluster for self signed up users.</td></tr><tr><td>Sub-org Name</td><td>Static</td><td>String</td><td>If user is org validated then the sub-org name mapped to this user. If user is self-declared then the user declared org/sub-org name.</td></tr><tr><td>Sub-org ID</td><td>Static</td><td>String</td><td>If user is org validated then the sub-org ID is mapped to this user. If the user is self-declared then the user declared org/sub-org ID.</td></tr><tr><td>Organization provided unique ID</td><td>Static</td><td>String</td><td>Self declared users this is their declared ID. For organization validated users this is their organization ID</td></tr><tr><td>User Phone</td><td>Static</td><td>String</td><td>User declared unmasked mobile number from consent declaration</td></tr><tr><td>User Email ID</td><td>Static</td><td>String</td><td>User declared unmasked email ID from consent declaration</td></tr><tr><td>User Type</td><td>Static</td><td>String</td><td>User type from user profile</td></tr><tr><td>User-Sub Type</td><td>Static</td><td>String</td><td>User sub type from user profile</td></tr><tr><td>Root Org of user</td><td>Static</td><td>String</td><td>Root/Tenant Org the user belongs to</td></tr></tbody></table>

