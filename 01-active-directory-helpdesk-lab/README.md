# Active Directory Helpdesk Lab

**Status:** In Progress  
**Environment:** Windows Server 2022 + Windows 11 Pro in Oracle VirtualBox  
**Domain:** `helpdesklab.local`

## Project Overview
This lab replicates common 1st Line / Helpdesk Active Directory tasks in a small Windows domain environment. The goal is to build practical experience with user and group administration, password resets, account lockouts, domain joining, DNS configuration, Group Policy and basic Joiner/Mover/Leaver activities.

> Change the status to **Completed** only after you have carried out the practical tasks and captured the evidence listed below.

## Skills Demonstrated
- Active Directory Domain Services
- Windows Server 2022
- User and group administration
- Organisational Units (OUs)
- Password resets and account unlocks
- Security groups
- DNS configuration
- Windows domain joining
- Group Policy
- Joiner / Mover / Leaver concepts
- Helpdesk troubleshooting
- Technical documentation

## Lab Environment
| System | Role | IP Address |
|---|---|---|
| DC01 | Windows Server 2022 Domain Controller / DNS | `192.168.50.10` |
| CLIENT01 | Windows 11 Pro domain workstation | `192.168.50.20` |

VirtualBox network: `ITLabNet` (Internal Network)  
Domain: `helpdesklab.local`

## Practical Tasks
1. Configure `DC01` with static IP `192.168.50.10` and DNS pointing to itself.
2. Install Active Directory Domain Services and promote `DC01` to a Domain Controller.
3. Create a new forest: `helpdesklab.local`.
4. Create OUs: Users, IT, HR, Sales, Workstations, Groups, Disabled Users.
5. Create users: Aisha Khan (`akhan`), Daniel Smith (`dsmith`), Maya Patel (`mpatel`).
6. Create security groups: `GG-HR`, `GG-Sales`, `GG-IT` and add users appropriately.
7. Practise password resets, account disable/enable and account unlock.
8. Configure `CLIENT01` with IP `192.168.50.20`, DNS `192.168.50.10`.
9. Test connectivity with `ping` and DNS with `nslookup`.
10. Join `CLIENT01` to `helpdesklab.local` and move it to the Workstations OU.
11. Create and test a Group Policy called `Workstation Login Message`.
12. Practise a basic Joiner/Mover/Leaver workflow by changing group membership and disabling a leaver account.

## Evidence to Capture
Save screenshots inside `screenshots/` using these names:
- `01-static-ip.png`
- `02-ad-ds-installed.png`
- `03-domain-created.png`
- `04-ou-structure.png`
- `05-users-and-groups.png`
- `06-password-reset.png`
- `07-disabled-user.png`
- `08-client-network-config.png`
- `09-ping-and-nslookup.png`
- `10-domain-join.png`
- `11-client-in-workstations-ou.png`
- `12-group-policy.png`
- `13-account-unlock.png`

Do not upload passwords, VM files, ISO files or sensitive account information.

## Troubleshooting
Document any real issues in `troubleshooting-notes.md`. Good examples include incorrect DNS, failed domain join, user login failure, account lockout and Group Policy not applying.

## What I Learned
Complete this section after finishing the lab. Focus on why domain clients use the DC for DNS, the difference between users/groups/OUs, how Group Policy works, how helpdesk teams handle password resets and account unlocks, and when to escalate.

## CV Bullet — Use Only After Completion
**Active Directory Helpdesk Lab:** Built a Windows Server 2022 Active Directory environment with a domain-joined Windows workstation. Practised user and group administration, password resets, account unlocks, security groups, DNS configuration, domain joining, Group Policy and basic Joiner/Mover/Leaver activities.

## Interview Talking Point — Use Only After Completion
I built a small Windows domain environment using Windows Server 2022 and a Windows client. I configured Active Directory and DNS, created users, groups and OUs, joined a workstation to the domain and practised common support tasks such as password resets, account unlocks, disabling accounts and updating group membership. I also created a basic Group Policy and troubleshot domain connectivity using tools such as ping and nslookup.
