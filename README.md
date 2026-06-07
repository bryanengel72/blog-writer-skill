git clone https://github.com/yourhandle/claude-skills
# Drop the blog-writer folder into your project's .claude/skills/ directory

# blog-writer

A Claude Code skill that turns a topic or rough notes into a complete, publish-ready blog post.

Built as a working example of the skill design patterns Anthropic published in [Lessons from Building Claude Code: How We Use Skills](https://claude.com/blog/lessons-from-building-claude-code-how-we-use-skills).

---

## What It Does

Give Claude a topic. Get back a complete blog post with a title, meta description, and body copy -- written to sound like a person wrote it, not a language model.

First run: Claude asks five setup questions and saves your preferences to `config.json`. Every run after that picks up where you left off.

After each post, a one-line entry is appended to `logs/history.md` so you can ask "have I written about this before?" and get a real answer.

---

## Folder Structure

```
blog-writer/
├── SKILL.md              # Main skill instructions (entry point)
├── config.json           # Your preferences, populated on first run
├── references/
│   ├── gotchas.md        # Growing list of failure patterns
│   └── seo-basics.md     # Lightweight SEO rules for titles and meta descriptions
└── logs/
    └── history.md        # Running log of every post written
```

This structure is intentional. `SKILL.md` is the front door. The reference files load only when needed. The log persists across sessions. This is progressive disclosure -- Claude reads only what it needs, when it needs it.

---

## Installation

1. Clone or download this repo
2. Copy the `blog-writer` folder into your project's `.claude/skills/` directory:

```bash
cp -r blog-writer your-project/.claude/skills/
```

3. Open Claude Code in your project and say:

```
Write a blog post about [your topic]
```

Claude will detect the skill and use it automatically.

---

## Usage

**Minimal:**
```
Write a blog post about why most AI-generated content sounds the same.
```

**With context:**
```
Write a blog post about prompt engineering for a technical audience,
around 600 words, conversational tone. Focus on the gotchas section
pattern from the Anthropic skills post.
```

**Check history:**
```
Have I written about AI writing patterns before?
```

---

## What Makes This Skill Different

Most people build Claude skills as a single markdown file. This skill is a folder, which is how Anthropic builds them internally.

A few things that come from that:

**Gotchas section.** The highest-signal content in any skill is not the instructions -- it is the failure patterns captured over time. This skill has a `Gotchas` section inline in `SKILL.md` for the patterns you always want loaded, and a `references/gotchas.md` for overflow as the list grows.

**Config for session setup.** `config.json` stores your author voice, audience, tone preference, and word count target. You fill it in once. Claude reads it every session.

**Memory via append-only log.** `logs/history.md` tracks every post written. No database, no external service. One line per post, version-controlled with your project.

**Descriptions written for the model.** The frontmatter description tells Claude when to trigger the skill, not what it does for a human reader. That distinction matters for reliable triggering.

---

## Customization

**Add your own gotchas.** When a post comes back with a problem you did not anticipate, open `references/gotchas.md` and add one line describing the failure and the fix. That is how the skill compounds in value over time.

**Update config.json.** Change your default tone, word count, or audience any time by editing the file directly or telling Claude to update it.

**Fork and adapt.** The pattern works for any writing workflow: newsletters, LinkedIn posts, technical docs, case studies. Swap out the writing rules and banned words list for your context.

---

## Contributing

Found a new gotcha? Open a PR and add it to `references/gotchas.md`.

One line. Short, specific, earned from a real failure. That is all.

---

## Background

This skill was built to demonstrate the folder-based skill design pattern described in Anthropic's June 2026 post on how they build and manage Claude Code skills internally. The core idea: a skill is not a file, it is a folder. Instructions, scripts, reference data, and memory all live together. The file system is the architecture.

The post is worth reading before you fork this: [Lessons from Building Claude Code: How We Use Skills](https://claude.com/blog/lessons-from-building-claude-code-how-we-use-skills)
