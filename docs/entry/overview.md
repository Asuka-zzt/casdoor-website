---
title: Entries
description: Manage telemetry entry endpoints in Casdoor for receiving observability data.
keywords: [entry, telemetry, OpenTelemetry, observability]
authors: [hsluoyz]
---

**Entries** are telemetry endpoint records in Casdoor. They represent external services or pipelines that send observability data (logs, traces, metrics) to Casdoor for storage and forwarding.

## Entry properties

| Field | Description |
|-------|-------------|
| **Name** | Unique identifier for the entry within the organization |
| **Display name** | Human-readable label |
| **URL** | The upstream endpoint URL |
| **Token** | Bearer token for authenticating requests to the upstream service |
| **Application** | The Casdoor application this entry is associated with |

## OpenTelemetry traces

Casdoor exposes `/api/v1/traces` to receive OpenTelemetry trace data in OTLP (OpenTelemetry Protocol) format over HTTP. Payloads must be serialized as protobuf with `Content-Type: application/x-protobuf`. Received traces are stored as entry records and can be forwarded to an upstream collector.

## Managing entries

Navigate to **Entries** in the Casdoor sidebar to view, create, and manage entry records. Each entry is scoped to an organization.
