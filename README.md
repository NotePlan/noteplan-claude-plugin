# NotePlan for Claude

This plugin connects Claude to [NotePlan](https://noteplan.co), the markdown planner for notes, tasks and your calendar. Claude can read, search and edit your notes, show your tasks as a checklist, check tasks off, move them to another day, and help you plan your day or review your week.

## What is in the plugin

- **The NotePlan connector** (`.mcp.json`): the remote MCP server `https://mcp.noteplan.co/mcp`. It runs on NotePlan's server, so your Mac does not need to be on.
- **Three skills** that tell Claude how to work with NotePlan:
  - `plan-my-day`: today's open tasks as a checklist, plus the tasks of the week, and a proposed order for the day.
  - `review-tasks`: a weekly review, or the tasks of a project note, and moving many tasks to new dates.
  - `capture-to-noteplan`: add a task, a bullet, meeting notes or a summary of the chat to the correct note.

## What you need

- NotePlan with **CloudKit** sync (NotePlan > Settings > Sync), and **Advanced Data Protection** off for the Apple ID.
- Or a NotePlan **Space**. For Spaces alone you sign in with your Spaces email and a one-time code.

## Sign in

When Claude first uses the connector, a NotePlan page opens. Choose **Sign in with Apple** or **Sign in with email (Spaces only)**. The Apple ID sign-in is on Apple's own page; NotePlan never sees your password.

## Try it

- "Show my open NotePlan tasks for today and help me plan the day."
- "Check off the tasks I finished today in NotePlan."
- "Review my tasks of this week and move the open ones to next week."
- "Save a summary of this chat as a new note in NotePlan."

## Your data

The plugin itself sends nothing. The connector sends the tool requests of Claude (for example a note name, a date or the text to add) to `mcp.noteplan.co`, which reads and writes your notes in your iCloud database or in your Space. The server does not store your notes on disk. It keeps your sign-in session in encrypted form and logs which tool ran, never your note text. Every change syncs to NotePlan on all your devices, and removed notes go to the NotePlan Trash.

Privacy policy: https://noteplan.co/privacy (section "Remote AI Connector").

## Support

hello@noteplan.co or https://help.noteplan.co

## License

MIT, see [LICENSE](LICENSE). This covers the files of this plugin. NotePlan and the NotePlan server are not part of it.
