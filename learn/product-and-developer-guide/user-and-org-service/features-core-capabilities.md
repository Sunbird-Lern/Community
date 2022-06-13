# Features/Core capabilities

### **Key Features:**

| Feature                        | Description                                                                                                                                                                         |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| User Management (CRUD)         | Creation of LUA and MUA users and updating user profile, fetching user information, block and unblock user, associating user with organisation etc are implemented via this feature |
| Organisation Management (CRUD) | This feature provides CRUD APIs for maintaining organisation details.                                                                                                               |
| Location Management (CRUD)     | Provides CRUD APIs for managing location master data.                                                                                                                               |
| Consent Management             | This helps to capture user consent to share the PII in organisation level and course collection level.                                                                              |
| OTP Services                   | Helps to generate OTP and send notification either through email or phone. Also OTP validation, expiry, rate limit are managed using this feature.                                  |
| Notes Management               | User can capture notes when content is being played. This service provides the CRUD APIs for the same.                                                                              |
| Tenant Configurations          | This service can be used to maintain tenant organisation level configurations.                                                                                                      |
| Backend Services               | Admins can upload master data in to location, organisation. This service allows to create users and update user information.                                                        |
| <p><br>System Settings</p>     | This service is used to configure system / application settings like default organisation, various T\&C etc                                                                         |

Reports generated :

1. Geo-report
   * geo-summary shows the number of schools, districts and blocks in a particular channel.
   * geo-summary-district shows the data with respect to district.
2. User-consent report
   * Consent Report gives the user info channel-wise as per the consent given by user
