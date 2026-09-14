# Higgs Hub plugins

[Higgs Hub](https://higgshub.pro) connects your Gmail / Google Workspace and Outlook / Microsoft 365 accounts — mail, calendar, files, spreadsheets, tasks — to your AI agent through one audited connection. This repository holds the plugin for **Claude Code** and for **Codex / ChatGPT**. Each install brings the Higgs Hub connection plus a guided getting-started skill.

You need a Higgs Hub account with a connected mailbox: sign up at https://higgshub.pro and open **Mailboxes → Add an inbox**.

## Claude Code

```
claude plugin marketplace add cogear/higgs-hub-plugins
claude plugin install higgs-hub@higgs-hub-plugins
```

Or inside Claude Code: `/plugin marketplace add cogear/higgs-hub-plugins`, then `/plugin install higgs-hub@higgs-hub-plugins`.

The first time, run `/mcp`, pick **higgs-hub** and choose *Authenticate*. A browser window opens on higgshub.pro to sign in and approve access. Then run `/higgs-hub:getting-started` for a guided first session.

If you connected earlier with `claude mcp add higgs-hub`, remove that copy first so there is one connection: `claude mcp remove higgs-hub`.

Already use the Higgs Hub connector on claude.ai? Claude Code picks it up when it is signed in with the same Claude account, so you only need this plugin for the getting-started command. Don't use both, or Higgs Hub shows up twice.

## Codex and ChatGPT

```
codex plugin marketplace add cogear/higgs-hub-plugins
codex plugin add higgs-hub
```

Or open `/plugins` inside Codex and install **Higgs Hub**. Codex signs you in to higgshub.pro as part of the install. Start a new session afterwards; *Getting started with Higgs Hub* is in the skills picker.

If you added Higgs Hub to Codex earlier by hand (an `mcp_servers` entry in `~/.codex/config.toml`, for example through mcp-remote), remove it with `codex mcp remove <name>` so there is one connection.

## What is inside

- `higgs-hub/` — the plugin: `.mcp.json` (the Higgs Hub endpoint, OAuth sign-in) and `skills/getting-started/`.
- `.claude-plugin/marketplace.json` — the catalog Claude Code reads.
- `.agents/plugins/marketplace.json` — the catalog Codex and ChatGPT read.

## About this repository

This is a publish-only mirror of the `plugins/` directory in Higgs Hub's source. Pull requests are not merged here; write to support@higgshub.pro. [Privacy](https://higgshub.pro/privacy) · [Terms](https://higgshub.pro/terms)
