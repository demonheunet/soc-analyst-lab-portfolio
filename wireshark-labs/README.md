# Wireshark Network Packet Analysis Labs

This section contains my hands-on packet analysis labs and investigations focusing on network telemetry triage, asset discovery, protocol dissection, and malware artifact identification.

---

## Lab Case: Traffic Analysis Exercise (`2026-10-01-traffic-analysis-exercise.pcap`)

### Objective
Perform network forensics on a compromised Active Directory environment to identify the victim asset, user account, compromise vector, and subsequent Command-and-Control (C2) activity.

### Key Findings & Methodology
* **Asset Discovery:** 
  * Utilized Windows Browser Protocol filters (`browser.response_computer_name`) to quickly map out local endpoints advertising their hostnames.
  * Identified the infected client hostname as **`DESKTOP-4VGYQX7`** (IP: `10.10.1.128`, MAC: `00:22:fb:ec:7e:e7`).
* **User Attribution:** 
  * Filtered Kerberos authentication requests (`kerberos.cname_string`) while excluding machine account objects (`$`) which will isolate human user activity.
  * Confirmed the active user account associated with the compromised session as **`bdiaz`**.
* **Compromise Vector:**
  * Discovered unauthorized executable file download activity originating from an external IP address (`107.175.82.242`) over non-standard **TCP port 9000**.

### Useful Wireshark Filters Used
* Hostname discovery: `browser.response_computer_name`
* User account identification: `kerberos.cname_string == 1 && !(kerberos.CNameString contains "$")`
* Executable transfer tracking: `http.request.uri contains ".exe"` or `smb2.filename contains ".exe"` for exports to VirusTotal.com for further investigation.

---
*[Back to Main Portfolio Dashboard](../README.md)*
