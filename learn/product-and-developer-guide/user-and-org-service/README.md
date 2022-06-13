# USER & ORG SERVICE

This component consists of various services which support user authentication, API management and token generation, Samza jobs for asynchronous notification along with user and organisation management.

![User Org service - Features](<../../../.gitbook/assets/image (21).png>)

### User & Org Service: <a href="#user-and-org-service" id="user-and-org-service"></a>

This service provides a set of APIs to manage the user, organisation and location information.

1. **Location** - It is mainly the geographical location of the organisation or user. Currently it supports - state, district, block, cluster location types.
2. **Organisation** - Supports tenant or non-tenant organisation. Tenant organisation has to have a channel and slug which is unique. Non-tenant organisations should have a channel which is having a tenant mapped to it. There should be a default organisation called ‘custodian’ created during setup.
3. **User** - User can be a LUA(Logged in User) or MUA(Managed User) user. LUA should have an email or phone number, which can be used for login. MUA will not have email and phone, their profile can be only used after logging in with LUA credentials. Each user should be mapped to custodian or other tenant orgs.

***

**Adopters:** Diksha

**Contributors**: EkStep

**Last Release Date**: April 28 2022

**Version :** 4.9.0
