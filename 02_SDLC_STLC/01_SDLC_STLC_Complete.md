# 02_SDLC_STLC

## Software Development Lifecycle और Software Testing Lifecycle को गहराई से समझो
### SDLC & STLC - The Complete Process Guide

---

## 📋 Table of Contents

1. [SDLC - Software Development Lifecycle](#sdlc)
2. [STLC - Software Testing Lifecycle](#stlc)
3. [SDLC Models](#sdlc-models)
4. [Waterfall SDLC in Detail](#waterfall)
5. [Agile SDLC in Detail](#agile)
6. [V-Model in Detail](#v-model)
7. [Real Project Example](#real-example)
8. [Interview Questions](#interview)

---

## <a name="sdlc"></a>SDLC - Software Development Lifecycle

### 🎯 What is SDLC?

```
SDLC = एक structured process जो एक software product के
creation से लेकर maintenance तक पूरे journey को define करता है।

मतलब:
"एक software को कैसे बनाएंगे?
कब बनाएंगे?
कौन बनाएगा?
कैसे test करेंगे?
कब release करेंगे?
यह सब define करना।"

Simple Words में:
Software को बनाने का एक systematic process।
```

### 🔄 SDLC का Basic Flow

```
┌─────────────┐
│ PLANNING    │ → क्या बनाएंगे? कितना खर्च? कितना टाइम?
└──────┬──────┘
       ↓
┌─────────────────┐
│ REQUIREMENTS    │ → क्या requirements हैं? User क्या चाहता है?
└──────┬──────────┘
       ↓
┌─────────────────┐
│ DESIGN          │ → कैसे बनाएंगे? Architecture क्या होगी?
└──────┬──────────┘
       ↓
┌─────────────────┐
│ DEVELOPMENT     │ → Code लिखना (Developers करते हैं)
└──────┬──────────┘
       ↓
┌─────────────────┐
│ TESTING         │ → Testing करना (QA/Testers करते हैं)
└──────┬──────────┘
       ↓
┌─────────────────┐
│ DEPLOYMENT      │ → Production में डालना
└──────┬──────────┘
       ↓
┌─────────────────┐
│ MAINTENANCE     │ → Bug fixes, Updates, Support
└─────────────────┘
```

### 📊 SDLC Phases (विस्तार से)

#### **Phase 1: Planning & Requirements**

```
क्या होता है:
- Project को शुरू करने की planning
- Budget allocate करना
- Timeline define करना
- Team assemble करना
- Risks identify करना
- Requirements gathering करना

Who:
- Project Manager
- Business Analyst
- Client/Stakeholder

Output:
- Project Charter
- Requirements Document
- Project Plan
- Risk Register

Timeline:
1-2 weeks (depending on project size)

Real Example:
"Amazon को एक नया feature चाहिए:
Prime membership के लिए exclusive deals दिखाना।

Planning में:
- कितना खर्च होगा?
- कितने developers/testers चाहिए?
- 3 महीने में पूरा होगा?
- क्या risks हैं?
"
```

#### **Phase 2: Requirements Analysis & Design**

```
क्या होता है:
- Requirements को detail में समझना
- System architecture design करना
- Database design करना
- UI/UX design करना
- Technical specifications लिखना

Who:
- Solution Architect
- System Designer
- Database Administrator
- UI/UX Designer

Output:
- Design Document
- System Architecture Diagram
- Database Schema
- UI Mockups/Wireframes
- Technical Specifications

Timeline:
2-4 weeks

Real Example:
"Prime exclusive deals के लिए:
- Database में नया table बनेगा: prime_deals
- User के dashboard में नया section: Exclusive Deals
- API बनेगा: GET /api/prime-deals
- Caching strategy क्या होगी?
"
```

#### **Phase 3: Development/Coding**

```
क्या होता है:
- Developers code लिखते हैं
- Code को repository में commit करते हैं
- Code review होता है
- Testing environment में deploy करते हैं

Who:
- Software Developers
- Tech Lead
- DevOps Engineer

Output:
- Source Code
- Code Documentation
- Build (Executable)
- Deployment Guide

Timeline:
3-8 weeks (Largest phase usually)

Real Example:
"Prime deals feature का code:
- Backend API development
- Frontend components development
- Database queries writing
- Error handling
- Logging implement करना
"

Developers करते हैं (QA/Testers नहीं)
```

#### **Phase 4: Testing**

```
क्या होता है:
- QA/Testers application को test करते हैं
- Bugs find करते हैं
- Bug reports create करते हैं
- Fixes verify करते हैं
- Sign-off देते हैं

Who:
- QA Engineers
- Test Automation Engineers
- QA Lead
- Test Manager

Output:
- Test Plans
- Test Cases
- Bug Reports
- Test Execution Reports
- Sign-off Document

Timeline:
2-4 weeks (या ज्यादा, bugs के आधार पर)

Real Example:
"Prime deals को test करना:
- Valid user को deals दिख रहे हैं?
- Invalid user को deals नहीं दिख रहे?
- Deals का price सही है?
- Mobile में भी काम कर रहा है?
- Performance ठीक है?
"

यह हमारा (Testers) का phase है!
```

#### **Phase 5: Deployment/Release**

```
क्या होता है:
- Code को production environment में deploy करना
- Configuration करना
- Database migration करना
- Monitoring setup करना
- Release notes publish करना

Who:
- DevOps Engineer
- Release Manager
- System Administrator

Output:
- Deployed Application
- Release Notes
- Rollback Plan
- Monitoring Dashboard

Timeline:
1-2 days (planned release)

Real Example:
"Prime deals feature को production में डालना:
- सही server पर deploy करना
- Database migration करना
- API के endpoints update करना
- Monitoring active करना
"
```

#### **Phase 6: Maintenance & Support**

```
क्या होता है:
- Production में issues handle करना
- User support देना
- Bug fixes करना
- Minor updates करना
- Performance optimization करना

Who:
- Support Team
- DevOps
- Developers
- QA Team

Duration:
Usually 6-12 months से ज्यादा

Real Example:
"Prime deals feature के लिए:
- Users को कोई issue आए तो fix करना
- Performance issues solve करना
- New deals add करने के लिए optimization
"
```

---

## <a name="stlc"></a>STLC - Software Testing Lifecycle

### 🎯 What is STLC?

```
STLC = Testing के सभी activities का एक structured approach

SDLC का एक PART है।
(हर SDLC model में STLC happen होती है)

STLC में defined होता है:
- कब testing शुरू होगी
- कैसे testing होगी
- कौन testing करेगा
- क्या deliverables होंगी
```

### 🔄 STLC Phases (6 Main Phases)

#### **Phase 1: Test Planning**

```
क्या:
- Testing approach define करना
- Test strategy बनाना
- Resources plan करना
- Timeline plan करना
- Risks assess करना

Who:
- QA Manager
- QA Lead
- Senior Testers

Input:
- Project Charter
- Requirements Document

Output:
- Test Plan document
- Test Strategy document
- Resource plan
- Risk assessment

Deliverables में होता है:
✓ Testing objectives
✓ Scope and out of scope
✓ Entry and exit criteria
✓ Test schedule
✓ Resource requirements
✓ Risk assessment and mitigation
✓ Assumptions and dependencies

Duration:
1 week

Document Looks Like:
┌──────────────────────────┐
│ Test Plan                │
├──────────────────────────┤
│ Project: Prime Deals     │
│ Release: v2.5            │
│ Duration: 3 weeks        │
│ Team Size: 4 testers     │
│ Scope: Full feature test │
│ In-scope: Functionality, │
│          Performance,    │
│          Security        │
│ Out-of-scope: Load test  │
│ Entry Criteria:          │
│  - Build available       │
│  - Test env ready        │
│  - Req doc finalized     │
│ Exit Criteria:           │
│  - All test cases run    │
│  - All critical bugs fix │
│  - No critical bugs      │
│  - Sign-off received     │
└──────────────────────────┘
```

#### **Phase 2: Test Case Design**

```
क्या:
- Test cases create करना
- Test data prepare करना
- Test scenarios define करना
- Requirements को map करना

Who:
- Senior QA Engineers
- QA Lead
- Test Designers

Input:
- Requirements document
- Test plan

Output:
- Test cases document
- Test data
- Test case traceability matrix (RTM)

Deliverables:
✓ Test cases (with expected results)
✓ Test data files
✓ Requirements Traceability Matrix
✓ Automation script (if applicable)

Duration:
2-3 weeks

Example Test Case:
┌────────────────────────────────┐
│ Test Case ID: TC_PD_001        │
├────────────────────────────────┤
│ Title: Verify Prime Deals      │
│        visible to Prime member │
├────────────────────────────────┤
│ Precondition: User logged in,  │
│              Prime member      │
├────────────────────────────────┤
│ Test Steps:                    │
│ 1. Navigate to Home page       │
│ 2. Look for Exclusive Deals    │
│    section                     │
│ 3. Verify deals are displayed  │
│ 4. Click on a deal             │
│ 5. Verify discount percentage  │
├────────────────────────────────┤
│ Expected Result:               │
│ All prime deals should be      │
│ visible with correct prices    │
│ and discounts                  │
├────────────────────────────────┤
│ Test Data:                     │
│ User: prime_user@amazon.com    │
│ Password: Test@123             │
└────────────────────────────────┘
```

#### **Phase 3: Test Environment Setup**

```
क्या:
- Test environment prepare करना
- Test data load करना
- Tools setup करना
- Network configure करना
- Database setup करना

Who:
- QA Engineer
- DevOps Engineer
- System Administrator

Input:
- Test plan
- Test data files

Output:
- Ready-to-use test environment
- Test data loaded
- Tools configured
- Access credentials

Duration:
3-5 days

Checklist:
□ Server/Database ready?
□ Application deployed?
□ Network connectivity ok?
□ Test data loaded?
□ Tools (JIRA, etc.) configured?
□ Access credentials distributed?
□ Documentation updated?
□ Baseline performance captured?
```

#### **Phase 4: Test Case Execution**

```
क्या:
- Test cases को run करना
- Actual results note करना
- Expected results से compare करना
- Bugs find करना
- Test results document करना

Who:
- QA Engineers
- Senior Testers

Input:
- Test cases
- Test environment (ready)
- Test data

Output:
- Test execution reports
- Bug reports
- Test coverage metrics

Duration:
2-4 weeks (Largest phase)

What We Do:
1. Test case को open करना
2. Preconditions verify करना
3. Test steps को follow करना
4. Actual result observe करना
5. Expected result से compare करना

Result के Options:
✓ PASS: Expected = Actual
✗ FAIL: Expected ≠ Actual
⚠ BLOCKED: Can't test (env issue)
$ NOT RUN: No time, or not needed

Example Execution:
Test Case: TC_PD_001

Step 1: Open application ✓
        Expected: Application loads
        Actual: Application loaded successfully

Step 2: Login with prime user ✓
        Expected: Login successful
        Actual: Login successful

Step 3: Check Exclusive Deals ✗
        Expected: Deals should display with 20% discount
        Actual: Only 10% discount showing

Result: FAILED
Bug Created: BUG_PD_001
```

#### **Phase 5: Bug Reporting & Tracking**

```
क्या:
- Bugs को detailed report में document करना
- JIRA में log करना
- Severity/Priority assign करना
- Developer को assign करना
- Status track करना

Who:
- QA Engineers (report करते हैं)
- Dev Lead (triage करता है)
- Developers (fix करते हैं)
- QA (verify करते हैं)

Output:
- Bug reports in JIRA
- Bug dashboard
- Daily bug status report

Bug Report Format:
┌─────────────────────────────────┐
│ Bug ID: BUG_PD_001              │
├─────────────────────────────────┤
│ Title: Prime deal discount       │
│        calculation is wrong      │
│                                 │
│ Severity: Critical              │
│ Priority: High                  │
│ Status: Open                    │
│ Assigned To: Dev_Lead           │
│                                 │
│ Description:                    │
│ Prime members are seeing only   │
│ 10% discount instead of 20%     │
│                                 │
│ Steps to Reproduce:             │
│ 1. Login as prime user          │
│ 2. Go to Exclusive Deals        │
│ 3. Check discount percentage    │
│                                 │
│ Expected: 20% discount          │
│ Actual: 10% discount            │
│                                 │
│ Environment: QA Server          │
│ Browser: Chrome (Latest)        │
│ OS: Windows 10                  │
│                                 │
│ Attachments: Screenshot.png     │
│ Reporter: Tester_Name           │
│ Reported Date: 26-Jan-2026      │
└─────────────────────────────────┘
```

#### **Phase 6: Test Sign-Off**

```
क्या:
- सभी testing complete करना
- Final report prepare करना
- Release decision लेना
- Go/No-Go decide करना
- Sign-off देना

Who:
- QA Manager
- QA Lead
- Project Manager
- Stakeholder

Output:
- Final test summary report
- Sign-off document
- Known issues list
- Release recommendation

Sign-Off Document में:
✓ Total test cases: X
✓ Passed: Y
✓ Failed: Z
✓ Blocked: W
✓ Not Run: V
✓ Defect Summary
  - Critical: 0
  - High: 2
  - Medium: 5
  - Low: 10
✓ Coverage Metrics
  - Functionality: 95%
  - Requirements: 98%
  - Critical Path: 100%
✓ Recommendation: RELEASE / HOLD

Timeline:
1 day
```

---

## <a name="sdlc-models"></a>SDLC Models (Different Approaches)

### 🔀 4 Main SDLC Models

#### **Model 1: Waterfall Model** (Sequential)

```
पानी की तरह बहता है → एक phase के बाद दूसरा

Flow:
Requirements → Design → Development → Testing → Deployment → Maintenance

फीचर:
- Linear process
- एक बार आगे गए, तो पीछे नहीं आ सकते
- Proper documentation
- Clear phases
- Long-term planning

Advantages:
✓ Clear structure
✓ Easy to understand
✓ Good for fixed requirements
✓ Easy to track progress

Disadvantages:
✗ Testing late में होती है
✗ Issues late में पता चलते हैं
✗ Change लगना मुश्किल होता है
✗ Customer involvement कम

When To Use:
- Government projects
- Fixed requirements
- Maintenance projects
- Legacy systems

Real Example:
Banking system का major upgrade

Timeline:
Req: Month 1 → Design: Month 2 → Dev: Months 3-4 → 
Testing: Months 5-6 → Release: Month 7 → Maintenance: Month 8+

Problems:
अगर Testing में big bugs मिलें, तो
पूरी चीज़ delay हो जाती है!
```

#### **Model 2: Agile Model** (Iterative)

```
छोटे-छोटे cycles में काम करते हैं

Sprint-based Development:
Sprint 1 (2 weeks) → Sprint 2 (2 weeks) → Sprint 3 (2 weeks) ...

हर Sprint में:
- Plan करो
- Develop करो
- Test करो
- Deploy करो (कभी-कभी)
- Review करो

Advantages:
✓ Quick feedback
✓ Early testing
✓ Flexibility
✓ Customer satisfaction
✓ Less risk

Disadvantages:
✗ Requires continuous communication
✗ Harder to estimate
✗ Less documentation

When To Use:
- Startups
- Evolving requirements
- Fast-changing market
- Customer-centric projects

Real Example:
Mobile app development

Timeline:
Sprint 1: Build login feature
Sprint 2: Build search feature
Sprint 3: Build shopping cart
Sprint 4: Payment integration

फायदा:
अगर Sprint 1 में issues आएं, तो
quickly fix करके Sprint 2 में move कर सकते हो।

This is MOST USED model in 2026!
```

#### **Model 3: V-Model** (Verification & Validation)

```
Testing हर development phase के साथ होती है

Structure:
Requirements Phase → Design Phase → Code Phase
    ↓ तय करो      ↓ define करो      ↓ लिखो
    ↓                                      ↓
UAT Testing ← Integration Testing ← Unit Testing
Test करो ← Test करो ← Test करो

फीचर:
- Testing parallel होती है
- Early bug detection
- Clear test planning
- Phases well-defined

Advantages:
✓ Defects early detected
✓ Clear structure
✓ Good for larger projects
✓ High quality

Disadvantages:
✗ Less flexible
✗ Late customer involvement
✗ More documentation

When To Use:
- Large projects
- Fixed requirements
- Manufacturing/Automotive
- Medical devices

Real Example:
Enterprise application development

Timeline:
Requirements → Design → Dev → Unit Test → 
Integration Test → System Test → UAT

फायदा:
Testing शुरू से ही planned है।
```

#### **Model 4: Spiral Model** (Risk-driven)

```
Risk को कम करने के लिए iterative cycles

हर Cycle में:
1. Planning
2. Risk Analysis
3. Development
4. Testing & Evaluation

फीचर:
- Risk-focused
- Iterative
- Flexibility
- Prototypes बनाते हैं

Advantages:
✓ Risk minimization
✓ Flexibility
✓ Good for complex projects
✓ Customer involvement

Disadvantages:
✗ Complex
✗ Expensive
✗ Requires expertise

When To Use:
- High-risk projects
- Complex systems
- Aerospace projects
- Large-scale systems
```

---

## <a name="waterfall"></a>Waterfall SDLC in Detail

### 💧 Complete Waterfall Process

```
Timeline: 12 Months (Example)

Month 1-2: REQUIREMENTS PHASE
├─ Client से requirements gather करो
├─ Document बनाओ
├─ Sign-off लो
└─ QA को requirement review करवाओ

Month 3: DESIGN PHASE
├─ System architecture design करो
├─ Database design करो
├─ Technical specifications लिखो
└─ Design review

Month 4-7: DEVELOPMENT PHASE
├─ Developers code लिखते हैं
├─ Code review
├─ Build creation
└─ Developers अपना unit testing करते हैं

Month 8-10: TESTING PHASE (QA का biggest phase)
├─ Test plan finalize करो
├─ Test cases design करो
├─ Environment setup करो
├─ Test execution करो
├─ Bugs report करो
├─ Retesting करो
└─ Sign-off

Month 11: DEPLOYMENT PHASE
├─ Code को production में डालो
├─ Data migration करो
├─ Monitoring setup करो
└─ Release communication

Month 12+: MAINTENANCE PHASE
├─ Support provide करो
├─ Issues fix करो
├─ Updates deliver करो
└─ Performance monitor करो
```

### 📊 Waterfall में Testing

```
Waterfall में Testing का role:

PHASE 1-7 में:
- QA planning करता है
- Test cases design करता है
- Test data prepare करता है
- (लेकिन actual testing नहीं)

PHASE 8 में (Testing Phase):
- Actual testing होती है
- All test cases execute होते हैं
- Bugs मिलते हैं
- Fixes होते हैं

क्या होता है अगर Phase 8 में:
- 100 bugs मिल जाएं?
- Phase 11 में delay हो जाता है!
- Release का schedule miss हो जाता है!

यही Waterfall की limitation है।
```

### ⚠️ Waterfall में Testing की Challenges

```
1. LATE TESTING
   - Code complete होने का wait
   - Late bug discovery
   - Late fixes = Delay

2. LIMITED FLEXIBILITY
   - Requirements change नहीं कर सकते
   - Scope change मुश्किल है
   - Customer feedback late में

3. HIGH RISK
   - अगर Phase 7 में issues हों
   - तो पूरा project delay
   - Expensive

4. TESTING PRESSURE
   - सब एक बार में test करना होता है
   - Time pressure होती है
   - Quality compromise हो सकता है

Real Example:
एक bank का project 12 months में था।
Month 10 में testing शुरू हुई।
50 critical bugs मिले।
Fixing में 2 महीने लग गए।
Project 2 महीने late हुआ।
```

---

## <a name="agile"></a>Agile SDLC in Detail

### 🚀 Agile Process (Most Modern)

```
Duration: 2-week Sprints (आमतौर पर)

Total Project: 6 Sprints (3 months)

┌─────────────────────────┐
│    Product Backlog      │
│ (सभी features की list) │
└──────────────┬──────────┘
               ↓
┌─────────────────────────────────┐
│     SPRINT PLANNING              │
│ (कौन से features इस sprint में) │
└──────────────┬──────────────────┘
               ↓
        ┌──────────────────┐
        │  SPRINT BACKLOG  │
        │ (2-week work)    │
        └────────┬─────────┘
                 ↓
    ┌────────────────────────┐
    │  DEVELOPMENT + TESTING │
    │     (Parallel!)        │
    │                        │
    │ Day 1: Feature A dev   │
    │ Day 2: Feature A test  │
    │ Day 3: Feature B dev   │
    │ Day 4: Feature B test  │
    │ ...                    │
    └────────────┬───────────┘
                 ↓
        ┌──────────────────┐
        │  SPRINT REVIEW   │
        │ (Demo to client) │
        └────────┬─────────┘
                 ↓
        ┌──────────────────┐
        │ SPRINT RETRO     │
        │ (Improve process)│
        └────────┬─────────┘
                 ↓
        Next Sprint शुरू
```

### 👥 Agile में की Roles

```
1. PRODUCT OWNER
   - Requirements define करता है
   - Priority set करता है
   - Backlog manage करता है

2. SCRUM MASTER
   - Process facilitate करता है
   - Blockers remove करता है
   - Team का mentoring करता है

3. DEVELOPMENT TEAM
   - Code लिखता है
   - Code review करता है
   - Unit testing करता है

4. QA/TEST ENGINEER
   - Test cases लिखता है
   - Features test करता है
   - Bugs report करता है
   - Part of team है (सब की तरह)
```

### 📅 Agile में Daily Activities

```
Daily Standup (15 minutes):
"What did you do yesterday?
What will you do today?
What are blockers?"

Example:
Developer: "Yesterday wrote login API.
Today will work on payment API.
No blockers."

QA: "Yesterday tested login feature.
Today will test payment flow.
Waiting for payment API completion."

This keeps everyone aligned!
```

### ✅ Agile में Testing

```
Key Difference from Waterfall:

Waterfall:
- Development → Testing
- Sequential

Agile:
- Development ↔ Testing
- Parallel

फायदे:
✓ Early bug detection
✓ Quick fixes
✓ Less late-phase surprises
✓ Customer feedback regular

Timeline Example:
Sprint 1 (2 weeks):
- Day 1-3: Login feature development
- Day 2-4: Login feature testing
- Day 5: Bug fixes + Retesting
- Day 10: Sprint review

अगर bugs मिलें, तो quickly fix हो जाते हैं।
Demo करते हो client को।
Next sprint में नया feature।
```

### 🎯 Agile Ceremonies

```
1. SPRINT PLANNING (1 hour)
   - Backlog items select करो
   - Estimation करो
   - Sprint goal define करो

2. DAILY STANDUP (15 minutes)
   - Progress share करो
   - Blockers identify करो

3. SPRINT REVIEW (1 hour)
   - Demo करो
   - Client feedback लो

4. SPRINT RETROSPECTIVE (1 hour)
   - क्या अच्छा रहा?
   - क्या बुरा रहा?
   - कैसे improve करें?

All together = healthy agile!
```

### ⚖️ Agile vs Waterfall

```
Criteria          Waterfall           Agile
────────────────────────────────────────────────
Schedule          Fixed               Flexible
Requirements      Defined upfront     Evolving
Testing          Late                Continuous
Customer         End                 Regular
Feedback                             
Risk              High (late discover) Low
Cost              Predictable         Variable
Flexibility      Low                 High
Documentation    Extensive           Minimal
Best For         Fixed scope         Evolving scope
```

---

## <a name="real-example"></a>Real Project Example

### 💼 Case Study: Building an Instagram-like Social App

#### **Waterfall Approach**

```
Timeline: 12 Months

MONTH 1: REQUIREMENTS
- Client wants a photo sharing app
- Features list: Upload, Like, Comment, Follow, Feed, Search
- Detailed requirements document
- Sign-off

MONTH 2-3: DESIGN
- Database schema: Users, Photos, Comments, Likes
- API design: 20+ APIs
- UI mockups

MONTH 4-7: DEVELOPMENT
- Backend APIs
- Mobile app (iOS/Android)
- Web app
- Admin panel
- Unit testing by devs

MONTH 8-10: TESTING (QA का biggest phase)
- Smoke testing
- Functional testing
- Performance testing
- Security testing
- UAT

MONTH 8: ISSUE!
"Photo upload feature में issue है।
Large photos crash कर रहे हैं।"

Fixing में 3 weeks लगेंगे।

MONTH 11: Delayed release
Expected: Month 11
Actual: Month 12 (1 month delay)

Cost impact:
- Team cost extra
- Market opportunity miss
- Competitor advantage
```

#### **Agile Approach (Same Project)**

```
Duration: 6 Sprints (3 months)

SPRINT 1 (Week 1-2):
Feature: User Registration & Login
Dev: 1.5 weeks
Test: 0.5 week
Result: Working feature

SPRINT 2 (Week 3-4):
Feature: Photo Upload
Dev: 1 week
Test: 1 week
Bugs found: Upload feature issue discovered
Fix: Done in sprint itself
Result: Working feature

SPRINT 3 (Week 5-6):
Feature: Like & Comment
Dev: 1.5 weeks
Test: 0.5 week
Result: Working feature

SPRINT 4 (Week 7-8):
Feature: Follow & Feed
Dev: 1.5 weeks
Test: 0.5 week
Result: Working feature

SPRINT 5 (Week 9-10):
Feature: Search & Notifications
Dev: 1.5 weeks
Test: 0.5 week
Result: Working feature

SPRINT 6 (Week 11-12):
Feature: Performance optimization & Security
Dev: 1 week
Test: 1 week
Result: App ready for release

Result: ON TIME RELEASE (3 months)

Key Benefit:
Photo upload issue in Sprint 2.
अगर issue Waterfall में late discover होता,
तो massive delay होता।

Agile में early found और fixed!
```

### 📊 Project Comparison

```
                    Waterfall       Agile
Timeline           12 months        3 months
Testing Starts     Month 8          Week 1
First Release      Month 12         Month 1 (MVP)
Bug Discovery      Late            Early
Cost               High            Lower
Client Feedback    Once            Every 2 weeks
Flexibility        Low             High
Risk               High            Low
Success Rate       50%             80%+
```

---

## <a name="interview"></a>Interview Questions

### 💼 Interview Preparation

#### **Q1: SDLC क्या है? Simple करके समझाओ।**

```
Answer:
"SDLC एक structured process है जो एक software को
बनाने की शुरुआत से लेकर release और maintenance तक
सभी phases को define करता है।

इसमें 6 main phases हैं:
1. Planning
2. Requirements & Design
3. Development
4. Testing
5. Deployment
6. Maintenance

प्रत्येक phase के objectives, deliverables, और timeline
clearly defined होते हैं।"
```

#### **Q2: SDLC और STLC में क्या difference है?**

```
Answer:
SDLC (Software Development Lifecycle):
- पूरा development lifecycle
- 6 phases
- सभी activities शामिल (dev, testing, deploy)

STLC (Software Testing Lifecycle):
- सिर्फ testing का lifecycle
- SDLC का एक part
- Testing specific processes

आसान भाषा में:
SDLC = पूरी journey
STLC = Testing का part

जैसे:
पूरा school day = SDLC
Math class = STLC
```

#### **Q3: Waterfall vs Agile - दोनों में कौन बेहतर है?**

```
Answer:
"दोनों के अपने use cases हैं।

Waterfall अच्छा है:
- Fixed requirements के लिए
- Government projects
- Documentation-heavy projects
- Long-term projects

Agile अच्छा है:
- Evolving requirements के लिए
- Startups
- Market-driven products
- Customer-centric projects

2026 में, Agile ज्यादा popular है
क्योंकि बाजार तेजी से बदल रहा है।"
```

#### **Q4: Testing late में क्यों नहीं करते?**

```
Answer:
"अगर testing late में होगी:

1. Bugs late में discover होंगे
2. Fixing में ज्यादा time लगेगा
3. Release delay होगा
4. Cost बढ़ेगा
5. Quality compromise होगी

Example:
Waterfall में Month 10 में 100 bugs मिलें।
Fixing में 2 महीने लगें।
Project 2 महीने late।

Agile में
Week 1 में feature ready होता है।
Issues immediately fix होते हैं।
No delays।

इसलिए 'Test Early, Test Often' कहते हैं।"
```

#### **Q5: STLC के 6 phases को समझाओ।**

```
Answer:

1. TEST PLANNING
   - क्या test करना है
   - कब करना है
   - कौन करेगा

2. TEST DESIGN
   - Test cases create करना
   - Test data prepare करना

3. TEST SETUP
   - Environment ready करना
   - Tools configure करना

4. TEST EXECUTION
   - Actual testing करना
   - Results document करना

5. BUG REPORTING
   - Bugs report करना
   - Developer को assign करना
   - Fixes verify करना

6. SIGN-OFF
   - Final report देना
   - Release recommendation
```

---

## 🎯 Key Takeaways

```
✓ SDLC एक systematic process है
✓ Testing हर SDLC में होती है
✓ Different models different scenarios के लिए
✓ Waterfall = Fixed scope
✓ Agile = Evolving scope
✓ Testing जितनी जल्दी हो, अच्छा है
✓ Modern companies Agile use करते हैं
```

---

## 📚 Next Steps

अब तुम समझ गए:
- ✓ SDLC क्या है
- ✓ STLC क्या है
- ✓ Different SDLC models
- ✓ Testing हर phase में

अगला: 📖 **03_Testing_Types** - Different types की testing को समझेंगे!

---

*Created: 2026*  
*Level: Beginner to Intermediate*  
*Language: Hinglish*
