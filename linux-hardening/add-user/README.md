# Linux System Administration and User Management Lab

## Overview
This laboratory module documents user provisioning, privilege escalation handling, file system directory structuring, and package management audit logging in a Linux environment (Ubuntu / Theia Cloud IDE)[cite: 32, 34]. The tasks cover resolving non-root permission restrictions, creating and validating new user accounts in `/etc/passwd`, setting up corporate directory hierarchies with spaced filenames, and inspecting system upgrade records in `dpkg.log`[cite: 31, 33, 34].

---

## Lab Tickets & Objectives
Based on the lab assignment guidelines:
* **Ticket 4: Create a New User** — Provision a standard user account with personal attributes, set a password, and verify account creation via `/etc/passwd`.
* **Ticket 5: Manage Files and Folders** — Create organizational directories (`Accounting`, `Payroll`), create an internal documentation file with spaces (`Best Practices`), and list directory contents[cite: 34].
* **Ticket 6: Apply System Updates** — Refresh package indices, upgrade packages, and review installation events in `/var/log/dpkg.log`.

---

## Lab Execution & Verification

### Ticket 4: Create a New User Account

#### 1. Privilege Escalation & Account Provisioning
Attempting `adduser` as a standard user returns a permission denied error (`Only root may add a user or group to the system`). Prepending `sudo` executes the script with administrative privileges to configure user `captainplanet`, create UID/GID `1001`, provision `/home/captainplanet`, copy template files from `/etc/skel`, and populate GECOS field details.

```bash
# Initial attempt without elevated privileges
adduser captainplanet

# Elevated user creation
sudo adduser captainplanet
