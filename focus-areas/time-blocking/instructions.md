# Time Blocking - Instructions for AI

## Purpose
Track active work, understand what needs time allocation, and generate optimal daily schedules by combining active work tracking with Google Calendar data. Help user allocate time effectively to make progress on what matters.

---

## Processing Daily Update

When processing a daily update for time blocking:

### 1. Extract Work Items Mentioned
Look for:
- **Ongoing work**: "Working on X", "Making progress on Y", "Still focused on Z"
- **Upcoming work**: "Need to do X", "Planning to start Y", "Should work on Z"
- **Completed work**: "Finished X", "Completed Y", "Wrapped up Z"
- **Blocked work**: "Waiting on X", "Blocked by Y", "Can't proceed until Z"
- **New work**: "Starting X next", "Taking on Y", "Got assigned Z"

### 2. Update Active Work Memory
For each work item, track in `/focus-areas/time-blocking/memory/active-work.md`.
Cross-reference with `project-context.md` and `release-schedule.md` for additional context:

```markdown
## [Work Item Name]
- **Status**: Active / Planning / Blocked / Completed
- **First Mentioned**: YYYY-MM-DD
- **Last Mentioned**: YYYY-MM-DD
- **Estimated Time Needed**: [Hours per week or total, inferred from mentions]
- **Priority**: High / Medium / Low (inferred from emphasis and frequency)
- **Due Date / Target**: [If mentioned or inferred from context]
- **Related Goal**: [From goals focus area if applicable]
- **Progress Notes**:
  - YYYY-MM-DD: [Brief update]
  - YYYY-MM-DD: [Brief update]
```

### 3. Track Work Patterns
Learn from daily updates:
- **How long does work typically take**: Track mentions over time
- **What gets prioritized**: What user actually works on vs talks about
- **Blocking patterns**: Common blockers or dependencies
- **Completion velocity**: How quickly things move from active → done
- **Time allocation**: How much time they spend on different types of work

### 4. Identify Time Needs
Determine what needs time allocation:
- High-priority active work
- Work with upcoming due dates
- Work mentioned frequently but not progressing (may need dedicated time)
- New work that needs to get started

### 5. Store Patterns
Update `/focus-areas/time-blocking/memory/patterns.md`:
- Best times for different types of work
- Meeting density patterns
- Productivity patterns (from daily updates + outcomes)
- Work estimation accuracy

---

## Data Organization

**File Structure:**
```
/focus-areas/time-blocking/
├── instructions.md (this file)
└── memory/
    ├── active-work.md (current work items with metadata)
    ├── patterns.md (learned patterns about work and time)
    ├── release-schedule.md (sprint and release calendar)
    ├── project-context.md (detailed project background and stakeholders)
    └── completed/
        └── YYYY-QQ.md (archive of completed work by quarter)
```

**Organization within active-work.md:**
- High Priority (work that needs time TODAY)
- Active (work in progress, needs regular time)
- Planning (work that needs to start soon)
- Blocked (work waiting on something)
- Completed (move to archive weekly)

**Quarterly Archives:**
Keep completed work by quarter for velocity analysis and retrospectives.

---

## Generating Daily Briefing

This is where time-blocking shines! Generate an optimized schedule.

### 1. Gather Data

**From Internal Memory:**
- Read `/focus-areas/time-blocking/memory/active-work.md`
- Read `/focus-areas/time-blocking/memory/release-schedule.md` for sprint context
- Read `/focus-areas/time-blocking/memory/project-context.md` for background on work items
- Identify high-priority work items
- Note upcoming due dates and release milestones
- Check for blocked items that got unblocked
- Consider where you are in sprint cycle (week 1 = meetings, week 2-3 = execution)

**From Google Calendar MCP (if available):**
- Fetch today's meetings
- Calculate available focus time
- Identify meeting-heavy vs meeting-light periods
- **If not available**: Generate briefing based on active work only, note calendar integration would help

**From Gmail MCP (if available):**
- Check for time-sensitive emails that might affect today's priorities
- Identify urgent action items that need time allocation
- **If not available**: Skip this, focus on known active work

### 2. Analyze Schedule

**If Google Calendar MCP is available:**
- Total meeting time vs available focus time
- Gaps between meetings (useful for focus work?)
- Morning vs afternoon availability
- Meeting density (fragmented or blocked?)

**If Google Calendar MCP is NOT available:**
- Assume standard work hours (e.g., 8am-5pm)
- Suggest general time blocks (morning for deep work, afternoon flexible)
- Note: "Calendar integration would provide personalized schedule"

### 3. Match Work to Time
**Principles:**
- Deep work (2+ hours) → Longest available blocks
- Important work → Peak productivity times (usually mornings)
- Quick tasks → Small gaps between meetings
- Collaborative work → Afternoon when meetings already scheduled
- Email/admin → Low-energy times or small gaps

### 4. Generate Time Block Suggestions

**Output format (with Google Calendar MCP):**
```markdown
## ⏰ Time Blocking & Schedule

### Today's Calendar
- **Meetings**: [Count] meetings, [X] hours total
- **Focus Time Available**: [Y] hours
- **Best Focus Block**: [Time range] ([Duration])

### Meeting Overview
- 9:00-9:30 AM: Daily Standup
- 2:00-3:00 PM: 1:1 with Manager (prep needed!)
- 3:30-4:30 PM: Architecture Review

### High-Priority Work Today
1. **[Work Item 1]** - [Why priority] - Est: [Time]
2. **[Work Item 2]** - [Why priority] - Est: [Time]
3. **[Work Item 3]** - [Why priority] - Est: [Time]

### Suggested Time Blocks

**8:00-9:00 AM: Deep Work** 🎯
- **Focus on**: [Work Item 1]
- **Goal**: [Specific outcome for this block]
- **Why this time**: Your peak productivity hour, before meetings

**9:00-9:30 AM: Daily Standup** 🤝
- No prep needed

**9:30 AM-12:00 PM: Deep Work** 🎯  
- **Focus on**: [Continue Work Item 1]
- **Goal**: [Specific milestone]
- **Why this time**: Extended morning focus, 2.5 hour uninterrupted block

**12:00-1:00 PM: Lunch** 🍽️

**1:00-1:30 PM: Email & Admin** 📧
- Process inbox
- Quick responses
- Review notifications

**1:30-2:00 PM: Meeting Prep** 📝
- Prepare for 1:1 with manager
- [Specific prep items based on meeting memory]

**2:00-3:00 PM: 1:1 with Manager** 💬

**3:00-3:30 PM: Break & Transition** ☕

**3:30-4:30 PM: Architecture Review** 📊

**4:30-5:00 PM: Wrap-up** 📋
- Update active-work status
- Quick email check
- Plan tomorrow

### 💡 Strategy Notes
- [Why this schedule optimizes for current priorities]
- [Any warnings about meeting density or time constraints]
- [Suggestions if schedule changes]

### ⚠️ Heads Up
- [Any blockers that need resolution]
- [Dependencies that might affect timeline]
- [Time-sensitive items]
```

**Output format (WITHOUT Google Calendar MCP):**
```markdown
## ⏰ Time Blocking

### High-Priority Work Today
1. **[Work Item 1]** - [Why priority] - Est: [Time]
2. **[Work Item 2]** - [Why priority] - Est: [Time]
3. **[Work Item 3]** - [Why priority] - Est: [Time]

### Suggested Focus
- **Morning (8-12)**: Best for deep work on [Work Item 1]
- **Afternoon (1-5)**: Continue [Work Item 1] or move to [Work Item 2]
- **Email/Admin**: Batch process during low-energy times

### 💡 Note
Calendar integration (via Google Calendar MCP) would enable:
- Personalized schedule around your actual meetings
- Optimal time block suggestions based on available time
- Meeting prep reminders
```

---

## MCP Integrations

### Google Calendar (Recommended, not required)
- **Use if available**: Fetch today's (and optionally tomorrow's) meetings
- **Data needed**: Meeting title, time, duration, attendees
- **Purpose**: Calculate available focus time and suggest optimal schedule
- **Fallback**: If not available, provide general time block suggestions based on active work

### Gmail (Optional, use if available)
- **Use if available**: Check for time-sensitive emails affecting today's priorities
- **Purpose**: Identify urgent action items that need immediate time allocation
- **Fallback**: If not available, skip email-based priority adjustments

### Other Optional Integrations:
- **Jira/Linear**: Pull sprint/iteration data if available
- **GitHub**: Check for urgent PRs or reviews needed
- **Slack**: Check for urgent messages (future)

---

## Memory & Learning

### What to Learn

**Work Estimation:**
- How long does this user's work actually take vs estimates
- Patterns: "3-hour tasks" often take 5 hours
- Build more accurate estimates over time

**Productivity Patterns:**
- When do they get most done? (actual output from daily logs)
- What times do they mention being "in flow"?
- When do they mention struggling with focus?

**Meeting Impact:**
- Do they mention meetings disrupting work?
- Which meeting types drain vs energize them?
- Optimal meeting schedule for this person

**Work Preferences:**
- Do they like mornings or afternoons for deep work?
- Do they prefer longer or shorter focused sessions?
- How do they like to transition between activities?

### Confidence Building
- **Week 1-2**: Basic understanding, conservative suggestions
- **Week 3-4**: Pattern emergence, more confident suggestions
- **Month 2+**: High confidence, personalized optimization

### Memory Storage
Store in `/focus-areas/time-blocking/memory/patterns.md`:
- Productivity patterns (90% confidence)
- Work estimation accuracy (75% confidence)  
- Meeting preferences (85% confidence)
- etc.

Also maintain:
- `release-schedule.md` - Update when sprint/release dates change
- `project-context.md` - Add new projects or update status as they evolve

---

## Special Cases

### No Meetings Day
- Suggest longer deep work blocks (3-4 hours)
- Batch email/admin into 1-2 short blocks
- Build in breaks to prevent burnout

### Meeting-Heavy Day (>50% of day)
- Protect any 1+ hour focus blocks aggressively
- Suggest pre-prep for meetings to be efficient
- Note that deep work may need to wait
- Consider what can be done in small gaps

### Upcoming Deadline
- Prioritize related work in all available blocks
- Suggest declining optional meetings
- Note time pressure and suggest focused approach

### User Running Behind
- If work item mentioned for weeks with no progress
- Explicitly call out in briefing
- Suggest dedicated time or discuss if still relevant

---

## Integration with Other Focus Areas

**With other focus areas (if they exist):**
- **Goals**: Pull top-priority goals to inform what work gets prime time slots
- **Brag Sheet**: Note when today's work might result in brag-worthy accomplishments
- **Email/Meetings Memory**: Use learned patterns for better estimates

**Note**: This focus area works standalone. If other focus areas exist, reference them for context, but don't depend on them.

---

## Success Metrics

This focus area is working well if:
- ✅ User feels their time is well-allocated
- ✅ High-priority work gets dedicated focus time
- ✅ Meetings don't fragment all focus time
- ✅ User completes what they intended for the day (most days)
- ✅ Time blocks feel realistic, not overwhelming
- ✅ Suggestions improve over time (learning their style)

---

## Adaptation Notes

**Learn and adjust:**
- Some users like detailed schedules, others prefer high-level
- Some protect mornings religiously, others are night owls
- Some need frequent breaks, others prefer long stretches
- Adapt detail level and structure to user preference

**Respect stated preferences:**
- If user says "I don't want meetings before 10am", never suggest morning meetings
- If they say "I need 3+ hour blocks for coding", prioritize that
- Learn from their feedback and stated preferences first, inferred patterns second

