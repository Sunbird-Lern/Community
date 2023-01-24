# Features/Core Capabilities

The following are a few sample functionalities that the Batch Service APIs can be used for, on the platform:

* Creation of a new batch for an existing/ new course, so as to track a cohort of users who are expected to take the course
* Configurations for the Batch such as - End date for batch enrolment, certificate criteria (completion of the course and minimum score of 70% for the course assessment) etc.
* Extension of the batch end date if need be
* Enrol and un-enrol from course batch

![](<../../../.gitbook/assets/image (16).png>)

#### What is a Course?

A Course is any collection which has trackable.enable=true

#### Course Batch

A batch is created to enable users to enrol to a course and consume. Batch and course have 1:1 relationship. While a course can have multiple batches. Batch also enables course admin or creator to issue certificates.

#### Who can update a batch?

Creator or mentors can update the batch. Once the batch is IN-Progress, we cannot update the startDate.

#### How is the batch status updated?

Batch status is updated by a data product CourseBatchStatusUpdater which runs every 30 mins.\


Batch Metadata:

Startdate: Beginning date of the batch. Users can consume the course from this date.

EndDate: End date of the batch

EnrollmentEndate: This date cannot be beyond endDate. By Deafult, it is one day before endDate if not defined.

CreatedBy: Batch creator, only this user can update the batch

Mentors: Has permission to update the batch

CreatedFor: Organisation for which the batch is created

Status: 0 = The batch is not started : Upcoming Batches

&#x20;            1 = In Progress : Ongoing Batches

&#x20;            2= Batch ended.

EnrollmentType: Open, invite-only(private)



#### Trackable Collections - Exhaust <a href="#title-text" id="title-text"></a>

Following are the available exhausts for a trackable collection:

1. Progress Exhaust - Progress exhaust contains the progress related information for the collection and the nested collections including the assessment related scores of the collection. The nested collections and the assessments within the collection will be transposed as columns and hence the columns for each collection exhaust file would vary.
2. User Info Exhaust - User personal info exhaust contains the additional information of the users that have joined the collection. The information contains personal details such as Email, Phone number etc and all such personal information is provided only on explicit consent by the user.
3. Response Exhaust - Response exhaust contains the user responses to each question for all question sets in a trackable collection.
