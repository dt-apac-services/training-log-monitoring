## Log entries not showing in 'Log Viewer'
Only log entries that were created after the log was setup to be ingested into Dynatrace (autodiscovery/manual & log storage setup) will be visible in Log Viewer. Older entries will not be ingested.

For the time a log started being monitored, look for below log line in `oneagent-logmon-detailed.log`. All log entries (from your manual log) after the `content since x`  noted in `oneagent-logmon-detailed.log` (see below log line) will be sent to Dynatrace.

> If you are manually testing this feature, make sure you add log entries with timestamps within 1 minute of current time. Older entries may not be ingested even if timestamp is after the `content since x` seen in logs but > 1 min older than current time.


```log
[2022-12-01 22:54:34.945 UTC] [/rework/loggroupinstance.cpp] [info] [+] C:\HDInsight\log\agent\sample\manual_test.log set to send content since 2022-12-01 22:38:59.454720
```
