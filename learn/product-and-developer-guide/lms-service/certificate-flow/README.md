# Certificate Flow

In Sunbird, you can attach a "Certificate" to any course or batch, and it will be given to users upon completion. The process involves creating certificate templates or layouts and linking them to the course batch. Certificates in Sunbird have the following features:

a. You can attach a certificate to a specific Course Batch. \
b. The certificate templates can be configured by the administrator for a specific organization. \
c. The Course creator or mentor can attach a certificate to a batch using the portal. \
d. Rules for issuing certificates can be set up through the portal. \
e. Sunbird allows you to create both the "certificate template layout" and "certificate templates" using APIs.

**Sample Workflow:**

<div data-full-width="true">

<figure><img src="../../../../.gitbook/assets/cert flow.drawio.png" alt=""><figcaption></figcaption></figure>

</div>

1. Read certificate rules or criteria from the user organization service.
2. Read asset details from the user organization service.
3. Send the certificate rules and asset information to the Learning Management System (LMS) service.
4. Use the course batch management APIs to attach or remove a certificate template to/from a course batch.

**Asset create/upload**

<div data-full-width="true">

<figure><img src="../../../../.gitbook/assets/asset create_upload.drawio.png" alt=""><figcaption></figcaption></figure>

</div>

To create and upload a certificate template asset in Sunbird, follow these steps:

1. Check if you have a new design for the certificate template:&#x20;

a. If yes,

1. Create an 'ASSET' type of "Certificate" using the asset APIs of Sunbird Knowledge: \
   a. Use the asset creation API with the parameters:
   * **certType**: Set it as **"cert template"** to specify the asset type.
   * Other relevant information for the certificate template.
2. Upload the design to the created template asset: \
   a. Use the asset upload API with the following parameters:
   * Asset ID: Use the ID of the created certificate template asset.
   * Design file: Upload the design file for the certificate template.
3. Validate the created templates using the asset APIs of Sunbird Knowledge: \
   a. Utilize the asset read API to ensure the correctness of the created certificate templates.

On following these steps, you can create and upload a certificate template asset with a new design in Sunbird. \
\
b. If no,

1. Configure the certificate template layout using the asset APIs of Sunbird Knowledge: \
   a. Create a new asset with the certType set as "cert template layout" using the asset creation API. \
   b. Provide the necessary information for the certificate template layout.
2. Configure the layout with placeholders and attach logos and signature images in the Sunbird portal.
3. Upload the template layout using asset upload APIs and validate the created certificate layouts using the asset read APIs of Sunbird Knowledge.

**Sample Postman Collection:**

{% file src="../../../../.gitbook/assets/Certification Flow.postman_collection.json" %}

**Sample Cert templates:**



**To know more,**

{% content-ref url="certificates-creation-and-configuration.md" %}
[certificates-creation-and-configuration.md](certificates-creation-and-configuration.md)
{% endcontent-ref %}
