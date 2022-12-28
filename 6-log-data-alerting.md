# 6. Log Data Alerting

If the application generating the logs is also monitored by Dynatrace OneAgent instrumentation, it is very likely that Dynatrace will see the problem first through OneAgent instrumentation, raise a Problem and then associate relevant logs to the Problem (Logs are automatically associated to corresponding traces).

In addition to above, if you would like alerting based exclusively on log content, `Log Events` and `Metric Events` based on `Log Metrics` are your two options.

We already covered `Log Events` and `Log Metrics` in [5-log-data-analytics](5-log-data-analytics.md). Please refer to the those topics on how to generate alerts based on logs.
- [](5-log-data-analytics.md#Log%20Events%20%7CLog%20Events)
- [](5-log-data-analytics.md#Log%20Metrics%7CLog%20Metrics)

