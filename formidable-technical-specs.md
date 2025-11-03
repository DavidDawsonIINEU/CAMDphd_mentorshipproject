# CAMD PhD Mentoring System - Formidable Technical Specifications

**Implementation Guide for WordPress/Formidable Forms**  
**Version:** 1.0  
**Date:** November 2025  
**For:** CAMD PhD in Interdisciplinary Design and Media

---

## TABLE OF CONTENTS

1. [System Overview](#system-overview)
2. [Prerequisites & Setup](#prerequisites-setup)
3. [User Account Configuration](#user-accounts)
4. [Form 1: Individual Development Plan](#form-1-idp)
5. [Form 2: Lab Manual](#form-2-lab-manual)
6. [Form 3: Advising Compact](#form-3-compact)
7. [Form 4: Summer Check-in](#form-4-summer)
8. [Form 5: Fall Check-in](#form-5-fall)
9. [Form 6: Annual Review (360°)](#form-6-annual)
10. [Views Configuration](#views-config)
11. [Email Notifications](#notifications)
12. [Testing Checklist](#testing)
13. [Troubleshooting](#troubleshooting)

---

## 1. SYSTEM OVERVIEW {#system-overview}

### Architecture Summary
- **Platform:** WordPress with Formidable Forms Pro
- **Users:** 77 students + 57 faculty = 134 total accounts
- **Forms:** 6 interconnected forms with data sharing
- **Storage:** WordPress database (CampusPress)
- **Access:** Role-based permissions (Student, Faculty, Administrator)

### Integration Flow
```
IDP (Foundation) → Compact (Student + Faculty)
    ↓                      ↓
Lab Manual         Check-ins (Summer/Fall) ← Compact
    ↓                      ↓
    └──────────→  Annual Review (360°)
```

### Key Features
- Data flows automatically between forms (no re-entry)
- Discipline-specific adaptations (STEM/Humanities/Practice-Based)
- Front-end editing (students can update, advisors can view/add)
- File uploads (CV/resume storage)
- Conditional logic (form adapts based on previous answers)
- Email notifications (to student, faculty, Academic Director)

---

## 2. PREREQUISITES & SETUP {#prerequisites-setup}

### Verify Formidable Capabilities

**Before starting, confirm you have:**
- [ ] Formidable Forms Pro installed and activated
- [ ] Formidable Views add-on available
- [ ] Front-end editing capabilities
- [ ] File upload field type
- [ ] Conditional logic options
- [ ] Email notification actions
- [ ] CSV export functionality

**To check:** Navigate to WordPress Admin → Formidable → Add-Ons  
You should see "Views" and other Pro features listed.

### Required WordPress Plugins

**Install these if not already present:**
1. **User Role Editor** (optional but recommended)
   - For creating custom Student/Faculty roles
   - Free plugin: wordpress.org/plugins/user-role-editor/

2. **WP Mail SMTP** (optional but recommended)
   - Ensures email notifications deliver reliably
   - Configure with university SMTP settings

### File Storage Verification

**Check available storage:**
- Go to Media → Library
- Upload test file (10-20MB)
- Verify no errors or warnings
- Contact CampusPress support if limits appear

Expected: At least 5GB available (4GB needed for ~5 years of CV uploads)

---

## 3. USER ACCOUNT CONFIGURATION {#user-accounts}

### Create Custom User Roles (Recommended)

**Option A: Use WordPress Default Roles**
- Set all users as "Subscriber" role
- Formidable filters by user ID to show only their data
- Simplest approach

**Option B: Create Custom Roles (Better)**

Using User Role Editor plugin:

**Create "PhD Student" role:**
- Capabilities:
  - `read` (access WordPress)
  - `frm_submit_entries` (submit forms)
  - `frm_edit_entries` (edit own entries)
  - `frm_view_entries` (view own entries)

**Create "PhD Faculty" role:**
- Capabilities:
  - `read` (access WordPress)
  - `frm_submit_entries` (submit forms)
  - `frm_edit_entries` (edit own and advisees' entries)
  - `frm_view_entries` (view own and advisees' entries)

**Academic Director keeps "Administrator" role** (full access)

### Bulk User Import

**Create CSV file with:**
```
username,email,first_name,last_name,role
jsmith,j.smith@northeastern.edu,Jane,Smith,phd_student
rdoe,r.doe@northeastern.edu,Robert,Doe,phd_faculty
```

**Import process:**
1. WordPress Admin → Users → Add New
2. Use bulk user import plugin (e.g., Import Users from CSV)
3. Map CSV columns to WordPress user fields
4. Set role column to "phd_student" or "phd_faculty"
5. Check "Send password reset email" option
6. Import

**Alternative: Manual creation**
- For 134 users: ~2 minutes each = 4.5 hours total
- For smaller pilot: Create 5-10 test accounts first

---

## 4. FORM 1: INDIVIDUAL DEVELOPMENT PLAN {#form-1-idp}

### Overview
- **Purpose:** Longitudinal tracking of goals, skills, research, career planning
- **Created:** Year 1, updated throughout program
- **Owner:** Student
- **Pages:** Multi-page form (8-10 pages)

### Page 1: Student Profile

**Fields:**

1. **Full Name** (Text)
   - Label: "Full Name"
   - Required: Yes
   - Placeholder: "First Last"

2. **NUID** (Number)
   - Label: "Northeastern University ID (NUID)"
   - Required: Yes
   - Validation: Exactly 10 digits
   - Format: "##########"

3. **Email** (Email)
   - Label: "Northeastern Email"
   - Required: Yes
   - Validation: Must end in "@northeastern.edu"

4. **Start Semester** (Dropdown)
   - Label: "When did you start the program?"
   - Options: Fall 2025, Spring 2026, Fall 2026, etc.
   - Required: Yes

5. **Program Track** (Radio)
   - Label: "Program Track"
   - Options:
     - Regular (5 years)
     - Advanced Entry (4 years)
   - Required: Yes

6. **Department** (Dropdown)
   - Label: "Primary Department (Administrative)"
   - Options:
     - Art + Design
     - Architecture
     - Communication Studies
     - Journalism
     - Music
     - Theatre
   - Required: Yes

7. **Research Approach** (Radio)
   - Label: "Research Approach (Methodological - may differ from department)"
   - Description: "Select the approach that best describes your research methodology. This can be different from your administrative department."
   - Options:
     - STEM/Computational
     - Humanities/Social Science
     - Practice-Based/Creative
     - Multiple approaches (specify below)
   - Required: Yes

8. **Research Approach Details** (Paragraph Text)
   - Label: "If multiple approaches, describe your primary and secondary methodologies"
   - Conditional: Show if "Multiple approaches" selected
   - Required: No
   - Rows: 3

9. **Research Area** (Dropdown)
   - Label: "Research Area"
   - Options:
     - Games + XR
     - Data Visualization
     - HCI / Interaction Design
     - Media Studies
     - Performance Studies
     - Design for Social Change
     - Still developing
     - Other (specify below)
   - Required: Yes

10. **Research Area Other** (Text)
    - Label: "Specify your research area"
    - Conditional: Show if "Other" selected
    - Required: If shown

11. **Primary Advisor Name** (Text)
    - Label: "Primary Advisor Name"
    - Required: Yes

12. **Primary Advisor Email** (Email)
    - Label: "Primary Advisor Email"
    - Required: Yes

13. **Co-Advisor Name** (Text)
    - Label: "Co-Advisor Name (if selected)"
    - Required: No
    - Description: "Leave blank if you haven't selected a co-advisor yet (required by Year 2)"

14. **Co-Advisor Email** (Email)
    - Label: "Co-Advisor Email"
    - Conditional: Show if Co-Advisor Name filled
    - Required: If shown

### Page 2: Year 1 Goals

**Section Header:** "Year 1 Goals & Planning"

**Description:** "For each semester, identify 3-5 specific goals for research, coursework, and professional development."

**Fields:**

15. **Fall Year 1 Goals** (Paragraph Text)
    - Label: "Fall Semester Goals"
    - Placeholder: "Example: Complete INPR 5100, identify potential qualifying exam fields, attend 2 department colloquia, start literature review on..."
    - Required: Yes
    - Rows: 5

16. **Spring Year 1 Goals** (Paragraph Text)
    - Label: "Spring Semester Goals"
    - Required: Yes
    - Rows: 5

17. **Summer Year 1 Goals** (Paragraph Text)
    - Label: "Summer Goals"
    - Required: Yes
    - Rows: 5

### Page 3: Year 2-5 Goals

**Repeat same structure as Page 2 for:**
- Year 2 (Fall/Spring/Summer)
- Year 3 (Fall/Spring/Summer)
- Year 4 (Fall/Spring/Summer)
- Year 5 (Fall/Spring/Summer)

**Note:** Years 3-5 can be less detailed initially, students update as they progress.

### Page 4: Milestone Planning

**Section Header:** "Program Milestones & Target Dates"

18. **Co-Advisor Target Date** (Date)
    - Label: "Target date to select co-advisor"
    - Description: "Required by end of Year 2"
    - Required: Yes

19. **Qualifying Exam Target** (Date)
    - Label: "Target date for Qualifying Exam"
    - Description: "Typically Spring Year 2 or Fall Year 3"
    - Required: Yes

20. **Qualifying Exam Field 1** (Text)
    - Label: "Proposed Qualifying Exam Field 1"
    - Required: No

21. **Qualifying Exam Field 2** (Text)
    - Label: "Proposed Qualifying Exam Field 2"
    - Required: No

22. **Proposal Defense Target** (Date)
    - Label: "Target date for Proposal Defense"
    - Description: "Typically end of Year 3 or Year 4"
    - Required: Yes

23. **Dissertation Defense Target** (Date)
    - Label: "Target date for Dissertation Defense"
    - Description: "Typically Year 5"
    - Required: Yes

### Page 5: Skills Development

24. **Technical Skills** (Checkboxes)
    - Label: "Technical skills to develop"
    - Options (customizable):
      - [ ] Programming/coding
      - [ ] Data analysis
      - [ ] Statistical methods
      - [ ] Design software
      - [ ] Video production
      - [ ] Audio engineering
      - [ ] Fabrication/making
      - [ ] Archival research
      - [ ] Qualitative methods
      - [ ] Other (specify below)
    - Required: No

25. **Technical Skills Other** (Text)
    - Conditional: Show if "Other" checked
    - Required: If shown

26. **Professional Skills** (Checkboxes)
    - Label: "Professional skills to develop"
    - Options:
      - [ ] Academic writing
      - [ ] Grant writing
      - [ ] Teaching
      - [ ] Presenting
      - [ ] Project management
      - [ ] Collaboration
      - [ ] Mentoring
      - [ ] Other (specify below)
    - Required: No

27. **Skill Development Plan** (Paragraph Text)
    - Label: "How will you develop these skills?"
    - Description: "Through coursework, workshops, self-directed learning, collaboration?"
    - Required: Yes
    - Rows: 5

### Page 6: Career Planning (Scaffolded)

**Description:** "These questions will evolve as you progress. Year 1-2: exploration. Year 3-5: concrete planning."

28. **Career Interests** (Checkboxes)
    - Label: "What types of careers interest you? (check all that apply)"
    - Options:
      - [ ] Academic (tenure-track faculty)
      - [ ] Research (non-academic, think tanks, R&D)
      - [ ] Industry (corporate, startups)
      - [ ] Arts/Creative practice
      - [ ] Nonprofit/Social sector
      - [ ] Government
      - [ ] Consulting
      - [ ] Entrepreneurship
      - [ ] Still exploring
    - Required: Yes

29. **Career Exploration** (Paragraph Text)
    - Label: "What are you curious about regarding careers?"
    - Conditional: Show if in Year 1-2
    - Required: Yes if shown
    - Rows: 5

30. **Career Planning** (Paragraph Text)
    - Label: "What specific career paths are you pursuing?"
    - Conditional: Show if in Year 3+
    - Required: Yes if shown
    - Rows: 5

31. **Professional Network** (Paragraph Text)
    - Label: "Who is in your professional network? Who would you like to connect with?"
    - Required: No
    - Rows: 4

### Page 7: Documentation Archive

**Description:** "Your CV/Resume will be uploaded through check-ins. This section tracks your archive."

32. **CV Archive Display** (HTML block)
    - Display list of uploaded CVs from check-ins (using Formidable View)
    - Show: Date uploaded, Filename, Download link

### Page 8: Completion & Confirmation

33. **Review Checkbox** (Checkbox)
    - Label: "I have reviewed my IDP and it accurately reflects my goals and plans"
    - Required: Yes

34. **Submit Button**
    - Label: "Save IDP"
    - Description: "You can update your IDP anytime by returning to this form"

### Form Actions (IDP)

**Action 1: Email to Student**
- Trigger: On form submission
- To: [email field]
- Subject: "Your IDP has been saved"
- Message: "Your Individual Development Plan has been saved successfully. You can update it anytime by visiting [form URL]."

**Action 2: Email to Academic Director**
- Trigger: On form submission
- To: d.dawson@northeastern.edu
- Subject: "IDP submitted: [Full Name]"
- Message: Include all form data or link to view entry

**Action 3: Create View**
- Create Formidable View showing IDP data
- Filter: Show only current user's entry
- Allow front-end editing
- Display on WordPress page "My IDP"

### Conditional Logic Notes (IDP)

- Research Approach Details → Shows if "Multiple approaches" selected
- Co-Advisor Email → Shows if Co-Advisor Name filled
- Career questions → Different versions for Year 1-2 vs Year 3+
  - Implement using date calculations from Start Semester

---

## 5. FORM 2: LAB MANUAL {#form-2-lab-manual}

### Overview
- **Purpose:** Faculty document lab culture and expectations
- **Created:** Once by faculty, updated annually
- **Owner:** Faculty
- **Pages:** Multi-page form (6-8 pages)
- **Three Templates:** STEM, Humanities, Practice-Based

### Template Selection Strategy

**Option A: Single Form with Conditional Sections**
- One form with sections that show/hide based on research approach selection
- More complex but unified experience

**Option B: Three Separate Forms** (Recommended)
- Form 2A: Lab Manual - STEM
- Form 2B: Lab Manual - Humanities
- Form 2C: Lab Manual - Practice-Based
- Simpler, faculty choose which template matches their work

**Proceeding with Option B (three forms):**

### Form 2A: Lab Manual - STEM/Computational

**Page 1: Faculty Profile**

1. **Faculty Name** (Text)
   - Auto-populate from logged-in user
   - Required: Yes

2. **Faculty Email** (Email)
   - Auto-populate from logged-in user
   - Required: Yes

3. **Department** (Dropdown)
   - Same options as IDP
   - Required: Yes

4. **Research Lab/Group Name** (Text)
   - Label: "Lab or research group name (if applicable)"
   - Required: No

5. **Lab Website** (URL)
   - Label: "Lab website URL (if applicable)"
   - Required: No

**Page 2: Research Philosophy**

6. **Research Philosophy** (Paragraph Text)
   - Label: "Describe your research philosophy and approach"
   - Description: "What questions drive your work? What methods do you use? What's the culture of your lab?"
   - Required: Yes
   - Rows: 6

7. **Lab Values** (Paragraph Text)
   - Label: "What values guide your lab? (e.g., collaboration, rigor, creativity, inclusion)"
   - Required: Yes
   - Rows: 4

**Page 3: Communication & Availability**

8. **Typical Work Hours** (Text)
   - Label: "Your typical work hours/days"
   - Placeholder: "e.g., M-F 9am-6pm, some evenings"
   - Required: Yes

9. **Meeting Frequency** (Radio)
   - Label: "Default meeting frequency with advisees"
   - Options:
     - Weekly
     - Bi-weekly
     - Monthly
     - Varies by project stage
   - Required: Yes

10. **Preferred Communication** (Checkboxes)
    - Label: "How should students reach you?"
    - Options:
      - [ ] Email
      - [ ] Slack
      - [ ] In-person office hours
      - [ ] Scheduled meetings only
      - [ ] Other (specify below)
    - Required: Yes

11. **Response Time Expectations** (Paragraph Text)
    - Label: "What response times should students expect?"
    - Placeholder: "e.g., Email within 48 hours, urgent matters via Slack within 4 hours"
    - Required: Yes
    - Rows: 3

**Page 4: STEM-Specific Expectations**

12. **Code Management** (Paragraph Text)
    - Label: "Code management and version control expectations"
    - Description: "GitHub? Lab standards? Code review process?"
    - Required: Yes
    - Rows: 4

13. **Data Management** (Paragraph Text)
    - Label: "Data management policies"
    - Description: "Where data stored? How documented? Sharing protocols?"
    - Required: Yes
    - Rows: 4

14. **Computational Resources** (Paragraph Text)
    - Label: "Available computational resources"
    - Description: "Servers, clusters, software licenses, etc."
    - Required: No
    - Rows: 3

15. **Reproducibility Standards** (Paragraph Text)
    - Label: "Reproducibility and documentation expectations"
    - Required: Yes
    - Rows: 4

**Page 5: Lab Meetings & Collaboration**

16. **Lab Meeting Schedule** (Text)
    - Label: "Lab meeting schedule (if applicable)"
    - Required: No

17. **Lab Meeting Format** (Paragraph Text)
    - Label: "What happens in lab meetings?"
    - Required: No
    - Rows: 3

18. **Collaboration Expectations** (Paragraph Text)
    - Label: "How do lab members collaborate?"
    - Description: "Help each other? Share resources? Joint projects?"
    - Required: Yes
    - Rows: 4

19. **Authorship Policy** (Paragraph Text)
    - Label: "How are authorship and credit determined?"
    - Required: Yes
    - Rows: 4

**Page 6: Professional Development**

20. **Conference Attendance** (Paragraph Text)
    - Label: "Conference attendance expectations and support"
    - Required: Yes
    - Rows: 3

21. **Publication Goals** (Paragraph Text)
    - Label: "Publication expectations and timeline"
    - Required: Yes
    - Rows: 3

22. **Funding Support** (Paragraph Text)
    - Label: "What funding support is available?"
    - Required: No
    - Rows: 3

**Page 7: Resources & Support**

23. **Equipment Available** (Paragraph Text)
    - Label: "Lab equipment and resources available to students"
    - Required: No
    - Rows: 3

24. **Safety Protocols** (Paragraph Text)
    - Label: "Safety protocols (if applicable)"
    - Required: No
    - Rows: 3

25. **Additional Resources** (Paragraph Text)
    - Label: "Any other resources or information students should know"
    - Required: No
    - Rows: 3

**Page 8: Confirmation**

26. **Last Updated** (Date)
    - Auto-populate with current date
    - Label: "Last updated"

27. **Submit Button**
    - Label: "Save Lab Manual"

### Form 2B: Lab Manual - Humanities/Social Science

**Same structure as STEM with different Page 4:**

**Page 4: Humanities-Specific Expectations**

12. **Reading Practices** (Paragraph Text)
    - Label: "Reading and theoretical engagement expectations"
    - Required: Yes
    - Rows: 4

13. **Writing Practices** (Paragraph Text)
    - Label: "Writing expectations and feedback process"
    - Required: Yes
    - Rows: 4

14. **Qualitative Methods** (Paragraph Text)
    - Label: "Qualitative methods and fieldwork expectations (if applicable)"
    - Required: No
    - Rows: 4

15. **IRB and Ethics** (Paragraph Text)
    - Label: "Research ethics and IRB process"
    - Required: No
    - Rows: 3

16. **Archival Research** (Paragraph Text)
    - Label: "Archival research protocols (if applicable)"
    - Required: No
    - Rows: 3

### Form 2C: Lab Manual - Practice-Based/Creative

**Same structure with different Page 4:**

**Page 4: Practice-Based Expectations**

12. **Practice as Research** (Paragraph Text)
    - Label: "How does creative practice generate knowledge in your work?"
    - Required: Yes
    - Rows: 4

13. **Critique Culture** (Paragraph Text)
    - Label: "Critique norms and feedback expectations"
    - Required: Yes
    - Rows: 4

14. **Studio Access** (Paragraph Text)
    - Label: "Studio/workshop access and resources"
    - Required: Yes
    - Rows: 3

15. **Documentation** (Paragraph Text)
    - Label: "Documentation expectations for creative work"
    - Required: Yes
    - Rows: 4

16. **Exhibition/Performance** (Paragraph Text)
    - Label: "Exhibition/performance planning and support"
    - Required: No
    - Rows: 3

### Form Actions (All Lab Manual Forms)

**Action 1: Email to Faculty**
- Trigger: On submission
- To: [Faculty Email]
- Subject: "Your Lab Manual has been saved"
- Message: "You can update it anytime at [form URL]"

**Action 2: Email to Academic Director**
- Trigger: On submission
- To: d.dawson@northeastern.edu
- Subject: "Lab Manual created: [Faculty Name]"

**Action 3: Create View**
- Publicly viewable Lab Manual for each faculty member
- Display on page "Lab Manuals"
- Filter by faculty member

---

## 6. FORM 3: ADVISING COMPACT {#form-3-compact}

### Overview
- **Purpose:** Collaborative agreement between student and advisor
- **Created:** Year 1, reviewed/updated annually
- **Owners:** Student + Faculty (both contribute)
- **Pages:** Multi-page form (7-9 pages)
- **Key Feature:** Auto-populates from IDP and Lab Manual

### Implementation Approach

**Two Options:**

**Option A: Single Form Both Complete Together**
- Student and advisor sit together
- One person enters data
- Both sign at end

**Option B: Two-Part Form** (Recommended)
- Part 1: Student completes their section (pre-populated from IDP)
- Part 2: Advisor accesses same form entry, adds their section (pre-populated from Lab Manual)
- Both sign electronically

**Proceeding with Option B:**

### Page 1: Identification (Auto-populated)

1. **Student Name** (Text)
   - Auto-populate from IDP
   - Read-only
   - Required: Yes

2. **Student Email** (Email)
   - Auto-populate from IDP
   - Read-only
   - Required: Yes

3. **Primary Advisor Name** (Text)
   - Auto-populate from IDP
   - Read-only
   - Required: Yes

4. **Primary Advisor Email** (Email)
   - Auto-populate from IDP
   - Read-only
   - Required: Yes

5. **Academic Year** (Text)
   - Auto-populate based on current date
   - Read-only
   - Required: Yes

6. **Program Track** (Text)
   - Auto-populate from IDP
   - Read-only

7. **Research Approach** (Text)
   - Auto-populate from IDP
   - Read-only

### Page 2: Student Section - Working Style

**Description:** "The following section is completed by the student. Your responses will help your advisor understand how to best support you."

8. **Preferred Working Style** (Paragraph Text)
   - Label: "Describe your preferred working style"
   - Description: "Do you prefer structured deadlines or flexibility? Work independently or collaboratively? Need frequent check-ins or more autonomy?"
   - Required: Yes
   - Rows: 5

9. **Communication Preferences** (Paragraph Text)
   - Label: "How do you prefer to communicate?"
   - Description: "Email, in-person, Slack? Prefer scheduled meetings or drop-in conversations?"
   - Required: Yes
   - Rows: 4

10. **Feedback Preferences** (Paragraph Text)
    - Label: "What type of feedback is most helpful to you?"
    - Description: "Detailed written comments? High-level guidance? In-person discussion?"
    - Required: Yes
    - Rows: 4

### Page 3: Student Section - Goals & Support

11. **Career Goals** (Paragraph Text)
    - Auto-populate from IDP Career Planning field
    - Editable: Yes
    - Label: "Career goals and aspirations"
    - Required: Yes
    - Rows: 5

12. **Research Goals This Year** (Paragraph Text)
    - Auto-populate from IDP current year goals
    - Editable: Yes
    - Label: "Research goals for this academic year"
    - Required: Yes
    - Rows: 5

13. **Support Needs** (Paragraph Text)
    - Label: "What support do you need from your advisor?"
    - Description: "Technical guidance? Writing feedback? Professional networking? Emotional support during challenges?"
    - Required: Yes
    - Rows: 5

14. **Concerns or Challenges** (Paragraph Text)
    - Label: "Any concerns or anticipated challenges?"
    - Description: "Optional. Helps advisor understand what might be difficult."
    - Required: No
    - Rows: 4

### Page 4: Advisor Section - Mentoring Approach

**Description:** "The following section is completed by the advisor. Your responses help the student understand your approach."

**Note:** These fields only become editable when faculty user accesses the form.

15. **Mentoring Philosophy** (Paragraph Text)
    - Auto-populate from Lab Manual if exists
    - Editable: Yes
    - Label: "Your mentoring philosophy and approach"
    - Required: Yes
    - Rows: 5

16. **Availability** (Paragraph Text)
    - Auto-populate from Lab Manual if exists
    - Editable: Yes
    - Label: "Your availability and typical work hours"
    - Required: Yes
    - Rows: 3

17. **Response Time Commitment** (Text)
    - Auto-populate from Lab Manual if exists
    - Editable: Yes
    - Label: "Typical response time to emails/messages"
    - Placeholder: "e.g., 48 hours for email, 4 hours for urgent Slack"
    - Required: Yes

18. **Resources Provided** (Paragraph Text)
    - Auto-populate from Lab Manual if exists
    - Editable: Yes
    - Label: "Resources you provide (equipment, funding, software, space)"
    - Required: No
    - Rows: 4

### Page 5: Mutual Agreements - Communication

**Description:** "Together, establish clear communication protocols."

19. **Meeting Frequency** (Radio)
    - Label: "Default meeting frequency"
    - Options:
      - Weekly
      - Bi-weekly
      - Monthly
      - Varies (specify below)
    - Required: Yes

20. **Meeting Frequency Details** (Text)
    - Conditional: Show if "Varies" selected
    - Label: "Describe meeting frequency plan"
    - Required: If shown

21. **Meeting Duration** (Dropdown)
    - Label: "Typical meeting duration"
    - Options: 30 min, 45 min, 60 min, 90 min, Varies
    - Required: Yes

22. **Meeting Format** (Checkboxes)
    - Label: "Meeting format"
    - Options:
      - [ ] In-person
      - [ ] Virtual (Zoom/Teams)
      - [ ] Hybrid (varies by need)
    - Required: Yes

23. **Standing Meeting Time** (Text)
    - Label: "Standing meeting time (if applicable)"
    - Placeholder: "e.g., Tuesdays 2-3pm"
    - Required: No

24. **Communication Channels** (Paragraph Text)
    - Label: "Primary communication channels and when to use each"
    - Placeholder: "e.g., Email for scheduling, Slack for quick questions, in-person for complex discussions"
    - Required: Yes
    - Rows: 4

25. **Document Feedback Timeline** (Paragraph Text)
    - Label: "Expected feedback timeline for written work"
    - Placeholder: "e.g., Short drafts (<10 pages) within 1 week, dissertation chapters within 2 weeks"
    - Required: Yes
    - Rows: 3

### Page 6: Mutual Agreements - Milestones

26. **Qualifying Exam Target** (Date)
    - Auto-populate from IDP
    - Editable: Yes
    - Label: "Target date for Qualifying Exam"
    - Required: Yes

27. **Qualifying Exam Preparation** (Paragraph Text)
    - Label: "How will we prepare for qualifying exam?"
    - Description: "Reading lists, practice exams, timeline for preparation"
    - Required: Yes
    - Rows: 4

28. **Proposal Defense Target** (Date)
    - Auto-populate from IDP
    - Editable: Yes
    - Label: "Target date for Proposal Defense"
    - Required: Yes

29. **Proposal Development Plan** (Paragraph Text)
    - Label: "Plan for developing proposal"
    - Required: Yes
    - Rows: 4

30. **Dissertation Defense Target** (Date)
    - Auto-populate from IDP
    - Editable: Yes
    - Label: "Target date for Dissertation Defense"
    - Required: Yes

### Page 7: Mutual Agreements - Professional Development

31. **Conference Attendance Plan** (Paragraph Text)
    - Label: "Conference attendance plans and support"
    - Required: Yes
    - Rows: 3

32. **Publication Goals** (Paragraph Text)
    - Label: "Publication goals for this year"
    - Required: Yes
    - Rows: 3

33. **Teaching Opportunities** (Paragraph Text)
    - Label: "Teaching opportunities and timeline"
    - Required: No
    - Rows: 3

34. **Professional Network Building** (Paragraph Text)
    - Label: "Plans for building professional network"
    - Required: No
    - Rows: 3

### Page 8: Mutual Agreements - Funding & Work

35. **Funding Source** (Radio)
    - Label: "Primary funding source this year"
    - Options:
      - RA (Research Assistantship)
      - TA (Teaching Assistantship)
      - Fellowship
      - Self-funded
      - Other (specify below)
    - Required: Yes

36. **Funding Source Other** (Text)
    - Conditional: Show if "Other" selected
    - Required: If shown

37. **RA Expectations** (Paragraph Text)
    - Conditional: Show if "RA" selected
    - Label: "RA project, hours per week, relation to dissertation"
    - Required: If shown
    - Rows: 4

38. **TA Expectations** (Paragraph Text)
    - Conditional: Show if "TA" selected
    - Label: "TA course, responsibilities, hours per week"
    - Required: If shown
    - Rows: 4

### Page 9: Annual Review & Signatures

39. **Annual Review Process** (Paragraph Text)
    - Label: "How will we conduct annual reviews?"
    - Default text: "We will complete the 360° Annual Review each April, meet to discuss, and update this compact as needed."
    - Editable: Yes
    - Required: Yes
    - Rows: 3

40. **Student Signature** (Text)
    - Label: "Student signature (type full name)"
    - Required: Yes

41. **Student Signature Date** (Date)
    - Auto-populate current date
    - Required: Yes

42. **Advisor Signature** (Text)
    - Label: "Advisor signature (type full name)"
    - Required: Yes

43. **Advisor Signature Date** (Date)
    - Auto-populate current date
    - Required: Yes

44. **Compact Creation Date** (Hidden)
    - Auto-populate with submission date
    - For tracking when compact was established

### Form Actions (Compact)

**Action 1: Email to Student**
- Trigger: On submission
- To: [Student Email]
- Subject: "Your Advising Compact is complete"
- Message: Include PDF attachment or link to view

**Action 2: Email to Advisor**
- Trigger: On submission
- To: [Advisor Email]
- Subject: "Advising Compact complete: [Student Name]"
- Message: Include PDF attachment or link to view

**Action 3: Email to Academic Director**
- Trigger: On submission
- To: d.dawson@northeastern.edu
- Subject: "New Advising Compact: [Student] + [Advisor]"
- Attachments: PDF of compact

**Action 4: Create View**
- Student sees their compact
- Advisor sees all advisees' compacts
- Academic Director sees all compacts

### Workflow Implementation (Compact)

**Step 1:** Student completes Pages 1-3 (their section)
- Form saves as draft (not submitted yet)
- Student status: "Awaiting advisor section"

**Step 2:** Advisor accesses same entry
- Formidable front-end editing feature
- Advisor completes Pages 4-9
- Form submits when advisor signs

**Technical Setup:**
- Use Formidable "Save Draft" feature
- Student initiates, advisor completes
- Requires front-end editing capability
- May need custom workflow using Formidable hooks

---

## 7. FORM 4: SUMMER CHECK-IN {#form-4-summer}

### Overview
- **Purpose:** Developmental reflection every August
- **Created:** 5 times throughout program (Years 1-5)
- **Owner:** Student
- **Pages:** Single-page or 2-page form
- **Key Feature:** CV/Resume upload REQUIRED

### Page 1: Student Identification

1. **Student Name** (Text)
   - Auto-populate from user account
   - Read-only
   - Required: Yes

2. **Submission Date** (Date)
   - Auto-populate current date
   - Read-only

3. **Academic Year** (Dropdown)
   - Label: "Which year are you completing?"
   - Options: Year 1, Year 2, Year 3, Year 4, Year 5
   - Required: Yes

### Page 2: Research Development

**Section Header:** "Research Development"

**Description:** "Take 15 minutes to reflect on your research journey since [last check-in date]. There are no wrong answers—honest reflection helps you and your advisors support your growth."

4. **Research Evolution** (Paragraph Text)
   - Label: "How has your research question or focus evolved since your last check-in?"
   - Required: Yes
   - Rows: 5

5. **New Insights** (Paragraph Text)
   - Label: "What new connections or insights have emerged in your work?"
   - Required: Yes
   - Rows: 5

6. **Changed Understanding** (Paragraph Text)
   - Label: "What's one thing you understand differently now than you did 4 months ago?"
   - Required: Yes
   - Rows: 4

### Discipline-Specific Prompts

**Description:** "The following prompts help you reflect on different aspects of your research. Answer the ones that are relevant to your work—you might answer all of them, just one, or create your own."

7. **STEM/Computational Reflection** (Paragraph Text)
   - Label: "💻 If your work involves STEM/computational methods: How have your experiments, implementations, or technical approaches evolved?"
   - Required: No
   - Rows: 4

8. **Humanities/Theory Reflection** (Paragraph Text)
   - Label: "📚 If your work involves theoretical/critical frameworks: How has your engagement with theory, archives, or fieldwork shaped your thinking?"
   - Required: No
   - Rows: 4

9. **Practice-Based Reflection** (Paragraph Text)
   - Label: "🎨 If your work involves creative/practice-based methods: How has your creative practice generated new questions or directions?"
   - Required: No
   - Rows: 4

10. **Other Research Aspects** (Paragraph Text)
    - Label: "📝 Other aspects of your research:"
    - Placeholder: "Any other developments, challenges, or insights in your work?"
    - Required: No
    - Rows: 4

### Developmental Thinking

11. **Skills Development** (Paragraph Text)
    - Label: "What skills are you developing that you didn't anticipate needing?"
    - Required: Yes
    - Rows: 4

12. **Current Challenges** (Paragraph Text)
    - Label: "What intellectual or creative challenges are you working through right now?"
    - Description: "It's okay to be stuck—this is part of the process"
    - Required: Yes
    - Rows: 4

13. **Uncertainty Areas** (Paragraph Text)
    - Label: "Where do you feel stuck or uncertain? (No judgment—identifying challenges helps find support)"
    - Required: No
    - Rows: 4

### Career Orientation (Scaffolded by Year)

14. **Career Exploration Year 1-2** (Paragraph Text)
    - Conditional: Show if Year 1 or Year 2 selected
    - Label: "What types of work environments are you curious about?"
    - Required: If shown
    - Rows: 4

15. **Career Connection Year 3-4** (Paragraph Text)
    - Conditional: Show if Year 3 or Year 4 selected
    - Label: "How does your current research connect to potential career paths?"
    - Required: If shown
    - Rows: 4

16. **Career Planning Year 5** (Paragraph Text)
    - Conditional: Show if Year 5 selected
    - Label: "What specific next steps are you considering post-graduation?"
    - Required: If shown
    - Rows: 4

### Support & Resources

17. **Support Needed** (Paragraph Text)
    - Label: "What support would be most helpful to you right now?"
    - Placeholder: "People, tools, funding, time, guidance on specific topics?"
    - Required: Yes
    - Rows: 4

18. **Meeting Frequency Check** (Radio)
    - Label: "Are you meeting with your advisor(s) as planned in your compact?"
    - Options:
      - Yes, consistently
      - Mostly, with occasional gaps
      - No, meetings are irregular
      - Compact needs updating
    - Required: Yes

19. **Resources Needed** (Paragraph Text)
    - Label: "What resources do you need to access? (equipment, software, training, connections)"
    - Required: No
    - Rows: 3

### CV/Resume Upload (REQUIRED)

**Section Header:** "Current CV/Resume"

**Description:** "Upload your current CV or Resume. This is required for summer check-ins to track your professional development."

20. **CV/Resume** (File Upload)
    - Label: "Upload current CV or Resume"
    - Required: YES (enforced)
    - Accepted formats: PDF, DOCX
    - Max file size: 52MB
    - Description: "Your CV/resume is archived in your IDP for reference"

### Completion

21. **Progress Bar** (HTML)
    - Show progress through form (e.g., "90% complete")

22. **Submit Button**
    - Label: "Submit Summer Check-in"

### Form Actions (Summer Check-in)

**Action 1: Email to Student**
- Trigger: On submission
- To: [Student Email]
- Subject: "Summer Check-in received"
- Message: "Thank you for completing your summer check-in. Your reflection has been saved and your advisor will receive a copy."

**Action 2: Email to Primary Advisor**
- Trigger: On submission
- To: [Primary Advisor Email from IDP]
- Subject: "Summer Check-in: [Student Name]"
- Message: "[Student Name] has completed their summer check-in. You can view their responses at [link to entry view]."
- Include key highlights (not full responses)

**Action 3: Email to Academic Director**
- Trigger: On submission
- To: d.dawson@northeastern.edu
- Subject: "Summer Check-in submitted: [Student Name]"

**Action 4: Store CV in IDP**
- Save uploaded file
- Link to student's IDP entry
- Display in CV archive section

### Conditional Logic Notes (Summer Check-in)

- Career questions adapt based on Year (1-2, 3-4, or 5)
- All discipline-specific prompts visible (student chooses relevant ones)
- Meeting frequency check triggers follow-up if "irregular" selected

---

## 8. FORM 5: FALL CHECK-IN {#form-5-fall}

### Overview
- **Purpose:** Progress review every December + spring planning
- **Created:** 5 times throughout program
- **Owner:** Student
- **Structure:** Identical to Summer Check-in with additions

### Differences from Summer Check-in

**Same fields 1-19 as Summer Check-in, PLUS:**

### Annual Review Reflection (If Not Year 1)

20. **Last Review Feedback** (Paragraph Text)
    - Conditional: Show if NOT Year 1
    - Label: "What feedback did you receive in your last Annual Review (April)? What progress have you made on that feedback?"
    - Auto-populate: Pull key points from last Annual Review if possible
    - Required: If shown
    - Rows: 5

### Spring Planning

21. **Spring Semester Plans** (Paragraph Text)
    - Label: "Looking ahead to spring semester, what needs to happen?"
    - Description: "Courses, milestones, research activities, writing goals, etc."
    - Required: Yes
    - Rows: 5

22. **Milestone Preparation** (Paragraph Text)
    - Label: "Are you preparing for any major milestones this spring? (Qualifying exam, proposal defense, dissertation defense)"
    - Required: No
    - Rows: 4

### CV/Resume Upload (OPTIONAL in Fall)

23. **CV/Resume** (File Upload)
    - Label: "Upload updated CV or Resume (optional—required in summer only)"
    - Required: NO (optional)
    - Accepted formats: PDF, DOCX
    - Max file size: 52MB
    - Description: "If you've updated your CV since summer, upload the new version"

24. **Submit Button**
    - Label: "Submit Fall Check-in"

### Form Actions (Fall Check-in)

**Same as Summer Check-in** with one change:

**Action 2: Email to Primary Advisor**
- Additional note: "This is [Student]'s fall check-in. They have also reflected on spring semester planning."

---

## 9. FORM 6: ANNUAL REVIEW (360°) {#form-6-annual}

### Overview
- **Purpose:** Comprehensive mutual assessment generating discussion guide
- **Created:** Once per year (every April)
- **Owners:** Student + Faculty (both complete separate parts)
- **Pages:** Multi-page form (8-12 pages)
- **Key Feature:** Four components with confidential faculty section

### Implementation Strategy

**Critical Decision:** How to handle the two-part nature?

**Option A: Two Separate Forms**
- Form 6A: Annual Review - Student Parts (1 & 3)
- Form 6B: Annual Review - Faculty Parts (2 & 4)
- Linked by student ID
- Both submitted separately

**Option B: Single Form, Sequential Completion**
- Student completes Parts 1 & 3 first (saves as draft)
- Faculty then accesses and completes Parts 2 & 4
- Form submits when both complete

**Recommendation: Option A (two forms)** for cleaner separation and confidential faculty section.

### Form 6A: Annual Review - Student Components

**Page 1: Identification**

1. **Student Name** (Text)
   - Auto-populate
   - Read-only
   - Required: Yes

2. **Academic Year Completing** (Dropdown)
   - Label: "Which year are you completing?"
   - Options: Year 1, Year 2, Year 3, Year 4, Year 5
   - Required: Yes

3. **Primary Advisor** (Text)
   - Auto-populate from IDP
   - Read-only

4. **Review Date** (Date)
   - Auto-populate current date

### Page 2: Part 1 - Student Self-Assessment

**Section Header:** "Part 1: Student Self-Assessment"

**Description:** "Reflect honestly on your progress this year. This helps your advisor understand your perspective and supports a productive review conversation."

5. **Research Progress** (Paragraph Text)
   - Label: "Describe your research progress this year"
   - Description: "What did you accomplish? What challenges did you face? How has your work evolved?"
   - Required: Yes
   - Rows: 6

6. **Milestones Achieved** (Checkboxes)
   - Label: "Milestones completed this year"
   - Options:
     - [ ] Selected co-advisor
     - [ ] Passed qualifying exam
     - [ ] Defended proposal
     - [ ] Defended dissertation
     - [ ] Other (specify below)
   - Required: No

7. **Milestones Other** (Text)
   - Conditional: Show if "Other" checked
   - Required: If shown

8. **Skills Developed** (Paragraph Text)
    - Label: "What skills have you developed this year?"
    - Required: Yes
    - Rows: 5

9. **Publications/Presentations** (Paragraph Text)
    - Label: "Publications, presentations, exhibitions, or creative works completed or in progress"
    - Required: No
    - Rows: 4

10. **Challenges Encountered** (Paragraph Text)
    - Label: "What challenges did you encounter and how did you address them?"
    - Required: Yes
    - Rows: 5

11. **Growth Areas** (Paragraph Text)
    - Label: "What are your areas for growth?"
    - Description: "Where do you want to improve or develop further?"
    - Required: Yes
    - Rows: 5

12. **Career Planning Progress** (Paragraph Text)
    - Label: "Progress on career planning and professional development"
    - Required: Yes
    - Rows: 4

13. **Goals for Next Year** (Paragraph Text)
    - Label: "Goals for next academic year"
    - Required: Yes
    - Rows: 5

### Page 3: Part 3 - Student Feedback on Advising

**Section Header:** "Part 3: Your Feedback on Advising (NEW - 360° Component)"

**Description:** "Your honest feedback helps your advisor improve their mentoring. This is developmental, not evaluative. Your advisor will see these responses as part of the 360° review process."

14. **Communication & Accessibility** (Paragraph Text)
    - Label: "How has communication and accessibility been this year?"
    - Description: "Meeting frequency, response times, availability"
    - Required: Yes
    - Rows: 5

15. **Quality of Guidance** (Paragraph Text)
    - Label: "Describe the quality of guidance you've received"
    - Description: "Research direction, feedback on work, professional advice"
    - Required: Yes
    - Rows: 5

16. **What's Working Well** (Paragraph Text)
    - Label: "What's working well in your advising relationship?"
    - Required: Yes
    - Rows: 5

17. **What Could Improve** (Paragraph Text)
    - Label: "What could improve in your advising relationship?"
    - Description: "Be specific and constructive"
    - Required: Yes
    - Rows: 5

18. **Specific Requests** (Paragraph Text)
    - Label: "Are there specific changes or adjustments you'd like to request?"
    - Required: No
    - Rows: 4

19. **Additional Feedback** (Paragraph Text)
    - Label: "Any additional feedback for your advisor?"
    - Required: No
    - Rows: 4

### Page 4: Confirmation

20. **Student Signature** (Text)
    - Label: "Type your full name to confirm this review"
    - Required: Yes

21. **Signature Date** (Date)
    - Auto-populate

22. **Submit Button**
    - Label: "Submit Student Self-Assessment & Feedback"

### Form 6B: Annual Review - Faculty Components

**Page 1: Identification**

1. **Faculty Name** (Text)
   - Auto-populate
   - Read-only

2. **Student Being Reviewed** (Dropdown)
   - Label: "Select advisee for this review"
   - Options: Auto-populate list of faculty's advisees
   - Required: Yes

3. **Academic Year** (Dropdown)
   - Options: Year 1, Year 2, Year 3, Year 4, Year 5
   - Required: Yes

4. **Review Date** (Date)
   - Auto-populate

### Page 2: Part 2 - Faculty Assessment (Shared Section)

**Section Header:** "Part 2: Faculty Assessment of Student (Student Will See This Section)"

**Description:** "This section will be shared with your student as part of the 360° review. Provide honest, constructive feedback."

5. **Research Progress Assessment** (Paragraph Text)
   - Label: "Assess student's research progress this year"
   - Required: Yes
   - Rows: 6

6. **Skills Development Observed** (Paragraph Text)
   - Label: "What skills has the student developed?"
   - Required: Yes
   - Rows: 5

7. **Areas of Strength** (Paragraph Text)
   - Label: "What are this student's key strengths?"
   - Required: Yes
   - Rows: 5

8. **Areas for Growth** (Paragraph Text)
   - Label: "What areas would benefit from further development?"
   - Description: "Be specific and constructive"
   - Required: Yes
   - Rows: 5

9. **Recommendations** (Paragraph Text)
   - Label: "Recommendations for the student for next year"
   - Required: Yes
   - Rows: 5

10. **Progress Toward Milestones** (Radio)
    - Label: "Overall progress toward program milestones"
    - Options:
      - Exceeds expectations
      - Meets expectations
      - Needs improvement
      - Serious concerns
    - Required: Yes

### Page 3: Part 2 - Confidential Faculty Section

**Section Header:** "Confidential Section (Academic Director Only - Student Will NOT See This)"

**Important Note Displayed Prominently:**
> "This section is CONFIDENTIAL. Responses will be visible ONLY to the Academic Director and will NOT be shared with the student. Use this section for probation/dismissal considerations or serious concerns requiring administrative review."

11. **Probation Consideration** (Radio)
    - Label: "Should this student be considered for academic probation?"
    - Options:
      - No
      - Yes - provide rationale below
    - Required: Yes

12. **Probation Rationale** (Paragraph Text)
    - Conditional: Show if "Yes" selected above
    - Label: "Rationale and supporting evidence for probation consideration"
    - Required: If shown
    - Rows: 6

13. **Dismissal Consideration** (Radio)
    - Label: "Should this student be considered for dismissal from the program?"
    - Options:
      - No
      - Yes - provide rationale below
    - Required: Yes

14. **Dismissal Rationale** (Paragraph Text)
    - Conditional: Show if "Yes" selected above
    - Label: "Rationale and supporting evidence for dismissal consideration"
    - Required: If shown
    - Rows: 6

15. **Serious Concerns** (Radio)
    - Label: "Are there serious concerns requiring immediate Academic Director review?"
    - Options:
      - No
      - Yes - describe below
    - Required: Yes

16. **Serious Concerns Description** (Paragraph Text)
    - Conditional: Show if "Yes" selected above
    - Label: "Describe concerns and recommended actions"
    - Required: If shown
    - Rows: 6

17. **Confidential Notes** (Paragraph Text)
    - Label: "Additional confidential notes for Academic Director"
    - Description: "Any other information that should not be shared with student but is important for program administration"
    - Required: No
    - Rows: 5

### Page 4: Part 4 - Faculty Self-Reflection

**Section Header:** "Part 4: Faculty Self-Reflection (NEW - 360° Component)"

**Description:** "This section demonstrates your openness to growth as a mentor. Your student will see these responses, modeling mutual accountability."

18. **What's Working Well** (Paragraph Text)
    - Label: "What's working well in this advising relationship?"
    - Required: Yes
    - Rows: 5

19. **Areas to Improve** (Paragraph Text)
    - Label: "What areas of your mentoring could you improve to better support this student?"
    - Description: "Be honest—this models growth mindset"
    - Required: Yes
    - Rows: 5

20. **Commitments for Next Year** (Paragraph Text)
    - Label: "What commitments are you making for the year ahead?"
    - Description: "Specific actions you'll take to support student's success"
    - Required: Yes
    - Rows: 5

21. **Support Needed** (Paragraph Text)
    - Label: "What resources or support would help you be a better advisor to this student?"
    - Required: No
    - Rows: 4

### Page 5: Compact Updates

22. **Compact Changes Needed** (Radio)
    - Label: "Does the Advising Compact need updating based on this review?"
    - Options:
      - No, compact is still accurate
      - Yes, minor updates needed
      - Yes, significant revisions needed
    - Required: Yes

23. **Proposed Compact Changes** (Paragraph Text)
    - Conditional: Show if "Yes" to updates
    - Label: "What changes should be made to the compact?"
    - Required: If shown
    - Rows: 5

### Page 6: Signatures

24. **Faculty Signature** (Text)
    - Label: "Type your full name to confirm this review"
    - Required: Yes

25. **Signature Date** (Date)
    - Auto-populate

26. **Submit Button**
    - Label: "Submit Faculty Assessment & Reflection"

### Form Actions (Annual Review)

**Action 1: Email to Student (after student submits 6A)**
- To: [Student Email]
- Subject: "Annual Review Part 1 received"
- Message: "Thank you for completing your self-assessment. Your advisor will now complete their assessment."

**Action 2: Email to Faculty (after student submits 6A)**
- To: [Faculty Email]
- Subject: "[Student Name] has completed Annual Review Part 1"
- Message: "Please complete your assessment at [link to Form 6B]"

**Action 3: Email to Academic Director (URGENT - after faculty submits 6B)**
- To: d.dawson@northeastern.edu
- Subject: "Annual Review submitted: [Student Name] - [FLAG IF PROBATION/DISMISSAL CHECKED]"
- Message: Include:
  - Link to full review
  - Highlight if probation/dismissal flagged (in subject line)
  - Confidential notes summary

**Action 4: Email to Student (after faculty submits 6B)**
- To: [Student Email]
- Subject: "Annual Review complete - Schedule discussion with advisor"
- Message: "Your annual review is complete. Please schedule a meeting with your advisor to discuss. You can view the shared sections at [link]."
- **Do NOT include confidential faculty section**

**Action 5: Email to Faculty (after faculty submits 6B)**
- To: [Faculty Email]
- Subject: "Annual Review complete: [Student Name]"
- Message: "Your review is complete. Please schedule a meeting with [Student] to discuss."

**Action 6: Generate Discussion Guide (Advanced)**
- Create Formidable View that compares:
  - Student self-assessment vs Faculty assessment (areas of alignment/disconnect)
  - Student feedback on advising vs Faculty self-reflection
  - Action items for both parties
- Display this view when both forms submitted

### Conditional Logic Notes (Annual Review)

**Critical Implementation:**
- Probation/Dismissal rationale fields ONLY show if "Yes" selected
- Confidential section clearly marked and not included in student-facing views
- Discussion guide only generated after BOTH forms submitted
- Email to Academic Director URGENT if flags checked

---

## 10. VIEWS CONFIGURATION {#views-config}

### Overview
Formidable Views allow you to display submitted form data back to users. Essential for creating dashboards and enabling data reference.

### View 1: Student IDP Dashboard

**Purpose:** Show student their complete IDP + all check-ins + annual reviews

**Configuration:**
- **Data Source:** Multiple forms (IDP, Summer Check-ins, Fall Check-ins, Annual Reviews)
- **Filter:** Current logged-in user only
- **Display:** Custom HTML layout

**Layout:**
```
━━━ YOUR IDP ━━━
[Profile summary]
[Current year goals]
[Upcoming milestones]

━━━ CHECK-IN HISTORY ━━━
✓ Summer Year 1 (Aug 2025) - [View]
✓ Fall Year 1 (Dec 2025) - [View]
⚠ Summer Year 2 (Due Aug 2026)

━━━ ANNUAL REVIEWS ━━━
✓ Year 1 Review (Apr 2026) - [View shared sections]

━━━ CV/RESUME ARCHIVE ━━━
[List of uploaded CVs with dates and download links]
```

**Front-End Editing:** Enable so students can update IDP anytime

### View 2: Faculty Advisee Dashboard

**Purpose:** Show faculty all their advisees and their submissions

**Configuration:**
- **Data Source:** All forms
- **Filter:** Show entries where Primary Advisor = logged-in faculty member
- **Display:** Table format with links to detailed views

**Columns:**
- Student Name
- Year in Program
- IDP (View link)
- Most Recent Check-in (Date and link)
- Annual Review Status (Complete/Pending)
- Compact (View link)

### View 3: Academic Director Complete Dashboard

**Purpose:** Show all students, all submissions, completion tracking

**Configuration:**
- **Data Source:** All forms
- **Filter:** None (show all)
- **Display:** Table with sorting/filtering

**Columns:**
- Student Name
- Year
- Advisor
- IDP Status
- Check-ins Complete (count)
- Annual Review Status
- Flags (if probation/dismissal noted)
- Last Activity Date

**Additional Features:**
- Export to CSV
- Search by student name
- Filter by year, advisor, or status
- Highlight overdue submissions

### View 4: Lab Manual Directory

**Purpose:** Public listing of all faculty lab manuals

**Configuration:**
- **Data Source:** Lab Manual forms (all 3 types)
- **Filter:** None (show all)
- **Display:** Grid or list format

**Information Shown:**
- Faculty Name
- Research Area
- Lab/Group Name (if applicable)
- View Lab Manual (link)

### View 5: Annual Review Discussion Guide

**Purpose:** Generate discussion guide after both student and faculty complete annual review

**Configuration:**
- **Data Source:** Both Annual Review forms
- **Filter:** Match student ID
- **Display:** Custom HTML comparing responses

**Content:**
```
━━━ AREAS OF ALIGNMENT ━━━
[Where student and faculty agree]

━━━ AREAS TO DISCUSS ━━━
[Where perspectives differ]

━━━ STUDENT FEEDBACK ON ADVISING ━━━
[Part 3 responses]

━━━ FACULTY SELF-REFLECTION ━━━
[Part 4 responses]

━━━ ACTION ITEMS ━━━
For Student: [from faculty recommendations]
For Advisor: [from faculty commitments]

━━━ COMPACT UPDATES NEEDED ━━━
[If flagged]
```

---

## 11. EMAIL NOTIFICATIONS {#notifications}

### Notification Strategy

**Principles:**
- Student receives confirmation for everything they submit
- Faculty notified when advisees submit
- Academic Director receives ALL submissions + urgent flags
- Clear subject lines for filtering/organization

### Critical Notification: Probation/Dismissal Flags

**Trigger:** Faculty checks "Yes" for probation or dismissal in Annual Review

**To:** d.dawson@northeastern.edu

**Subject:** 🚨 URGENT: [Student Name] flagged for [PROBATION/DISMISSAL]

**Message:**
```
URGENT REVIEW REQUIRED

Faculty: [Name]
Student: [Name]
Year: [X]
Date: [Date]

FLAG: [Probation / Dismissal]

RATIONALE:
[Faculty's rationale text]

CONFIDENTIAL NOTES:
[Faculty's notes]

View full review: [Link]

Action required: Review flag and follow university procedures for [probation/dismissal] consideration.
```

### Reminder Notifications (Optional Enhancement)

**Using WordPress scheduling plugins:**

**Reminder 1: Summer Check-in Due (early August)**
- To: All active students
- Subject: "Summer Check-in due this month"
- Message: "Your summer check-in (including CV/resume upload) is due by August 31. Complete it at [link]."

**Reminder 2: Fall Check-in Due (early December)**
- To: All active students
- Subject: "Fall Check-in due this month"

**Reminder 3: Annual Review Season (early April)**
- To: All students and faculty
- Subject: "Annual Review process begins - Due April 30"

---

## 12. TESTING CHECKLIST {#testing}

### Pre-Launch Testing

**Phase 1: Form Functionality (Each Form)**
- [ ] All required fields enforce validation
- [ ] Conditional logic works (fields show/hide correctly)
- [ ] File uploads accept correct formats and reject others
- [ ] File size limits enforced (52MB)
- [ ] Auto-population from other forms works
- [ ] Date fields format correctly
- [ ] Email validation works
- [ ] NUID validation (10 digits) works
- [ ] Form saves progress (if enabled)
- [ ] Submit button works
- [ ] Success message displays

**Phase 2: Integration Testing**
- [ ] IDP data flows into Compact correctly
- [ ] Lab Manual data references in Compact
- [ ] Check-ins pull IDP goals correctly
- [ ] Annual Review references previous submissions
- [ ] CV uploads store in IDP archive
- [ ] User filtering works (students see only their data)

**Phase 3: Email Notification Testing**
- [ ] Student confirmation emails send
- [ ] Faculty notification emails send
- [ ] Academic Director receives all submissions
- [ ] URGENT flags work for probation/dismissal
- [ ] Email content includes correct data
- [ ] Links in emails work

**Phase 4: Views Testing**
- [ ] Student IDP Dashboard displays correctly
- [ ] Faculty Advisee Dashboard shows only their advisees
- [ ] Academic Director sees all data
- [ ] Lab Manual Directory works
- [ ] Front-end editing works
- [ ] Discussion Guide generates correctly

**Phase 5: Permissions Testing**
- [ ] Students cannot see other students' data
- [ ] Faculty see only own advisees
- [ ] Academic Director sees everything
- [ ] Confidential faculty sections hidden from students
- [ ] Lab Manuals are publicly viewable (or restricted as intended)

**Phase 6: Mobile Testing**
- [ ] All forms work on phones
- [ ] All forms work on tablets
- [ ] Touch controls work
- [ ] File uploads work on mobile
- [ ] Forms are readable on small screens

### Pilot Testing (5-10 Users)

**Week 1: IDP Creation**
- 3 students create IDPs
- Collect feedback on clarity, length, technical issues

**Week 2: Lab Manual + Compact**
- 2 faculty create Lab Manuals
- Same 3 students + advisors create Compacts
- Test data flow from IDP → Compact
- Collect feedback on collaborative process

**Week 3: Check-ins**
- Pilot students complete check-ins
- Test CV upload
- Faculty review student check-ins
- Collect feedback on developmental questions

**Week 4: Views & Dashboards**
- Test all dashboard views
- Verify data displays correctly
- Test editing capabilities
- Collect usability feedback

### User Acceptance Testing

**Criteria for Launch:**
- [ ] 90%+ of pilot users complete all forms successfully
- [ ] No critical bugs identified
- [ ] Email notifications 100% reliable
- [ ] Data integration working correctly
- [ ] Positive user feedback (survey results)
- [ ] Mobile experience acceptable
- [ ] Load time under 3 seconds for all forms

---

## 13. TROUBLESHOOTING {#troubleshooting}

### Common Issues & Solutions

#### Issue 1: Auto-population Not Working

**Symptom:** IDP data not showing up in Compact

**Causes:**
- Field mapping incorrect
- Student hasn't completed IDP yet
- User ID mismatch

**Solutions:**
1. Verify field mapping in Formidable settings
2. Check that IDP entry exists for this user
3. Confirm user IDs match across forms
4. Use Formidable's "Dynamic field" feature with correct field IDs
5. Test with known working IDP entry

**How to Debug:**
- Formidable → Forms → Compact → Edit
- Find field that should auto-populate
- Check "Default Value" setting
- Should be: `[get param=field_id id=[IDP field ID] user_id=current]`
- Verify IDP field ID is correct

#### Issue 2: File Uploads Failing

**Symptom:** CV/Resume upload returns error

**Causes:**
- File too large (over 52MB)
- Wrong format (not PDF/DOCX)
- Server upload limit too low
- Permissions issue

**Solutions:**
1. Check file size and format first
2. Increase WordPress upload limit in php.ini:
   ```
   upload_max_filesize = 64M
   post_max_size = 64M
   ```
3. Check file upload permissions on server
4. Verify Media Library has space available
5. Test with small (1MB) PDF first

#### Issue 3: Email Notifications Not Sending

**Symptom:** Emails not being received

**Causes:**
- Email action not configured
- SMTP settings incorrect
- Emails going to spam
- WordPress mail function failing

**Solutions:**
1. Verify email actions exist in form settings
2. Install WP Mail SMTP plugin
3. Configure with university SMTP settings
4. Test email with simple test form
5. Check spam folders
6. Add sender address to safe senders list
7. Use Formidable Email Logs to debug

**Test Process:**
- Create simple test form with email action
- Submit form
- Check Formidable → Emails (if logging enabled)
- Verify email content is correct
- Check if email appears in logs as "sent"

#### Issue 4: Students Can See Other Students' Data

**Symptom:** Privacy violation - wrong data visible

**Causes:**
- View filter not configured correctly
- User role permissions too broad
- Formidable security settings incorrect

**Solutions:**
1. Edit View → Filters → Add "User ID = Current User"
2. Check WordPress user roles (should be "Subscriber" or "PhD Student")
3. Verify Formidable Pro security settings
4. Test with two different student accounts
5. Clear cache if using caching plugin

**Critical Check:**
- Log in as Test Student 1
- Verify can only see own data
- Log in as Test Student 2
- Verify sees different data (their own)
- If overlap exists, filter is broken

#### Issue 5: Conditional Logic Not Working

**Symptom:** Fields not showing/hiding correctly

**Causes:**
- Logic rule syntax error
- Field IDs wrong
- Multiple conflicting rules
- JavaScript conflict with theme/plugin

**Solutions:**
1. Edit field → Advanced → Conditional Logic
2. Verify logic is: "Show this field if [Field X] [is equal to] [Value Y]"
3. Check Field X exists and has correct ID
4. Test with simple conditions first
5. Check browser console for JavaScript errors
6. Temporarily disable other plugins to test for conflicts

**Debug Process:**
- Create simple test: Show Field B if Field A = "Yes"
- Test in form preview
- If works, add complexity gradually
- If fails, check field IDs and logic syntax

#### Issue 6: Front-End Editing Not Working

**Symptom:** Faculty cannot edit student-started forms

**Causes:**
- Front-end editing not enabled
- User doesn't have edit permissions
- Form entry locked
- View configuration wrong

**Solutions:**
1. Form Settings → Form Options → Allow Front-End Editing (check)
2. Set "Who can edit entries?" to "Administrator and entry creator"
3. For faculty editing student entries: Custom capability required
4. May need Formidable hooks/custom code
5. Verify entry is not marked as "complete" (if using that feature)

**Alternative Workflow:**
If front-end editing proves too complex:
- Use two-stage process: Student submits → Faculty creates linked entry
- Or: Both fill out form together (one person enters data)

#### Issue 7: Form Too Slow/Timing Out

**Symptom:** Form takes >10 seconds to load or submit

**Causes:**
- Too many fields (over 100)
- Large file uploads
- Complex conditional logic
- Slow server
- Database issues

**Solutions:**
1. Split form into multiple pages (reduce fields per page)
2. Optimize conditional logic (simpler rules)
3. Increase PHP execution time:
   ```
   max_execution_time = 300
   ```
4. Enable caching (but disable for logged-in users)
5. Check server resources (CPU, memory)
6. Optimize database (use plugin like WP-Optimize)

**For IDP specifically:**
- Consider splitting into 2-3 separate forms
- IDP Part 1: Profile + Year 1-2 goals
- IDP Part 2: Year 3-5 goals + Skills
- IDP Part 3: Career planning
- Link forms using hidden user ID field

#### Issue 8: Probation/Dismissal Flags Not Confidential

**Symptom:** Students can see confidential faculty section

**Causes:**
- View configuration includes confidential fields
- Permissions not set correctly
- User role can access restricted data

**Solutions:**
1. Edit View for students → Exclude confidential fields
2. Create separate View for Academic Director only
3. Set View permissions: "Administrator only"
4. Double-check field visibility settings
5. Test by logging in as student account

**Critical Security Check:**
- Log in as test student
- Navigate to Annual Review view
- Verify CANNOT see:
  - Probation consideration
  - Dismissal consideration
  - Confidential notes
- If visible, VIEW IS MISCONFIGURED (fix immediately)

#### Issue 9: Data Loss on Form Submission

**Symptom:** User submits form but data doesn't save

**Causes:**
- Database connection lost
- Form spam protection triggered
- JavaScript error before submit
- Server timeout
- Duplicate entry prevention

**Solutions:**
1. Enable "Save Draft" feature (save as user types)
2. Increase server timeout limits
3. Check Formidable Spam Protection settings (may be blocking)
4. Test with browser console open (check for errors)
5. Verify database has space available
6. Check WordPress debug logs

**Prevention:**
- Always enable auto-save/save draft
- Add "Your data is being saved automatically" message
- Test submission with slow internet connection

#### Issue 10: Discipline-Specific Questions Not Adapting

**Symptom:** Wrong questions showing for research approach

**Causes:**
- Research approach field not triggering conditions
- Conditional logic references wrong field ID
- Value comparison doesn't match exactly

**Solutions:**
1. Verify Research Approach field captures correct value
2. Check conditional logic: Field [Research Approach] [is equal to] [STEM/Computational]
3. Match exact text (case-sensitive)
4. Test with each research approach option
5. Use radio buttons instead of dropdowns (more reliable for conditions)

**Test Each Path:**
- Select STEM → Verify STEM questions show
- Select Humanities → Verify Humanities questions show
- Select Practice-Based → Verify Practice questions show
- Select Multiple → Verify ALL questions show

---

## 14. IMPLEMENTATION TIMELINE

### Recommended Build Sequence

**Week 1: Foundation Setup**
- Day 1-2: User roles and account creation
- Day 3-4: Build Form 1 (IDP)
- Day 5: Test IDP, create student dashboard view

**Week 2: Faculty & Compact**
- Day 1-2: Build Forms 2A, 2B, 2C (Lab Manuals)
- Day 3-4: Build Form 3 (Compact)
- Day 5: Test data flow IDP → Compact

**Week 3: Check-ins & Reviews**
- Day 1-2: Build Forms 4 & 5 (Summer/Fall Check-ins)
- Day 3-5: Build Form 6A & 6B (Annual Review)

**Week 4: Views & Integration**
- Day 1-2: Create all dashboard views
- Day 3-4: Set up all email notifications
- Day 5: Test complete system end-to-end

**Week 5: Pilot Testing**
- 5-10 users test all forms
- Collect feedback
- Fix bugs

**Week 6: Refinement & Launch**
- Implement feedback
- Final testing
- Create training materials
- Bulk user import
- Official launch

---

## 15. TRAINING MATERIALS NEEDED

### For Students

**Video Tutorial: "Getting Started with Your IDP"** (5 min)
- How to log in
- Completing your IDP
- Understanding the sections
- Saving and updating
- Where to find your dashboard

**Written Guide: "Using the Mentoring System"** (2 pages)
- Overview of all forms
- When each form is due
- How to upload CV/resume
- Who sees your information
- How to get help

**Quick Reference Card: "Annual Timeline"**
- September: Create IDP + Compact (Year 1)
- December: Fall Check-in
- April: Annual Review
- August: Summer Check-in + CV

### For Faculty

**Video Tutorial: "Creating Your Lab Manual"** (5 min)
- Choosing the right template
- What to include
- How students will use it
- Updating annually

**Video Tutorial: "Using the Advising Compact"** (5 min)
- How students initiate
- How to complete advisor section
- Making mutual agreements
- Annual review process

**Written Guide: "Faculty Dashboard"** (2 pages)
- Viewing advisee submissions
- Responding to check-ins
- Completing annual reviews
- Understanding confidential flags

### For Academic Director

**Administrator Manual** (10 pages)
- Dashboard overview
- Monitoring completion
- Exporting data
- Handling flags
- Troubleshooting
- Annual maintenance tasks

---

## 16. ANNUAL MAINTENANCE

### Tasks to Complete Each Year

**August:**
- [ ] Review all forms for updates needed
- [ ] Update year options in dropdowns
- [ ] Check file storage space
- [ ] Archive previous year's data (if needed)

**September:**
- [ ] Send welcome email to new students with system info
- [ ] Create accounts for new students/faculty
- [ ] Verify all forms functioning correctly

**April:**
- [ ] Monitor Annual Review completion rates
- [ ] Follow up on overdue submissions
- [ ] Review probation/dismissal flags
- [ ] Generate annual report

**June:**
- [ ] Export all data for backup
- [ ] Generate program-level statistics
- [ ] Update training materials if needed
- [ ] Plan improvements for next year

### Form Updates to Consider

**Add fields for:**
- New research areas as they emerge
- Updated career pathways
- New resources or services
- Policy changes

**Remove/update:**
- Outdated options
- Deprecated services
- Old faculty who left program

---

## 17. DATA EXPORT & ANALYSIS

### Useful Reports to Generate

**Student Progress Report:**
- All students
- Year in program
- Milestones completed
- Check-ins submitted
- Annual review status

**Completion Rate Report:**
- % of students with current IDP
- % completing check-ins on time
- % completing annual reviews
- Identify students needing follow-up

**Faculty Engagement Report:**
- Lab manuals created
- Advisees per faculty
- Annual reviews completed
- Response patterns

**Program Trends Report:**
- Research approaches distribution
- Career pathway interests over time
- Common challenges identified
- Skills development trends

### How to Export Data

**Formidable → Forms → [Form Name] → Entries**
- Click "Export" button
- Choose CSV format
- Select fields to include
- Download file
- Open in Excel for analysis

**Creating Custom Reports:**
- Use Formidable Views with filters
- Display aggregated data
- Create charts/graphs with Excel
- Present to stakeholders

---

## 18. GOING LIVE CHECKLIST

### Pre-Launch (Complete All Items)

**Technical Readiness:**
- [ ] All 6 forms built and tested
- [ ] All Views configured and working
- [ ] All email notifications tested and working
- [ ] User accounts created and roles assigned
- [ ] Permissions verified (students see only their data)
- [ ] Mobile experience tested and acceptable
- [ ] File uploads working correctly
- [ ] Data integration working (IDP → Compact, etc.)
- [ ] Confidential sections hidden from students
- [ ] Backup system in place

**Training & Communication:**
- [ ] Student training video completed
- [ ] Faculty training video completed
- [ ] Administrator manual completed
- [ ] Quick reference cards created
- [ ] Launch email drafted
- [ ] Support process established (who handles questions?)

**Pilot Testing:**
- [ ] 5-10 users successfully completed all forms
- [ ] Feedback collected and incorporated
- [ ] No critical bugs remaining
- [ ] User satisfaction acceptable

**Stakeholder Approval:**
- [ ] Supervisors reviewed and approved
- [ ] Faculty informed and trained
- [ ] Student leaders consulted
- [ ] IT/CampusPress confirmed technical readiness

### Launch Day

**Morning:**
- [ ] Send launch email to all users
- [ ] Activate all forms (remove "Coming Soon" notices)
- [ ] Monitor system for issues
- [ ] Be available for support questions

**First Week:**
- [ ] Daily check of submissions
- [ ] Respond to questions quickly
- [ ] Monitor for technical issues
- [ ] Collect initial feedback

**First Month:**
- [ ] Weekly usage reports
- [ ] Address any bugs promptly
- [ ] Collect user feedback
- [ ] Make minor improvements

---

## 19. SUCCESS METRICS

### How to Measure System Effectiveness

**Adoption Metrics:**
- % of students with completed IDPs (Target: 95%)
- % of faculty with Lab Manuals (Target: 80%)
- % of students with signed Compacts (Target: 90%)
- Check-in completion rate (Target: 85%)
- Annual Review completion rate (Target: 95%)

**Engagement Metrics:**
- Average time to complete each form
- Frequency of IDP updates
- Faculty viewing of student submissions
- Student engagement with check-ins (depth of responses)

**Outcome Metrics:**
- Milestone completion rates (improvement over baseline)
- Student satisfaction with advising (survey)
- Faculty satisfaction with system (survey)
- Reduction in advisor changes
- Reduction in Academic Director mediation needs

**Technical Metrics:**
- Form load time (Target: <3 seconds)
- Email delivery rate (Target: 100%)
- Mobile completion rate (Target: >30%)
- System uptime (Target: 99%)

### Annual Assessment

**Collect data on:**
- Forms completed (counts by type)
- Probation/dismissal flags (track trends)
- Common challenges identified in check-ins
- Career pathway trends
- Skills development patterns

**Survey questions for students:**
- How helpful is the IDP for tracking your progress? (1-5 scale)
- Do check-ins feel developmental or administrative? (1-5 scale)
- Has the system improved communication with your advisor? (Yes/No)
- What would you change about the system? (Open-ended)

**Survey questions for faculty:**
- Does the Lab Manual reduce repeated explanations? (Yes/No)
- Is the Compact helpful for establishing expectations? (1-5 scale)
- Are check-ins useful for monitoring student progress? (1-5 scale)
- What would you change? (Open-ended)

---

## 20. FUTURE ENHANCEMENTS TO CONSIDER

### Phase 2 Additions (Year 2)

**Automated Reminders:**
- Install plugin for scheduled emails
- Reminder 2 weeks before check-ins due
- Reminder for overdue submissions
- Annual review season kick-off email

**Enhanced Analytics:**
- Create dashboard showing program-wide trends
- Visualizations of student progress
- Cohort comparisons
- Research approach distribution charts

**Co-Advisor Agreement Form:**
- Add 7th form for co-advisor relationships
- Triggered when student selects co-advisor in IDP
- Similar to Compact but simpler
- Clarifies co-advisor role

### Phase 3 Additions (Year 3+)

**SharePoint API Integration:**
- Automatic storage of submissions to SharePoint
- Eliminate email-to-admin step
- Central repository managed automatically

**Document Generation Enhancements:**
- Generate branded PDFs automatically
- Include CAMD branding
- Digital signatures (DocuSign integration?)
- Automated PDF delivery

**Advanced Reporting:**
- Programmatic access to data (API)
- Automated monthly reports
- Predictive analytics (which students at risk?)
- Benchmarking against other programs

**Alumni Tracking:**
- Extended IDP after graduation
- Track career outcomes
- Maintain connections
- Network building

---

## CONCLUSION

This technical specification provides complete instructions for implementing the CAMD PhD Mentoring System using WordPress and Formidable Forms. 

### Key Reminders

1. **Build incrementally** - One form at a time, test thoroughly
2. **Pilot before full launch** - 5-10 users catch most issues
3. **Prioritize security** - Confidential sections must stay confidential
4. **Document everything** - Future you will thank current you
5. **Iterate based on feedback** - No system is perfect at launch

### Next Steps

1. Verify Formidable Pro capabilities (30 minutes)
2. Create user accounts (1-4 hours depending on approach)
3. Build Form 1 (IDP) following specifications (4-6 hours)
4. Test with pilot students (1 week)
5. Continue with remaining forms

### Support Resources

- **Formidable Documentation:** formidableforms.com/knowledgebase/
- **WordPress Codex:** wordpress.org/support/
- **CampusPress Support:** Contact your university IT
- **This Document:** Reference throughout implementation

---

**Document Version:** 1.0  
**Created:** November 2025  
**Last Updated:** November 2025  
**For:** CAMD PhD in Interdisciplinary Design and Media  
**Prepared by:** David Dawson with AI assistance  
**Questions:** d.dawson@northeastern.edu

---

**END OF TECHNICAL SPECIFICATIONS**