Week 3 – Application Selection for Performance Testing
Overview

This week focused on selecting representative applications to evaluate operating system performance under different workload types. The objective was to assess how the Linux operating system behaves when subjected to CPU, memory, disk, and network intensive workloads, as well as a long-running server service.

Each selected application represents a distinct resource profile to enable structured performance analysis in later testing phases.

Application Selection Matrix
Application	Workload Type	Justification
stress-ng	CPU & Memory Intensive	Widely used benchmarking tool capable of generating controlled CPU and RAM load to observe scheduling and memory management behaviour
fio	Disk I/O Intensive	Industry-standard tool for testing disk throughput, latency, and I/O patterns
iperf3	Network Intensive	Used to measure network throughput and latency between systems
apache2	Server / Service Load	Represents a persistent network-facing service to observe process behaviour, resource usage, and service response under load
Installation Documentation (SSH-Based)

All applications were installed remotely on the server via SSH using the system package manager.

Package Installation Commands
sudo apt update
sudo apt install -y stress-ng fio iperf3 apache2


These commands ensure that all required tools are available for performance testing while maintaining a minimal and controlled server environment.

Expected Resource Profiles
stress-ng

High CPU utilisation across available cores

Increased memory allocation depending on stress parameters

Useful for observing scheduler behaviour and memory pressure handling

fio

High disk read/write activity

Increased I/O wait times under load

Useful for evaluating disk performance and filesystem behaviour

iperf3

High network throughput during testing

Minimal CPU and disk usage

Useful for analysing network stack performance

apache2

Persistent background service

Moderate memory footprint

Network activity dependent on client requests

Useful for observing long-running service behaviour and system stability

Monitoring Strategy

System performance will be monitored remotely from the workstation using standard command-line tools.

Metrics to be Collected

CPU usage

Memory usage

Disk I/O activity

Network throughput

Process behaviour

Monitoring Tools
top
htop
vmstat
iostat
ss


These tools provide real-time and summary statistics that will be recorded during baseline and load testing in the next phase.

Reflection

This week established a structured foundation for performance evaluation by selecting applications that stress different operating system subsystems. Defining expected resource profiles in advance allows meaningful comparison between baseline and load conditions.

This preparation ensures that subsequent performance testing and optimisation efforts can be measured objectively and linked directly to operating system behaviour.
