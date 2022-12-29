# Checklist: OneAgent manually added log files

Dynatrace doc - [Log file matching](https://www.dynatrace.com/support/help/shortlink/log-monitoring-custom-source#log-file-matching)

.txt log file help table - [Table](https://www.dynatrace.com/support/help/how-to-use-dynatrace/log-monitoring/acquire-log-data/add-log-files-manually-v2#:~:text=sources%20and%20storage-,Example%3A,-If%20you%20have)

OneAgent discovers logs if 'any' of below conditions are met (unless specified otherwise):

- [ ] Log paths must be absolute
	- [ ] Windows paths must start with `drive_letter:\`
	- [ ] Linux paths must start with `/`
- [ ] Windows Event Log path in Windows Event System must be a relative path
- [ ] If Wildcard used
	- [ ] Path & file names
		- [ ] `*` can be used to replace string of characters except `\` and `/`
			- Examples: 
			  `C:\log\log_*.txt``
			  `C:\lo*\log_*.txt`
	- [ ] File names only
		- [ ] `#` can use used to replace numbers
			- Example: `12` can be replaced by `#` in the log path `C:\log\log_12.log`. i.e.  `C:\log\log_#.log`
- [ ] Log satisfies OneAgent security rules (To override security rules see [doc](https://www.dynatrace.com/support/help/shortlink/log-monitoring-custom-source#override-security-rules))
	- [ ] Log path not in:
		- [ ] `/etc`
		- [ ] `/boot`
		- [ ] `/proc`
		- [ ] `/dev`
		- [ ] `/bin`
		- [ ] `/sbin`
		- [ ] `/usr`
		- [ ] `WindowsRoot:\windows`
		- [ ] `WindowsRoot:\winnt` except `Windows|winnt\system32\winevt\Logs`
	- [ ] Log path does not contain `.ssh`
	- [ ] Log path does not have `.pem` extension
	- [ ] Log path not in directory whose name starts with `.` (hidden)
	- [ ] Log path must have `log` literal separated by `.`.`-`or`_` 
		- [ ] Must be located in a folder or direct subfolder of `log` or `logs` directory. Deep nested files will be rejected OR
		- [ ] Must be in `/var/log` directory (Nesting allowed if in this dir) OR
		- [ ] Must be `catalina.out` file


<br/>

### Back: [3.1-oneAgent](../3.1-oneAgent.md)