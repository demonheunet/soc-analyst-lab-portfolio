# SOC Analyst Lab & SIEM Portfolio

Welcome to my hands-on Security Operations Center (SOC) lab portfolio. This repository documents my practical experience building, querying, and analyzing enterprise log data using a Splunk Cloud trial environment.

---

## Lab Project 1: Enterprise Log Triage & System Error Analysis

### Objective
Practice basic Log Inspection, filtering, and aggregation using Splunk's internal telemetry (`index=_internal`) to understand how backend services generate logs and how to isolate system errors.




## Lab Entry 1: Isolating System Errors

### SPL Query
```spl
index=_internal log_level=ERROR

### Objective
Practice searching through system logs to find and filter out routine background noise, focusing on identifying actual system errors and warnings.




## Lab Entry 2: Summarizing and Ranking System Errors

### SPL Query
```spl
index=_internal log_level=ERROR | stats count by component | sort - count

### Objective
Practice searching through system logs to group and rank errors, turning a messy list of data into a clean, readable summary table.




## Lab Entry 3: Exploring Web Access Logs

### SPL Query
```spl
index=_internal sourcetype=splunkd_access
(NOTE: splunkd_access is only for the splunk trial environment. In a real life scenario, replace it with 'win_security' or 'firewall')

### Objective
Practice searching through web access logs to examine incoming requests and API calls hitting the system.





## Lab Entry 4: Visualizing Web Request Distributions

### SPL Query
```spl
index=_internal sourcetype=splunkd_access | stats count by uri | sort - count

### Objective
Practice transforming tabular log statistics into a visual pie chart to quickly see the proportional share of each endpoint's activity.





## Lab Entry 5: Isolating Authentication Activity in Visualizations

### SPL Query
```spl
index=_internal sourcetype=splunkd_access | stats count by uri | sort - count

### Objective
Practice interacting with SIEM visualization charts to highlight and inspect specific segments of server traffic, focusing on authentication endpoints.





## Lab Entry 6: Isolating and Filtering Specific Endpoints

### SPL Query
```spl
index=_internal sourcetype=splunkd_access uri="/services/auth/login?output_mode=json"

### Objective
Practice refining a search query to isolate traffic targeting a specific high-value endpoint (the authentication login route) rather than viewing all system web requests.





## Lab Entry 7: Identifying Client IP Sources for Authentication Requests

### SPL Query
```spl
index=_internal sourcetype=splunkd_access uri="/services/auth/login?output_mode=json" | stats count by clientip | sort - count

### Objective
Practice grouping and ranking authentication requests by client IP address to identify the origin of login traffic hitting the system.





## Lab Entry 9: Filtering Out Internal Noise Using the NOT Operator

### SPL Query
```spl
index=_internal sourcetype=splunkd_access NOT clientip="127.0.0.1" | stats count by clientip | sort - count

### Objective
Practice using the NOT boolean operator to filter out known internal loopback traffic (127.0.0.1) and check whether any other client IPs are interacting with the system.





## Lab Entry 10: Analyzing HTTP Status Codes for System Health

### SPL Query
```spl
index=_internal sourcetype=splunkd_access clientip="127.0.0.1" | stats count by status

### Objective
Practice grouping and analyzing HTTP response status codes for internal loopback traffic to evaluate system health, successful API calls, and internal application errors.
