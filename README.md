# 🔍 Linux eBPF Real-Time Security & Syscall Tracer

> A lightweight kernel-level security observability and threat detection tool using extended Berkeley Packet Filters (eBPF) to monitor syscalls, privilege escalation, and suspicious process activity in real time.

[![Author](https://img.shields.io/badge/Made%20by-cyber--atharv-00ffcc?style=flat-square&logo=github)](https://github.com/cyber-atharv)
[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![eBPF](https://img.shields.io/badge/eBPF-Kernel_Tracing-A8B9CC?style=flat-square&logo=linux)](https://ebpf.io)
[![License](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](LICENSE)

---

## 📌 What is eBPF in Cybersecurity?

**eBPF (extended Berkeley Packet Filter)** is a revolutionary Linux kernel technology that allows custom monitoring programs to run directly inside the kernel safely, with near-zero performance overhead and without modifying kernel code.

Traditional security monitors in user space can be bypassed or blinded by rootkits. By tracing at the eBPF kernel layer, this tool, created by **cyber-atharv**, intercepts raw system calls (like `execve`, `connect`, `setuid`, `ptrace`) the exact instant they happen, making it impossible for malware to hide process execution.

---

## ✨ Key Features

- **Real-Time Syscall Hooks:** Hooks kernel tracepoints for process launches (`execve`), network sockets (`connect`/`accept`), file opens (`openat`), and privilege changes (`setuid`).
- **10 MITRE ATT&CK Threat Detection Rules:**
  - **D001:** Unauthorized privilege escalation attempts (`setuid(0)`).
  - **D002:** Access to credential stores (`/etc/shadow`).
  - **D003:** SSH private key access.
  - **D004:** Process injection via `ptrace`.
  - **D005:** Stealth kernel module loads (`init_module`).
  - **D006:** Outbound reverse shell connections.
- **Enriched Telemetry:** Automatically correlates process IDs (PID) with parent processes, usernames, and binary paths via `/proc`.
- **Flexible Output:** Live color-coded terminal alerts, structured JSON streams, and JSONL event log files.

---

## 🚀 Quick Start & Usage

### 1. Requirements & Setup
> Note: Requires a Linux system with kernel >= 5.8 and root privileges.

```bash
cd linux-ebpf-security-tracer
chmod +x install.sh
./install.sh
```

### 2. Live Monitoring

#### 🔹 Stream all security events live in terminal
```bash
sudo python -m ebpf_tracer.cli
```

#### 🔹 Only show High & Critical security alerts
```bash
sudo python -m ebpf_tracer.cli --detections -s HIGH
```

#### 🔹 Monitor network connections only
```bash
sudo python -m ebpf_tracer.cli -t network
```

#### 🔹 Stream events as JSON to file
```bash
sudo python -m ebpf_tracer.cli -f json -o security_events.jsonl
```

---

## 🧠 Why I Built This

eBPF is the future of Linux observability, cloud-native security, and next-generation EDRs (like Falco and Tetragon). Writing custom eBPF programs in C and Python helped me understand the boundary between user-space and kernel-space execution, low-level syscall conventions, and runtime behavioral threat detection.

---

## ⚠️ Educational & Defensive Notice

> Built for educational research, threat hunting, and defensive telemetry on authorized systems.

---

## 📜 Author & License

- **Author:** [cyber-atharv](https://github.com/cyber-atharv)
- **License:** Open source under the MIT / AGPL License.
