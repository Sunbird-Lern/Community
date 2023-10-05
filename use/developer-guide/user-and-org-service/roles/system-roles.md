# System Roles

#### How to create system roles?

Currently there are no APIs present in UserOrg service to do role management. If any new role needs to be added it is done through DB script.&#x20;

Sample Script:

<pre><code><strong>insert into sunbird.role (id,name,rolegroupid,status) values ('PROGRAM_MANAGER','Program Manager',['PROGRAM_MANAGER'],1);
</strong>insert into sunbird.role_group (id,name) values ('PROGRAM_MANAGER','Program Manager');
</code></pre>

DB details:

```
CREATE TABLE IF NOT EXISTS sunbird.role(id text, name text,roleGroupId List<text>,status int, PRIMARY KEY (id));
CREATE TABLE IF NOT EXISTS sunbird.role_group(id text, name text, PRIMARY KEY (id));
```

To fetch the roles in the system, below API can be used:

```
GET /v1/role/read
```

#### Role List

<table><thead><tr><th width="280">Roles</th><th>Description</th></tr></thead><tbody><tr><td>SYSTEM_ADMINISTRATION</td><td></td></tr><tr><td>ADMIN</td><td></td></tr><tr><td>ORG_ADMIN</td><td><p></p><p>A org admin can :</p><ul><li>Download consent user data file in manage page.</li><li>Download Geo report data.</li><li>Search same org users from profile using their external ID.</li><li>Assign roles to the users of same org.</li><li>Create and Manage (edit, modify, delete, publish, add users) Sourcing Projects</li></ul></td></tr><tr><td>ORG_MODERATOR</td><td></td></tr><tr><td>ORG_MANAGEMENT</td><td></td></tr><tr><td>MEMBERSHIP_MANAGEMENT</td><td></td></tr><tr><td>PUBLIC</td><td>Default role</td></tr><tr><td>BOOK_CREATOR</td><td>A book creator can create book</td></tr><tr><td>BOOK_REVIEWER</td><td>A book reviewer can review and publish book</td></tr><tr><td>COURSE_ADMIN</td><td></td></tr><tr><td>COURSE_MENTOR</td><td><p>A course mentor can:</p><ul><li>create a batch</li><li>add or edit other mentors to a batch</li><li>add or edit participants to a batch</li><li>edit ongoing batches</li><li>view status of all the batch participants</li><li>Request for userinfo, progress, and question set exhaust report</li><li>Download the userinfo, progress, and question set exhaust report</li></ul></td></tr><tr><td>CONTENT_CREATOR</td><td>A content creator can create all type(Course, resource, Collection, Lessonplan, Upload content, Upload large videos, Course assessment) of contents except book</td></tr><tr><td>CONTENT_REVIEWER</td><td>A content reviewer can review and publish all type of contents except book</td></tr><tr><td>CONTENT_CURATION</td><td></td></tr><tr><td>REPORT_ADMIN</td><td>Can publish reports on the portal as 'Live'. Also has access to the 'Datasets' tab on the portal, where datasets are made available for Admins to be able to download. Also has all the rights of the 'REPORT_VIEWER' role - all of these for the tenant that they have the role for</td></tr><tr><td>REPORT_VIEWER</td><td>This role allows a registered user to have 'view' access to all reports pulbished for their tenant on the portal. These are accessed via the 'Dashboards' page on the portal</td></tr><tr><td>PROGRAM_MANAGER</td><td><p>This is a new role introduced as a part of 4.2 hotfix. The role will have access to Program dashboards and can access all CSVs for different resources mapped in a program. They will have access to the programs that they are program managers of. The role will have the following right:</p><ul><li>Will have access to the data of all the resources that are part of the program mapped to them</li></ul></td></tr><tr><td>PROGRAM_DESIGNER</td><td><p>This is a new role introduced as a part of 4.2 hotfix. The role will have access to Program dashboards and can access Status CSVs for different resources mapped in a program designed by them. </p><p>The role has following rights: </p><ul><li>Create a program with different published resources in it </li><li>Add a description to the program </li><li>Sequence different resources that are part of the program</li><li>Target the program and resources to a geography </li><li>Target the program and resources for different sub-roles </li><li>Edit the program Access to the status data of all the resources that are part of the program created by him/her</li></ul></td></tr></tbody></table>
