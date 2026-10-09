# Windows 11 New Starter Deployment & Workstation Configuration Lab

## Project Status
Completed — Hands-on Configuration

## Overview

This project simulates the onboarding of a new employee in a Windows domain environment.

Using an existing Windows 11 workstation and Windows Server 2022 domain controller, I created a new employee account, configured Active Directory group membership, verified domain authentication, applied Group Policy, configured shared folder permissions and mapped a network drive.

The project demonstrates practical skills used by 1st Line IT Support and Service Desk technicians when preparing workstations for new employees.

## Lab Environment

| Component | Configuration |
|---|---|
| Virtualisation | Oracle VirtualBox |
| Domain Controller | DC01 — Windows Server 2022 |
| Workstation | CLIENT01 — Windows 11 Pro |
| Active Directory Domain | helpdesklab.local |
| Domain Controller IP | 192.168.50.10 |
| Workstation IP | 192.168.50.20 |
| Network | ITLabNet — Internal Network |
| Test Employee | Sophie Turner |
| Username | sturner |
| Department | Sales |

## Technologies Used

- Windows 11 Pro
- Windows Server 2022
- Active Directory Users and Computers
- Active Directory Security Groups
- Group Policy
- Windows File Sharing (SMB)
- NTFS Permissions
- Command Prompt
- Oracle VirtualBox

## Task 1 — New Employee Account Setup

Created a fictional employee account in Active Directory.

**Employee:** Sophie Turner  
**Username:** `sturner`  
**Department:** Sales  
**Organisational Unit:** Employees → Sales

Completed the following:

1. Created and configured the employee's domain account.
2. Set a temporary password.
3. Required a password change at next logon.
4. Added the employee to the `GG-Sales` security group.
5. Verified the account was active.

## Task 2 — Windows 11 Domain Authentication

Signed in to the existing domain-joined Windows 11 workstation using the new employee's credentials.

**Username:** `HELPDESKLAB\sturner`

Verified domain authentication using:

```cmd
whoami
hostname
echo %logonserver%
```

Confirmed:

- Domain username: `helpdesklab\sturner`
- Computer hostname: `CLIENT01`
- Authenticating domain controller: `DC01`

This demonstrated successful domain authentication and creation of the employee's Windows user profile.

## Task 3 — Group Membership and Network Verification

Verified the employee's Active Directory security group membership using:

```cmd
net user sturner /domain
whoami /groups
```

Confirmed membership of `GG-SALES` and `Domain Users`.

Also checked the workstation's network configuration using:

```cmd
ipconfig /all
```

Verified:

- IPv4 address: `192.168.50.20`
- DNS server: `192.168.50.10`
- DNS suffix: `helpdesklab.local`

Applied Group Policy updates using:

```cmd
gpupdate /force
```

Both computer and user policy updates completed successfully.

## Task 4 — Department Shared Folder Configuration

Created a shared Sales folder on the lab domain controller.

**Local folder:** `C:\LabShares\Sales`  
**Network path:** `\\DC01\Sales`

Configured share permissions:

- Removed the default Everyone share permission.
- Added the `GG-Sales` security group.
- Allowed Read and Change permissions.

Configured NTFS permissions:

- Added `GG-Sales`.
- Granted Modify permissions.
- Preserved existing administrative and system permissions.

Tested access from CLIENT01 while signed in as Sophie.

Successfully created `Sales-Test.txt` in the shared folder, confirming the employee could write to the department's shared location.

## Task 5 — Network Drive Mapping

Mapped the Sales department's shared folder as a network drive on CLIENT01.

**Drive letter:** `S:`  
**Network location:** `\\DC01\Sales`

Enabled **Reconnect at sign-in**.

Confirmed that the employee could access the mapped drive and view `Sales-Test.txt`.

Restarted the workstation and verified that the mapped S: drive remained accessible.

## Troubleshooting Experience

During setup, the Sales security group initially did not appear in the employee's current Windows logon session.

I investigated using:

```cmd
whoami /groups
net user sturner /domain
```

The domain account query confirmed that `GG-SALES` was assigned correctly in Active Directory.

I also verified that the group was configured as a Security group.

After restarting and signing in again, `whoami /groups` displayed the expected group membership.

This reinforced the importance of checking both Active Directory membership and the user's current Windows logon session when troubleshooting permissions.

## Evidence

Screenshots captured during the lab demonstrate:

1. Domain authentication and workstation hostname verification.
2. Active Directory group membership.
3. Workstation IP and DNS configuration.
4. Successful Group Policy updates.
5. Access to the Sales shared folder.
6. Successful S: network drive mapping.
7. Continued access to the mapped drive after restarting.

Evidence screenshots are stored in the `screenshots/` directory.

## Lab Scope

CLIENT01 was an existing Windows 11 Pro virtual machine previously joined to the domain. This project focused on new employee onboarding and workstation configuration rather than a fresh Windows installation or automated operating system deployment.

The shared folder was hosted on DC01 for lab purposes. In a production environment, shared business files would typically be hosted on a dedicated file server or managed storage platform.

## Skills Demonstrated

- New starter IT onboarding
- Active Directory account administration
- Security group membership management
- Windows 11 domain authentication
- Windows networking and DNS verification
- Group Policy troubleshooting
- SMB shared folder configuration
- Share and NTFS permission management
- Network drive mapping
- Workstation access verification
- Technical troubleshooting and documentation

## What I Learned

This project strengthened my understanding of how Windows workstations, Active Directory accounts, security groups and shared network resources work together.

I gained practical experience preparing an existing domain-joined workstation for a new employee, verifying their permissions and troubleshooting access issues.

These skills are directly relevant to IT Support Technician, 1st Line Support Analyst and Service Desk Analyst roles.

## CV Project Description

**Windows 11 New Starter Configuration Lab** — Onboarded a simulated employee in an Active Directory environment, configured security group membership, verified Windows 11 domain authentication and Group Policy updates, and implemented department-based shared folder access using SMB and NTFS permissions. Mapped and tested a persistent network drive and documented troubleshooting steps.
