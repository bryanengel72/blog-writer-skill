---
name: blog-writer
description: "Write a complete, publish-ready blog post on any topic. Use this skill whenever the user asks to write, draft, or create a blog post, article, or long-form content. Trigger on phrases like 'write a blog post', 'draft an article', 'write something about', 'create a post on', or any time someone provides a topic and wants it turned into a complete blog post. Always use this skill -- do not just freeform a blog post."
---

# Blog Writer

Turns a topic, a few notes, or a rough idea into a complete, publish-ready blog post.

---

## How to Use This Skill

**What you provide:**
- A topic or working title
- Optional: target audience, tone preference, word count target
- Optional: any notes, angles, or points you want included

**What this skill delivers:**
- A complete blog post with title, intro, body, and conclusion
- A suggested meta description (for SEO)
- A session log entry (see `logs/history.md`)

---

## Config

Read `config.json` before writing. It stores your default preferences so you do not have to repeat them every session.

If `config.json` does not exist yet, ask the user these questions once, then create it:

1. What is your name or brand? (used in author voice)
2. Who is your primary audience?
3. What tone do you default to? (conversational / authoritative / educational)
4. What is your typical target word count? (default: 800)
5. Do you have any topics or words you want avoided?

---

## Writing Rules

**Voice first.** Write like the author has actually done the thing. Avoid summarizing knowledge from the outside. Use "I" where natural.

**Hook in the first sentence.** No preamble. No "In today's world..." Start with the claim, the story, or the surprising fact.

**Earn every claim.** If you assert something is true, ground it with a number, a named example, or a specific observed behavior. No vague gestures toward "trends."

**Short paragraphs.** Two to four sentences max. White space is not wasted space on the web.

**End with something.** Not "I hope this was helpful." End with a provocation, a next step, or a question worth sitting with.

---

## Banned Words and Phrases

Do not use these. They are statistical fingerprints of AI-generated content:

- delve, tapestry, pivotal, nuanced (overused), underscore (as verb)
- leverage (as verb), seamlessly, robust, transformative, revolutionize
- "it is important to note", "in today's fast-paced world"
- "not just X, but Y" negative parallelism
- "game-changer", "unlock the potential of", "moving forward"
- "in conclusion" as a section opener
- "overall" as a paragraph opener
- Any closing platitude ("I hope this was helpful", "feel free to reach out")

When in doubt: cut the word. The sentence is almost always stronger without it.

---

## Gotchas

These are real failure patterns. Read this section before writing every post.

- **Intro drift.** The first paragraph often becomes a wind-up instead of a hook. If the first sentence could be deleted without losing anything, delete it and start with the second.
- **The three-item default.** AI defaults to listing exactly three things. If your post has a list, count the items. If it is three by habit rather than by logic, add one or cut one.
- **Weak conclusions.** The closing paragraph is often the blandest. Write it first as a forcing function, then write toward it.
- **False authority voice.** Phrases like "experts agree" or "studies show" without a specific citation. Name the expert. Name the study. Or cut the claim.
- **Over-formatted body.** Not every post needs H2 subheadings and bullet points. If the post is under 600 words, prose usually reads better than a formatted outline.

For more patterns discovered over time, read `references/gotchas.md`.

---

## Memory

After delivering every post, append a one-line entry to `logs/history.md`:

```
[DATE] | [TOPIC] | [WORD COUNT] | [TONE] | [NOTES]
```

Example:
```
2026-06-06 | Why AI skills are folders not files | 620 | conversational | user wanted shareable LinkedIn angle
```

This lets you say "have I written about this before?" and get a real answer.

---

## Output Format

1. Post title (H1)
2. Meta description (one sentence, under 155 characters, in italics)
3. Full post body
4. Word count

---

## Reference Files

- `references/gotchas.md` -- growing list of failure patterns; read when a post feels off
- `references/seo-basics.md` -- lightweight SEO rules for titles, meta descriptions, and headings
- `logs/history.md` -- running post log; check before writing to avoid topic overlap
- `config.json` -- user preferences; read at session start
