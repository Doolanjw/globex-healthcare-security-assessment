# Globex Healthcare — Secure File Storage & Access Management

> **Note on AI assistance:** This is a portfolio project completed during my pivot from twenty years of legal practice into AI Governance and cybersecurity GRC. The technical implementation work in this repository was completed with AI tooling (ChatGPT, Claude, Copilot) under my direction. My role on the project was design, evaluation, documentation, and quality assurance — the specific seat the IAPP AIGP credential is designed to fill. I do not represent myself as a hands-on developer or security engineer.

**Author:** Jonathan W. Doolan  
**Date:** October 2025  
**Frameworks:** HIPAA Security Rule, NIST CSF, ISO 27001/27002, CIS Controls v8, SOC 2

---

## Overview

This project implemented a comprehensive secure file storage and access management system for Globex Financial & Healthcare Services following a security breach where unauthorized users accessed confidential financial reports and Protected Health Information (PHI). The solution addresses critical security gaps through role-based access control, audit trail management, real-time monitoring, and persistent security configurations.

All five project objectives were completed, demonstrating practical skills in Linux system administration, access control management, security logging, and compliance monitoring applicable to healthcare and financial services environments.

## Problem Statement

After a security breach involving unauthorized access to both financial data and PHI, Globex needed:
- Granular access controls enforcing minimum necessary access principles
- Audit trail capabilities compliant with both financial regulations and HIPAA
- Real-time security violation monitoring for IT security teams
- Persistent configurations that survive system maintenance and reboots

## What I Built

### 1. Role-Based Access Control (RBAC) via Linux ACLs
- Created user accounts with differentiated access levels (senior analyst: read-only oversight; project leads: full access to assigned directories only)
- Configured ACLs enforcing minimum necessary access for PHI protection per HIPAA § 164.502(b) and § 164.514(d)
- Set default ACLs so future files automatically inherit correct permissions

### 2. Audit Trail Management
- Configured differentiated command history retention by role (senior analysts: 10 commands; project users: 50 commands)
- Implemented persistent audit settings in user .bashrc files
- Supports HIPAA Security Rule audit controls (45 CFR § 164.312(b))

### 3. Security Violation Logging
- Installed and configured rsyslog with custom configuration for security events
- Created dedicated log file (/var/log/security-violations.log)
- Automated logging of all permission denial events
- Tested with unauthorized access attempts to verify logging functionality

### 4. Real-Time Web Security Dashboard
- Built a PHP-based security monitoring dashboard served via Apache2
- Auto-refresh every 30 seconds for continuous monitoring
- Displays total and recent violation statistics, timestamped event details, and color-coded violation entries
- Provides IT security teams with immediate visibility into unauthorized access attempts

### 5. Persistent Security Architecture
- All configurations verified to survive system reboots
- ACL default mount options enabled at filesystem level (tune2fs)
- rsyslog and Apache2 services enabled at boot via systemctl

## Regulatory Framework Alignment

| Requirement | Framework Reference |
|------------|-------------------|
| Workforce Security | HIPAA § 164.308(a)(3) |
| Information Access Management | HIPAA § 164.308(a)(4) |
| Access Control | HIPAA § 164.312(a)(1) |
| Audit Controls | HIPAA § 164.312(b) |
| Minimum Necessary Standard | HIPAA § 164.502(b), § 164.514(d) |
| Logical Access Controls | SOC 2 CC6.1 |
| System Monitoring | NIST CSF DE.CM-1 |
| Access Control Policy | ISO 27002 5.15 |

## Tools & Technologies

Linux (Ubuntu), ACLs (setfacl/getfacl), rsyslog, Apache2, PHP, Bash scripting

## Verification Commands
```bash
# Check user accounts
cat /etc/passwd | grep -E "senioranalyst|projecta|projectb"

# Check ACL permissions
getfacl /projects/project-a

# Check services status
sudo systemctl status rsyslog apache2

# View security violations
sudo tail -20 /var/log/security-violations.log
```

## Contact

- [LinkedIn](https://www.linkedin.com/in/jonathanwdoolan)
- Email: doolanjw0@gmail.com
