---
title: Log providers
description: Collect OS logs and permission audit events into Casdoor Entry records.
keywords: [log, provider, permission, audit, syslog, system log, OpenClaw]
authors: [hsluoyz]
---

**Log providers** (Category: **Log**) collect or receive log data and store each record as a Casdoor [Entry](/docs/entry/overview).

There are two kinds:

- **Push-based** — Casdoor writes one entry per authorization event (Casdoor Permission Log).
- **Pull-based** — a background collector reads log records from an external source and stores them as entries (System Log, Agent/OpenClaw).

## Provider types

### Casdoor Permission Log

Records every non-GET API call that passes through Casdoor's authorization filter. Each call produces one entry containing the subject, HTTP method, URL path, and whether access was allowed or denied.

No configuration fields are required. Create a provider of this type and enforcement events start flowing immediately.

**Entry format:**
```
[info]    sub=<owner>/<user> method=<METHOD> url=<path> objOwner=<org> allowed=true
[warning] sub=<owner>/<user> method=<METHOD> url=<path> objOwner=<org> allowed=false
```

### System Log

Reads records from the operating system's native log facility — **journald/syslog** on Linux/Unix and **Windows Event Log** on Windows — and stores each record as an Entry. The collector starts automatically when Casdoor starts and runs in the background.

| Field | Description |
|-------|-------------|
| **Title** | Log tag used to filter records (e.g. `casdoor`). Leave empty to collect all records. |

### Agent (OpenClaw)

Receives OpenTelemetry trace data pushed by an [OpenClaw](https://openclaw.io) agent via the `/api/v1/traces` endpoint. Only requests from the configured IP are accepted; all other senders get a 403.

| Field | Description |
|-------|-------------|
| **Sub type** | `OpenClaw` |
| **Host** | IP address of the OpenClaw agent (e.g. `192.168.1.100`). Leave empty to allow any IP. |

Received traces are stored as `trace`-type entries. See [Entries — OpenTelemetry traces](/docs/entry/overview#opentelemetry-traces) for details on the payload format and viewer.

## Setting up permission logging

1. Go to **Providers** → **Add**.
2. Set **Category** to `Log`, **Type** to `Casdoor Permission Log`.
3. Save. Enforcement events are recorded as entries immediately.
4. View results under **Entries** in the sidebar.
