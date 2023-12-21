# Component Diagram

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-08-17 at 9.37.07 AM.png" alt=""><figcaption></figcaption></figure>

Program Exhaust is a service that generates CSV file containing user details for those who has joined a program.

1. **Database Layer**:

* **PostgreSQL Database (job\_request)**: This is where job requests are stored. These requests include information about which users have requested reports.
* **Cassandra Database (user\_consent)**: This is where user consent data is stored. It contains information about whether users have agreed to share their PII data.
* **Cassandra Database (program\_enrollment)**: This is where program enrollment data is stored when a user joins new program.&#x20;
* **Redis Cache (user):** Contains cached user data that can be quickly retrieved.\
  \
  **Data provider**

| Database    | Table                             |
| ----------- | --------------------------------- |
| PostgreSQL  | job\_request                      |
| Redis Cache | user                              |
| Cassandra   | program\_enrolment, user\_consent |

2. **Data Processing Layer**:\
   Apache Spark is used to perform transformations, sort columns, eliminate duplicates, and replace unknown values with null. This process enhances data quality, organizes data logically before storing to CSV.

## **User Interaction Diagram**

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-08-17 at 9.38.40 AM.png" alt=""><figcaption></figcaption></figure>

This interaction diagram details the complete process of requesting and generating reports. The user can request a user info exhaust report through SunbirdEd from the program dashboard. Using exhaust APIs, this will map the request to SunbirdLern Which internally calls SunbirdObsrv service. userInfoExhaust data-product will be triggered by a scheduled cron task, which will query cassandra and redis to get data and process it using Spark to transform data and generate the report. The user receives the same report once it has been created.

## **CSV File Structure**

<table data-header-hidden><thead><tr><th width="189"></th><th width="149.33333333333331"></th><th width="156"></th><th></th></tr></thead><tbody><tr><td><strong>Format</strong></td><td><strong>Nomenclature</strong></td><td><strong>Example</strong></td><td><strong>Security Levels</strong></td></tr><tr><td><strong>CSV zip (Password protected)</strong></td><td><strong>program-user-exhaust/&#x3C;request_id>_&#x3C;UpdatedDate>.zip</strong></td><td><strong>9CD107F48B5AF0D163F8AE8410829674_20230622.zip</strong></td><td><strong>L3 - Data encrypted with a user provided encryption key. Generally applicable to non PII data but can contain sensitive information which may not be considered open</strong></td></tr></tbody></table>

## CSV Columns Contents <a href="#file-contents" id="file-contents"></a>

<table data-header-hidden><thead><tr><th width="160"></th><th width="139"></th><th width="118"></th><th></th></tr></thead><tbody><tr><td><strong>Column Label</strong></td><td><strong>Column Type</strong></td><td><strong>Data Type</strong></td><td><strong>Description</strong></td></tr><tr><td>User UUID</td><td>Static</td><td>String</td><td>The system generated unique user ID</td></tr><tr><td>User Name</td><td>Static</td><td>String</td><td>Name of the user(Firstname and Lastname)</td></tr><tr><td>Mobile Number</td><td>Static</td><td>String</td><td>User declared unmasked mobile number</td></tr><tr><td>Email ID</td><td>Static</td><td>String</td><td>User declared unmasked email ID</td></tr><tr><td>Consent Provided</td><td>Static</td><td>String</td><td>Yes/No. Flag to denote whether user has consented to the data sharing.</td></tr><tr><td>Consent Provided Date</td><td>Static</td><td>Date</td><td>Date when the user has consented to share the data</td></tr><tr><td>Program Name</td><td>Static</td><td>String</td><td>Program title</td></tr><tr><td>Program ID</td><td>Static</td><td>String</td><td>Unique Program Identifier.</td></tr><tr><td>State</td><td>Static</td><td>String</td><td>User declared state for self signed up users. If the user is a org validated user then the state as passed from org SSO or derived from sub-org ID.</td></tr><tr><td>District</td><td>Static</td><td>String</td><td>User declared district for self signed up users. If the user is a org validated user then the district as passed from org SSO or derived from sub-org ID.</td></tr><tr><td>Block</td><td>Static</td><td>String</td><td>Block name mapped to the user’s org/sub-org id</td></tr><tr><td>Cluster</td><td>Static</td><td>String</td><td>Cluster name mapped to the user’s org/sub-org id</td></tr><tr><td>School Id</td><td>Static</td><td>String</td><td>User declared school id for self signed up users. If the user is a org validated user then the school id as passed from org SSO or derived from sub-org ID</td></tr><tr><td>School Name</td><td>Static</td><td>String</td><td>School name mapped to the user’s org/sub-org id</td></tr><tr><td>User Type</td><td>Static</td><td>String</td><td>Type of the user</td></tr><tr><td>User Sub Type</td><td>Static</td><td>String</td><td>Sub Type of the user</td></tr><tr><td>Org Name</td><td>Static</td><td>String</td><td>Name of user org - Custodian for self signed up users and respective org name for org validated users</td></tr></tbody></table>

## Consent Fields <a href="#consent-fields" id="consent-fields"></a>

Following are the fields/columns that will be available in the CSV file only when the user consented for the data sharing.

| User Name       | Mobile number   | Email ID        |
| --------------- | --------------- | --------------- |
| On user consent | On user consent | On user consent |

## **Sample CSV Data**

<table><thead><tr><th width="146">User UUID</th><th width="125">User Name</th><th width="156">Mobile number</th><th width="255">Email ID</th><th width="183">Consent Provided</th><th width="220">Consent Provided Date</th><th width="147">Program Name</th><th width="124">Program ID</th><th>State</th><th>District</th><th>Block</th><th>Cluster</th><th width="107">School Id</th><th width="143">School Name</th><th width="121">Usertype</th><th>Usersubtype</th></tr></thead><tbody><tr><td>ef3733df-41e7-4bf1-b67c-091fd0762ee</td><td>opa5</td><td>7272272777</td><td>pao@test.com</td><td>false</td><td>01/01/23</td><td>'Prerak Head Teacher of the Block 19-20'</td><td>PGM-Prerak-Head-Teacher-of-the-Block-19-20-Feb2021</td><td>Uttar Pradesh</td><td>AGRA</td><td>ACHHNERA</td><td>ZPHS AGALI</td><td>9150206302</td><td>JHS NAGLA SADLE COMPOSITE</td><td>administrator</td><td>hm,dikshapreprodcustodian</td></tr></tbody></table>
