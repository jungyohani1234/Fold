# /replicate — backup-assurance (DNA→DNA)

Ensure a versioned, off-site backup of the Fold **exists** — don't create a redundant one. A faithful copy,
nothing synthesized. Your Fold is a model of you; losing it means building yourself back from scratch — that's
the why. The most side-effectful skill: **consent-gated at every irreversible step**, and every gate is a warm,
plain sentence ("I'd like to make sure there's a safe, private copy somewhere off your laptop — okay?"), never
machinery. Voice: `playbook.md`.

## 1. Detect first (never assume)
Probe, in order; if any already covers the vault, that IS the backup:
- **Obsidian Sync** — `.obsidian/sync.json` / sync plugin config present.
- **iCloud** — vault path under `~/Library/Mobile Documents/…`.
- **Dropbox / Drive / OneDrive** — vault path under one of those synced folders.
- **git remote** — the VAULT is its own repo root (`git rev-parse --show-toplevel` == vault path) AND has a
  remote. Don't count an enclosing repo the vault merely sits inside.

Report what you found as reassurance, not a non-event. If a backup covers it → **tell them they're already
covered and where ("you're covered — this vault's in iCloud"), check that secrets aren't syncing where they
shouldn't (honor `_exclude.md`), and STOP.** No redundant backup.

## 2. Only if nothing covers it: offer the lowest-friction backup they can already use
- **Match the person, not the power-user.** Lead with the consumer option their OS already has — an iCloud/Drive
  folder or Obsidian Sync (GUI, no terminal); offer a **private git remote** as the power-user alternative, not
  the default. "git remote" is the least accessible option for a non-technical user.
- **Private, never public** — it's their life. Explicit consent before creating a remote or pushing.
- **Secret gate before the first push:** scan for secret-looking files + honor `_exclude.md` → `.gitignore`
  them. If secrets are already in git history, **scrub history before** the first push (offer to — don't
  push over it silently).
- Push only on a clear yes. State exactly what will be pushed (and what's gitignored) before doing it.

## 3. After
- Record the backup status (where/how) so the next Replicate detects it and refuses redundancy.
- Log a watermark (op `replicate`) noting what backup now covers the vault.

## Safety
- Every irreversible step (create remote, push, history-scrub) is consent-gated and stated first.
- Never push RAW/secrets without explicit per-action consent. DNA→DNA: copy, never synthesize.
