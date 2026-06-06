# First-Run Setup

Ask these one topic at a time, then save the answers to `~/.config/meeting-briefings/config.md`. Keep it conversational; the goal is to learn the user's tools once so every later run is fast and quiet. Do not save this config in the current project folder because it may contain personal calendar, account, and destination preferences.

1. **User identity.** The user's display name and email aliases to remove from attendee lists.
2. **Calendar source** and how to reach it. Do not assume the obvious calendar is the right one. Work and personal items often live in different accounts, and a desktop app may aggregate accounts that a browser view does not. Confirm a day with real meetings actually shows them before relying on a source. Save the timezone and default day fallback rule.
3. **Which meetings count.** Default to events with at least one external human attendee. Save include and exclude rules, such as external-only, skip solo focus blocks, skip personal items, skip all-day events, skip declined events, and how to treat tentative events.
4. **Context sources.** Where to look for what the user already knows about an attendee: past notes, a CRM, email threads, LinkedIn messages, saved memory, and prior session transcripts if the host exposes them. Save which sources are enabled and the search order. A memory file or index is a starting point, not the whole record. The richer history usually lives in past session transcripts, so do not conclude "nothing on file" from the index alone. If transcripts cannot be searched in bulk, read the most relevant recent ones and say plainly what was and was not checked.
5. **LinkedIn/profile lookup.** Ask whether to enable attendee profile lookup for future meeting briefings, confirm the lookup scope, and confirm the user is signed in wherever the lookup happens. Scope examples: profiles only, profiles plus DMs, profiles plus recent posts/activity. Make clear it reads only profiles and conversations the user already has access to under their own account. It does not scrape or store anyone else's private data. If the user approves only the current run, use it once but save the config as unconfigured or one-time-only so future runs ask again.
6. **Fallback behavior.** What to do when profile lookup or a context source is unavailable: ask, continue calendar-only, or omit the profile/background section.
7. **Output.** Where the briefings go: a dated file in a folder, a notes app, a message to self, or just shown in the chat. Save format and destination. Explain that sending, posting, or writing to an external service requires explicit confirmation at delivery time.
8. **Timing.** On demand, or a recurring morning task. If recurring, save the schedule, timezone, and host scheduler, then hand off to the host's scheduler rather than building one here.

Do not store cookies, tokens, profile contents, attendee research, message excerpts, or other harvested personal data in this config. Store preferences and source locations only.

## Config Template

```markdown
# Meeting Briefings config

Runtime environment: <agent, and the tools detected for calendar, LinkedIn, and files>
User identity:
  Name: <display name>
  Email aliases:
    - <email>
Calendar:
  Source: <how to read the calendar>
  Timezone: <default timezone>
  Default day fallback: <today / next business day / ask>
Meetings:
  Include rules: <external meetings only, humans only, etc.>
  Exclude rules: <internal, solo blocks, personal, all-day, declined, tentative, etc.>
Context sources:
  Search order:
    - <source name>
  Sources:
    - Name: <source>
      Status: <enabled / disabled>
      Access: <how to reach it>
LinkedIn/profile lookup: <enabled / disabled / unconfigured / one-time-only>
Profile source: <LinkedIn or other source, where the user is logged in>
Profile scope: <profiles only / profiles and DMs / profiles and recent posts>
Fallback if source unavailable: <ask / calendar-only / omit background>
Output:
  Destination: <chat / dated file / notes app / message to self>
  Format: <markdown / plain text>
  Location: <folder, note, or app target>
Timing:
  Mode: <on demand / recurring morning task>
  Schedule: <time and weekdays, if recurring>
  Scheduler: <host scheduler or automation tool>
External delivery confirmation: required unless explicitly approved for the current run
Last updated: <date>
```
