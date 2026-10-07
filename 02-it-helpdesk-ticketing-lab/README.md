# IT Helpdesk & Ticketing Lab

## Status
Completed

## Overview
Built a practical IT helpdesk ticketing lab using Jira Service Management alongside a Windows Active Directory environment.

The project simulated real first-line IT support incidents from initial ticket creation through troubleshooting, resolution, verification, documentation, and ticket closure.

## Environment

- Jira Service Management
- Windows Server 2022
- Active Directory Domain Services
- Windows 11 Pro client
- Domain: `helpdesklab.local`
- Domain Controller: `DC01`
- Client: `CLIENT01`

## Skills Demonstrated

- IT ticket lifecycle management
- Incident troubleshooting
- Active Directory user administration
- Password resets
- Disabled account troubleshooting
- DNS troubleshooting
- Windows networking
- `ping`, `nslookup`, and `ipconfig`
- Ticket prioritisation and assignment
- Internal support documentation
- Resolution verification

## Tickets Completed

### Ticket 1 - Password Reset

**Issue:** User was unable to access their domain account and required a password reset.

**Actions taken:**
- Verified the affected user in Active Directory.
- Reset the user's password.
- Required the user to change their password at next logon.
- Tested authentication on CLIENT01.
- Confirmed the user successfully changed their password and regained access.
- Documented the resolution and closed the ticket.

### Ticket 2 - Disabled User Account

**Issue:** User was unable to log in to their domain account.

**Troubleshooting:**
- Reproduced the login failure on CLIENT01.
- Investigated the user account in Active Directory.
- Identified that the account was disabled.

**Resolution:**
- Re-enabled the user account.
- Tested authentication from CLIENT01.
- Confirmed successful login.
- Documented and resolved the ticket.

### Ticket 3 - DNS / Domain Resource Issue

**Issue:** User was unable to access domain resources from CLIENT01.

**Troubleshooting:**
- Used `ping` to verify connectivity to DC01 at `192.168.50.10`.
- Confirmed IP connectivity was working.
- Used `nslookup` and identified that DNS resolution was failing.
- Used `ipconfig /all` to inspect the client's network configuration.
- Identified an incorrect DNS server address of `192.168.50.99`.

**Resolution:**
- Corrected the preferred DNS server to `192.168.50.10`.
- Re-tested DNS resolution using `nslookup`.
- Confirmed `helpdesklab.local` successfully resolved to `192.168.50.10`.
- Documented the troubleshooting process and resolved the ticket.

## Helpdesk Workflow

For each incident I followed a structured support process:

**Log → Prioritise → Assign → Troubleshoot → Identify Root Cause → Resolve → Verify → Document → Close**

## What I Learned

This project gave me practical experience managing IT support tickets and documenting technical work clearly. I also developed a more structured troubleshooting approach by testing connectivity and configuration before making changes.

The DNS incident demonstrated the importance of separating basic network connectivity from name-resolution problems, while the Active Directory incidents provided hands-on experience supporting user authentication issues.

## CV Project Description

**IT Helpdesk & Ticketing Lab** - Built a practical helpdesk environment using Jira Service Management, Windows Server 2022, Active Directory and Windows 11. Managed support tickets involving password resets, disabled accounts and DNS connectivity issues. Diagnosed incidents using Active Directory tools and Windows networking commands, implemented fixes, verified service restoration and documented resolutions through the full ticket lifecycle.
