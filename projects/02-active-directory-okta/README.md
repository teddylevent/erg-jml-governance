# Project 2: Active Directory and Okta Integration

I built the ERG directory in Active Directory and connected it to Okta through the Okta Active Directory Agent. This project puts the identity lifecycle design from Project 1 into practice.

## Watch the demonstrations

- [Part A: Directory setup and integration](https://youtu.be/MM5khwgVLxI)
- [Part B: Joiner, mover, and leaver workflows](https://youtu.be/FH3u3lXZNAU)

## What I configured

- Fictional employee and contractor accounts.
- Department organizational units.
- Security groups for approved access.
- A scoped directory connection through the Okta Active Directory Agent.
- Imported users and groups in Okta.

Active Directory holds the lab accounts and memberships. Okta imports the selected directory objects and uses the resulting groups to support access assignment.

## Scenarios

| Person | Scenario | What I checked |
|---|---|---|
| Morgan Reed | Joiner | Account setup and approved group membership |
| Alex Carter | Finance-to-Sales mover | Removal of old access and assignment of new access |
| Jamie Brooks | Contractor leaver | Account status and removal of access |
| Riley Chen | Temporary elevated access | Temporary group membership and its removal |

The temporary elevated-access exercise is a lab scenario, not a deployment of Microsoft Entra Privileged Identity Management.

## What I learned

An organizational unit organizes directory objects. Security groups deliver access. Moving a user between organizational units does not automatically replace their group memberships.

I also learned to verify the imported state in Okta rather than assuming that a directory change had already arrived.

The Business Portal application used here was a placeholder. Project 3 introduces the working custom SAML portal.

[Back to the portfolio](../../README.md) · [Previous: Governance](../01-identity-governance/) · [Next: SAML single sign-on](../03-saml-single-sign-on/)
