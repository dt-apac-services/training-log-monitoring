# Logs Introduction

## What are Logs ?
If you have ever used software, chances are your interactions were recorded by the software into a file called 'Log' .  These log files contain point in time information on activity within the software. As to what's captured in these log files, it depends on the instructions added to the underlying code by the programmer. It could be any number of things like:
- Interaction with the Graphical User Interface (GUI)
- An internal module recording response from another module within the chain
- Stack trace
- Call to database
- and much more..

## Why monitor Logs?

If you work in technology, these logs can provide important insights into the operation of the application code, like what's working as designed and what's not. This can help with troubleshooting issues as well as optimizing code for better performance. In addition, logs can also provide important business insights like the number of users accessing an application, revenue captured (think online shopping platform) and much more. 

The popularity as well as limitation of logs comes from its flexibility - developers decide what goes into the logs and what doesn't. This can mean important information being captured or missed. Another limitation usually comes from the sheer volume of data generated. When analyzing logs, it can feel like looking for a needle in a haystack (try reading Windows Event logs!). This is where a good log analytics platform can help. 

## Log Content

A typical log contains at least 3 parts:
1. `timestamp`: Point in time the log was written
2. `status`: Status (or urgency) of the log entry. It can take the values of Critical, Error, Warning, Info, Debug etc.
3. `message`: Message that the application wants to convey through the entry. 

Example:
```log
2022-11-15 09:20:43 DEBUG [Simulator] Headless Customer Scenario: visitcount: 6212

# Here the 3 basic parts are:
# timestamp: 2022-11-15 09:20:43
# status: DEBUG
# message: DEBUG [Simulator] Headless Customer Scenario: visitcount: 6212
```

The amount of data in a log line can depend on what was coded into the logging part of the software. This could include application name, ip address and more depending on the context and what the developer  wanted to convey.

## Log types
### Unstructured Logs
When logs first came out (with the dawn of software) there used to be only one type of log line. Ones like the example we saw earlier (shown again below).

Example:
```
2022-11-15 09:20:43 DEBUG [Simulator] Headless Customer Scenario: visitcount: 6212
```

These are just text strings that are now commonly referred to as an 'unstructured' log entry.

These log lines were designed at a time when humans were the only ones reading logs. When Log Management and Analytics software started reading logs (remember needle in a haystack problem?), these unstructured logs started posing problems. As these logs were designed for human eyes, there was no clear delineation of where a log part ended and where another started - like where log status ended and message started. Parsing (or reading & analyzing) logs into a form that machines understand became an increasingly complex problem to solve. So came 'Semi-structured' and 'Structured' log formats.

### Semi-structured Logs
After unstructured logs came 'semi-structured' logs. Semi-structured logs are still text strings, but  follow an agreed standard. An example is  [Common Log Format](https://en.wikipedia.org/wiki/Common_Log_Format) used by web servers.

Example:
```log
127.0.0.1 - frank [10/Oct/2000:13:55:36 -0700] "GET /apache_pb.gif HTTP/1.0" 200 2326
```
Other examples are:
- [Extended Log Format](https://en.wikipedia.org/wiki/Extended_Log_Format)
- [Syslog](https://en.wikipedia.org/wiki/Syslog)

Semi-structured logs made log parsing easier for Log Management systems, as the order of contents became predictable, but this too was not without issues (After all, it's just text strings).

### Structured Logs
Structured logs came in as a solution to log parsing problems. These logs are written in easily parsed formats likes JSON, XML etc. JSON is arguably the most popular of the lot and you are likely to see a lot more of it.

Example:
```json
{ "timestamp": "2022-11-15T17:23:18.275251140Z", "message": "Sleeping 4.989986122s", "log_level": "info", "source": "cc.deployment_updater.scheduler", "data": {}, "thread_id": 47012094035440, "fiber_id": 47012138728420, "process_id": 6, "file": "/var/vcap/data/packages/cloud_controller_ng/bcf72371ae8625bf4e5d9ee6c9339ebff8f152f2/cloud_controller_ng/lib/cloud_controller/deployment_updater/scheduler.rb", "lineno": 54, "method": "update" }
```

In structured logs, content is presented in key-value pairs (as seen above) making it easy for log managements to know exactly what each pair meant and parse them. This meant minimum log processing rule complexity.

### To summarize
Despite all the advances in log formats, there are still systems that use 'unstructured' and 'semi-structured' log formats. This makes complex log parsing rules unavoidable for Log Management and Analytics systems, including Dynatrace Log Monitoring. Log Parsing and[ Dynatrace Pattern Language (DPL)](https://www.dynatrace.com/support/help/shortlink/dpl-dynatrace-pattern-language-hub) are therefore important parts of Dynatrace Log Monitoring setup in addition to Log Ingestion, Storage and Alerting.

<br/>

### Next: [2. Dynatrace log monitoring](2-dynatrace-log-monitoring.md)
