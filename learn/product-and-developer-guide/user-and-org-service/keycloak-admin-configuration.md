---
description: Configure Keycloak to Generate Link for Required User Action
coverY: 0
---

# Keycloak Admin Configuration

### Overview <a href="#overview" id="overview"></a>

A new user can be created in Sunbird in the following two ways:

* Self sign-up using Sunbird where user can provide email, phone and password during user creation
* Bulk users creation by Organisation Admin where an initial password is not yet set

The Sunbird requires users to either verify email (when user is created by self sign-up) or set password (when users are created by bulk upload) for the first time before they are able to log in to Sunbird.

The verify email or set password link is sent to the newly created users via email and/or SMS. The generated link also consists of a redirect URI to which the user is redirected after completing the required action.

This document explains the configuration required in Keycloak to generate links for the required action to be performed by a new user.

### Configure Environment Variables <a href="#configure-environment-variables" id="configure-environment-variables"></a>

Following environment variables need to be configured in Sunbird LMS service for generating required action links:

* sunbird\_sso\_url
* sunbird\_sso\_username
* sunbird\_sso\_password
* sunbird\_sso\_realm
* sunbird\_sso\_client\_id
* sunbird\_url\_shortner\_enable
* sunbird\_url\_shortner\_access\_token
* sunbird\_keycloak\_required\_action\_link\_expiration\_seconds

> Note: For details on the environment variables, refer to [Sunbird LMS Service Environment Variables](http://docs.sunbird.org/latest/developer-docs/configuring\_sunbird/env\_variables\_lms/).
>
> ### Configure Administrator Role <a href="#configure-administrator-role" id="configure-administrator-role"></a>
>
> It is mandatory to configure a user with administrator role permissions to be able to generate the required action link in Keycloak.

1\. Enter your Username or email and Password\
2\. Click Log in to log into the Keycloak admin console

<figure><img src="../../../.gitbook/assets/keycloak_login (1).png" alt=""><figcaption></figcaption></figure>

3\. Click the Realm Selector dropdown from the navigation pane and select the appropriate realm.\
Note: The Master realm is selected by default

<figure><img src="../../../.gitbook/assets/realm_select.png" alt=""><figcaption></figcaption></figure>

4\. Go to the Configure section and select the Roles tab

<figure><img src="../../../.gitbook/assets/roles_selector (1).PNG" alt=""><figcaption></figcaption></figure>

5\. Go to the Realms Roles tab, click the Add Role button if the administrator role is not available in the Realm Roles table. If the role is available, then proceed to step 5

<figure><img src="../../../.gitbook/assets/add_admin_role (1).PNG" alt=""><figcaption></figcaption></figure>

6\. Go to the Users tab under the Manage section and search the user in the Lookup tab

<figure><img src="../../../.gitbook/assets/select_user_selector_and_search_for_ admin_user.PNG" alt=""><figcaption></figcaption></figure>

7\. Click the Role Mappings tab

<figure><img src="../../../.gitbook/assets/user_role_mapping.PNG" alt=""><figcaption></figcaption></figure>

8\. Assign the admin role at realm level

<figure><img src="../../../.gitbook/assets/add_admin_role_to_user.PNG" alt=""><figcaption></figcaption></figure>

9\. Select the client option from the Client Roles drop-down list to which the user belongs and assign admin role at the client level

<figure><img src="../../../.gitbook/assets/admin_role_added.PNG" alt=""><figcaption></figcaption></figure>

### Configure Redirect URI <a href="#configure-redirect-uri" id="configure-redirect-uri"></a>

The redirect URI configuration is necessary to redirect user to Sunbird tenant’s specific home page after completing the required action steps.

1\. Go to the Configure section and select the Clients tab in the navigation pane

<figure><img src="../../../.gitbook/assets/client_list.PNG" alt=""><figcaption></figcaption></figure>

2\. Click the client corresponding to the user configured in step 8 of above section

<figure><img src="../../../.gitbook/assets/select_user_client (1).PNG" alt=""><figcaption></figcaption></figure>

3\. Select the Settings tab and click the Implicit Flow Enabled toggle button. Once this button is enabled, a Valid Redirect URIs text box is displayed

<figure><img src="../../../.gitbook/assets/in_settings_tab_enabl_implicit_flow_enabled.PNG" alt=""><figcaption></figcaption></figure>

4\. Enter values in the Root URL and Valid Redirect URIs text boxes

<figure><img src="../../../.gitbook/assets/config-url.PNG" alt=""><figcaption></figcaption></figure>

***



\
