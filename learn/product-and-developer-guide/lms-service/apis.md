# APIs

#### API Documentation:

Refer to \*\*\*\* the below various API documentation related to all the different APIs that are being consumed with in all the batch jobs.

**Reference:** [Course Batch Management APIs](http://docs.sunbird.org/latest/apis/coursebatchmanapi/)

Course Batch Management APIs are listed below:

{% swagger src="../../../.gitbook/assets/coursebatchmanapi (1) (2).yaml" path="/course/v1/batch/read/{batch-id}" method="get" %}
[coursebatchmanapi (1) (2).yaml](<../../../.gitbook/assets/coursebatchmanapi (1) (2).yaml>)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/coursebatchmanapi (1) (1) (2).yaml" path="/course/v1/batch/update" method="patch" %}
[coursebatchmanapi (1) (1) (2).yaml](<../../../.gitbook/assets/coursebatchmanapi (1) (1) (2).yaml>)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/coursebatchmanapi (1) (2).yaml" path="/course/v1/batch/list" method="post" %}
[coursebatchmanapi (1) (2).yaml](<../../../.gitbook/assets/coursebatchmanapi (1) (2).yaml>)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/coursebatchmanapi (1) (1) (4).yaml" path="/course/v1/batch/create" method="post" %}
[coursebatchmanapi (1) (1) (4).yaml](<../../../.gitbook/assets/coursebatchmanapi (1) (1) (4).yaml>)
{% endswagger %}

**Reference:** [Course Enrolment APIs](http://docs.sunbird.org/latest/apis/courseenrolmentapi/)

Course Enrolment APIs are listed below:

{% swagger src="../../../.gitbook/assets/courseenrolmentapi (1) (1) (2).yaml" path="/course/v1/enrol" method="post" %}
[courseenrolmentapi (1) (1) (2).yaml](<../../../.gitbook/assets/courseenrolmentapi (1) (1) (2).yaml>)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/courseenrolmentapi (1) (1) (2).yaml" path="/course/v1/unenrol" method="post" %}
[courseenrolmentapi (1) (1) (2).yaml](<../../../.gitbook/assets/courseenrolmentapi (1) (1) (2).yaml>)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/courseenrolmentapi (1) (1) (1).yaml" path="/course/v1/user/enrollment/list/{user-id}" method="get" %}
[courseenrolmentapi (1) (1) (1).yaml](<../../../.gitbook/assets/courseenrolmentapi (1) (1) (1).yaml>)
{% endswagger %}

**Reference:** [Course Progress APIs](http://docs.sunbird.org/latest/apis/courseprogressapi/)

Course Progress APIs are listed below:

{% swagger src="../../../.gitbook/assets/courseprogressapi (1) (1).yaml" path="/course/v1/content/state/read" method="post" %}
[courseprogressapi (1) (1).yaml](<../../../.gitbook/assets/courseprogressapi (1) (1).yaml>)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/courseprogressapi (1) (1).yaml" path="/course/v1/content/state/update" method="patch" %}
[courseprogressapi (1) (1).yaml](<../../../.gitbook/assets/courseprogressapi (1) (1).yaml>)
{% endswagger %}

**Reference:** [Course Batch Certificates](http://docs.sunbird.org/latest/apis/coursebatchcertificateapi/)

Course Batch Certificates APIs are listed below:

{% swagger src="../../../.gitbook/assets/coursebatchcertificateapi (1).yaml" path="/course/batch/cert/v1/template/add" method="patch" %}
[coursebatchcertificateapi (1).yaml](<../../../.gitbook/assets/coursebatchcertificateapi (1).yaml>)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/coursebatchcertificateapi.yaml" path="/course/batch/cert/v1/template/remove" method="patch" %}
[coursebatchcertificateapi.yaml](../../../.gitbook/assets/coursebatchcertificateapi.yaml)
{% endswagger %}

Reference: [Group Activity Aggregator](http://docs.sunbird.org/latest/apis/groupactivityapi/#tag/Group-Activity-Apis)

{% swagger src="../../../.gitbook/assets/groupactivityapi.yaml" path="/data/v1/group/activity/agg" method="post" %}
[groupactivityapi.yaml](../../../.gitbook/assets/groupactivityapi.yaml)
{% endswagger %}

Reference: [Collection Summary](https://project-sunbird.atlassian.net/wiki/spaces/AN/pages/1121058947/Design+Druid+Proxy+API)

{% swagger method="post" path="" baseUrl="" summary="Collection Summary(https://staging.open-sunbird.org/report/v1/collection/summary)" %}
{% swagger-description %}
This API gives the collection summary, like the total number of enrolments, completion count, count of certificates issued.
{% endswagger-description %}

{% swagger-parameter in="body" name="request" required="true" type="Object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="filters" type="Object" required="true" %}
Search filters
{% endswagger-parameter %}

{% swagger-parameter in="body" name="collectionId" type="String" required="true" %}
Id of the collection
{% endswagger-parameter %}

{% swagger-parameter in="body" name="batchId" type="String" required="true" %}
Id of the batch
{% endswagger-parameter %}

{% swagger-parameter in="body" name="group_by" type="String Array" required="false" %}
`"state", "dist"`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="intervals" type="String" required="false" %}
`2019-09-23T00:00:00.000Z/2019-09-24T00:00:00.000Z"`

 St

`artDate - Batch Start Date and  Default EndDate - Current Date`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "result": {
    "collectionId": "", // Collection/CourseId
    "name": "", // Collection Name
    "batchId": "", // Batch Identifier
    "enrolmentCount": "",
    "completionCount": "",
    "certificatesIssuedCount": "",
    "summary": {  // Summary by state and district level
      "state": {
        "enrolmentCount": "",
        "completionCount": ""
      },
      "district": {
        "enrolmentCount": "",
        "completionCount": ""
      }
    }
  }
}
```
{% endswagger-response %}
{% endswagger %}

Reference: [Page APIs](http://docs.sunbird.org/latest/apis/pagesapi/)

{% swagger src="../../../.gitbook/assets/pagesapi.yaml" path="/data/v1/page/create" method="post" %}
[pagesapi.yaml](../../../.gitbook/assets/pagesapi.yaml)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/pagesapi.yaml" path="/data/v1/page/update" method="patch" %}
[pagesapi.yaml](../../../.gitbook/assets/pagesapi.yaml)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/pagesapi.yaml" path="/data/v1/page/read/{pageName}" method="get" %}
[pagesapi.yaml](../../../.gitbook/assets/pagesapi.yaml)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/pagesapi.yaml" path="/data/v1/page/section/create" method="post" %}
[pagesapi.yaml](../../../.gitbook/assets/pagesapi.yaml)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/pagesapi.yaml" path="/data/v1/page/section/update" method="patch" %}
[pagesapi.yaml](../../../.gitbook/assets/pagesapi.yaml)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/pagesapi.yaml" path="/data/v1/page/section/read/{SectionId}" method="get" %}
[pagesapi.yaml](../../../.gitbook/assets/pagesapi.yaml)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/pagesapi.yaml" path="/data/v1/page/section/list" method="get" %}
[pagesapi.yaml](../../../.gitbook/assets/pagesapi.yaml)
{% endswagger %}

{% swagger method="post" path="/submit" baseUrl="{{host}}/api/course/v1/jobrequest" summary="Exhaust Submit Proxy API" fullWidth="false" %}
{% swagger-description %}
This API will internally call ‘/dataset/v1/request/submit’ API in SB-Obsrv ‘On Demand Data Exhaust API’, to submit the on demand exhaust job request. The job status will be in the submitted state. \n\n- This API should encrypt the password using auto generated encryption key and pass it in the exhaust API request if the security level is L2 or L3. \n- L1 and L4 do not need encryption keys. \n- Fetch the security level using tenant preference APIs to check this.\n- Configure the exhaust api base url and endpoints.
{% endswagger-description %}

{% swagger-parameter in="header" name="x-authenticated-user-token" required="true" %}
User token
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
To make use of the API, you require a authorization.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" required="true" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" required="true" %}
Organisation id of the requestor
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-authenticated-userid" required="true" %}
UserId of the requester - ORG_ADMIN, COURSE_MENTOR
{% endswagger-parameter %}

{% swagger-parameter in="body" name="request" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="OK successful." %}

{% endswagger-response %}
{% endswagger %}



