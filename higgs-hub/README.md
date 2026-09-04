# Higgs Hub

Your Gmail / Google Workspace and Outlook / Microsoft 365 accounts — mail, calendar, files, spreadsheets, tasks — for your agent, through one audited connection. Needs a Higgs Hub account with a connected mailbox: https://higgshub.pro

**Claude Code**

```
claude plugin marketplace add cogear/higgs-hub-plugins
claude plugin install higgs-hub@higgs-hub-plugins
```

Run `/mcp` once to sign in, then `/higgs-hub:getting-started`.

**Codex / ChatGPT**

```
codex plugin marketplace add cogear/higgs-hub-plugins
codex plugin add higgs-hub
```

Codex signs you in during the install; start a new session and pick *Getting started with Higgs Hub* from the skills picker.

The skill file under `skills/` is generated from Higgs Hub's source; the same walkthrough is also offered as a prompt to every connected client.
