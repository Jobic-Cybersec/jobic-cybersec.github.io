# Linux System Hardening with Lynis

## Overview
This project demonstrates a practical Linux system hardening exercise conducted
on an Ubuntu 22.04 LTS system running inside a Docker container. The objective was
to identify common security misconfigurations using the Lynis auditing tool and
apply remediation measures aligned with industry best practices such as CIS
Benchmarks and GDPR security principles.

## Tools & Environment
- Docker (Ubuntu 22.04 LTS container)
- Lynis Security Auditing Tool
- Linux command-line utilities (chmod, chown)
- Windows PowerShell (host environment)

## Audit Findings (Before Hardening)
The initial Lynis security audit identified several weaknesses, including:
- Insecure permissions on cron configuration files
- Incorrect ownership of multiple user home directories
- Missing or weak hardening controls
- Initial hardening index score of **59**

These issues posed risks related to privilege escalation, unauthorized access,
and compliance gaps.

## Remediation Actions
The following corrective actions were implemented to address the identified risks:

```bash
sudo chmod 600 /etc/crontab
sudo chmod 700 /etc/cron.d
sudo chmod 700 /etc/cron.hourly
sudo chmod 700 /etc/cron.daily
sudo chmod 700 /etc/cron.weekly
sudo chmod 700 /etc/cron.monthly

sudo chown Benny:Benny /home/Benny
sudo chown Benny:Benny /home/AnotherUser
```

These changes enforced the principle of least privilege and ensured proper
ownership of user directories.

## Validation (After Hardening)
After applying the remediation steps, the system was re-audited using Lynis.
The follow-up audit confirmed that the identified permission and ownership issues
were resolved and that the system’s overall security posture had improved.

## Notes
This lab was conducted in a containerized environment for learning and testing
purposes. Some findings (e.g., networking and hardware identifiers) are expected
limitations of containerized systems.

 

