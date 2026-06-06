# First-Run Setup

Ask these one topic at a time, then save the answers to `~/.config/meeting-briefings/config.md`. Keep it conversational; the goal is to learn the user's tools once so every later run is fast and quiet. Do not save this config in the current project folder because it may contain personal calendar, account, and destination preferences.

1. **Calendar source** and how to reach it. Do not assume the obvious calendar is the right one. Work and personal items often live in different accounts, and a desktop app may aggregate accounts that a browser view does not. Confirm a day with real meetings actually shows them before relying on a source.
2. **Which meetings count.** Default to events with at least one external human attendee. Skip solo focus blocks, personal items, and all-day events unless the user says otherwise.
3. **Context sources.** Where to look for what the user already knows about an attendee: past notes, a CRM, email threads, LinkedIn messages, saved memory, and prior session transcripts if the host exposes them. A memory file or index is a starting point, not the whole record. The richer history usually lives in past session transcripts, so do not conclude "nothing on file" from the index alone. If transcripts cannot be searched in bulk, read the most relevant recent ones and say plainly what was and was not checked.
4. **LinkedIn/profile lookup.** Whether to look attendees up, and confirm the user is signed in wherever the lookup happens. Make clear it reads only profiles and conversations the user already has access to under their own account. It does not scrape or store anyone else's private data.
5. **Output.** Where the briefings go: a dated file in a folder, a notes app, a message to self, or just shown in the chat. Explain that sending, posting, or writing to an external service requires explicit confirmation at delivery time.
6. **Timing.** On demand, or a recurring morning task. If recurring, hand off to the host's scheduler rather than building one here.

## Config Template

```markdown
# Meeting Briefings config

Runtime environment: <agent, and the tools detected for calendar, LinkedIn, and files>
Calendar source: <how to read the calendar>
Meetings to include: <filter rule>
Context sources:
  - <source and how to reach it>
LinkedIn/profile lookup: <yes/no, where the user is logged in>
Output: <destination and format>
Timing: <on demand / recurring morning task>
External delivery confirmation: required unless explicitly approved for the current run
Last updated: <date>
```
