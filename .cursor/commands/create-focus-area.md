# /create-focus-area Command

> Helper command to create a new focus area following best practices

---

## When User Types `/create-focus-area` or `/create-focus-area [name]`

### 1. Determine Focus Area Name

**If name provided**: Use it (sanitize for filesystem)
**If not provided**: Prompt user: "What do you want to name this focus area?"

**Naming guidelines:**
- Use lowercase with hyphens (e.g., `email-intelligence`, `sprint-tracking`)
- Short and descriptive
- No spaces or special characters

### 2. Check if Already Exists

Check if `/focus-areas/[name]/` already exists:
- If yes: Ask if they want to override or choose different name
- If no: Proceed

### 3. Gather Focus Area Details

Prompt the user for:

**a) Purpose**: "What will this focus area track?"
- Example: "Track email patterns and importance"
- Example: "Monitor sprint work and velocity"

**b) Data organization**: "How do you want to organize the data?"
- Options: "By time (sprint/quarter/year)", "By category", "By project", "Other"
- User can describe their preferred structure

**c) Daily update processing**: "What should the AI look for in daily updates?"
- What keywords, patterns, or information to extract
- Examples of what to track

**d) Daily briefing output**: "What should be shown in morning briefings?"
- What information to present
- Format preferences

**e) MCP integrations**: "Will this need MCP integrations?"
- If yes: Which services? (Calendar, Gmail, Docs, Drive, etc.)
- If no: Purely based on daily logs

### 4. Create Directory Structure

Create: `/focus-areas/[name]/`

**Basic structure:**
```
focus-areas/[name]/
├── README.md (describe what this focus area does)
└── instructions.md (tell AI how to process it)
```

**With memory option:**
```
focus-areas/[name]/
├── README.md
├── instructions.md
└── memory/
    └── [data-file].md
```

### 5. Generate README.md

Create `/focus-areas/[name]/README.md`:

```markdown
# [Focus Area Name] Focus Area

> [Purpose from user input]

---

## What This Tracks

[Description of what this focus area monitors/tracks]

---

## How It Works

### During `/daily-update`
[Brief description of what gets extracted from daily logs]

### During `/daily-briefing`
[Brief description of what gets shown in briefings]

---

## Files

**`instructions.md`** - Complete instructions for AI

**[List other data files and their purpose]**

---

## Customization

Edit `instructions.md` to change:
- What gets tracked
- How data is organized
- What shows in briefings

---

## Tips

[Any specific tips for using this focus area]
```

### 6. Generate instructions.md

Create `/focus-areas/[name]/instructions.md` using the template from `/focus-areas/README.md`:

```markdown
# [Focus Area Name] - Instructions for AI

## Purpose
[Purpose from user input]

---

## Processing Daily Update

When processing a daily update for this focus area:

### 1. Look For
[What to extract from daily updates - from user input]

Examples:
- [Example pattern 1]
- [Example pattern 2]

### 2. Extract and Store
[Where and how to store the information]

Update: `/focus-areas/[name]/[data-file].md`

Format:
```markdown
## [Entry Title]
- **Date**: YYYY-MM-DD
- [Other relevant fields]
```

### 3. Learn Patterns
[What patterns to track over time]

---

## Data Organization

**File Structure:**
```
/focus-areas/[name]/
├── instructions.md (this file)
└── [data-files as described by user]
```

[Describe organization approach: by time, category, etc.]

---

## Generating Daily Briefing

When generating morning briefing for this focus area:

### 1. Read Data
- Read `/focus-areas/[name]/[data-files]`
- [Any other data sources]

### 2. Analyze
[What to calculate or analyze from the data]

### 3. Present
[What to show to user]

### 4. Output Format

```markdown
## [Focus Area Name]

[What to display in the briefing]
- [Key information 1]
- [Key information 2]
- [Suggestions or reminders]
```

---

## MCP Integrations

[If user specified MCP needs]

**[Service Name]** (if available):
- **Use**: [What MCP function to call]
- **Purpose**: [Why this data is needed]
- **Fallback**: [What to do if MCP unavailable]

[Or if no MCP needed]

**Not needed** - this focus area works purely from daily logs.

---

## Memory & Learning

### What to Learn
[What patterns should be tracked over time]

### Confidence Levels
[How to build confidence in patterns]

### Memory Storage
[Where learned patterns are stored]

---

## Success Metrics

This focus area is working well if:
- ✅ [Success criterion 1]
- ✅ [Success criterion 2]
- ✅ [Success criterion 3]

---

## Notes

[Any additional notes or special considerations]
```

### 7. Create Initial Data Files (Optional)

Based on user's data organization preference, create starter files:
- If by quarter: Create current quarter file
- If by category: Create category template
- If custom: Create as specified

### 8. Confirm Creation

Show user what was created:
```
✅ Created new focus area: [name]

Files created:
- /focus-areas/[name]/README.md
- /focus-areas/[name]/instructions.md
- /focus-areas/[name]/[data-files]

Next steps:
1. Review and customize instructions.md
2. Run /daily-update - the AI will now process this focus area
3. Run /daily-briefing - this focus area will be included

Edit /focus-areas/[name]/instructions.md anytime to change behavior.
```

### 9. Offer to Test

Ask: "Want to test it with a sample daily update?"
- If yes: Run through processing logic with example
- If no: Done

---

## Key Principles

- **Follow focus-areas/README.md structure** - Maintain consistency
- **Use template from README** - Don't invent new format
- **Be helpful with prompts** - Guide user through creation
- **Make it easy** - Provide good defaults, let user customize
- **Test the basics** - Ensure instructions.md is valid

---

## Example Flow

```
User: /create-focus-area

AI: What do you want to name this focus area?
    (Use lowercase with hyphens, e.g., 'email-intelligence')

User: sprint-tracking

AI: Great! What will this focus area track?

User: Track my sprint work, velocity, and what I'm working on each sprint

AI: How do you want to organize the data?
    - By sprint (recommended for sprint tracking)
    - By quarter
    - By category
    - Other

User: By sprint

AI: What should I look for in your daily updates?

User: Look for mentions of sprint work, tickets completed, blockers, sprint goals

AI: What should be shown in morning briefings?

User: Show current sprint progress, tickets in progress, sprint goals, blockers

AI: Will this need MCP integrations? (y/n)

User: No, just from daily logs

AI: ✅ Creating focus area: sprint-tracking

Files created:
- /focus-areas/sprint-tracking/README.md
- /focus-areas/sprint-tracking/instructions.md
- /focus-areas/sprint-tracking/current-sprint.md

Your new focus area is ready! 

Next:
1. Review /focus-areas/sprint-tracking/instructions.md
2. Customize if needed
3. Run /daily-update - it will now process sprint information
4. Run /daily-briefing - sprint progress will be included

Want to test it with a sample update? (y/n)
```

---

## Template Structure

The generated `instructions.md` should follow this exact structure from `/focus-areas/README.md`:

1. **Purpose** section
2. **Processing Daily Update** section (with numbered steps)
3. **Data Organization** section (file structure)
4. **Generating Daily Briefing** section (what to show)
5. **MCP Integrations** section (if applicable)
6. **Memory & Learning** section (optional)
7. **Success Metrics** section (optional)

---

## Error Handling

- If invalid name: Suggest valid format
- If directory exists: Offer to merge or rename
- If user unclear on structure: Provide more examples
- If instructions are too vague: Ask clarifying questions

---

## Advanced Options (Future)

Could support:
- `/create-focus-area --from-template [template-name]` - Use predefined template
- `/create-focus-area --clone [existing-area]` - Copy structure from existing
- Pre-built templates for common focus areas (sprints, learning, projects)

---

## Notes

- This command makes it easy to extend the system
- Users can still create focus areas manually
- Generated instructions.md is a starting point - customize as needed
- Follows best practices from `/focus-areas/README.md`

