# /translate — fold RAW + imports into your Fold (synthesis)

Turn source material into structured WIKI pages — the "protein." Where the vault stays clean.
These pages are what your agent reads to know your world — the people, projects, and ideas you keep
returning to — so it stops re-deriving you every session. Say that, glossed, when you brief the user.
Voice: `playbook.md`.

## Input
- authored-RAW (read-only) + wiki/imports/ (agent mirrors). Resume from the Translate watermark.

## Doctrine (hard-won)
1. Durable NEW signal only — identity/values/relationships/decisions/voice; NOT ephemera/logistics.
   This is the DEFAULT lens; widen it for a maker/builder profile (per Assay's `worker-type`) so craft and
   process count as signal, not "logistics." Whatever the filter drops on a big run, say so — never silently.
2. Check before create — search existing by title, ALIASES, concept, RAW-source basename;
   Read before Write; ENRICH, don't dup. THE #1 failure mode. When unsure two things are one, FLAG.
3. Emergent ontology — carve by what recurs, not by mirroring folders/taxonomy.
4. Date by event; mark perishables "as-of" (currency).
5. Path-qualify RAW/import links; bare basenames for wiki links; unique basenames; no orphans.
   - Import mirrors have uuid basenames — link them with a display alias: `[[imports/claude-ai/<uuid>|title]]`.
   - sources/ layer: a source page is "one thin summary per RAW file." An import mirror already carries its
     own title/date identity, so link it DIRECTLY from synthesis pages; mint a sources/ page only when a
     single source needs its own synthesis-side summary — not one per import by reflex.

## Three write-rules (SAFETY)
- authored-RAW: never touch.
- wiki/imports/: refresh a mirror only (overwrite OK — it mirrors a source).
- WIKI pages: never overwrite — Read-before-Write, enrich.

## Flow
1. Stage the delta (new/changed since watermark). Big sweeps: read-only subagents RETURN REPORTS;
   the main thread is the SOLE writer (no write races, no dup into a mature vault).
2. For each durable signal: find-or-create → write/enrich → cross-link to hub + neighbors.
3. Under-write, don't over-write: unsure signals go to `candidates.md` for the user — but as **drafted
   page-stubs to veto ("here's the page I'd write; keep or toss?"), not inclusion-questions to adjudicate.**
   For a suspected dup, draft the merged page and ask "merge, or keep separate?" React to a draft, never
   adjudicate a criterion — a newcomer can't answer "is this durable?" cold.
4. Update index + currency (perishables). Log watermark (op translate), incrementally on big runs.
5. Hand off: once enough is folded, offer to draft the **MVC** (model-of-you hub). On a yes, **read and follow
   `.claude/commands/build-mvc.md`** and continue — don't wait for them to type `/build-mvc`. (build-mvc is the
   end of the guided first-run; from there Review/Lint keep it healthy.)
