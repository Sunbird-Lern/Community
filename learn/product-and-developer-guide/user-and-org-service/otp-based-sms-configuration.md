# OTP based SMS Configuration

An OTP sent via SMS to the user’s registered mobile number is one of the most secure and efficient ways to authenticate users for specific transactions. For example, if a user wants to reset the password, configure the text message to be sent via SMS along with the generated OTP in Keycloak. To configure the text messages, complete the following steps:

1. Enter your Username or email and Password
2. Click Log in to log into the Keycloak admin console

<figure><img src="../../../.gitbook/assets/keycloak_login (1) (1).png" alt=""><figcaption></figcaption></figure>

3\. Click the Realm Selector dropdown from the navigation pane and select an appropriate realm Note: The Master realm is selected by default.

<figure><img src="../../../.gitbook/assets/realm_select.png" alt=""><figcaption></figcaption></figure>

4\. Go to the Configure section and select the Authentication tab.

<figure><img src="../../../.gitbook/assets/selectauthenticationsection.png" alt=""><figcaption></figcaption></figure>

5\. Go to the Flows tab, select Reset Credentials With SMS OTP option from the drop-down list.

<figure><img src="../../../.gitbook/assets/selectflows.png" alt=""><figcaption></figcaption></figure>

6\. Select Actions as _Config_ for SMS Authentication (Reset credentials with SMS OTP).

<figure><img src="../../../.gitbook/assets/selectconfig.png" alt=""><figcaption></figcaption></figure>

7\. Change the text for Template of text to send to the user with the actual text of the message to be sent to users while sending the OTP SMS.

<figure><img src="../../../.gitbook/assets/changesmsotp.png" alt=""><figcaption></figcaption></figure>
