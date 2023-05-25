# DATA PIPELINE (Flink Jobs)

Lern uses flink jobs for asynchronous processes.&#x20;

UserOrg service uses User cache updater flink job to de-normalise the user data and stores it in Redis.

BatchService(LMS) with the help of flink jobs calculate consumption progress, scores and generates certificates. Also there is Merge User Courses flink job which is used to merge course and certificate data from one user account to another.

Notification Service has a flink job which helps in sending asynchronous notifications.
