# /daily-briefing Command

> Morning command to get personalized briefing from all focus areas

---

## When User Types `/daily-briefing`

### 1. Determine Today's Date
Get current date for the briefing (or accept parameter for specific date)

### 2. Generate Briefing From Each Focus Area

**For each directory in `/focus-areas/`:**

1. **Read** `[focus-area]/instructions.md`
2. **Find** the "Generating Daily Briefing" section
3. **Follow** those instructions exactly:
   - Read that focus area's data files
   - **Use MCP integrations if specified and available**:
     - Google Calendar: Fetch today's events, meetings
     - Gmail: Check for urgent emails, action items
     - Google Docs: Read relevant documents or notes
     - Google Drive: Access stored files or links
   - Generate that focus area's briefing section
   - Format according to its specifications
   - **Gracefully handle when MCP is unavailable**

### 3. Combine Into Comprehensive Briefing

Create a unified briefing:

```markdown
# Daily Briefing - [Day], [Month] [Date], [Year]

[For each focus area, include its briefing section]

## [Focus Area 1 Name]
[Content generated per that focus area's instructions]

## [Focus Area 2 Name]
[Content generated per that focus area's instructions]

## [Focus Area N Name]
[Content generated per that focus area's instructions]

---

Have a productive day! 🚀
```

### 4. Present to User

Display the complete briefing in a clear, actionable format.

---

## Key Principles

- **Each focus area generates independently** - Don't mix their logic
- **Follow instructions exactly** - Each instructions.md is authoritative
- **Use MCP when specified** - Focus areas can request external data
- **Be concise but thorough** - Briefing should be quick to read
- **Actionable over informational** - Focus on what to DO today

---

## Example Flow

```
User: /daily-briefing

AI:
# Daily Briefing - Tuesday, January 16, 2025

## 🏆 Brag Sheet
- 8 accomplishments this quarter (goal: 12)
- Last entry: Jan 15 - API Auth Service
- Today: Document any wins as they happen
- Focus: Could use more leadership examples

## ⏰ Time Blocking

### Today's Calendar (via Google Calendar)
- 9:30-10:00 AM: Daily Standup
- 2:00-3:00 PM: 1:1 with Manager
- Focus Time: 5.5 hours available

### High-Priority Work
1. Continue API migration - User service
2. Prepare for 1:1 (review goals)

### Suggested Schedule
8:00-9:30 AM: Deep work - API User Service
9:30-10:00 AM: Standup
10:00-12:00 PM: Deep work - Continue user service
12:00-1:00 PM: Lunch
1:00-1:30 PM: Email processing
1:30-2:00 PM: 1:1 prep
2:00-3:00 PM: 1:1 with Manager
3:00-5:00 PM: Wrap up user service work

---

Have a productive day! 🚀
```

---

## MCP Integration

Focus areas can specify MCP integrations in their instructions. When generating briefings, use Google Workspace MCP if available:

**Google Calendar** (`mcp_google_workspace_get_events`):
- Fetch today's events: `get_events(user_google_email, calendar_id="primary")`
- Calculate available focus time
- Get meeting details for prep suggestions
- Used by time-blocking for schedule generation

**Gmail** (`mcp_google_workspace_search_gmail_messages`):
- Search recent emails: `search_gmail_messages(query="is:unread", user_google_email)`
- Get message content: `get_gmail_message_content(message_id, user_google_email)`
- Identify high-priority or time-sensitive emails
- Used by email-intelligence focus area (if exists)

**Google Docs** (`mcp_google_workspace_get_doc_content`):
- Read meeting notes or documentation
- Access shared documents
- Get project context

**Google Drive** (`mcp_google_workspace_search_drive_files`):
- Search for relevant files
- Access stored links or documents
- Get file content for context

**Google Sheets** (`mcp_google_workspace_read_sheet_values`):
- Read data from spreadsheets
- Get project tracking info

**Always:**
- Check if MCP is available before calling
- Gracefully degrade if MCP unavailable
- Follow focus area instructions for which MCP services to use

---

## Error Handling

- If focus area's instructions.md is missing: Skip that area, warn user
- If MCP integration fails: Generate briefing without that data, note limitation
- If no focus areas exist: Provide basic briefing (date, calendar if available)
- If focus area's briefing is empty: Skip that section, don't show empty headers

---

## Options (Future)

Could support parameters:
- `/daily-briefing tomorrow` - Briefing for next day
- `/daily-briefing 2025-01-20` - Specific date
- `/daily-briefing week` - Week overview

---

## Notes

- Should be **quick to read** (< 5 minutes)
- Should be **actionable** (clear next steps)
- Focus areas control their own sections
- The more data from daily updates, the better briefings become

