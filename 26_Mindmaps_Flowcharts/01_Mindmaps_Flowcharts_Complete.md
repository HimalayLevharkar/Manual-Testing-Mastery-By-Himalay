# Module 26: Testing Mindmaps & Flowcharts

## विजुअल गाइड - Testing Concepts को समझने के लिए

---

## 📋 Table of Contents

1. [SDLC Flowchart](#sdlc-flowchart)
2. [STLC Mindmap](#stlc-mindmap)
3. [Testing Types Decision Tree](#testing-types)
4. [Bug Lifecycle Flowchart](#bug-lifecycle)
5. [Test Case Design Process](#test-design)
6. [Risk Assessment Matrix](#risk-matrix)
7. [Quality Assurance Framework](#qa-framework)
8. [Career Path Roadmap](#career-path)

---

## SDLC Flowchart

### Software Development Lifecycle - Complete Flow

```
┌─────────────────────────────────────────────────────┐
│           START: New Project Initiated              │
└─────────────┬───────────────────────────────────────┘
              │
              ▼
      ┌───────────────────┐
      │ 1. PLANNING PHASE │
      │ ─────────────────── │
      │ • Feasibility Study │
      │ • Resource Planning │
      │ • Timeline Planning │
      │ • Risk Assessment   │
      └───────────┬─────────┘
                  │
                  ▼
       ┌─────────────────────┐
       │ 2. REQUIREMENTS PHASE│
       │ ──────────────────── │
       │ • Gather Requirements│
       │ • Document Features │
       │ • Get Approvals     │
       │ • Create Specs      │
       └──────────┬──────────┘
                  │
                  ▼
      ┌───────────────────────┐
      │ 3. DESIGN PHASE       │
      │ ───────────────────── │
      │ • Architecture Design │
      │ • Database Design     │
      │ • UI/UX Design       │
      │ • Technical Design   │
      └──────────┬────────────┘
                 │
                 ▼
      ┌──────────────────────┐
      │ 4. DEVELOPMENT PHASE │
      │ ────────────────────── │
      │ • Write Code         │
      │ • Code Review        │
      │ • Version Control    │
      │ • Build Process      │
      └──────────┬───────────┘
                 │
                 ▼
      ┌──────────────────────┐
      │ 5. TESTING PHASE     │
      │ ────────────────────── │
      │ • QA Testing         │
      │ • Bug Reporting      │
      │ • Bug Fixing         │
      │ • Regression Testing │
      └──────────┬───────────┘
                 │
          ┌──────┴──────┐
          │             │
         NO            YES
      BUGS?          PASSED?
          │             │
          ▼             ▼
    ┌─────────┐  ┌────────────────────┐
    │ Fix & │  │ 6. DEPLOYMENT PHASE │
    │Re-test│  │ ──────────────────── │
    └────┬──┘  │ • Release Planning  │
         │     │ • Deployment        │
         │     │ • Smoke Testing     │
         └─┬───┤ • User Training     │
           │   └────────┬────────────┘
           │            │
           │            ▼
           │   ┌────────────────────┐
           │   │ 7. MAINTENANCE     │
           │   │ ──────────────────── │
           │   │ • Monitor System    │
           │   │ • Fix Issues        │
           │   │ • Enhancements      │
           │   │ • Support           │
           └───┤                     │
               └────────┬───────────┘
                        │
                        ▼
              ┌──────────────────┐
              │ RETIRE/END OF    │
              │     LIFE         │
              └──────────────────┘
```

---

## STLC Mindmap

### Software Testing Lifecycle - Phases & Activities

```
                        STLC
                         │
          ┌──────┬───────┼───────┬──────┬────────┐
          │      │       │       │      │        │
          ▼      ▼       ▼       ▼      ▼        ▼
       PLANNING ANALYSIS DESIGN EXECUTION REPORTING CLOSURE
       
PLANNING PHASE:
├─ Define scope
├─ Identify resources
├─ Create timeline
├─ Risk assessment
└─ Estimate effort

ANALYSIS PHASE:
├─ Review requirements
├─ Create test cases
├─ Define test strategy
├─ Identify tools
└─ Plan automation

DESIGN PHASE:
├─ Test case design
├─ Test data prep
├─ Script preparation
├─ Automation scripts
└─ Tool setup

EXECUTION PHASE:
├─ Run test cases
├─ Report bugs
├─ Retest fixes
├─ Regression test
└─ Performance test

REPORTING PHASE:
├─ Defect summary
├─ Coverage report
├─ Quality metrics
├─ Test completion
└─ Recommendations

CLOSURE PHASE:
├─ Lessons learned
├─ Documentation
├─ Knowledge transfer
├─ Archive artifacts
└─ Team feedback
```

---

## Testing Types Decision Tree

### How to Choose Testing Type?

```
                    START: Need to Test
                            │
                    ┌───────┴────────┐
                    │                │
              WHEN?                WHAT?
                    │                │
        ┌───────────┼─────────┐      │
        │           │         │      │
      EARLY      DURING    AFTER    │
      (Dev)      (Dev)     (QA)     │
        │           │         │      │
        ▼           ▼         ▼      ▼
      UNIT    INTEGRATION   SYSTEM  └─ FUNCTIONAL
      TEST      TEST        TEST       TEST
                                         │
                                    ┌────┴─────┬─────────┬──────────┐
                                    │          │         │          │
                               Performance Security Usability Compatibility
                               Testing    Testing    Testing    Testing


CHOOSING FLOW:
├─ During Development?
│  ├─ YES → Unit Testing, Integration Testing
│  └─ NO → Proceed
│
├─ At QA Phase?
│  ├─ YES → System Testing, Regression
│  └─ NO → Proceed
│
├─ After Release?
│  ├─ YES → Smoke, Sanity, UAT
│  └─ NO → Proceed
│
└─ For Performance?
   ├─ High Users? → Load Testing
   ├─ Stress Testing? → Push Limits
   ├─ Endurance? → Long Run
   └─ Spike? → Sudden Load
```

---

## Bug Lifecycle Flowchart

### From Creation to Closure

```
                      BUG FOUND
                           │
                           ▼
                    ┌──────────────┐
                    │ Report Bug   │
                    │              │
                    │ NEW/OPEN     │
                    └──────┬───────┘
                           │
                    QA Lead Review
                           │
              ┌────────────┴────────────┐
              │                         │
           VALID?                    INVALID?
              │                         │
             YES                       NO
              │                         │
              ▼                         ▼
        ┌─────────────┐         ┌──────────────┐
        │   ASSIGN    │         │ CLOSE AS     │
        │ TO DEVELOPER│         │ NOT A BUG    │
        └──────┬──────┘         └──────────────┘
               │
               ▼
        ┌──────────────┐
        │  ASSIGNED    │
        │ (In queue)   │
        └──────┬───────┘
               │
    Developer Starts Work
               │
               ▼
        ┌──────────────┐
        │ IN PROGRESS  │
        │ (Being fixed)│
        └──────┬───────┘
               │
        Fix Implemented
        Code Committed
               │
               ▼
        ┌──────────────┐
        │  RESOLVED    │
        │ (Code fixed) │
        └──────┬───────┘
               │
    QA Tests the Fix
               │
         ┌─────┴─────┐
         │           │
        PASS       FAIL
         │           │
         ▼           ▼
    ┌────────┐  ┌──────────┐
    │VERIFIED│  │ REOPENED │
    │(CLOSED)│  └────┬─────┘
    └────────┘       │
                     │ (Fix Again)
                     │
              (Back to IN PROGRESS)


TIME METRICS:
- NEW → ASSIGNED: 24 hours
- ASSIGNED → IN PROGRESS: 48 hours
- IN PROGRESS → RESOLVED: Variable
- RESOLVED → VERIFIED: 24 hours
- Total: 3-7 days typical
```

---

## Test Case Design Process

### From Requirements to Execution

```
START: Requirement Identified
│
▼
┌─────────────────────────────────┐
│ 1. ANALYZE REQUIREMENT          │
│ ─────────────────────────────── │
│ • Understand functionality       │
│ • Identify edge cases            │
│ • Note assumptions               │
│ • List constraints               │
└────────────┬────────────────────┘
             │
             ▼
┌─────────────────────────────────┐
│ 2. IDENTIFY TEST SCENARIOS       │
│ ─────────────────────────────── │
│ • Happy path                     │
│ • Negative cases                 │
│ • Boundary values                │
│ • Error conditions               │
└────────────┬────────────────────┘
             │
             ▼
┌─────────────────────────────────┐
│ 3. DESIGN TEST CASES            │
│ ─────────────────────────────── │
│ • Write clear title              │
│ • Define preconditions           │
│ • List test steps                │
│ • State expected result           │
│ • Add test data                  │
└────────────┬────────────────────┘
             │
             ▼
┌─────────────────────────────────┐
│ 4. REVIEW & APPROVE             │
│ ─────────────────────────────── │
│ • Peer review                    │
│ • Lead approval                  │
│ • Requirements trace             │
│ • Quality check                  │
└────────────┬────────────────────┘
             │
             ▼
┌─────────────────────────────────┐
│ 5. PREPARE TEST ENVIRONMENT      │
│ ─────────────────────────────── │
│ • Setup test data                │
│ • Configure environment           │
│ • Prepare test accounts          │
│ • Document preconditions         │
└────────────┬────────────────────┘
             │
             ▼
┌─────────────────────────────────┐
│ 6. EXECUTE TEST CASE            │
│ ─────────────────────────────── │
│ • Follow steps exactly           │
│ • Observe actual result           │
│ • Compare with expected          │
│ • Document findings              │
└────────────┬────────────────────┘
             │
        ┌────┴────┐
        │          │
      PASS?      FAIL?
        │          │
        ▼          ▼
    ┌──────┐  ┌───────┐
    │PASS  │  │FAIL - │
    │      │  │Report │
    │      │  │Bug    │
    └──┬───┘  └───┬───┘
       │          │
       │    ┌─────┴──────┐
       │    │ Re-test    │
       │    │ After Fix  │
       │    │            │
       │    └─────┬──────┘
       │          │
       └────┬─────┘
            │
            ▼
      ┌──────────────┐
      │ TEST RESULTS │
      │ DOCUMENTED  │
      └──────────────┘
```

---

## Risk Assessment Matrix

### Visual Risk Evaluation

```
                    IMPACT/SEVERITY
                          │
        LOW    │ MEDIUM    │    HIGH
             ├───────────┼──────────┤
HIGH       │ MEDIUM    │ HIGH    │ CRITICAL│
           │  RISK     │  RISK   │  RISK   │
PROBABILITY│           │         │         │
├───────────┼───────────┼─────────┼─────────┤
MEDIUM     │   LOW     │ MEDIUM  │  HIGH   │
           │  RISK     │  RISK   │  RISK   │
├───────────┼───────────┼─────────┼─────────┤
LOW        │   LOW     │  LOW    │ MEDIUM  │
           │  RISK     │  RISK   │  RISK   │
└───────────┴───────────┴─────────┴─────────┘


COLOR CODING:
🟢 GREEN = LOW RISK (Skip or minimal testing)
🟡 YELLOW = MEDIUM RISK (Standard testing)
🔴 RED = HIGH RISK (Extra testing required)
⚫ BLACK = CRITICAL RISK (Maximum testing effort)


EXAMPLES:
Login Page:
- HIGH Impact (Users need it)
- HIGH Probability (Frequently used)
→ CRITICAL RISK (Max testing)

Help Link:
- LOW Impact (Non-critical)
- LOW Probability (Rarely used)
→ LOW RISK (Minimal testing)

Payment Gateway:
- HIGH Impact (Financial)
- MEDIUM Probability (Some users)
→ HIGH RISK (Extra testing)
```

---

## Quality Assurance Framework

### Complete QA Organization Structure

```
                   QA DEPARTMENT
                         │
          ┌──────────────┼──────────────┐
          │              │              │
          ▼              ▼              ▼
      QA MANAGER    TEST LEAD      AUTOMATION
                                    LEAD
          │              │              │
    ┌─────┴─────┐    ┌───┴────┐    ┌──┴────┐
    │           │    │        │    │       │
    ▼           ▼    ▼        ▼    ▼       ▼
STRATEGY   METRICS MANUAL   EXPLORATORY AUTO  TOOLS
PLANNING   TRACKING TESTING  TESTING    TESTS SETUP


ACTIVITIES BY PHASE:

┌─────────────────────────────────────────┐
│ REQUIREMENT PHASE                       │
├─────────────────────────────────────────┤
│ • Review specifications                  │
│ • Identify test scenarios                │
│ • Plan test approach                     │
│ • Estimate effort                        │
└─────────────────────────────────────────┘
         ▼
┌─────────────────────────────────────────┐
│ DESIGN PHASE                            │
├─────────────────────────────────────────┤
│ • Write test cases                       │
│ • Design test data                       │
│ • Prepare scripts                        │
│ • Setup environment                      │
└─────────────────────────────────────────┘
         ▼
┌─────────────────────────────────────────┐
│ EXECUTION PHASE                         │
├─────────────────────────────────────────┤
│ • Run test cases                         │
│ • Report bugs                            │
│ • Log execution                          │
│ • Perform regression                     │
└─────────────────────────────────────────┘
         ▼
┌─────────────────────────────────────────┐
│ ANALYSIS PHASE                          │
├─────────────────────────────────────────┤
│ • Analyze metrics                        │
│ • Track defects                          │
│ • Generate reports                       │
│ • Plan improvements                      │
└─────────────────────────────────────────┘
```

---

## Career Path Roadmap

### QA Career Progression

```
                    SENIOR DIRECTOR
                    (10+ years)
                          │
                          │
                    MANAGER/LEAD
                     (7-10 years)
                          │
        ┌─────────────────┼─────────────────┐
        │                 │                 │
    AUTOMATION        TEST MANAGER      TEST LEAD
    ARCHITECT            │                 │
   (Testing Skills)      │                 │
        │                │                 │
        └────┬───────────┼────────┬────────┘
             │           │        │
             ▼           ▼        ▼
        SENIOR QA     QA LEAD   AUTOMATION
        ENGINEER      TESTING   ENGINEER
        (5-7 years)   (5-7 yrs) (5-7 yrs)
             │           │        │
             └────┬───────┴───┬────┘
                  │           │
                  ▼           ▼
            AUTOMATION    QA ENGINEER
            TESTER      SPECIALIST
           (3-5 years)   (3-5 years)
                  │           │
                  └──┬────┬───┘
                     │    │
                     ▼    ▼
                QA ENGINEER
               (0-2 years)
                   │
                   ▼
            ENTRY LEVEL QA
            (Training Period)


SKILLS PROGRESSION:

Entry Level:
├─ Manual testing
├─ Test case writing
├─ Bug reporting
└─ Basic tools

Mid Level:
├─ Automation scripting
├─ Test design techniques
├─ Performance testing
├─ Leadership skills

Senior Level:
├─ Architecture design
├─ Team management
├─ Process improvement
├─ Strategic planning
└─ Technical mentoring

Director Level:
├─ Department leadership
├─ Budget management
├─ Strategic vision
├─ Organization planning
└─ Executive communication
```

---

## Testing Pyramid

### Test Distribution & Focus

```
                           ┌─────┐
                           │ E2E │ (10%)
                           │Tests│
                           └─────┘
                          ╱       ╲
                         ╱         ╲
                     ┌──────────────┐
                     │ Integration  │ (30%)
                     │   Tests      │
                     └──────────────┘
                    ╱              ╲
                   ╱                ╲
              ┌─────────────────────┐
              │   Unit Tests        │ (60%)
              └─────────────────────┘


DISTRIBUTION RATIONALE:
- Unit Tests (60%): Fast, cheap, developer-written
- Integration (30%): Medium speed, good coverage
- E2E Tests (10%): Slow, expensive, critical paths


TEST EXECUTION TIME:
Unit Tests:        Minutes
Integration Tests: Minutes to Hours
E2E Tests:         Hours to Days


COST vs BENEFIT:
Unit Tests:        Low cost, High benefit
Integration:       Medium cost, Good benefit
E2E Tests:         High cost, Medium benefit


STRATEGY:
1. Write many unit tests (developers)
2. Write moderate integration tests (QA)
3. Write few E2E tests (critical paths only)
4. Automate all levels
5. Run parallel execution
```

---

## Summary

Visual representations help:
- Understand concepts quickly
- Remember complex processes
- Communicate with team
- Plan testing approach
- Track progress
- Make decisions

Use these mindmaps and flowcharts as reference during your testing.

---

## Key Takeaways

✅ Visualize SDLC and STLC  
✅ Understand bug lifecycle  
✅ Apply risk assessment  
✅ Follow career progression  
✅ Use flowcharts for planning  

---

**Happy Learning! 🚀**

---

*Module 26: Testing Mindmaps & Flowcharts - Complete Guide*  
*Created: 2026 | Language: Hinglish (Hindi + English)*  
*For: QA Professionals & Aspirants*
