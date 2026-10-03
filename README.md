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

## IT Support & Endpoint Troubleshooting

- Windows installation and deployment
- Linux installation and deployment
- Windows Recovery Environment (WinRE)
- Windows PE / WinPE
- Windows startup and boot troubleshooting
- Windows Boot Manager recovery
- Linux GRUB recovery
- UEFI/BIOS boot troubleshooting
- Partition management
- Filesystem troubleshooting
- Data backup and recovery workflows
- Offline system troubleshooting
- Bootable recovery media
- Hardware diagnostics
- Storage diagnostics
- RAM diagnostics
- Peripheral troubleshooting
- Application troubleshooting
- System health verification
- Offline malware/antivirus scanning
- Technical documentation and incident-style troubleshooting

## Network Troubleshooting

- TCP/IP troubleshooting
- IPv4 configuration
- IPv6 fundamentals
- DHCP troubleshooting
- DNS troubleshooting
- Default gateway troubleshooting
- Routing diagnosis
- ARP troubleshooting
- Network connectivity testing
- Packet-loss investigation
- Latency investigation
- Ethernet troubleshooting
- Wi-Fi troubleshooting
- Network adapter diagnostics
- Port connectivity testing
- Local-network troubleshooting
- Internet connectivity troubleshooting
- Firewall-related connectivity diagnosis
- Network configuration inspection
- Network path analysis
- Layered fault isolation

## System & Infrastructure Troubleshooting

- Windows system diagnostics
- Linux system diagnostics
- System performance analysis
- Service troubleshooting
- Event-log analysis
- Linux journal analysis
- Process and resource analysis
- Storage and filesystem diagnostics
- Boot and recovery troubleshooting
- Server troubleshooting
- Virtualization troubleshooting
- Monitoring and log analysis
- Infrastructure fault isolation

## Security Troubleshooting

- Malware triage
- Offline malware scanning
- Suspicious process investigation
- Suspicious network activity investigation
- Endpoint security troubleshooting
- Security event analysis
- Initial incident triage
- System isolation during security incidents
- Post-incident validation

# Diagnostic & Recovery Environments

This lab uses multiple environments depending on the fault domain.

### Boot & Recovery

- Ventoy
- Windows PE / WinPE
- Windows Recovery Environment / WinRE
- Linux Live environments
- Medicat
- Vendor recovery environments

### Hardware Diagnostics

- MemTest86
- UEFI/OEM diagnostics
- CPU diagnostics
- RAM diagnostics
- Storage diagnostics
- Hardware monitoring utilities

### Storage & Recovery

- SMART diagnostics
- NVMe utilities
- Disk and partition utilities
- Filesystem utilities
- Disk imaging tools
- Data recovery utilities
- Disk cloning tools

### Network Diagnostics

- Windows PowerShell
- Windows networking utilities
- Linux networking utilities
- Packet/path testing utilities
- DNS diagnostic utilities
- Socket and connection inspection tools

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

<p align="center">
  <img src="images/IT Troubleshooting Flowchart.png" />
</p>

The correct starting layer depends on the observed symptom.

The purpose of the investigation is to narrow this fault domain using evidence rather than immediately applying fixes.

# Network Troubleshooting Model

Network incidents should also be approached systematically.

<p align="center">
  <img src="images/Network Troubleshooting Flowchart.png" />
</p>

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

---

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

# Future Expansion

Planned additions include:

### Endpoint & OS

- Windows performance troubleshooting
- Windows event-log case studies
- PowerShell diagnostic scripts
- Linux system diagnostic scripts
- Linux boot and filesystem recovery
- Application troubleshooting

### Networking

- TCP/IP troubleshooting labs
- DNS troubleshooting
- DHCP troubleshooting
- Routing troubleshooting
- VLAN troubleshooting
- Switching fundamentals
- Wi-Fi troubleshooting
- Firewall troubleshooting
- Port and service connectivity
- Packet-analysis exercises

### Server & Enterprise Infrastructure

- Windows Server diagnostics
- Active Directory troubleshooting
- DNS server troubleshooting
- DHCP server troubleshooting
- File-server troubleshooting
- Authentication troubleshooting
- Group Policy troubleshooting
- Server performance diagnostics

### Virtualization

- Virtual machine boot problems
- Virtual networking problems
- Virtual disk problems
- Hypervisor troubleshooting
- VM performance diagnostics

### Monitoring & Observability

- System monitoring
- Resource monitoring
- Log analysis
- Event correlation
- Performance baselines
- Alert investigation
- Incident timelines

### Cloud Infrastructure

- Cloud connectivity troubleshooting
- Virtual network troubleshooting
- Security-group/firewall diagnosis
- Compute-instance troubleshooting
- Storage troubleshooting
- Load-balancer troubleshooting
- Cloud monitoring and logging

### Security

- Malware triage
- Endpoint security troubleshooting
- Suspicious process investigation
- Network security investigation
- Security-event analysis
- Incident response fundamentals

# Official Documentation

- Microsoft Windows Recovery Environment: https://learn.microsoft.com/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference
- Microsoft Windows recovery framework: https://learn.microsoft.com/en-us/windows/configuration/windows-device-recovery-framework
- Microsoft WinRE troubleshooting features: https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/windows-re-troubleshooting-features
- Ventoy documentation: https://www.ventoy.net/en/doc_start.html
- Ventoy source repository: https://github.com/ventoy/Ventoy
- MemTest86: https://www.memtest86.com/
- MemTest86 user guide: https://www.memtest86.com/userguide.html
- Ubuntu bootable USB documentation: https://ubuntu.com/desktop/docs/en/latest/how-to/create-a-bootable-usb-stick/

Always obtain third-party software from its official project/vendor source and verify downloads where checksums or signatures are provided.

# Disclaimer

This repository documents educational and authorized troubleshooting practices.

Recovery, diagnostic, networking, configuration, and security operations can damage data or systems if performed incorrectly.

Always:

- Verify the target system.
- Maintain appropriate backups.
- Understand the potential impact of changes.
- Obtain authorization before working on third-party systems.
- Avoid destructive operations until non-destructive diagnostic options have been exhausted.
- Follow vendor and organizational procedures where applicable.

Do not use these procedures on systems or data without authorization.
