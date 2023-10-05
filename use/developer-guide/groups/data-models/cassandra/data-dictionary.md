---
description: List of tables in Cassandra database used in Groups service
---

# Groups Service



### sunbird\_groups.group \[PRIMARY KEY: id]



<table><thead><tr><th width="176.33333333333331">Column Name</th><th width="120">Data Type</th><th>Description</th><th>Sample Value</th></tr></thead><tbody><tr><td>id</td><td>text</td><td>UUID of the group</td><td>ad2ffd12-ee05-46fc-bbe7-f5a67bd0534e</td></tr><tr><td>activities</td><td>list&#x3C;frozen&#x3C;map&#x3C;text, text>>></td><td>Activities that are published with in the group</td><td>[{'id': 'do_2132889347963535361756', 'type': 'Course'}, {'id': 'do_2133016209522933761354', 'type': 'Course'}, {'id': 'do_21333644232679424012289', 'type': 'Course'}, {'id': 'do_21331802990687027216', 'type': 'Course'}, {'id': 'do_2133483390278287361856', 'type': 'Course'}, {'id': 'do_2133817803741347841999', 'type': 'Content Playlist'}, {'id': 'do_213375362019328000129', 'type': 'Teacher Resource'}, {'id': 'do_21333645138176409618', 'type': 'Course'}, {'id': 'do_2132734144209469441409', 'type': 'Course'}, {'id': 'do_2132882557402644481743', 'type': 'Course'}, {'id': 'do_2133187549468098561201', 'type': 'Course'}, {'id': 'do_21334149144616960013071', 'type': 'Course'}]</td></tr><tr><td>createdby</td><td>text</td><td>UUID of the group created user</td><td>fbe926ac-a395-40e4-a65b-9b4f711d7642</td></tr><tr><td>createdon</td><td>timestamp</td><td>Group created on</td><td>2021-05-31 11:04:58.580000+0000</td></tr><tr><td>description</td><td>text</td><td>Description of the Group</td><td>EditedGroup</td></tr><tr><td>membershiptype</td><td>text</td><td>Type of member to the group, Possible values: moderated, invite_only</td><td>invite_only</td></tr><tr><td>name</td><td>text</td><td>Name of the Group</td><td>dashletEditedGroup</td></tr><tr><td>status</td><td>text</td><td>Staus of the group</td><td>active</td></tr><tr><td>updatedby</td><td>text</td><td>Last updated by</td><td>fca2925f-1eee-4654-9177-fece3fd6afc9</td></tr><tr><td>updatedon</td><td>timestamp</td><td>Last updated timestamp</td><td>2021-11-03 04:28:30.528000+0000</td></tr></tbody></table>



### sunbird\_groups.group\_member \[PRIMARY KEY (groupid, userid)]



<table><thead><tr><th width="165.33333333333331">Column Name</th><th width="131">Data Type</th><th>Description</th><th>Sample Value</th></tr></thead><tbody><tr><td>groupid</td><td>text</td><td>UUID, id of the group</td><td>ad2ffd12-ee05-46fc-bbe7-f5a67bd0534e</td></tr><tr><td>userid</td><td>text</td><td>UUID, id of the user</td><td>7557fd26-5b7c-4dd7-bd60-8e13ac856652</td></tr><tr><td>createdby</td><td>text</td><td>UUID, created user id</td><td>fca2925f-1eee-4654-9177-fece3fd6afc9</td></tr><tr><td>createdon</td><td>timestamp</td><td>Created on timestamp</td><td>2021-10-21 14:41:23.654000+0000</td></tr><tr><td>removedby</td><td>text</td><td>UUID, of the user that triggered the event</td><td>fca2925f-1eee-4654-9177-fece3fd6afc9</td></tr><tr><td>removedon</td><td>timestamp</td><td>removed timestamp</td><td>2021-12-03 04:29:09.182000+0000</td></tr><tr><td>role</td><td>text</td><td>Role of the person in the group, possible values are: member, admin</td><td>member</td></tr><tr><td>status</td><td>text</td><td>Status of the user with respect to the group</td><td>active</td></tr><tr><td>updatedby</td><td>text</td><td>UUID, of the last updated user</td><td>fbe926ac-a395-40e4-a65b-9b4f711d7642</td></tr><tr><td>updatedon</td><td>timestamp</td><td>Last updated timestamp</td><td>2021-09-08 07:02:12.553000+0000</td></tr><tr><td>visited</td><td>boolean</td><td>Member visited the group</td><td>True</td></tr></tbody></table>



### sunbird\_groups.user\_group \[PRIMARY KEY: userid]



<table><thead><tr><th width="158.33333333333331">Column Name</th><th width="116">Data Type</th><th>Description</th><th>Sample Value</th></tr></thead><tbody><tr><td>userid</td><td>text</td><td>UUID, id of the user</td><td>10e2cac0-1757-47d3-a010-b9bca8d2d5d0</td></tr><tr><td>groupid</td><td>set&#x3C;text></td><td>UUID of the groups, groups id's of the user that are linked to</td><td>{'95cea74a-2647-44a4-98e1-a4337b9e67b2', 'c535cd6a-f03d-4484-9b48-5cce6f935d78'}</td></tr></tbody></table>







