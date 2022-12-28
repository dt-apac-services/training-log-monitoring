# OneAgent AutoDiscovery - Checklist

Dynatrace doc: [Log content autodiscovery](https://www.dynatrace.com/support/help/shortlink/log-monitoring-auto-discovery-v2)

OneAgent autodiscovers logs if 'any' of below conditions are met (unless specified otherwise):

- [ ] System Logs
	- [ ] Windows (See attributes selected [here](https://www.dynatrace.com/support/help/shortlink/log-monitoring-auto-discovery-v2#attributes-selected-in-windows-event-logs))
		- [ ] Windows Security Log
		- [ ] Windows Application Log
		- [ ] Windows System Log
	- [ ] Linux
		- [ ] `/var/log/messages`
		- [ ] `/var/log/syslog`
- [ ] IIS Logs (Windows only) - Event and plain log files
- [ ] Container logs (Linux only) - Kubernetes, OpenShift and non-instrumented Docker.
- [ ] Log files opened by running processes (All conditions below must be met)
	- [ ] Opened by an important and running process AND	
	- [ ] Must exist for a minimum of one minute AND
	- [ ] Must have supported character encoding. UTF-8. UTF-8 BOM, UTF-16LE, UTF-16BE AND
	- [ ] >= 0.5 KB in size AND
	- [ ] updated in <= 7 days AND
	- [ ] Log file path/name
	    - [ ] Accepts `.log` & `.txt` extensions if following conditions met
	        - [ ] If in a folder or direct subfolder of `log` or `logs` directory. Deep nested files won't be auto-discovered
	            - Examples 
					- Valid: `C:\log\log_file.txt`, `C:\logs\NewFolder\log_file.txt`, 
					- Invalid: `C:\log\NewFolder\NewFolder\log_file.txt`
	        - [ ] If not in `log` or `logs` folder then the log file name has `log` literal preceded or followed by `.` or `_`
	            - Examples:
					- Valid:  `C:\NewFolder\abc.log` or `C:\NewFolder\0565842.log.txt`
					- Invalid: `C:\NewFolder\logfile.txt`

<br/>

[Limitations](https://www.dynatrace.com/support/help/shortlink/log-monitoring-auto-discovery-v2#limitations-for-detected-files)

<br/>

### Back: [3.1-oneAgent](../3.1-oneAgent.md)
