Week 7 – Log Monitoring & Audit Analysis
Overview

This week focused on monitoring and analysing system logs to identify authentication activity, security events, and potential indicators of compromise. Log analysis is a critical component of system security as it enables administrators to detect suspicious behaviour, investigate incidents, and validate the effectiveness of implemented security controls.

1. Authentication Log Analysis

Linux authentication logs were reviewed to examine SSH login activity and verify that access controls are functioning as expected.

Command executed:

sudo cat /var/log/auth.log | tail -n 20


<img width="404" height="304" alt="image" src="https://github.com/user-attachments/assets/d50beb1c-b32e-4ea1-b5ee-efd9071f50e5" />

(Screenshot showing recent SSH authentication entries from /var/log/auth.log with visible adminuser@os-server prompt)

Explanation:
The authentication log records successful and failed login attempts, privilege escalations, and SSH access events. Reviewing these entries confirms that only authorised users are accessing the system and that security controls such as Fail2Ban and SSH hardening are active.

2. Failed Login Attempts Review

To specifically check for failed authentication attempts, the log was filtered to highlight unsuccessful SSH access.

Command executed:

sudo grep "Failed password" /var/log/auth.log


<img width="402" height="40" alt="image" src="https://github.com/user-attachments/assets/f84e56ea-1d29-4473-b2ed-2fe215bf75f9" />

(Screenshot showing failed SSH login attempts or no output if none are present)

Explanation:
The absence of repeated failed login attempts indicates that brute-force attacks are either not occurring or are being effectively mitigated by Fail2Ban.

3. Fail2Ban Log Verification

Fail2Ban logs were reviewed to confirm that intrusion prevention mechanisms are actively monitoring authentication events.

Command executed:

sudo cat /var/log/fail2ban.log | tail -n 20

<img width="407" height="213" alt="image" src="https://github.com/user-attachments/assets/9b0ac95a-1c90-4f4e-a72d-ba0013bf94e9" />

(Screenshot showing Fail2Ban monitoring activity with visible adminuser@os-server prompt)

Explanation:
Fail2Ban logs provide insight into detected threats, banned IP addresses, and jail activity. This confirms that automated intrusion prevention is functioning correctly.

4. System Journal Review

The system journal was queried to review recent security-relevant system events.

Command executed:

sudo journalctl -xe | tail -n 20


<img width="404" height="305" alt="image" src="https://github.com/user-attachments/assets/4b384d1b-9e2b-4f76-be10-965bd8ce55e7" />

(Screenshot showing system journal entries related to services, SSH, or security events)

Explanation:
The system journal consolidates logs from multiple services, allowing efficient investigation of system behaviour and error conditions.

Reflection

Regular log monitoring provides visibility into system activity and strengthens incident detection capabilities. By analysing authentication logs, Fail2Ban activity, and system journal entries, potential security threats can be identified early, reducing response time and limiting impact. This week reinforces the importance of logs as both a preventative and investigative security control.
