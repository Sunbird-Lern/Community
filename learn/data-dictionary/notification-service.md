---
description: List of tables in Cassandra database used in Notification service
---

# Notification Service



### sunbird\_notifications.notification\_feed \[PRIMARY KEY (userid,id)]



<table><thead><tr><th width="234.33333333333331">Column Name</th><th width="124">Data Type</th><th>Description</th><th>Sample Value</th></tr></thead><tbody><tr><td>id</td><td>text</td><td>UUID, notification ID</td><td>1d48ab59-71c1-45a9-add4-44e78a333eb6</td></tr><tr><td>createdby</td><td>text</td><td>UUID, notification feed created by</td><td>d9b6751b-7d49-42e0-840a-209acff2dcee</td></tr><tr><td>createdon</td><td>timestamp</td><td>Notification feed created on</td><td>2021-12-10 07:08:14.545000+0000</td></tr><tr><td>action</td><td>text</td><td>Notification feed content. </td><td>{"template":{"ver":"4.5.0","data":"{"description":"You have earned a certificate! Download it from your profile page.","title":"New Cert Course 4.5 "}","type":"JSON"},"createdBy":{"id":null,"type":"system"},"additionalInfo":{"actionType":"certificateUpdate","identifier":"do_213432103242072064167","type":1},"type":"certificateUpdate","category":"Notification"}</td></tr><tr><td>category</td><td>text</td><td>Feed category<br><br>Available values:<br>notification/ group</td><td>Notification</td></tr><tr><td>expireon</td><td>timestamp</td><td>Notification feed expires on</td><td>2021-12-10 07:08:21.841000+0000</td></tr><tr><td>priority</td><td>int</td><td>Priortiy of the notification-feed</td><td>1</td></tr><tr><td>status</td><td>text</td><td>Status of the feed<br><br>Available values: read/unread</td><td>read</td></tr><tr><td>updatedby</td><td>text</td><td>UUID, notification feed last updated by</td><td>d9b6751b-7d49-42e0-840a-209acff2dcee</td></tr><tr><td>updatedon</td><td>timestamp</td><td>Notification feed last updated on</td><td>2021-12-10 07:08:14.545000+0000</td></tr><tr><td>userid</td><td>text</td><td>UUID, user id</td><td>02b8bade-c8ed-44c7-87fd-ebabeaed98c2</td></tr><tr><td>version</td><td>text</td><td>Version of the feed</td><td>v1</td></tr></tbody></table>



### sunbird.notification\_template \[PRIMARY KEY((templateId,language))]



<table><thead><tr><th width="184.33333333333331">Column Name</th><th width="113">Data Type</th><th>Description</th><th>Sample Value</th></tr></thead><tbody><tr><td>templateId</td><td>text</td><td>Template ID</td><td>context-assigned</td></tr><tr><td>config</td><td>map&#x3C;text, text></td><td>Condiguration value map for the data in the template</td><td></td></tr><tr><td>type</td><td>text</td><td>Type of the template<br><br>supporting values: xml, json</td><td>JSON</td></tr><tr><td>ver</td><td>text</td><td>Version of the template</td><td>4.4.3</td></tr><tr><td>data</td><td>text</td><td>Actual data of the template</td><td>{"title": "${param1} has been assigned to ${param2} by ${param3}"}</td></tr><tr><td>template_schema</td><td>text</td><td>Template schema</td><td>{"$schema":"#/definition/params","title":"params context","description":"properties Data","type":"object","properties":{"param1":{"description":"property 1 value","type":"string"},"param2":{"description":"property 2 value","type":"string"},"param3":{"description":"property 3 value","type":"string"}},"required":["param1","param2","param3"] }</td></tr><tr><td>createdOn</td><td>timestamp</td><td>Template created on</td><td>2023-02-22 08:09:40.335000+0000</td></tr><tr><td>lastUpdatedOn</td><td>timestamp</td><td>Template last updated on</td><td>2022-07-25 04:58:11.576000+0000</td></tr><tr><td>createdBy</td><td>text</td><td>UUID, Template created by</td><td>fca2925f-1eee-4654-9177-fece3fd6afc9</td></tr><tr><td>lastUpdatedBy</td><td>text</td><td>UUID, Template last update by</td><td>fca2925f-1eee-4654-9177-fece3fd6afc9</td></tr></tbody></table>

####

#### sunbird\_notifications.action\_template \[PRIMARY KEY(action)]

<table><thead><tr><th width="184.33333333333331">Column Name</th><th width="113">Data Type</th><th width="184.33333333333331">Description</th><th>Sample Value</th></tr></thead><tbody><tr><td>action</td><td>text</td><td>Name of the action template</td><td>group-activity-added</td></tr><tr><td>templateid</td><td>text</td><td>Template ID</td><td>context-assigned</td></tr><tr><td>type</td><td>text</td><td>Type of action template</td><td>FEED</td></tr></tbody></table>





#### sunbird\_notifications.feed\_version\_map \[PRIMARY KEY(id)]

<table><thead><tr><th width="184.33333333333331">Column Name</th><th width="113">Data Type</th><th width="184.33333333333331">Description</th><th>Sample Value</th></tr></thead><tbody><tr><td>id</td><td>text</td><td>UUID, User ID</td><td>9613f870-f560-4550-bb9b-27e14c168d80</td></tr><tr><td>feedid</td><td>text</td><td>UUID, Feed ID</td><td>21ae13fa-9d1c-42c3-8ad9-2fe04e3d7323</td></tr><tr><td>status</td><td>text</td><td>status of feed with respect to user</td><td>deleted</td></tr></tbody></table>
