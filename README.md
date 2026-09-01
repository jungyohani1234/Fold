# Fold

*🇰🇷 한국어: [README.ko.md](README.ko.md)*

**Your AI should know who you actually are.** Fold builds a model of you from everything you've already told Claude, and it lives in your own files.

Your Claude lives on two sides of a wall. Chat and Cowork on one side, Claude Code on the other. There's literally a toggle. Everything you've told it is scattered across that wall, and none of it is a model of *you* that you own.

**Fold crosses the wall.** It harvests your Claude conversations (chats, Cowork, and your Code sessions) into structured local markdown your agent actually reads: a model of you that's yours.

![Fold running: one command walks you from setup to a model of you](docs/demo.gif)

**How you use Claude says a lot about who you are.** Every problem you talked through, every draft, every 3am question. Not exhaust, but raw material. And Fold catches the part no second-brain does: your **revealed** self. Not just what you wrote down, but what you kept coming back to, what you poured hours into, how your attention actually moved. A bio is who you'd *like* to be. Your Claude trail is who you've *been*.

- **Already keep an Obsidian / LLM-wiki?** Fold is the wall-jumping upgrade. It pulls the other side in.
- **Don't have one, but want an AI that actually knows you?** Fold builds you one from what you've already said.

**What you'll need:** [Obsidian](https://obsidian.md) + [Claude Code](https://claude.com/claude-code) (the terminal app) and a Claude plan. About 15 minutes to your first MVC. It writes only inside a `wiki/` folder, never your own notes.

## What you get: your MVC

**Memory tells your agent what you know. Your MVC tells it who you are.** Hundreds of scattered conversations in, a navigable **model of you** out. At its center is your **MVC (Mission · Vision · Core-value)**, the one-page essence of a person, drawn from your own words. Everything else becomes a page: the people and projects that recur, the ideas you keep circling, the way you actually think. All cross-linked, each one traceable back to the conversation it came from.

![Your MVC: a model of you on the left, and how it all connects on the right](docs/mvc.png)

## How it works

| | |
|---|---|
| **Assay** | sizes up your setup, writes a tailored plan |
| **Transcribe** | pulls your chats, Cowork, Code sessions (and Notion) across the wall |
| **Translate** | folds that raw material into structured pages |
| **build-mvc** | drafts your MVC, the model-of-you |
| **Replicate / Lint / Review** | back it up, keep it healthy, keep it current |

Each step is glossed in plain language. You never hear "running Assay," you hear "let me get a feel for your setup." And you run just one: `/assay` carries you to each next step at your yes, with no chain to memorize.

Want the mechanics (the browser harvest, the session MCP, the skills)? See **[docs/SPEC.md](docs/SPEC.md)**.

## Quickstart

1. Get **[Obsidian](https://obsidian.md)** and Claude Code.
2. Copy the **contents** of this repo's `template/` into a vault. (An Obsidian vault is just a folder, new or existing; you want `.claude/` and `wiki/` to sit at its root.)
3. Open it in Claude Code.
4. Run **`/assay`** and it walks you through the rest (pull your Claude over, fold it into pages, draft your MVC), one confirm at a time. *(Power users: `/transcribe`, `/translate`, `/build-mvc` also run standalone.)*

## It's yours

Plain markdown in your own vault. No Fold server; there isn't one. The agent writes only inside `wiki/`, never your own notes. Anything financial, medical, or private is skipped, not stored.

Not an AI-notes plugin (those only chat with the notes you already wrote), and not a hosted memory API (those rent your context back to you). Fold harvests both sides of the wall into files that are just yours.

## Early days

It runs end to end, but it's young, and the internal APIs it leans on (reading your claude.ai chats through your own logged-in browser) can shift, so expect rough edges. A file-export fallback always works. [Issues, ideas](../../issues), and [contributions](CONTRIBUTING.md) are welcome.

## Shoutout

Karpathy's LLM-wiki pattern. Garry Tan's GBrain, and "own your intelligence, don't rent it." Hashed 김서준's "in the agentic era, what remains is intent (의도)." GBrain is 220,000 pages and 25 years of one life, compiled by agents. Fold is the harvester that lets anyone begin their own.
