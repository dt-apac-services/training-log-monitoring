# 2. Dynatrace Log Monitoring

Dynatrace log monitoring capabilities can be broadly classified into Log Monitoring Classic (LQL) and **Log powered by Grail**.

Log Monitoring Classic (LQL) is the common name for combined Log Monitoring 1.0 and Log Monitoring 2.0 capabilities and Log powered by Grail is the latest and most advanced offering.

As we will see below, 'Log Data Analytics' is where Dynatrace log capability diverges into Log Monitoring Classic and Log powered by Grail. Steps 1 & 2 in log monitoring setup (below) are the same for both old and new capabilities.

> To read more about Grail and how it brings a huge leap in log management, see below resources:
> - [Dynatrace Grail: The data lakehouse for observability and security analysis and automation](https://www.dynatrace.com/news/blog/why-you-need-a-data-lakehouse/)
> - [Any analysis, any time: Dynatrace Log Management and Analytics powered by Grail](https://www.dynatrace.com/news/blog/any-analysis-any-time/)

<br/>

There are 4 main steps to Dynatrace Log Monitoring setup
1. Log Ingestion
2. Log Processing
3. Log Data Analytics
4. Log Data Alerting

## Log Ingestion
This is the first step of Dynatrace Log Monitoring where logs are sent to Dynatrace Servers (ingested).

Dynatrace accepts logs from/through 4 different sources:
1. OneAgent
2. Cloud Providers
	- AWS
	- Azure
	- GCP
3. Open Source
	- Fluentd
	- Logstash
4. Generic Log Ingest (Dynatrace API)

## Log Processing (parsing)
Log Processing is the second step in Dynatrace Log Monitoring setup. In this step, log lines are reshaped into required format (using processing rules) for better understanding, efficient filtering and data extraction. As discussed previously, without processing, Log Monitoring systems may not be able to separate out important parts of the log message.

Custom Attribute capture can be setup in this stage.

Processing Language used at this stage is  [Dynatrace Pattern Language](https://www.dynatrace.com/support/help/shortlink/dpl-dynatrace-pattern-language-hub)

NOTE: Log powered by Grail has the capability to parse logs in-line during a log search. This in-line parsing (discussed later) is done using [Dynatrace Query Language](https://www.dynatrace.com/support/help/shortlink/dql-dynatrace-query-language-hub).

## Log Data Analytics
This is the third step of Dynatrace Log Monitoring. Once the data is in Dynatrace and parsed, it is available for viewing through  'Log Viewer'. In this step more actions like custom log metric & custom attributes (capture of specific value) creation are done.

> Log Data Analytics step is where Dynatrace Log Monitoring capability diverges into Log Monitoring Classic (LQL) and Log powered by Grail. 
> 
> Log Monitoring Classic (LQL) is the common name for combined Log Monitoring 1.0 and Log Monitoring 2.0 capabilities and Log powered by Grail is the latest and most advanced offering.

Log Viewer has a search bar with dropdown selection and an advanced view for custom queries. The advanced search query accepted will depend on your Log Monitoring version.

Search Language for LQL is [Dynatrace Search Query Language](https://www.dynatrace.com/support/help/how-to-use-dynatrace/log-monitoring/analyze-log-data/log-viewer#sql)

Search Language for Log powered by Grail [Dynatrace Query Language](https://www.dynatrace.com/support/help/shortlink/dql-dynatrace-query-language-hub)


## Log Data Alerting

The final step of Log Monitoring is setting up of alerts based on log content. Alerts can be setup using 'Log Events' or 'Log Metrics + Metric Events' features.

<br/>

Next  let's dive into the different stages of Log Monitoring setup.

<br/>

### Next: [3. Log ingestion](3-log-ingestion.md)

### Previous: [1. Log monitoring](1-log-monitoring.md)
