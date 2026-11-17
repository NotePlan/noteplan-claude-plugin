---
name: review-tasks
description: Review tasks in NotePlan over a week or in a project note. Use for a weekly review, for cleaning up overdue or unfinished tasks, and for moving many tasks to new dates.
---

# Review tasks in NotePlan

## Weekly review

1. Call `list_tasks` for each day of the week under review (`YYYY-MM-DD`) and for the weekly note (`YYYY-Www`), with `status: "all"`.
2. Report in three short parts: done, still open, cancelled. Name the day for each open task.
3. For the open tasks, ask the user what to do with each one, or with all of them: move to a day, move to next week (`YYYY-Www`), cancel, or leave.
4. Apply the answers with `reschedule_task` or `cancel_task`, one call per task. Work from the last line to the first line of a note, so the line numbers of the remaining tasks stay correct, or use `text`.
5. Finish with a short summary of what changed and what stays open.

## Tasks of a project

1. Find the note: `search_notes` with the project name and `within: "title"`, or `list_notes` with `folder`.
2. Call `list_tasks` with the note's exact `filename`.
3. Show open tasks under their headings.
4. To put a project task on a day, call `reschedule_task` with `to`. From a project note this only adds a date link, so the task stays in the project and also shows on that day.

## Show a note

- When the user wants to see or read a note, call `show_note` with its exact `filename`, or with `date` for a calendar note. It shows the note as formatted text that the user can scroll, open larger and check tasks off in. Do not repeat the note in your answer.
- When you only need the text for your own work, use `get_note` or `get_calendar_note`: they show nothing in the chat.

## Rules

- Never use `replace_in_note` to complete, cancel, reopen or reschedule a task. The task tools keep done dates, scheduled copies and synced lines correct.
- Ask before you change more than five tasks in one step. List them first.
- Checklist items (`+` lines) are included by default. Set `includeChecklists: false` when the user wants tasks only.
- For a NotePlan Space, pass `space` (name or id from `list_spaces`). Changes in a Space reach all its members, so say this before the first change.
