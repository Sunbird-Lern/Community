# FAQs

**Q 1: I am unable to see the total enrolled count for a course or collection summary report is not running**

<details>

<summary>Answer</summary>

1. Ensure that the specified **Obsrv** Flink jobs are currently active and running smoothly.
   1. telemetry extractor&#x20;
   2. pipeline-preprocessor&#x20;
   3. ingest router

<!---->

2.  Please ensure the configurations below are correctly set in the configuration file as specified.

    * "collection\_summary\_agg\_data\_source": "audit-rollup-syncts"


3. If the data source is **audit-rollup-syncts**, then it should be available in the Druid data source. if not then,
   * Run the specified job in the desired environment by...
     * navigating to, **/Deploy/\{{env\}}/DataPipeline/DruidIngestion**
     * Select **rollup\_telemetry\_audit\_syncts** from **ingestion\_task\_names** list
     * deploy

</details>

**Q 2: I am unable to download the question set report on the portal, and the error is showing something related to encryption.**

<details>

<summary>Answer</summary>

Please ensure your security configuration aligns with the Data security policy setup detailed in release 5.3.0.

[https://lern.sunbird.org/use/release-notes/release-v-5.3.0#data-security-policy-setup](https://lern.sunbird.org/use/release-notes/release-v-5.3.0#data-security-policy-setup)

</details>
