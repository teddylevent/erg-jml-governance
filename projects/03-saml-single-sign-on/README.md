# Project 3: SAML Single Sign-On with Okta

> Video links open the original 1080p MP4 files. GitHub may download the file; open it to watch in full quality, without automatic resolution changes.

I connected the working ERG Business Portal to Okta so that users could sign in through a trusted identity provider and receive access based on their groups.

[Watch the demonstration — 1080p MP4](https://github.com/teddylevent/erg-jml-governance/releases/download/portfolio-hd-v1/ERG-Project-3-Final.mp4)

## How the sign-in works

1. The user opens the portal and starts sign-in.
2. The portal sends a SAML authentication request to Okta.
3. Okta authenticates the user.
4. Okta returns a signed SAML response to the portal's reply endpoint.
5. The portal validates the response and maps the supplied groups to application permissions.

Okta is the identity provider. The portal is the service provider.

## What I configured

- The application's identifier, also called its Entity ID.
- The reply URL, also called the Assertion Consumer Service endpoint.
- The sign-on URL.
- The signing certificate and trust settings.
- User attributes and group claims.
- Approved group assignments to the application.

The walkthrough includes Morgan Reed's HR portal sign-in.

## What the access controls mean

Authentication confirms the user's identity. Authorization determines which portal workspaces that user can open.

The portal uses group information from the signed response to determine permissions. Its protected routes enforce access on the server.

A successful sign-in does not give the user access to every department.

## Scope

This is a local application using fictional business records. This project demonstrates SAML single sign-on and group-based authorization.

It does not implement SCIM provisioning. Group changes must reach the identity provider, and a new sign-in is needed to refresh the portal's session information.

[Back to the portfolio](../../README.md) · [Previous: Active Directory and Okta](../02-active-directory-okta/) · [Next: Access reviews](../04-access-reviews/)
