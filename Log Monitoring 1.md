## Training Objectives
- Guide to Dynatrace Log Monitoring doc navigation
- Answer some common but hard to find questions
- Implementation Guide
- How to try examples in Dynatrace docs pages

## FAQs
- How long does it take for log entries to show in console once log file is monitored?
	- ~ 2 mins
- Where to check if log data is being sent successfully to cluster?
	- Unix
	  `/var/log/dynatrace/oneagent/loganalytics/oneagent-logmon-detailed.log`
	- Windows
	  `%PROGRAMDATA%\dynatrace\oneagent\log\loganalytics/oneagent-logmon-detailed.log`
- Log Monitoring logs
	- Unix
	  `/var/log/dynatrace/oneagent/loganalytics/`
	- Windows
	  `%PROGRAMDATA%\dynatrace\oneagent\log\loganalytics\`

## Logs Basics
### Log Types
- Unstructured Logs
	- Text files made up of strings. 
	  `2022-11-15 09:20:43 WebLaunche DEBUG [Simulator] Headless Customer Scenario: visitcount: 6212`
	- Easy to read by humans but difficult for Log Management systems
	- Humans have to code into Log Management systems where the timestamp begins and ends, where to capture the log level, what part is the message and so on.
	- Gets complicated when there are multiline log entries like Stacktraces or there are user entered content like SQL with unescaped line breaks.
- Semi Structured Logs
	- Logs that follow an agreed standard like [Common Log Format](https://en.wikipedia.org/wiki/Common_Log_Format) that's used by web servers 
	  `127.0.0.1 - frank [10/Oct/2000:13:55:36 -0700] "GET /apache_pb.gif HTTP/1.0" 200 2326`
- Structured Logs
	- Written in easily parsed formats like JSON, XML etc
	- JSON is most populary used
	  `{ "timestamp": "2022-11-15T17:23:18.275251140Z", "message": "Sleeping 4.989986122s", "log_level": "info", "source": "cc.deployment_updater.scheduler", "data": {}, "thread_id": 47012094035440, "fiber_id": 47012138728420, "process_id": 6, "file": "/var/vcap/data/packages/cloud_controller_ng/bcf72371ae8625bf4e5d9ee6c9339ebff8f152f2/cloud_controller_ng/lib/cloud_controller/deployment_updater/scheduler.rb", "lineno": 54, "method": "update" }`
	- Easy for Log Management systems to read

