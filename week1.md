# Week 1 – System Planning & Architecture

## 1. System Architecture Overview

This coursework uses a dual-system architecture consisting of a headless Linux server and a separate workstation for remote administration via SSH. This approach enforces command-line proficiency and mirrors professional server management practices.

- Server: Ubuntu Server 22.04 LTS (headless)
- Workstation: Windows host machine (PowerShell SSH client)
- Administration method: SSH only

---

## 2. Network Configuration Summary

A dual-network configuration was implemented to separate secure management access from outbound internet connectivity.

- Host-only network is used for secure SSH administration from workstation to server
- NAT adapter is used only for outbound internet access (updates and package installation)

### VirtualBox Network Configuration
- Adapter 1: Host-only Adapter
- Adapter 2: NAT

### IP Addressing
- Host-only IP (server): 192.168.56.101/24  
- NAT IP (server): Dynamic (e.g. 10.0.3.15/24)

---

## 3. Distribution Selection Justification

### Selected Distribution
**Ubuntu Server 22.04 LTS (Headless)**

### Justification
- Long-Term Support (LTS) provides stability and extended security updates
- Strong documentation and community support
- Minimal headless installation reduces attack surface
- Large package repository supports security and monitoring tools

### Alternatives Considered

**Debian**
- Pros: Extremely stable and minimal
- Cons: Older package versions

**RHEL-based distributions**
- Pros: Enterprise-aligned tooling
- Cons: Higher complexity

---

## 4. Workstation Configuration Decision

**Chosen option:** Windows host machine with PowerShell SSH client.

This option allows native SSH access without additional virtual machines, reduces host resource usage, and reflects real-world administration workflows.

---

5. Baseline System Specifications (CLI Evidence)

Baseline system specifications were captured to establish a reference point for later security hardening and performance analysis.

Operating System and Kernel

Commands used:

uname -a
lsb_release -a


<img width="408" height="87" alt="image" src="https://github.com/user-attachments/assets/b70a5080-8953-44f1-8a44-dcef43f27fdc" />

(Screenshot showing uname -a and lsb_release -a output with visible adminuser@os-server prompt)

Challenges Encountered

During initial setup, the NAT interface did not consistently initialise automatically after reboot. This issue was resolved by manually bringing the interface up and renewing the DHCP lease.

Reflection

This week established the foundational architecture for the coursework by enforcing remote administration via SSH and separating management traffic from outbound connectivity. Capturing baseline specifications provides a stable reference point for future security hardening and performance evaluation.
