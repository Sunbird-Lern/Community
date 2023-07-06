# Assessment Score Correction Job

This job identifies the incorrect response details for an assessment from user and remove those records from assessment aggregator table and exports the issued certificates for those consumption. It helps to revoke the certificates.

It is an one-time script written to fix the issue. It is deprecated since no longer used.

**Data provider:**

**Cassandra**

1. user\_enrolments
2. assessment\_aggregator

**API:**

1. Content read API

\
\
