# Module 06: Agile & Scrum Testing

## Agile aur Scrum mein Testing - Complete Guide

**Last Updated:** January 2026  
**Reading Time:** 2 hours  
**Level:** Intermediate

---

## 📋 Table of Contents

1. [Agile Testing Fundamentals](#agile-fundamentals)
2. [Scrum Framework & Roles](#scrum-framework)
3. [Sprint Cycle Detailed](#sprint-cycle)
4. [Testing in Agile Environment](#testing-in-agile)
5. [Test Estimation in Agile](#test-estimation)
6. [Agile vs Waterfall Testing](#agile-vs-waterfall)
7. [Real Agile Project Example](#real-example)
8. [Agile Testing Best Practices](#best-practices)
9. [Common Challenges & Solutions](#challenges)
10. [25+ Interview Questions](#interview-questions)

---

## <a name="agile-fundamentals"></a>Agile Testing Fundamentals

### Agile Testing क्या है?

**Agile Testing = Testing continuously throughout the development lifecycle**

Traditional testing में:
```
Requirements → Design → Development → Testing → Deployment
                                         ↑
                                    Last mein test करते थे
```

Agile testing में:
```
Sprint 1: Req → Design → Dev → Test → Deploy
Sprint 2: Req → Design → Dev → Test → Deploy
Sprint 3: Req → Design → Dev → Test → Deploy
                ↑
           हर sprint में test
```

### Agile Testing के 4 Core Values

```
1. CONTINUOUS FEEDBACK
   └─ हर दिन feedback लो
   └─ Developers को तुरंत बताओ
   └─ "Shift Left" - early testing

2. CUSTOMER COLLABORATION
   └─ Customer के साथ काम करो
   └─ Requirements clear रखो
   └─ Acceptance criteria define करो

3. RESPOND TO CHANGE
   └─ Requirements change हो सकते हैं
   └─ Flexible रहो
   └─ New priorities accept करो

4. WORKING SOFTWARE
   └─ Documentation से ज्यादा important
   └─ Working feature deliver करो
   └─ Quality over quantity
```

### Agile Tester की Responsibilities

```
एक Agile Tester को:

✓ Sprint planning में participate करना
✓ User stories को समझना
✓ Acceptance criteria define करना
✓ Test cases design और execute करना
✓ Developers के साथ daily collaborate करना
✓ Regression testing continuously करना
✓ Automation scripts maintain करना
✓ Sprint review में demo देना
✓ Retrospective में improve करना
```

### Agile Testing Quadrants

```
                    ┌─────────────────────────────────────┐
                    │         AGILE TESTING QUADRANTS     │
                    └─────────────────────────────────────┘

Q1: Component Testing          Q2: Story Testing
    (Technology Facing)            (Business Facing)
    ├─ Unit Tests                ├─ Functional Tests
    ├─ Component Tests           ├─ Story Tests
    └─ Static Code Analysis      └─ API Tests
    
                    ↑ Team Support ↑

Q3: Exploratory Testing        Q4: System Testing
    (Business Facing)              (Technology Facing)
    ├─ Exploratory Tests         ├─ Performance Tests
    ├─ Usability Tests           ├─ Security Tests
    └─ UAT                       └─ Load Tests
```

---

## <a name="scrum-framework"></a>Scrum Framework & Roles

### Scrum क्या है?

**Scrum = Agile की सबसे popular framework**

```
Scrum का simple मतलब:
- Small iterations (Sprints) में काम करना
- हर sprint में working software deliver करना
- Continuous improvement करना
```

### 3 Scrum Roles

```
┌─────────────────────────────────────────────────────────┐
│                   SCRUM ROLES                           │
└─────────────────────────────────────────────────────────┘

1. PRODUCT OWNER (PO)
   └─ "WHAT" decide करता है
   └─ Product backlog maintain करता है
   └─ Priority set करता है
   └─ Stakeholders से बात करता है
   └─ Acceptance criteria define करता है
   
   Tester का काम:
   ✓ PO के साथ requirements discuss करना
   ✓ Acceptance criteria clear करना
   ✓ Testability ensure करना

2. SCRUM MASTER (SM)
   └─ Process को follow करवाता है
   └─ Impediments remove करता है
   └─ Team को protect करता है
   └─ Meetings facilitate करता है
   
   Tester का काम:
   ✓ Testing blockers report करना
   ✓ Quality concerns raise करना
   ✓ Process improvements suggest करना

3. DEVELOPMENT TEAM
   └─ 5-9 members
   └─ Cross-functional (Dev, QA, UX, etc.)
   └─ Self-organizing
   └─ Sprint goal achieve करता है
   
   Tester का काम:
   ✓ Test planning और execution
   ✓ Bug reporting और tracking
   ✓ Automation scripting
   ✓ Quality assurance
```

### Product Backlog vs Sprint Backlog

```
PRODUCT BACKLOG (PO owns):
┌──────────────────────────────────────┐
│ All features, enhancements, bugs     │
│ Priority-wise sorted                 │
│ Dynamic - changes allowed            │
│ Example:                             │
│ 1. User login feature (High)         │
│ 2. Payment gateway (High)            │
│ 3. Dark mode (Medium)                │
│ 4. Export to PDF (Low)               │
└──────────────────────────────────────┘

SPRINT BACKLOG (Team owns):
┌──────────────────────────────────────┐
│ Selected for THIS sprint only        │
│ Fixed once sprint starts             │
│ Task-level breakdown                 │
│ Example (Sprint 5):                  │
│ - Login page design (Dev)            │
│ - Login API (Dev)                    │
│ - Login test cases (QA)              │
│ - Login automation (QA)              │
└──────────────────────────────────────┘
```

---

## <a name="sprint-cycle"></a>Sprint Cycle Detailed

### Sprint Timeline (2 Weeks Example)

```
┌────────────────────────────────────────────────────────────┐
│                    2-WEEK SPRINT                           │
│                                                            │
│ Day 1    Day 2-9        Day 10      Day 11      Day 12    │
│  │         │              │           │           │        │
│  ▼         ▼              ▼           ▼           ▼        │
│Planning  Development    Testing    Review     Retro      │
│          + Testing                                  │      │
│                                                    ▼      │
│                                                Next Sprint │
└────────────────────────────────────────────────────────────┘
```

### Sprint Ceremonies (Events)

#### 1. Sprint Planning (Day 1 - 4 hours for 2-week sprint)

```
कौन attends करता है:
├─ Product Owner
├─ Scrum Master
├─ Development Team (including QA)
└─ Stakeholders (optional)

क्या होता है:
├─ PO priority items present करता है
├─ Team capacity discuss होती है
├─ Stories select की जाती हैं
├─ Tasks break down होते हैं
├─ Estimates finalize होते हैं
└─ Sprint goal define होता है

Tester की preparation:
✓ Previous sprint का quality data
✓ Testing effort estimates
✓ Test environment requirements
✓ Automation scope
```

**Sprint Planning में Tester का Role:**

```
BEFORE Planning:
├─ Backlog items review करो
├─ Dependencies identify करो
├─ Test effort estimate करो
└─ Questions prepare करो

DURING Planning:
├─ Acceptance criteria clarify करो
├─ Test scenarios suggest करो
├─ Testing effort present करो
├─ Dependencies flag करो
└─ Quality risks highlight करो

AFTER Planning:
├─ Test plan update करो
├─ Test cases design शुरू करो
├─ Test data prepare करो
└─ Automation scripts plan करो
```

#### 2. Daily Standup (15 minutes - Every day)

```
Format: 3 Questions

1. "कल क्या किया?"
   └─ Yesterday's progress

2. "आज क्या करेंगे?"
   └─ Today's plan

3. "कोई blocker?"
   └─ Any impediments

Tester's Standup Update Example:
┌────────────────────────────────────────────┐
│ "कल मैंने Login feature के 15 test cases  │
│  लिखे और 10 execute किए। 3 bugs मिले।     │
│                                            │
│  आज regression testing करूंगी और new      │
│  Payment feature के test cases लिखूंगी।   │
│                                            │
│  Blocker: Test environment down है         │
│  पिछले 2 घंटे से।"                        │
└────────────────────────────────────────────┘
```

#### 3. Sprint Review (Day 10/11 - 2 hours)

```
क्या होता है:
├─ Team demo देती है
├─ PO accept/reject करता है
├─ Stakeholders feedback देते हैं
├─ Done/Not Done review होता है
└─ Next sprint की planning input

Tester का contribution:
✓ Test summary report present करना
✓ Quality metrics share करना
✓ Known issues list करना
✓ Automation coverage update करना
```

**Test Summary Report Template:**

```
SPRINT 5 - TEST SUMMARY
─────────────────────────────────────
Sprint Goal: User Authentication

TEST EXECUTION:
├─ Total Test Cases: 45
├─ Executed: 45 (100%)
├─ Passed: 42 (93%)
├─ Failed: 3 (7%)
└─ Blocked: 0

DEFECTS:
├─ New Bugs: 5
├─ Critical: 1
├─ High: 2
├─ Medium: 2
├─ Fixed: 8
└─ Open: 3

AUTOMATION:
├─ Scripts Added: 12
├─ Total Coverage: 78%
└─ Regression Time: 45 min

RECOMMENDATION: ✅ GO FOR DEPLOY
```

#### 4. Sprint Retrospective (Day 11/12 - 1.5 hours)

```
क्या होता है:
├─ What went well?
├─ What didn't go well?
├─ Action items for improvement
└─ Process improvements

Tester के लिए Sample Inputs:

WENT WELL:
✓ Early test case review helped
✓ Dev-QA collaboration improved
✓ Automation saved 10 hours

NOT WELL:
✗ Test environment unstable था
✗ Requirements late मिले
✗ Bug fixes retest के लिए late आए

ACTION ITEMS:
→ Environment monitoring setup
→ Requirements 2 days before sprint
→ Bug fix SLA: 24 hours
```

---

## <a name="testing-in-agile"></a>Testing in Agile Environment

### Agile Testing Lifecycle

```
┌──────────────────────────────────────────────────────────┐
│              AGILE TESTING LIFECYCLE                     │
│                                                          │
│  Sprint Planning                                         │
│       ↓                                                  │
│  Test Planning & Design                                  │
│       ↓                                                  │
│  Test Development (Automation)                           │
│       ↓                                                  │
│  Test Execution (Continuous)                             │
│       ↓                                                  │
│  Defect Tracking & Retest                                │
│       ↓                                                  │
│  Sprint Review & Retro                                   │
└──────────────────────────────────────────────────────────┘
```

### Shift-Left Testing

```
TRADITIONAL:
Requirements → Design → Dev → TEST → Deploy
                         ↑
                    Late testing (bugs expensive)

AGILE (SHIFT-LEFT):
TEST → Requirements → Design → Dev → TEST → Deploy
 ↑                              ↑
Early testing            Continuous testing

Benefits:
✓ Bugs early मिलते हैं (10x cheaper)
✓ Requirements clear होते हैं
✓ Rework कम होता है
✓ Quality improves
```

### Shift-Left में Tester के Activities

```
SPRINT -1 (Before Development):
├─ Requirements review
├─ Acceptance criteria define
├─ Test scenarios design
└─ Test data planning

SPRINT 0 (Setup):
├─ Test environment setup
├─ Automation framework setup
├─ Test tools configure
└─ Baseline tests create

SPRINT 1+ (Active):
├─ Daily test execution
├─ Continuous regression
├─ Automation script updates
└─ Performance testing
```

### Definition of Done (DoD)

```
एक feature "Done" तब होता है जब:

CODE:
✓ Code complete है
✓ Code review हुआ
✓ Unit tests pass हैं

TESTING:
✓ Test cases execute हुए
✓ All tests pass हैं
✓ No critical/open bugs
✓ Regression pass है

DOCUMENTATION:
✓ Technical docs update
✓ User docs update
✓ Release notes ready

DEPLOYMENT:
✓ Staging में tested
✓ PO approval मिला
✓ Deploy ready है
```

### Continuous Testing in Agile

```
┌─────────────────────────────────────────────────────────┐
│              CONTINUOUS TESTING PYRAMID                 │
│                                                         │
│                    /\                                   │
│                   /  \                                  │
│                  / E2E \       (10% tests)              │
│                 /________\                              │
│                /          \                             │
│               /  SERVICE  \     (20% tests)             │
│              /______________\                           │
│             /                \                          │
│            /    UNIT TESTS    \   (70% tests)           │
│           /____________________\                        │
│                                                         │
│  Execution Speed: Fast → Slower                         │
│  Cost: Low → High                                       │
│  Maintenance: Easy → Complex                            │
└─────────────────────────────────────────────────────────┘
```

---

## <a name="test-estimation"></a>Test Estimation in Agile

### Test Estimation Techniques

#### 1. Story Point Estimation

```
Fibonacci Scale: 1, 2, 3, 5, 8, 13, 21

Complexity के basis पर:

1 Point = Very Simple
└─ 1-2 test cases
└─ No dependencies
└─ Well-known feature

2 Points = Simple
└─ 3-5 test cases
└─ Minor dependencies
└─ Similar to existing feature

3 Points = Medium
└─ 5-10 test cases
└─ Some dependencies
└─ New functionality

5 Points = Complex
└─ 10-20 test cases
└─ Multiple dependencies
└─ Integration required

8 Points = Very Complex
└─ 20+ test cases
└─ High dependencies
└─ Third-party integration

13+ Points = Epic (Break down needed)
```

#### 2. Three-Point Estimation

```
हर task के लिए 3 estimates:

Optimistic (O) = Best case
Most Likely (M) = Normal case
Pessimistic (P) = Worst case

Formula:
Expected Effort = (O + 4M + P) / 6

Example: Login Feature Testing
O = 4 hours (सब कुछ smooth)
M = 8 hours (Normal scenarios)
P = 16 hours (Many bugs found)

Expected = (4 + 32 + 16) / 6 = 8.67 hours ≈ 9 hours
```

#### 3. Test Effort Breakdown

```
User Story: "As a user, I want to login with email"

TEST EFFORT BREAKDOWN:
┌────────────────────────────────────────────┐
│ Activity                    │ Hours       │
├────────────────────────────────────────────┤
│ Test Case Design            │ 2.0         │
│ Test Data Preparation       │ 1.0         │
│ Manual Test Execution       │ 2.0         │
│ Bug Reporting & Retesting   │ 2.0         │
│ Automation Scripting        │ 4.0         │
│ Regression Testing          │ 1.0         │
├────────────────────────────────────────────┤
│ TOTAL                       │ 12.0 hours  │
└────────────────────────────────────────────┘

Factors that increase effort:
✗ New team member (+20%)
✗ Unstable environment (+30%)
✗ Complex integrations (+40%)
✗ Tight deadlines (+25% overtime)
```

### Capacity Planning

```
SPRINT CAPACITY CALCULATION:

Team: 6 members (2 QA)
Sprint: 2 weeks (10 working days)

Total Hours Available:
= 6 people × 10 days × 8 hours
= 480 hours

Focus Factor (meetings, emails, etc.):
= 480 × 0.75 (75% productive)
= 360 hours available

QA Capacity (2 testers):
= 2 × 10 × 8 × 0.75
= 120 hours for testing

Story Points Capacity:
If 1 SP = 8 hours testing
Then 120/8 = 15 SP for testing
```

---

## <a name="agile-vs-waterfall"></a>Agile vs Waterfall Testing

### Detailed Comparison

```
┌──────────────────────────────────────────────────────────────┐
│              WATERFALL vs AGILE TESTING                      │
├──────────────────────────────────────────────────────────────┤
│ Aspect            │ Waterfall        │ Agile               │
├──────────────────────────────────────────────────────────────┤
│ Testing Phase     │ After Dev        │ Throughout          │
│ Test Planning     │ Once (start)     │ Every sprint        │
│ Test Cases        │ Detailed upfront │ Just-in-time        │
│ Bug Detection     │ Late (expensive) │ Early (cheap)       │
│ Customer Feedback │ End of project   │ Every sprint        │
│ Documentation     │ Heavy            │ Lightweight         │
│ Changes           │ Difficult        │ Welcome             │
│ Team Structure    │ Siloed           │ Cross-functional    │
│ Release Frequency │ Monthly/Quarterly│ Every sprint        │
│ Risk              │ High             │ Managed             │
└──────────────────────────────────────────────────────────────┘
```

### Waterfall Testing Timeline

```
WATERFALL PROJECT (6 Months):

Month 1-2: Requirements
    └─ Test team नहीं involve

Month 3: Design
    └─ Test team review करता है

Month 4-5: Development
    └─ Test team test cases लिखता है

Month 6: TESTING
    └─ 4 weeks testing
    └─ Bugs मिले? Fix → Retest
    └─ Delay होता है
    └─ Release pressure

PROBLEMS:
✗ Testing के पास कम time
✗ Bugs late मिलते हैं (expensive)
✗ No time for thorough testing
✗ Quality compromise हो सकती है
```

### Agile Testing Timeline

```
AGILE PROJECT (6 Months = 12 Sprints):

Sprint 1 (2 weeks):
├─ Feature 1 development
├─ Feature 1 testing
└─ Deployed ✅

Sprint 2 (2 weeks):
├─ Feature 2 development
├─ Feature 2 testing
├─ Feature 1 regression
└─ Deployed ✅

...continues...

Sprint 12 (2 weeks):
├─ Feature 12 development
├─ Feature 12 testing
├─ Full regression
└─ Deployed ✅

BENEFITS:
✓ Testing को हर sprint में time मिलता है
✓ Bugs early मिलते हैं
✓ Quality consistent रहती है
✓ Customer हर sprint में feedback देता है
```

### When to Use What?

```
WATERFALL TESTING Better When:
✓ Requirements fixed और clear हैं
✓ Regulatory compliance needed
✓ Safety-critical systems
✓ Team distributed across timezones
✓ Customer unavailable for feedback

AGILE TESTING Better When:
✓ Requirements evolve करेंगे
✓ Fast time-to-market चाहिए
✓ Customer feedback important है
✓ Innovation needed
✓ Competitive market
```

---

## <a name="real-example"></a>Real Agile Project Example

### E-commerce App - 6 Sprint Journey

```
PROJECT: Flipkart-style E-commerce App
TEAM: 8 members (2 PO, 1 SM, 3 Dev, 2 QA)
SPRINT DURATION: 2 weeks
TOTAL SPRINTS: 6
```

#### Sprint 1: User Registration & Login

```
SPRINT 1 BACKLOG:
┌─────────────────────────────────────────────┐
│ User Stories:                               │
│ 1. User registration with email            │
│ 2. User login with email/password          │
│ 3. Forgot password functionality           │
│ 4. Email verification                      │
└─────────────────────────────────────────────┘

TESTER ACTIVITIES:

Day 1 (Planning):
├─ 4 stories समझीं
├─ Acceptance criteria define कीं
├─ Estimate: 13 story points
└─ Test scenarios brainstorm किए

Day 2-3:
├─ 25 test cases design किए
├─ Test data prepare किया
├─ Automation framework setup किया
└─ Smoke tests लिखे

Day 4-7:
├─ Developers को test cases review किए
├─ Parallel में development हुआ
├─ 2 bugs early पकड़े (requirements gap)
└─ Automation scripts बनाए

Day 8-9:
├─ Full testing की
├─ 25/25 test cases pass
├─ 5 bugs found (2 critical, 3 minor)
├─ Developers ने fix किए
└─ Retest किया

Day 10 (Review):
├─ Demo दिया
├─ PO ने accept किया
├─ 1 minor bug production में जाने दिया
└─ Sprint goal achieved ✅

Day 11 (Retro):
├─ Early bug detection worked well
├─ Test data creation में delay हुआ
└─ Next sprint में improve करने का plan
```

#### Sprint 2: Product Catalog

```
SPRINT 2 BACKLOG:
┌─────────────────────────────────────────────┐
│ User Stories:                               │
│ 1. View product list                       │
│ 2. Product search                          │
│ 3. Product filters (price, rating)         │
│ 4. Product details page                    │
└─────────────────────────────────────────────┘

TESTER ACTIVITIES:

New Challenges:
├─ Large test data needed (100+ products)
├─ Search algorithm testing complex
├─ Filter combinations many हैं
└─ Performance testing needed

Test Approach:
├─ Equivalence Class Partitioning used
├─ Boundary Value Analysis for price filter
├─ Exploratory testing for UX
├─ Load testing for search (1000 users)
└─ 45 test cases executed

Bugs Found:
├─ Search में special characters crash
├─ Price filter boundary issue (₹999 vs ₹1000)
├─ Images load नहीं हो रहीं slow network पर
└─ 8 bugs total, all fixed

Automation Added:
├─ Search functionality tests
├─ Filter tests
└─ Total automation: 35 scripts
```

#### Sprint 3-6 Summary

```
SPRINT 3: Shopping Cart
├─ Stories: 5
├─ Test Cases: 55
├─ Bugs: 12
├─ Automation: +18 scripts
└─ Go-Live: Partial (Cart + Catalog + Login)

SPRINT 4: Payment Gateway
├─ Stories: 4 (complex)
├─ Test Cases: 40
├─ Bugs: 8 (3 security-related)
├─ Security testing added
└─ Go-Live: Payment integrated

SPRINT 5: Order Management
├─ Stories: 6
├─ Test Cases: 60
├─ Bugs: 15
├─ End-to-end testing
└─ Go-Live: Full order flow

SPRINT 6: Performance & Polish
├─ Stories: 3 + bugs
├─ Test Cases: 30 + regression
├─ Performance testing (load, stress)
├─ Accessibility testing
└─ Go-Live: PRODUCTION READY ✅
```

### Sprint-wise Metrics

```
┌────────────────────────────────────────────────────────────┐
│                    SPRINT METRICS                          │
├────────────────────────────────────────────────────────────┤
│ Sprint │ Stories │ Test Cases │ Bugs │ Automation Coverage│
├────────────────────────────────────────────────────────────┤
│   1    │    4    │     25     │   5  │       15%          │
│   2    │    4    │     45     │   8  │       35%          │
│   3    │    5    │     55     │  12  │       55%          │
│   4    │    4    │     40     │   8  │       70%          │
│   5    │    6    │     60     │  15  │       85%          │
│   6    │    3    │     30     │   6  │       95%          │
├────────────────────────────────────────────────────────────┤
│ TOTAL  │   26    │    255     │  54  │       95%          │
└────────────────────────────────────────────────────────────┘

KEY LEARNINGS:
✓ Early testing ने 40% bugs production से बचाए
✓ Automation ने regression time 4 hours → 30 minutes
✓ Daily Dev-QA sync ने rework 50% कम किया
✓ Sprint-wise release ने confidence बढ़ाया
```

---

## <a name="best-practices"></a>Agile Testing Best Practices

### 10 Golden Rules

```
1. TEST EARLY, TEST OFTEN
   └─ Requirements phase से start करो
   └─ हर day test करो
   └─ Continuous feedback दो

2. AUTOMATE SMARTLY
   └─ Repetitive tests automate करो
   └─ Regression priority दो
   └─ Maintenance cost consider करो

3. COLLABORATE WITH DEV
   └─ Daily sync रखो
   └─ Pair testing करो
   └─ Knowledge share करो

4. KEEP TESTS SIMPLE
   └─ Complex tests break होते हैं
   └─ Maintainable रखो
   └─ Document करो

5. FOCUS ON BUSINESS VALUE
   └─ User perspective से test करो
   └─ Critical paths priority करो
   └─ Risk-based testing करो

6. EXPLORE BEYOND SCRIPTS
   └─ Exploratory testing करो
   └─ Edge cases खोजो
   └─ User behavior observe करो

7. USE CHECKLISTS
   └─ Test coverage checklist
   └─ Bug report checklist
   └─ Release checklist

8. MEASURE WHAT MATTERS
   └─ Bug escape rate
   └─ Test coverage
   └─ Automation ROI

9. CONTINUOUS LEARNING
   └─ New tools सीखो
   └─ Domain knowledge बढ़ाओ
   └─ Best practices follow करो

10. COMMUNICATE CLEARLY
    └─ Bug reports clear रखो
    └─ Status updates दो
    └─ Risks highlight करो
```

### Test Case Management in Agile

```
BEST PRACTICES:

✓ Just-enough detail (not too much, not too little)
✓ Version control में रखो
✓ Sprint-wise organize करो
✓ Automation-tagged tests mark करो
✓ Regular cleanup करो (obsolete tests delete)

TEST CASE TEMPLATE (Agile):
┌────────────────────────────────────────────┐
│ ID: TC_LOGIN_01                           │
│ Story: US-001 (User Login)                │
│ Title: Valid login with correct credentials│
│                                           │
│ Pre-condition: User registered है         │
│                                           │
│ Steps:                                    │
│ 1. Navigate to login page                 │
│ 2. Enter valid email                      │
│ 3. Enter valid password                   │
│ 4. Click Login button                     │
│                                           │
│ Expected: Dashboard पे redirect हो       │
│                                           │
│ Automation: Yes (Smoke suite)             │
│ Priority: High                            │
└────────────────────────────────────────────┘
```

### Bug Management in Agile

```
BUG TRIAGE PROCESS:

Daily bug triage meeting (15 min):
├─ New bugs review
├─ Priority assign
├─ Owner assign
├─ Sprint में fix करेंगे या backlog?
└─ Target fix date

BUG PRIORITY IN SPRINT:
┌────────────────────────────────────────────┐
│ Priority  │ Action                        │
├────────────────────────────────────────────┤
│ Critical  │ Fix immediately, stop sprint  │
│ High      │ Fix this sprint               │
│ Medium    │ Fix if time, else next sprint │
│ Low       │ Backlog में डालो              │
└────────────────────────────────────────────┘

BUG TRACKING TIPS:
✓ Screenshots/videos attach करो
✓ Steps to reproduce clear रखो
✓ Environment mention करो
✓ Expected vs Actual लिखो
✓ Impact describe करो
```

---

## <a name="challenges"></a>Common Challenges & Solutions

### Challenge 1: "Testing को time नहीं मिलता"

```
PROBLEM:
✗ Sprint के last 2 days only testing के लिए
✗ Developers late code deliver करते हैं
✗ Testing rush हो जाती है

SOLUTIONS:
✓ Shift-left testing adopt करो
✓ Sprint में testing capacity buffer रखो (20%)
✓ Definition of Done enforce करो
✓ Partial stories accept मत करो
✓ Daily progress track करो
```

### Challenge 2: "Requirements clear नहीं हैं"

```
PROBLEM:
✗ User stories vague हैं
✗ Acceptance criteria missing हैं
✗ Mid-sprint requirements change होते हैं

SOLUTIONS:
✓ Sprint planning में clarify करो
✓ "3 Cs" follow करो (Card, Conversation, Confirmation)
✓ Example-driven requirements लो
✓ PO के साथ 1:1 sync रखो
✓ Ambiguous stories reject करो
```

### Challenge 3: "Regression testing का time नहीं"

```
PROBLEM:
✗ हर sprint में full regression possible नहीं
✗ Manual regression बहुत time लेता है
✗ Bugs slip हो जाते हैं

SOLUTIONS:
✓ Automation investment करो
✓ Risk-based regression करो (critical first)
✓ Sprint-wise regression scope define करो
✓ CI/CD pipeline में automated tests डालो
✓ Testing pyramid follow करो
```

### Challenge 4: "Environment issues"

```
PROBLEM:
✗ Test environment unstable है
✗ Data refresh नहीं होता
✗ Third-party services down रहते हैं

SOLUTIONS:
✓ Environment owner assign करो
✓ Monitoring setup करो
✓ Mock services use करो
✓ Backup environment रखो
✓ Sprint capacity में buffer दो
```

### Challenge 5: "Automation maintain करना मुश्किल है"

```
PROBLEM:
✗ Scripts बार-बार break होती हैं
✗ Maintenance में बहुत time लगता है
✗ ROI negative लगता है

SOLUTIONS:
✓ Page Object Model use करो
✓ Stable selectors use करो
✓ Regular refactoring करो
✓ Flaky tests fix/remove करो
✓ Automation specialist assign करो
```

---

## <a name="interview-questions"></a>25+ Interview Questions

### Fundamentals (1-5)

**Q1. Agile testing क्या है?**
```
A: Agile testing continuous testing है जो पूरे development 
lifecycle में होता है। Waterfall की तरह last में नहीं, बल्कि 
हर sprint में testing होती है। इसमें feedback early मिलता है 
और bugs सस्ते में fix हो जाते हैं।
```

**Q2. Agile के 4 values क्या हैं?**
```
A: 
1. Individuals and interactions over processes and tools
2. Working software over comprehensive documentation
3. Customer collaboration over contract negotiation
4. Responding to change over following a plan
```

**Q3. Scrum में कौन-कौन roles होते हैं?**
```
A:
1. Product Owner - Requirements और priority decide करता है
2. Scrum Master - Process follow करवाता है, blockers remove करता है
3. Development Team - 5-9 members जो काम deliver करते हैं (Dev, QA, UX)
```

**Q4. Sprint क्या होता है?**
```
A: Sprint time-boxed iteration होता है (usually 2-4 weeks) जिसमें 
team committed work complete करती है। हर sprint में planning, 
development, testing, review, और retrospective होता है।
```

**Q5. Definition of Done (DoD) क्या है?**
```
A: DoD criteria की list है जो decide करती है कि work complete हुआ 
या नहीं। Example: Code complete, tested, reviewed, documented, 
और deploy-ready।
```

### Scrum Ceremonies (6-10)

**Q6. Sprint planning में tester क्या करता है?**
```
A: 
- Backlog items review करता है
- Test effort estimate देता है
- Acceptance criteria clarify करता है
- Test scenarios suggest करता है
- Dependencies और risks highlight करता है
```

**Q7. Daily standup में tester क्या बताता है?**
```
A:
1. कल क्या किया (test cases लिखे, execute किए, bugs found)
2. आज क्या करेगा (regression, new features test)
3. Blockers (environment down, data issue, dev delay)
```

**Q8. Sprint review में test summary report क्या होता है?**
```
A:
- Total test cases executed
- Pass/fail percentage
- New bugs found और status
- Automation coverage
- Known issues list
- Go/No-Go recommendation
```

**Q9. Retrospective में tester क्या input देता है?**
```
A:
Went Well: Early test review worked, automation helped
Not Well: Environment unstable, requirements late
Action Items: Environment monitoring, earlier requirement sync
```

**Q10. Backlog refinement में tester का role?**
```
A:
- Stories की testability check करता है
- Acceptance criteria strengthen करता है
- Test effort estimate देता है
- Dependencies identify करता है
- Edge cases suggest करता है
```

### Testing Techniques (11-15)

**Q11. Shift-left testing क्या है?**
```
A: Shift-left का मतलब testing को early start करना। Requirements 
phase में ही test planning शुरू कर देना ताकि bugs early मिलें 
और fix करना सस्ता पड़े।
```

**Q12. Agile testing pyramid explain करो?**
```
A: 
- Bottom (70%): Unit tests - fast, cheap, stable
- Middle (20%): Service/API tests - integration testing
- Top (10%): E2E tests - slow, expensive, brittle

यह pyramid इसलिए है क्योंकि unit tests maintain करना easy 
हैं और E2E tests expensive हैं।
```

**Q13. Exploratory testing कब करते हो?**
```
A:
- नए features के साथ
- जब test cases नहीं हैं
- Complex scenarios के लिए
- UX testing के लिए
- जब time कम हो
- Scripted testing के बाद extra coverage के लिए
```

**Q14. Regression testing को कैसे manage करते हो Agile में?**
```
A:
- Critical tests automate करते हैं (smoke suite)
- Sprint-wise regression scope define करते हैं
- CI/CD pipeline में automated tests डालते हैं
- Risk-based approach use करते हैं
- Full regression हर 2-3 sprint में करते हैं
```

**Q15. Story point estimation में tester कैसे help करता है?**
```
A:
- Testing complexity बताता है
- Test scenarios की count बताता है
- Dependencies highlight करता है
- Test data requirements बताता है
- Automation effort estimate देता है
```

### Scenario-Based (16-20)

**Q16. Sprint के last day में critical bug मिला। क्या करोगे?**
```
A:
1. Bug की severity assess करूंगा
2. Dev और PO को immediately inform करूंगा
3. Impact analyze करूंगा
4. Options discuss करेंगे:
   - Fix करके deploy करेंगे (अगर time है)
   - Sprint से story remove करेंगे
   - Known issue के साथ deploy करेंगे (अगर low priority)
5. Lesson learn को retro में discuss करेंगे
```

**Q17. Developer कहता है "मेरा code सही है, test case गलत है"। क्या करोगे?**
```
A:
1. Test case review करूंगा
2. Expected behavior requirements से verify करूंगा
3. PO/business analyst से clarification लूंगा
4. Pair testing करूंगा developer के साथ
5. अगर test case सही है तो evidence के साथ bug report update करूंगा
6. Disagree रहता है तो escalation करूंगा
```

**Q18. Test environment 2 दिन से down है। Sprint खत्म होने वाला है। Solution?**
```
A:
1. Scrum master को escalate करूंगा
2. Dev team से local testing के लिए पूछूंगा
3. अगर possible हो तो mock environment use करूंगा
4. PO को status update करूंगा
5. Sprint goal adjust करने का suggest करूंगा
6. Retro में preventive measures discuss करूंगा
```

**Q19. PO नई story mid-sprint में add करने को कहता है। क्या करोगे?**
```
A:
1. Urgency और business value understand करूंगा
2. Impact analysis करूंगा (existing stories पर effect)
3. Team capacity check करूंगा
4. अगर critical है तो:
   - कम priority story swap-out करेंगे
   - Sprint goal adjust करेंगे
5. अगर नहीं critical तो backlog में डालने का suggest करूंगा
6. Future के लिए process improvement suggest करूंगा
```

**Q20. Automation scripts बार-बार fail हो रही हैं। क्या करोगे?**
```
A:
1. Failure pattern analyze करूंगा (flaky tests?)
2. Root cause find करूंगा:
   - Locator changes?
   - Timing issues?
   - Data issues?
3. Stable selectors use करूंगा
4. Explicit waits add करूंगा
5. Test data refresh strategy बनाूंगा
6. Regular maintenance schedule बनाूंगा
```

### Advanced (21-25)

**Q21. Agile में quality metrics क्या track करते हो?**
```
A:
- Sprint-wise defect density
- Bug escape rate (production bugs)
- Test coverage percentage
- Automation coverage और pass rate
- Mean time to detect bugs
- Mean time to fix bugs
- Customer-reported issues
```

**Q22. Continuous testing क्या है?**
```
A: Continuous testing का मतलब हर code change को automatically 
test करना। CI/CD pipeline में automated tests integrate होते 
हैं और हर commit पर run होते हैं। इससे bugs immediately मिलते 
हैं और deployment safe होता है।
```

**Q23. DevOps में tester का role क्या है?**
```
A:
- CI/CD pipeline में tests design करना
- Automated test suites maintain करना
- Quality gates define करना
- Performance testing automate करना
- Security testing integrate करना
- Monitoring और alerting setup करना
- Production incidents में root cause analysis
```

**Q24. Velocity क्या होता है? Tester कैसे contribute करता है?**
```
A: Velocity team की capacity है जो बताती है कि team हर sprint 
में कितने story points complete कर सकती है। Tester contribute 
करता है:
- Testing effort estimates देकर
- Bugs count और severity बताकर
- Automation coverage बढ़ाकर
- Quality metrics track करके
```

**Q25. Agile में test documentation कैसे manage करते हो?**
```
A:
- Lightweight documentation रखते हैं
- Wiki/confluence में maintain करते हैं
- Test cases को version control में रखते हैं
- Living documents रखते हैं (regular update)
- Screenshots/videos attach करते हैं
- Automation scripts को document करते हैं
- Knowledge sharing sessions करते हैं
```

**Q26. SAFe (Scaled Agile Framework) के बारे में क्या जानते हो?**
```
A: SAFe enterprise-level agile framework है जहाँ multiple teams 
एक साथ काम करते हैं। इसमें:
- Program Increment (PI) Planning होता है
- Multiple agile teams synchronized होते हैं
- Release Train Engineer (RTE) coordinate करता है
- Tester को cross-team coordination करना होता है
- Integration testing important होता है
```

**Q27. BDD (Behavior Driven Development) क्या है?**
```
A: BDD collaboration approach है जहाँ business language में 
requirements define होते हैं। Format:

Given [premise]
When [action]
Then [expected outcome]

Example:
Given user registered है
When user सही credentials से login करता है
Then user dashboard पे redirect होना चाहिए

Tester का role: Gherkin syntax में test scenarios लिखना
```

---

## 🎯 Quick Reference: Agile Tester Checklist

```
SPRINT START:
□ Backlog items reviewed
□ Estimates provided
□ Acceptance criteria clear
□ Test data planned

DURING SPRINT:
□ Daily standup attended
□ Test cases executed
□ Bugs reported
□ Retesting done
□ Automation updated

SPRINT END:
□ Test summary ready
□ Review demo prepared
□ Retro inputs ready
□ Next sprint planned
```

---

## 📊 Sprint Health Dashboard

```
┌────────────────────────────────────────────────────────────┐
│              SPRINT HEALTH DASHBOARD                       │
├────────────────────────────────────────────────────────────┤
│ Metric              │ Target    │ Actual    │ Status      │
├────────────────────────────────────────────────────────────┤
│ Story Completion    │ 100%      │ 95%       │ 🟡 Good     │
│ Bug Count           │ <10       │ 8         │ 🟢 Good     │
│ Test Coverage       │ >90%      │ 92%       │ 🟢 Good     │
│ Automation Pass     │ >95%      │ 97%       │ 🟢 Good     │
│ Critical Bugs       │ 0         │ 0         │ 🟢 Good     │
│ Sprint Goal         │ Achieved  │ Achieved  │ 🟢 Good     │
└────────────────────────────────────────────────────────────┘
```

---

## 🏆 Key Takeaways

```
1. Agile testing continuous है, one-time नहीं
2. Shift-left से bugs early और सस्ते मिलते हैं
3. Collaboration > Documentation
4. Automation smart करो, सब कुछ नहीं
5. Definition of Done enforce करो
6. Metrics track करो और improve करो
7. Retro में honest रहो और improve करो
```

---

*Module 06 Complete ✅*  
*Next: Module 07 - API Testing Basics*
