## Week 6 – Performance Monitoring & Stress Testing

### Overview
This week focused on analysing system performance under controlled load conditions. CPU and memory stress testing was conducted to observe system behaviour, while real-time monitoring tools were used to capture performance metrics. This establishes a performance baseline for comparison in later optimisation and security hardening stages.

---

### Baseline Performance Metrics (Remote Monitoring)
Baseline system performance metrics were collected remotely via SSH from the workstation. Monitoring was performed remotely from the workstation to reinforce the separation between management and server environments established in Week 1.

Command executed:
```bash
uptime && free -h && df -h
```

<img width="609" height="230" alt="image" src="https://github.com/user-attachments/assets/29ed853e-4b62-41c3-930a-0ff0927472ad" />

Screenshot showing uptime, free -h, and df -h with visible adminuser@os-server prompt

CPU Stress Testing

Controlled CPU load was applied to the system to observe behaviour under processing pressure.

Command executed:
```bash
stress-ng --cpu 2 --timeout 60s
```
Screenshot showing active CPU stress testing using stress-ng.

<img width="487" height="59" alt="image" src="https://github.com/user-attachments/assets/22008611-0eda-4904-b10b-1a158a1cca38" />


Memory Stress Testing

Memory load was generated to evaluate system stability under increased memory usage.

Command executed:
```bash
stress-ng --vm 1 --vm-bytes 512M --timeout 60s
```
Screenshot showing memory stress testing using stress-ng.

<img width="296" height="34" alt="image" src="https://github.com/user-attachments/assets/9ddf5a4e-06ee-4995-97ec-52e1549c7aa6" />


Live Resource Monitoring

Real-time system resource usage was monitored during stress testing.

Command executed:
```bash
top
```
Screenshot showing real-time CPU load, memory usage, and process activity during live system monitoring using the top command.

<img width="404" height="307" alt="image" src="https://github.com/user-attachments/assets/d544b6e3-2d8c-4322-bdf5-a3ad5f34d68c" />


Reflection

The system remained stable throughout CPU and memory stress testing, with no service interruptions or abnormal behaviour observed. Real-time monitoring confirmed that CPU load increased as expected and memory usage remained within safe limits. This demonstrates that the system can handle moderate workloads without degradation. Establishing this performance baseline supports future optimisation decisions and ensures that security hardening measures do not negatively impact system stability.
