Week 1 – System Planning & Architecture
1. System Architecture Overview

This coursework adopts a dual-system architecture consisting of a headless Linux server and a separate workstation used exclusively for remote administration via SSH. This design enforces command-line proficiency and reflects professional server management practices commonly used in production environments.

Server: Ubuntu Server 22.04 LTS (headless)

Workstation: Windows host machine using PowerShell as the SSH client

Administration method: SSH-only remote access

This separation ensures that all configuration and management tasks are performed securely and remotely, minimising direct interaction with the server console.

2. Network Configuration Summary

A dual-network configuration was implemented to separate secure management traffic from outbound internet connectivity.

A host-only network is used for secure SSH administration between the workstation and the server.

A NAT adapter is used solely for outbound internet access, such as system updates and package installation.

VirtualBox Network Configuration

Adapter 1: Host-only Adapter

Adapter 2: NAT

IP Addressing

Host-only IP (server): 192.168.56.101/24

NAT IP (server): Dynamically assigned (e.g. 10.0.3.15/24)

This configuration reduces the server’s exposure while maintaining necessary connectivity for maintenance tasks.

3. Distribution Selection Justification
Selected Distribution

Ubuntu Server 22.04 LTS (Headless)

Justification

The Long-Term Support (LTS) release provides stability and extended security updates.

Strong documentation and community support simplify troubleshooting and configuration.

A minimal headless installation reduces the attack surface compared to desktop environments.

A large package repository supports the installation of security, monitoring, and testing tools required later in the coursework.

Alternatives Considered

Debian

Pros: Extremely stable and minimal.

Cons: Older package versions may limit access to newer tools.

RHEL-based distributions

Pros: Enterprise-aligned tooling and security features.

Cons: Higher complexity and a steeper learning curve for this coursework context.

4. Workstation Configuration Decision

Chosen option: Windows host machine with PowerShell SSH client.

This approach allows native SSH access without deploying additional virtual machines, reducing host resource usage and reflecting real-world remote administration workflows used by system administrators.

5. Baseline System Specifications (CLI Evidence)

Baseline system specifications were captured to establish a reference point for later security hardening and performance analysis.

Operating System and Kernel

Commands used:

uname -a
lsb_release -a


IMAGE:
Screenshot showing uname -a and lsb_release -a output with a visible adminuser@os-server command prompt.

<img width="816" height="174" alt="image" src="https://github.com/user-attachments/assets/df94ec41-9b8c-462e-89a6-82440405ee7a" />


Challenges Encountered

During the initial setup, the NAT network interface did not consistently initialise automatically after reboot. This issue was resolved by manually bringing the interface up and renewing the DHCP lease, followed by verification of normal network behaviour.

Reflection

This week established the foundational architecture for the coursework by enforcing secure remote administration via SSH and separating management traffic from outbound connectivity. Documenting the baseline system configuration provides a stable reference point for subsequent security hardening, monitoring, and performance evaluation activities.
