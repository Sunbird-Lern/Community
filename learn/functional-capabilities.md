---
description: Functional capabilities enabled by Sunbird Lean
---

# Functional Capabilities

These functional capabilities are powered by different Sunbird Lern components - which can be configured by an adopter based on their specific needs.

* **User account creation and management, user login as well as platform administration capabilities** - these are powered by the [`User and Org Service`](product-and-developer-guide/user-and-org-service/) component of Sunbird Lern
  * Enable users to create accounts to save their platform preferences, access relevant content based on their preferences etc. Users with accounts on the system who login also get access to richer platform features such as Courses and Learner passbook.
  * Platform administrators can be granted capabilities to manage user roles on the platform, as well as manage platform master data (eg. Location data, Framework values etc.)
  * Configure the platform to allow for user logins via various mechanisms including username/ password, Google login or single sign-on with other approved systems
*   **Enable batches of students to take courses on the platform**: Create and manage a course batch - this allows for a cohort of users to take the course within a specified time frame, review user course progress or assessment performance, issue rule based certificates for course completion, merit scores etc.

    The [`Batch Service`](product-and-developer-guide/batch-service/) component of the Lern Building block is used to power these capabilities within Sunbird Lern.
*   **Allow users on the platform to collaborate**: Sunbird Lern components can be configured to give users on the platform collaboration capabilities. These components include the Groups Service as well as Discussion Forums. The functionalities enabled by the Groups component includes the ability for users to create a Group on the platform, add/ remove users from the group, as well as assign activities (content, assessments etc) for the users in the group to undertake. The Group creator is also able to track how much of the activities the users have completed. A Group can also have a Dicussion Forum attached to it, which allows a user to start or contribute to discussions on relevant topics. Such capabilities allow for users to learn together as a cohort, as well as engage in useful collaborative activities to further their learning.

    The components used to enable collaboration include [`Groups`](product-and-developer-guide/groups/) as well as [`Discussion Forum`](product-and-developer-guide/discussion-forum/).
* **Configure the platform to be able to send notifications to users on events of choosing** - these could be user driven or system driven events. This capability is enabled via the [`Notification service`](product-and-developer-guide/notification-service/) component.

Various components of Lern permit for different configurations, allowing the system to enable different workflows based on specific requirements. Learn more about the configurations that each component allows for, on the pages for each of the specific components.
