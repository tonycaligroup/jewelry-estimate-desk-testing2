# Model Enforcement

## Required runtime

The skill runs only on Alibaba Qwen 3.7 Plus. Kolo's verified model ID is:

`litellm-fireworks/qwen-3-7-plus`

Kolo does not support a model requirement in `SKILL.md` or
`.clawhub/origin.json`. Enforce the requirement at the agent and routine layers.

## Dedicated agent

Add a dedicated agent entry to `agents.list` in
`~/.openclaw/openclaw.json`:

```json
{
  "id": "jewelry-desk",
  "model": "litellm-fireworks/qwen-3-7-plus",
  "skills": ["jewelry-estimate-desk"]
}
```

Do not configure `agents.list[].model.fallbacks` for this agent. A missing or
unavailable required model must fail closed, not silently switch providers.

Use Kolo's supported configuration interface to apply and validate the entry.
Do not replace the whole configuration file or disturb unrelated agents.

## Preflight

Before reading customer content:

1. Read `session_status`.
2. Require the reported model to equal
   `litellm-fireworks/qwen-3-7-plus`.
3. If it differs, route the work to `jewelry-desk` or set the current session
   model to the required ID once.
4. Verify again. If it still differs, stop and tell the owner the current model,
   required model, and the missing route, configuration, or permission.

Do not offer “continue anyway.” Record the verified model ID in every estimate
audit record.

## Automated runs

Every inbox-monitoring routine uses an isolated session and passes:

```text
--model litellm-fireworks/qwen-3-7-plus
```

Any delegated subagent uses the same exact model ID. Routine creation is not
complete until its stored configuration shows the override.

## Validation

- Dedicated agent reports the required model.
- No model fallback is present.
- Manual work on another agent fails preflight and routes correctly.
- Every inbox routine stores the model override.
- Simulated model unavailability stops before customer content is read.

