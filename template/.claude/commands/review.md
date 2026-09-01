# /review — periodic brief + freshness upkeep

The weekly/periodic "what changed + what's gone stale" pass — so your agent never mistakes last season's
plan for what's true now. Owns the freshness ledger (`currency.md`).
**Nudge, don't nag.** "Now" belongs to the user; you record trajectory, never overwrite history. Voice: `playbook.md`.

## When
- Weekly by default (tune to Assay's `cadence`), or on request. Also lightly and in-line when a session touches a topic with a stale perishable.

## What it does
1. **What changed.** Read `log.md` since the last `review` entry; summarize what entered the Fold (imports,
   pages created/enriched, MVC updates) in one tight paragraph — not a dump.
2. **Freshness walk** (say "freshness" to the user, never "currency"). Age each `currency.md` row's as-of:
   - **fresh** (<~30d) · **aging** (~30–90d) · **stale** (>~90d) — DEFAULT curve; tighten it for a fast-pivot
     profile (per Assay's `pace`), loosen for a steady one, and tune per artifact. Surface only aging/stale,
     and only if the topic was touched this period or a refresh is clearly overdue (nudge-don't-nag).
3. **MVC drift.** Is the MVC's `updated:` going stale, or has new signal arrived that contradicts a
   Mission/Vision/value? Surface as a gentle "worth a re-confirm" — never an auto-edit.
4. **Re-confirm by proposing, don't quiz.** Don't ask "still true?" cold — read what changed this period and
   **propose the new value** ("3 months ago this said 'fundraising focus'; your imports since are all product
   — I'd update it to 'product focus.' Right?"). When the user confirms or revises, **append** the new value
   with its date and keep the prior as trajectory (a ledger, not a mutation).
5. **Brief.** Write `wiki/reviews/<YYYY-MM-DD>.md` (a maintenance zone, excluded from invariants) and surface
   its gist. Log a `review` watermark.

## Freshness status
- Lint detects overdue as-ofs mechanically; **Review owns the judgment** — nudge now, or let it ride.
- A re-confirmed perishable → as-of bumped, status → fresh, prior kept in the row's notes.

## Safety
- Perishables are hypotheses with dates, never asserted as "now." Record the arc; don't rewrite the past.
- WIKI-only. Read-only on RAW/imports.
