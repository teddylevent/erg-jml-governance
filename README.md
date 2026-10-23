# Identity and Access Management Portfolio

Hi, I'm Ted. I work in customer and technical support at a software company, and I am building my skills in Identity and Access Management (IAM).

This portfolio follows five connected projects using a fictional company called Energy Retail Group (ERG). I started by planning how employee access should work. I then built a lab using Active Directory, Okta, PowerShell, and Microsoft Entra ID to put those ideas into practice.

The projects cover account creation, department changes, access reviews, single sign-on, multi-factor authentication, and account offboarding.

The employees and business data are fictional. The technical demonstrations use working lab systems.

## Explore the projects

| Project | Focus | Documentation |
|---|---|---|
| 1 | Identity lifecycle and access governance | [Open Project 1](projects/01-identity-governance/) |
| 2 | Active Directory and Okta integration | [Open Project 2](projects/02-active-directory-okta/) |
| 3 | SAML single sign-on with Okta | [Open Project 3](projects/03-saml-single-sign-on/) |
| 4 | Access reviews with PowerShell | [Open Project 4](projects/04-access-reviews/) |
| 5 | PowerShell identity lifecycle with Microsoft Entra ID | [Open Project 5](projects/05-entra-identity-lifecycle/) |

## What I wanted to demonstrate

My goal was to answer three questions:

- How does a new employee receive the access they need?
- How does that access change when the employee changes jobs?
- How do we remove access when the employee leaves?

I also wanted to show how to check the results. A successful command is only part of the work. I need to confirm the account status, group membership, application assignment, and what the user can actually open.

## Lab environment

I used the following tools across the projects:

- Windows Server and Active Directory for users, organizational units, and security groups.
- Okta and the Okta Active Directory Agent for directory integration and single sign-on.
- Microsoft Entra ID and Cloud Sync for the final hybrid identity project.
- PowerShell for account changes and access review reports.
- SAML 2.0 to connect the ERG Business Portal to an identity provider.
- Conditional Access and Microsoft Authenticator to demonstrate MFA.
- Excel and diagrams to document access rules, responsibilities, and test cases.

I initially planned to use Microsoft Entra ID throughout the series, but I had difficulty activating the trial. I used Okta for the earlier technical projects. After resolving the trial issue, I completed the final project with Microsoft Entra ID.

## Project 1: Identity Lifecycle and Access Governance

Before building the technical environment, I planned how ERG should manage access.

I documented the joiner, mover, and leaver process:

- Joiner: a new employee receives approved access.
- Mover: an employee changes roles and receives access for the new job.
- Leaver: an employee leaves and their access is removed.

I created an access catalogue showing which groups support each business role. I also documented who requests, approves, implements, and reviews access.

The supporting documents include a workflow diagram, responsibility matrix, controls matrix, and test cases.

This project demonstrates process design. Its approvals and test results are simulated.

[Watch Project 1](https://youtu.be/CXaLiN_0gcA) · [View documents and evidence](projects/01-identity-governance/)

## Project 2: Active Directory and Okta Integration

I built the ERG directory in Active Directory and connected it to Okta through the Okta Active Directory Agent.

I created fictional users, department organizational units, and security groups. I then imported the selected users and groups into Okta.

Using this environment, I demonstrated:

- Onboarding Morgan Reed.
- Moving Alex Carter from Finance to Sales.
- Offboarding Jamie Brooks.
- A temporary elevated-access scenario for Riley Chen.

I checked the resulting account and group changes and reviewed the available Okta audit information.

This project helped me understand how changes in the source directory affect the connected identity platform.

[Watch Project 2A: Directory Setup and Integration](https://youtu.be/MM5khwgVLxI)

[Watch Project 2B: Joiner, Mover, and Leaver Workflows](https://youtu.be/FH3u3lXZNAU)

[View Project 2](projects/02-active-directory-okta/)

## Project 3: SAML Single Sign-On with Okta

I connected the ERG Business Portal to Okta using SAML single sign-on.

The portal is a custom lab application with separate business workspaces. It gave me an application where I could test sign-in and department access.

I configured the SAML trust settings, signing certificate, user attributes, and group information. I then tested access through the portal.

This project demonstrates two separate controls:

- Authentication checks who the user is.
- Authorization checks what the user is allowed to access.

Okta authenticates the user. The portal validates the SAML response and uses the supplied group information to determine access.

This integration uses SAML for sign-in and group-based authorization. It does not implement SCIM account provisioning.

[Watch Project 3](https://youtu.be/4mITBHTkiUY) · [View Project 3](projects/03-saml-single-sign-on/)

## Project 4: Access Reviews with PowerShell

I used PowerShell to review fictional account and access data stored in CSV files.

The review compared worker information, current access, and an approved role baseline.

The checks looked for:

- Accounts still enabled after a worker's end date.
- Access retained after a worker leaves.
- Access from a previous department.
- Privileged access with missing or expired approval.
- Access outside the person's approved role.

The script produced findings for review. I recorded simulated decisions and checked a corrected sample dataset.

The script reports exceptions; it does not automatically remove access. The demonstration uses prepared sample data and does not change live Active Directory or Okta accounts.

[Watch Project 4](https://youtu.be/FPPE3XCKlGU) · [View Project 4](projects/04-access-reviews/)

## Project 5: PowerShell Identity Lifecycle with Microsoft Entra ID

For the final project, I connected the Active Directory lab to Microsoft Entra ID using Cloud Sync. I also connected the ERG Business Portal to Entra using SAML.

I followed one fictional employee, Taylor Quinn, through the full lifecycle.

### Joiner

I created Taylor in Active Directory, updated his profile, and assigned the approved Finance and employee groups.

After enabling the account and verifying synchronization, I tested his portal sign-in. Taylor could open the Finance workspace, while unrelated workspaces were restricted.

### Conditional Access and MFA

I evaluated MFA and legacy-authentication policies in report-only mode before enabling them.

I then tested MFA and reviewed the sign-in logs to check the policy result.

The browser sign-in demonstrated MFA enforcement. It was not a test of a legacy-authentication client.

### Mover

I moved Taylor from Finance to Sales.

I removed the old Finance group membership and added the approved Sales group. I also updated his department, job title, manager, and organizational unit in Active Directory.

After the changes synchronized, I signed in again and verified that the portal displayed Sales and allowed the correct workspace access.

### Leaver

I disabled Taylor's Active Directory account, completed the cloud block and session-revocation actions, and removed his access groups.

I checked the account state, group memberships, application assignment, and a fresh sign-in attempt.

PowerShell handled the directory changes, while Cloud Sync carried supported changes to Entra. Some cloud administration and verification steps were performed manually.

The final test demonstrated that a fresh sign-in was rejected. It did not demonstrate immediate termination of an already-open portal session.

[Watch Project 5](https://youtu.be/NklKCgPlbjU) · [View Project 5](projects/05-entra-identity-lifecycle/)

## What I learned

These projects helped me understand that:

- An organizational unit and a security group serve different purposes.
- Department information does not automatically grant application access.
- A role change requires both profile updates and access changes.
- Directory synchronization and application sessions are separate processes.
- Report-only policies evaluate access without enforcing the configured controls.
- Offboarding requires verification across the directory, identity platform, and application.

I also learned to investigate problems using account properties, group memberships, synchronization information, and sign-in logs.

## About this lab

ERG is a fictional company created for this portfolio. The projects use fictional employees and sample business records.

The governance exercises and sample-data reviews are identified separately from the working technical demonstrations.

## Contact

[LinkedIn](https://www.linkedin.com/in/tedweks/) · [GitHub](https://github.com/teddylevent)
