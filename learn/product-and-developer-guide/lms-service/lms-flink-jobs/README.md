---
description: This page details about the Flink Jobs present as part of LERN Building block.
---

# Flink Jobs

BatchService(LMS) with the help of flink jobs calculate consumption progress, scores and generates certificates. Also there is Merge User Courses flink job which is used to merge course and certificate data from one user account to another.

Flink Jobs in LERN have been to developed to support LMS (Learning Management System) journey of a user. Jobs are used to compute data necessary to calculate user's progress and validate the same against certificate issuance criteria and then trigger Sunbird RC to create and issue certificate to the user.&#x20;

## Data-pipeline Overview

<div data-full-width="true">

<figure><img src="../../../../.gitbook/assets/OVERVIEW - LERN JOBS.drawio (1) (1).png" alt=""><figcaption><p><strong>Data-pipeline Overview Diagram</strong></p></figcaption></figure>

</div>

## Certificate Generation Jobs Execution Flow

<div data-full-width="true">

<figure><img src="../../../../.gitbook/assets/Untitled Diagram-V2 LERN - CERTIFICATE GENERATION FLOW.drawio.png" alt=""><figcaption><p><strong>Certificate Generation jobs execution flow diagram</strong></p></figcaption></figure>

</div>

## Additional Reading

{% embed url="https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/1520042020/Course+Infra+-+Async+Jobs+-+Implementation+Design" %}

{% embed url="https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/1782087720/Flink+jobs+for+certificates+generation+and+processing" %}
