# Project agent memory

This file is the project's committed home for project-intrinsic agent knowledge: build, test, release, architecture, and sharp-edge notes that should travel with the code.

- Add durable project-specific notes here as they are discovered through real work.

## What this repo is

Public static site for `canteenwaterapp.com`: the Canteen landing page plus `privacy.html` and `terms.html`.
Plain HTML + one stylesheet (`canteen.css`), no build step, no JS, no CI. Served by GitHub Pages from `main`; `CNAME` holds the domain. Modeled on the sibling LEAF site at `firstmate/projects/leaflegal`.

## Sources of truth (do not copy app facts from memory; re-read these)

- Current app and privacy posture: `firstmate/projects/Canteen` (spec `docs/SPEC - v1.md` §3, §5, §6, §10, §14; `docs/Money and Privacy.md`; app code under `Canteen/Analytics/`, `Canteen/Screens/Settings/PrivacyScreen.swift`, `WhatCanteenSendsScreen.swift`). The in-app privacy copy is the authoritative wording.
- Analytics decisions: `firstmate/data/canteen-feedback-analytics-spec/captain-decision-*.md`. Settled facts: PostHog, **opt-in, off by default**, anonymous (`personProfiles = .never`, no IDFA), **US Cloud** (`us.i.posthog.com`), client IP discarded, retention 1 year, deletion within 30 days on request. Contact everywhere is `support@canteenwaterapp.com`.
- Design: Readout v3 tokens, `firstmate/data/canteen-design-readout-v3-1/readout-v3.html` (Saira UI + IBM Plex Mono numerals, warm dark default, warm-paper light via `prefers-color-scheme`). Favicons are generated from the Canteen app icon (`AppIcon-light.png`) with `sips`.

## Watch-outs

- SPEC §6 says v1 is **free with no StoreKit/IAP**. `terms.html` §5 carries forward-compatible wording for a possible future one-time unlock, flagged for captain review; do not assert an unlock ships today.
- Copy rules: no em dashes anywhere (middot `·` is fine), no corrective-contrast phrasing ("No X. No Y.", "not X but Y", "less A more B"). State things plainly and positively.
- Open captain wordings live in `privacy.html` (children/age, device-backup posture, analytics retention/deletion) and `terms.html` §5/§11 (payments, governing law). Re-confirm before finalizing.
- Verify no horizontal scroll at 390px and 1280px after layout changes (`chrome-devtools-axi emulate --viewport "390x844x3,mobile"`, check `scrollWidth > innerWidth`).

## Maintaining this file

Keep this file for knowledge useful to almost every future agent session in this project.
Do not repeat what the codebase already shows; point to the authoritative file or command instead.
Prefer rewriting or pruning existing entries over appending new ones.
When updating this file, preserve this bar for all agents and keep entries concise.
