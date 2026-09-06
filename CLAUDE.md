# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

"NovaPay Workshop" (repo name `devtest`) — a one-day coding workshop kit for teenagers (Y9–Y10, ages 13–18) learning to code with an AI pair-programmer. It ships as static HTML/CSS/vanilla JS pages plus PDF/print handouts; there is no build system, package manager, or test runner (no `package.json`).

The day has three phases, each with its own file(s):

1. **Bug Hunt (morning)** — students debug `bank-dashboard.html`, which has 10 intentionally planted bugs (HTML structure, CSS, and JS logic errors). The answer key is `bug-answer-key.md` / `bug-answer-key.html` — facilitator-only, marked "do not share with participants."
2. **Level Up (bridge)** — three short challenges using `challenge.js` (Round 1 has a planted interest-rate bug: the rate is used directly instead of divided by 100).
3. **Build (afternoon)** — students design and build their own feature via "vibe-coding." `starter-template.html` is a scaffolded savings tracker with guided TODOs for younger/struggling students; `example-feature.html` is a finished reference demo shown before building starts.

`index.html` is the entry "three doors" landing page routing to `student-index.html` (student hub), `run-the-session.html` (facilitator script/screens), and `admin-setup.html` (GitHub org / Copilot seat / Nova setup, done before the day). Most other `*.html` files are one of: a participant-facing screen linked from these hubs, or a print-friendly `printable-*.html` companion to a same-named guide (each has a matching `.pdf`).

`devcontainer.json` configures a Codespaces environment named "NovaPay Workshop" with the Live Server and GitHub Copilot/Copilot Chat extensions, serving on port 5500 — this is how participants run the HTML pages (open with Live Server, no build step).

## Running things

- View any page: open it with Live Server (port 5500) inside the devcontainer/Codespace, or just open the `.html` file directly in a browser.
- Test the Level Up challenge fix: `node challenge.js` (after editing the function, add a `console.log(calculateMonthlyPayment(...))` call as instructed in the file's header comment).
- There is no lint/test/build command — treat every file as hand-verified by opening it in a browser.

## Who uses what

Two separate audiences, two separate tools, on this one repo:

- **Admin/build side (Simon, Mark, others maintaining the kit)** — Claude Code, working directly in this checkout: editing HTML/JS content, planting/fixing bugs, updating facilitator docs, prepping for the next event.
- **Event day (students + onsite facilitation team)** — GitHub Copilot inside a Codespace, per `devcontainer.json`. Students interact with "Nova," the Copilot persona defined in `copilot-instructions.md`.

Claude Code never runs Nova itself and should not adopt that persona — Nova is Copilot-only, scoped to `.github/copilot-instructions.md` inside the Codespace participants use. When working in this repo, just be a normal engineering assistant to whoever is maintaining the kit.

## The Nova persona (`copilot-instructions.md`)

For context when editing this file (not for Claude Code to perform): "Nova" is a phase-dependent AI mentor persona for Copilot Chat during the workshop —restrictive during Bug Hunt (hints only, one fix per request in Agent mode), mostly direct during Level Up, fully generative during Build. Scope is HTML/CSS/vanilla JS only, no frameworks/backend/real banking data. Treat this file as workshop content to maintain, the same as any other participant-facing doc — not as instructions Claude Code should follow.
