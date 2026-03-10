# IT Security Audit: Defense Against the Digital Dark Arts
## Project Overview
This project involves a comprehensive security audit of a local workstation. The goal was to identify vulnerabilities, assess the current defensive posture, and implement hardening techniques to mitigate risks from external and internal threats.

### Focus Areas:
* **Encryption & Authentication:** Evaluating password strength and credential storage.
* **Network Security:** Auditing firewall configurations and port status.
* **System Hygiene:** Assessing patch management and OS support lifecycle.

---

## 1. Security Audit Checklist
Below is the status of the system during the initial inspection:

| Category | Finding | Risk Level | Status |
| :--- | :--- | :--- | :--- |
| **Authentication** | Password hint revealed credential structure | Medium |  Needs Hardening |
| **Firewall** | Windows Defender active on all profiles | Low |  Secure |
| **System Updates** | OS reached End of Support (EOL) | **Critical** |  Vulnerable |
| **Least Privilege** | User account has Administrative privileges | Medium |  Needs Hardening |

---

## 2. Technical Implementation & Observations

### A. Authentication & Credential Security
Observation & Risk Assessment:
During the system audit, I conducted a review of the local authentication mechanisms. While the system required a password for access, the password hint was found to be highly descriptive (revealing partial credential strings and specific naming conventions).

This represents a significant Social Engineering vulnerability, as it provides an attacker with a high-probability starting point for brute-force or dictionary attacks, effectively bypassing the security intended by the password.
> **Improvement:** Removed the descriptive password hint and recommended the use of a high-entropy passphrase (12+ characters) managed via a dedicated password manager.

<img width="1439" height="834" alt="image" src="https://github.com/user-attachments/assets/48dda0e8-722e-4432-a9c8-d943e55545ca" />


### B. OS Integrity & Patch Management
Observation & Risk Assessment:
The audit identified a Critical Vulnerability: the OS has reached End of Life (EOL). This means the system no longer receives security intelligence updates or kernel patches, leaving it permanently exposed to modern exploits and Zero-Day attacks.

Hardening & Mitigation:

Immediate Action: Developed a migration plan to upgrade to a supported OS version to restore the security patch lifecycle.

Interim Measure: Restricted the machine from processing sensitive data or accessing secure network segments until the upgrade is complete.

> **Improvement:** Documented a migration plan to a supported OS version (Windows 10/11) to ensure the system receives monthly security intelligence updates and kernel patches.

<img width="1024" height="705" alt="image" src="https://github.com/user-attachments/assets/567a48d6-67c1-4c68-bea4-a725517832ed" />


### C. Firewall & Network Protection
Observation & Risk Assessment:
A review of the Windows Defender Firewall confirmed it is active across all network profiles (Domain, Private, and Public). While the perimeter is "On," the primary risk lies in overly permissive inbound rules or unnecessary services that could bypass these defenses.

Hardening & Mitigation:

Protocol Hardening: Audited the "Allowed Apps" list to ensure only essential services have network access.

Stealth Mode: Verified that the firewall is configured to block all unsolicited inbound connections on Public networks to minimize the system’s footprint.

> **Improvement:** Verified that stealth mode is enabled for Public networks to prevent the system from responding to unauthorized "pings" or discovery requests.

<img width="1003" height="791" alt="image" src="https://github.com/user-attachments/assets/eec194b2-7ad1-4539-bae3-ff3eab54ee3b" />


---

## 3. Conclusion
The audit successfully identified a high-risk security posture primarily due to **outdated software (EOL)** and **predictable authentication hints**. While the firewall provided a baseline layer of defense, the lack of OS patches means the system remains vulnerable to Zero-Day exploits. 

**Final Recommendations:**
1. **Immediate OS Upgrade:** To restore the security update lifecycle.
2. **Credential Hardening:** Implementation of MFA (Multi-Factor Authentication) and removal of password hints.
3. **Continuous Monitoring:** Monthly reviews of "Allowed Apps" within the firewall settings.

---
*This project was completed as part of the Google IT Support Professional Certificate - Course 5.*
