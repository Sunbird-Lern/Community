# State Admin Report

The consent Report gives the user info channel-wise as per the consent given by the user. StateAdminReportJob generates a folder declared\_user\_detail which contains the user-declared consent and user details. It is generated in CSV format with respect to the channel name.It also provides organisation-wise consent details.

<figure><img src="../../../../../.gitbook/assets/state_Admin_Report.png" alt=""><figcaption></figcaption></figure>

**Data Provider:**

1. user\_declaration
2. user\_consent
3. organisation
4. location
5. user

**Consent report CSV content:**

<table data-header-hidden><thead><tr><th width="174"></th><th width="125"></th><th width="99"></th><th></th></tr></thead><tbody><tr><td><strong>Column Label</strong></td><td><strong>Column Type</strong></td><td><strong>Data Type</strong></td><td><strong>Description</strong></td></tr><tr><td>Name</td><td>Static</td><td>String</td><td>Name of the user</td></tr><tr><td>Diksha UUID</td><td>Static</td><td>String</td><td>The system generated DIKSHA unique user ID</td></tr><tr><td>State</td><td>Static</td><td>String</td><td>User declared state for self signed up users. If the user is a state validated user then the state as passed from state SSO or derived from school ID.</td></tr><tr><td>District</td><td>Static</td><td>String</td><td>User declared district for self signed up users. If the user is a state validated user then the district as passed from state SSO or derived from school ID.</td></tr><tr><td>Block</td><td>Static</td><td>String</td><td>User declared block for self signed up users. If the user is a state validated user then the block as passed from state SSO or derived from school ID.</td></tr><tr><td>Cluster</td><td>Static</td><td>String</td><td>User declared cluster for self signed up users. If the user is a state validated user then the cluster as passed from state SSO or derived from school ID.</td></tr><tr><td>School Name</td><td>Static</td><td>String</td><td>If user is state validated teacher then the school name mapped to this user. If user is self declared user then the user declared org/school name.</td></tr><tr><td>School UDISE ID</td><td>Static</td><td>String</td><td>If user is state validated teacher then the school UDISE ID mapped to this user. If user is self declared user then the user declared org/school UDISE ID.</td></tr><tr><td>State provided ext. ID</td><td>Static</td><td>Number</td><td>Self declared users this is their declared ID. For state validated users this is their Teacher ID</td></tr><tr><td>Profile Email</td><td>Static</td><td>String</td><td>User declared unmasked email ID from user profile</td></tr><tr><td>Profile Phone number</td><td>Static</td><td>String</td><td>User declared unmasked mobile number from user profile</td></tr><tr><td>Org Phone</td><td>Static</td><td>String</td><td>User declared unmasked mobile number from consent declaration</td></tr><tr><td>Org Email ID</td><td>Static</td><td>String</td><td>User declared unmasked email ID from consent declaration</td></tr><tr><td>User Type</td><td>Static</td><td>String</td><td>User type from user profile</td></tr><tr><td>User-Sub Type</td><td>Static</td><td>String</td><td>User sub type from user profile</td></tr><tr><td>Root Org of user</td><td>Static</td><td>String</td><td>Root/Tenant Org the user belongs to</td></tr></tbody></table>

