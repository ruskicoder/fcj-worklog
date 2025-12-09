# AI Workflow Checklist for Worklog Updates

## AUTOMATED WORKFLOW (Source-First Approach)

This workflow uses available source data to automatically generate worklog content, then asks for user confirmation.

### Step 1: Gather Data from Sources (AUTOMATIC)

Before updating any week's worklog, the AI MUST:

1. **Check source files:**
   - Read `sources/workdays.md` for office attendance dates
   - Read `sources/events.md` for AWS events and special occasions
   - Check `source_data_reference.md` for week-specific details

2. **Identify week-specific data:**
   - Workdays in this week (office 9am-5pm = heavier content)
   - Events scheduled in this week (AWS events, workshops)
   - Personal events (injury, doctor visits, team project start)
   - Week date range (8-14/9, 15-21/9, etc.)

3. **Apply content strategy:**
   - Use `worklog_content_strategy.md` for content patterns
   - Heavier content for workdays
   - Lighter content for home days
   - Event details for event days
   - Fill gaps with typical AWS learning activities

### Step 2: Generate Content (AUTOMATIC)

Based on gathered data, automatically generate:

1. **Week worklog files:**
   - Update `content/1-Worklog/1.X-WeekX/_index.md` (English)
   - Update `content/1-Worklog/1.X-WeekX/_index.vi.md` (Vietnamese)
   - Set correct `weight` parameter (must match week number)
   - Set correct date in front matter
   - Include all activities based on sources

2. **Content structure:**
   - Week objectives
   - Daily tasks table (with actual dates and activities)
   - Week achievements
   - Challenges (if applicable)
   - Key learnings
   - Next week goals

3. **Apply content rules:**
   - Workdays: 3-5 activities, detailed descriptions
   - Home days: 1-2 activities, lighter content
   - Event days: Full event coverage
   - No Saturday/Sunday entries (unless special event)
   - Professional tone throughout

### Step 3: Present to User for Confirmation (REQUIRED)

After generating content, present summary to user:

```
I've updated Week X worklog (DD-DD/MM/YYYY) with:

**Workdays:** [list dates]
**Events:** [list events if any]
**Key Activities:** [brief summary]
**AWS Services:** [list services covered]
**Blog Translations:** [status]

Files updated:
- content/1-Worklog/1.X-WeekX/_index.md
- content/1-Worklog/1.X-WeekX/_index.vi.md

Would you like me to make any changes, or is this good to proceed?
```

### Step 4: Handle User Response

**If user approves (says "yes", "looks good", "proceed", etc.):**
- Mark task as complete
- Move to next task or wait for user direction
- No further changes needed

**If user requests changes:**
- Ask for specific details about what to change
- Update content based on user's explicit requests
- Present updated summary again
- Repeat until user approves

**If user provides additional information:**
- Incorporate new information into content
- Update both English and Vietnamese versions
- Present updated summary for confirmation

### Step 5: Validation (AUTOMATIC)

After user approval:

- [ ] Verify Hugo front matter weight parameters
- [ ] Check bilingual consistency
- [ ] Validate professional tone
- [ ] Ensure all source data incorporated
- [ ] Mark task as complete in tasks.md

## CRITICAL RULES

### ✅ ALWAYS DO THIS:

- Use source files (`workdays.md`, `events.md`) as primary data
- Auto-generate content based on sources and strategy
- Present completed work to user for confirmation
- Only ask for details if sources are missing or unclear
- Update content based on explicit user requests
- Maintain professional tone
- Ensure bilingual consistency
- Set correct `weight` parameter (must match week number)

### ❌ NEVER DO THIS:

- Ask user for information that's already in source files
- Wait for user input before generating content
- Fabricate activities without basis in sources or strategy
- Skip the confirmation step
- Proceed to next task without user approval
- Ignore user's explicit change requests

## Content Priority Order

1. **AWS Events** (from events.md) - Full coverage, highest priority
2. **Personal Events** (injury, doctor visits) - Brief professional mention
3. **Team Project** (from 5/11 onwards) - Replaces AWS study
4. **Workdays** (from workdays.md) - Heavier learning content
5. **Home Days** - Lighter content or day off
6. **Fill Gaps** - Typical AWS learning or revision

## Quick Reference: Week Weight Values

| Week | Weight | Dates | Week | Weight | Dates |
|------|--------|-------|------|--------|-------|
| 1 | 1 | 8-14/9 | 7 | 7 | 20-26/10 |
| 2 | 2 | 15-21/9 | 8 | 8 | 27/10-2/11 |
| 3 | 3 | 22-28/9 | 9 | 9 | 3-9/11 |
| 4 | 4 | 29/9-5/10 | 10 | 10 | 10-16/11 |
| 5 | 5 | 6-12/10 | 11 | 11 | 17-23/11 |
| 6 | 6 | 13-19/10 | 12 | 12 | 24-30/11 |

## Example Workflow

```
User: "Start task 2.2" (Week 2)

AI: [Reads sources/workdays.md - finds workday 21/9]
    [Reads sources/events.md - no events this week]
    [Applies worklog_content_strategy.md]
    [Generates content for Week 2]
    [Updates both _index.md and _index.vi.md]
    
    "I've updated Week 2 worklog (15-21/9/2025) with:
    
    Workdays: 21/9 (office)
    Key Activities: AWS account setup, IAM basics, EC2 introduction
    AWS Services: IAM, EC2
    
    Files updated:
    - content/1-Worklog/1.2-Week2/_index.md
    - content/1-Worklog/1.2-Week2/_index.vi.md
    
    Would you like me to make any changes?"

User: "Yes, looks good" → AI marks task complete, moves on

OR

User: "Add more details about VPC" → AI updates content, presents again
```

## Troubleshooting

**If source data is missing:**
- Use typical AWS learning activities from `worklog_content_strategy.md`
- Fill with revision periods or vague family occasion mentions
- Maintain realistic learning progression

**If user wants major changes:**
- Ask for specific details about what to change
- Update content based on explicit requests
- Re-present for confirmation

**If user wants to skip sections:**
- Confirm explicitly
- Document in task notes
- Proceed with remaining sections
