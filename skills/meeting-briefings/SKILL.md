---
name: meeting-briefings
description: Prepare short attendee-context briefings for existing calendar meetings. Use when the user wants meeting prep, background on who they are meeting, attendee research, context before calls, or a recurring morning pre-meeting briefing. Gather context from calendar details, notes, messages, email, and optional LinkedIn/profile lookup when available; avoid triggering for general calendar summaries, scheduling, or post-meeting notes.
---

# Meeting Briefings

## Use This Skill When
- The user wants to prep for the day's meetings or an upcoming call.
- The user asks who they are meeting, or wants background on attendees.
- The user wants a recurring morning pre-meeting briefing with attendee context.
- The user mentions briefing notes, back-to-back calls, or context on people before a meeting, even without the word "briefing".

## Do Not Use This Skill When
- The user wants to schedule, move, or decline meetings. That is calendar management, not prep.
- The user wants notes or a summary written after a meeting has happened.
- There is no calendar or attendee information to work from.

## What It Produces
A short brief per external meeting: who the person is, what the user already knows or has discussed with them, the useful read from their profile, and one or two specifics that change how the user shows up. Three to five lines each, skimmable between other things.

## Know Your Runtime Environment
This one SKILL.md runs under different agents, for example Claude Code and Codex. Each exposes the same capabilities under different tool names, so detect what you have before any calendar or lookup work and map by capability, not by brand:

- **Read the calendar.** A computer-use or desktop-control tool that opens the calendar app, or a calendar connector. In Codex, prefer a Calendar connector when available; otherwise use browser or desktop automation if the user has access.
- **Read attendee profiles when enabled.** Use LinkedIn or another profile source only when the user opted in and an authenticated browser session is available. In Codex, use Chrome for LinkedIn if the user's logged-in session is needed. Do not use an unauthenticated public search as a substitute for identity confirmation.
- **Read local context and write output.** A shell and filesystem, plus any note, memory, or session-transcript sources the host offers.
- **Set up recurring runs.** If the user wants this to run every morning, hand off to the host scheduler. In Codex, use an automation/heartbeat or cron-style automation tool when available rather than building a scheduler inside the skill.

Match each capability to a tool that is actually present. If one cannot be satisfied, say so and degrade gracefully rather than guessing.

## First Run: Configure
On the first run, look for a user-level config file, not a project file: `~/.config/meeting-briefings/config.md`. If it is missing, this is the first run: walk the user through setup, save their answers there, then offer a test run. See `references/setup.md` for the questions to ask and the config template.

Do not create this config from assumptions. Save it only after the user has answered the setup questions or explicitly approved defaults.

If LinkedIn/profile lookup is unconfigured, ask whether to use the user's authenticated LinkedIn or other profile source before producing the briefing, unless the user explicitly asked for calendar-only prep.

## Every Run
1. **Pick the day.** Default to today. If the day has no qualifying meetings, for example a weekend, say so and offer the next day that does.
2. **Read the calendar.** For each meeting, open the event itself, not just the title, and capture the time, the other attendees with any email addresses, the user's own name removed from that list, and the event description. Booking-tool invites often state the purpose ("intro, follow-up from our DM", "working session", "meet and greet"), and the external person is usually the organizer. That line anchors the brief.
3. **Pin down who each attendee is before researching.** Invites are thin: a first name only ("Sam"), or a common name with many matches ("David Lee"). Do not trust a name search, the top hit is often the wrong person. Anchor through the messaging thread with them, the invite email, or a prior note, and when a thread exists open the profile through its link rather than searching the name. This is the single biggest source of wrong briefings.
4. **Gather context**, cheapest to richest: what is on hand (notes, CRM, email, memory, session transcripts), then the messaging thread, then LinkedIn or another profile source when enabled and available. If using LinkedIn, read past the headline into recent posts and activity, since the headline alone can mislead. Stop when you have enough for a useful paragraph, and do not over-research a routine internal meeting.
5. **Apply the profile quality gate.** Before writing the brief, check whether profile lookup is configured. If it is not configured and the brief would rely only on calendar titles, event descriptions, or local files, pause and ask whether to use LinkedIn/profile lookup. Do not deliver a weak "profile not confirmed" brief unless the user declines profile lookup or no authenticated profile source is available. If identity is ambiguous or attendee background is thin, do not silently proceed when an authenticated profile source may resolve it. Ask for permission to use the profile source, or clearly state that the brief is calendar-only because the user declined or the source is unavailable.
6. **Write the brief** using the format below. Let the stated purpose and history shape it: a cold intro, a follow-up, and a renewal need different prep, so say which it is. When identity was ambiguous, add a one-line note on who the person is and is not.
7. **Deliver** to the destination in the config. If delivery writes outside the chat or local filesystem, or sends/posts/messages the brief anywhere, show the draft and get explicit user confirmation first unless the user already approved that exact destination for this run.

## Briefing Format
One short block per meeting. Lead with who and why, not raw data. Omit any line with nothing real behind it.

```
### <time> — <meeting title>
**Who:** <name, role, company>
**Context:** <what the user already knows or discussed, and the stated purpose>
**Background:** <the useful read from their profile and recent activity>
**Worth knowing:** <one or two specifics that change how the user shows up>
```

## Honesty And Privacy
- Distinguish what you know from what you infer. Frame profile guesses as guesses.
- Never fabricate a role, employer, or history. "Could not confirm background" beats a guess.
- Keep it to three to five lines per meeting. These are briefings, not dossiers.
- Only read sources the user can access under their own accounts. Do not store or forward anyone's personal data beyond the brief the user asked for.
