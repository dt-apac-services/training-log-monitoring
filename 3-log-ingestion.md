# 3. Log Ingestion

Log Ingestion is the process through with Log data is brought into Dynatrace. 

As discussed in [2. Dynatrace Log Monitoring](2-dynatrace-log-monitoring.md), Dynatrace accepts logs from/through 4 different sources:
1. OneAgent
2. Cloud Providers
	- AWS
	- Azure
	- GCP
3. Open Source
4. Generic Log Ingest (Dynatrace API)

## Before setting up Log Ingestion
Few items need your attention before setting up Dynatrace Log Monitoring:
1. Supported log data formats
	
	[Supported log data formats](https://www.dynatrace.com/support/help/shortlink/log-monitoring-supported-format) is the guide to how built-in parsing rules work in Dynatrace. If the logs are not in the supported format, you will have to create parsing rules to extract even basic values like timestamp and status/log severity. Please read the doc for more information, but here are some important points:
	- Log severity is detected through a keyword search on the first 100 characters in log line. This can be adjusted in `Dynatrace Settings > Log Monitoring > OneAgent settings`
	- Plain-text logs (.txt) are valid as long as it meets format and path requirements mentioned in the [doc](https://www.dynatrace.com/support/help/how-to-use-dynatrace/log-monitoring/log-monitoring-configuration/log-data-format).
	- Any log entry with unsupported/unrecognized timestamp will have 'ingestion time' as the `timestamp` value ([Supported timestamp formats](https://www.dynatrace.com/support/help/how-to-use-dynatrace/log-monitoring/log-monitoring-configuration/timestamp-data-format)).  However, this can be corrected after ingestion using [Timestamp rules](https://www.dynatrace.com/support/help/shortlink/log-monitoring-timestamp-configuration#timestamp-rules) created at Host, HostGroup or Environment levels under respective (Host/HostGroup/Global) `Settings` page -  `Settings > Log Monitoring`.

2. Connecting log data to traces
   
	Dynatrace has the capability to connect log entries to Dynatrace traces (PurePaths). This is a 2 step process:
	1. Dynatrace OneAgent enriches log entries with `dt.trace_id`, `dt.span_id` & `dt.entity.process_group_instance` values for supported frameworks as described in [Connecting log data to traces](https://www.dynatrace.com/support/help/shortlink/log-monitoring-log-enrichment) doc. 
	   
	   **Automatic Log Enrichment**
	   
	   This is where Dynatrace OneAgent automatically adds these fields to log lines before sending them to Dynatrace Server. See [Automatic Log Enrichment steps](https://www.dynatrace.com/support/help/shortlink/log-monitoring-log-enrichment#enabledisable-automatic-log-enrichment-for-a-specific-technology) 
	   
	   **Limitation**: 
	   - OneAgent based automatic log enrichment can only be done for [structured logs](1-log-monitoring.md#structured-logs) and for [supported frameworks](https://www.dynatrace.com/support/help/shortlink/log-monitoring-log-enrichment#supported-frameworks). 
	   - Enabling Automatic log enrichment on [unstructured logs](1-log-monitoring.md#unstructured-logs) may cause issues with other log management systems ingesting the same logs.
	   
	   **Manual Log Enrichment** 
	   
	   Available [OneAgent v1.239+](checklist-minimum-dynatrace-versions.md)
	   
	   Log Entries can also be enriched using custom configuration on supported technologies. For details see [manual-log-enrichment-steps](manual-log-enrichment-steps.md).  
	   Manual Log Enrichment is also useful for logs that come through sources other than OneAgent.
	   
	2. Dynatrace Server uses this extra data/fields to connect Log entries to traces (PurePaths). 
	
3. Sensitive data masking
	
	[Sensitive data masking](https://www.dynatrace.com/support/help/shortlink/log-monitoring-mask-sensitive-data) rules can be created to prevent sensitive data like email, url parameters and similar being sent by Dynatrace OneAgents to Dynatrace Server. These rules added through Dynatrace UI can either hide or replace content on OneAgent side before the data is sent to Dynatrace.

	The data masking rules can be applied to host, host group or environment wide using respective `Settings > Log monitoring` configuration. Precedence is in the order Host, HostGroup and Environment respectively.

	See [Create rule](https://www.dynatrace.com/support/help/shortlink/log-monitoring-mask-sensitive-data#create-rule) section of doc for steps and examples.

## Log Ingestion setup

Next lets go through the different log ingestion setups.
- [3.1 OneAgent](3.1-oneAgent.md)
- [3.2 Cloud Providers](3.2-cloud-providers.md) (Coming soon)
- [3.2 Open Source](3.3-open-source.md) (Coming soon)
- [3.3 Generic log ingest (Dynatrace API)](3.4-generic-log-ingest-dynatrace-api.md) (Coming soon)

<br/>

### Next: [3.1 OneAgent Log Ingest](3.1-oneAgent.md)

### Previous: [2-dynatrace-log-monitoring](2-dynatrace-log-monitoring.md) 