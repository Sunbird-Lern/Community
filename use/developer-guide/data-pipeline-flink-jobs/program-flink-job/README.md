# Program User Info

'program-user-info' is used to capture the user's information when the user joins the [program](https://ed.sunbird.org/learn/product-and-developers-guide/manage-learn/what-is-a-program). Whenever a user joins a program, this job receives an event with the user's information as JSON data and then it parses and stores it as respective key-value pairs in Cassandra.&#x20;
