# Batch service(LMS)

Batch service jobs include,

* Progress exhaust - Report on user progress on the collection.
* Response exhaust - Report on user responses for the question set on the trackable collections.
* User-info exhaust - Report on all enrolled Users on the course.
* Collection summary - updates collection-summary-snapshot of the druid data source.
* Course batch status updater - updates course batch elastic search index.
* Course enrollment - Report on enrollment details in the course batch
* Course consumption -  Report on consumption metrics data of the course batch.
* Cassandra migrator - Migrating User enrollment data to reports cluster.

Progress exhaust job, Response exhaust job, User-info exhaust job, Collection summary job, course batch status updater job, course enrollment job, course consumption job and Cassandra migrator job.

