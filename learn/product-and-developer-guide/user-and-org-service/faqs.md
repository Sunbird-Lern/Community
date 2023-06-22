# FAQs

User Registration and Login : FAQs&#x20;

a) I’ve not received my OTP&#x20;

* Either the learner-service is not working or failures at MSG91/Sendgrid side. &#x20;
* Also the limit exceeded in MSG91/Sendgrid.&#x20;

b) My login is not successful (SSU)&#x20;

If all users or majority of the users are impacted then it could be an issue with Keycloak or learner service. &#x20;

* Check for authentication failures b/w portal/app to keycloak&#x20;
* Check for user lookup failures b/w keycloak and learner service&#x20;

b) My login is not successful (SSO)&#x20;

* Could be an issue with state portal/state token.&#x20;
* State is not in whitelisted state list&#x20;
* School is not registered with us&#x20;
* Check for authentication failures b/w portal/app to keycloak&#x20;
* Check for user lookup failures b/w keycloak and learner service&#x20;
* Check for user read with external id failures in learner service&#x20;

&#x20;

c) I’m not able to register/create an account (SSU)&#x20;

* Check for failures b/w portal/app and user exists API&#x20;
* Check for authentication failures b/w portal/app to keycloak&#x20;
* OTP generation failures&#x20;
* OTP verification failures&#x20;
* User signup API (SSU) failures in learner service&#x20;

c) I’m not able to register/create an account (SSO)&#x20;

* Could be an issue with state portal/state token.&#x20;
* State is not in whitelisted state list&#x20;
* School is not registered with us&#x20;
* Check for authentication failures b/w portal/app to keycloak&#x20;
* Check for user lookup failures b/w keycloak and learner service&#x20;
* Check for user read with external id failures in learner service&#x20;
* OTP generation failures&#x20;
* OTP verification failures&#x20;
* Migrate User failure if already have an SSU account with same email or phone&#x20;
* User create(v3/create) API (SSO) failures&#x20;

&#x20;

d) I’m not able to migrate my account&#x20;

* Migrate User API failure &#x20;

&#x20;

e) I’m not able to merge &#x20;

* Merge User API failure &#x20;

&#x20;

f) Unable to update my profile page&#x20;

* User Update API failure in learner-service&#x20;

g) My location details are shown incorrectly in the progress exhaust/profile page&#x20;

* User Update API failure in learner-service&#x20;
