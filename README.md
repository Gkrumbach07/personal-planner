# Personal Planner

> An AI-powered personal planning system using Cursor and markdown files

## What is This?

This is your intelligent personal planning system built on a simple idea: **you describe your work in natural language, and the AI organizes everything for you.**

### Core Commands to Get Started:

- 📝 **`/daily-update`** - Share what you did today (AI learns and organizes everything)
- 🌅 **`/daily-briefing`** - Get your morning briefing (AI tells you what to focus on)
- ➕ **`/create-focus-area`** - Create new tracking systems for anything you want

The system is **flexible and extensible** - these are starting points. You can add more commands or focus areas as needed.

---

## 🚀 Quick Start

### First Time Setup - Onboard the System

**Think of this like onboarding a new assistant** - the AI needs context about you and your work!

On your very first `/daily-update`, don't hold back. Share:

**About You & Your Role:**
- What's your job title and responsibilities?
- What team are you on?
- Who do you work with regularly?
- Who's your manager?

**Your Current Projects:**
- What are you working on right now?
- What's the context and goals for each project?
- Any deadlines or milestones?
- Who are the stakeholders?

**Your Goals:**
- What are you trying to achieve? (Promotion, project completion, skills, etc.)
- What matters most to you professionally?
- Any upcoming performance reviews or important dates?

**Your Work Patterns:**
- When are you most productive?
- What kinds of meetings do you have?
- Common collaborators or stakeholders?

**Example first update:**
```
I'm a Senior Software Engineer on the Platform team, reporting to Jane Smith. 
I'm currently leading the API microservices migration - we're breaking down 
our monolith into independent services. Target is Q1 2025 completion.

Also working toward promotion to Staff Engineer - hoping for mid-year promo 
cycle. I mentor two junior engineers (Sarah and Mike) and I'm trying to build 
more cross-functional visibility.

Regular meetings: Daily standups (9:30am), 1:1 with Jane (Tuesdays 2pm), 
architecture reviews (Thursdays). Most productive in mornings 9-12.

Current priorities: API migration is #1, promotion prep is #2, team mentoring 
is ongoing. Key stakeholders: Product team (always emailing about timelines), 
SRE team (for deployment), Engineering leadership.
```

**Don't worry about being too detailed** - this context helps the AI understand what matters and make better suggestions!

### After Initial Onboarding

1. **Daily**: Type `/daily-update` (5-10 min) - just your day's highlights
2. **Mornings**: Type `/daily-briefing` (5 min) - get your personalized briefing
3. **As needed**: Type `/create-focus-area` to track new things

The system gets smarter with each update!

---

## 🎯 How It Works

### The Commands

The system comes with a few starter commands in `.cursor/commands/`:

**`/daily-update`** - Log your day
- You: Share what you worked on (free-form, natural language)
- AI: Reads each focus area's instructions
- AI: Processes your update through each focus area
- Result: Everything organized automatically

**`/daily-briefing`** - Get your morning brief
- AI: Reads each focus area's instructions
- AI: Generates briefing for each focus area (may use Google Calendar/Gmail MCP)
- AI: Combines into comprehensive morning brief
- Result: You know exactly what to focus on today

**`/create-focus-area`** - Track something new
- AI: Guides you through creating a new focus area
- AI: Generates proper `instructions.md` and structure
- Result: New tracking system ready immediately

**You can add more commands!** Edit `.cursorrules` or create new command files in `.cursor/commands/`.

### Focus Areas (Modular Plugins)

The system has **focus areas** - self-contained modules that each track something different.

Each focus area:
- Has its own `instructions.md` that tells the AI what to do
- Organizes its data however makes sense
- Processes daily updates independently
- Contributes its own section to daily briefings

**You can add any focus areas you want!** Track whatever matters to you.

See `/focus-areas/README.md` for examples and how to create your own.

---

## 📂 File Structure

```
personal-planner/
│
├── daily-logs/                    # Your daily updates
│   └── YYYY-MM-DD.md
│
├── focus-areas/                   # Modular tracking systems
│   ├── README.md                 # Guide to creating focus areas
│   │
│   ├── [your-focus-area-1]/      # Each focus area is independent
│   │   ├── instructions.md       # Tells AI what to do
│   │   └── [data-files]          # Organized however you want
│   │
│   ├── [your-focus-area-2]/
│   │   ├── instructions.md
│   │   └── [data-files]
│   │
│   └── [add-more-as-needed]/     # Infinitely extensible!
│
└── .cursorrules                  # System configuration
```

---

## 💡 The Magic

### What Makes This Powerful

**1. You Just Talk**
- No form filling
- No categorizing
- Just describe your day naturally
- AI figures out the rest

**2. AI Learns Over Time**
- Week 1: Basic tracking
- Week 2-3: Patterns emerge  
- Month 2+: Personalized insights

**3. Modular & Extensible**
- Each focus area is independent
- Add new focus areas anytime
- Remove what you don't need
- Customize instructions per area

**4. Private & Yours**
- All data in markdown files
- Your private repo
- No external databases
- Full control

---

## 🎨 Example Daily Update

```
You: /daily-update

AI: How was your day?

You: Spent most of the morning finishing up the user service extraction for
the API migration - that's finally done! Had our weekly 1:1 which was really
valuable, discussed promotion timeline. Helped Sarah debug a race condition 
in the payment system. Got spammed by JIRA emails again about tickets I'm 
not even on. Tomorrow need to start on the notification service.

AI: ✅ Processed your update through your focus areas:

[Each focus area processes according to its instructions.md]

Focus Area 1:
- [What it extracted/updated]

Focus Area 2:
- [What it extracted/updated]

Focus Area 3:
- [What it extracted/updated]

📝 Patterns learned:
- [Any new learnings across focus areas]

✅ Daily log saved to /daily-logs/2025-01-15.md

Tomorrow's suggested focus: [Based on what focus areas learned]
```

---

## 🌅 Example Daily Briefing

```
You: /daily-briefing

AI:
# Daily Briefing - Tuesday, January 16, 2025

[Each focus area generates its briefing section based on its instructions.md]

## [Focus Area 1 Briefing]
[Generated content based on that focus area's data and instructions]

## [Focus Area 2 Briefing]
[Generated content - might use MCP integrations like Google Calendar]

## [Focus Area 3 Briefing]
[Generated content with suggestions and reminders]

[Continues for all focus areas...]

---

Have a productive day! 🚀
```

The specific content depends entirely on what focus areas you've created and
what their `instructions.md` files tell the AI to do.

---

## 🔧 Extending the System

### Add New Focus Areas

Want to track something else? Easy!

**Using the helper command:**
```
/create-focus-area
```
The AI will guide you through creating a properly structured focus area.

**Or manually:**
1. Create `/focus-areas/[name]/`
2. Write `instructions.md` (tells AI what to do)
3. Create data files (organize however you want)
4. Done! AI automatically includes it

See `/focus-areas/README.md` for complete guide, templates, and examples.

### Add New Commands

Commands are just markdown files in `.cursor/commands/`. To add your own:

1. Create `.cursor/commands/your-command.md`
2. Write instructions for the AI to follow
3. Update `.cursorrules` to reference it
4. Use `/your-command` in Cursor

The system is infinitely extensible!

---

## 🎓 How Each Focus Area Works

### Focus Area = Instructions + Data

Each focus area has:

**`instructions.md`** - Tells the AI:
- What to look for in daily updates
- Where/how to store information
- What to show in briefings
- How to learn and improve

**Data files** - Organized however makes sense:
- By time (sprint, quarter, year)
- By category
- By project
- Whatever works for that focus area!

### The AI Reads Instructions

When you run `/daily-update` or `/daily-briefing`:
1. AI finds all focus areas
2. Reads each `instructions.md`
3. Follows those instructions exactly
4. Each focus area processes independently

---

## 💻 Setup (Optional MCP Integrations)

### Google Workspace MCP Server (Recommended)

For full integration with Gmail, Calendar, Docs, Sheets, Slides, and Drive:

**Install**: [Google Workspace MCP Server](https://github.com/taylorwilsdon/google_workspace_mcp)

```bash
# Install via uvx (easiest)
uvx workspace-mcp
```

**What it enables:**
- **Time-blocking**: Real calendar data, optimized schedules around meetings
- **Email intelligence**: Process Gmail for priorities and action items
- **Document access**: Read meeting notes, project docs from Google Docs
- **Data integration**: Access spreadsheets, presentations, drive files
- **Context awareness**: Link daily updates to actual emails, meetings, documents

**Setup in Cursor:**

Add to your MCP settings (`.cursor/mcp.json` or similar):

```json
{
  "mcpServers": {
    "google_workspace": {
      "command": "uvx",
      "args": ["workspace-mcp"],
      "env": {
        "GOOGLE_OAUTH_CLIENT_ID": "your-client-id",
        "GOOGLE_OAUTH_CLIENT_SECRET": "your-secret"
      }
    }
  }
}
```

See the [Google Workspace MCP documentation](https://github.com/taylorwilsdon/google_workspace_mcp) for:
- Creating OAuth credentials
- First-time authentication
- Available services and tools
- Advanced configuration

### Without MCP

All focus areas work without MCP! You'll get:
- ✅ Daily update tracking
- ✅ Brag sheet building
- ✅ General time block suggestions
- ❌ No real calendar integration
- ❌ No email processing
- ❌ No document access

MCP makes the system **significantly more powerful** but isn't required.

---

## 📊 Tips for Success

### Daily Update Tips
- **Be conversational**: Talk like you're telling a friend
- **Include context**: Why things mattered
- **Note patterns**: "Another useless meeting", "Really productive morning"
- **Mention people**: Collaborations and help given/received
- **Be honest**: Challenges, blocks, frustrations

### Consistency Matters
- **Week 1**: System is learning
- **Week 2-3**: Patterns start emerging
- **Month 2+**: System knows you well
- **The more you use it, the smarter it gets**

### Customization
- Edit any focus area's `instructions.md` to change behavior
- Add focus areas for anything you want to track
- Remove focus areas you don't need
- System adapts to YOU

---

## 🚦 Getting Started Checklist

- [ ] **Day 1**: Do comprehensive first `/daily-update` with full context (see onboarding section above)
- [ ] Review what AI extracted and where it stored things
- [ ] **Day 2**: Morning `/daily-briefing` - see what AI learned
- [ ] **Day 2**: Evening `/daily-update` - shorter, just today's work
- [ ] **Week 1**: Daily updates (build the habit and let AI learn)
- [ ] **Week 2**: Review focus areas - check what's being tracked
- [ ] **Anytime**: Add new focus areas with `/create-focus-area`
- [ ] (Optional) Set up Google Workspace MCP for calendar/email integration

---

## ❓ FAQ

**Q: Do I need to use all focus areas?**  
A: No! Use what's helpful. Remove or ignore others.

**Q: Can I edit the AI's work?**  
A: Yes! All files are yours to edit.

**Q: What if AI gets something wrong?**  
A: Edit the file, and AI will learn from it.

**Q: Can I track personal stuff too?**  
A: Absolutely! Add focus areas for anything.

---

## 🎉 Philosophy

This system is built on simple principles:

1. **Consistency > Perfection**: Quick daily updates beat perfect weekly ones
2. **AI Augments, Not Replaces**: You describe, AI organizes
3. **Memory is Powerful**: Systems that learn get smarter
4. **Privacy Matters**: Your data stays yours
5. **Modular is Better**: Add what you need, ignore the rest
6. **Knowledge Share First**: Treat the system like a new hire - onboard it properly!

---

## 🚀 You're Ready!

Start with your first update:

```
/daily-update
```

**First time?** Give the AI context - share about your role, projects, goals, work patterns. Think of it like onboarding a new assistant who needs to understand your world.

**After that?** Just 5-10 minutes daily describing what you did. The AI learns and gets smarter over time.

The system is flexible - use what works, change what doesn't, add what's missing. It adapts to YOU.

Good luck! 🎯
