# Splunk Security Log Analysis & Queries

This section highlights practical Security Information and Event Management (SIEM) skills, including SPL (Search Processing Language) queries, log parsing, and security log investigations using Splunk Cloud.

---

## Lab Overview & Focus Areas
* **Internal Log Auditing:** Monitoring internal component health and error tracking (`index=_internal`, `log_level=ERROR`).
* **Access Control & Web Traffic Analysis:** Investigating client IP interactions, HTTP status codes (`200`, `401`, `403`, `404`), and `sourcetype=splunkd_access`.
* **Statistical Aggregation:** Using the `stats count by` command to baseline normal network behavior and spot anomalies.

### Sample SPL Cheat Sheet / Portfolio Queries

```splunk
# Search for internal error logs
index=_internal log_level=ERROR 

# Summarize log component counts
index=_internal | stats count by component

# Analyze web access logs and status codes
sourcetype=splunkd_access | stats count by clientip, status
