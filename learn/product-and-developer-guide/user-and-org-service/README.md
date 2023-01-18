# USER & ORG SERVICE

This component consists of various services which support user authentication, API management and token generation, Samza jobs for asynchronous notification along with user and organisation management.

![User Org service - Features](<../../../.gitbook/assets/image (21).png>)

### User & Org Service: <a href="#user-and-org-service" id="user-and-org-service"></a>

This service provides a set of APIs to manage the user, organisation, and location information.

1. **Location** - It is mainly the geographical location of the organisation or user. Currently, it supports - state, district, block, and cluster location types.
2. **Organisation** - Supports tenant or non-tenant organisations. Tenant organisation has to have a channel and slug which is unique. Non-tenant organisations should have a channel which is having a tenant mapped to it. There should be a default organisation called ‘custodian’ created during setup.
3. **User** - The user can be an LUA(Logged in User) or MUA(Managed User) user. LUA should have an email or phone number, which can be used for login. MUA will not have email and phone, their profile can be only used after logging in with LUA credentials. Each user should be mapped to the custodian or other tenant orgs.

### Terms:

#### **slug** &#x20;

* Slug is a text and its a set of characters, usually 2 to 4 in length, is used in a URL
* Slug and channel are abbreviations of organisation name, where a slug is a URL compatible, while the channel is not.
* Most often the channel and slug are the same, but it is not guaranteed.

**Ex:**  slug : channel1003

#### Channel

* Channel is a text and is Usually, a two-letter string that denotes a unique hashtagid registered in the global index.
* Channel is an entity in content-service(KP) against which framework, BGMS, and contents are mapped.
* It has a name, id/code, and description.
* Channel id/code can be the Organisation id or any dummy digits.
* It is independent of Organisation, but for the portal or app to use it, the channel id needs to be mapped to the organisation id.
* Channel abbreviations like '**tn'** and '**ka**' are not used in content-service(KP)
* Channel is a neo4j object, there is no tabular structure.
* The channel is ‘exactly’ the same for the rootOrg-subOrg combination.

**Ex:** channel: channel1003

#### Tenant Organisation

* While creating a tenant organisation in learner service, organisationid is passed to channel API to register it as a channel in content service.
* If the channel is already existing in content service then use the channel id/code as the organisation id.
* If tenant org needs to be created, then the channel should be registered in content-service, also it should be unique.
* Portal searches the tenant organisation using slug and this organisation id is passed in channel/v1/read to get the channel configurations and details from content-service.
* Tenant org and channel both are the same for the portal, only that different areas of the channel are handled by content-service(content, framework, BGMS) and learner service(user, location, user details).

#### Non-Tenant Organisation

* While creating a non-tenant organisation, mention an existing tenant's channel. This channel's org id is searched before creating a new organisation.
* If it is not a tenant org, then the channel should be internally mapped to a tenantOrg by specifying the tenant org channel.
* Non-tenant organisation - channel relation is not used in the portal

#### Org External Id

* Org External Id is a unique id of the external organisation.&#x20;

#### Organisation Type

* It will save the int values corresponding to the organisation types like board/school/contentOrg.&#x20;
*   The types will be represented with bit positions

    * bit 0 isBoard
    * bit 1 isSchool
    * bit 2 canCreateContent
    * bit 3 isBoard

    So the value in digit for board - 5, school - 2.

#### RootOrg Vs Tenant Org

* Most often the rootOrg and the tenant org are the same for representing the board, but it is not guaranteed.&#x20;
* RootOrg is a list of IDs of root organisations, and it is a list\<varChar>.

#### Tenant Association

* There are two tenant associations possible one is for the board and another one is for the school.

#### Non-Tenant Association

* Non-Tenant Associations will be declared as a custodian.
* and it's removed by hard delete.



**Adopters:** Diksha

**Contributors**: EkStep

**Last Release Date**: April 28, 2022

**Version:** 4.9.0
