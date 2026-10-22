# Project 4: Access Reviews with PowerShell

I used PowerShell to compare fictional worker records, current access, and an approved role baseline. The goal was to identify access that needed a human review.

[Watch the demonstration](https://youtu.be/FPPE3XCKlGU)

## Review inputs

- Worker records: employment status, department, and relevant dates.
- Entitlements: the access assigned to each person.
- Role baseline: the access normally approved for that person's role.

These inputs are prepared CSV files. The review uses a separate sample snapshot rather than a live export from the Okta tenant.

## Checks

| Check | Why it matters |
|---|---|
| An account is enabled after the worker's end date | The account may still allow sign-in |
| Access remains after the worker leaves | Permissions may not have been removed |
| Previous-department access remains after a move | The user may have accumulated unnecessary access |
| Privileged access has missing or expired approval | Elevated access needs valid ownership and approval |
| Access falls outside the role baseline | An owner needs to review the exception |

A finding is an exception requiring review. It is not automatically proof of misuse.

## Review process

1. Run the PowerShell review against the sample data.
2. Inspect the findings.
3. Record simulated decisions to remove, retain, or investigate access.
4. Review a corrected sample dataset.
5. Compare the before-and-after results.

The script identifies exceptions and produces reports. It does not grant access, remove access, or disable accounts.

## What I learned

A review needs reliable source data and an approved baseline. A script can identify differences, but a manager or application owner still needs to decide whether the access is appropriate.

The corrected dataset simulates approved remediation. This demonstration does not change live Active Directory or Okta accounts.

[Back to the portfolio](../../README.md) · [Previous: SAML single sign-on](../03-saml-single-sign-on/) · [Next: Microsoft Entra identity lifecycle](../05-entra-identity-lifecycle/)
