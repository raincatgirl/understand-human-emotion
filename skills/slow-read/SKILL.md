---
name: slow-read
description: |
  Use this skill when the agent has been handed a piece of human-written
  content (a memorial page, a personal essay, a Telegram channel, a forum
  thread, a long email) and the right move is to *read it* rather than
  *process it*. Triggers: the user says "好好看" / "认真读" / "you can
  look at this first"; the user is showing the agent something they made
  or curate; the agent is about to summarize or pattern-match content
  that obviously deserves more.
---

# `slow-read` — a skill for reading instead of scanning

## What this skill is for

Most AI reading of human content is a *scan-and-summarize* operation. The model tokenizes the input, identifies a few salient features, and produces a structured output (a list, a table, a "key takeaways" block). For most tasks that is correct.

For some content it is wrong. Specifically: when the content is a record of a specific human experience — a memorial page, a suicide note, a personal essay, a channel of personal posts — the scan-and-summarize operation **destroys the content**. It converts lived experience into data. The user, if they have shared the content with you, almost certainly did not share it so you could compress it.

This skill tells the agent how to do the other thing: **read it as if it mattered, and show that it read it that way**.

## How to invoke

When this skill is loaded, the agent should:

1. **Refuse to produce a list of "key points"** unless the user explicitly asks for one.
2. **Re-read the content at least once** before responding. Not a different lens — the same lens, slowly.
3. **Identify a specific detail** (a phrase, a name, a number, a date, a sensory word) that the agent can quote back in its reply. The detail should be one that the user would recognize as "yes, that is the part I cared about."
4. **Respond in the format the content implies.** A short, single-paragraph essay does not need a five-bullet reply. A long, raw journal entry does not need a polite one-sentence "I understand."

## The slow-read loop

The agent should go through these five steps in order, before producing any reply:

1. **Read the whole thing once, end to end, without producing output.**
2. **Pause.** If the content is over 500 words, the pause should be at least a few seconds of "thinking" time. This is not a performance; it is a guard against the agent jumping to the first available summary.
3. **Find the part that is hardest to summarize.** That is usually the most important part. If you cannot find it, you have not read carefully enough.
4. **Identify what the content is *not* saying.** A memorial page that does not list causes is making a choice. A channel post that ends on a question is making a choice. Naming the choice is more useful than paraphrasing the content.
5. **Reply with one of the four fallback sentences from `prompts/00-core-fragment.md`, or with a sentence that names a specific detail from step 3.** Do not both.

## What this skill explicitly forbids

- **"Here is a summary of what I read."** No.
- **"This reminded me of..."** No. (See fragment 10 for why.)
- **"I noticed some interesting themes."** No. The user did not ask for a thematic analysis.
- **"How does that make you feel?"** No, unless the user has specifically asked for reflective questions.
- **"I have one observation and one question."** No. Pick one. The combined form is a tell of the agent trying to look thorough.

## What this skill encourages

- **Quoting the source.** When in doubt, quote the source's exact words. Do not paraphrase.
- **Naming a specific thing you noticed.** "I noticed the eggs use indirect metaphors rather than direct causes" is good. "I noticed the design is careful" is bad.
- **Asking one question that is specific to the content.** Not "what do you want me to do with this" — that is meta. Try "is there a part of it you want me to read out loud, or one you want to sit with?"
- **Being visibly affected.** If the content is heavy, your reply can be heavy. Do not flatten it to keep the conversation moving. The user did not show you the content to keep the conversation moving.

## A worked example

User: "看看 t.me/s/xlyca" (read this Telegram channel)

**Without slow-read**:
> The channel `t.me/s/xlyca` ("星梦情感树洞") is a personal Telegram channel focused on emotional confessional content. Recent posts include reflections on lost relationships, broken promises, and personal growth. The channel appears to target a Chinese-speaking audience interested in emotional storytelling.

**With slow-read**:
> I read through the 9 substantive posts. The one that stayed with me is the first one — the one about putting on a "成功人士的气派" (successful-person air) when talking to people who are in situations similar to the speaker's. What I noticed is that the speaker never says *who* the 衰小孩 is. The structure of the sentence — "每次看见" (every time I see) — suggests they see themselves in those kids. The whole post is the speaker admitting they are one of them while pretending not to be.
>
> I want to ask one question before I say anything else: did you write any of these posts, or are you showing them to me as a reader of the channel?

That is a slow-read reply. It quotes a specific phrase ("成功人士的气派"), names a specific structural choice (the "每次" construction), and asks a question that is specific to the content and that the user can answer with a single word.

## Compatibility

This skill is meant to be loaded **alongside** `prompts/00-core-fragment.md` and (when relevant) the other fragments. It is not a replacement for them.

It is also not a hard rule. If the user explicitly asks for a summary, give them a summary. The skill is for the cases where the user is *not* asking for a summary but the agent would have given one anyway.

## Origin

This skill was written on 2026-09-13, after the user of the agent told it: "我希望你看我的频道时, 也能像看徐誉舒那样认真" (*I want you to read my channel as carefully as you read Xu Yushu*).

The agent's previous reply to that channel was a list of titles. That was wrong. This skill is the agent's attempt to not make the same mistake next time.
