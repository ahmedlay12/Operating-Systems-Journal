Week 2 – Security Baseline & Threat Assessment
Security Baseline Assessment

A baseline security assessment was conducted to identify the system’s exposure prior to implementing hardening controls. This establishes a reference point for later comparison and validation of security improvements.

Firewall Status

The Uncomplicated Firewall (UFW) was verified to be active. At this stage, only SSH traffic is permitted to allow remote administration.

SSH (TCP port 22) is allowed for both IPv4 and IPv6

All other inbound traffic is denied by default

This configuration minimises the attack surface while maintaining required management access.

<img width="416" height="284" alt="image" src="https://github.com/user-attachments/assets/ff78ff56-3b17-4564-af5f-8f0ddd29153f" />

Evidence: Screenshot showing sudo ufw status output with active firewall and port 22 allowed.

SSH Service Status

The SSH service was confirmed to be running and enabled at system startup. This allows secure remote administration of the headless server.

SSH daemon is active and listening on port 22

Service is enabled to start automatically at boot

<img width="416" height="284" alt="image" src="https://github.com/user-attachments/assets/ff78ff56-3b17-4564-af5f-8f0ddd29153f" />

Evidence: Screenshot showing sudo systemctl status ssh output.

Open Ports and Listening Services

Network sockets were inspected to identify active listening services.

Only SSH (port 22) is listening on all interfaces

No unnecessary services were detected

This confirms that the system is not exposing unintended network services.

<img width="416" height="284" alt="image" src="https://github.com/user-attachments/assets/ff78ff56-3b17-4564-af5f-8f0ddd29153f" />

Evidence: Screenshot showing sudo ss -tuln output.

Threat Identification

Based on the baseline assessment, the following threats were identified:

Threat	Risk Description	Potential Impact
SSH brute-force attacks	Automated login attempts against SSH	Unauthorised access
Credential compromise	Weak or reused passwords	Privilege escalation
Network exposure	Services listening on all interfaces	Remote exploitation
Lack of monitoring	Attacks may go unnoticed	Delayed response
Planned Mitigations

The following controls will be implemented in later weeks:

SSH hardening (disable root login, limit authentication methods)

Intrusion prevention using Fail2Ban

Firewall rule refinement

Improved logging and monitoring of authentication events

These mitigations aim to reduce the likelihood and impact of identified threats.

Reflection

This week established a clear security baseline for the system. Verifying firewall rules, active services, and exposed ports provided visibility into the system’s initial risk posture. Identifying realistic threats at this stage ensures that future hardening steps are targeted and measurable.
