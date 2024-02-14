# Architecture

## UserOrg Service Architecture&#x20;

The below diagram represents the components involved and their arrangement in **UserOrg** service.

<div data-full-width="true">

<figure><img src="../../../../.gitbook/assets/LMS-ServiceFlowDiagram-User-Org Service.drawio.png" alt=""><figcaption><p>UserOrg Architecture</p></figcaption></figure>

</div>

### Flow Diagram:

<div data-full-width="true">

<figure><img src="../../../../.gitbook/assets/UserOrgServiceFlowDiagram-Simplyfied Overall-FlowDiagram.drawio.png" alt=""><figcaption><p>UserOrg Flow Diagram</p></figcaption></figure>

</div>

* User service includes multiple operations to creating new users and search the user.
* Keyclock for user authentication.
* Enabled Notification feature and messaging like Email and SMS on any operations performed.
* Updation of user details using jobs.
* OTP Creations on user merge action.
* Admin Util will do token verification.
* Content service is for to register the channel and framework validation.
* Userorg service will send an audit event to `{env}.telemetry.raw` topic. This event will be processed by pipeline-preprocessor(SB-Obsrv) and valid events will pushed to the audit topic to cache the user data by `user-cache-updater-v2` flink job.

{% embed url="https://youtu.be/VGHIhGWI-us?list=PLUrm4D0K_7nxlaZZYirokpx5Mo-jMd64M&t=450" %}
User-Org Highlevel Architecture
{% endembed %}
