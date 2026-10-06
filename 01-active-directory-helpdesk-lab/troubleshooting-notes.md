# Troubleshooting Notes

Use this file to record real issues you encounter during the lab.

## Scenario 1 — CLIENT01 Cannot Join the Domain
**Checks:**
1. Confirm CLIENT01 has the correct IP.
2. Confirm DNS points to `192.168.50.10`.
3. Run `ping 192.168.50.10`.
4. Run `nslookup helpdesklab.local`.
5. Confirm AD DS and DNS are running on DC01.

**Common cause:** CLIENT01 is using the wrong DNS server.  
**Resolution:** Set DNS to `192.168.50.10`, run `ipconfig /flushdns`, and retry the join.

## Scenario 2 — User Cannot Sign In
Check username/domain, password, disabled/locked status, network connectivity, DNS and whether the workstation can contact the Domain Controller.

## Scenario 3 — Group Policy Does Not Apply
Run `gpupdate /force` and `gpresult /r`. Check the computer is in the correct OU and the GPO is linked and enabled.

## My Real Troubleshooting Notes
**Issue:**  
**Symptoms:**  
**What I checked:**  
**Root cause:**  
**Resolution:**  
**What I learned:**  
