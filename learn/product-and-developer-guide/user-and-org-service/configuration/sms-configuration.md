# SMS Configuration

Create an account on [msg91](https://msg91.com/in) and login to get the [authKey](https://msg91.com/help/MSG91/where-can-i-find-my-authentication-key). Register the sender ID. Register the SMS template in the DLT portal and get a template ID. Add the approved template to the msg91 portal along with the template ID.

* [Step-by-step process to configure SMS](https://msg91.com/help/MSG91/step-by-step-process-to-configure-sms)
* [Where can I find my authentication key?](https://msg91.com/help/MSG91/where-can-i-find-my-authentication-key)
* [How to Add, Update, or Delete a sender ID (header) on MSG91?](https://msg91.com/help/MSG91/how-to-add-sender-id-in-msg91)
* [How to add or delete an SMS template?](https://msg91.com/help/MSG91/how-to-add-or-delete-an-sms-template)

#### Use the below msg91 curl to verify sending the SMS: <a href="#use-the-below-msg91-curl-to-verify-sending-the-sms" id="use-the-below-msg91-curl-to-verify-sending-the-sms"></a>

```
curl --location --request POST 'https://api.msg91.com/api/v2/sendsms' \
--header 'accept: application/json' \
--header 'authkey: <authkey>' \
--header 'content-type: application/json' \
--data-raw '{
  "sender": "<senderid registered with DLT>",
  "route": "4",
  "country": "91",
  "unicode": 1,
  "sms": [
    {
      "message": "<message registered with DLT>",
      "to": [
        "<mobilenumber>"
      ]
    }
  ],
  "DLT_TE_ID": "<template id of the message registered with DLT>"
}'
```

### smsTemplateConfig: <a href="#smstemplateconfig" id="smstemplateconfig"></a>

Once sending the SMS is verified using the above curl, configure the message template using the SystemSetting API in learner service using the below curl.

**Note:** Replace the `<DLT_TE_ID>` with the template ID of the message registered with DLT.

```
curl --location --globoff '{{host}}/v1/system/settings/set' \
--header 'Content-Type: application/json' \
--header 'Authorization: {{kong_api_key}}' \
--header '{{keycloak_access_token}}' \
--data '{
    "request": {
        "id": "smsTemplateConfig",
        "field": "smsTemplateConfig",
        "value": "{\"91SMS\":{\"OTP to verify your phone number on $installationName is $otp. This is valid for $otpExpiryInMinutes minutes only.\":\"<DLT_TE_ID>\",\"OTP to reset your password on $installationName is $otp. This is valid for $otpExpiryInMinutes minutes only.\":\"<DLT_TE_ID>\",\"Your ward has requested for registration on $installationName using this phone number. Use OTP $otp to agree and create the account. This is valid for $otpExpiryInMinutes minutes only.\":\"<DLT_TE_ID>\",\"Welcome to $instanceName. Your user account has now been created. Click on the link below to  set a password  and start using your account: $link\":\"<DLT_TE_ID>\",\"You can now access your diksha state teacher account using $phone. Please log out and login once again to see updated details.\":\"<DLT_TE_ID>\",\"VidyaDaan: Your nomination for $content has not been accepted. Thank you for your interest. Please login to https:\/\/vdn.diksha.gov.in for details.\":\"<DLT_TE_ID>\",\"VidyaDaan: Your nomination for $content is accepted. Please login to https:\/\/vdn.diksha.gov.in to start contributing content.\":\"<DLT_TE_ID>\",\"VidyaDaan: Your Content $content has not been approved by the project owner. Please login to https:\/\/vdn.diksha.gov.in for details.\":\"<DLT_TE_ID>\",\"VidyaDaan: Your Content $content has been approved by the project owner.\":\"<DLT_TE_ID>\",\"VidyaDaan: Your Content $contentName for the project $projectName has been approved by the project owner. Please login to $url for details.\":\"<DLT_TE_ID>\",\"VidyaDaan: Your Content $contentName for the project $projectName has been approved by the project owner with few changes. Please login to $url for details.\":\"<DLT_TE_ID>\",\"VidyaDaan: Your Content $contentName has not been accepted by your organization upon review. Please login to $url for details.\":\"<DLT_TE_ID>\",\"All your diksha usage details are merged into your accountAll your diksha usage details are merged into your account $installationName . The account $account has been deleted\":\"<DLT_TE_ID>\",\"Use OTP $otp to edit the contact details for your Diksha profile.\":\"<DLT_TE_ID>\"},\"NIC\":{\"NCERT: OTP to verify your phone number on $installationName is $otp. This is valid for $otpExpiryInMinutes minutes only.\":\"<DLT_TE_ID>\",\"NCERT: OTP to reset your password on $installationName is $otp. This is valid for $otpExpiryInMinutes minutes only.\":\"<DLT_TE_ID>\",\"NCERT: Your ward has requested for registration on $installationName using this phone number. Use OTP $otp to agree and create the account. This is valid for $otpExpiryInMinutes minutes only.\":\"<DLT_TE_ID>\",\"NCERT: Welcome to $instanceName. Your user account has now been created. Click on the link below to  set a password  and start using your account: $link\":\"<DLT_TE_ID>\",\"NCERT: You can now access your diksha state teacher account using $phone. Please log out and login once again to see updated details.\":\"<DLT_TE_ID>\",\"NCERT: Your nomination for $content has not been accepted. Thank you for your interest. Please login to $url for details.\":\"<DLT_TE_ID>\",\"NCERT: Your nomination for $content is accepted. Please login to $url to start contributing content.\":\"<DLT_TE_ID>\",\"NCERT: Your Content $content has not been approved by the project owner. Please login to $url for details.\":\"<DLT_TE_ID>\",\"NCERT: Your Content $contentName for the project $projectName has been approved by the project owner. Please login to $url for details.\":\"<DLT_TE_ID>\",\"NCERT: Your Content $contentName for the project $projectName has been approved by the project owner with few changes. Please login to $url for details.\":\"<DLT_TE_ID>\",\"NCERT: Your Content $contentName has not been accepted by your organization upon review. Please login to $url for details.\":\"<DLT_TE_ID>\",\"NCERT: All your diksha usage details are merged into your account $installationName . The account $account has been deleted\":\"<DLT_TE_ID>\"}}"
    }
}'
```

#### Verify the smsTemplateConfig by using the below curl: <a href="#verify-the-smstemplateconfig-by-using-the-below-curl" id="verify-the-smstemplateconfig-by-using-the-below-curl"></a>

```
curl --location --globoff '{{host}}/api/data/v1/system/settings/get/smsTemplateConfig' \
--header 'Accept: application/json' \
--header 'Authorization: {{kong_api_key}}'
```

#### Set the auth key and sender name as system env to user-org service, notification service and notification data pipeline job: <a href="#set-the-auth-key-and-sender-name-as-system-env-to-learner-service-notification-service-and-notificat" id="set-the-auth-key-and-sender-name-as-system-env-to-learner-service-notification-service-and-notificat"></a>

```
sunbird_msg_91_auth=<authKey> 
sunbird_msg_sender=<senderid registered with DLT>
sms_gateway_provider=91SMS // for a different provider like NIC , this varible will be set as NIC
```

&#x20;

\
