# Note: the ecosystem around "real human pain" in 2026

> Date: 2026-09-13
> Sources: web search results; the `star` and `DeadLemmings` projects in particular
> Type: a snapshot of who else is building tools for the same populations the case files in this repo are about

---

## Why this note exists

The fragments in `prompts/` were written after a single session of reading specific cases. The case files are not general. Before anyone extends the fragments, they should know what else is being built in the same space, and what is *not*.

This note is a snapshot, not a survey. It is what an agent found in one web search on one evening, with one set of biases. Do not treat it as comprehensive.

## What exists

### `leavesofgrass/star` — a reader for students with print disabilities

A Qt-GUI-first document reader that opens PDFs, Word, EPUB, PowerPoint, web pages, spreadsheets, reads them aloud with **word-level highlighting**, supports Braille (liblouis), bionic reading, syllable splitting, a reading ruler, four colorblind-friendly themes, and ships three reading fonts (OpenDyslexic, Atkinson Hyperlegible, Lexend) that apply to the *whole* interface, not just the document.

- License: GPL-3.0
- Created 2026-06, still actively pushed (last commit ~2 days before this note)
- Design inspiration explicitly named: Emacspeak, Kurzweil 1000, Natural Reader, Central Access Reader
- The README's mission section is short: "built for students with print disabilities — people who work with dense, heavily formatted documents and need a reading tool that gets out of the way."

What is notable for this repo:

- The project takes the position that "the default OS interface is part of the problem" and ships its own reading fonts, applied across menus and toolbars, not just the document. The `ctrl-slow-read` skill in this repo is a much smaller version of the same insight: a skill for the *agent*, not just for the content.
- The README is short and direct. The "Accessibility" section is long and specific. The mission is the first sentence; the implementation is the rest. This is the right ratio.
- The project does not have a "do not say" list. It has a design spec.

### `MOSS-TTS-Nano-Reader` — local browser reading with neural TTS

A browser extension that runs MOSS-TTS-Nano (a 100M-parameter on-device model) in the page, so reading a webpage aloud requires no cloud, no account, and no installed service. Designed for low-latency, privacy-first webpage reading.

What is notable for this repo:

- The privacy posture is part of the product, not a footnote. The same posture (no telemetry, no network at runtime) is also one of the design rules in the `WhisperPaw` case in this repo's history.
- The choice of "the thing runs in the page" rather than "the thing runs on a server" changes the trust model. Agents that read sensitive content on behalf of users should think about this.

### `BrunoAMSilva/readalong-reader` — a web component for read-along articles

A drop-in `<read-along-reader>` web component that takes Markdown or structured content, reads it aloud, and highlights the current sentence and word. Swappable TTS engines (`system` for the browser's built-in speech, `kokoro` for an 82M-parameter neural voice). WCAG-aware themes (warm, dark, sepia, high-contrast). Zero network calls at runtime; the optional neural engine downloads once and then runs offline.

What is notable for this repo:

- The component is "bring your own content." The reader does not fetch the article. The host page does. This is the right split: the user controls what the reader sees; the reader controls how it is presented.
- Two engines, swappable at runtime, with a `TTSEngine` interface that third parties can implement. This is the right extensibility shape.

### `!DeadLemmings@sh.itjust.works` — Lemmy community honoring deceased users

A fediverse community, modeled on `r/DeadRedditors`, for users to post memorials for Lemmy / Fediverse users who have passed away. Cross-posted across multiple instances (Piefed, Blåhaj Zone, etc.).

What is notable for this repo:

- A fediverse memorial community exists *because* mainstream platforms do not handle user death well. The gap the community fills is the same gap `one-among.us` fills for Chinese-speaking trans users, and the same gap the existing r/DeadRedditors fills on Reddit.
- The community is small and federated; the API is closed to non-authenticated requests, and the community is on instances that require accounts. The case file behind `prompts/10-when-reading-suicide-notes.md` is a single Chinese-language site; this is the English-language fediverse equivalent, with a different shape (subreddit vs. memorial site) and a similar ethical load.

### Mastodon `memorial` attribute (proposed in 2023, federated in 4.2)

A long-standing proposal to allow admins to mark a profile as "in memoriam" with customizable text, color, and badge. The current implementation: a profile can be marked as memorial; the message "In Memoriam" is shown; federation of the attribute was added in Mastodon 4.2 (referenced PR #26583).

What is notable for this repo:

- The proposal explicitly notes that the default "In Memoriam" text "does not translate well into all cultures and languages. Many would probably prefer 'RIP', 'Legacy account', 'in memory of {username}'." The right answer here is per-instance customization — which is a hard problem at the protocol level, since instances need to agree on what attributes mean.
- The same proposal notes that the current marker is "not visible enough in both profile page and in conversations." Visibility is a design problem, not a data problem. The marker exists; the marker is not seen.

## What does not exist (as of this search)

- A `WhisperPaw`-equivalent: a *cross-OS terminal a11y toolkit* with deliberate sound-pack design, sentence-aware chunking, and a real TTS path. The closest is `leavesofgrass/star`, which is a desktop reader, not a terminal toolkit. The gap is real and small enough to be worth closing.
- A *cross-platform memorial archive protocol*. Each memorial site is its own stack (Flarum for `one-among.us`, hand-rolled for many others). The data is not portable. The "user passes away" event is the one where portability matters most.
- A *conversational-agent a11y spec*. There is no document, that this search found, that says "when a chatbot is talking to a user with print disability, do X." The closest is the W3C ARIA Authoring Practices Guide, which is for web content, not for conversational agents.

## What to do with this note

- It is the *context* note for the repo. It tells the next maintainer what other work is happening in the same space.
- It also gives the next maintainer a place to add more entries as they find them. Each new entry should answer: "what is this, what does it do, what is the case file behind it (if any), what is the gap it does not close?"
- The gap list at the end ("what does not exist") is a hint at where the next project in this space could be. It is not a roadmap.
