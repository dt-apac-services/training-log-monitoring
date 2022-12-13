## Log entries not showing in 'Log Viewer'
Only log entries that were created after the log was setup to be ingested into Dynatrace (autodiscovery/manual & log storage setup) will be visible in Log Viewer. Older entries will not be ingested.

For the time a log started being monitored, look for below log line in `oneagent-logmon-detailed.log`. All log entries in the file after the `content since x` will be sent to Dynatrace.
```log
[2022-12-01 22:54:34.945 UTC] [/rework/loggroupinstance.cpp] [info] [+] C:\HDInsight\log\agent\sample\manual_test.log set to send content since 2022-12-01 22:38:59.454720
```
