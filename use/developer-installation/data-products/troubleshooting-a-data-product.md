# Troubleshooting a data-product

## Logs for Data-products

In the server, data-product generates two types of logs when running a job.

### 1. Execution log

The spark script code execution log can be found in the below location of the server.

```
/mount/data/analytics/logs/lern-data-products/{{date}}-job-execution.log
```

### 2. Joblog

Also, from the job we are having logs for identifying the status of the job. This type of log configurable to put either in log file or kafka topic based on below config.

```
log.appender.kafka.enable="{{ boolean }}"
log.appender.kafka.broker_host="{{ host }}:9092"
log.appender.kafka.topic="{{ env }}.druid.events.log"
```

If `log.appender.kafka.enable` is `false`, the log goes into the below file.

```
/mount/data/analytics/scripts/logs/joblog.log
```
