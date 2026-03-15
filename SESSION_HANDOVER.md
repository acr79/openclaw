# OpenClaw Session Handover - March 15, 2026

## Repo State

- Repository: `openclaw`
- Branch: `main`
- Local state on March 15, 2026:
  - working tree is not clean
  - local branch is ahead of `origin/main` by 5 commits

## Current Local Config Snapshot

- Repo snapshot config lives in `personal/openclaw.json`.
- Live runtime config lives in `~/.openclaw/openclaw.json`.
- Repo snapshot default agent model:
  - primary: `google/gemini-2.5-flash-lite`
  - fallbacks: `anthropic/claude-haiku-4-5`, `google/gemini-2.5-flash`
- Live runtime default agent model:
  - primary: `google/gemini-2.5-flash-lite`
  - fallbacks: `anthropic/claude-haiku-4-5`, `google/gemini-3-flash-preview`
- Main agent model file currently still includes `gemini-3-flash-preview` in `~/.openclaw/agents/main/agent/models.json`.
- Auto-update remains enabled in config.

## Runtime Notes

- Gateway was verified running via `launchd` on March 15, 2026 under `ai.openclaw.gateway`.
- Cron jobs have changed since the March 9 handover. Do not rely on old job IDs from earlier notes.
- Telegram and other channel connectivity should be treated as runtime state and rechecked when needed.

## Backup CLI

- The built CLI in this checkout already includes `openclaw backup create` and `openclaw backup verify`.
- `node dist/entry.js backup` is no longer just a temporary workaround for this repo checkout.

## Cheap Model Recommendation

- Best default low-cost recommendation: `google/gemini-2.5-flash-lite`
  - current Google docs list it as GA
  - positioned as Google's smallest and most cost-effective Gemini 2.5 model
  - free tier exists with published rate limits
- If you want the absolute cheapest OpenAI option instead: `openai/gpt-4.1-nano`
  - likely cheaper than most non-Google paid options
  - tradeoff is lower capability than Flash-Lite for general assistant work
- Practical recommendation for OpenClaw:
  - use `google/gemini-2.5-flash-lite` as the cheap primary or first fallback
  - keep `anthropic/claude-haiku-4-5` or `google/gemini-2.5-flash` as a higher-quality fallback when needed

## Useful Commands

- Restart gateway: `node dist/entry.js daemon restart`
- Check cron jobs: `openclaw cron list`
- Verify config: `openclaw doctor`
- Backup dry run: `openclaw backup create --dry-run --json`
- Build project: `npm exec pnpm -- run build`

## Workspace Context Files

- `~/.openclaw/workspace/BOOTSTRAP.md`
- `~/.openclaw/workspace/IDENTITY.md`
- `~/.openclaw/workspace/SOUL.md`
