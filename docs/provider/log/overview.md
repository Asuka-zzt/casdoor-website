---
title: Log providers
description: Forward permission audit events to external logging backends or Casdoor Entry records.
keywords: [log, provider, permission, audit, syslog]
authors: [hsluoyz]
---

**Log providers** (Category: **Log**) forward permission enforcement events to an external logging backend. Each non-GET API call that passes through Casdoor's authorization filter generates one log entry recording the subject, HTTP method, URL path, and whether access was allowed or denied.

Log providers are applied at the organization level. All Log providers configured for an organization receive every enforcement event for that org.

## Provider types

### Casdoor Permission Log

Stores enforcement events directly in Casdoor as [Entry](/docs/entry/overview) records. No external service is required.

| Field | Value |
|-------|-------|
| **Category** | Log |
| **Type** | Casdoor Permission Log |

Each enforcement event produces one entry with:
- **Type**: `permission`
- **Message**: `[info] sub=<owner>/<user> method=<METHOD> url=<path> objOwner=<org> allowed=true` (or `[warning]` when denied)

This is the simplest setup — just create a provider of this type and no additional configuration is needed.

### Linux Syslog

Sends log lines to a local or remote syslog daemon.

:::note
Linux Syslog support is not yet implemented. This type is reserved for a future release.
:::

## Configuration

| Field | Description |
|-------|-------------|
| **Host** | Syslog server host or IP (e.g. `127.0.0.1`) |
| **Port** | Syslog server port |
| **Title** | Log tag / app name included in each syslog line (e.g. `casdoor`) |

For **Casdoor Permission Log**, these fields are not used.

## Log format

Each log line follows this format:

```
[<severity>] sub=<owner>/<username> method=<HTTP_METHOD> url=<path> objOwner=<org> allowed=<true|false>
```

`severity` is `info` for allowed requests and `warning` for denied requests.

## Setting up permission logging

1. Go to **Providers** → **Add**.
2. Set **Category** to `Log` and **Type** to `Casdoor Permission Log`.
3. Save the provider. Enforcement events for that organization are now recorded automatically as entries.
4. View the results under **Entries** in the sidebar.
