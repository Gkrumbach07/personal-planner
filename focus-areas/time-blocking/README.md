# Time Blocking Focus Area

> Track active work and generate optimal daily schedules

---

## What This Tracks

- Current work items and what you're actively working on
- Work that needs time allocation
- Upcoming due dates and targets
- Productivity patterns and preferences

---

## How It Works

### During `/daily-update`
- Extracts work items mentioned
- Tracks progress on active work
- Notes what got completed
- Identifies new work starting
- Learns time estimation patterns

### During `/daily-briefing`
- Fetches today's calendar (via Google Calendar MCP)
- Matches high-priority work to available time slots
- Generates optimal time block suggestions
- Respects learned productivity patterns
- Suggests meeting prep time

---

## Files

**`instructions.md`** - Complete instructions for AI

**`memory/active-work.md`** - Current work items being tracked

**`memory/patterns.md`** - Learned productivity patterns and preferences

---

## MCP Integration

**Requires**: Google Calendar MCP server

This focus area uses Google Calendar to:
- See today's meetings
- Calculate available focus time
- Suggest optimal schedule around meetings

Without MCP, it will still track work but won't generate calendar-integrated time blocks.

---

## Customization

Edit `instructions.md` to change:
- How work items are tracked
- Time block generation logic
- What shows in briefings
- Data organization

---

## Tips

- Naturally mention what you're working on in daily updates
- AI learns your work patterns over time
- Time blocks get more personalized as it learns your style
- Edit `patterns.md` to correct AI's learnings

