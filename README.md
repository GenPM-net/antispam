# @core/antispam

[![genpm](https://api.genpm.net/v1/badge/@core/antispam.svg)](https://genpm.net/p/@core/antispam) ![license](https://img.shields.io/badge/license-MIT-blue)

> Spam protection for public forms: honeypot, signed timing, Turnstile or hCaptcha and Postgres rate limits

A [GenPM](https://genpm.net) module: **source code + AI rules + MCP config**, injected into your project instead of hidden in `node_modules`. The code lands in `src/lib/antispam`, pinned to a verified commit, and you own it.

## Install

```bash
genpm add @core/antispam
```

No genpm yet? `curl -fsSL https://genpm.net/install.sh | sh` (macOS/Linux), `irm https://genpm.net/install.ps1 | iex` (Windows), or one-off with `npx @genpm-net/cli add @core/antispam`.

Or let your AI agent do it: run `genpm mcp setup` once, then ask *"add @core/antispam with genpm"* in Claude Code, Cursor, VS Code, Windsurf, Codex or Gemini CLI. It shows you a dry-run plan before writing anything.

## What it does

Protects public endpoints that write (forms, comments, newsletter, login): honeypot field, signed minimum-time token,
captcha (Cloudflare Turnstile or hCaptcha, optional) and fixed-window rate limits stored in Postgres with HMAC-hashed
keys (no plain IPs or emails). Not a WAF or DDoS protection. Table: `rate_limits`.

## At a glance

- **GenPM dependencies** (installed with it): [@core/db](https://genpm.net/p/@core/db)
- **npm dependencies** (proposed, never installed without asking): `react`
- **Environment variables** (added to `.env.example`): `ANTISPAM_SECRET`, `TURNSTILE_SITE_KEY`, `TURNSTILE_SECRET_KEY`, `ANTISPAM_IP_HEADER`, `ANTISPAM_TRUSTED_PROXIES`
- **AI rules**: [`AGENTS.md`](AGENTS.md), loaded by your agent only when it works in `src/lib/antispam`

## Security

GenPM installs a 40-character commit SHA (never a branch), verifies an Ed25519-signed manifest, never runs install scripts and scans AI rules for prompt injection. Details: [genpm.net/docs/security](https://genpm.net/docs/security).

## License

MIT — see [LICENSE](LICENSE). Browse the full catalog at [genpm.net](https://genpm.net).
