# Ml User Delete

'ml-user-delete' flink job deletes user Personal Identifiable Information (PII) data from different collections of mongo database. Whenever a user chooses to delete his/her account from the sunbird platform this job receives an kafka event with userId, Based on the userId we delete user related information from the documents of different collections.
