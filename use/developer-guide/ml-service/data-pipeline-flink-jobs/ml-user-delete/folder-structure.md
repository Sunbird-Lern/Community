# Folder Structure

Ml User Delete Service folder structure is designed to organize the different modules and files that constitute the ml user delete flink job. It follows a modular approach, facilitating easy management and development of the service.

### The structure is as follows

```
.  
│
└── ml-jobs
    ├── pom.xml
    └── ml-user-delete
        ├── pom.xml
        └── src
            ├── main
            │   ├── resources
            │   │   └── user-delete.conf
            │   └── scala
            │       └── org
            │           └── sunbird
            │               └── job
            │                   └── userdelete
            │                       ├── domain
            │                       │   └── Event.scala
            │                       ├── functions
            │                       │   └── UserDeleteFunction.scala
            │                       └── task
            │                           ├── UserDeleteConfig.scala
            │                           └── UserDeleteStreamTask.scala                           
            └── test
                ├── resources
                │   └── test.conf
                └── scala
                    └── org
                        └── sunbird
                            └── job
                                ├── fixture
                                │   ├── EventFixture.scala
                                │   └── LoadMongoData.scala
                                └── spec
                                    └── UserDeleteFunctionTestSpec.scala
       
```

**ml-jobs**&#x20;

This is the main directory that contains manage learn related Flink jobs.

**ml-user-delete**

This folder contains all the required directory for actual implementation of logics.&#x20;

**resources \[main]**

This folder contains application related configurations in a file called _user-delete.conf_

**domain**

This directory contains a file called _Even.scala_ which is used to declare methods to get specific keys out of JSON.

**functions**

This folder contains the file _UserDeleteFunction.scala_ which helps in processing and deleting user information from the MongoDB.

**task**

This folder contains a file called _UserDeleteStreamTask.scala_ which is an entry point for this service. and another file called _UserDeleteConfig.scala_ which holds the variable constants.

**resources \[test]**

This folder contains test related configurations values in a file called _test.conf_. &#x20;

**fixture**

This directory contains a file called _EventFixture_ which is  a hard coded kafka events for the testing purpose. Also contains _LoadMongoData_ file which holds the Mongo Data for the testing purpose.

**spec**

In the spec folder we have the main test case file called _UserDeleteFunctionTestSpec.scala_ that is used to test our stream processing task.

### **Source code**

{% embed url="https://github.com/Sunbird-Lern/data-pipeline/tree/release-7.0.0/ml-jobs/ml-user-delete" %}
