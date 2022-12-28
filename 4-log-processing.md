# 4. Log Processing

>From [2-dynatrace-log-monitoring](2-dynatrace-log-monitoring.md):
>Log Processing is the second step in Dynatrace Log Monitoring setup. In this step, log lines are reshaped into required format (using processing rules) for better understanding, efficient filtering and data extraction. As discussed previously, without processing, Log Monitoring systems may not be able to separate out important parts of the log message.
>
>Processing Language used at this stage is  [Dynatrace Pattern Language](https://www.dynatrace.com/support/help/shortlink/dpl-dynatrace-pattern-language-hub)

## Processing rules

When creating a Dynatrace log processing rule, there are 3 fields to complete :
1. `Processor name` - Rule name
2. `Matcher` - Log entries to match
	- This can be the path to log file or lines based on content or much more. Examples:
		-  `log.source="/var/log/sample.log"`
		- `content="starting network manager"`
	- This field requires value written in [Dynatrace Search Query Language](https://www.dynatrace.com/support/help/how-to-use-dynatrace/log-monitoring/analyze-log-data/log-viewer#sql)
	- TIP:  Use `Log Viewer` first to filter content, then switch to `Advanced mode` and copy the search query from advanced field. Use this query in  `Matcher` field.
3. `Processor rule definition` - Processing rule
	- This field requires value written in [Dynatrace Pattern Language](https://www.dynatrace.com/support/help/shortlink/dpl-dynatrace-pattern-language-hub)

Before saving the rule, you have the option to test it by applying it on a sample log line.

A limitation with the `Log sample` box is that you cannot directly copy paste a line from your log file and use it. The log line has to be in Dynatrace's structured log format (the format to which Dynatrace automatically converts all incoming logs). Below is an example of a log line and the structured format (json) that Dynatrace converts it into once in Dynatrace.

```log
Dec 14 06:29:13 ip-172-31-9-214 systemd[1]: NetworkManager-dispatcher.service: Succeeded.
```

```log
{
  "event.type": "LOG",
  "content": "Dec 14 06:29:13 ip-172-31-9-214 systemd[1]: NetworkManager-dispatcher.service: Succeeded.",
  "status": "NONE",
  "timestamp": "1670952553000",
  "loglevel": "NONE",
  "dt.entity.process_group": "PROCESS_GROUP-4ED515623E1C0F5C",
  "dt.entity.process_group_instance": "PROCESS_GROUP_INSTANCE-EADFAC768A7332A3",
  "log.source": "/var/log/messages",
  "dt.host_group.id": "linux",
  "dt.entity.host": "HOST-23DFA6FB3EC993F0"
}
```


In above Dynatrace structured log you can see the original log line in the `content` field. The other fields are added either by Dynatrace OneAgent before sending the logs or by Dynatrace Server after parsing the line.

`dt.entity.process`, `dt.entity.process_group_instance`,`dt.host_group.id`,`dt.entity.host` are all examples of fields added by Dynatrace OneAgent. Some of the other fields like `timestamp`,`status`, `loglevel` are added by Server after parsing the line (based on built-in parsing rule or custom rules).

Therefore when using `Rule testing` either click `Download sample log` button, to get the latest line based on the `Matcher` value (recommended), or specify entry in the following format.

```log
{
"content":"" // Paste your log line as the value here between quotes
}
```

NOTE: Dynatrace takes into account value specified in `Matcher` field when `Rule testing`. So make sure to provide an apt value and not any dummy value in `Matcher` field. Else you may get `The rule has not matched the log sample` result. This also applies when trying out [Log Processing examples](https://www.dynatrace.com/support/help/shortlink/log-monitoring-log-processing-examples). Make sure you copy the `Matcher` values from the examples along with processing rules and sample log lines.

<br/>

### Next: [4.1-processor-rule-definition](4.1-processor-rule-definition.md)

### Previous: [3-log-ingestion](3-log-ingestion.md)

