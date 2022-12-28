# Help Sheet: Log Parsing

Full doc: [Dynatrace Pattern Language](https://www.dynatrace.com/support/help/shortlink/dpl-dynatrace-pattern-language-hub)

Some common parameters:
- `LD` - Line Data. Matches all characters until an end is specified 
- `SPACE` - Match a single space
- `STRING` - Match a string
- `UPPER` - Match an upper case string
- `LOWER` - Match a lower case string
- `INT` - Match integer value
- `FLOAT` - Match float value
- `?` - Optional. Used with other parameters
	- Example: `SPACE?` - Optional space
- `CPU Usage` - Match literal value 'CPU Usage'
- `('user'| 'User')` - Match literal value 'user' or 'User'
- `IPADDR` - Match IP Address
- `PARSE(content, "JSON{STRING:message}(flat=true)")` - Parse flat (one liner) JSON for further processing
- `MM` - Month in numeric format. E.g.: 01
- `MMM` - Month in short text format. E.g.: Jan
- `MMMM` - Month in long format. E.g.: January

<br/>

### Back: [4.1-processor-rule-definition](../4.1-processor-rule-definition.md)
