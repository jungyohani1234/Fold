# /lint — health sweep

Keep the Fold healthy: catch what rots (broken links, orphans, dupes, stale claims, filename hazards),
**fix** the mechanical, **flag** the structural. Read-only on RAW/imports; writes only to WIKI. Voice: `playbook.md`.

## When
- On request, or every ~20 new pages (tune to Assay's `cadence`). Cheap — run it often.

## Checks
**Structural**
- **Orphans** — a synthesis page (`themes/ concepts/ entities/ sources/`) not reachable from `index.md`.
- **Broken [[links]]** — a wikilink whose target doesn't exist (bare → basename; path-qualified → path).
- **Missing from index** — a page not listed in `index.md` (same set as orphans; reported as a fix).
- **Duplicate concepts** — two pages that look like one node (title/alias overlap, near-identical summary).

**Hygiene**
- **Filename rule** — no `: / \ ? * < > | "` in a basename (breaks Windows/iOS/sync).
- **Basename collision** — the same basename twice anywhere in the vault (corrupts Obsidian links).
- **Dangling RAW links** — a `[[path/to/RAW]]` that no longer resolves (after a user rename).
- **Stale perishables** — `currency.md` rows whose as-of is overdue (hand the *nudge* to Review).
- **Frontmatter** — missing `type`/`updated`, or an `updated` in the future.

## Fix vs Flag
- **Fix (mechanical, safe):** add a missing page to index; repoint a link after an unambiguous rename;
  rename a filename-rule violation (and repoint its links, NFC-safe); normalize frontmatter.
- **Flag (structural) — but flag WITH a drafted fix, don't just ask:** for a dup, draft the merged page and
  ask "apply, or keep separate?"; for an ambiguous link, propose the best target and offer the alternative.
  Anything touching meaning. **Never auto-merge pages** — but never hand a cold decision either.

## Runnable core (implementation notes, validated 2026-08-30)
- Normalize BOTH filenames and `[[link]]` targets to Unicode **NFC** before comparing — macOS stores Korean
  basenames as NFD, so a naive compare false-flags every Korean page.
- Exclude from link/orphan checks: `wiki/imports/**` (mirror zone), `_*.md` scaffolding (`_page-template`,
  `_exclude`), and maintenance files (`index`, `log`, `currency`, `candidates`, `setup-plan`, `reviews/**`).
- Link grammar: `[[target]]` or `[[target|display]]` — take the part before `|`. A `/` in target → path
  relative to vault root (+`.md`); else → match by basename anywhere in the vault.
- Emit the report in plain outcomes, not check-names ("fixed 4 broken links, renamed a file that would've
  tripped sync; two pages look like duplicates — want to see them?"). A wiki that rots is a garbled map of
  you, and your agent reads it — that's the why. Keep the `file:line` detail available underneath.

## Safety
- WIKI-only writes. Never touch RAW or imports. A "fix" that would change meaning is a **flag**, not a fix.
