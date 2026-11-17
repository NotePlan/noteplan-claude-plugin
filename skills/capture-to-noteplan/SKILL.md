---
name: capture-to-noteplan
description: Save something to NotePlan. Use when the user wants to add a task, a bullet, meeting notes, a summary of this chat or a new note to NotePlan.
---

# Capture to NotePlan

## Where it goes

- A task or a quick thought with no named note: today's daily note. Call `append_to_note` with `date` = today.
- "Tomorrow", "next week", "in March": the calendar note of that period (`YYYY-MM-DD`, `YYYY-Www`, `YYYY-MM`).
- A named note: find it with `search_notes` and `within: "title"`, then `append_to_note` with its exact `filename`. If several notes match, ask which one.
- A new document (meeting notes, a plan, a summary): `create_note` with `title`, `content` and `folder`. Call `list_folders` first and propose a folder; "" is the top level.
- Under a heading: pass `heading` to `append_to_note`. The heading must exist in the note.

## NotePlan markdown

- Task: `* Call Anna`
- Checklist item: `+ Passport`
- Bullet: `- A point`
- Quote: `> Text`
- Heading: `## Title`
- Scheduled to a day: add `>2026-11-20` at the end of the task.
- Link to another note: `[[Note title]]`
- Tags and mentions: `#project`, `@anna`

Write tasks as short actions that start with a verb. One task per line.

## Rules

- Tell the user which note you wrote to. If the user wants to see the result, call `show_note` for that note.
- Do not create a note that exists. `create_note` fails if the title exists in the folder: append to the note in that case.
- `replace_in_note` changes existing text and can remove it. Use it only when the user asks to change text, read the note with `get_note` first, and copy `oldText` exactly.
- Images and file attachments cannot be added.
