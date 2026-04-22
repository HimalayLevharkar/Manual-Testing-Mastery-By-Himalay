# 04_Test_Case_Design_Techniques

## Test Cases को Professional तरीके से design करना
### Complete Guide to Test Case Design & Techniques

---

## 📋 Table of Contents

1. [Test Case क्या है?](#what-is-tc)
2. [Test Case Structure](#structure)
3. [Test Case Design Techniques](#techniques)
4. [Real-World Examples](#examples)
5. [Best Practices](#best-practices)
6. [Interview Questions](#interview)

---

## <a name="what-is-tc"></a>Test Case क्या है?

### 📝 Definition

```
Test Case = एक documented sequence of steps जो
एक specific scenario को test करने के लिए execute किया जाता है।

Simple Meaning:
"कोई feature को test करने के लिए क्या-क्या steps दोहराते हो,
उसे एक documented format में लिखना = Test Case"

Real Analogy:
Cake बनाने की recipe की तरह:
- Ingredients (Preconditions)
- Steps (Test Steps)
- Result (Expected Result)

Test Case को कोई भी execute कर सके,
वही अच्छा test case है।
```

### 🎯 Why Test Cases Matter?

```
✓ Consistency - हर कोई same तरीके से test करे
✓ Reusability - बार-बार use कर सको
✓ Documentation - Reference के लिए
✓ Coverage - क्या सब scenarios cover हैं
✓ Training - नए testers को सिखा सको
✓ Audit Trail - कौन क्या test किया
✓ Regression - पुरानी issues दोबारा न आएं
```

---

## <a name="structure"></a>Test Case Structure

### 📋 Standard Test Case Format

```
┌─────────────────────────────────────────────────┐
│ TEST CASE ID         │ TC_LOGIN_001            │
├──────────────────────┼─────────────────────────┤
│ Title                │ Valid User Login        │
├──────────────────────┼─────────────────────────┤
│ Objective            │ Verify valid login works│
├──────────────────────┼─────────────────────────┤
│ Module               │ Authentication          │
├──────────────────────┼─────────────────────────┤
│ Precondition         │ 1. User registered     │
│                      │ 2. User not logged in  │
│                      │ 3. Browser opened      │
├──────────────────────┼─────────────────────────┤
│ Test Steps           │ 1. Navigate to login   │
│                      │ 2. Enter username      │
│                      │ 3. Enter password      │
│                      │ 4. Click Login button  │
├──────────────────────┼─────────────────────────┤
│ Test Data            │ Username: john@test    │
│                      │ Password: Test@123     │
├──────────────────────┼─────────────────────────┤
│ Expected Result      │ 1. User logged in      │
│                      │ 2. Redirected to home  │
│                      │ 3. User name visible   │
├──────────────────────┼─────────────────────────┤
│ Actual Result        │ [Tester fills after]   │
├──────────────────────┼─────────────────────────┤
│ Status               │ Pass / Fail / Blocked  │
├──────────────────────┼─────────────────────────┤
│ Severity (if failed) │ Critical / High / Med   │
├──────────────────────┼─────────────────────────┤
│ Executed By          │ Tester Name             │
├──────────────────────┼─────────────────────────┤
│ Executed Date        │ 26-Jan-2026             │
├──────────────────────┼─────────────────────────┤
│ Remarks              │ [Any notes]             │
└─────────────────────────────────────────────────┘
```

### 📝 Detailed Field Explanation

```
1. TEST CASE ID
   Format: TC_MODULE_NUMBER
   Example: TC_LOGIN_001, TC_PAYMENT_015
   Purpose: Unique identification
   Important: Sequential, easy to track

2. TITLE
   Clear, descriptive, concise
   Example: "Valid User Login"
   NOT: "Test login" (too vague)
   NOT: "User can click login button and it works" (too long)

3. OBJECTIVE
   क्या verify करना है?
   Example: "Verify that valid user can login successfully"

4. MODULE / FEATURE
   किस feature का है?
   Example: Authentication, Payment, Search

5. PRECONDITION
   क्या prerequisites हैं test execute करने से पहले?
   Example:
   - User must be registered
   - User should not be logged in
   - Browser must be open
   - Internet connection required

6. TEST STEPS
   Step-by-step actions
   Numbered, clear, detailed
   Each step should be atomic (एक काम करे)
   
   Good:
   Step 1: Open website
   Step 2: Click Login button
   Step 3: Enter email "john@gmail.com"
   
   Bad:
   Step 1: Open website, click login, enter email

7. TEST DATA
   Actual values use करोगे
   Example:
   - Email: test@example.com
   - Password: Test@123
   - Phone: 9876543210

8. EXPECTED RESULT
   क्या होना चाहिए अगर test pass हो?
   Clear, specific, measurable
   
   Good:
   - User logged in
   - Redirected to dashboard
   - "Welcome John" message displayed
   
   Bad:
   - Everything works
   - Login successful

9. ACTUAL RESULT
   [Tester fills after execution]
   क्या actually happen हुआ?

10. STATUS
    PASS: Expected = Actual
    FAIL: Expected ≠ Actual
    BLOCKED: कुछ barrier है test करने में
    NOT RUN: execute नहीं किया

11. SEVERITY (अगर fail हो)
    Critical: Product unusable
    High: Major functionality broken
    Medium: Feature partially working
    Low: Minor issue, workaround available

12. EXECUTED BY / DATE
    Audit trail के लिए
    किसने किया, कब किया
```

---

## <a name="techniques"></a>Test Case Design Techniques

### 🎯 Common Techniques (Manual Testers के लिए)

#### **1. Equivalence Class Partitioning (ECP)** 📊

```
Concept:
Input को groups में divide करना
उस तरीके से कि सब groups same तरीके से behave करें।

Logic:
"अगर 10 valid inputs सब same तरीके से काम करते हैं,
तो सिर्फ 1 को test करो।"

Example: AGE का validation

Requirements:
- 18 years or above allowed
- Below 18 years denied

Age को groups में divide करो:
- Valid class: 18-100 (acceptable)
- Invalid class: 0-17 (not acceptable)
- Invalid class: 101+ (not realistic)

Test Cases:
1. Age = 20 (Valid class) → Should allow ✓
2. Age = 15 (Invalid class) → Should deny ✓
3. Age = 150 (Invalid class) → Should deny ✓

बाकी सभी valid ages (25, 30, 40, etc.) को test करने की जरूरत नहीं।
सब same तरीके से काम करेंगे।

Real Example: PIN Code
Requirement: 6 digit PIN

Classes:
- Valid: 123456 (6 digits)
- Invalid: 12345 (5 digits)
- Invalid: 1234567 (7 digits)
- Invalid: ABCDEF (non-numeric)

Test:
1. 123456 → Accept ✓
2. 12345 → Reject ✓
3. 1234567 → Reject ✓
4. ABCDEF → Reject ✓

बाकी सभी 6-digit numbers same काम करेंगे।
```

#### **2. Boundary Value Analysis (BVA)** 🎯

```
Concept:
Testing करो boundaries पर - values के edge पर।
क्योंकि यहीं bugs ज्यादा आते हैं।

Logic:
"Boundary cases सबसे ज्यादा bugs का घर होते हैं।"

Formula:
If valid range है: 18-65
Then test करो: 17, 18, 65, 66

Example: Temperature control system

Requirement:
- Valid temperature: 16°C to 32°C
- Below 16°C: Too cold (heating on)
- Above 32°C: Too hot (cooling on)

Boundary Values:
- 15°C (just below min) → Heating should be ON
- 16°C (exact min) → Normal
- 32°C (exact max) → Normal
- 33°C (just above max) → Cooling should be ON

Test Cases:
1. Set 15°C → Heater should activate ✓
2. Set 16°C → Normal temperature ✓
3. Set 25°C → Normal temperature ✓
4. Set 32°C → Normal temperature ✓
5. Set 33°C → Cooling should activate ✓

Real Example: Discount calculation

Rule: 
- Purchase < Rs. 1000: 0% discount
- Rs. 1000 - Rs. 5000: 10% discount
- Rs. 5000 - Rs. 10000: 15% discount
- > Rs. 10000: 20% discount

Boundary test cases:
- Rs. 999 (just below 1000) → 0% discount
- Rs. 1000 (exact boundary) → 10% discount
- Rs. 4999 (just below 5000) → 10% discount
- Rs. 5000 (exact boundary) → 15% discount
- Rs. 9999 (just below 10000) → 15% discount
- Rs. 10000 (exact boundary) → 20% discount
- Rs. 10001 (just above 10000) → 20% discount

Common bugs caught by BVA:
✓ Off-by-one errors
✓ Boundary condition logic errors
✓ Inclusive/exclusive issues
```

#### **3. Decision Table Testing** 📋

```
Concept:
Multiple conditions को एक table में organize करके
सभी combinations को test करना।

जब use करें:
- Multiple conditions
- Multiple outcomes
- Complex business logic

Example: Bank Account Opening

Conditions:
- Age >= 18? (Y/N)
- Valid ID? (Y/N)
- Minimum balance? (Y/N)

Decision Table:
┌───┬─────┬────────┬──────┬────────────────┐
│TC│ Age │  ID    │Balance│ Result          │
├───┼─────┼────────┼──────┼────────────────┤
│ 1 │  Y  │  Y     │  Y   │ Account Open    │
│ 2 │  Y  │  Y     │  N   │ Reject (Low Bal)│
│ 3 │  Y  │  N     │  Y   │ Reject (No ID)  │
│ 4 │  Y  │  N     │  N   │ Reject (Multi)  │
│ 5 │  N  │  Y     │  Y   │ Reject (Minor)  │
│ 6 │  N  │  Y     │  N   │ Reject (Multi)  │
│ 7 │  N  │  N     │  Y   │ Reject (Multi)  │
│ 8 │  N  │  N     │  N   │ Reject (Multi)  │
└───┴─────┴────────┴──────┴────────────────┘

Total combinations: 2^3 = 8
Test cases needed: 8

Real Example: E-commerce Checkout

Conditions:
- Valid card? (Y/N)
- Sufficient balance? (Y/N)
- Delivery address? (Y/N)
- Coupon valid? (Y/N)

Total combinations: 2^4 = 16
सब 16 को test करना होगा complex logic के लिए।
```

#### **4. State Transition Testing** 🔄

```
Concept:
Application कितने states में जा सकता है
और एक state से दूसरे में कैसे जाता है।

जब use करें:
- State-based applications
- Workflow systems
- Order lifecycle

Example: Order Status Flow

States:
- New Order
- Processing
- Shipped
- Delivered
- Returned

Transitions:
New Order → Processing → Shipped → Delivered
         ↘ Cancelled
Delivered → Returned → Refunded

Valid Transitions:
1. New → Processing ✓
2. Processing → Shipped ✓
3. Shipped → Delivered ✓
4. Delivered → Returned ✓
5. New → Cancelled ✓
6. Returned → Refunded ✓

Invalid Transitions (नहीं होने चाहिए):
- New → Delivered (बिना shipping के) ✗
- Shipped → New (पीछे नहीं आ सकते) ✗
- Cancelled → Shipped (cancel order ship नहीं हो सकता) ✗

Test Cases:
1. Order place करो → State = New ✓
2. Payment process करो → State = Processing ✓
3. Item dispatch करो → State = Shipped ✓
4. Item delivered → State = Delivered ✓
5. Customer return request → State = Returned ✓
6. Refund process → State = Refunded ✓

Real Example: User Account

States:
- New (created)
- Active (verified)
- Suspended (rule violation)
- Closed (user deleted)

Valid transitions:
New → Active (after verification)
Active → Suspended (on violation)
Suspended → Active (after appeal approval)
Active → Closed (user request)

Invalid:
Closed → Active (can't reactivate)
```

#### **5. Use Case Based Testing** 🎬

```
Concept:
Real-world user scenarios को based करके test cases बनाना।

जब use करें:
- User-centric testing
- End-to-end flows
- Business processes

Example: Online Shopping

Use Case 1: "Customer चाहता है product खरीदना"

Main Flow:
1. Customer login करता है
2. Search करता है product
3. Product compare करता है
4. Add करता है cart में
5. Checkout करता है
6. Payment करता है
7. Order confirm होता है
8. Notification मिलता है

Alternate Flows:
- Product out of stock → सुझाव दो similar product
- Payment fail → Retry या alternate payment
- Coupon expired → Alert करो

Test Cases:
1. Happy path: सब steps successfully complete
2. Out of stock: Alternative suggest करो
3. Payment failure: Retry option दो
4. Coupon invalid: Clear message दो
5. Address invalid: Error show करो

यह approach real users को समझ आता है।
```

---

## <a name="examples"></a>Real-World Examples

### 💼 Example 1: Login Feature Test Cases

```
Module: Authentication
Feature: User Login

TC_AUTH_001: Valid Login
├─ Precondition: Unregistered user, browser open
├─ Steps:
│  1. Navigate to login page
│  2. Enter valid email: john@gmail.com
│  3. Enter valid password: Test@123
│  4. Click Login button
├─ Expected: User logged in, redirected to dashboard
└─ Status: [To be filled]

TC_AUTH_002: Invalid Password
├─ Precondition: Registered user, not logged in
├─ Steps:
│  1. Navigate to login page
│  2. Enter valid email: john@gmail.com
│  3. Enter invalid password: wrong123
│  4. Click Login button
├─ Expected: Error message "Invalid password"
└─ Status: [To be filled]

TC_AUTH_003: Invalid Email Format
├─ Steps:
│  1. Navigate to login page
│  2. Enter invalid email: invalidmail
│  3. Enter password: Test@123
│  4. Click Login button
├─ Expected: Error "Invalid email format"
└─ Status: [To be filled]

TC_AUTH_004: Empty Email
├─ Steps:
│  1. Navigate to login page
│  2. Leave email field empty
│  3. Enter password: Test@123
│  4. Click Login button
├─ Expected: Error "Email required"
└─ Status: [To be filled]

TC_AUTH_005: Account Locked (5 Failed Attempts)
├─ Precondition: Account exists, wrong password 5 times already
├─ Steps:
│  1. Navigate to login page
│  2. Enter email: john@gmail.com
│  3. Enter wrong password: wrong
│  4. Click Login button
├─ Expected: Error "Account locked for 30 minutes"
└─ Status: [To be filled]

Coverage:
- Positive: 1 test case
- Negative: 4 test cases
- Edge cases: 1 test case
```

### 💼 Example 2: Payment Feature Test Cases

```
Module: Payment
Feature: Card Payment

TC_PAY_001: Valid Card Payment
├─ Steps:
│  1. Proceed to payment
│  2. Select Credit Card
│  3. Enter card number: 4532015112830366
│  4. Enter expiry: 12/25
│  5. Enter CVV: 123
│  6. Click Pay
├─ Expected: Payment successful, order confirmed
└─ Status: [To be filled]

TC_PAY_002: Expired Card
├─ Steps:
│  1. Proceed to payment
│  2. Select Credit Card
│  3. Enter expired card: 4532015112830366
│  4. Enter expiry: 12/23 (already expired)
│  5. Enter CVV: 123
│  6. Click Pay
├─ Expected: Error "Card expired"
└─ Status: [To be filled]

TC_PAY_003: Invalid CVV
├─ Steps:
│  1. Proceed to payment
│  2. Enter valid card
│  3. Enter invalid CVV: 99
│  4. Click Pay
├─ Expected: Error "Invalid CVV"
└─ Status: [To be filled]

TC_PAY_004: Insufficient Balance
├─ Precondition: Card has Rs. 100, payment is Rs. 5000
├─ Steps:
│  1. Proceed to payment
│  2. Enter valid card
│  3. Amount: 5000
│  4. Click Pay
├─ Expected: Error "Insufficient balance"
└─ Status: [To be filled]

TC_PAY_005: Payment Timeout
├─ Steps:
│  1. Proceed to payment
│  2. Enter card details
│  3. Wait for 60 seconds (timeout)
├─ Expected: Error "Request timeout, try again"
└─ Status: [To be filled]

Decision Table for Payment:
┌─────────┬──────────┬─────────┬─────────────┐
│ Card    │ Balance  │ CVV     │ Result      │
├─────────┼──────────┼─────────┼─────────────┤
│ Valid   │ Sufficient│ Valid  │ Success     │
│ Valid   │ Sufficient│ Invalid│ CVV Error   │
│ Expired │ Sufficient│ Valid  │ Card Expired│
│ Valid   │ Low      │ Valid   │ Low Balance │
└─────────┴──────────┴─────────┴─────────────┘
```

---

## <a name="best-practices"></a>Best Practices

### ✅ Test Case Writing Guidelines

```
1. CLEAR TITLE
   ❌ Bad: "Login Test"
   ✅ Good: "Valid user should be able to login successfully"

2. ATOMIC STEPS
   ❌ Bad: "Open browser, go to login, enter credentials, login"
   ✅ Good: 
      Step 1: Open browser
      Step 2: Navigate to login page
      Step 3: Enter email
      Step 4: Enter password
      Step 5: Click Login

3. SPECIFIC DATA
   ❌ Bad: "Enter username"
   ✅ Good: "Enter username: john@gmail.com"

4. CLEAR EXPECTED RESULTS
   ❌ Bad: "It should work"
   ✅ Good: "User should be redirected to dashboard and see 'Welcome John' message"

5. PRECONDITIONS
   Always define what must be true before test execution
   "User must be registered and not logged in"

6. ONE SCENARIO PER TEST CASE
   ❌ Bad: "Test valid and invalid login"
   ✅ Good: "Test valid login" (एक test case), "Test invalid login" (अलग test case)

7. REUSABILITY
   Test case ऐसा लिखो कि कोई भी understand कर सके
   और execute कर सके बिना assumptions के

8. MAINTAINABILITY
   Regular update करो जब:
   - Requirements change हों
   - Feature change हो
   - Bugs fixed हों
   - New scenarios discovered हों

9. TESTABILITY
   क्या actually test करना possible है?
   ❌ Bad: "Performance should be good"
   ✅ Good: "Page should load in < 2 seconds"

10. TRACEABILITY
    हर test case एक requirement से mapped होना चाहिए
    "Requirement: User can login with email"
    "Test Case: TC_AUTH_001"
```

### 📊 Test Case Coverage

```
Coverage = (Test Cases Executed / Total Test Cases) × 100%

Good Coverage:
- Functional Coverage: 80-90%
- Critical Path: 100%
- Boundary Cases: 100%
- Overall: 70-80%

Example:
Total features: 10
Critical features: 3 (must test 100%)
Important features: 4 (must test 80%)
Nice-to-have: 3 (must test 50%)

Test cases:
Critical: 3 × 5 = 15
Important: 4 × 3 = 12
Nice-to-have: 3 × 2 = 6
Total: 33 test cases

Coverage = 33/50 = 66%
```

---

## <a name="interview"></a>Interview Questions

#### **Q1: अच्छा test case के qualities क्या हैं?**

```
Answer:
✓ Clear & Concise - आसानी से समझ आ जाए
✓ Specific - टेस्ट डेटा clearly दिया हो
✓ Testable - Actually execute करना possible हो
✓ Reproducible - कोई भी सामान्य execute कर सके
✓ Independent - एक test case दूसरे पर dependent न हो
✓ Complete - सभी prerequisite दिए हों
✓ Maintainable - Future में update करना आसान हो
```

#### **Q2: ECP और BVA में क्या फर्क है?**

```
Answer:
ECP (Equivalence Class Partitioning):
- Input को classes में divide करना
- एक class से एक test case
- Coverage बेहतर, efficiency बेहतर

BVA (Boundary Value Analysis):
- Boundaries पर values test करना
- Boundary पर bugs ज्यादा आते हैं
- More specific, bugs catch करने की क्षमता बेहतर

Together:
दोनों को साथ use करते हैं:
- ECP से equivalence classes identify करो
- BVA से boundaries identify करो
- Test करो
```

#### **Q3: Test Case कितने detailed होने चाहिए?**

```
Answer:
"Depends on audience:

Junior testers / New team members:
- Very detailed
- Step-by-step
- Expected results clearly written

Experienced testers / Smart team:
- Moderate detail
- High-level steps
- They can figure out details

Automation:
- Very detailed
- Clear inputs/outputs
- No ambiguity

Standard:
- Detailed enough कि कोई भी execute कर सके
- Simple enough कि redundant न हो
- Clear enough कि confusion न हो
"
```

---

## 🎯 Key Takeaways

```
✓ Test cases documentation का foundation हैं
✓ Clear structure होना बहुत महत्वपूर्ण है
✓ Design techniques से बेहतर coverage मिलता है
✓ ECP + BVA सबसे common combinations हैं
✓ Real-world scenarios को base करके लिखो
✓ Maintenance और reusability important हैं
```

---

## 📚 Next Steps

अब तुम जानते हो:
- ✓ Test cases कैसे लिखते हैं
- ✓ Design techniques का use
- ✓ Real-world examples
- ✓ Best practices

अगला: 📖 **05_Bug_Defect_Management** - Bugs को कैसे report और manage करते हैं!

---

*Created: 2026*  
*Level: Intermediate*  
*Language: Hinglish*
