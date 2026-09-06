# StemTastic

StemTastic is the administration and delivery layer for running coding workshops. This repo currently holds one workshop's full kit: the **NovaPay Workshop**.

## The NovaPay Workshop

A one-day coding workshop for Y9–Y10 students (ages 13–18), pairing them with an AI assistant ("Nova," a GitHub Copilot persona) to debug, extend, and build a simple banking app. It's run multiple times, not a one-off event — this kit is the reusable source for each run.

Ships as static HTML/CSS/vanilla JS pages plus PDF/print handouts. No build system, package manager, or test runner.

## Start here

Open [index.html](index.html) — it routes to one of three hubs depending on who you are:

| I am... | Go to | For |
|---|---|---|
| A student | [student-index.html](student-index.html) | Today's agenda and session materials |
| Running today's session | [run-the-session.html](run-the-session.html) | Facilitator script, screens, troubleshooting |
| Setting this up | [admin-setup.html](admin-setup.html) | GitHub org, Copilot seats, Nova install — before the day |

## The three phases of the day

1. **Bug Hunt (morning)** — students debug [bank-dashboard.html](bank-dashboard.html), which has 10 intentionally planted bugs (HTML, CSS, JS). Answer key: [bug-answer-key.md](bug-answer-key.md) / `.html` — **facilitator-only, never share with participants**.
2. **Level Up (bridge)** — three short challenges in [challenge.js](challenge.js). Round 1 has a planted interest-rate bug (rate used directly instead of divided by 100).
3. **Build (afternoon)** — students design and build their own feature. [starter-template.html](starter-template.html) is a scaffolded savings tracker with guided TODOs for younger/struggling students; [example-feature.html](example-feature.html) is a finished reference demo shown before building starts.

## Running it

- Open any page with Live Server (port 5500) inside the devcontainer/Codespace, or just open the `.html` file directly in a browser.
- Test the Level Up fix: `node challenge.js` (after editing, add a `console.log` call as instructed in the file's header comment).
- There's no lint/test/build command — every file is hand-verified by opening it in a browser.

## File map

Most other `*.html` files are either a participant-facing screen linked from the three hubs above, or a print-friendly `printable-*.html` companion (each with a matching `.pdf`) to a same-named guide. For the full breakdown, see [CLAUDE.md](CLAUDE.md).

## Who uses what

- **Admin/build side** (Simon, Mark, others maintaining the kit) — Claude Code, working directly in this checkout: editing content, planting/fixing bugs, updating facilitator docs, prepping for the next run.
- **Event day** (students + onsite facilitation team) — GitHub Copilot inside a Codespace, per [devcontainer.json](devcontainer.json). Students interact with "Nova," defined in [copilot-instructions.md](copilot-instructions.md).

Claude Code never runs Nova and shouldn't adopt that persona — Nova is Copilot-only, scoped to participant Codespaces.

## Re-running the workshop

Since NovaPay runs multiple times: [github-setup-guide.md](github-setup-guide.md) covers turning this kit into a fresh participant-ready Codespace repo for each run. [CLAUDE.md](CLAUDE.md) is the exhaustive reference for the workshop's structure when maintaining it between runs. If the planted bugs in `bank-dashboard.html` ever change, update `bug-answer-key.md` to match.
