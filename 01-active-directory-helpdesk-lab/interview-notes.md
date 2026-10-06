# Active Directory Helpdesk Lab — Interview Notes

## What is Active Directory?
Microsoft's directory service used to centrally manage users, computers, groups and access within a Windows domain.

## What is a Domain Controller?
A server running Active Directory Domain Services that authenticates users/computers and stores directory information.

## What is an OU?
A container used to organise Active Directory objects and apply administrative settings or Group Policy.

## Security Group vs OU
A security group is mainly used to assign permissions/access. An OU is mainly used to organise objects and target administration or Group Policy.

## Why does CLIENT01 use the Domain Controller for DNS?
Active Directory relies on DNS to locate domain services. Using unrelated DNS can prevent domain discovery and joining.

## How would you reset a user password?
Verify identity, locate the user in AD Users and Computers, reset the password, require a password change if appropriate, document the ticket, and confirm the user can sign in.

## What would you check if a user cannot log in?
Username/domain, password, lockout, disabled account, network connectivity, DNS, domain controller reachability and recent account/access changes.

## What is Group Policy?
A way to centrally configure Windows users and computers across a domain, including security settings, login messages and restrictions.

## What does `gpupdate /force` do?
Forces Windows to refresh user and computer Group Policy settings.

## What does `nslookup` help with?
Tests DNS resolution.

## What does `ping` tell you?
Tests basic IP connectivity, but does not prove every service is working.

## Example STAR answer — only use after doing the exercise
**Situation:** A domain user could not sign into a workstation during my lab.  
**Task:** Identify whether it was credentials, the account or connectivity.  
**Action:** I checked network connectivity to DC01, then reviewed the user account and found it locked after failed attempts. I unlocked it and retested.  
**Result:** The user could sign in, and I documented the steps for future troubleshooting.
