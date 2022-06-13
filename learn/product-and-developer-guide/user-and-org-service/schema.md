# Schema

### ER Diagram

### User & Org **Keyspace Creation**

![](../../../.gitbook/assets/sunbird\_user\_org.png)

```
CREATE KEYSPACE IF NOT EXISTS sunbird WITH replication = {'class':'SimpleStrategy','replication_factor':1};CREATE TABLE IF NOT EXISTS  sunbird.user(id text,userId text,userName text, email text,phone text,aadhaarNo text,createdDate text,updatedDate text,updatedBy text,
```

Cassandra Migration in [sunbird-utils](https://github.com/project-sunbird/sunbird-utils) needs to be run before user\&org service run to create necessary tables required in sunbird keyspace.

### **Table Creation in Cassandra**

```
CREATE TABLE sunbird.user (
    id text PRIMARY KEY,
    alltncaccepted map<text, text>,
    channel text,
    countrycode text,
    createdby text,
    createddate text,
    dob text,
    email text,
    emailverified boolean,
    firstname text,
    flagsvalue int,
    framework map<text, frozen<list<text>>>,
    isdeleted boolean,
    lastname text,
    locationids list<text>,
    loginid text,
    managedby text,
    maskedemail text,
    maskedphone text,
    phone text,
    phoneverified boolean,
    prevusedemail text,
    prevusedphone text,
    profilelocation text,
    profileusertype text,
    profileusertypes text,
    recoveryemail text,
    recoveryphone text,
    roles list<text>,
    rootorgid text,
    status int,
    tncacceptedon timestamp,
    tncacceptedversion text,
    updatedby text,
    updateddate text,
    userid text,
    username text,
    usersubtype text,
    usertype text
);
```

```
CREATE TABLE sunbird.organisation (
    id text PRIMARY KEY,
    channel text,
    contactdetail text,
    createdby text,
    createddate text,
    description text,
    email text,
    externalid text,
    hashtagid text,
    isrootorg boolean,
    isssoenabled boolean,
    istenant boolean,
    keys map<text, frozen<list<text>>>,
    locationids list<text>,
    organisationtype int,
    orglocation text,
    orgname text,
    provider text,
    rootorgid text,
    slug text,
    status int,
    updatedby text,
    updateddate text
);
```

```
CREATE TABLE sunbird.system_settings (
    id text PRIMARY KEY,
    field text,
    value text
);
```

```
CREATE TABLE sunbird.location (
    id text PRIMARY KEY,
    code text,
    name text,
    parentid text,
    type text
);
```

```
CREATE TABLE sunbird.action_group (
    id text PRIMARY KEY,
    actionid list<text>,
    groupname text
);
```

```
CREATE TABLE sunbird.address (
    id text PRIMARY KEY,
    addressline1 text,
    addressline2 text,
    addtype text,
    city text,
    country text,
    createdby text,
    createddate text,
    isdeleted boolean,
    state text,
    updatedby text,
    updateddate text,
    userid text,
    zipcode text
);
```

```
CREATE TABLE sunbird.bulk_upload_process (
    id text PRIMARY KEY,
    createdby text,
    createdon timestamp,
    data text,
    failureresult text,
    lastupdatedon timestamp,
    objecttype text,
    organisationid text,
    processendtime text,
    processstarttime text,
    retrycount int,
    status int,
    storagedetails text,
    successresult text,
    taskcount int,
    telemetrycontext map<text, text>,
    uploadedby text,
    uploadeddate text
);
CREATE INDEX inx_status ON sunbird.bulk_upload_process (status);
```

```
CREATE TABLE sunbird.bulk_upload_process_task (
    processid text,
    sequenceid int,
    createdon timestamp,
    data text,
    failureresult text,
    iterationid int,
    lastupdatedon timestamp,
    status int,
    successresult text,
    PRIMARY KEY (processid, sequenceid)
);
```

```
CREATE TABLE sunbird.cassandra_migration_version (
    version text PRIMARY KEY,
    checksum int,
    description text,
    execution_time int,
    installed_by text,
    installed_on timestamp,
    installed_rank int,
    script text,
    success boolean,
    type text,
    version_rank int
);
```

```
CREATE TABLE sunbird.cassandra_migration_version_counts (
    name text PRIMARY KEY,
    count counter
);
```

```
CREATE TABLE sunbird.cert_registry (
    id text PRIMARY KEY,
    accesscode text,
    createdat timestamp,
    createdby text,
    data text,
    isrevoked boolean,
    jsonurl text,
    pdfurl text,
    reason text,
    recipient text,
    related text,
    updatedat timestamp,
    updatedby text
);
```

```
CREATE TABLE sunbird.config_path_audit (
    id text,
    cloud_store_type text,
    created_date bigint,
    cloud_store_account text,
    cloud_store_container text,
    cloud_store_path text,
    version bigint,
    PRIMARY KEY ((id, cloud_store_type), created_date)
);
CREATE INDEX inx_created_date ON sunbird.config_path_audit (created_date);
```

```
CREATE TABLE sunbird.email_template (
    name text PRIMARY KEY,
    createdby text,
    createdon timestamp,
    lastupdatedby text,
    lastupdatedon timestamp,
    template text
);
```

```
CREATE TABLE sunbird.geo_location (
    id text PRIMARY KEY,
    createdby text,
    createddate text,
    location text,
    rootorgid text,
    topic text,
    type text,
    updatedby text,
    updateddate text,
    usercount int,
    usercountttl text
);
CREATE INDEX inx_gl_rootorgid ON sunbird.geo_location (rootorgid);
```

```
CREATE TABLE sunbird.master_action (
    id text PRIMARY KEY,
    name text
);
CREATE INDEX inx_ma_name ON sunbird.master_action (name);
```

```
CREATE TABLE sunbird.media_type (
    id text PRIMARY KEY,
    name text
);
```

```
CREATE TABLE sunbird.org_external_identity (
    provider text,
    externalid text,
    orgid text,
    PRIMARY KEY (provider, externalid)
);
```

```
CREATE TABLE sunbird.otp (
    type text,
    key text,
    attemptedcount int,
    createdon timestamp,
    otp text,
    PRIMARY KEY (type, key)
);
```

```
CREATE TABLE sunbird.page_management (
    id text PRIMARY KEY,
    appmap text,
    created_date timestamp,
    createdby text,
    createddate text,
    name text,
    organisationid text,
    portalmap text,
    updated_date timestamp,
    updatedby text,
    updateddate text
);
```

```
CREATE TABLE sunbird.page_section (
    id text PRIMARY KEY,
    alt text,
    created_date timestamp,
    createdby text,
    createddate text,
    datasource text,
    description text,
    display text,
    dynamicfilters text,
    imgurl text,
    name text,
    searchquery text,
    sectiondatatype text,
    status int,
    updated_date timestamp,
    updatedby text,
    updateddate text
);
```

```
CREATE TABLE sunbird.rate_limit (
    key text,
    unit text,
    count int,
    rate int,
    PRIMARY KEY (key, unit)
);
```

```
CREATE TABLE sunbird.report_tracking (
    id text PRIMARY KEY,
    createddate text,
    data text,
    email text,
    fileurl text,
    firstname text,
    format text,
    period text,
    resourceid text,
    resourcename text,
    status int,
    trycount int,
    type text,
    updateddate text,
    uploadeddate text,
    userid text
);
CREATE INDEX inx_report_tracking_userid ON sunbird.report_tracking (userid);
CREATE INDEX inx_report_tracking_status ON sunbird.report_tracking (status);
```

```
CREATE TABLE sunbird.role (
    id text PRIMARY KEY,
    name text,
    rolegroupid list<text>,
    status int
);
```

```
CREATE TABLE sunbird.role_group (
    id text PRIMARY KEY,
    name text,
    url_action_ids list<text>
);
```

```
CREATE TABLE sunbird.shadow_user (
    channel text,
    userextid text,
    addedby text,
    attemptedcount int,
    claimedon timestamp,
    claimstatus int,
    createdon timestamp,
    email text,
    name text,
    orgextid text,
    phone text,
    processid text,
    updatedon timestamp,
    userid text,
    userids list<text>,
    userstatus int,
    PRIMARY KEY (channel, userextid)
);
CREATE INDEX inx_shausr_userextid ON sunbird.shadow_user (userextid);
CREATE INDEX inx_shausr_userstatus ON sunbird.shadow_user (userstatus);
CREATE INDEX shadow_user_userids_idx ON sunbird.shadow_user (values(userids));
CREATE INDEX inx_shausr_claimstatus ON sunbird.shadow_user (claimstatus);
CREATE INDEX inx_shausr_userid ON sunbird.shadow_user (userid);
CREATE INDEX inx_shausr_processid ON sunbird.shadow_user (processid);
CREATE INDEX inx_shausr_orgextid ON sunbird.shadow_user (orgextid);
```

```
CREATE TABLE sunbird.tenant_preference (
    id text PRIMARY KEY,
    data text,
    key text,
    orgid text,
    role text,
    tenantname text
);
CREATE INDEX inx_tp_key ON sunbird.tenant_preference (key);
CREATE INDEX inx_tp_userid ON sunbird.tenant_preference (orgid);
```

```
CREATE TABLE sunbird.tenant_preference_v2 (
    orgid text,
    key text,
    createdby text,
    createdon timestamp,
    data text,
    updatedby text,
    updatedon timestamp,
    PRIMARY KEY (orgid, key)
);
```

```
CREATE TABLE sunbird.url_action (
    id text PRIMARY KEY,
    name text,
    url list<text>
);
CREATE INDEX inx_ua_url ON sunbird.url_action (values(url));
CREATE INDEX inx_ua_name ON sunbird.url_action (name);
```

```
CREATE TABLE sunbird.user_action_role (
    id text PRIMARY KEY,
    actiongroupid list<text>,
    roleid text
);
```

```
CREATE TABLE sunbird.user_cert (
    id text PRIMARY KEY,
    accesscode text,
    createdat timestamp,
    isdeleted boolean,
    oldid text,
    store map<text, text>,
    updatedat timestamp,
    userid text
);
CREATE INDEX inx_usrcert_user_id ON sunbird.user_cert (userid);
```

```
CREATE TABLE sunbird.user_consent (
    user_id text,
    consumer_id text,
    object_id text,
    categories list<text>,
    consent_data text,
    consumer_type text,
    created_on timestamp,
    expiry timestamp,
    id text,
    last_updated_on timestamp,
    object_type text,
    status text,
    PRIMARY KEY (user_id, consumer_id, object_id)
);
```

```
CREATE TABLE sunbird.user_declarations (
    userid text,
    orgid text,
    persona text,
    createdby text,
    createdon timestamp,
    errortype text,
    status text,
    updatedby text,
    updatedon timestamp,
    userinfo map<text, text>,
    PRIMARY KEY (userid, orgid, persona)
);
```

```
CREATE TABLE sunbird.user_feed (
    id text PRIMARY KEY,
    category text,
    createdby text,
    createdon timestamp,
    data text,
    expireon timestamp,
    priority int,
    status text,
    updatedby text,
    updatedon timestamp,
    userid text
);
CREATE INDEX user_feed_category_idx ON sunbird.user_feed (category);
CREATE INDEX user_feed_userid_idx ON sunbird.user_feed (userid);
```

```
CREATE TABLE sunbird.user_lookup (
    type text,
    value text,
    userid text,
    PRIMARY KEY ((type, value))
);
```

```
CREATE TABLE sunbird.user_notes (
    id text PRIMARY KEY,
    contentid text,
    courseid text,
    createdby text,
    createddate text,
    isdeleted boolean,
    note text,
    tags list<text>,
    title text,
    updatedby text,
    updateddate text,
    userid text
);
```

```
CREATE TABLE sunbird.user_org (
    id text PRIMARY KEY,
    addedby text,
    addedbyname text,
    approvaldate text,
    approvedby text,
    hashtagid text,
    isapproved boolean,
    isdeleted boolean,
    isrejected boolean,
    organisationid text,
    orgjoindate text,
    orgleftdate text,
    position text,
    roles list<text>,
    updatedby text,
    updateddate text,
    userid text
);
CREATE INDEX inx_uorg_userid ON sunbird.user_org (userid);
CREATE INDEX inx_uorg_orgid ON sunbird.user_org (organisationid);
```

```
CREATE TABLE sunbird.user_organisation (
    userid text,
    organisationid text,
    addedby text,
    addedbyname text,
    approvaldate text,
    approvedby text,
    associationtype int,
    hashtagid text,
    id text,
    isapproved boolean,
    isdeleted boolean,
    isrejected boolean,
    orgjoindate text,
    orgleftdate text,
    position text,
    roles list<text>,
    updatedby text,
    updateddate text,
    PRIMARY KEY (userid, organisationid)
);
```

```
CREATE TABLE sunbird.user_roles (
    userid text,
    role text,
    createdby text,
    createddate text,
    scope text,
    updatedby text,
    updateddate text,
    PRIMARY KEY (userid, role)
);
```

```
CREATE TABLE sunbird.user_skills (
    id text PRIMARY KEY,
    createdby text,
    createdon timestamp,
    endorsementcount int,
    endorserslist frozen<list<frozen<map<text, text>>>>,
    lastupdatedby text,
    lastupdatedon timestamp,
    skillname text,
    skillnametolowercase text,
    userid text
);
CREATE INDEX inx_us_userid ON sunbird.user_skills (userid);
```

```
CREATE TABLE sunbird.usr_external_identity (
    provider text,
    idtype text,
    externalid text,
    createdby text,
    createdon timestamp,
    lastupdatedby text,
    lastupdatedon timestamp,
    originalexternalid text,
    originalidtype text,
    originalprovider text,
    userid text,
    PRIMARY KEY (provider, idtype, externalid)
) ;
CREATE INDEX inx_usrextid_user_id ON sunbird.usr_external_identity (userid);
```

#### Insert Values into Tables:

**Example**:

```
cqlsh:sunbird> insert into sunbird.system_settings (id,field,value) values ('custodianOrgId','custodianOrgId','0130144097756938240');
```

```
cqlsh:sunbird> insert into sunbird.system_settings (id,field,value) values ('userProfileConfig','userProfileConfig','{"fields":["firstName","lastName","profileSummary","avatar","countryCode","dob","email","gender","grade","language","location","phone","subject","userName","webPages","jobProfile","address","education","skills","badgeAssertions"],"publicFields":["firstName","lastName","profileSummary"],"privateFields":["email","phone"],"csv":{"supportedColumns":{"NAME":"firstName","MOBILE PHONE":"phone","EMAIL":"email","SCHOOL ID":"orgId","USER_TYPE":"userType","ROLES":"roles","USER ID":"userId","SCHOOL EXTERNAL ID":"orgExternalId"},"outputColumns":{"userId":"USER ID","firstName":"NAME","phone":"MOBILE PHONE","email":"EMAIL","orgId":"SCHOOL ID","orgName":"SCHOOL NAME","userType":"USER_TYPE","orgExternalId":"SCHOOL EXTERNAL ID"},"outputColumnsOrder":["userId","firstName","phone","email","organisationId","orgName","userType","orgExternalId"],"mandatoryColumns":["firstName","userType","roles"]},"read":{"excludedFields":["avatar","jobProfile","address","education","webPages","skills"]},"framework":{"fields":["board","gradeLevel","medium","subject","id"],"mandatoryFields":["board","gradeLevel","medium","id"]}}');
```

```
cqlsh:sunbird> insert into sunbird.system_settings (id,field,value) values ('orgProfileConfig','orgProfileConfig','{"csv":{"supportedColumns":{"SCHOOL NAME":"orgName","BLOCK CODE":"locationCode","STATUS":"status","SCHOOL ID":"organisationId","EXTERNAL ID":"externalId","DESCRIPTION":"description"}, "outputColumns": {"organisationId":"SCHOOL ID","orgName":"SCHOOL NAME","locationCode":"BLOCK CODE","locationName":"BLOCK NAME","externalId":"EXTERNAL ID"}, "outputColumnsOrder":["organisationId","orgName","locationCode", "locationName","externalId"],"mandatoryColumns":["orgName","locationCode","status"]}}');
```
