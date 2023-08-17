# Folder Structure

Program Exhaust Service folder structure is designed to organize the different modules and files that constitute the Program User Info Exhaust Job application. It follows a modular approach, facilitating easy management and development of the service.

### The structure is as follows

<pre><code>.
├── pom.xml
<strong>└── src
</strong>    ├── main
    │   ├── resources
    │   │   ├── application.conf
    │   │   ├── data.cql
    │   │   ├── log4j.properties
    │   │   └── log4j2.xml
    │   └── scala
    │       └── org
    │           └── sunbird
    │               └── ml
    │                   └── exhaust
    │                       ├── BaseMLExhaustJob.scala
    │                       └── ProgramUserInfoExhaustJob.scala
    │               
    └── test
        ├── resources
        │   └── application.conf
        │     
        └── scala
            └── org
                └── sunbird
                    └── ml
                        └── exhaust
                            └── TestProgramUserInfoExhaustJob.scala
 
 
</code></pre>

**main.ml.exhaust**&#x20;

This main directory houses our Program Exhaust data product. The _ProgramUserInfoExhaustJob.scala_ file contains functions related to Personally Identifiable Information (PII), used for querying the Cassandra database. Additionally, the _BaseMLExhaustJob.scala_ file contains generic functions such as execution, data transformation, storage in blob storage, and retrieval of file paths.

**test.ml.exhaust**&#x20;

In the exhaust folder we have the main test case file called _TestProgramUserInfoExhaustJob.scala_ that is used to test our data-product.

**resources**

This folder contains application related configurations under both main and test directory.

### **Source code**

{% embed url="https://github.com/shikshalokam/data-products/tree/release-5.3.0/lern-data-products/src/main/scala/org/sunbird/ml/exhaust" %}
