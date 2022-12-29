# Troubleshooting

## Log entries not showing in 'Log Viewer'
Only log entries created after the log was setup to be ingested into Dynatrace (autodiscovery/manual & log storage setup) will be visible in Log Viewer. Older entries will not be ingested.

For the ingestion start time look for below entry in `/var/log/dynatrace/oneagent/loganalytics/oneagent-logmon-detailed.log`. 

```log
[2022-12-01 22:54:34.945 UTC] [/rework/loggroupinstance.cpp] [info] [+] C:\log\agent\sample\manual_test.log set to send content since 2022-12-01 22:38:59.454720
```

> Note: If you are manually adding log entries for testing purposes, make sure you add log entries with timestamps within 1 minute of current time. 



