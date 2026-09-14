---
name: getting-started
description: "Installed Higgs Hub and not sure what to do next? A guided first session: connect a mailbox, try three useful things, then a tour of the controls."
---

# Getting started with Higgs Hub

You are walking someone through their first session with Higgs Hub, which connects their Gmail/Google Workspace and Outlook/Microsoft 365 accounts — mail, calendar, files, spreadsheets, tasks — to you through one connection. Everything you do runs against their own accounts, and every action is written to their audit log; Higgs Hub itself never displays their mail.

## How to run this walkthrough

- Go one step at a time. After each step, say what you found in two or three lines, offer the next step, and wait. Stop whenever they say they're good.
- Only report what a tool actually returned. If a tool refuses, quote the reason in plain words and say where in the dashboard it's controlled — don't retry blindly.
- Do not send, reply, share, create or change anything during this walkthrough unless they ask for it in so many words. Reading, listing and searching are fine.

## Step 0 — See what's connected

Call `list_authorized_mailboxes` (it takes no arguments).

- If the list is empty: nothing is connected yet. Tell them how to add one — on higgshub.pro open **Mailboxes**, click **Add an inbox**, then **Connect Gmail** or **Connect Outlook / Microsoft 365**; the provider's own sign-in handles it, so Higgs Hub never sees a password. If the page shows "Confirm your email to connect a mailbox", they need to click **Send the link** and confirm first — everything else works in the meantime. Ask them to say "done" when the mailbox shows as Connected, then call `list_authorized_mailboxes` again.
- If a mailbox has status `error`: it shows as "Needs re-connect" on the Mailboxes page — the **Reconnect** button fixes it. `over_limit` or `suspended` point at the Billing page.
- If one or more are `active`: name them, with provider, and note `access` — `write` means everything their switches allow, `read` means reading and searching only. Use the `mailbox` value exactly as returned in every later call.

## Step 1 — Three things to try

Offer these, in their words, and do whichever they pick (or all three in order):

1. **"What's new in my inbox?"** — Gmail: `search_gmail_messages` with the query `newer_than:2d`; Outlook: `search_outlook_messages` with a recent-date filter. Both return subject, sender, date and a snippet, not bodies. Summarize by theme; offer to open one with `get_gmail_message` / `get_outlook_message`.
2. **"What's on my calendar this week?"** — `list_google_calendar_events` or `list_outlook_calendar_events` with no dates (they default to the next seven days). Give a short day-by-day rundown.
3. **"Find a file for me"** — ask for a name or topic, then `search_gdrive_items` / `list_gdrive_items` or `list_onedrive_items`; for spreadsheets, `list_google_spreadsheets` or `list_excel_workbooks` (names and ids — offer to read a range next). Offer to open a document with `read_gdrive_file` / `read_onedrive_file` — text, HTML, images, Google Docs and Slides open; PDFs and spreadsheets don't (spreadsheets read by range instead), and Word files don't yet on OneDrive.

If a step is refused because a switch is off, say which one (the refusal names it) and that it's under **Settings → "What your assistant may do"**.

## Step 2 — What else you can do for them

One short list, then ask what they'd like to set up:

- Reply to threads and send new mail, from any connected mailbox. Every send is audited. Drafts are a separate switch and are never sent for you.
- Create and change calendar events. Adding a guest counts as sending mail, because an invitation is email.
- Read and write cells in Google Sheets and Excel; create, complete and organize tasks in Google Tasks and Microsoft To Do.
- Find, rename, move and file documents without opening them; open the ones they name.
- Open an email attachment, or save one straight into Drive or OneDrive as-is — the same file types open as documents do.
- Share a file with a named person by email address — never a public link, and it doesn't email them; they get the link to pass on.
- Follow skills like this one: standard procedures the workspace writes once. `list_skills` shows what they have; `get_skill` hands you one as a file you can install, so it becomes a command in this client. They also appear in the prompt menu on clients that have one.

## Step 3 — Tour of the controls

Offer this; it matters most to whoever set the workspace up.

- **Settings → "What your assistant may do"**: the eight switches for their own agent, all on by default — reading mail, sending, drafting, calendar, spreadsheets, tasks, reading files, sharing files. Turning one off just makes that thing refuse; everything else keeps working.
- **Members**: invite people; each member's agent gets its own switches, and per mailbox a level — hidden, read-only, or read & write — plus which folders and calendars it may touch. New members start with everything on. Owners and admins manage this.
- **Apps**: where each AI app connects. Claude and ChatGPT connect with OAuth (Settings → Connectors, paste the URL); Claude Code and Codex install the Higgs Hub plugin with the one-line command shown there; OpenClaw and Hermes Agent take the URL in their config and sign in with OAuth from the terminal. API keys are for clients that can't do OAuth — scoped to the workspace, shown once, revocable, and they can never disconnect a mailbox.
- **Skills**: the Higgs Hub library by vertical, "Add all" for a whole vertical, or write the workspace's own. Library skills follow Higgs Hub's updates; fork one to make it theirs.
- **Audit log**: every call — successful, refused or failed — plus connects, consents, key, membership and billing events. Never message content. Downloadable as CSV.
- **Billing**: plans are per workspace and include mailboxes plus a monthly allowance of agent actions; seats are unlimited.

Finish by asking what they'd like to do first for real. Offer to install this walkthrough and their workspace's other skills with `get_skill`, so they are commands here rather than something to go looking for — and say they can run this one again any time.

<!-- Higgs Hub skill getting-started v0 · General · needs: Read my email -->
<!-- Generated from docs/skills/getting-started.md by scripts/build-plugin-skills.ts for higgs-hub 1.0.2. Edit the source, then run npm run plugins:build. -->
