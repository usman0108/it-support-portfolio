# Network Troubleshooting Lab

**Status:** Completed  
**Environment:** Windows 11 Pro, Windows Server 2022, VirtualBox

## Project Overview

Built a virtual Windows network environment and performed three hands-on troubleshooting scenarios involving DNS resolution, IP connectivity and network adapter failures.

The objective was to practise diagnosing common IT support incidents, identifying configuration problems, restoring connectivity and verifying successful resolutions.

## Lab Environment

| Device | Role | IP Address |
|---|---|---|
| DC01 | Windows Server 2022, Domain Controller and DNS Server | 192.168.50.10 |
| CLIENT01 | Windows 11 Pro workstation | 192.168.50.20 |

**Domain:** `helpdesklab.local`  
**Network:** VirtualBox Internal Network (`ITLabNet`)

## Scenario 1: DNS Resolution Failure

**Problem:** CLIENT01 could not resolve the Active Directory domain.

**Troubleshooting performed:**
- Configured an incorrect DNS server address of `192.168.50.99`.
- Used `ipconfig /all` to inspect the network configuration.
- Used `nslookup helpdesklab.local` to reproduce the DNS timeout.
- Restored the correct DNS server address, `192.168.50.10`.
- Repeated the lookup and confirmed the domain resolved to `192.168.50.10`.

**Evidence:**

![Incorrect DNS configuration](screenshots/01-dns-wrong-server.png)

![DNS lookup failure](screenshots/02-dns-lookup-failed.png)

![DNS lookup restored](screenshots/03-dns-lookup-restored.png)

## Scenario 2: IP Connectivity Troubleshooting

**Problem:** CLIENT01 experienced a simulated network connectivity failure.

**Troubleshooting performed:**
- Reproduced a connectivity failure in the lab.
- Used `ping` to test communication with DC01.
- Checked the workstation's IPv4 configuration.
- Restored the working network configuration.
- Verified connectivity using four successful ICMP replies with 0% packet loss.

**Evidence:**

![Connectivity failure](screenshots/04-ip-connectivity-failed.png)

![Restored IP configuration](screenshots/05-ip-configuration-restored.png)

![Connectivity restored](screenshots/06-ip-connectivity-restored.png)

## Scenario 3: Network Adapter Failure

**Problem:** CLIENT01 lost network connectivity after its Ethernet adapter was disabled.

**Troubleshooting performed:**
- Disabled the Ethernet adapter using Windows Network Connections.
- Ran `ipconfig /all` and observed that the Ethernet configuration was no longer listed.
- Used `ping 192.168.50.10`, which returned a general failure and 100% packet loss.
- Re-enabled the Ethernet adapter.
- Repeated the connectivity test and received four successful replies with 0% packet loss.

**Evidence:**

![Network adapter disabled](screenshots/07-network-adapter-disabled.png)

![Network adapter connectivity restored](screenshots/08-network-adapter-restored.png)

## Tools and Commands Used

| Tool / Command | Purpose |
|---|---|
| `ipconfig /all` | Inspect IP addresses, DNS settings and network adapters |
| `ping` | Test IP connectivity |
| `nslookup` | Troubleshoot DNS name resolution |
| `ipconfig /flushdns` | Clear the local DNS resolver cache |
| `ncpa.cpl` | Manage Windows network adapters |
| VirtualBox | Host the isolated virtual network |

## Skills Demonstrated

- Windows 11 network troubleshooting
- IPv4 and DNS configuration
- Diagnosing connectivity failures
- Network adapter management
- Command-line diagnostics
- Fault isolation and resolution verification
- Documenting technical issues with screenshots

## What I Learned

This project reinforced the importance of structured troubleshooting. I practised checking IP configuration, testing connectivity, distinguishing DNS failures from network connectivity problems and verifying that fixes worked.

The exercises also demonstrated how different faults can produce similar symptoms, making it important to investigate the underlying cause rather than assuming every connection problem is the same.

## CV Project Description

**Network Troubleshooting Lab:** Simulated and resolved DNS, IP connectivity and network adapter issues in a Windows 11 and Windows Server 2022 virtual environment, using ipconfig, ping and nslookup to diagnose faults and verify restored connectivity.
