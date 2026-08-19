# Audit Payload

Use one stable external ID for the life of an estimate. Check for an existing
record before writing so polling retries update instead of duplicate.

## Required fields

```json
{
  "customer": {"name": "", "contact": "", "channel": "", "thread_id": ""},
  "inbound": {"message_id": "", "received_at": ""},
  "runtime": {"model_id": "litellm-fireworks/qwen-3-7-plus"},
  "mode": "retail|wholesale",
  "trust_stage": 1,
  "spec": {},
  "spec_complete": false,
  "missing_spec_fields": [],
  "assumptions": [],
  "pricing": {
    "cost_lines": [],
    "cogs": null,
    "markup": null,
    "computed_quote": null,
    "owner_approved_price": null,
    "valid_through": null
  },
  "approval": {"owner_notified_at": null, "medium": null, "approved_at": null},
  "timing": {"event_date": null, "lead_time": null, "feasible": null,
    "time_to_pending_approval_minutes": null},
  "appointment": {"event_id": null, "start": null, "timezone": null,
    "duration_minutes": null, "type": null, "location": null, "mode": null},
  "rendering_paths": [],
  "next_action_at": null,
  "status": "awaiting_specs"
}
```

Use `awaiting_specs`, `pending_approval`, `estimate_sent`,
`appointment_booked`, `approved`, `declined`, or `dormant`. Do not advance a
status until the corresponding external action succeeds.

## Idempotency and privacy

- Deduplicate inbound work by message ID and thread ID.
- Use a stable record external ID and a dated, job-specific action-log key.
- Keep internal cost lines and assumptions out of customer-facing messages.
- Store only operationally necessary customer data.
- Log computed and approved prices separately; the approved price is the only
  number eligible for customer send.

## Failure recording

Record failed notification medium, calendar write, rendering, CRM write, or
model preflight explicitly. Never record requested as approved, approved as
sent, or invite sent as booked.

