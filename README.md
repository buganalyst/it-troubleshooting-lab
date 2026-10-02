# IT Troubleshooting & Endpoint Recovery Lab

A hands-on technical lab documenting practical IT troubleshooting, endpoint diagnostics, operating-system deployment, system recovery, hardware diagnostics, storage recovery, bootloader repair, and offline troubleshooting using Windows PE and Linux live environments.

The repository is designed for two purposes:

1. **Portfolio evidence:** demonstrate practical IT infrastructure, endpoint support, system administration, recovery, and troubleshooting skills.
2. **Technical reference:** provide structured troubleshooting workflows that another technician, student, or user can follow when diagnosing a Windows/Linux computer.

> Scope: Endpoint and workstation troubleshooting. This repository is being expanded toward server, networking, monitoring, cloud, and security diagnostics.

## Core Philosophy

The objective is not to collect tools. The objective is to develop a repeatable engineering method for isolating faults.

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
DEFINE SCOPE
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
APPLY REMEDIATION
   |
   v
VALIDATE FIX
   |
   v
DOCUMENT / PREVENT
```

A diagnostic result is evidence, not automatically a root cause. Every repair should be validated after remediation.

## Skills Demonstrated

### IT Support and Endpoint Engineering

- Windows installation and deployment
- Linux installation and deployment
- Windows Recovery Environment (WinRE)
- Windows startup and boot troubleshooting
- Windows Boot Manager recovery
- Linux GRUB recovery
- UEFI/BIOS boot troubleshooting
- Partition management
- Partition and filesystem troubleshooting
- Data backup and recovery workflows
- Offline system troubleshooting
- Bootable recovery media
- Hardware diagnostics
- Storage diagnostics
- RAM diagnostics
- Peripheral troubleshooting
- System health verification
- Offline malware/antivirus scanning
- Technical documentation and incident-style troubleshooting

### Diagnostic and Recovery Environments

- Ventoy
- Windows PE / WinPE
- Windows Recovery Environment / WinRE
- Linux Live environments
- MemTest86
- Disk and partition diagnostic/recovery utilities
- Vendor hardware diagnostics

### Engineering Concepts

- Fault isolation
- Root-cause analysis
- Evidence-based troubleshooting
- Recovery planning
- Least-destructive-first remediation
- Backup-before-modification
- Validation after remediation
- Documentation and prevention

## Repository Structure

```text
it-troubleshooting-lab/
|
|-- README.md
|-- LICENSE
|-- DISCLAIMER.md
|-- THIRD-PARTY-NOTICES.md
|
|-- docs/
|   |-- troubleshooting-methodology.md
|   |-- endpoint-diagnostics.md
|   |-- hardware-diagnostics.md
|   |-- storage-and-data-recovery.md
|   |-- windows-recovery.md
|   |-- linux-recovery.md
|   |-- bootloader-recovery.md
|   |-- networking-diagnostics.md
|   |-- toolkit.md
|   |
|   |-- procedures/
|   |   |-- pre-recovery-checklist.md
|   |   |-- windows-no-boot.md
|   |   |-- linux-no-boot.md
|   |   |-- slow-system.md
|   |   |-- no-network.md
|   |
|   |-- checklists/
|       |-- endpoint-intake.md
|       |-- hardware-diagnostics.md
|       |-- recovery-validation.md
|   |
|   |-- images/
|       |-- skills-profile.png
|       |-- endpoint-recovery-lab.png
|       |-- troubleshooting-methodology.png
|
|-- incident-reports/
|   |-- README.md
|   |-- examples/
|       |-- windows-boot-failure.md
|
|-- toolkit/
|   |-- README.md
|   |-- scripts/
|       |-- README.md
```

## Diagnostic Architecture

A professional endpoint investigation can be divided into layers:

```text
+--------------------------------------------------+
|                 USER / SYMPTOM                   |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
| APPLICATION / SERVICES                           |
| Logs, errors, service state, application health  |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
| OPERATING SYSTEM                                 |
| Processes, memory, drivers, filesystems, logs    |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
| NETWORK                                          |
| NIC, IP, DNS, gateway, routes, ports, firewall  |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
| STORAGE                                          |
| SMART/NVMe health, partitions, filesystem       |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
| HARDWARE                                         |
| RAM, CPU, GPU, display, keyboard, power, NIC    |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
| FIRMWARE / BOOT                                  |
| UEFI/BIOS, Secure Boot, boot entries, bootloader|
+--------------------------------------------------+
```

The correct starting layer depends on the symptom.

## Recovery Media Strategy

A bootable USB is useful because it allows diagnostics and recovery independently of the installed operating system.

Typical workflow:

```text
UEFI / BIOS
     |
     v
Boot Menu
     |
     v
Ventoy
     |
     +------------------+
     |                  |
     v                  v
Windows PE          Linux Live
     |                  |
     +---------+--------+
               |
               v
        Diagnostics / Recovery
```

Ventoy is an open-source bootable USB solution that can boot multiple ISO/WIM/IMG/VHD(x)/EFI images from one device. The project documents support for Windows/WinPE and Linux among other environments. See the official Ventoy documentation before creating or modifying recovery media.

## Evidence and Portfolio

The `docs/images/` directory contains screenshots supplied as portfolio evidence/reference material.

### Skills Profile

![IT support and system administration skills](docs/images/skills-profile.png)

### Endpoint Diagnostics and Recovery Lab

![Endpoint diagnostics and recovery lab](docs/images/endpoint-recovery-lab.png)

### Troubleshooting Methodology

![Professional troubleshooting loop](docs/images/troubleshooting-methodology.png)

For future case studies, add screenshots that you personally captured during legitimate testing. Prefer screenshots that show:

- UEFI diagnostics
- Ventoy boot menu
- WinPE environment
- Linux live environment
- MemTest86 results
- SMART/NVMe health
- Disk Management / partition layout
- Windows Recovery Environment
- GRUB recovery
- Network configuration and diagnostic output
- Before/after validation

Do not publish personal data, product keys, recovery keys, passwords, private IP information, serial numbers, or customer information.

## Recommended Case Study Format

Every troubleshooting case should document:

```text
Incident
  |
  +-- Symptom
  +-- Environment
  +-- Initial observations
  +-- Scope
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

This demonstrates engineering reasoning.

## Tool Matrix

| Area | Tools / Environments | Purpose |
|---|---|---|
| Bootable media | Ventoy | Multi-image boot and recovery media |
| Windows recovery | WinRE / WinPE | Offline Windows troubleshooting |
| Linux recovery | Linux Live environment | Offline Linux/filesystem troubleshooting |
| Memory | MemTest86 | Stand-alone RAM diagnostics |
| Storage | SMART / NVMe tools / vendor utilities | Drive health and diagnostics |
| Partitioning | Disk/partition utilities | Partition inspection and recovery workflows |
| Hardware | UEFI/OEM diagnostics | Pre-OS hardware testing |
| Networking | ipconfig, PowerShell, ip, ping, nslookup/dig, tracert/traceroute | Layered network diagnosis |
| Logs | Event Viewer, journalctl | OS/event investigation |
| Windows | PowerShell | System inspection and automation |
| Linux | Bash and standard CLI tools | System inspection and troubleshooting |

## Troubleshooting Guides

- [Troubleshooting methodology](docs/troubleshooting-methodology.md)
- [Endpoint diagnostics](docs/endpoint-diagnostics.md)
- [Hardware diagnostics](docs/hardware-diagnostics.md)
- [Storage and data recovery](docs/storage-and-data-recovery.md)
- [Windows recovery](docs/windows-recovery.md)
- [Linux recovery](docs/linux-recovery.md)
- [Bootloader recovery](docs/bootloader-recovery.md)
- [Networking diagnostics](docs/networking-diagnostics.md)
- [Recovery toolkit](docs/toolkit.md)

### Procedures

- [Pre-recovery checklist](docs/procedures/pre-recovery-checklist.md)
- [Windows no-boot workflow](docs/procedures/windows-no-boot.md)
- [Linux no-boot workflow](docs/procedures/linux-no-boot.md)
- [Slow-system workflow](docs/procedures/slow-system.md)
- [No-network workflow](docs/procedures/no-network.md)

### Checklists

- [Endpoint intake](docs/checklists/endpoint-intake.md)
- [Hardware diagnostics](docs/checklists/hardware-diagnostics.md)
- [Recovery validation](docs/checklists/recovery-validation.md)

## Safety and Data Protection

Recovery operations can cause permanent data loss.

Before modifying partitions, filesystems, boot configuration, or disks:

1. Identify the correct physical disk.
2. Determine whether the data is important.
3. Create a backup or forensic image where appropriate.
4. Avoid writing to a failing source disk unnecessarily.
5. Work from a copy when recovery integrity matters.
6. Record the original partition layout and relevant observations.
7. Validate the recovered data before declaring success.

For enterprise or third-party systems, obtain authorization before performing diagnostics or recovery.

## Official Documentation

- Microsoft Windows Recovery Environment: https://learn.microsoft.com/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference
- Microsoft Windows recovery framework: https://learn.microsoft.com/en-us/windows/configuration/windows-device-recovery-framework
- Microsoft WinRE troubleshooting features: https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/windows-re-troubleshooting-features
- Ventoy documentation: https://www.ventoy.net/en/doc_start.html
- Ventoy source repository: https://github.com/ventoy/Ventoy
- MemTest86: https://www.memtest86.com/
- MemTest86 user guide: https://www.memtest86.com/userguide.html
- Ubuntu bootable USB documentation: https://ubuntu.com/desktop/docs/en/latest/how-to/create-a-bootable-usb-stick/

Always obtain third-party software from its official project/vendor source and verify downloads where checksums/signatures are provided.

## Future Expansion

Planned additions:

- Windows event-log case studies
- PowerShell endpoint diagnostic scripts
- Linux system diagnostic scripts
- Network troubleshooting labs
- TCP/IP fault-isolation exercises
- DNS/DHCP troubleshooting
- Windows Server diagnostics
- Active Directory troubleshooting
- Virtualization diagnostics
- Monitoring and log-analysis examples
- Cloud infrastructure troubleshooting
- Security incident triage
- Endpoint Detection and Response concepts
- IT incident reports and postmortems

## Disclaimer

This repository documents educational and authorized troubleshooting practices. Recovery and diagnostic operations can damage data or systems if performed incorrectly. Always verify the target device and maintain appropriate backups. Do not use these procedures on systems or data without authorization.
