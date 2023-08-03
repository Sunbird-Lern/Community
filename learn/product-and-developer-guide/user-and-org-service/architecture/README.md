# Architecture

## UserOrg Service Architecture&#x20;

The below diagram represents the components involved and their arrangement in **UserOrg** service.

<div data-full-width="true">

<figure><img src="../../../../.gitbook/assets/LMS-ServiceFlowDiagram-User-Org Service.drawio.png" alt=""><figcaption><p>UserOrg Architecture</p></figcaption></figure>

</div>

### Flow Diagram:

<div data-full-width="true">

<figure><img src="../../../../.gitbook/assets/UserOrgServiceFlowDiagram-Overall-FlowDiagram.drawio (1).png" alt=""><figcaption><p>UserOrg Flow Diagram</p></figcaption></figure>

</div>

* User service includes multiple operations to creating new users and search the user.
* Keyclock for user authentication.
* Enabled Notification feature and messaging like Email and SMS on any operations performed.
* Updation of user details using jobs.
* OTP Creations on user merge action.
* Admin Util will do token verification.
* Content service is for to register the channel and framework validation.
