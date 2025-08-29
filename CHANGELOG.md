# Changelog

All notable changes to linux-ebpf-security-tracer will be documented in this file.

## [0.1.0] - 2025-08-22
- Initial commit: kernel syscall monitor with eBPF

## [0.1.1] - 2025-08-23
- feat: attach kprobes to sys_enter_execve and sys_enter_ptrace

## [0.1.2] - 2025-08-26
- feat: stream kernel events via perf ring buffer to user space

## [0.1.3] - 2025-08-29
- refactor: simplify user space event parser in Go

