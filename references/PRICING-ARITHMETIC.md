# Pricing Arithmetic

Use this reference only during pricing and quote-validity decisions.

## Deterministic calculation

Use a calculator or deterministic script for all arithmetic. Never ask the
language model to perform the final math mentally.

```text
metal_cost       = finished_grams × metal_rate_per_gram
center_cost      = center_carat × center_rate_per_carat
accent_cost      = accent_total_carat × accent_rate_per_carat
labor_cost       = bench_hours × bench_rate_per_hour
COGS             = metal + center + accents + CAD + casting + labor
                   + setting + finishing + engraving + other approved costs
computed_quote   = COGS × markup_multiplier
```

Round only the final customer quote according to the shop profile. Preserve
unrounded internal values for auditability.

## Source priority

1. Current shop rate card and dated vendor inputs.
2. Comparable jobs from the shop's own history.
3. Explicit owner-provided assumptions.
4. Market defaults, labeled provisional and never represented as shop facts.

Bench labor is always a visible internal line. Customer-supplied specs override
photo interpretation. Never treat a photograph as evidence of origin, grade,
carat, weight, or authenticity.

## Uncertainty and false precision

Bracket a load-bearing unknown instead of fabricating a precise number. Common
drivers are finished metal weight, center-stone origin and grade, accent count,
and hand-assembly time.

For retail, uncertainty never bypasses the spec gate. Price internally using a
low/high scenario, show what moves the number in the owner brief, and send
nothing until the minimum spec is complete and the owner approves one number.

For wholesale, a labeled bracket is allowed when the profile permits it. State
every assumption and never expose vendor identity or internal margin.

## Freshness and validity

Date every rate input. Print a quote-valid-through date. Shorten the validity
window when metal or stones are volatile, especially when metal exceeds 40% of
COGS. Recalculate after expiry or a material specification change.

Production cost, retail price, and replacement value are different numbers.
This workflow may calculate the first two; it never supplies an appraisal or
replacement value.

