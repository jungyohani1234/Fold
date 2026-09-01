# /assay — first-run intake (the measurements)

Run once at setup (or to re-measure). Produces a tailored setup plan.
Blanks are the measurement, never a failure. Never requires a hub. Runs in the user's language.
Voice: follow `playbook.md` (align before the headache; ask few, infer many, propose; nothing is permanent).

## 0. Language
Detect the language the user writes in; confirm. Everything user-facing runs in it.

## 1. Auto-detect (silent probe — HINTS, not verdicts)
Vault present? (.obsidian) · wiki/ present? · hub present? · domain layer? · backup signals ·
git remote? · RAW volume · secret-looking files.
(Backup often can't be detected from the filesystem — always ASK it in step 2.)

## 2. Interview (ask ONLY what probing can't settle — ~4; supportive, low-stakes)
Open with a BRIEFING, not a question: why these matter, "nothing here is permanent,"
"'I don't know' is a real answer → I'll look and propose."
**Then reflect back a provisional profile from the step-1 probe BEFORE any menu** — e.g. "Here's what I can
already see: Obsidian vault, ~200 notes, looks iCloud-backed, lots on <topic>, no wiki yet — reads to me
like a <both-packed> setup. Fix anything?" The questions below then confirm/correct a filled-in draft, not
a blank menu:
- Q1 What's pulling you here? (multi-select + "not sure")
- Q2 Where does your thinking live? (claude chat · Cowork · Code · Notion · Obsidian · in my head)
- Q3 How's this vault backed up? (Sync · iCloud/Dropbox · git · not sure → "I'll check")
- Q4 Sensitive topics: "I'll steer clear of anything about health, money, or identity unless you say otherwise — sound right?"
The hub is NOT asked as a commitment — deferred ("a center usually suggests itself in a few weeks").
Every "not sure" routes to: infer from the probe → PROPOSE → user approves/tweaks.

## 3. Classify → branch
{greenfield · chat-only · code-only · both-packed} × has-vault? × has-hub? × has-backup?
Plus inferred dims (mostly observed, not asked): maintenance appetite (compounder/dabbler) ·
kind of worker / content type · incumbent system (Notion/Roam/…) · audience (private/shareable) ·
corpus privacy posture · why-now.

## 4. Emit `wiki/setup-plan.md`
Profile + ordered tailored steps + seeded config (`_exclude.md`, language, backup status, hub-later).
- Write the profile as **named fields downstream skills read** (don't just prose it): `worker-type`,
  `pace` (fast-pivot / steady), `maintenance-appetite` (compounder / dabbler), and a derived `cadence`.
  Translate reads `worker-type` (what counts as signal), Review reads `pace` (the freshness curve),
  Lint/Review read `cadence`. Measured once here, honored everywhere — so the Fold fits *this* person, not a default one.
- greenfield → create vault + doctrine + bones → 3 seed pages → first Transcribe.
- chat-only → Transcribe is the main event → Translate → `build-mvc` drafts the MVC hub.
- code-only → doctrine + bones → Translate existing notes.
- both-packed → confirm + tune cadence, no scaffolding.

## 5. Confirm, then guide the flow — don't make them memorize commands
Once the plan is approved, OFFER to run its first build step now; on a yes, **read and follow the matching
command file** (`.claude/commands/transcribe.md`, or `translate.md` if the plan is code-only) and keep going.
Each step then hands to the next the same way, so a single `/assay` walks the user all the way to their MVC —
every step consent-gated. They can stop, tweak, or drive with the individual `/commands` anytime.

## Implementation notes (validated 2026-08-30 on a fresh greenfield vault)
- The skill ships INSIDE `template/`, so by the time `/assay` runs, the Fold bones already exist.
  "greenfield" in practice = template present but **empty** (0 wiki pages, 0 imports, no hub) — detect
  *emptiness*, don't expect a bare directory. (A truly bare vault only happens if Assay is ever shipped
  standalone — a v2 concern.)
- Probe corrections — both were **false positives** in testing:
  • **git remote:** scope it to the vault being its OWN repo root — compare `git rev-parse --show-toplevel`
    to the vault path. A naive `git remote` walks UP to any enclosing repo and reports a remote that
    isn't the vault's.
  • **RAW volume:** exclude Fold's own scaffold (`CLAUDE.md`, `playbook.md`, `README*`, `wiki/`, `.claude/`)
    or you count the scaffold as the user's notes.
- Interview: use the native question UI (AskUserQuestion) — Q1 multi-select; every question offers
  "not sure"; each "not sure" routes to infer-from-probe → propose. Keep to ~4; open with the briefing.
- Emit `wiki/setup-plan.md` with `status: proposed` — never auto-run steps. Seeding config is allowed
  (it's low-risk + reversible): write the confirmed `_exclude.md` categories and the language. A worked
  example lives in the test vault. Everything user-facing runs in the user's language (this test ran in Korean).
