# On-Demand Exhaust

**What is an exhaust?**\
\
In the context of reports, an "exhaust" typically refers to the complete or comprehensive set of data or information included in the report. In an exhaust report, all available relevant data or details on a particular topic or subject have been exhaustively gathered, analyzed, and presented in the report.

Using the term "exhaust" implies that the report contains all the necessary information and leaves little room for additional details or data to be included.



On-demand reports are the reports that the admin(course-batch-creator) will request through the UI on an as-needed basis.

**Overall architecture diagram:**

<figure><img src="../../../../../.gitbook/assets/on_Demand_exhaust.drawio (1).png" alt=""><figcaption></figcaption></figure>

**Internal architecture diagram:**

<figure><img src="../../../../../.gitbook/assets/Untitled design.png" alt=""><figcaption></figcaption></figure>

1. The admin(course-batch-creator) initiates a report request from the Sunbird Ed portal to the Lern portal.&#x20;
2. The Lern portal forwards the request to the Postgres Analytics database using Exhaust APIs.&#x20;
3. The Obsrv portal periodically checks the job request table in the Postgres Analytics database based on a predefined cron schedule.&#x20;
4. The Obsrv portal retrieves the job requests made by the admin.&#x20;
5. The On-Demand Exhaust job retrieves the consumption data from the Cassandra database.&#x20;
6. The On-Demand Exhaust job processes the report request and generates the report.&#x20;
7. If the report generation is successful, the On-Demand Exhaust job creates a password-protected zip file containing the report.&#x20;
8. The zip file is uploaded to the specified cloud server.&#x20;
9. In case the report generation fails, the On-Demand Exhaust job sends a status notification back to the Obsrv portal.&#x20;

**Pointers to keep in mind:**

All the exhaust reports are generated based on course batch and user enrolment info.&#x20;

For Response and User Info Exhaust reports, there is no filter on contents.

Any content which is generating Assess events in the collection will be considered for response exhaust.

**Configuration Details:**&#x20;

We have two checks for obtaining score details during the progress exhaust. Any content that passes either of the two checks below will be considered for score calculation.

`contentType: "SelfAssess"`&#x20;

`objectType: "QuestionSet" AND primaryCategory: "Practice Question Set"`

The following variables control the aforementioned checks:

`assessment.metrics.supported.contentType`

`assessment.metrics.supported.primaryCategories`

`assessment.metrics.supported.objectType`&#x20;

If only the content type variable is set, then only ECML SelfAssess will be considered. If the primaryCategory is set, then only Quml Question Set will be considered for report generation. If both variables are given, then both will be considered.
