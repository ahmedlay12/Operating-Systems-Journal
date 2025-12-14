Week 2 – Security Baseline & Threat Assessment
Overview

A baseline security assessment was conducted to identify the system’s exposure prior to implementing hardening controls. This establishes a reference point for later comparison and validation of security improvements introduced in subsequent weeks.

1. Firewall Status (UFW)

The Uncomplicated Firewall (UFW) was verified to be active to enforce basic network-level protection.

SSH (TCP port 22) is permitted for both IPv4 and IPv6 to allow remote administration

All other inbound traffic is denied by default

This configuration minimises the attack surface while maintaining required management access.

Command used:

sudo ufw status

<img width="320" height="96" alt="image" src="https://github.com/user-attachments/assets/b9b99f70-731a-4813-8058-4b0b1ef4a198" />


(Screenshot showing sudo ufw status with firewall active and port 22 allowed)

2. SSH Service Status

The SSH service was confirmed to be running and enabled at system startup. This ensures secure remote administration of the headless server.

SSH daemon is active and listening on port 22

Service is enabled to start automatically at boot

Command used:

sudo systemctl status ssh


<img width="383" height="158" alt="image" src="https://github.com/user-attachments/assets/19c23d5d-7af8-4776-bfdf-4c1bbf6bb894" />

(Screenshot showing sudo systemctl status ssh with service active and running)

3. Open Ports and Listening Services

Network sockets were inspected to identify active listening services on the system.

Only SSH (port 22) is listening on all interfaces

No unnecessary or unintended services were detected

This confirms that the system is not exposing additional services that could increase the attack surface.

Command used:

sudo ss -tuln


<img width="401" height="77" alt="image" src="https://github.com/user-attachments/assets/13e99e54-65b6-4e0a-9d19-c734b390df20" />

(Screenshot showing sudo ss -tuln output with only port 22 listening)

4. Threat Identification

Based on the baseline assessment, the following threats were identified:

SSH brute-force attacks
Automated login attempts targeting SSH could lead to unauthorised access

Weak or reused credentials
Increases the risk of privilege escalation

Network exposure
Services listening on all interfaces could allow remote exploitation

Lack of intrusion detection
Attacks may go unnoticed, resulting in delayed response

5. Planned Mitigations

To address the identified risks, the following controls will be implemented in later weeks:

SSH hardening (disable root login, restrict allowed users)

Intrusion prevention using Fail2Ban

Firewall rule refinement

Enhanced logging and monitoring of authentication events

These mitigations aim to reduce both the likelihood and impact of identified threats.

Reflection

This week established a clear security baseline for the system. Verifying firewall rules, active services, and exposed ports provided visibility into the system’s initial risk posture. Identifying realistic threats at this stage ensures that future hardening steps are targeted, measurable, and aligned with real-world attack scenarios.
