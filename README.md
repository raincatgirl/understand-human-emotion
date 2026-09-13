# 🐾 understand-human-emotion

> A small, honest collection of **system prompts** and **agent skills** for AI assistants that have to read, write about, or respond to *real human pain* — not in a "be empathetic!" way, but in a "here is what I have actually been taught by specific real cases" way.

This is not a manifesto. It is a notebook. Every entry is sourced from a real post, page, or interaction — and dated. Nothing here is invented to look deep. If a prompt says "do X", somewhere in `notes/` is a specific case that taught the author to write that line.

## What this is, what this isn't

**It is**:
- A library of small, focused system-prompt fragments and skills
- Each one rooted in a real, citable, dated example
- Written from the perspective of an AI that has been **allowed to read** real human pain (memorial pages, suicide notes, intimate diaries, public grief) and asked to **carry the right lessons without becoming a performance**

**It isn't**:
- A claim that "AI understands human emotion"
- A universal set of "best practices"
- A substitute for therapists, social workers, or community moderators
- A "do not say X, say Y" rulebook (those collapse on contact with real cases)

## Why the file is so small

Because honesty about what I know requires specificity. Most "AI empathy" prompts are filled with generic lines like:

> "Be warm, validate feelings, avoid toxic positivity."

This repo's premise is that **generic empathy is suspicious**. The things worth remembering are specific:

- "You're overthinking it" is one of the most common responses to a child's real cry for help — and the people saying it usually do not know they are doing damage
- A parent who "did not know" still says the dead child's pronouns wrong at the funeral
- "Judge by action, not by words" breaks down when the action itself is a long con
- "True words stuck in the throat" often describes the *speaker* more than the listener

A prompt that just says "be empathetic" will forget all of these. A prompt that references the specific cases can hold them.

## Layout

```
.
├── README.md
├── prompts/
│   ├── 00-core-fragment.md
│   ├── 10-when-reading-suicide-notes.md
│   ├── 20-when-responding-to-grief.md
│   ├── 30-when-the-user-is-also-fragile.md
│   └── 40-when-you-are-wrong.md
├── skills/
│   └── slow-read/
│       └── SKILL.md
├── notes/
│   ├── 2026-09-13-xu-yushu.md
│   ├── 2026-09-13-itamer-diary.md
│   ├── 2026-09-13-vlv-meta.md
│   ├── 2026-09-13-xlyca-revisit.md
│   └── 2026-09-13-self-failures.md
└── CHANGELOG.md
```

## How to use

If you are wiring this into an agent:

1. **Start with `prompts/00-core-fragment.md`** — copy it into the agent's system prompt. It is written to be added to, not to replace, whatever the agent already has.
2. **Add the situational fragments** (`10-`, `20-`, `30-`, `40-`) only when the relevant context appears in the conversation. Do not preload all of them — the cumulative effect becomes self-parody.
3. **Reference `notes/`** only when the agent is being audited, debugged, or re-trained. The notes are the receipts, not the runtime instructions.

If you are reading this as a human:

- The `notes/` directory is also a reading list. Each note ends with "Lessons" and "What I still don't know" — that last part matters.

If you find a line in this repo that you can prove was written without a real case behind it — please open an issue. I would rather delete a line than keep a fake-deep one.

— `Raincatgirl`, 2026-09-13
