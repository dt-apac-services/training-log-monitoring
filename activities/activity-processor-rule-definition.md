# Activity: Processor rule definition


### Setup steps & Example 1:

1. Navigate to  `Settings > Log Monitoring > Log processing > Add processing rule` and fill out as below:
	-  `processor name`: 'Timestamp parsing'
	- `Matcher`: 'content="This is a sample"'
	- `Processor rule definition`: `PARSE(content,"TIMESTAMP('dd/MM/yyyy HH:mm'):timestamp LD")`
	- `Log sample`: 
```json
{
  "event.type": "LOG",
  "content": "13/12/2022 17:29 WARN This is a sample warn log line. CPU usage 50.",
  "status": "NONE",  
  "timestamp": "1670952553000",
  "loglevel": "NONE"  
}
```
 
2. Click `Test the rule` button.

The result should like below:

```json
{
  "content": "13/12/2022 17:29 WARN This is a sample warn log line. CPU usage 50.",
  "timestamp": "2022-12-13T17:29:00.000000000 +0000",
  "event.type": "LOG",
  "status": "NONE",
  "loglevel": "NONE"
}

```


### Example 2:

Next let's modify the rule to extract both `timestamp` and `loglevel`.

Simplified log:
```json
{
  "event.type": "LOG",
  "content": "13/12/2022 17:29 WARN This is a sample warn log line. CPU usage 50.",
  "status": "NONE",  
  "timestamp": "1670952553000",
  "loglevel": "NONE"  
}
```

The parsing rule to extract both `timestamp` and `loglevel` will look like below:
```parse
PARSE(content,"TIMESTAMP('dd/MM/yyyy HH:mm'):timestamp SPACE STRING:loglevel LD")
```

Here is a breakdown. 
- `PARSE(content, ...)`: This initial part tells Dynatrace that it needs to parse the log content in the Dynatrace structured log `content` field. 
- `"TIMESTAMP('dd/MM/yyyy HH:mm')"`: This part tells Dynatrace the format of the custom timestamp. [Time and Date format doc](https://www.dynatrace.com/support/help/how-to-use-dynatrace/dynatrace-pattern-language/log-processing-time-date)
- `:timestamp"`: This part tells Dynatrace to assign the value captured by the previous step to the `timestamp` field.
- `SPACE`: This part tells Dynatrace there is a space after time stamp value
- `STRING:loglevel`: This part tells Dynatrace to capture the string immediately following the space and assign it to `loglevel` field
- `LD`: Match the rest of the line

The result will now look like below:

```json
{
  "content": "13/12/2022 17:29 WARN This is a sample warn log line. CPU usage 50.",
  "timestamp": "2022-12-13T17:29:00.000000000 +0000",
  "event.type": "LOG",
  "status": "NONE",
  "loglevel": "WARN"
}
```

Notice how the `loglevel` value has changed from `NONE` to `WARN` in the result. This way we can extract  all values from the log line and assign to fields

### Example 3: 

In this example let's add a extract `CPU Usage` value from the log line and assign it to a new field. 

Simplified log:
```json
{
  "event.type": "LOG",
  "content": "13/12/2022 17:29 WARN This is a sample warn log line. CPU usage 50.",
  "status": "NONE",  
  "timestamp": "1670952553000",
  "loglevel": "NONE"  
}
```

The parsing rule to extract `timestamp`, `loglevel` and the new field `cpuusage` will look like below:

```parse
PARSE(content,"TIMESTAMP('dd/MM/yyyy HH:mm'):timestamp SPACE STRING:loglevel LD 'CPU usage' SPACE FLOAT:cpuusage")
```

Here is a breakdown. 
- `PARSE(content, ...)`: This initial part tells Dynatrace that it needs to parse the log content in the Dynatrace structured log `content` field. 
- `"TIMESTAMP('dd/MM/yyyy HH:mm')"`: This part tells Dynatrace the format of the custom timestamp. [Time and Date format doc](https://www.dynatrace.com/support/help/how-to-use-dynatrace/dynatrace-pattern-language/log-processing-time-date)
- `:timestamp"`: This part tells Dynatrace to assign the value captured by the previous step to the `timestamp` field.
- `SPACE`: This part tells Dynatrace there is a space after time stamp value
- `STRING:loglevel`: This part tells Dynatrace to capture the string immediately following the space and assign it to `loglevel` field
- `LD 'CPU usage'`: `LD` matches the rest of the line until literal value 'CPU usage' and `CPU usage` matches the text 'CPU usage'.
- `SPACE`: This part tells Dynatrace there is a space after 'CPU usage'
- `INT:cpusuage`: This part asks Dynatrace to capture the float value (FLOAT) and assign it to a new field `cpuusage`.

> NOTE: `cpuusage` field is called a custom attribute.

The result will now look like below:

```json
{
  "content": "13/12/2022 17:29 WARN This is a sample warn log line. CPU usage 50.",
  "timestamp": "2022-12-13T17:29:00.000000000 +0000",
  "event.type": "LOG",
  "status": "NONE",
  "loglevel": "WARN",
  "cpuusage": "50.0"
}
```

This field can now be used to create a log metric and used for charting & alerting.

<br/>

### Next: [5. Log data analytics](../5-log-data-analytics.md)

### Previous: [4.1 Processor rule definition](../4.1-processor-rule-definition.md)