# Professional Workflow System - Obsidian Setup Guide

## System Overview

This Obsidian vault serves as your personal command center for PhD program administration. It connects your thinking, planning, and documentation across multiple Microsoft systems (Teams, SharePoint, Lists, Outlook) without replacing them. The system is designed to protect your morning focus time (9-11am), capture institutional knowledge, and provide structure to your work that spans multiple platforms.

**Key Philosophy:** Obsidian is where you think and plan; Microsoft systems are where you execute and collaborate.

---

## Quick Start Setup

1. Create a new Obsidian vault
2. Create the folder structure below
3. Copy each template into the Templates folder
4. Enable "Daily Notes" and "Templates" core plugins in Settings
5. Configure Daily Notes to use the Daily Note Template
6. Start with your first morning check-in

---

## Folder Structure & Purpose Guide

### 📁 **00 - SYSTEM README**
**Location:** Root of vault  
**Purpose:** Quick reference guide explaining each section's purpose. Essential for handoff situations or when you need to remember why something is structured a certain way. Read this when you're orienting someone new to the system.

### 📁 **00 - Daily Notes**
**Purpose:** Your daily workspace. Each day gets a new note (auto-generated) with morning protocol, focus block planning, interaction logs, and evening brain dump. This is your operational hub - where each day's work begins and ends.

**Contents:**
- Daily note template (automated)
- Current and recent daily notes
- Archive older notes monthly to keep this folder manageable

### 📁 **01 - Areas**

#### **PhD Program Administration**
**Purpose:** Core program operations, policies, and your institutional knowledge about running the PhD program. Think of this as your "program manual" that lives in your head - now documented.

**Key Notes:**
- Program Overview (70 students, structure, your role)
- Annual Cycle Map (what happens when throughout the year)
- Policy & Procedure Index (links to official docs, your notes on how things actually work)

#### **Student Support & Issues**
**Purpose:** Quick-capture system for student interactions and common scenarios. Links to your Microsoft Lists with Casper. Helps you maintain consistency in how you handle similar situations.

**Key Notes:**
- Student Interaction Template (quick capture)
- Common Scenarios Playbook (how you handle recurring situations)
- Individual student notes as needed (link to their advisor, track ongoing issues)

#### **Major Projects**
**Purpose:** Active strategic projects like your advising mentorship system development. These are NOT routine tasks - these are initiatives that transform the program.

**Contents:**
- One note per major project (use project template)
- Living projects that span weeks/months
- Move to Archive when complete

#### **Recurring Processes**
**Purpose:** Documentation of your cyclical work. This is institutional knowledge preservation - what happens every semester, every year. Critical for continuity and potential delegation.

**Key Notes:**
- Process Documentation Template
- Recruitment cycle documentation
- Annual handbook updates process
- Milestone tracking procedures
- Registration period workflows

### 📁 **02 - Resources**

#### **Templates**
**Purpose:** All your note templates live here. When you need to create a new project, meeting note, or student interaction log, you pull from here.

**Contents:**
- Daily Note Template
- Weekly Templates (Monday Start, Friday Close)
- Project Template
- Student Interaction Template
- Meeting Templates (Prep, Notes, Debrief)
- Process Documentation Template

#### **External System Links**
**Purpose:** Your map to Microsoft-land. This is where everything actually lives - you just need quick access to it from your thinking space.

**Contents:**
- Teams Channels Reference (links to key channels)
- SharePoint Sites Map (Resources Hub, admin sites)
- Microsoft Lists Reference (link to student issues list with Casper)
- Quick links to Salesforce, Canvas, Slate, Workday

#### **Meeting Notes**
**Purpose:** Structured notes from meetings, especially recurring ones with Casper or important student/faculty conversations. Links to relevant project or student notes.

**Organization:** 
- Can organize by person, by date, or by topic
- Link back to relevant projects or student notes

#### **People**
**Purpose:** Quick-reference information about your stakeholders. Not a full CRM, but enough to maintain relationships and remember context.

**Contents:**
- Student quick-reference notes (current situation, advisor, special considerations)
- Faculty relationship notes (communication style, lab culture, collaboration history)
- Administrator contacts (who handles what)
- Note: This supplements, not replaces, official student records

#### **Ideas & Backlog**
**Purpose:** Parking lot for things you can't act on now but don't want to forget. Keeps your daily notes clean and your mind clear.

**Contents:**
- Process improvement ideas
- Student suggestions for future consideration
- Project ideas to develop with Claude later
- "Someday/maybe" initiatives

### 📁 **03 - Archive**
**Purpose:** Completed projects, past academic years, old processes. Keeps current workspace clean but preserves institutional knowledge.

**When to Archive:**
- Projects: When fully complete and documented
- Processes: When replaced by new version
- Daily Notes: Monthly (move previous month here)
- Student Notes: When student graduates

---

## Core Templates

### Daily Note Template

```markdown
# {{date:YYYY-MM-DD}} - {{date:dddd}}

## Morning Protocol (9:00-9:15am)

### Today's Calendar
- [ ] Reviewed Outlook calendar
- Key meetings today:
  - 
  - 

### THE Priority for Focus Block (9:15-10:45am)
**What is the ONE thing that matters most today?**



**Why this? Why now?**



### Quick Checks
- [ ] Any urgent student issues? (Check Teams/Lists)
- [ ] Any immediate fires to address before focus work?
- [ ] Everything else can wait until 10:45am

---

## Focus Block (9:15-10:45am)

### Focus Block Rules
- No email
- No Teams
- No reactive work
- Just THE priority

### Work Log
*What got done:*



*Blockers or decisions needed:*



---

## Admin Batch (10:45-11:00am)

- [ ] Process accumulated emails
- [ ] Schedule any pending meetings
- [ ] Quick Teams check-ins
- [ ] Update Microsoft Lists if needed

---

## Interactions Log

### Students
| Student | Topic | Action Needed | List Updated? |
|---------|-------|---------------|---------------|
|         |       |               |               |

### Casper
*Topics discussed:*


*Decisions made:*


*Follow-up needed:*


### Faculty
| Faculty | Topic | Follow-up |
|---------|-------|-----------|
|         |       |           |

---

## Evening Brain Dump (End of Day)

### What Happened Today?
*Brain dump everything - meetings, decisions, tasks, conversations, ideas*




### Smart Prompts
- [ ] **Student conversations** → Did I update Microsoft List with Casper?
- [ ] **Decisions made** → Did I document in relevant project note?
- [ ] **Faculty interactions** → Follow-up needed in Teams?
- [ ] **Files created** → Where do they live? (SharePoint/Teams)
- [ ] **Tasks surfaced** → What's tomorrow's focus block priority?
- [ ] **Ideas emerged** → Add to Ideas & Backlog?
- [ ] **Commitments made** → Calendar blocked? Reminder set?

### Tomorrow's Setup

**Tomorrow's Priority:**


**Prep needed tonight:**
- [ ] 
- [ ] 

**Calendar for tomorrow:**



---

## Notes & Links
*Random observations, links to other notes, things to remember*



---

**Tags:** #daily

**Links:** [[Weekly Plan]], [[Current Projects]]
```

---

### Weekly Monday Start Template

```markdown
# Week of {{date:YYYY-MM-DD}} - Monday Start

## Week Overview

### This Week's Focus
*What are the 2-3 big outcomes for this week?*

1. 
2. 
3. 

### Calendar Scan
*Major meetings, deadlines, commitments this week*

**Monday:**

**Tuesday:**

**Wednesday:**

**Thursday:**

**Friday:**

---

## Project Status Check

### Active Major Projects
| Project | Current Status | This Week's Action | Blocker? |
|---------|----------------|-------------------|----------|
|         |                |                   |          |

### Recurring Process Check
*What cyclical work is happening this week?*
- [ ] Recruitment activities?
- [ ] Milestone deadlines?
- [ ] Annual process cycle work?

---

## Student Issues Scan
*Any urgent or ongoing student situations to monitor?*

- 

### Casper Sync
*Topics to discuss this week:*

1. 
2. 
3. 

---

## This Week's Focus Block Priorities

**Monday Priority:**

**Tuesday Priority:**

**Wednesday Priority:**

**Thursday Priority:**

**Friday Priority:**

---

## Notes
*Strategic thinking, patterns noticed, concerns*



---

**Tags:** #weekly #monday

**Links:** [[{{date:YYYY-MM-DD}}]], [[Monthly Goals]]
```

---

### Weekly Friday Close Template

```markdown
# Week of {{date:YYYY-MM-DD}} - Friday Close

## Week Review

### Intended Focus vs. Reality
*What did I plan to accomplish? What actually happened?*

**Planned:**
1. 
2. 
3. 

**Reality:**
1. 
2. 
3. 

---

## Wins & Accomplishments
*What got done? What went well?*

- 
- 
- 

---

## Challenges & Learning
*What was hard? What did I learn?*

**Challenges:**


**What I learned:**


**What I'll do differently:**


---

## Project Progress

| Project | Progress This Week | Next Steps | Notes |
|---------|-------------------|------------|-------|
|         |                   |            |       |

---

## Student Situations
*Any ongoing issues to monitor into next week?*



### Microsoft List Status
- [ ] All interactions logged
- [ ] Casper updated on key issues
- [ ] Follow-ups scheduled

---

## Loose Ends & Handoff to Monday

### Still Pending
- [ ] 
- [ ] 

### Next Week Preview
*What's coming that I need to prep for?*



### Monday's Priority
*What should Monday's focus block be?*



---

## Process Observations
*Any thoughts on improving workflows, documenting processes, system changes?*



---

## Personal Reflection
*How am I feeling about the work? Energy level? Work-life balance?*



---

**Tags:** #weekly #friday

**Links:** [[Next Monday Start]], [[Monthly Review]]
```

---

### Project Template

```markdown
# [Project Name]

## Project Overview

**Project Lead:** [Your name]  
**Status:** 🟢 Active / 🟡 On Hold / 🔴 Blocked / ✅ Complete  
**Start Date:** YYYY-MM-DD  
**Target Completion:** YYYY-MM-DD  

### Purpose
*Why does this project exist? What problem does it solve?*



### Success Criteria
*What does "done" look like?*

1. 
2. 
3. 

---

## Stakeholders

| Name | Role | Involvement Level | Communication Preference |
|------|------|-------------------|-------------------------|
|      |      |                   |                         |

---

## Project Components

### Key Deliverables
- [ ] 
- [ ] 
- [ ] 

### Technical Requirements
*Tools, platforms, access needed*



### Dependencies
*What has to happen first? Who do I need things from?*

- 

---

## Timeline & Milestones

| Milestone | Target Date | Status | Notes |
|-----------|-------------|--------|-------|
|           |             |        |       |

---

## Decision Log

### Major Decisions
| Date | Decision | Rationale | Who Decided |
|------|----------|-----------|-------------|
|      |          |           |             |

---

## Development Notes

### Work in Progress
*Current work, Claude collaboration sessions, drafts*



### Resources
*Links to docs, files, external systems*

- **Teams Channel:** [link]
- **SharePoint Folder:** [link]
- **Related Microsoft List:** [link]
- **Work Account Collaboration:** [link to relevant work]

---

## Challenges & Solutions

### Current Blockers



### Solved Problems
*Document for future reference*



---

## Communication Plan

### Updates to Stakeholders
*When and how do people get informed?*



### Announcement Plan
*How will this be rolled out?*



---

## Next Steps
- [ ] 
- [ ] 
- [ ] 

---

## Related Notes
- [[Related Project]]
- [[Student Impact Note]]
- [[Process Documentation]]

---

**Tags:** #project #active

**Created:** {{date:YYYY-MM-DD}}  
**Last Updated:** {{date:YYYY-MM-DD}}
```

---

### Student Interaction Template

```markdown
# Student Interaction - [Student Name] - {{date:YYYY-MM-DD}}

## Quick Capture

**Student:** [Name]  
**Date:** {{date:YYYY-MM-DD}}  
**Type:** Meeting / Email / Teams Chat / Quick Question  
**Advisor:** [Faculty Name]

---

## What Happened
*Summary of the conversation/issue*



---

## Action Items

### Student's Next Steps
- [ ] 
- [ ] 

### My Next Steps
- [ ] 
- [ ] 

### Faculty/Advisor Involvement Needed?
- [ ] Yes - what: 
- [ ] No

---

## Follow-Up

**Timeline:**

**Communication Method:**

---

## Documentation

- [ ] **Added to Microsoft List with Casper?**
- [ ] **Emailed student confirming next steps?**
- [ ] **Calendar reminder set for follow-up?**
- [ ] **Related to ongoing issue?** Link: [[Related Note]]

---

## Notes
*Context, concerns, patterns noticed*



---

**Tags:** #student #interaction

**Links:** [[Student - [Name]]], [[Current Student Issues]]
```

---

### Meeting Prep Template

```markdown
# Meeting Prep - [Meeting Name] - {{date:YYYY-MM-DD}}

## Meeting Details

**With:** [Person/People]  
**When:** {{date:YYYY-MM-DD}} at [TIME]  
**Where:** Teams / In-Person / Office  
**Duration:** [X minutes]

---

## Meeting Purpose
*What's this meeting for?*



---

## My Objectives
*What do I need from this meeting?*

1. 
2. 
3. 

---

## Agenda Items

### To Discuss
- [ ] 
- [ ] 
- [ ] 

### Questions to Ask
- 
- 

---

## Background Context
*What does the other person need to know? What's the story so far?*



---

## Decisions Needed
*What needs to be decided in this meeting?*

1. 
2. 

---

## Materials Needed
- [ ] Document/file to share:
- [ ] Data/report to review:
- [ ] Links to send:

---

## Follow-Up Plan
*What happens after this meeting?*



---

**Tags:** #meeting #prep

**Links:** [[Meeting Notes - [Name]]], [[Related Project]]
```

---

### Meeting Notes Template

```markdown
# Meeting Notes - [Meeting Name] - {{date:YYYY-MM-DD}}

## Meeting Info

**With:** [Person/People]  
**Date:** {{date:YYYY-MM-DD}}  
**Duration:** [X minutes]  
**Type:** Recurring / One-time / Check-in

---

## Attendees
- 
- 

---

## Discussion Summary
*Key topics covered*



---

## Decisions Made

| Decision | Rationale | Next Steps | Owner |
|----------|-----------|------------|-------|
|          |           |            |       |

---

## Action Items

### My Actions
- [ ] [Action] - Due: [Date]
- [ ] [Action] - Due: [Date]

### Others' Actions
- [ ] [Person] - [Action] - Due: [Date]
- [ ] [Person] - [Action] - Due: [Date]

---

## Key Takeaways
*Important insights, changes in direction, things to remember*

- 
- 

---

## Follow-Up Needed

**Next Meeting:** [Date/Time if scheduled]

**Between Now and Then:**
- 
- 

---

## Links & References
- **Related Project:** [[Project Name]]
- **Related Student:** [[Student Name]]
- **Documents Discussed:** [SharePoint/Teams links]
- **Microsoft List Updates Needed:** Yes/No

---

**Tags:** #meeting #notes

**Prep:** [[Meeting Prep - [Name]]]
```

---

### Process Documentation Template

```markdown
# Process: [Process Name]

## Process Overview

**Process Owner:** [Your name]  
**Frequency:** Daily / Weekly / Monthly / Semester / Annual  
**Systems Used:** Teams / SharePoint / Lists / Outlook / Salesforce / Canvas / Slate / Workday  
**Documentation Status:** 🟢 Current / 🟡 Needs Update / 🔴 Outdated

---

## Purpose
*Why does this process exist? What problem does it solve?*



---

## When This Happens
*Timing, triggers, cyclical schedule*



---

## Who's Involved

| Role | Person/Team | Responsibilities |
|------|-------------|------------------|
|      |             |                  |

---

## Step-by-Step Process

### Phase 1: [Phase Name]
**Timeline:** [When this happens]

1. **Step:** [Action]
   - **Who:** [Person/role]
   - **Where:** [System/tool]
   - **Output:** [What gets produced]
   - **Tip:** [Helpful note]

2. **Step:** [Action]
   - **Who:** 
   - **Where:** 
   - **Output:** 
   - **Tip:** 

### Phase 2: [Phase Name]
**Timeline:** [When this happens]

1. **Step:** [Action]
   - **Who:** 
   - **Where:** 
   - **Output:** 
   - **Tip:** 

---

## Key Deadlines
*Critical dates that can't be missed*

| Deadline | Task | Consequence if Missed |
|----------|------|----------------------|
|          |      |                      |

---

## Common Issues & Solutions

### Issue: [Problem that comes up]
**Solution:** 


### Issue: [Problem that comes up]
**Solution:** 


---

## Resources & Links

- **Official Policy:** [Link to SharePoint/handbook]
- **Forms/Templates:** [Link to Teams/SharePoint]
- **Relevant Microsoft List:** [Link]
- **Contact for Questions:** [Person/office]

---

## Improvement Ideas
*Notes for future optimization*



---

## Version History

| Date | Change | Reason |
|------|--------|--------|
|      |        |        |

---

**Tags:** #process #documentation

**Related:** [[Annual Cycle Map]], [[PhD Program Administration]]

**Last Reviewed:** {{date:YYYY-MM-DD}}
```

---

### Student Quick-Reference Note Template

```markdown
# Student: [Full Name]

## Quick Facts

**Program Year:** [1st/2nd/3rd/4th/5th+]  
**Advisor:** [[Faculty - [Name]]]  
**Research Area:** [Brief description]  
**Expected Graduation:** [Semester Year]

---

## Current Status

**Academic Standing:** Good / Probation / Leave  
**Milestone Status:** [On track / Behind / Ahead]

**Current Focus:**


---

## Advising Notes

### Advising Style Needs
*How does this student work best? What do they need from you?*



### Special Considerations
*Accommodations, circumstances, context to remember*



---

## Interaction History

*Link to recent interactions*
- [[Student Interaction - [Date]]]
- [[Student Interaction - [Date]]]

---

## Ongoing Issues
*Track in Microsoft List, summarize here*



---

## Milestones

| Milestone | Target Date | Status | Notes |
|-----------|-------------|--------|-------|
| Qualifier |             |        |       |
| Proposal  |             |        |       |
| Defense   |             |        |       |

---

## Quick Links
- **Student Record:** [University system link]
- **Advisor Contact:** [Faculty note link]
- **Microsoft List:** [Relevant issues]

---

**Tags:** #student #reference

**Created:** {{date:YYYY-MM-DD}}  
**Last Updated:** {{date:YYYY-MM-DD}}
```

---

## System README Note

*Copy this into your vault root as "00 - SYSTEM README"*

```markdown
# Obsidian Workflow System - README

## System Purpose

This Obsidian vault is your personal command center for PhD program administration at CAMD. It's designed to:
- Protect and structure your morning focus time (9-11am)
- Connect your thinking across Microsoft systems (Teams, SharePoint, Lists, Outlook)
- Capture institutional knowledge about running a 70-student PhD program
- Provide smart prompts to keep your workflows consistent
- Document cyclical processes for continuity

**Philosophy:** Obsidian is where you think and plan. Microsoft systems are where you execute and collaborate.

---

## Folder Guide

### 00 - Daily Notes
Your operational hub. Each day's work begins and ends here with structured protocols.

### 01 - Areas

**PhD Program Administration:** Your program manual - policies, annual cycles, how things work.

**Student Support & Issues:** Quick-capture for student interactions, links to Microsoft Lists with Casper.

**Major Projects:** Strategic initiatives like the advising mentorship system. Multi-week/month efforts.

**Recurring Processes:** Institutional knowledge - what happens when throughout the year.

### 02 - Resources

**Templates:** All note templates. Pull from here when creating new notes.

**External System Links:** Your map to Microsoft-land (Teams, SharePoint, Lists, etc.).

**Meeting Notes:** Structured notes, especially for recurring meetings with Casper.

**People:** Quick-reference for students, faculty, administrators. Context for relationships.

**Ideas & Backlog:** Parking lot for future ideas so your daily notes stay focused.

### 03 - Archive
Completed projects, past cycles, graduated students. Preserves history, keeps workspace clean.

---

## Daily Workflow

### Morning (9:00-9:15am)
Use Daily Note template:
1. Review calendar
2. Identify THE priority for focus block
3. Quick check for urgent issues

### Focus Block (9:15-10:45am)
Sacred time. THE priority only. No email, no Teams, no reactive work.

### Admin Batch (10:45-11:00am)
Process emails, schedule meetings, quick Teams/Lists updates.

### Evening Brain Dump
Smart prompts guide you:
- Update Microsoft Lists?
- Document decisions?
- Follow-up needed?
- Tomorrow's priority?

---

## Weekly Rhythms

**Monday:** Week planning, project status, priority setting for each day's focus block.

**Friday:** Week review, wins capture, loose ends, prep Monday's focus.

---

## Integration with Microsoft Systems

This vault doesn't replace your Microsoft tools - it enhances them:

**Microsoft Lists (with Casper):** Track student issues → Obsidian prompts you to update
**Teams:** Communication hub → Obsidian links to channels, drafts messages
**SharePoint:** File repository → Obsidian maps where things live
**Outlook:** Email/calendar → Obsidian helps you prepare and reflect
**Other Systems:** Salesforce, Canvas, Slate, Workday → Reference links in External System Links

---

## Key Templates

1. **Daily Note:** Automated each day, morning/evening structure
2. **Weekly Monday/Friday:** Week planning and review
3. **Project:** For major initiatives
4. **Student Interaction:** Quick capture with prompt to update Lists
5. **Meeting Prep/Notes:** Before and during meetings
6. **Process Documentation:** Capture cyclical workflows

---

## Getting Started

1. Start with today's daily note (auto-generated)
2. Do your first morning protocol (9:00-9:15am)
3. Use your focus block (9:15-10:45am)
4. Do evening brain dump
5. On Monday, add weekly planning
6. On Friday, do weekly review
7. Create project notes as needed
8. Build out student quick-references gradually

---

## Handoff Instructions

If this system needs to be handed off:

1. Read this README first
2. Review folder structure - each folder has clear purpose
3. Daily notes show operational patterns
4. Project notes document active initiatives
5. Process documentation in Recurring Processes folder
6. Student quick-references provide context
7. Ideas & Backlog shows future considerations

**Key Context:** This system supports a solo administrator managing a 70-student PhD program at CAMD, Northeastern University. Heavy use of Microsoft systems (Teams, SharePoint, Lists, Outlook). Morning focus block (9-11am) is sacred for deep work.

---

## Maintenance

**Daily:** Use daily note template (auto-generated)
**Weekly:** Monday start + Friday close
**Monthly:** Archive last month's daily notes
**Quarterly:** Review process documentation for updates
**Annually:** Update annual cycle maps, archive completed projects

---

**Created:** {{date:YYYY-MM-DD}}  
**System Owner:** [Your Name]  
**Questions?** Review individual folder purposes above or check template examples.
```

---

## Setup Instructions

### Step 1: Create Vault & Folders
1. Open Obsidian
2. Create new vault: "PhD Program Administration" (or your preferred name)
3. Create all folders as outlined in structure above

### Step 2: Enable Plugins
1. Settings → Core Plugins → Enable:
   - Daily Notes
   - Templates
   - Backlinks
   - Outgoing Links
   - Tag Pane
   - File Recovery

2. Settings → Daily Notes:
   - Set Daily note template location: `02 - Resources/Templates/Daily Note Template`
   - Set New file location: `00 - Daily Notes`
   - Set Date format: `YYYY-MM-DD`

3. Settings → Templates:
   - Set Template folder location: `02 - Resources/Templates`

### Step 3: Add Templates
1. Create a new note in `02 - Resources/Templates` for each template above
2. Copy the template content
3. Name it appropriately (e.g., "Daily Note Template", "Project Template")

### Step 4: Create Your First Notes
1. Create the README: Copy "System README" content to root, name it "00 - SYSTEM README"
2. Create your first daily note (should auto-generate when you use Daily Notes plugin)
3. Try your first morning protocol

### Step 5: Start Building
**Week 1:**
- Use daily notes consistently
- Create 2-3 student quick-reference notes
- Start one project note for your advising system work
- Do Monday/Friday weekly notes

**Week 2:**
- Add meeting notes as you have meetings
- Start documenting one recurring process
- Populate External System Links with your Teams/SharePoint references

**Week 3:**
- Refine templates based on what's working
- Add faculty relationship notes as needed
- Build out Ideas & Backlog

---

## Tips for Success

1. **Start small:** Just use daily notes for first week
2. **Morning protocol is key:** The 9:00-9:15 structure protects your focus time
3. **Link liberally:** Use [[double brackets]] to connect related notes
4. **Trust the evening prompts:** They'll help you stay consistent
5. **Review weekly:** Friday close is where you learn and adjust
6. **Archive regularly:** Keep current workspace clean
7. **Iterate:** Adjust templates to fit your actual workflow

---

## Questions?

Refer to the System README note in your vault root for quick reference on any folder's purpose.