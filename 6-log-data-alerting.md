# 6. Log Data Alerting

If the application generating the logs is also monitored by Dynatrace OneAgent instrumentation, it is very likely that Dynatrace will see the problem first through OneAgent instrumentation, raise a Problem and then associate relevant logs to the Problem (Logs are automatically associated to corresponding traces).

In addition to above, if you would like alerting based exclusively on log content, `Log Events` and `Metric Events` based on `Log Metrics` are your two options.

We already covered `Log Events` and `Log Metrics` in [5. Log data analytics](5-log-data-analytics.md). Please refer to the those topics on how to generate alerts based on logs.
- [Log events](5-log-data-analytics.md#log-events)
- [Log metrics](5-log-data-analytics.md#log-metrics)

<br/>

## Congratulations!!

Congratulations on completing the course. Please provide your valuable feedback to the authors for future improvements.

Thank you!

Back to home page: [Home page](README.md)