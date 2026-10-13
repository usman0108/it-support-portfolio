
# Microsoft 365 Troubleshooting Lab

## Project Overview

This project demonstrates practical IT helpdesk troubleshooting using a Microsoft 365 test environment.

I simulated common user issues, investigated their causes, applied fixes, and documented the results.

## Lab Environment

- Microsoft 365 Admin Center
- Microsoft 365 Business Standard
- Exchange Online / Outlook
- OneDrive for Business
- Test users: Aisha Khan and Daniel Smith

## Scenario 1: Account Sign-in Troubleshooting

**Issue:** A user cannot access their Microsoft 365 account.

**Actions performed:**
1. Blocked Aisha Khan's sign-in through the Admin Center.
2. Unblocked the account.
3. Reset the test user's password.
4. Successfully signed in to verify account access.

**Result:** Account access was restored.

## Scenario 2: Licence Troubleshooting

**Issue:** A user has no Microsoft 365 licence assigned.

**Actions performed:**
1. Removed Aisha's Microsoft 365 Business Standard licence.
2. Confirmed that the account showed zero assigned licences.
3. Reassigned the licence.
4. Verified that the licence was assigned successfully.

**Result:** The user's licence was restored.

## Scenario 3: Outlook Access Troubleshooting

**Issue:** A user cannot access Outlook on the web.

**Actions performed:**
1. Disabled Outlook on the web in the user's email app settings.
2. Attempted to access Outlook using the test account.
3. Observed an Outlook error (440).
4. Re-enabled Outlook on the web.
5. Verified that the Outlook inbox loaded successfully.

**Result:** Outlook web access was restored.

## Scenario 4: OneDrive Sharing Permissions

**Issue:** A colleague can open a shared document but cannot edit it.

**Actions performed:**
1. Created a test Word document in Aisha Khan's OneDrive.
2. Shared it with Daniel Smith using Can view permissions.
3. Signed in as Daniel and confirmed that Word opened in Viewing mode.
4. Changed Daniel's permissions to Can edit.
5. Verified the updated permission in Manage Access.

**Result:** Editing permission was assigned successfully. A final editing test could not be completed because of a OneDrive sign-in error.

## Skills Demonstrated

- Microsoft 365 user administration
- Account access troubleshooting
- Password resets
- Licence management
- Outlook access troubleshooting
- OneDrive sharing and permissions
- Troubleshooting verification
- Technical documentation

## Evidence

Screenshots were captured during the troubleshooting exercises, including:

- Licence removed and restored
- Outlook access disabled
- Outlook error 440
- Outlook inbox restored
- OneDrive view-only access
- OneDrive editing permission assigned

## What I Learned

This lab helped me understand how Microsoft 365 administrators troubleshoot user access, licensing, email application settings, and file-sharing permissions.

It also reinforced the importance of verifying fixes using test accounts and documenting any unresolved issues accurately.
