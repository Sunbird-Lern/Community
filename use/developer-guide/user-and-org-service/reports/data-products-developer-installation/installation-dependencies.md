# Installation Dependencies

### Analytics framework: <a href="#authentication" id="authentication"></a>

Analytics job driver and analytics framework is used to trigger the job in job manager.&#x20;

**GitHub Repository:** [Sunbird-Obsrv/sunbird-analytics-core](https://github.com/Sunbird-Obsrv/sunbird-analytics-core)

**Adopters:** Diksha

**Contributors**: EkStep

**Jenkins Job:** &#x20;

/Build/DataPipeline/AnalyticsCore

/Deploy/DataPipeline/AnalyticsCore

It will generate `analytics-framework-2.0.jar` in `/mount/data/analytics/models-2.0/`

### &#x20;Core Data-products: <a href="#api-manager-util" id="api-manager-util"></a>

Batch-models module is used from this library handling the execution of job

**GitHub Repository:** [Sunbird-Obsrv/sunbird-core-dataproducts](https://github.com/Sunbird-Obsrv/sunbird-core-dataproducts)

**Adopters:** Diksha

**Contributors**: EkStep

**Jenkins Job:** &#x20;

/Build/DataPipeline/CoreDataProducts

/Deploy/DataPipeline/CoreDataProducts

It will generate `batch-models-2.0.jar` in `/mount/data/analytics/models-2.0/`
