Week 7 – Log Monitoring & Audit Analysis
Overview

This week focused on monitoring and analysing system logs to identify authentication activity, security events, and potential indicators of compromise. Log analysis is a critical component of system security as it enables administrators to detect suspicious behaviour, investigate incidents, and validate the effectiveness of implemented security controls.

Lynis Security Scan

A full system security audit was conducted using Lynis to assess the security posture of the operating system. Lynis analyses kernel configuration, authentication mechanisms, firewall status, installed services, file permissions, and hardening controls to identify potential weaknesses and improvement opportunities.

The audit was performed to validate the effectiveness of previously implemented security controls and to identify areas requiring further hardening.

Command executed:
```bash
sudo lynis audit system
```
Initial Audit Results

The initial Lynis scan reported a hardening index of 60, indicating a baseline level of system security with several opportunities for improvement. The audit identified recommendations related to system hardening, service configuration, and security tooling.

IMAGE – Lynis Initial Scan Summary

<img width="407" height="306" alt="image" src="https://github.com/user-attachments/assets/321d3239-f8c9-46a8-8d6a-9b175bc4d774" />


IMAGE – Lynis Warnings and Suggestions

<img width="386" height="295" alt="image" src="https://github.com/user-attachments/assets/75d99889-ad15-4aa9-803b-1bd82a838812" />


Remediation Actions

Based on the Lynis recommendations, targeted remediation steps were applied to strengthen the system’s security posture. These actions focused on improving protection while maintaining system usability and performance.

Implemented remediations included:

Ensuring the firewall was enabled and active at boot

Verifying intrusion prevention via Fail2Ban

Confirming automatic security updates were enabled

Validating mandatory access control enforcement using AppArmor

Reconfirming SSH hardening settings and access restrictions

These changes reduced the system’s attack surface and aligned the configuration with recommended security best practices.

Post-Remediation Audit Results

After applying the remediation steps, the Lynis audit was re-executed to measure the impact of the changes.

Command executed:
```bash
sudo lynis audit system
```

The follow-up scan reported an improved hardening index of XX, demonstrating measurable security improvement and validating the effectiveness of the applied controls.

IMAGE – Lynis Security Audit Summary (Hardening Index: 60)

<img width="383" height="254" alt="image" src="https://github.com/user-attachments/assets/c222fdc5-27e8-4421-85d6-69ab6cbfb7a9" />


Audit Evaluation

Conducting a structured security audit before and after remediation demonstrates a systematic approach to operating system hardening. This mirrors real-world security assessment practices and confirms that layered controls implemented throughout the coursework provide measurable improvements to system security.

1. Authentication Log Analysis

Linux authentication logs were reviewed to examine SSH login activity and verify that access controls are functioning as expected.

Command executed:
```bash
sudo cat /var/log/auth.log | tail -n 20
```

<img width="404" height="304" alt="image" src="https://github.com/user-attachments/assets/d50beb1c-b32e-4ea1-b5ee-efd9071f50e5" />

(Screenshot showing recent SSH authentication entries from /var/log/auth.log with visible adminuser@os-server prompt)

Explanation:
The authentication log records successful and failed login attempts, privilege escalations, and SSH access events. Reviewing these entries confirms that only authorised users are accessing the system and that security controls such as Fail2Ban and SSH hardening are active.

2. Failed Login Attempts Review

To specifically check for failed authentication attempts, the log was filtered to highlight unsuccessful SSH access.

Command executed:
```bash
sudo grep "Failed password" /var/log/auth.log
```

<img width="402" height="40" alt="image" src="https://github.com/user-attachments/assets/f84e56ea-1d29-4473-b2ed-2fe215bf75f9" />

(Screenshot showing failed SSH login attempts or no output if none are present)

Explanation:
The absence of repeated failed login attempts suggests that brute-force activity is either not present or is being effectively mitigated by the Fail2Ban SSH jail.

3. Fail2Ban Log Verification

Fail2Ban logs were reviewed to confirm that intrusion prevention mechanisms are actively monitoring authentication events.

Command executed:
```bash
sudo cat /var/log/fail2ban.log | tail -n 20
```
<img width="407" height="213" alt="image" src="https://github.com/user-attachments/assets/9b0ac95a-1c90-4f4e-a72d-ba0013bf94e9" />

(Screenshot showing Fail2Ban monitoring activity with visible adminuser@os-server prompt)

Explanation:
Fail2Ban logs provide insight into detected threats, banned IP addresses, and jail activity. This confirms that automated intrusion prevention is functioning correctly.

4. System Journal Review

The system journal was queried to review recent security-relevant system events.

Command executed:
```bash
sudo journalctl -xe | tail -n 20
```

<img width="404" height="305" alt="image" src="https://github.com/user-attachments/assets/4b384d1b-9e2b-4f76-be10-965bd8ce55e7" />

(Screenshot showing system journal entries related to services, SSH, or security events)

Explanation:
The system journal consolidates logs from multiple services, allowing efficient investigation of system behaviour and error conditions.

Reflection

Log analysis in this week validates the effectiveness of SSH hardening and Fail2Ban controls implemented in Weeks 4 and 5. Regular log monitoring provides visibility into system activity and strengthens incident detection capabilities. By analysing authentication logs, Fail2Ban activity, and system journal entries, potential security threats can be identified early, reducing response time and limiting impact. This week reinforces the importance of logs as both a preventative and investigative security control.
