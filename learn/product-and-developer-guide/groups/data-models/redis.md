# Redis

Caching of API responses in groups service is implemented using Redis (DB index: 0).&#x20;

Group create, update and delete APIs deletes the cached data from Redis and Group read and list APIs populates the cache with the updated data from database.

3 types of group data are stored in Redis:

1. group data - key is \<group\_uuid>
2. group member list - key is \<group\_uuid>\_members
3. group list for a user - key is \<user\_uuid>

There is a separation proposed to independently scale members and activities. We could expect activities to be having content metadata (size=big) and other metadata (size=small). The member data is relatively a list of alike fields and therefore will directly be related to the count of members.

<table data-header-hidden><thead><tr><th width="180"></th><th></th><th width="70"></th><th></th></tr></thead><tbody><tr><td><strong>Identifier</strong></td><td><strong>Data refresh when?</strong></td><td><strong>TTL</strong></td><td><strong>Comments</strong></td></tr><tr><td>groupId_members</td><td>Members added/role changes/removed</td><td>1d</td><td>Members of this specific group. Likely less or no changing once group is formed. Members might get added only infrequently. But when a member gets added/updated/removed from group this cache gets deleted.<br><br>The member name changes within 1d is less likely to reflect. This TTL can be tweaked as its an env var.</td></tr><tr><td>userId</td><td>When the user reads his groups</td><td>1h</td><td><p>Groups the user belongs. This is populated only after a read of this user by calling /group/v1/list. When a member gets added/updated/removed from group this cache gets deleted, along with groupId_members.</p><p>The activity info changes within 1h is less likely to reflect. This TTL can be tweaked as its an env var.</p></td></tr><tr><td>groupId</td><td>Group name, description changes<br>Add/Remove activities</td><td>1d</td><td><p>Group name, description and activities. Likely less changing, but often in the initial days.<br>Activity data within a group - like leaf nodes etc - would it get updated within the TTL? - this was discussed with DC and found to be okay to live with.</p><p>When group information gets updated or activity is added/removed, this cache gets deleted.</p></td></tr></tbody></table>
