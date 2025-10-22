# Focus Areas

> Modular tracking systems - each is self-contained and independent

---

## What Are Focus Areas?

Focus areas are **self-contained modules** that each track a different aspect of your work.

### Structure
Each focus area is a subdirectory with:
- **`instructions.md`** (required) - Tells the AI what to do
- **Data files** (your choice) - Organized however makes sense

### How They Work

**During `/daily-update`:**
1. AI reads the focus area's `instructions.md`
2. Follows the "Processing Daily Update" section
3. Extracts relevant info from your update
4. Updates that focus area's data files

**During `/daily-briefing`:**
1. AI reads the focus area's `instructions.md`
2. Follows the "Generating Daily Briefing" section
3. Creates that focus area's briefing section
4. May use MCP integrations (Google Calendar, Gmail, etc.)

**Key Point:** Each focus area is independent - add, remove, or modify without affecting others.

---

## Your Current Focus Areas

Look inside each subdirectory in `/focus-areas/` to see what it tracks.
Each one has its own README explaining what it does.

---

## Creating New Focus Areas

### Quick Start

1. **Create directory**: `mkdir -p focus-areas/[name]`
2. **Write `instructions.md`** (see template below)
3. **Create data files** (organize however you want)
4. **Done!** AI automatically includes it

### Example: "Learning" Focus Area

```bash
mkdir -p focus-areas/learning
```

Create `focus-areas/learning/instructions.md`:
```markdown
# Learning - Instructions for AI

## Purpose
Track skills and learning progress

## Processing Daily Update
When processing daily updates:
1. Look for: "learned X", "studying Y", "got better at Z"
2. Extract: Skill area, what was learned, progress level
3. Store in: learning/skills.md organized by skill area

## Data Organization
- skills.md: Current skills being developed
- completed.md: Skills achieved/mastered

## Generating Daily Briefing
Show:
- Recent learning progress
- Skills being actively developed
- Suggested learning opportunities for today

## MCP Integrations
None needed (purely based on daily logs)
```

Create data file:
```bash
echo "# Skills In Progress" > focus-areas/learning/skills.md
```

**That's it!** The AI will now process learning in daily updates and include it in briefings.

---

## Ideas for More Focus Areas

Here are some focus areas you could add:

### 🏃 Sprints
- Track sprint work and velocity
- Show sprint progress in briefings
- Organize by sprint number

### 📚 Learning
- Track skills being developed
- Note resources and courses
- Show learning streaks

### 🤝 Relationships
- Track stakeholder interactions
- Note important conversations
- Remember context for people

### 💡 Ideas
- Capture ideas mentioned in logs
- Organize by project or area
- Surface relevant ideas in briefings

### 🏥 Work-Life Balance
- Track work hours and breaks
- Monitor burnout indicators
- Suggest when to disconnect

### 📧 Email Intelligence
- Learn email importance patterns
- Track response times
- Suggest email processing times

### 🤝 Meetings
- Track meeting effectiveness
- Learn which meetings add value
- Suggest meeting optimizations

### 📈 Projects
- Track specific project progress
- Organize by project milestones
- Show project health

### 🎨 Side Projects
- Track personal projects
- Log creative work
- Manage multiple interests

---

## Focus Area Structure

Each focus area should have:

```
focus-areas/[name]/
├── instructions.md          # Required: tells AI what to do
├── [data-files]            # Your choice: organize however makes sense
└── memory/                 # Optional: for learned patterns
    └── patterns.md
```

---

## How Focus Areas Work

### During `/daily-update`
1. AI reads each focus area's `instructions.md`
2. Follows "Processing Daily Update" section
3. Updates that focus area's data files
4. Each area processes independently

### During `/daily-briefing`
1. AI reads each focus area's `instructions.md`
2. Follows "Generating Daily Briefing" section
3. Creates briefing section for that area
4. All sections combined into full briefing

---

## Best Practices

### Instruction Files
- Be specific about what to look for
- Define clear data organization
- Specify briefing format
- Include examples

### Data Organization
- Use whatever structure makes sense
- By time (sprint, quarter, year)
- By category or project
- Keep it simple

### Focus Area Independence
- Each area should work standalone
- Can reference other areas but not depend on them
- Easy to add/remove without breaking others

---

## Current System Architecture

```
Daily Update Flow:
User describes day
  ↓
AI reads: brag-sheet/instructions.md
AI process: Extract accomplishments
AI updates: brag-sheet/accomplishments.md
  ↓
AI reads: time-blocking/instructions.md
AI process: Track work items
AI updates: time-blocking/memory/active-work.md
  ↓
AI reads: goals/instructions.md
AI process: Update goal progress
AI updates: goals/active-goals.md
  ↓
Summary: What was learned across all areas

Daily Briefing Flow:
AI reads: goals/instructions.md
AI generates: Goals section of briefing
  ↓
AI reads: time-blocking/instructions.md
AI fetches: Google Calendar via MCP
AI generates: Time blocking section
  ↓
AI reads: brag-sheet/instructions.md
AI generates: Brag sheet reminders
  ↓
Combined: Full daily briefing
```

---

## Customization

### Modify Existing Focus Areas
Edit `instructions.md` to change behavior:
- What gets tracked
- How it's organized
- What shows in briefings

### Remove Focus Areas
Just delete the directory - system adapts automatically

### Add Focus Areas
Create new directory with `instructions.md` - that's it!

---

The system is **infinitely extensible** - add whatever you want to track! 🚀

