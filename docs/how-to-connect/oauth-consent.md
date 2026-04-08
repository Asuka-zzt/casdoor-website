---
title: OAuth consent page
description: Configure the OAuth consent screen that asks users to approve scope grants.
keywords: [OAuth, consent, scopes, grant, revoke]
authors: [hsluoyz]
---

When a user authorizes a third-party application via Casdoor's OAuth flow, a **consent page** may be shown asking them to approve the requested scopes before the authorization code is issued.

## Consent policy

The `ConsentPolicy` field on the application controls when the consent page appears:

| Policy | Behavior |
|--------|----------|
| `Always` | Show the consent screen on every authorization request. |
| `Once` | Show the consent screen only the first time a user authorizes this application. Subsequent authorizations are approved silently if the requested scopes haven't changed. |
| `Never` | Skip the consent screen entirely. Suitable for first-party applications where user approval is implicit. |

Set the policy on the application edit page under the **OIDC/OAuth** tab.

## User flow

When the policy requires consent and the user has not previously approved the requested scopes, Casdoor redirects the browser to:

```text
/consent/<application-name>?<original-authorization-parameters>
```

The consent page displays the application name, logo, and the list of requested scopes with their display names and descriptions. The user can **Grant** or **Deny** access.

- **Grant** — Casdoor records the grant, then continues the authorization flow and issues the authorization code.
- **Deny** — Casdoor returns an `access_denied` error to the redirect URI.

## Stored grants

Granted scopes are stored on the user object in the `ApplicationScopes` field as a list of consent records. Each record contains the application name and the list of scopes the user approved. This allows Casdoor to skip the consent screen on subsequent requests when the `Once` policy is in effect and the scopes are already granted.

## Consent APIs

You can manage grants programmatically:

### Grant consent

```http
POST /api/grant-consent
Content-Type: application/json

{
  "owner": "<org>",
  "name": "<username>",
  "application": "<application-name>",
  "grantedScopes": ["openid", "email", "profile"]
}
```

### Revoke consent

```http
POST /api/revoke-consent
Content-Type: application/json

{
  "owner": "<org>",
  "name": "<username>",
  "application": "<application-name>"
}
```

Revoking consent removes the stored grant for that application. The next authorization request will trigger the consent screen again (if the policy is `Once` or `Always`).

:::tip

Use `Never` for your own first-party applications and `Once` or `Always` for third-party applications where transparency about scope grants matters to the user.

:::
