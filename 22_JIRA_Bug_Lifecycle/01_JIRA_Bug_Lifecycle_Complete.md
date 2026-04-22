# Module 22: JIRA & Bug Lifecycle - Complete Guide

## JIRA में Bug Lifecycle और Workflow Management

---

## 📋 Table of Contents

1. [JIRA Introduction](#jira-intro)
2. [Creating Issues in JIRA](#creating-issues)
3. [Bug Lifecycle & Workflow](#bug-lifecycle)
4. [Issue Linking & Dependencies](#linking)
5. [JIRA Best Practices](#best-practices)
6. [JIRA Reports](#reports)
7. [Practical Examples](#examples)
8. [Interview Questions](#interview)

---

## JIRA Introduction

### What is JIRA?

JIRA एक project management और issue tracking tool है जो teams को bugs, features, और tasks को manage करने में मदद करता है।

**Key Features:**
- Bug tracking
- Issue management
- Project planning
- Workflow automation
- Reporting & analytics
- Team collaboration
- Integration with development tools

### Why JIRA for QA?

```
✓ Centralized bug tracking
✓ Clear workflow management
✓ Priority & severity assignment
✓ Assignment & ownership
✓ Status tracking
✓ Resolution reporting
✓ Traceability
✓ Team communication
✓ Historical data analysis
```

### JIRA Types

1. **Jira Cloud** - Cloud-based, SaaS model
2. **Jira Server** - Self-hosted (discontinued)
3. **Jira Data Center** - Enterprise deployment

---

## Creating Issues in JIRA

### Issue Types

```
BUG
├─ Functional Bug
├─ UI Bug
├─ Performance Bug
├─ Security Bug
└─ Data Bug

TASK
├─ Development Task
├─ Testing Task
├─ Documentation Task
└─ Infrastructure Task

STORY (Feature)
├─ User Story
├─ Epic
└─ Feature Request

SUB-TASK
└─ Breaking down larger issues
```

### Creating a Bug Report

**Step 1: Click "Create Issue"**

**Step 2: Fill Required Fields**

```
Project: eCommerce_Application
Issue Type: Bug
Priority: High
Severity: Critical
```

**Step 3: Complete Bug Details**

**Project:** Select your project  
**Issue Type:** Select "Bug"  
**Summary:** Brief description of the bug  
**Priority:** Critical/High/Medium/Low  
**Severity:** Blocker/Critical/Major/Minor  
**Reporter:** Your name (auto-filled)  
**Assignee:** Developer who'll fix it  
**Description:** Detailed bug description  
**Steps to Reproduce:** How to recreate bug  
**Expected Result:** What should happen  
**Actual Result:** What actually happens  
**Environment:** OS, Browser, Version  
**Attachments:** Screenshots, logs, videos  

### Good Bug Report Example

```
SUMMARY: "Login page crashes when password exceeds 50 characters"

PRIORITY: High
SEVERITY: Critical

DESCRIPTION:
User cannot login when entering password longer than 50 characters.
System shows white screen instead of error message.

STEPS TO REPRODUCE:
1. Open login page
2. Enter email: test@example.com
3. Enter password: "MyPassword@12345MyPassword@12345MyPassword@12345XYZ" (60 chars)
4. Click Login button
5. Observe page behavior

EXPECTED RESULT:
- Show error message "Password must be less than 50 characters"
- Remain on login page
- Keep email field filled

ACTUAL RESULT:
- Page becomes white blank screen
- No error message displayed
- User is confused

ENVIRONMENT:
- OS: Windows 10
- Browser: Chrome 120
- URL: https://app.example.com/login
- Version: 2.5.1

ATTACHMENT: screenshot.png (showing white screen)
```

---

## Bug Lifecycle & Workflow

### Standard Bug Workflow

```
1. OPEN/NEW
   ↓
2. ASSIGNED
   ↓
3. IN PROGRESS
   ↓
4. RESOLVED/FIXED
   ↓
5. IN TESTING (Re-testing)
   ↓
6. VERIFIED/CLOSED
```

### Detailed Workflow States

#### **1. NEW/OPEN**
- Bug just reported
- Awaiting review
- QA Lead reviews for completeness
- **Duration:** 1-2 days

#### **2. ASSIGNED**
- Bug assigned to developer
- Developer accepts/acknowledges
- Developer starts working
- **Duration:** Variable

#### **3. IN PROGRESS**
- Developer actively fixing
- Commit to code
- Code review process
- **Duration:** 1-7 days

#### **4. RESOLVED/FIXED**
- Developer completed fix
- Code merged to branch
- Awaiting QA testing
- **Status:** Developer perspective

#### **5. IN TESTING/VERIFICATION**
- QA re-tests the bug
- Follows exact reproduction steps
- Verifies fix completely
- **Duration:** 1-2 days

#### **6. VERIFIED/CLOSED**
- Bug confirmed fixed
- No longer reproducible
- Ready for release
- **Status:** Final state

### Bug Status Transitions

```
Scenario 1: Bug Fixed on First Attempt
NEW → ASSIGNED → IN PROGRESS → RESOLVED → IN TESTING → VERIFIED

Scenario 2: Bug Needs More Work
NEW → ASSIGNED → IN PROGRESS → RESOLVED → IN TESTING → RE-OPEN → IN PROGRESS...

Scenario 3: Bug is Actually Not a Bug
NEW → ASSIGNED → RESOLVED (As Not a Bug) → CLOSED

Scenario 4: Bug is Duplicate
NEW → ASSIGNED → RESOLVED (Duplicate of #123) → CLOSED
```

### JIRA Workflow Configuration Example

```
Issue Type: Bug

Workflow Transitions:
NEW
  → ASSIGN (button) → ASSIGNED
  → REJECT (button) → CLOSED

ASSIGNED
  → START WORK (button) → IN PROGRESS
  → REASSIGN (button) → ASSIGNED
  → CLOSE (button) → CLOSED

IN PROGRESS
  → RESOLVE (button) → RESOLVED
  → BLOCK (button) → BLOCKED

RESOLVED
  → TEST (button) → IN TESTING
  → REOPEN (button) → IN PROGRESS

IN TESTING
  → VERIFIED (button) → VERIFIED
  → REOPEN (button) → IN PROGRESS

VERIFIED/CLOSED
  → (Terminal state)
```

---

## Issue Linking & Dependencies

### Link Types

```
1. BLOCKS
   Bug A blocks Bug B
   (Must fix A before B)

2. RELATES TO
   Bug A relates to Bug B
   (Similar or related)

3. DUPLICATES
   Bug A duplicates Bug B
   (Same issue reported twice)

4. CHILD OF / PARENT
   Bug A is child of Epic B
   (Hierarchical relationship)

5. RELATES TO (Feature)
   Bug links to Feature request
```

### Creating Links

**In JIRA:**
1. Open Issue → Link Issue
2. Select link type
3. Enter other issue key (e.g., BUG-123)
4. Save

**Example:**
```
BUG-456: "Login button color wrong"
├─ RELATES TO → BUG-457: "Logout button color wrong"
└─ CHILD OF → EPIC-10: "UI Color Refactoring"

BUG-789: "Search crashes"
├─ BLOCKS → BUG-790: "Can't view search results"
└─ DUPLICATES → BUG-123: "Search functionality broken"
```

---

## JIRA Best Practices

### 1. Effective Summarization

```
❌ BAD: "Bug in login"
✅ GOOD: "Login page throws 500 error for email with special characters"

❌ BAD: "Payment not working"
✅ GOOD: "Payment gateway timeout when processing orders > $1000"

❌ BAD: "UI issue"
✅ GOOD: "Dashboard layout broken on mobile screen 375px width"
```

### 2. Detailed Description

```
Use Template:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

ISSUE:
[What is broken?]

STEPS TO REPRODUCE:
1. [First step]
2. [Second step]
3. ...

EXPECTED BEHAVIOR:
[What should happen]

ACTUAL BEHAVIOR:
[What actually happens]

IMPACT:
[How many users affected]

ENVIRONMENT:
[OS, Browser, Version]

ATTACHMENTS:
[Screenshots, Logs]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### 3. Priority vs Severity

```
SEVERITY (What is wrong):
- BLOCKER: System completely broken
- CRITICAL: Core functionality broken
- MAJOR: Important feature not working
- MINOR: Minor functionality affected

PRIORITY (How urgent):
- HIGHEST: Fix immediately
- HIGH: Fix in this sprint
- MEDIUM: Fix when possible
- LOW: Fix in future release
```

### 4. Assignment Best Practices

```
✓ Assign to correct owner
✓ Add clear comments for context
✓ Mention decision makers
✓ Tag affected teams
✓ Set realistic due dates
✓ Update status regularly
```

### 5. Communication via JIRA

```
Use Comments for:
- Clarifications
- Updates on progress
- Questions to reporter
- Additional findings
- Solution summary

Mention users with @ symbol:
"@dev-lead Please review this critical issue"
"@qa-team Please retest after fix"
```

---

## JIRA Reports

### Common Reports

#### **1. Defect Summary Report**

```
Shows:
- Total bugs in project
- Open vs Closed
- By priority
- By severity
- By assignee
- Trend over time
```

#### **2. Bug Burndown Report**

```
Shows:
- Bugs opened per day
- Bugs closed per day
- Net open bugs trend
- Sprint progress
- Helps predict release date
```

#### **3. Defect Distribution**

```
By Priority:
- Critical: 5 bugs
- High: 12 bugs
- Medium: 25 bugs
- Low: 18 bugs

By Severity:
- Blocker: 2 bugs
- Critical: 8 bugs
- Major: 28 bugs
- Minor: 22 bugs

By Module:
- Login: 8 bugs
- Payment: 15 bugs
- Search: 12 bugs
- Dashboard: 10 bugs
- Other: 25 bugs
```

#### **4. Resolution Time Report**

```
Average time to resolve:
- Critical bugs: 2 days
- High bugs: 5 days
- Medium bugs: 10 days
- Low bugs: 20 days
```

---

## Practical Examples

### Real Bug Workflow Example

```
2026-04-22 10:00 AM
Reporter: Priya (QA)
Summary: "Checkout page fails when cart exceeds 10 items"

Status: NEW
↓

2026-04-22 11:30 AM
QA Lead reviews and approves the bug report
Assigns to: Rahul (Backend Developer)

Status: ASSIGNED
↓

2026-04-22 02:00 PM
Rahul starts investigating
Identifies cause: Array limit set to 10 in checkout API
Creates code fix

Status: IN PROGRESS
↓

2026-04-22 03:45 PM
Code committed and merged to develop branch
Code review approved
Requests QA testing

Status: RESOLVED (code review passed)
↓

2026-04-23 09:00 AM
Priya performs regression testing
Steps through bug reproduction
Verifies fix works
Tests with 50 items in cart

Status: IN TESTING
↓

2026-04-23 10:15 AM
Bug confirmed fixed
No longer reproducible
Added to verified bugs list
Ready for production release

Status: VERIFIED/CLOSED
Duration: ~24 hours total
```

### Handling Re-open

```
2026-04-25 02:00 PM
During UAT, customer reports: 
"Checkout still fails with 15 items"

Status: REOPENED
Comment: "Issue still present in production environment"
Assigned back to: Rahul

2026-04-25 03:30 PM
Rahul investigates
Finds: Array limit increased to 10, but should be 100
Root cause: Incomplete fix in first attempt

Status: IN PROGRESS
↓

2026-04-25 05:00 PM
New fix deployed
Committed to production branch

Status: RESOLVED
↓

2026-04-26 09:00 AM
Priya re-tests thoroughly
Tests with 100+ items
All scenarios pass

Status: VERIFIED/CLOSED
Total Duration: 3 days
```

---

## Interview Questions

### JIRA Basics

**Q1: What is JIRA and why is it important in QA?**

A: JIRA एक issue/bug tracking tool है जो teams को bugs report, track, और manage करने में मदद करता है। QA के लिए important है क्योंकि:
- Centralized bug tracking
- Clear workflow & status management
- Traceability & historical data
- Team communication & collaboration
- Reporting & metrics

**Q2: Explain bug lifecycle in JIRA?**

A: Bug lifecycle typically:
NEW → ASSIGNED → IN PROGRESS → RESOLVED → IN TESTING → VERIFIED → CLOSED

हर state में specific actions होते हैं। Developer फिक्स करता है, फिर QA verify करता है।

**Q3: What's the difference between Severity and Priority?**

A: Severity = problem की तीव्रता (क्या गलत है)
Priority = कितना urgent है (कब fix करना है)

Example: Typo in help text = Low severity but can be High priority if visible to customers.

### Advanced Questions

**Q4: How would you handle a duplicate bug in JIRA?**

A: 1) Identify duplicate issue
2) Link both issues
3) Mark the newer one as duplicate
4) Link to original issue
5) Provide explanation in comment
6) Close the newer issue

**Q5: What makes a good bug report?**

A: - Clear, specific summary
- Detailed reproduction steps
- Expected vs Actual result
- Environment details
- Screenshots/logs/videos
- One issue per bug
- No assumptions, just facts

**Q6: How do you prioritize bugs in JIRA?**

A: Based on:
- Business impact
- User count affected
- Functionality blocked
- Severity level
- Customer complaints
- Release timeline

Critical bugs first, then high, then medium, then low.

**Q7: Tell about JIRA Workflows?**

A: Workflows define allowed state transitions for issues.
Example: NEW → ASSIGNED → IN PROGRESS → RESOLVED → VERIFIED

Different issue types can have different workflows. Can be customized per project.

**Q8: How do you use JIRA for Agile/Scrum?**

A: - Create user stories as issues
- Estimate using story points
- Add to sprints
- Track burndown
- Daily standup updates
- Sprint reports
- Retrospective data

**Q9: What reports do you generate from JIRA?**

A: - Bug summary (open/closed)
- Priority distribution
- Defect density
- Resolution time
- Burndown chart
- Velocity chart
- Test execution status

**Q10: How to effectively search in JIRA using JQL?**

A: JQL (Jira Query Language) examples:
```
project = "BUG" AND status = "Open"
priority >= "High" AND assignee = "Rahul"
created >= -30d AND resolution = "Unresolved"
```

### Scenario-Based

**Q11: 100 bugs reported but only 80 developers' seats available. How to prioritize?**

A: 1) Filter by Severity (Critical > Major > Minor)
2) Filter by Business impact
3) Filter by Customer priority
4) Critical/Blocker bugs: Assign immediately
5) High priority: Queue for next sprint
6) Medium/Low: Backlog for future sprints
7) Use JIRA reports to communicate status

**Q12: Bug status is stuck in "In Testing" for 10 days. What to do?**

A: 1) Check if QA is actually testing
2) Verify developer fix is correct
3) Communicate with QA team
4) Identify blockers
5) Add more QA resources
6) Use JIRA comments for updates
7) Escalate if needed

---

## JIRA Tips & Tricks

```
✓ Use keyboard shortcuts
✓ Create custom filters
✓ Automate workflow transitions
✓ Use labels for grouping
✓ Link related issues
✓ Comment with @mentions
✓ Attach relevant files
✓ Regular report review
✓ Cleanup old issues
✓ Train team on JIRA usage
```

---

## Summary

JIRA is essential for QA professionals:
- Bug tracking और management
- Clear workflow definition
- Team collaboration
- Reporting & analytics
- Process standardization
- Historical data analysis

Effective JIRA usage = Better quality software delivery.

---

## Key Takeaways

✅ Create detailed bug reports  
✅ Follow workflow process  
✅ Update status regularly  
✅ Use comments for communication  
✅ Link related issues  
✅ Generate useful reports  
✅ Keep JIRA clean and organized  

---

**Happy Testing with JIRA! 🚀**

---

*Module 22: JIRA & Bug Lifecycle - Complete Guide*  
*Created: 2026 | Language: Hinglish (Hindi + English)*  
*For: QA Professionals & Aspirants*
