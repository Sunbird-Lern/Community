# Folder Structure

Program User Info Service folder structure is designed to organize the different modules and files that constitute the program user info flink job. It follows a modular approach, facilitating easy management and development of the service.

### The structure is as follows

```
.  
│
└── ml-jobs
    ├── pom.xml
    └── program-user-info
        ├── pom.xml
        └── src
            ├── main
            │   ├── resources
            │   │   └── program-user-info.conf
            │   └── scala
            │       └── org
            │           └── sunbird
            │               └── dp
            │                   └── userinfo
            │                       ├── domain
            │                       │   └── Event.scala
            │                       ├── functions
            │                       │   └── ProgramUserInfoFunction.scala
            │                       ├── task
            │                       │   ├── ProgramUserInfoConfig.scala
            │                       │   └── ProgramUserInfoStreamTask.scala
            │                       └── util
            │                           └── Commons.scala
            └── test
                ├── resources
                │   ├── test.conf
                │   └── test.cql
                └── scala
                    └── org
                        └── sunbird
                            └── dp
                                ├── fixture
                                │   └── EventFixture.scala
                                └── spec
                                    └── ProgramUserInfoTaskTestSpec.scala
       
    
```

**ml-jobs**&#x20;

This is the main directory that contains one Flink job called program-user-info.

**program-user-info**

This folder contains all the required directory for actual implementation of logics.&#x20;

**resources \[main]**

This folder contains application related configurations in a file called _program-user-info.conf_

**domain**

This directory contains a file called _Even.scala_ which is used to declare methods to get specific keys out of JSON.

**functions**

This folder contains the file _ProgramUserInfoFunction.scala_ which helps in processing and flattening the JSON into one-level key-value pairs. This file also contains the logic to store the flattened data into Cassandra database.

**task**

This folder contains a file called _ProgramUserInfoStreamTask.scala_ which is an entry point for this service. and another file called _ProgramUserInfoConfig.scala_ which holds the variable constants.

**resources \[test]**

This folder contains test related configurations values in a file called _test.conf_. Also contains _test.cql_ file which holds the Cassandra query to create keyspace for the testing purpose.&#x20;

**fixture**

This directory contains a hard coded kafka events for the testing purpose.

**spec**

In the spec folder we have the main test case file called _ProgramUserInfoTaskTestSpec.scala_ that is used to test our stream processing task.

### **Source code**

{% embed url="https://github.com/Sunbird-Lern/data-pipeline/tree/release-5.3.0/ml-jobs/program-user-info" %}

