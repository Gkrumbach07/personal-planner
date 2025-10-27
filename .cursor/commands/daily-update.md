# /daily-update Command

> End-of-day command to log what you did and process through all focus areas

---

## When User Types `/daily-update`

### 1. Fetch Activity Data (Automated)

**Before asking for user input, automatically gather today's activity:**

1. **Slack Activity**: Search for messages from user today
   - `mcp_slack_conversations_search_messages(filter_date_on="Today", filter_users_from="gkrumbac", limit=100)`
2. **Google Calendar**: Get today's events
   - `mcp_google_workspace_get_events(time_min=today_start, time_max=today_end, detailed=true)`
3. **Gmail**: Get today's emails (metadata only for speed)
   - `mcp_google_workspace_search_gmail_messages(query="after:YYYY/MM/DD before:YYYY/MM/DD", page_size=50)`
   - Then batch get metadata: `get_gmail_messages_content_batch(format="metadata")`
4. **Google Drive**: Get files modified/accessed today
   - `mcp_google_workspace_search_drive_files(query="modifiedTime >= 'YYYY-MM-DDT00:00:00' and modifiedTime < 'YYYY-MM-DDT23:59:59'", page_size=20)`

**Summarize the activity** into a structured format:
- Key Slack conversations (by channel/topic)
- Calendar meetings attended
- Important emails (filter out noise)
- Active Drive documents

### 2. Ask for Daily Update
Prompt the user: **"How was your day? Tell me what you worked on."**

Accept free-form, conversational text. They should talk naturally about:
- What they worked on
- What they accomplished
- Meetings attended
- People helped
- Challenges faced
- What they learned
- Tomorrow's focus

### 3. Save Raw Update with Activity Context
Create or update `/daily-logs/YYYY-MM-DD.md` with:

```markdown
# YYYY-MM-DD

## My Update
[User's raw update - exactly as they wrote it]

---

## Activity Summary (Auto-generated)

### Slack Conversations
[Summarized by channel/topic]

### Calendar
[List of meetings attended]

### Emails
[Key emails received/sent - filter noise]

### Drive Activity
[Documents worked on with links]
```

### 4. Process Through Each Focus Area

**For each directory in `/focus-areas/`:**

1. **Read** `[focus-area]/instructions.md`
2. **Find** the "Processing Daily Update" section
3. **Follow** those instructions exactly:
   - Extract what that focus area looks for
   - **Use MCP integrations if specified**:
     - Google Calendar: Verify meetings mentioned
     - Gmail: Check referenced emails
     - Google Docs: Link to mentioned documents
     - Google Drive: Store links to files
   - Update that focus area's data files
   - Use that focus area's organization structure
4. **Track** what was updated for summary
5. **Use the Activity Summary data** from step 1 to enrich context

### 5. Summarize What Was Learned

Present summary to user:
```
✅ Processed your update through [N] focus areas:

[Focus Area 1 Name]:
- [What was extracted/updated]

[Focus Area 2 Name]:
- [What was extracted/updated]

📝 Patterns learned:
- [Any new learnings]

✅ Daily log saved to /daily-logs/YYYY-MM-DD.md
```

---

## Key Principles

- **User input is free-form** - No structure required from user
- **Each focus area is independent** - Process them separately
- **Follow instructions exactly** - Each focus area's instructions.md is authoritative
- **Preserve all data** - Save raw update, don't lose information
- **Be conversational** - This should feel easy and natural

---

## Example Flow

```
User: /daily-update

AI: [Automatically fetches Slack, Calendar, Gmail, Drive activity...]

AI: How was your day? Tell me what you worked on.

User: Had a really productive morning working on the API migration. 
Finally got the auth service separated out - that took longer than 
expected but it's done! Helped Sarah with a bug after lunch. Got 
way too many JIRA emails today, mostly noise.

AI: ✅ Processed your update through 2 focus areas:

Brag Sheet:
- Added: "API Auth Service Extraction" (Technical Leadership)
- Added: "Mentored Sarah on debugging" (Collaboration)

Time Blocking:
- Completed: Auth service work
- Active: API migration continues
- Pattern: Morning is your productive time

✅ Daily log saved to /daily-logs/2025-01-15.md
   - Your update at the top
   - Auto-generated activity summary at the bottom
   - Includes: 3 Slack channels, 5 meetings, 12 emails, 8 Drive docs
```

---

## Error Handling

- **If MCP services fail**: Continue with update, note what couldn't be fetched in activity summary
- **If Slack/Gmail/Calendar/Drive is unavailable**: Skip that section, continue with others
- If focus area's instructions.md is missing: Skip that area, warn user
- If focus area's instructions are unclear: Do best effort, note uncertainty
- If user update is very short: Accept it anyway (some days are just like that)
- If date already has a log: Append or ask if they want to replace

---

## Notes

- This is the **core command** - everything else builds on daily updates
- Consistency matters more than perfection
- The more they use it, the smarter the system gets
- Each focus area learns independently from the same input

