# Project 5: PowerShell Identity Lifecycle with Microsoft Entra ID

I used PowerShell, Active Directory, Microsoft Entra Cloud Sync, and the ERG Business Portal to follow Taylor Quinn through joining the company, moving departments, and leaving.

[Watch the demonstration](https://youtu.be/NklKCgPlbjU)

## Environment

- Active Directory stores the lab user and security groups.
- Cloud Sync synchronizes supported directory changes to Microsoft Entra ID.
- Microsoft Entra ID authenticates the user and supplies signed SAML information.
- The ERG Business Portal maps the supplied groups to workspace permissions.

## Joiner: Finance

I created Taylor's Active Directory account, updated his profile, and assigned the approved Finance and employee groups.

After enabling the account, I checked the synchronized user, group membership, and application access in Entra. I then tested the portal: Finance was available and unrelated workspaces were restricted.

## Conditional Access and MFA

I evaluated the MFA and legacy-authentication policies in report-only mode before enabling them.

The report-only results showed how the policies would apply. I verified administrator MFA, completed the transition from Security Defaults, and tested the enforced MFA policy.

The sign-in logs showed MFA success. The browser test did not test a legacy-authentication client.

## Mover: Finance to Sales

I removed Taylor's Finance access and assigned the approved Sales group. I also updated his:

- Department.
- Job title.
- Manager.
- Organizational unit.

After synchronization, I verified the cloud memberships and application assignment. A fresh portal sign-in showed the Sales department and the correct workspace permissions.

Updating a department or moving an account to an organizational unit does not itself replace the user's access groups.

## Leaver: Disable and verify

I disabled Taylor's Active Directory account, completed the cloud block and session-revocation actions, and removed the Sales and employee access groups.

I then checked:

- The disabled account state.
- Removal of the synchronized access groups.
- Removal of the application assignment.
- Rejection of a fresh sign-in attempt.

The final sign-in screen reported that the account was locked. The disabled account state and removed assignments were verified separately.

## What was automated

I ran individual PowerShell commands to make the directory changes. Cloud Sync carried supported changes to Entra.

Cloud administration and verification also included manual steps. This demonstrates PowerShell-driven lifecycle administration, not a fully unattended workflow.

## Session behavior

A portal session is separate from the Entra sign-in session. Revoking Entra sessions does not immediately destroy an existing session cookie issued by the portal.

The final test demonstrates a rejected fresh sign-in. The portal also has a five-minute inactivity timeout.

[Back to the portfolio](../../README.md) · [Previous: Access reviews](../04-access-reviews/)
