# IT Troubleshooting Lab

A hands-on technical lab documenting practical IT troubleshooting, diagnostics, fault isolation, system recovery, operating-system deployment, hardware diagnostics, storage recovery, networking, and infrastructure troubleshooting.

The repository is designed for two purposes:

1. **Portfolio evidence:** demonstrate practical IT infrastructure, endpoint support, system administration, networking, diagnostics, recovery, and troubleshooting skills.
2. **Technical reference:** provide structured troubleshooting workflows that another technician, student, or IT professional can follow when diagnosing systems, networks, and infrastructure problems.

> **Scope:** This repository covers IT troubleshooting across endpoints, hardware, operating systems, storage, recovery environments, networking, and infrastructure. It is designed to expand into server, virtualization, cloud, monitoring, and security troubleshooting.

## Core Philosophy

The objective is not to collect tools or memorize commands.

The objective is to develop a repeatable engineering method for identifying symptoms, collecting evidence, isolating faults, determining root causes, applying appropriate remediation, and validating the result.

```text
INCIDENT
   |
   v
IDENTIFY SYMPTOM
   |
   v
GATHER INFORMATION
   |
   v
DEFINE SCOPE & IMPACT
   |
   v
FORM HYPOTHESES
   |
   v
TEST HYPOTHESES
   |
   v
ISOLATE FAULT DOMAIN
   |
   v
IDENTIFY ROOT CAUSE
   |
   v
SELECT REMEDIATION
   |
   v
APPLY REMEDIATION
   |
   v
VALIDATE FIX
   |
   v
DOCUMENT / PREVENT
```

A diagnostic result is evidence, not automatically a root cause.

Every remediation should be validated after the change, and important incidents should be documented for future reference and prevention.

# Troubleshooting Domains

The repository is organized around practical IT troubleshooting domains.

<p align="center">
  <img src="images/IT Troubleshooting Taxonomy.png" />
</p>

The domains are intentionally expandable. New troubleshooting areas can be added without changing the overall structure of the repository.

# Skills Demonstrated

## IT Support Troubleshooting

- Help desk and user issue diagnosis
- Hardware, software, OS, and peripheral support
- System configuration and basic connectivity troubleshooting
- User-focused issue resolution and escalation

## Endpoint Troubleshooting

- Windows/Linux installation and deployment
- WinRE/WinPE and bootable recovery media
- Windows Boot Manager and GRUB recovery
- UEFI/BIOS and boot troubleshooting
- Hardware, RAM, storage, and filesystem diagnostics
- Partition, backup, and data recovery
- Peripheral and application troubleshooting
- Offline malware scanning
- System health verification
- Technical incident documentation

## Network Troubleshooting

- TCP/IP, IPv4/IPv6, DHCP, DNS, and ARP
- Gateway and routing troubleshooting
- Ethernet and Wi-Fi diagnostics
- Connectivity, latency, and packet-loss analysis
- Port and firewall troubleshooting
- Network configuration and path analysis
- Layered network fault isolation

## System & Infrastructure Troubleshooting

- Windows/Linux system diagnostics
- Performance and resource analysis
- Service and log troubleshooting
- Server and virtualization diagnostics
- Monitoring and infrastructure fault isolation

## Security Troubleshooting

- Malware and endpoint security triage
- Suspicious process/network investigation
- Security event analysis
- Incident isolation and validation

# Engineering Concepts

The repository focuses on transferable troubleshooting principles rather than individual tools.

- Fault isolation
- Root-cause analysis
- Evidence-based troubleshooting
- Hypothesis-driven diagnosis
- Layered troubleshooting
- Fault-domain isolation
- Least-destructive-first remediation
- Backup-before-modification
- Change awareness
- Dependency analysis
- Recovery planning
- Validation after remediation
- Preventive actions
- Incident documentation
- Reproducibility
- Escalation based on evidence

# Diagnostic Architecture

Different incidents require investigation at different layers.

For endpoint and workstation problems:

```text
+--------------------------------------------------+
|                 USER / SYMPTOM                   |
|   User reports an issue or unexpected behaviour  |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|          APPLICATION / SERVICES                  |
| Check application logs, errors, services state,  |
| and application health                           |  
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|              OPERATING SYSTEM                    |
| Investigate processes, filesystems, system logs, |
| memory and drivers                               |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|                   NETWORK                        |
| Verify network connectivity and configuration    |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|                   STORAGE                        |
| Check storage health, partitions and filesystems |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|                   HARDWARE                       |
|        Diagnose physical components              |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|               FIRMWARE / BOOT                    |
|     Verify UEFI/BIOS settings and bootloader     |
+--------------------------------------------------+
```

The correct starting layer depends on the observed symptom.

The purpose of the investigation is to narrow this fault domain using evidence rather than immediately applying fixes.

# Network Troubleshooting Model

Network incidents should also be approached systematically.

```text
+--------------------------------------------------+
|               USER / APPLICATION                 |
| User or application is accessing a network       |
| resource or service                              |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|                SERVICE / PORT                    |
| Verify the required service is running and       |
| the destination port is reachable                |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|                     DNS                          |
| Verify the hostname resolves to the correct      |
| destination IP address                           |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|                IP CONFIGURATION                  |
| Verify IP address, subnet mask, gateway and DNS  |
| configuration                                    |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|                 DEFAULT GATEWAY                  |
| Verify the device can reach its local router     |
| or default gateway                               |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|                  LOCAL NETWORK                   |
| Verify connectivity within the local network     |
| and network devices                              |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|                   ROUTING                        |
| Verify traffic has a valid path to the remote    |
| destination                                      |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|                 REMOTE NETWORK                   |
| Verify the remote network is reachable and       |
| responding                                       |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|              INTERNET / DESTINATION              |
| Verify final connectivity to the destination     |
| service or internet resource                     |
+--------------------------------------------------+
```

This helps distinguish problems such as:

- Physical/link failure
- Network adapter failure
- DHCP failure
- Incorrect IP configuration
- Default gateway failure
- Routing problems
- DNS failure
- Firewall restrictions
- Remote service failure
- Application-level problems

# Recovery Media Strategy

A bootable USB is useful because it allows diagnostics and recovery independently of the installed operating system.

Typical workflow:

<p align="center">
  <img src="images/Boot and Recovery Flowchart.png" />
</p>

Ventoy is an open-source bootable USB solution that can boot multiple ISO/WIM/IMG/VHD(x)/EFI images from one device. The project documents support for Windows/WinPE and Linux among other environments.

See the official Ventoy documentation before creating or modifying recovery media.

# Tool Matrix

| Domain | Tools / Environments | Purpose |
|---|---|---|
| Bootable media | Ventoy | Multi-image boot and recovery media |
| Windows recovery | WinRE / WinPE | Offline Windows troubleshooting |
| Linux recovery | Linux Live | Offline Linux/filesystem troubleshooting |
| Memory | MemTest86 | Stand-alone RAM diagnostics |
| Storage | SMART / NVMe / vendor utilities | Drive health and diagnostics |
| Partitioning | Disk/partition utilities | Partition inspection and recovery |
| Hardware | UEFI/OEM diagnostics | Pre-OS hardware testing |
| Windows networking | ipconfig, PowerShell, ping, tracert, nslookup | Network diagnosis |
| Linux networking | ip, ping, traceroute, dig, ss | Network diagnosis |
| DNS | nslookup, dig | DNS resolution troubleshooting |
| Routing | route, ip route, tracert, traceroute | Routing/path diagnosis |
| Connectivity | ping, Test-NetConnection, nc | Connectivity and port testing |
| Logs | Event Viewer, journalctl | OS/event investigation |
| Windows | PowerShell | System inspection and automation |
| Linux | Bash and standard CLI tools | System inspection and troubleshooting |
| Hardware monitoring | HWiNFO / vendor utilities | Hardware health and telemetry |
| Storage recovery | TestDisk / PhotoRec / recovery utilities | Data and partition recovery |
| Imaging | Clonezilla / Rescuezilla / imaging utilities | Disk imaging and migration |

# Recommended Case Study Format

Every troubleshooting case should document:

```text
Incident
  |
  +-- Symptom
  +-- Environment
  +-- Initial observations
  +-- Scope & impact
  +-- Hypotheses
  +-- Diagnostic tests
  +-- Evidence
  +-- Fault domain
  +-- Root cause
  +-- Remediation
  +-- Validation
  +-- Preventive action
```

Example:

> **Incident:** Windows fails to boot after a configuration change.

Do not write only:

> "Fixed Windows boot."

Instead document:

> Symptom → observed boot failure → verified hardware → inspected EFI/boot configuration → tested recovery commands → repaired boot configuration → rebooted → validated normal startup.

This demonstrates the reasoning behind the troubleshooting process rather than simply showing the final command.

# Safety and Data Protection

Recovery and diagnostic operations can cause permanent data loss.

Before modifying partitions, filesystems, boot configuration, or disks:

1. Identify the correct physical disk.
2. Determine whether the data is important.
3. Create a backup or forensic image where appropriate.
4. Avoid writing to a failing source disk unnecessarily.
5. Work from a copy when recovery integrity matters.
6. Record the original partition layout and relevant observations.
7. Validate recovered data before declaring success.
8. Confirm the target before destructive operations.
9. Document significant changes.
10. Use appropriate authorization for systems that are not personally owned.

For enterprise or third-party systems, obtain authorization before performing diagnostics, recovery, configuration changes, or security investigations.

# Disclaimer

This repository documents educational and authorized troubleshooting practices. Recovery and diagnostic operations can damage data or systems if performed incorrectly. Always verify the target device and maintain appropriate backups. Do not use these procedures on systems or data without authorization.
