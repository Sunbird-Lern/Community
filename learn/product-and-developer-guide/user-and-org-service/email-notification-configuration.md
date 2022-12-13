# Email Notification Configuration

### Overview <a href="#overview" id="overview"></a>

The content published on Sunbird undergoes review to ensure its adherance to defined guidelines and standards set by the organization. Each organization sets standard guidelines based on their organizational ideologies. Sunbird has the feature to notifying content creators about the status of their content which is sent for review. The adopter can use this feature and configure email templates and notify content creators.

The default email templates available on Sunbird are:

\
 a. Send for review - sendForReview\
 b. Request for changes - requestForChanges\
 c. Publish - publish

### Customizing Email Templates <a href="#customizing-email-templates" id="customizing-email-templates"></a>

Default templates are stored in Sunbird middleware (learner service). The templates are configurable and are stored as form configurations. During the installation process, the default templates can be configured using Form APIs.

#### Adding Email Template to Cassandra DB <a href="#adding-email-template-to-cassandra-db" id="adding-email-template-to-cassandra-db"></a>

Sunbird LMS stores email templates in the table **email\_template** within the **sunbird** keyspace.

The following command allows you to view email templates currently available in Cassandra DB:

`SELECT * from sunbird.email_template;`

Command to add an email template to Cassandra DB using CQL shell. Ensure that the template name is unique so that it doesnot override the existing template information in Cassandra DB:

```
  INSERT INTO sunbird.email_template(name, template) VALUES('myEmailTemplate', '<!doctype html><html> <head> <meta> <meta> <title></title> </head> <body> <table> <tr> <td>&nbsp;</td><td> <div class="content"> <span class="preheader"></span> <table class="main"> <tr> <td class="wrapper"> <table> <tr> <tr> <td> #if ($orgImageUrl) <p> <img src="$orgImageUrl" alt="logo" align="right" width="180" height="100"> </p>#end </td></tr><td> #if ($name) <p >Hi $name,</p>#end <p >$body</p></body></html>')

```

#### Configuring Using Form API <a href="#configuring-using-form-api" id="configuring-using-form-api"></a>

The following are sample template configurations for different content review workflows in form APIs:

**Send for review:**

```
  {
	"request": {
		"type": "notification",
		"action": "sendForReview",
		"subType": "email",
		"data": {
			"templateName": "sendForReviewTemplate",
			"action": "sendForReview",
			"fields": [{
				"body": "A content has been submitted for review.
				<br><br><b>Content Type</b>: <br><b>Title</b>: 
				<br><b>Creator</b>: 
				<br><b>Link</b>: <br>",
				"subject": "Content submitted for Review Content Type: , Title: ",
				"logo": "https://dev.open-sunbird.org/assets/images/sunbird_logo.png",
				"orgName": "Sunbird",	
				"fromEmail": "support-dev@open-sunbird.org"
			}]
		}
	}
}

```

**Request for changes**

```
  {
	"request": 
	{
		"type": "notification",
		"action": "requestForChanges",
		"subType": "email",
		"data": 
		{
			"templateName": "requestForChangesTemplate",
			"action": "requestForChanges",
			"fields": [
				{
				"body": "Thank you for your contribution. We appreciate your effort in creating content for us. However, before we publish the content request you to make the necessary changes as mentioned in the comments.<br>We look forward to receiving the revised content.<br><br><b>Content Type: </b><br><b>Title: </b><br><b>Link: </b><br><b>Reviewer name: </b><br>",
				"subject": "Our Sincere Apologies! Content Type: , Title: ",
				"logo": "https://dev.open-sunbird.org/assets/images/sunbird_logo.png",
				"orgName": "Sunbird",	
				"fromEmail": "support-dev@open-sunbird.org"
			}]
		}
	}
}

```

**Publish**

```
  {
	"request": {
		"type": "notification",
		"action": "publish",
		"subType": "email",
		"data": {
			"templateName": "publishedTemplate",
			"action": "publish",
			"fields": [{
				"body": "This is to inform you that the content submitted has been accepted for publication and will be available on the portal shortly.<br><br><b>Content Type: </b><br><b>Title: </b><br><b>Link: </b><br>",
				"subject": "Congratulations, Your Content is Live! Content Type: , Title: ",
				"logo": "https://dev.open-sunbird.org/assets/images/sunbird_logo.png",
				"orgName": "Sunbird",	
				"fromEmail": "support-dev@open-sunbird.org"
			}]
		}
	}
}

```

**Description of Paramaters**

a. **type:** Type of form

b. **action:** Workflow action, review, publish etc

c. **subType:** Type of notification

d. **templateName:** Template name used to store in Cassandra DB

e. **body:** Body of the email

f. **subject:** Subject line of email

g. **logo:** Logo attached in the email, when the logo is not defined, the default logo is used

Some parameters are used to dynamically change the content information. It is recommended that these parameters are retained in the request body:

a. Content type

b. Content title

c. Content link

d. Creator name

e. Reviewer name

### Custom Templates <a href="#custom-templates" id="custom-templates"></a>

You can aslo create custom email templates which are channel/tenant specific. When customized templates are not present, the default template is used to send emails for different actions in review workflows.

To configure email template:

* Add a new email template configurations in Form API
* Manually insert the new template in Casandra DB of Sunbird middleware service

#### Creating Custom Templates <a href="#creating-custom-templates" id="creating-custom-templates"></a>

1.Name the templates in the form API in **slug\_workflowAction** format 2.Store the template in Cassandra DB, same as the configured Form API 3.Add the **rootOrgId** in the form API request along with other fields, which is the channel 4.All required fields should have placeholders 5.If the custom template is configured in form service, then the custom template with the same name should also be added in learner service(Sunbird middleware). If not added, the Learner service displays an error

For example, if slug is “Sunbird” and action is “send for review”, template name should be “sunbird\_sendforReviewTemplate”

**Sample Custom Template Configuration**

```
  {
	"request": {
		"type": "notification",
		"action": "sendForReview",
		"subType": "email",
		"rootOrgId": "0123166367624478721",
		"data": {
			"templateName": "sendForReviewTemplate",
			"action": "sendForReview",
			"fields": [{
				"body": "A content has been submitted for review.<br><br><b>Content Type: </b><br><b>Title: </b><br><b>Creator: </b><br><b>Link: </b><br>",
				"subject": "Content has been submitted for review! Content Type: , Title: ",
				"logo": "https://dev.open-sunbird.org/assets/images/sunbird_logo.png",
				"orgName": "Sunbird",	
				"fromEmail": "support-dev@open-sunbird.org"
			}]
		}
	}
}

```

> Note: In the email templates, only predefined parameters can be dynamically replaced with content data while sending the email.

Refer [Notification API](api-documentation/notification-apis.md) for sending email notification
