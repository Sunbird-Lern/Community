# Features/Core Capabilities

**Key Features:**

1. Group Creation - Any type of user could create groups and any number of groups can be created. A maximum of 50 groups can be created by a user as per the default configuration.
2. Add/remove members - Members can be either users or managed users. The Default configuration for a maximum number of members is 150.
3. Groups can be associated with activities - Activity is a specific interest associated with the group. Example: Content, Discussion, Announcement. Up to 20 activities can be added in a group as per the default configuration.
4. Activities that can be added to the group are configured using activityConfig.json. This configuration enables to connect to various services to fetch activities.
5. Group admin can monitor the progress of member's trackable collection that is assigned through a dashboard
6. Discussion Forums can be enabled for Groups
7. Group-related in-app notifications are enabled with the help of Sunbird Lern - Notification service.
8. Redis cache support can be enabled for caching groups list and the group details using configuration. For a user group list, the default caching time is 3600 seconds and that of each group detail is 86400 seconds.
9. Groups can be deleted only by the creator, not by the admin.
10. The user can activate or deactivate the group
11. The user can also edit and update the group based on the need
