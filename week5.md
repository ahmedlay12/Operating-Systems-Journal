Week 5 – Advanced Security Controls & Monitoring Infrastructure
Overview

This week focused on implementing advanced security mechanisms and monitoring capabilities to further harden the Ubuntu Server system. These controls enhance protection against unauthorised access, ensure timely patching, and provide automated verification of the system’s security posture.

1) Mandatory Access Control (AppArmor)

Ubuntu Server uses AppArmor to enforce Mandatory Access Control (MAC), restricting how applications interact with system resources.

Verification of AppArmor Status

The following command was used to confirm that AppArmor is enabled and enforcing policies:
```bash
sudo aa-status
```

<img width="403" height="302" alt="image" src="https://github.com/user-attachments/assets/121b30cc-828c-40b7-ad39-9646bb34cb38" />

Screenshot showing AppArmor status with profiles in enforce mode and visible adminuser@os-server prompt.

Reflection

AppArmor reduces the impact of potential compromises by limiting application permissions even if a service is exploited.

2) Automatic Security Updates

Automatic security updates were configured to ensure timely installation of critical patches without manual intervention.

Verification of Unattended Upgrades

The following command was used to confirm unattended upgrades are enabled:
```bash
systemctl status unattended-upgrades
```

<img width="407" height="118" alt="image" src="https://github.com/user-attachments/assets/ff8527de-95c7-478f-8952-56680b1ebe99" />

Screenshot showing unattended-upgrades service active (running).

Reflection

Automated patching significantly reduces exposure to known vulnerabilities, particularly on remotely administered systems.

3) Intrusion Prevention with Fail2Ban

Fail2Ban was configured to detect repeated failed login attempts and automatically block offending IP addresses.

Fail2Ban Service Status

The following command verified that Fail2Ban is active:
```bash
sudo systemctl status fail2ban
```
<img width="383" height="133" alt="image" src="https://github.com/user-attachments/assets/c94c2f30-0d42-4f74-89d6-7ac79bb6e05f" />

Screenshot showing Fail2Ban service active and running.

SSH Jail Verification

The following command was used to verify the SSH jail configuration:
```bash
sudo fail2ban-client status sshd
```

<img width="303" height="119" alt="image" src="https://github.com/user-attachments/assets/a251ab54-dc9c-4700-9df9-85462be05458" />

Screenshot showing SSH jail enabled with monitoring of /var/log/auth.log.

Reflection

Fail2Ban provides dynamic protection against brute-force attacks, complementing static firewall rules.

4) Security Baseline Verification Script

A security baseline verification script was created to automatically validate key security controls implemented across Weeks 4 and 5.

Script Purpose

The script verifies:

SSH root login is disabled

SSH user restrictions are enforced

Firewall is enabled

AppArmor is active

Automatic updates are enabled

Fail2Ban service is running

Script Execution

The script was executed remotely via SSH to validate the system state:

./security-baseline.sh


<img width="249" height="158" alt="image" src="https://github.com/user-attachments/assets/782f56a6-3b37-4b55-bb73-44ca69c7f03b" />

Screenshot showing successful execution of security-baseline.sh with pass/fail outputs.

5) Remote Monitoring via SSH

A remote monitoring process was implemented to collect live performance metrics from the server via SSH. This approach reflects real-world system administration practices, where servers are monitored and managed remotely without direct console access. Monitoring was performed from the workstation to reinforce the separation between management and server environments.

#### Metrics Collected
The following system metrics were retrieved remotely to assess operational health and resource utilisation:

- **CPU usage and load average**
- **Memory utilisation**
- **Disk usage and filesystem capacity**

These metrics provide immediate insight into system performance and stability during normal operation.

#### Script Execution
Monitoring commands were executed remotely from a Windows workstation using PowerShell over an encrypted SSH connection. The following command was used to retrieve live performance data:

```bash
uptime && free -h && df -h
```
This command outputs system uptime and load averages, memory availability, and disk usage in a concise and readable format suitable for ongoing monitoring.

Evidence:


<img width="659" height="293" alt="image" src="https://github.com/user-attachments/assets/f79f1ca4-69ab-48ab-addf-9b9b92ffc31f" />

Screenshot showing successful SSH connection from the Windows workstation to the server.

<img width="701" height="215" alt="image" src="https://github.com/user-attachments/assets/60011105-6c0d-4cca-b966-8f6d72151fe6" />

Screenshot showing real-time system performance metrics retrieved remotely via SSH.

Reflection

Implementing remote monitoring validates that the server can be securely accessed and assessed without physical interaction. Capturing live performance metrics establishes a reliable baseline for future stress testing and performance comparison, while reinforcing secure remote administration practices used in production environments.
