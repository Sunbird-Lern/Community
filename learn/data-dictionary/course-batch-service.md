---
description: List of tables in Cassandra database used in Course-Batch service
---

# Course-Batch Service





### sunbird\_courses.question \[PRIMARY KEY: id]



<table><thead><tr><th width="164">Column Name</th><th width="199.33333333333331">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>assess_ts</td><td>timestamp</td><td></td></tr><tr><td>max_score</td><td>double</td><td></td></tr><tr><td>score</td><td>double</td><td></td></tr><tr><td>type</td><td>text</td><td></td></tr><tr><td>title</td><td>text</td><td></td></tr><tr><td>resvalues</td><td>list&#x3C;frozen&#x3C;map&#x3C;text, text>>></td><td></td></tr><tr><td>params</td><td>list&#x3C;frozen&#x3C;map&#x3C;text, text>>></td><td></td></tr><tr><td>description</td><td>text</td><td></td></tr><tr><td>duration</td><td>decimal</td><td></td></tr></tbody></table>



### sunbird\_courses.content\_consumption \[PRIMARY KEY (userid, contentid, batchid, courseid)]



<table><thead><tr><th width="199.33333333333331">Column Name</th><th width="114">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>userid</td><td>text</td><td></td></tr><tr><td>contentid</td><td>text</td><td></td></tr><tr><td>batchid</td><td>text</td><td></td></tr><tr><td>courseid</td><td>text</td><td></td></tr><tr><td>completedcount</td><td>text</td><td></td></tr><tr><td>contentversion</td><td>text</td><td></td></tr><tr><td>datetime</td><td>timestamp</td><td></td></tr><tr><td>grade</td><td>text</td><td></td></tr><tr><td>lastaccesstime</td><td>text</td><td></td></tr><tr><td>lastcompletedtime</td><td>text</td><td></td></tr><tr><td>lastupdatedtime</td><td>text</td><td></td></tr><tr><td>progress</td><td>int</td><td></td></tr><tr><td>result</td><td>text</td><td></td></tr><tr><td>score</td><td>text</td><td></td></tr><tr><td>status</td><td>int</td><td></td></tr><tr><td>viewcount</td><td>int</td><td></td></tr></tbody></table>



### sunbird\_courses.user\_activity\_agg \[PRIMARY KEY ((activity\_type, activity\_id, user\_id), context\_id)]



<table><thead><tr><th width="186.33333333333331">Column Name</th><th width="147">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>activity_type</td><td>text</td><td></td></tr><tr><td>activity_id</td><td>text</td><td></td></tr><tr><td>user_id</td><td>text</td><td></td></tr><tr><td>context_id</td><td>text</td><td></td></tr><tr><td>agg</td><td>map&#x3C;text, int></td><td></td></tr><tr><td>agg_details</td><td>list&#x3C;text></td><td></td></tr><tr><td>agg_last_updated</td><td>map&#x3C;text, timestamp></td><td></td></tr><tr><td>aggregates</td><td>map&#x3C;text, double></td><td></td></tr></tbody></table>



### sunbird\_courses.report\_user\_enrolments \[PRIMARY KEY (userid, courseid, batchid)]



<table><thead><tr><th width="223.33333333333331">Column Name</th><th width="165">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>userid</td><td>text</td><td></td></tr><tr><td>courseid</td><td>text</td><td></td></tr><tr><td>batchid</td><td>text</td><td></td></tr><tr><td>active</td><td>boolean</td><td></td></tr><tr><td>addedby</td><td>text</td><td></td></tr><tr><td>certificates</td><td>list&#x3C;frozen&#x3C;map&#x3C;text, text>>></td><td></td></tr><tr><td>certstatus</td><td>text</td><td></td></tr><tr><td>completedon</td><td>timestamp</td><td></td></tr><tr><td>completionpercentage</td><td>text</td><td></td></tr><tr><td>contentstatus</td><td>text</td><td></td></tr><tr><td>datetime</td><td>timestamp</td><td></td></tr><tr><td>enrolled_date</td><td>timestamp</td><td></td></tr><tr><td>enrolleddate</td><td>text</td><td></td></tr><tr><td>issued_certificates</td><td>list&#x3C;frozen&#x3C;map&#x3C;text, text>>></td><td></td></tr><tr><td>lastreadcontentid</td><td>text</td><td></td></tr><tr><td>lastreadcontentstatus</td><td>int</td><td></td></tr><tr><td>progress</td><td>int</td><td></td></tr><tr><td>status</td><td>int</td><td></td></tr></tbody></table>



### sunbird\_courses.assessment\_aggregator \[PRIMARY KEY ((user\_id, course\_id), batch\_id, content\_id, attempt\_id)]



<table><thead><tr><th width="190.33333333333331">Column Name</th><th width="214">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>user_id</td><td>text</td><td></td></tr><tr><td>course_id</td><td>text</td><td></td></tr><tr><td>batch_id</td><td>text</td><td></td></tr><tr><td>content_id</td><td>text</td><td></td></tr><tr><td>attempt_id</td><td>text</td><td></td></tr><tr><td>created_on</td><td>timestamp</td><td></td></tr><tr><td>grand_total</td><td>text</td><td></td></tr><tr><td>last_attempted_on</td><td>timestamp</td><td></td></tr><tr><td>question</td><td>list&#x3C;frozen&#x3C;question>></td><td></td></tr><tr><td>total_max_score</td><td>double</td><td></td></tr><tr><td>total_score</td><td>double</td><td></td></tr><tr><td>updated_on</td><td>timestamp</td><td></td></tr></tbody></table>



### sunbird\_courses.course\_batch \[PRIMARY KEY (courseid, batchid)]



<table><thead><tr><th width="199.33333333333331">Column Name</th><th width="240">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>courseid</td><td>text</td><td></td></tr><tr><td>batchid</td><td>text</td><td></td></tr><tr><td>cert_templates</td><td>map&#x3C;text, frozen&#x3C;map&#x3C;text, text>>></td><td></td></tr><tr><td>created_date</td><td>timestamp</td><td></td></tr><tr><td>createdby</td><td>text</td><td></td></tr><tr><td>createddate</td><td>text</td><td></td></tr><tr><td>createdfor</td><td>list&#x3C;text></td><td></td></tr><tr><td>description</td><td>text</td><td></td></tr><tr><td>end_date</td><td>timestamp</td><td></td></tr><tr><td>enddate</td><td>text</td><td></td></tr><tr><td>enrollment_enddate</td><td>timestamp</td><td></td></tr><tr><td>enrollmentenddate</td><td>text</td><td></td></tr><tr><td>enrollmenttype</td><td>text</td><td></td></tr><tr><td>mentors</td><td>list&#x3C;text></td><td></td></tr><tr><td>name</td><td>text</td><td></td></tr><tr><td>start_date</td><td>timestamp</td><td></td></tr><tr><td>startdate</td><td>text</td><td></td></tr><tr><td>status</td><td>int</td><td></td></tr><tr><td>tandc</td><td>boolean</td><td></td></tr><tr><td>updated_date</td><td>timestamp</td><td></td></tr><tr><td>updateddate</td><td>text</td><td></td></tr></tbody></table>



### sunbird\_courses.user\_enrolments \[PRIMARY KEY (userid, courseid, batchid)]



<table><thead><tr><th width="230">Column Name</th><th width="161.33333333333331">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>userid</td><td>text</td><td></td></tr><tr><td>courseid</td><td>text</td><td></td></tr><tr><td>batchid</td><td>text</td><td></td></tr><tr><td>active</td><td>boolean</td><td></td></tr><tr><td>addedby</td><td>text</td><td></td></tr><tr><td>certificates</td><td>list&#x3C;frozen&#x3C;map&#x3C;text, text>>></td><td></td></tr><tr><td>certstatus</td><td>int</td><td></td></tr><tr><td>completedon</td><td>timestamp</td><td></td></tr><tr><td>completionpercentage</td><td>int</td><td></td></tr><tr><td>contentstatus</td><td>map&#x3C;text, int></td><td></td></tr><tr><td>datetime</td><td>timestamp</td><td></td></tr><tr><td>enrolled_date</td><td>timestamp</td><td></td></tr><tr><td>enrolleddate</td><td>text</td><td></td></tr><tr><td>issued_certificates</td><td>list&#x3C;frozen&#x3C;map&#x3C;text, text>>></td><td></td></tr><tr><td>lastreadcontentid</td><td>text</td><td></td></tr><tr><td>lastreadcontentstatus</td><td>int</td><td></td></tr><tr><td>progress</td><td>int</td><td></td></tr><tr><td>status</td><td>int</td><td></td></tr></tbody></table>



### sunbird\_courses.bulk\_upload\_process \[PRIMARY KEY: id]



<table><thead><tr><th width="182.33333333333331">Column Name</th><th width="121">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>text</td><td></td></tr><tr><td>data</td><td>text</td><td></td></tr><tr><td>failureresult</td><td>text</td><td></td></tr><tr><td>objecttype</td><td>text</td><td></td></tr><tr><td>processendtime</td><td>text</td><td></td></tr><tr><td>processstarttime</td><td>text</td><td></td></tr><tr><td>status</td><td>int</td><td></td></tr><tr><td>successresult</td><td>text</td><td></td></tr><tr><td>uploadedby</td><td>text</td><td></td></tr><tr><td>uploadeddate</td><td>text</td><td></td></tr></tbody></table>



### sunbird\_courses.assessment\_aggregator\_temp \[PRIMARY KEY (course\_id, batch\_id, user\_id, content\_id, attempt\_id)]



<table><thead><tr><th width="190.33333333333331">Column Name</th><th width="213">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>course_id</td><td>text</td><td></td></tr><tr><td>batch_id</td><td>text</td><td></td></tr><tr><td>user_id</td><td>text</td><td></td></tr><tr><td>content_id</td><td>text</td><td></td></tr><tr><td>attempt_id</td><td>text</td><td></td></tr><tr><td>created_on</td><td>timestamp</td><td></td></tr><tr><td>grand_total</td><td>text</td><td></td></tr><tr><td>last_attempted_on</td><td>timestamp</td><td></td></tr><tr><td>question</td><td>list&#x3C;frozen&#x3C;question>></td><td></td></tr><tr><td>total_max_score</td><td>double</td><td></td></tr><tr><td>total_score</td><td>double</td><td></td></tr><tr><td>updated_on</td><td>timestamp</td><td></td></tr></tbody></table>



### sunbird\_courses.user\_courses \[PRIMARY KEY (batchid, userid)]



<table><thead><tr><th width="185.33333333333331">Column Name</th><th width="158">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>batchid</td><td>text</td><td></td></tr><tr><td>userid</td><td>text</td><td></td></tr><tr><td>active</td><td>boolean</td><td></td></tr><tr><td>addedby</td><td>text</td><td></td></tr><tr><td>certificates</td><td>list&#x3C;frozen&#x3C;map&#x3C;text, text>>></td><td></td></tr><tr><td>completedon</td><td>text</td><td></td></tr><tr><td>completionpercentage</td><td>int</td><td></td></tr><tr><td>contentstatus</td><td>map&#x3C;text, int></td><td></td></tr><tr><td>courseid</td><td>text</td><td></td></tr><tr><td>datetime</td><td>timestamp</td><td></td></tr><tr><td>delta</td><td>text</td><td></td></tr><tr><td>enrolleddate</td><td>text</td><td></td></tr><tr><td>grade</td><td>text</td><td></td></tr><tr><td>lastreadcontentid</td><td>text</td><td></td></tr><tr><td>lastreadcontentstatus</td><td>int</td><td></td></tr><tr><td>progress</td><td>int</td><td></td></tr><tr><td>status</td><td>int</td><td></td></tr></tbody></table>











































































































































