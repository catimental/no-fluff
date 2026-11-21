# no-fluff

A Claude Code skill that removes fluff from what Claude writes: docs, release notes, comments, commit messages, and the text on a screen.

`no-fluff-writing` makes a sentence state what a thing is or what it does.

- Verbs name the actual operation. No metaphor, no marketing voice.
- Software is not described as alive. "The parser swallows the error" becomes "The parser does not report the error."
- No em-dash asides. An aside becomes the next sentence.
- Nothing is said twice.
- Adjectives without a measurement are deleted.
- On a screen, a label does not repeat its heading, and a line under a control stays only if it states a fact the control cannot show.

The skill decides words only. It does not decide which controls, sections, or buttons a screen has.

A Korean appendix (`ko.md`) adds Korean registers and phrases.

## Test results

Each prompt was run in fresh Claude Sonnet contexts, one sample per context, with and without the skill.

### Screen text

Prompt: a notification settings section, an empty project list, and a "settings saved and synced" toast. 3 English and 2 Korean samples without the skill, 2 English and 2 Korean with it.

| Pattern | Without skill | With skill |
|---|---|---|
| Helper line that rephrases its label | 5 / 5 | 0 / 4 |
| Label repeats the heading ("Email notifications" under "Notifications") | 5 / 5 | 0 / 4 |
| Description line under the section heading | 4 / 5 | 0 / 4 |
| Explanation paragraph in the empty state | 5 / 5 | 0 / 4 |
| Invented facts (a digest schedule the prompt did not give) | 5 / 5 | 0 / 4 |

When the prompt gave three facts (digest schedule, what quiet hours mute, overnight ranges), 2 / 2 samples with the skill placed each fact next to the item it is about.

`examples/compare.html` renders the generated screens side by side.

```html
<!-- Without the skill (shortened) -->
<h2>Notifications</h2>
<p>Choose how and when you hear about activity in your projects.</p>
<label>Email notifications</label>
<p>Get emails about assignments, mentions, and due dates.</p>
<label>Push notifications</label>
<p>Receive alerts on your devices when something needs your attention.</p>

<!-- With the skill, facts given in the prompt -->
<h2>Notifications</h2>
<label>Email</label>
<label>Push</label>
<label>Weekly digest</label>
<p>Sent every Monday at 9:00.</p>
```

### Prose

With a plainly worded prompt (release notes and a doc comment), Sonnet already wrote plain text without the skill in 4 / 4 samples.

With a prompt that asked for engaging copy ("make it engaging, people should be excited to update!!"), the results split. 2 English and 1 Korean samples per arm.

| Pattern | Without skill | With skill |
|---|---|---|
| Hype or figurative phrases ("feel the difference", "from the ground up", "travels with you") | 3 / 3 | 0 / 3 |
| Claims without a measurement ("faster than ever", "easy on the eyes") | 3 / 3 | 0 / 3 |

```text
Without the skill:
  Search is rebuilt from the ground up. Results appear in under 200 ms,
  which feels less like searching and more like remembering.

With the skill:
  Search is rebuilt. Results return in under 200 ms on 10,000 notes.
```

With the skill, Claude states the facts and tells you that an energetic tone conflicts with the skill. If you want promotional copy, say so or turn the skill off for that task.

The sample counts are small. Treat the tables as a demonstration, not a benchmark.

## Install

As a plugin:

```
/plugin marketplace add catimental/no-fluff
/plugin install no-fluff@no-fluff
```

Or copy `skills/no-fluff-writing/` into `~/.claude/skills/`.
