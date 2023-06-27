# Product Roadmap

Use this link to see the Jira Board that has the [Sunbird Lern roadmap](https://project-sunbird.atlassian.net/jira/software/c/projects/LR/boards/102/roadmap). The roadmap has the list of Epics that are to be taken up, as well as form the backlog for the Sunbird Lern team&#x20;

Sunbird Lern [ISSUE TRACKER](https://github.com/Sunbird-Lern/Community/issues) : This is the link to the set of issues/ submissions or requests that are being considered for development as part of the Sunbird Lern roadmap. You can upvote an issue if you find it relevant, or <mark style="color:blue;">add a new issue</mark> to the list



<mark style="color:orange;">**Release-5.4.0**</mark> <mark style="color:orange;">**(Planned release date - 07 Jul '23)**</mark>

Release Plan:

Design Discussions : 15 May '23 - 26 May '23 (2 weeks)\
Sprint 01 : 29 May '23 - 09 Jun '23 (2 weeks)\
Sprint 02 : 12 Jun '23 - 32 Jun '23 (2 weeks)\
Regression & Testing : 26 Jun '23 to 06 Jul (2 weeks)\
Production Release : 07 Jul '23

`Release List for Lern 5.4 on` [`Jira`](https://project-sunbird.atlassian.net/projects/LR/versions/10260/tab/release-report-all-issues)



<mark style="color:orange;">**Release-5.3.0**</mark> <mark style="color:orange;">**(Planned release date - 26 May '23)**</mark>

Release plan:

Design Discussions : 16 Jan '23 - 27 Jan '23 (2 weeks)\
Sprint 01 : 17 Apr '23 - 28 Apr '23 (2 weeks)\
Sprint 02 : 01 May '23 - 12 May '23 (2 weeks)\
Regression & Testing : 15 May '23 to 25 May (2 weeks)\
Production Release : 26 May '23



`UPDATE:`

`Actual release date for 5.3.0 : 27 May '23 (`[`Discussion Forum Update`](https://github.com/orgs/Sunbird-Lern/discussions/128)`)`

`Release List for Lern 5.3 on` [`Jira`](https://project-sunbird.atlassian.net/projects/LR/versions/10233/tab/release-report-all-issues)



<mark style="color:orange;">**Release-5.2.0**</mark> <mark style="color:orange;">**(Planned release date - 27 Mar '23)**</mark>



[Click here](https://project-sunbird.atlassian.net/issues/?filter=12735) to see the list of issues planned for SB Lern Release 5.2

The following are the planned release dates of release 5.2:

Design Discussions : 16 Jan '23 - 27 Jan '23 (2 weeks)\
Sprint 01 : 30 Jan '23 - 17 Feb '23 (3 weeks)\
Sprint 02 : 20 Feb '23 - 10 Mar '23 (3 weeks)\
Regression & Testing : 13 March '23 to '24 March (2 weeks)\
Production Release : 27 March '23\
Bug Fixes & Support : 28 March ' 23 to 31 March '23 (1 week)

UPDATE:

`Actual Release date for 5.2.0 : 06 April '23 (see Discussion Forum update` [`here`](https://github.com/orgs/Sunbird-Lern/discussions/59)`)`\
\
`Release list for Lern 5.2 on` [`Jira`](https://project-sunbird.atlassian.net/projects/LR/versions/10232/tab/release-report-all-issues)&#x20;



[<mark style="color:orange;">**Release-5.1.0**</mark>](https://project-sunbird.atlassian.net/issues/?filter=12607) <mark style="color:orange;">**(Planned release date - 13 Jan '23)**</mark>

**Project: Making SB Lern Cloud Agnostic**

**Task : Completion of Data migration  (**[**LR-254**](https://project-sunbird.atlassian.net/browse/LR-4)**)**

CSP data migration task for certificates in RC.&#x20;

**Project: Sunbird Lern integration with SB RC**

**Task : Completion of Sunbird RC integration with Lern (**[**LR-4**](https://project-sunbird.atlassian.net/browse/LR-4)**,** [**LR-6**](https://project-sunbird.atlassian.net/browse/LR-6)**)**

Integration of Sunbird RC with Sunbird Lern has been taken up over the last 2 releases in order to facilitate Registry driven credentials. A few pending backlog items in this project will be completed as part of Release 5.1.0, including migration of certificates issued so far to Sunbird RC.&#x20;

**Project: New Feature Development**

**Task: Support for Optional material for Courses (**[**LR-1**](https://project-sunbird.atlassian.net/browse/LR-1)**)**

All Course content is considered as mandatory for course completion as of today. There is a functional need called out for being able to add 'optional' material to courses - such that it does not contribute to course progress. This project will cover Lern changes that need to be done in order to enable Optional material for courses

**Task : Course progress exhaust to capture number of attempts (**[**LR-127**](https://project-sunbird.atlassian.net/browse/LR-127)**)**

The current Course progress exhaust is required to be enhanced to capture the number of attempts that a user has made against the assessment tagged to the course.&#x20;

**Project: Enabling ease of Adoption**

**Task: Refactoring of SB Lern Batch Service (**[**LR-131**](https://project-sunbird.atlassian.net/browse/LR-131)**)**

There are a few dependencies for the course service APIs and the DB layers that need to be resolved in order to remove the dependecies that Lern has on SB Obsrv and Knowlg.



**Note :**&#x20;

The team was engaged with an interrupt - i.e. work on [CSP support](https://project-sunbird.atlassian.net/browse/LR-147) related items over the months of September and October 2022. The next release for SB Lern will be 5.1, for which Sprint 1 will commence on 31 Oct 2022.



[**Release-5.0.0**](https://project-sunbird.atlassian.net/issues/?filter=12509) **(Planned release date - 19 Aug'22)**

| **1.** [**Design and plan for decoupling Lern building block from other BB repos and creating its own set up**](https://project-sunbird.atlassian.net/browse/SB-30063)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| The code base of some of the components are spread across different building blocks. This makes the installation and setup difficult. Due to this PR approval and merge takes time. Decoupling the code from other BB repos will help to maintain the repos and code most efficiently. For example, batch service code is spread across many repositories like Sunbird Knowlg, Sunbird Obsrv. Also sunbird-utils repo has the cassandra migration scripts from all components - this needs to be separated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **2.** [**Stabilising of components - increase code coverage and unit test cases**](https://project-sunbird.atlassian.net/browse/SB-30072)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| The code base needs to be further stabilised by bringing in some design changes and also by increasing code coverage and unit tests in components like batch service, notification service etc                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **3.** [**Deployment and Release processes**](https://project-sunbird.atlassian.net/browse/SB-30066)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| i. Build, Deploy and provisioning scripts : refactoring of the provisioning and deployment scripts for the BB                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ii. Be able to deploy existing microservices into a different namespace (SB Ed)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| <p><strong>4. Making SB Lern Cloud agnostic (</strong><a href="https://project-sunbird.atlassian.net/browse/LR-113"><strong>LR-113</strong></a><strong>,</strong> <a href="https://project-sunbird.atlassian.net/browse/LR-112"><strong>LR-112</strong></a><strong>,</strong> <a href="https://project-sunbird.atlassian.net/browse/LR-111"><strong>LR-111</strong></a><strong>,</strong> <a href="https://project-sunbird.atlassian.net/browse/LR-110"><strong>LR-110</strong></a><strong>,</strong> <a href="https://project-sunbird.atlassian.net/browse/LR-109"><strong>LR-109</strong></a><strong>,</strong> <a href="https://project-sunbird.atlassian.net/browse/LR-108"><strong>LR-108</strong></a><strong>,</strong> <a href="https://project-sunbird.atlassian.net/browse/LR-107"><strong>LR-107</strong></a><strong>,</strong> <a href="https://project-sunbird.atlassian.net/browse/LR-106"><strong>LR-106</strong></a><strong>,</strong> <a href="https://project-sunbird.atlassian.net/browse/LR-105"><strong>LR-105</strong></a><strong>,</strong> <a href="https://project-sunbird.atlassian.net/browse/LR-104"><strong>LR-104</strong></a><strong>,</strong> <a href="https://project-sunbird.atlassian.net/browse/LR-103"><strong>LR-103</strong></a><strong>,</strong> <a href="https://project-sunbird.atlassian.net/browse/LR-125"><strong>LR-125</strong></a><strong>,</strong> <a href="https://project-sunbird.atlassian.net/browse/LR-128"><strong>LR-128</strong></a><strong>)</strong></p><p>SB Lern currently has code that is specific to one CSP - this effort will ensure that such dependencies are removed, and SB Lern can function in a cloud agnostic fashion.</p> |

#### [Sunbird Lern Backlog](https://project-sunbird.atlassian.net/issues/?filter=12361)

This is the list of approved backlog items that can be picked up by the Sunbird Lern team as well as other contributors or adopters for development and submission as part of the Lern building block.
