# Program Exhaust

Program user personal info exhaust is data-product that generates CSV file containing user details. Each record represents user details who has joined the [prog  ram](https://ed.sunbird.org/learn/product-and-developers-guide/manage-learn/what-is-a-program). This service uses flattened data from Cassandra which is created by a Flink job called [Program User Info](../../data-pipeline-flink-jobs/program-flink-job/). This data-product is configurable for L2, L3 and L4 [data security levels](https://docs.google.com/document/d/1pLvKSiPYzFm-XNl9zA5KAIU1MM5CC0tC/edit#heading=h.gjdgxs).