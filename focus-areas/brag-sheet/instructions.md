# Brag Sheet - Instructions for AI

## Purpose
Track accomplishments and significant work for promotion documentation, performance reviews, and career advancement. Extract and organize achievements from daily updates in a format that aligns with the user's promotion document template.

---

## Processing Daily Update

When processing a daily update for the brag sheet focus area:

### 1. Identify Brag-Worthy Items
Look for:
- **High-impact work**: Significant project completions, major features shipped, system improvements
- **Leadership**: Led initiatives, mentored others, influenced direction, resolved conflicts
- **Collaboration**: Cross-team work, helped others succeed, facilitated important discussions
- **Problem-solving**: Resolved critical bugs, prevented incidents, debugged complex issues
- **Innovation**: New approaches, process improvements, creative solutions
- **Visibility**: Work seen by leadership, customers, or broader organization

**What's NOT brag-worthy** (skip these):
- Routine tasks without special impact
- Small bug fixes (unless critical)
- Standard meeting attendance
- Normal day-to-day work

### 2. Extract Details
For each brag-worthy item, capture:
- **What you did** (action-oriented, use strong verbs: led, built, implemented, resolved, improved)
- **The impact** (quantifiable if possible: metrics, users affected, time/money saved, performance gains)
- **Context** (why it mattered, what the challenge was)
- **Skills demonstrated** (technical, leadership, communication, etc.)
- **Visibility** (who saw this: team, department, organization, company, customers)

### 3. Categorize by Promotion Template
Read `/focus-areas/brag-sheet/promotion-context.md` for career goals and promotion themes.
Read `/focus-areas/brag-sheet/promotion-template.md` for Red Hat Principal Engineer competencies.

**Red Hat Principal Engineer - 5 Core Competencies:**
1. **Technical Contribution** (Business Impact, Scope, Planning, Innovation, Knowledge)
2. **Leadership** (Work Impact, Continuous Improvement, Portfolio Impact)
3. **Collaboration** (Cross-functional driving)
4. **Mentorship** (Growth Impact, Mentee execution)
5. **End-to-End Delivery** (Product delivery, Customer focus)

**Important**: Principal level requires evidence across ALL competencies, demonstrating impact **beyond immediate team**, across **multiple technical areas**, with **sustained contribution** over time.

Assign each accomplishment to appropriate competency/subcategories.

### 4. Store in accomplishments.md
Add to `/focus-areas/brag-sheet/accomplishments.md` using this format:

```markdown
## [Accomplishment Title]
- **Date**: YYYY-MM-DD
- **Category**: [From promo template sections]
- **Impact**: High/Medium
- **Visibility**: Team/Department/Organization/Company/Customer

### What I Did
[Action-oriented description using strong verbs]

### The Result
[Quantifiable impact - metrics, outcomes, feedback]

### Skills Demonstrated
[Competencies this showcases]

### Context
[Why it mattered, what made it challenging or significant]
```

### 5. Organize by Time Period
Within `accomplishments.md`, organize by:
- Current Quarter (most recent at top)
- Previous Quarter(s)
- Year to date

This makes it easy to generate timeframe-based exports.

---

## Data Organization

**File Structure:**
```
/focus-areas/brag-sheet/
├── instructions.md (this file)
├── accomplishments.md (all accomplishments, organized by quarter)
├── promotion-context.md (career goals, manager feedback, promotion path context)
└── promotion-template.md (Red Hat Principal Engineer competency framework)
```

**Organization within accomplishments.md:**
- By quarter/year for easy time-based filtering
- High-impact items at top of each section
- Consistent format for all entries
- Cross-reference related items

---

## Generating Daily Briefing

When generating morning briefing for brag sheet:

### 1. Check Recent Patterns
- Read `promotion-context.md` for career goals and focus areas
- When was last high-impact accomplishment added?
- Are we getting good coverage across promo template categories?
- Any category underrepresented?
- How do recent accomplishments align with Staff++ path goals?

### 2. Provide Reminders
- If big milestone is expected today (from time-blocking memory), remind to document it
- If it's been >2 weeks since last entry, encourage looking for wins
- If specific promo category is thin, suggest opportunities

### 3. Output Format
```markdown
## 🏆 Brag Sheet Reminders
- [Number] accomplishments this quarter
- Last entry: [Date] - [Brief description]
- Today's opportunity: [If applicable, what might be worth documenting]
- Category focus: [If needed, which promo section needs more examples]
```

### Example:
```markdown
## 🏆 Brag Sheet Reminders
- 8 accomplishments this quarter (target: 12 for strong promo case)
- Last entry: Jan 10 - Database incident leadership
- Today's opportunity: User service completion is promotion-worthy!
- Category focus: Could use more collaboration examples
```

---

## MCP Integrations

**Not needed for this focus area** - works entirely from daily logs and user's stated work.

Optional: Could integrate with Jira/GitHub to auto-detect significant PRs or issue resolutions, but not required.

---

## Memory & Learning

### What to Learn
- **What user considers brag-worthy**: Some people are modest, others liberal with what they include
- **Impact thresholds**: What level of impact merits documentation
- **Career goals**: What type of work aligns with their promotion goals
- **Writing style**: How they describe accomplishments (mirror this)

### Confidence Levels
- 100%: User explicitly says "this is brag-worthy"
- 90%: Clear high-impact work (major milestone, leadership, visible success)
- 75%: Solid accomplishment but user didn't emphasize it
- 50%: Potentially significant but unsure (ask user)

### When to Update
- User provides feedback ("this should/shouldn't be in brag sheet")
- Patterns emerge (user consistently includes/excludes certain types of work)
- Promotion template is updated
- Career goals change

### Memory Storage
Store learnings in `/memory/priorities.md` under "Career Goals" section or create `/focus-areas/brag-sheet/memory/patterns.md` for focus-area-specific learnings.

---

## Tips for Quality Brag Entries

**Strong Verbs**: Led, built, implemented, resolved, improved, designed, established, prevented, accelerated, enabled

**Quantify Impact**:
- X% performance improvement
- Y users/customers affected
- $Z saved or revenue generated
- N team members helped/mentored
- Reduced time from X to Y

**Context Matters**:
- What was the challenge?
- Why was it important?
- What was the stakes/urgency?
- Who benefited?

**Show Growth**:
- Progression over time
- Increasing scope/complexity
- Expanded influence/visibility
- New skills demonstrated

---

## Exporting Brag Sheet

When user wants to export (via `/weekly-review` or similar):

1. Read `accomplishments.md`
2. Filter by requested timeframe
3. Read `/templates/promotion-template.md`
4. Format accomplishments to match template structure
5. Group by template categories
6. Order by impact (high first)
7. Output ready for copy-paste into promotion doc

---

## Success Metrics

This focus area is working well if:
- ✅ User has 12-20 strong examples over 6 months (for promotion)
- ✅ Coverage across all promo template categories
- ✅ Mix of technical, leadership, and collaboration
- ✅ Quantifiable impact for most entries
- ✅ User can export promotion doc in <5 minutes
- ✅ Nothing significant gets forgotten

---

## Adaptation

This focus area should adapt to:
- User's company culture (what's valued)
- Promotion template format
- Career level (IC vs management track)
- Industry norms
- User's personal style and comfort with self-promotion

