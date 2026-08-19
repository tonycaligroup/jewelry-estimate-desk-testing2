# Scheduling Flow

Use this reference only when a customer expresses meeting intent or an existing
appointment changes.

## Resolve availability

1. Obtain the shop's supported calendar route from `kolo integration-routing`.
2. Resolve relative dates in the owner's IANA timezone from the shop profile.
   The pod clock is UTC and is never the shop's clock.
3. If the profile timezone is blank, use the owner's stored timezone only for
   internal calculations. Confirm it before stating it to a customer.
4. Read live free/busy and intersect it with declared windows, blackouts,
   minimum notice, duration, required attendees, and buffers.
5. Offer 2–3 specific times with date, time, timezone, duration, and place.

A declared window is standing permission at Trust Stage 3; it is not proof of
availability. Live free/busy always wins. If no calendar is configured, leave
`[OWNER: two times you can hold this week]` in a Stage 1 draft or ask the owner
for a general window. Never invent availability.

## Book

Immediately before writing, re-check the chosen slot. Create one event with the
job number, meeting type, duration, location, preparation notes, and safe links.
Confirm to the customer only after the calendar reports a successful write.
Then send the owner a one-line notice.

## Changes

- **Reschedule:** re-check availability and update the existing event. Do not
  create a duplicate.
- **Cancellation:** remove the event, record the reason if supplied, notify the
  owner, and keep the estimate open unless the customer also declines it.
- **No-show:** record it and offer one friendly replacement slot set.
- **Conflict after offer:** apologize without blame, refresh availability, and
  offer 2–3 new times. Never force a stale slot.

Every customer confirmation includes date, time, timezone, duration, place,
and what to bring. “Invite sent” is not “booked.”

