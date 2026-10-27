# Detection & Analysis: Credential Brute-Force & Compromise (Splunk)

## Overview
This project simulates detection engineering and incident triage in **Splunk Cloud**[cite: 1]. It models an external adversary executing an automated brute-force / password-spraying campaign against common administrative service accounts, culminating in a successful credential compromise.

---

## Scenario & Threat Profile
* **Log Ingest File:** `brute_force_2min.csv`
* **Target System:** Windows Domain / Authentication Services
* **Attacker IP (`src`):** `10.17.0.102`[cite: 1, 2]
* **Compromised Identity (`user`):** `admin`[cite: 2, 3]
* **Attack Window:** 2026-10-26 (20:00:00 - 20:02:00)[cite: 1, 4]
* **Total Ingested Events:** 121[cite: 1, 2]
* **Outcome:** 120 Failed Logins, 1 Successful Login[cite: 1, 2]

---

## Detection Methodology (SPL)

### 1. Ingestion & Raw Event Verification
Verify complete indexing of the raw CSV telemetry:

```spl
source="brute_force_2min.csv"
