# FAQs

1. Which flink job in Lern data-pipeline triggers certificate generation?&#x20;
   * Collection Certificate Generator
2. UserOrg Service is built on which framework?&#x20;
   * Play-Akka
3. Which building block is used by Lern to generate, sign and store certificates?&#x20;
   * Sunbird-RC
4. How is Tenant organisation id in UserOrg linked to Channel in content service?&#x20;
   * Channel Code
5. Which dataproduct is used to update course batch status?&#x20;
   * CourseBatchStatusUpdater &#x20;
6. Which tool is used for authentication management in Sunbird?&#x20;
   * Keycloak
7. Which is the secondary data store in UserOrg service?&#x20;
   * ElasticSearch
8. Which technology is commonly used to build micro services in sunbird Lern?&#x20;
   * Java&#x20;
9. Which authentication mechanism is commonly used in Subird microservices?&#x20;
   * JSON&#x20;
10. Default SMS provider in Sunbird?&#x20;
    * MSG91
11. Default SMTP provider in Sunbird?&#x20;
    * Sendgrid
12. Denormalisation of user data is done by which flink job in Lern data-pipeline?&#x20;
    * User-cache-updater&#x20;
13. Which framework is used to implement data-pipeline in Sunbird-Lern?&#x20;
    * Flink Spark&#x20;
14. Which data processing framework is used to implement data-products in Sunbird-Lern?&#x20;
    * Spark
15. On-demand exhaust jobs in Lern are scheduled jobs, which generate reports if a user request is available at scheduled time&#x20;
    * TRUE&#x20;
16. Standard exhaust jobs in Lern are scheduled jobs, which generate reports at scheduled time without any user request&#x20;
    * TRUE&#x20;
17. Cloud-store-sdk library in maven helps Sunbird Lern to be cloud agnostic
    * TRUE &#x20;
18. How many MUAs(Managed User Accounts) can be created by default by an LUA(LogIn User Accounts) in UserOrg service?&#x20;
    * 30&#x20;
19. Default Tenant Organisation in Sunbird is referred as CustodianOrg
20. Default cloud service provider in sunbird?&#x20;
    * Azure
21. After creating a user using the API, the password couldn't be updated, resulting in the error message, **"User is created but password couldn't be updated"**
    * Checked Cassandra provider in user federation and ensured channels are available in Cassandra DB.&#x20;
    * Verified Keycloak environment variables, and if an issue is found, rebuild and redeploy Keycloak from Jenkins.&#x20;
    * Confirmed that Ingress IP is properly updated in Keycloak configuration.&#x20;
    * Checked and updated variables in the private repo, specifically related to public keys.&#x20;
    * Ensured that recaptcha is set to false in the Player service configmap.&#x20;
    * Restarted the Player pod after making configuration changes.&#x20;
    * Verified mandatory variables in the installation documentation were filled before deployment.
    * Resolved certificate-related issues by updating the certificate chain CRT file.&#x20;
    * Checked if the user is visible in the system after creation and looked for errors in the learner service.&#x20;
    *   Fixed the "unable to verify the first certificate" issue by updating the certificate chain CRT file.

        **Note:** All mandatory variables mentioned in the installation documentation should be filled before deployment. Recaptcha settings and certificate updates are crucial for resolving password update issues.

        \
        **For more details check the below DF threads,**
    * [https://github.com/orgs/Sunbird-Ed/discussions/306](https://github.com/orgs/Sunbird-Ed/discussions/306)&#x20;
    * [https://github.com/orgs/Sunbird-Ed/discussions/678](https://github.com/orgs/Sunbird-Ed/discussions/678)
22. I'm unable to change preferences for a logged-in user. How can I fix this issue?
    * Identify the Missing Field:&#x20;
      * Check the **user profile** system settings.&#x20;
      * Ensure that the missing field is present under the framework.
    * If you cannot find then, Update System Settings:&#x20;
      * Use the update system settings API to set the missing framework fields:
      * Verify and Close: Ensure the necessary system settings are updated. Confirm that the reported issue no longer occurs.
23. "I've uploaded the encryption key for my organization. How do I verify if the upload was successful?
    * If you haven't uploaded an encryption key for your organization yet, please do so by following the steps outlined [**here**](https://lern.sunbird.org/use/release-notes/release-v-5.3.0#data-security-policy-setup-1)
    * After uploading the key, you can verify the success of the upload by running the following cURL command for the organization read API.

```url
curl --location 'https://dev.sunbirded.org/api/org/v1/read' \
--header 'Content-Type: application/json' \
--header 'Authorization: {{kong_api_key}}' \
--data '{
  "request": {
    "organisationId": "{{org_id}}"
  }
}'
```

* In the response, look for the 'keys' section to find the URL of the uploaded encryption key for your organization.

```json
"keys": {
                "exhaustEncryptionKey": [
                    "{{url of encryption key/pem file}}"
                ]
        },
```

24. &#x20;When using the user bulk upload API, if I set `orgExternalId` it to null, I get a notification to onboard. But I don't get the notification if I set it to a value. How can I debug/fix this"
    * To debug/fix:
      * Perform a user read to identify the organization ID of the user.
      * Perform an org search using this ID and find the external ID in the response.
      * Use the external ID from the response in your upload. If the external ID is null, don't pass any value for it.
