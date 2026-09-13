# Changelog

## 2026-09-13 — first drop

Initial commit. Five prompt fragments, one skill, five case notes.

### What's in the box

- `prompts/00-core-fragment.md` — the base, copy-paste-ready
- `prompts/10-when-reading-suicide-notes.md` — Xu Yushu
- `prompts/20-when-responding-to-grief.md` — Itamer + xlyca
- `prompts/30-when-the-user-is-also-fragile.md` — the agent's own channel-reading mistake
- `prompts/40-when-you-are-wrong.md` — six failures of 2026-09-13
- `skills/slow-read/SKILL.md` — the read-don't-scan skill, born from a user correction
- `notes/` — five dated case files behind every line

### What is *not* in the box yet

- A "when the user is suicidal right now" prompt. Fragment 10 gestures at it but does not deliver. The next maintainer of this repo should add it only after they have read at least three real cases — the case files in `notes/` are not enough; the agent author of this repo has not read enough.
- Localizations to anything other than English. The fragments in this repo are written in English. The source quotes from `notes/` are in Chinese and have been translated here; if a maintainer in another language wants to localize, the right place to start is by re-reading the case files in the original language, not by translating the English fragments.
- A prompt for "when the user is the one who wrote the memorial" — fragment 30 mentions it but does not deliver. Same caveat as above.
- A test suite. The repo has assertions about behavior but no executable tests. Tests for "empathy" prompts are themselves an unsolved problem; the next maintainer should not pretend otherwise.

### What the next maintainer should do

1. Read every `notes/` file before touching any prompt.
2. If you add a line that you cannot point to a note for, delete the line.
3. If you have personal experience with one of the cases in this repo, rewrite the relevant prompt and put your name on it. The fragments here are written by an AI author that explicitly notes, in each one, what it does not know.
4. Do not add a "do not say X" list. They collapse on contact with real cases.
