# Week 3 – Tooling Installation & System Preparation

## Overview

This week focused on preparing the Ubuntu Server system with essential tooling required for later performance testing and security assessment. Installing and verifying these tools at this stage ensures the environment is ready for controlled testing in subsequent weeks.

---

## Tool Selection Rationale

The following tools were selected to support later coursework activities:

- **Apache2**  
  Installed to provide a realistic network-facing service. This allows testing of firewall rules, service exposure, and future security hardening techniques.

- **iperf3**  
  Installed to perform controlled network bandwidth and throughput testing between systems.

- **stress-ng**  
  Installed to generate CPU and memory load in order to observe system behaviour under stress conditions.

These tools establish a controlled and realistic baseline for later security and performance evaluation.

---

## Installation Verification

The following command was used to verify that all required tools were successfully installed on the system:

```bash
dpkg -l | grep -E "stress-ng|iperf3|apache2"
```



Evidence: Screenshot showing installed apache2, iperf3, and stress-ng packages with visible adminuser@os-server command prompt.

<img width="452" height="142" alt="image" src="https://github.com/user-attachments/assets/37bd71c7-4599-48fd-af33-0a7fced996b7" />


Reflection

Completing tool installation and verification during this week ensures that later performance testing and security hardening can be carried out without configuration uncertainty. This structured preparation reduces risk and supports reliable analysis in subsequent coursework phases.
