Week 4 – SSH Hardening & Secure Access Control
Overview

This week focused on hardening Secure Shell (SSH) access to reduce the risk of unauthorised remote access. As SSH is the primary management interface for the server, securing it is critical to limiting attack vectors and protecting administrative credentials.

The objective was to enforce least-privilege access, remove unsafe defaults, and validate the effectiveness of the applied controls.

Threat Context

SSH services are frequently targeted by attackers through:

Brute-force password attacks

Credential reuse attempts

Privilege escalation via root login

Leaving default SSH configurations in place significantly increases exposure. Therefore, proactive hardening was required before introducing further services or performance testing.

SSH Hardening Measures Implemented
Disable Root Login

Direct root login over SSH was disabled to prevent attackers from attempting privileged access directly.

sudo nano /etc/ssh/sshd_config


The following configuration change was applied:

PermitRootLogin no


Security impact:
This forces attackers to compromise a non-privileged account first, significantly reducing the risk of immediate full system compromise.

Restrict SSH Access to Approved User

SSH access was restricted to the dedicated administrative account.

AllowUsers adminuser


Security impact:
Only explicitly authorised users can authenticate via SSH, preventing access attempts from unknown local accounts.

Restart SSH Service

After applying configuration changes, the SSH service was restarted to enforce the new rules.

sudo systemctl restart ssh

Configuration Verification

The active SSH configuration was verified using the following commands.

sudo sshd -T | grep permitrootlogin


<img width="303" height="44" alt="image" src="https://github.com/user-attachments/assets/1e57275d-e809-41a2-b1bf-c85bde479546" />

Screenshot showing permitrootlogin no with visible adminuser@os-server prompt


sudo sshd -T | grep allowusers


<img width="272" height="37" alt="image" src="https://github.com/user-attachments/assets/e2a667b7-2d6f-4271-a405-1154fb005268" />

Screenshot confirming allowusers adminuser


Service Status Validation

The SSH service status was checked to confirm it was running correctly after hardening.

sudo systemctl status ssh


<img width="358" height="152" alt="image" src="https://github.com/user-attachments/assets/990c214a-0b12-46ef-8203-f6d4d1b0a998" />

Screenshot showing SSH service active (running)


Reflection

Hardening SSH at this stage significantly reduces the system’s exposure to common remote attacks. Disabling root login and restricting access to a specific administrative user enforces least-privilege principles and aligns the system with secure configuration best practices.

This week establishes a hardened remote administration baseline, ensuring that future firewall adjustments, service deployments, and performance testing are performed on a securely managed system.
