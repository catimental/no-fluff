---
name: no-fluff-writing
description: Use when writing any text a person will read (docs, READMEs, release notes, changelogs, code comments, commit messages, chat explanations) or the text on a screen (headings, labels, buttons, helper text, empty states, toasts in an HTML page, web UI, dashboard, form, or artifact), or when text reads as marketing, poetic, literary, or padded, leans on em-dash asides, describes software as if it were alive, or a screen repeats its headings in labels and helper lines.
---

# No-fluff writing

A sentence states what a thing is or what it does. It does not decorate, persuade, or perform.

If the text is Korean, also read `ko.md` in this folder. It adds Korean registers and a Korean phrase table.

## Sentence contract

Every sentence has this shape. If it does, it is right. If it does not, rewrite it.

- **Verbs name the actual operation.** Save, delete, load, send, return, retry, skip, turn off. Use the system's own nouns and verbs. No metaphor, no poetry, no literary or marketing voice.
- **When the subject is a thing, the verb is what happens to it.** Code, data, features, and services do not wait, sleep, wake up, breathe, swallow, or come alive. "The parser swallows the error" becomes "The parser does not report the error."
- **One sentence carries one point.** An aside does not hang off an em dash ("Sync is faster — up to 3x on large vaults"). It becomes the next sentence. Two complete sentences on one line are fine.
- **Nothing is said twice.** A sentence that restates the one before it, a heading that the first line repeats, and a closing summary of what was just said are deleted.
- **Numbers carry units and come from the source.** "3 seconds", "12%". No invented totals, ranges, or examples the source does not contain.
- **Claims are checkable.** "Faster search" becomes "Search returns results in under 200 ms on 10,000 notes" if the number exists, and "Search is faster" if it does not. Adjectives without a measurement are deleted.

## Screen text

This section decides the words on a screen. The controls, sections, buttons, validation, and default values of the screen are decided elsewhere and stay as they are.

Each piece of screen text is one of these:

- **Heading:** a noun phrase in sentence case that names the section. "Quiet hours".
- **Label:** the name of one value, without the words its heading already carries. Under "Notifications" the labels are "Email" and "Push".
- **Button:** the verb of the action, with its object when the verb alone is unclear. "Save", "Create project", "Try again".
- **Fact line:** a sentence that states something the heading, label, and control cannot show: a schedule, what a setting does not affect, a constraint, a time zone, how an edge case is handled. The fact comes from the task, the code, or the spec. An item with no such fact has no fact line. The line sits next to the item it is about. A line that only rephrases its label or heading is not a fact line and is deleted.
- **Status text** (toast, notice, empty state, error): a plain declarative sentence that states what happened or what is there. "Settings saved." "No projects." No exclamation marks, no emoji.

A state that turns on and off has one pair of names ("On / Off" or "Enabled / Disabled") across the whole screen.

```html
<!-- Before -->
<p class="eyebrow">Peace of mind</p>
<h2>Backup Settings</h2>
<p>Keep your work safe. Choose how your data is backed up below.</p>
<label>Automatic backup <small>Automatically back up your data</small></label>
<label>Backup location <small>Where your backups are stored</small></label>
<button>Save changes</button> <button>Reset</button>

<!-- After: same controls, fewer words. The spec says backups run daily at 02:00. -->
<h2>Backup</h2>
<label>Automatic <small>Runs daily at 02:00.</small></label>
<label>Location</label>
<button>Save</button> <button>Reset</button>
```

## Phrases to replace

| Do not write | Write |
|---|---|
| delve into · dive into · explore | read · look at · cover |
| seamless · effortless · robust · powerful · cutting-edge | (delete, or state the measurement) |
| unlock · supercharge · elevate · empower · level up | (name the feature, or delete) |
| a testament to · a tapestry of · the landscape of | (delete) |
| It's worth noting that · It's important to remember | (delete, state the fact) |
| Not just X — it's Y | X. It also does Y. |
| In today's fast-paced world | (delete) |
| Whether you're A or B, … | (delete, or name who it is for) |
| The function wakes up · the queue breathes · the cache remembers | The function starts · the queue drains · the cache stores |
| Happy coding! · Enjoy! · 🎉 | (delete) |
| Your journey starts here · Let's get started! | Create project · Start |
| Nothing to see here (yet)! · It's lonely in here | No projects. |
| All set! Your changes are live | Settings saved. |
| This is where you can manage… · In this section you can… | (delete) |

Phrases not in the table are judged by the contract. Words for real physical position or motion ("the panel at the top", "drag the file") are fine.

## Review pass
1. Find every em dash. Split each into two sentences.
2. Read every sentence whose subject is a thing. If the verb is something a person or animal does, replace it with what happens to the thing.
3. Delete each sentence and see whether the text loses information. If it does not, leave it deleted. On a screen, apply this to each line under a heading or beside a control.
4. Find every adjective of quality (fast, easy, powerful). Replace it with a measurement or delete it.
5. On a screen, read each label together with its heading. Remove the words they share from the label.
