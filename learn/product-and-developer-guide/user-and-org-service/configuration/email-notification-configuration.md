# Email Configuration

In sunbird, SendGrid is used for sending email notifications. Below are the confgurations that need to be updated for sending email. These configurations are common for user-org service, notification service and notification data-pipeline flink job.

```
sunbird_mail_server_host = 
sunbird_mail_server_port = 
sunbird_mail_server_username = 
sunbird_mail_server_password = 
sunbird_mail_server_from_email = support@open-sunbird.org
sendgrid_connection_reset_interval //default is 60000L
```

#### Adding Email Template to Cassandra DB <a href="#adding-email-template-to-cassandra-db" id="adding-email-template-to-cassandra-db"></a>

Userorg service stores email templates in the table **email\_template** within the **sunbird** keyspace.

The following command allows you to view email templates currently available in Cassandra DB:

`SELECT * from sunbird.email_template;`

Command to add an email template to Cassandra DB using CQL shell. Ensure that the template name is unique so that it doesnot override the existing template information in Cassandra DB:

```
  INSERT INTO sunbird.email_template(name, template) VALUES('myEmailTemplate', '<!doctype html><html> <head> <meta> <meta> <title></title> </head> <body> <table> <tr> <td>&nbsp;</td><td> <div class="content"> <span class="preheader"></span> <table class="main"> <tr> <td class="wrapper"> <table> <tr> <tr> <td> #if ($orgImageUrl) <p> <img src="$orgImageUrl" alt="logo" align="right" width="180" height="100"> </p>#end </td></tr><td> #if ($name) <p >Hi $name,</p>#end <p >$body</p></body></html>')

```
