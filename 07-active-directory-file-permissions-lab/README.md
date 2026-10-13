# Project 7 – Active Directory File Share Permissions Lab

## Overview

This project demonstrates how I configured and troubleshot shared folder permissions in a Windows Server Active Directory environment.

The aim was to ensure employees could access their department's shared files while preventing unauthorised access to other departments.

I used Active Directory security groups, NTFS permissions and Windows file sharing to implement and test department-based access control.

## Lab Environment

| Component | Configuration |
|---|---|
| Domain Controller | DC01 – Windows Server 2022 |
| Client Computer | CLIENT01 – Windows 11 Pro |
| Domain | helpdesklab.local |
| Server IP Address | 192.168.50.10 |
| Client IP Address | 192.168.50.20 |
| Virtualisation | Oracle VirtualBox |
| Security Groups | GG-HR, GG-SALES |

## Objectives

- Configure shared folders for HR and Sales departments.
- Apply Active Directory group-based permissions.
- Configure NTFS and network sharing permissions.
- Allow authorised users to access and modify department files.
- Prevent users from accessing other departments' folders.
- Troubleshoot network share connectivity issues.
- Verify permissions using real domain user accounts.

## 1. Active Directory Group Membership

I used Active Directory Users and Computers to manage departmental security group membership.

The following test accounts were used:

| User | Username | Department | Security Group |
|---|---|---|---|
| Aisha Khan | akhan | HR | GG-HR |
| Sarah Johnson | sjohnson | Sales | GG-SALES |

Group membership was also checked from the Windows client using:

```cmd
whoami /groups
```

This helped verify that the appropriate security group was present in each user's logon session.

## 2. Shared Folder Configuration

The shared folders were located on DC01:

```text
C:\LabShares\HR
C:\LabShares\Sales
```

They were made available over the network using the following UNC paths:

```text
\\dc01.helpdesklab.local\HR
\\dc01.helpdesklab.local\Sales
```

I used the following command on DC01 to verify the network shares:

```cmd
net share
```

The output confirmed that both HR and Sales were shared from the server.

## 3. HR Folder Permissions

I configured the HR folder's NTFS permissions through:

**Properties → Security → Advanced**

I disabled permission inheritance and converted the existing inherited permissions into explicit permissions.

I then removed general Users group permissions and configured the following access:

| Security Principal | Permission |
|---|---|
| GG-HR | Modify |
| Administrators | Full Control |
| SYSTEM | Full Control |

The GG-HR permission applied to the folder, subfolders and files.

I also configured network sharing for the HR folder, granting GG-HR the appropriate access.

This configuration was intended to ensure that only authorised HR users and administrators could access HR documents.

## 4. HR User Access Test

I signed into CLIENT01 as Aisha Khan (`akhan`).

I accessed the HR share using:

```text
\\dc01.helpdesklab.local\HR
```

The folder opened successfully.

I then created a test text document inside the HR folder.

**Result: PASS**

The authorised HR user could access the shared folder and create files.

## 5. Sales User Access Test

I signed into CLIENT01 as Sarah Johnson (`sjohnson`), a member of GG-SALES.

I accessed:

```text
\\dc01.helpdesklab.local\Sales
```

The Sales folder opened successfully.

I created a test text document to verify write access.

**Result: PASS**

The authorised Sales user could access and create files in the Sales share.

## 6. Unauthorised Access Tests

I tested whether users could access folders belonging to other departments.

### Test A – Sales User Accessing HR

While logged in as Sarah Johnson, I attempted to access:

```text
\\dc01.helpdesklab.local\HR
```

Windows displayed a permissions error indicating that the user did not have permission to access the folder.

**Result: PASS – Access denied as expected.**

### Test B – HR User Accessing Sales

While logged in as Aisha Khan, I attempted to access:

```text
\\dc01.helpdesklab.local\Sales
```

Windows displayed an access-denied error.

**Result: PASS – Access denied as expected.**

These tests demonstrated that department-based access restrictions were functioning as intended.

## 7. Network Share Troubleshooting

During testing, I encountered the following error:

```text
Error code: 0x80070043
The network name cannot be found.
```

This occurred when attempting to access:

```text
\\DC01\HR
```

### Troubleshooting Steps

**Step 1 – Verify the Share**

On DC01, I ran:

```cmd
net share
```

This confirmed that the HR share existed and pointed to the correct folder.

**Step 2 – Test Direct IP Access**

On CLIENT01, I entered:

```text
\\192.168.50.10\HR
```

The folder opened successfully.

This confirmed that the share was accessible using the server's IP address.

**Step 3 – Check DNS Resolution**

I ran:

```cmd
nslookup DC01
```

The command initially reported a DNS timeout but ultimately resolved:

```text
dc01.helpdesklab.local
192.168.50.10
```

**Step 4 – Test the Fully Qualified Domain Name**

I entered:

```text
\\dc01.helpdesklab.local\HR
```

The folder opened successfully.

### Troubleshooting Outcome

The share was accessible using both the server IP address and fully qualified domain name.

The short hostname access issue was not fully resolved, but testing established a working alternative and confirmed that the folder permissions were functioning correctly.

## 8. Test Results

| Test | Expected Result | Actual Result | Status |
|---|---|---|---|
| HR user opens HR folder | Allowed | Allowed | PASS |
| HR user creates file in HR | Allowed | Allowed | PASS |
| Sales user opens Sales folder | Allowed | Allowed | PASS |
| Sales user creates file in Sales | Allowed | Allowed | PASS |
| Sales user opens HR folder | Denied | Denied | PASS |
| HR user opens Sales folder | Denied | Denied | PASS |
| HR share accessed by IP | Accessible | Accessible | PASS |
| HR share accessed by FQDN | Accessible | Accessible | PASS |

## 9. Screenshot Evidence

Screenshots captured during the lab include:

- Active Directory group membership verification.
- HR folder NTFS permissions.
- Network share troubleshooting.
- Successful access to the HR share.
- Successful file creation in the Sales share.
- Sales user denied access to HR.
- HR user denied access to Sales.

Screenshots are stored in the `screenshots` folder.

## 10. Skills Demonstrated

- Windows Server 2022 administration
- Active Directory Users and Computers
- Security group management
- NTFS file permissions
- SMB network file sharing
- Access control and least privilege
- Windows 11 client troubleshooting
- DNS troubleshooting
- Command Prompt diagnostics
- User access verification
- Technical documentation

## 11. What I Learned

This lab helped me understand how Windows file permissions work in a domain environment.

I gained practical experience configuring shared folders, assigning permissions to security groups and testing access with different user accounts.

I also learned how to distinguish between network connectivity problems and permission-related errors.

The troubleshooting process reinforced the importance of verifying each part of a problem rather than assuming the cause.

## CV Description

**Active Directory File Share Permissions Lab:** Configured and tested departmental SMB file shares using Windows Server 2022, Active Directory security groups and NTFS permissions. Verified authorised read/write access, restricted cross-department access and troubleshot network share connectivity issues.
