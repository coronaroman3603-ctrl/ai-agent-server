# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Projects Overview

This environment contains three projects:

- **ai-agent-server** — Node.js HTTP server (port 80)
- **raysbot** — Python/Flask Telegram bot webhook (port 8000)
- **apps/first-repo** — Git learning repository (no code logic)

## Commands

### ai-agent-server (Node.js)
```bash
cd ai-agent-server
npm start        # runs node index.js
```
No test or lint scripts configured. Uses ES6 modules (`"type": "module"` in package.json). No npm dependencies — only Node.js core `http` module.

### raysbot (Python)
```bash
cd raysbot
source venv/bin/activate
python telegram_webhook.py
```
Python 3.10, Flask-based. No test or lint configuration.

## Architecture

### ai-agent-server
Single-file server (`index.js`). Listens on `0.0.0.0:80`, responds to all requests with `{ "message": "AI agent server is running" }`.

### raysbot / telegram_webhook.py
Flask app with two routes:
- `GET /` — health check, returns "RaysAgent is running"
- `POST /webhook` — receives Telegram updates and echoes messages back via Telegram Bot API

The Telegram bot token is hardcoded in the script — move it to an environment variable before production use.

**Note:** `telegram_webhook.py` exists in both `/home/ubuntu/` (root) and `/home/ubuntu/raysbot/` — the canonical version is in `raysbot/`.

## Git Remotes
- `ai-agent-server` → `git@github.com:coronaroman3603-ctrl/ai-agent-server.git`
- `first-repo` → `git@github.com:coronaroman3603-ctrl/first-repo.git`
