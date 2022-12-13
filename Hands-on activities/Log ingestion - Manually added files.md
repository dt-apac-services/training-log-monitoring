# Manually added log files & Log Storage

> Complete [Setup a lab environment](Setup%20a%20lab%20environment.md) before starting this activity.

Dynatrace provides the ability to manually add log files for ingestion if they are not auto discovered by OneAgent. In this activity we will be testing that capability.

## Steps:
1. Place sample logs on host - [Microsoft HDInsight Sample Log File](https://www.microsoft.com/en-us/download/details.aspx?id=37003)
2. Setup rules for manual log file ingestion
3. Enable log storage for the manual log file
4. View logs in 'Log Viewer'



## Log Sources and Storage

Below video shows manually adding logs and enabling log storage for a logs in 'Log Sources and Storage' page.

1. Add Manual log file to an unsupported folder
   `C:\HDInsight\log\agent\sample\sample.log`
   `C:\HDInsight\log\agent\actor\actors.txt`
2. Add custom log file path in host settings
3. Add new entries to log files
4. See if log shows in Log Storage
5. Enable Log Storage
6. Check OneAgent logs
7. Add new entries to log file
8. Wait for data to show in Log Viewer
9. Check OneAgent logs


## Log Storage Configuration

Below video shows manually adding logs and enabling log storage for a logs in 'Log Storage Configuration' page.
