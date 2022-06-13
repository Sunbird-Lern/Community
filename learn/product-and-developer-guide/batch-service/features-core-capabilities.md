# Features/Core Capabilities

The following are a few sample functionalities that the Batch Service APIs can be used for, on the platform:

* Creation of a new batch for an existing/ new course, so as to track a cohort of users who are expected to take the course
* Configurations for the Batch such as - End date for batch enrolment, certificate criteria (completion of the course and minimum score of 70% for the course assessment) etc.
* Extension of the batch end date if need be
* Enrol and un-enrol from course batch

![](<../../../.gitbook/assets/image (16).png>)

#### Trackable Collections - Exhaust <a href="#title-text" id="title-text"></a>

Following are the available exhausts for a trackable collection:

1. Progress Exhaust - Progress exhaust contains the progress related information for the collection and the nested collections including the assessment related scores of the collection. The nested collections and the assessments within the collection will be transposed as columns and hence the columns for each collection exhaust file would vary.
2. User Info Exhaust - User personal info exhaust contains the additional information of the users that have joined the collection. The information contains personal details such as Email, Phone number etc and all such personal information is provided only on explicit consent by the user.
3. Response Exhaust - Response exhaust contains the user responses to each question for all question sets in a trackable collection.
