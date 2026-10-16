# Project 8 – Windows Event Viewer & Troubleshooting Lab

## Project Overview

This project demonstrates practical Windows 11 troubleshooting using Event Viewer, PowerShell, Windows system repair tools and network diagnostics.

The lab involved investigating a DistributedCOM error and diagnosing a Windows Update connectivity failure on a domain-joined Windows 11 virtual machine.

## Lab Environment

| Component | Configuration |
|---|---|
| Virtualisation | Oracle VirtualBox |
| Domain Controller | Windows Server 2022 – DC01 |
| Client | Windows 11 Pro – CLIENT01 |
| Domain | helpdesklab.local |
| Client IP | 192.168.50.20 |
| Domain Controller IP | 192.168.50.10 |
| Network | Internal Network (ITLabNet) + NAT |

## Issue 1 – Event Viewer Investigation

**Problem:** A DistributedCOM error (Event ID 10010) appeared in Windows Event Viewer.

### Investigation

1. Opened Event Viewer and examined the Windows System log.
2. Filtered the log to identify errors.
3. Investigated Event ID 10010, which referenced `MicrosoftWindows.Client.WebExperience`.
4. Attempted to launch Windows Widgets using `Win + W`.
5. Confirmed that the Widgets panel did not open.
6. Checked the Windows Web Experience package using PowerShell.
7. Reset the application package and performed Windows system integrity checks.

### Troubleshooting Commands

```powershell
Get-AppxPackage *WebExperience*
```

```powershell
Get-AppxPackage *WebExperience* | Reset-AppxPackage
```

```powershell
sfc /scannow
```

```powershell
DISM.exe /Online /Cleanup-Image /RestoreHealth
```

### Findings

- The Windows Web Experience package was installed.
- System File Checker reported no integrity violations.
- DISM completed successfully.
- Widgets continued to fail to launch.

**Status:** Further investigation required. The DistributedCOM event was identified, but its relationship to the Widgets failure was not conclusively established.

## Issue 2 – Windows Update Connectivity Failure

**Problem:** Windows Update displayed an error and could not successfully check for updates.

### Investigation

The Windows 11 client was initially configured with a single VirtualBox Internal Network adapter.

Network diagnostics showed:

- Static client IP: `192.168.50.20`
- DNS server: `192.168.50.10`
- No default gateway
- Failed connectivity test to `8.8.8.8`

### Root Cause

The virtual machine had no route to the internet because it was connected only to the isolated VirtualBox Internal Network.

### Resolution

1. Shut down CLIENT01.
2. Opened VirtualBox network settings.
3. Preserved Adapter 1 as Internal Network (`ITLabNet`).
4. Enabled Adapter 2 and configured it as NAT.
5. Restarted CLIENT01.
6. Repeated the connectivity tests.
7. Opened Windows Update and checked for updates.

### Verification

Following the network configuration change:

- Ping to `8.8.8.8` succeeded with 0% packet loss.
- Windows Update successfully detected available updates.
- Windows updates were downloaded and installed.
- Microsoft Store successfully downloaded application updates.

**Status: Resolved.**

## Skills Demonstrated

- Windows Event Viewer analysis
- Event ID investigation
- PowerShell troubleshooting
- SFC and DISM system integrity checks
- TCP/IP connectivity testing
- VirtualBox network configuration
- Diagnosing Windows Update connectivity failures
- Root cause analysis
- Technical troubleshooting documentation

## Conclusion

This lab provided experience investigating Windows application errors and resolving a network connectivity issue affecting Windows Update.

The confirmed resolution was restoring internet connectivity to a domain-joined Windows 11 virtual machine using a second NAT network adapter, while retaining the existing internal lab network.

The Widgets issue remains documented for further investigation, demonstrating the importance of distinguishing verified fixes from unresolved symptoms.
## Screenshots

### Event Viewer – Event ID 10010
![Event Viewer error](01-event-viewer-error.png)

### Network Connectivity Restored
![Successful ping test](02-connectivity-restored.png)

### System Integrity Checks
![SFC and DISM troubleshooting](03-system-repair-checks.png)
