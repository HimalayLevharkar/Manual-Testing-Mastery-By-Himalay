# 16_Banking_Domain_Testing

## Banking Applications को Professional तरीके से Test करना
### Complete Guide to Banking Domain Testing with Real-World Scenarios

---

## 📋 Table of Contents

1. [Banking Domain Overview](#overview)
2. [Banking Features to Test](#features)
3. [Security Requirements](#security)
4. [Compliance & Regulations](#compliance)
5. [Transaction Testing](#transactions)
6. [Real Banking Scenarios](#scenarios)
7. [Common Banking Bugs](#bugs)
8. [Test Cases Examples](#test-cases)
9. [Interview Questions](#interview)

---

## <a name="overview"></a>Banking Domain Overview

### 🏦 Banking Software क्यों Special है?

```
Banking Software बाकी applications से अलग है क्योंकि:

1. HIGH SECURITY REQUIRED 🔐
   - Financial data sensitive है
   - Fraud prevention जरूरी है
   - Encryption mandatory है

2. ZERO TOLERANCE FOR ERRORS ❌
   - ₹1 भी गलत हुआ तो issue है
   - Calculations 100% accurate होने चाहिए
   - No room for mistakes

3. REGULATORY COMPLIANCE 📋
   - RBI guidelines follow करनी हैं
   - KYC norms mandatory हैं
   - Audit trail रखना होता है

4. HIGH AVAILABILITY EXPECTED ⏰
   - 24/7 uptime चाहिए
   - Downtime = Customer trust loss
   - Performance critical है

5. COMPLEX INTEGRATIONS 🔗
   - Core Banking System
   - Payment Gateways
   - Third-party services (UPI, NEFT, IMPS)
   - ATM networks
   - Mobile banking
```

### 📊 Banking Application Types

```
1. CORE BANKING SYSTEM
   - Account management
   - Customer information
   - Transaction processing
   - Loan management
   - Interest calculation

2. INTERNET BANKING
   - Online account access
   - Fund transfers
   - Bill payments
   - Statement download
   - Service requests

3. MOBILE BANKING APP
   - All internet banking features
   - QR code payments
   - Mobile wallet integration
   - Biometric login
   - Push notifications

4. ATM SYSTEM
   - Cash withdrawal
   - Balance inquiry
   - Mini statement
   - PIN change
   - Card services

5. PAYMENT SYSTEMS
   - NEFT/RTGS/IMPS
   - UPI payments
   - Card payments (Debit/Credit)
   - Merchant payments
   - Recurring payments

6. LOAN MANAGEMENT
   - Loan application
   - Approval workflow
   - Disbursement
   - EMI calculation
   - Prepayment/Foreclosure
```

---

## <a name="features"></a>Banking Features to Test

### ✅ Critical Features Checklist

```
1. USER AUTHENTICATION
   □ Login with username/password
   □ MPIN login (mobile)
   □ Biometric login (fingerprint/face)
   □ OTP verification
   □ Two-factor authentication
   □ Password reset
   □ Security questions
   □ Account unlock after failed attempts

2. ACCOUNT SERVICES
   □ View account balance
   □ View transaction history
   □ Download account statement
   □ View available balance
   □ View held/lien amount
   □ Account summary
   □ Nominee details
   □ KYC status check

3. FUND TRANSFERS - DOMESTIC
   □ Add beneficiary (own bank)
   □ Add beneficiary (other bank)
   □ IMPS transfer (instant)
   □ NEFT transfer (batch processing)
   □ RTGS transfer (high value)
   □ UPI transfer
   □ Quick transfer (without adding beneficiary)
   □ Scheduled transfers
   □ Recurring transfers (standing instructions)
   □ Cancel/Modify scheduled transfer

4. FUND TRANSFERS - INTERNATIONAL
   □ Wire transfer
   □ Forex services
   □ SWIFT code validation
   □ IBAN validation
   □ Currency conversion
   □ Compliance checks

5. BILL PAYMENTS
   □ Electricity bill
   □ Water bill
   □ Gas bill
   □ Telephone/Mobile bill
   □ DTH recharge
   □ Insurance premium
   □ Mutual fund SIP
   □ Auto-pay setup
   □ Payment reminders

6. CARD SERVICES
   □ View card details
   □ Activate debit card
   □ Set/change PIN
   □ Block/unblock card
   □ Request new card
   □ Card limit management
   □ Transaction alerts
   □ International usage enable/disable
   □ Online transactions enable/disable
   □ Contactless payment enable/disable

7. INVESTMENT SERVICES
   □ Fixed Deposit (FD) booking
   □ Recurring Deposit (RD) booking
   □ View FD/RD details
   □ Premature withdrawal
   □ FD/RD renewal
   □ Mutual fund purchase
   □ Insurance purchase
   □ Demat account linkage

8. LOAN SERVICES
   □ Apply for loan
   □ Check loan eligibility
   □ Upload documents
   □ Track application status
   □ View loan details
   □ Download loan statement
   □ Make prepayment
   □ Request NOC
   □ Top-up loan application

9. CUSTOMER SERVICE
   □ Raise service request
   □ Track request status
   □ Update contact details
   □ Update address
   □ Stop payment (cheque)
   □ Cheque book request
   □ Passbook request
   □ Branch locator
   □ Contact center
   □ Chat support

10. NOTIFICATIONS & ALERTS
    □ Transaction alerts (SMS)
    □ Transaction alerts (Email)
    □ Push notifications
    □ Low balance alert
    □ Due date reminders
    □ OTP alerts
    □ Login alerts
    □ Password change alerts
```

---

## <a name="security"></a>Security Requirements

### 🔐 Banking Security Testing Checklist

```
1. AUTHENTICATION SECURITY
   □ Password complexity enforced
   □ Minimum 8 characters
   □ At least 1 uppercase, 1 lowercase
   □ At least 1 number, 1 special character
   □ Password history (can't reuse last 5)
   □ Password expiry (90 days)
   □ Account lockout (5 failed attempts)
   □ Auto-logout (5 minutes inactivity)
   □ Session timeout
   □ Concurrent session restriction

2. DATA ENCRYPTION
   □ HTTPS/SSL for all pages
   □ TLS 1.2 or higher
   □ Valid SSL certificate
   □ Data encrypted in transit
   □ Data encrypted at rest
   □ Password encrypted in database
   □ Sensitive data masked in logs
   □ Card number masked (XXXX-XXXX-XXXX-1234)

3. AUTHORIZATION
   □ Role-based access control
   □ User can access only own accounts
   □ Transaction limits enforced
   □ Approval workflow for high-value
   □ Maker-checker concept
   □ Admin functions restricted
   □ API access controlled

4. INPUT VALIDATION
   □ SQL injection protection
   □ XSS (Cross-site scripting) protection
   □ CSRF (Cross-site request forgery) protection
   □ Command injection protection
   □ Path traversal protection
   □ Session hijacking protection
   □ Man-in-the-middle protection

5. TRANSACTION SECURITY
   □ OTP for all transactions
   □ Transaction signing
   □ Beneficiary cooling period (4 hours)
   □ Daily transaction limits
   □ Per transaction limits
   □ Velocity checks (frequency)
   □ Duplicate transaction detection
   □ Fraud detection rules

6. AUDIT & LOGGING
   □ All transactions logged
   □ Login attempts logged
   □ Failed transactions logged
   □ Admin actions logged
   □ Data changes logged
   □ Logs tamper-proof
   □ Audit trail maintained
   □ Log retention (minimum 5 years)

7. MOBILE SECURITY
   □ App integrity check
   □ Rooted/jailbroken device detection
   □ Screenshot prevention
   □ App timeout
   □ Remote wipe capability
   □ Secure storage
   □ Code obfuscation

8. API SECURITY
   □ API authentication
   □ API rate limiting
   □ Input validation
   □ Output encoding
   □ Error handling (no info leakage)
   □ Version control
   □ Deprecation policy
```

### 🧪 Security Test Scenarios

```
SCENARIO 1: SQL Injection Testing

Test Input in login field:
' OR '1'='1

Expected Result:
- Login should fail
- Error message should NOT reveal database structure
- Query should be sanitized
- Alert should be logged

SCENARIO 2: XSS Testing

Test Input in beneficiary name:
<script>alert('XSS')</script>

Expected Result:
- Script should not execute
- Input should be sanitized
- Special characters escaped
- Stored as plain text

SCENARIO 3: Session Hijacking

Steps:
1. Login to application
2. Copy session cookie
3. Try to use in different browser
4. Try to use after logout

Expected Result:
- Session should be tied to browser fingerprint
- Session should invalidate on logout
- Session timeout should work
- Concurrent sessions should be restricted

SCENARIO 4: Man-in-the-Middle

Steps:
1. Use proxy tool (Burp Suite)
2. Intercept transaction request
3. Try to modify amount
4. Try to modify beneficiary

Expected Result:
- Request should be signed
- Modification should be detected
- Transaction should fail
- Alert should be generated

SCENARIO 5: Brute Force Attack

Steps:
1. Try 5 wrong passwords
2. Try 6th attempt

Expected Result:
- Account should be locked
- OTP/email verification required to unlock
- Alert sent to customer
- Attempt logged
```

---

## <a name="compliance"></a>Compliance & Regulations

### 📋 RBI Guidelines to Test

```
1. KYC (Know Your Customer) COMPLIANCE
   □ Aadhaar verification
   □ PAN verification
   □ Address proof validation
   □ Photo verification
   □ Video KYC option
   □ e-KYC integration
   □ KYC expiry tracking
   □ Re-KYC reminders

2. AML (Anti-Money Laundering) CHECKS
   □ Large transaction monitoring (>₹10 lakh)
   □ Suspicious transaction detection
   □ Cash transaction reporting
   □ Beneficiary name screening
   □ Sanctions list check
   □ PEP (Politically Exposed Person) check
   □ STR (Suspicious Transaction Report) generation

3. CASH TRANSACTION LIMITS
   □ Cash deposit limit (₹50,000 PAN required)
   □ Cash withdrawal limit
   □ Daily cash limit
   □ Monthly cash limit
   □ Threshold alerts

4. TRANSACTION REPORTING
   □ CTR (Cash Transaction Report)
   □ STR (Suspicious Transaction Report)
   □ TTR (Trade Transaction Report)
   □ Automated reporting to FIU-IND
   □ Report within prescribed timeline

5. DATA LOCALIZATION
   □ Customer data stored in India
   □ Transaction data in India
   □ Backup within India
   □ Cross-border transfer restrictions

6. CUSTOMER PROTECTION
   □ Grievance redressal mechanism
   □ Ombudsman details displayed
   □ Complaint tracking
   □ Resolution timeline (30 days)
   □ Compensation policy

7. DIGITAL LENDING GUIDELINES
   □ Key Fact Statement (KFS) display
   □ All-inclusive cost disclosure
   □ Cooling-off period
   □ Grace period mentioned
   □ Recovery practices compliant

8. UPI COMPLIANCE
   □ NPCI guidelines followed
   □ Transaction limits (₹1 lakh/day)
   □ UPI PIN security
   □ VPA validation
   □ Transaction timeout handling
```

### 📊 Compliance Test Cases

```
TEST CASE 1: PAN Validation for Large Deposits

Precondition: Customer making cash deposit
Test Steps:
1. Navigate to cash deposit screen
2. Enter amount: ₹51,000
3. Proceed without PAN
Expected Result:
- System should prompt for PAN
- Transaction should not proceed without PAN
- As per RBI guidelines

TEST CASE 2: Daily Transaction Limit Check

Precondition: Customer with ₹1 lakh daily limit
Test Steps:
1. Transfer ₹60,000 via NEFT (9:00 AM)
2. Transfer ₹50,000 via IMPS (10:00 AM)
3. Try to transfer ₹10,000 (11:00 AM)
Expected Result:
- First two transactions successful
- Third transaction should fail with limit exceeded message
- Available limit should be displayed

TEST CASE 3: Beneficiary Cooling Period

Test Steps:
1. Add new beneficiary
2. Immediately try to transfer money
3. Wait 4 hours, try again
Expected Result:
- Immediate transfer should be blocked
- Message: "Beneficiary added. Can transfer after 4 hours"
- After 4 hours, transfer should be allowed

TEST CASE 4: Account Lockout After Failed Attempts

Test Steps:
1. Enter wrong password 5 times
2. Try 6th login
Expected Result:
- After 5 attempts, account locked
- Message: "Account locked. Reset password or wait 24 hours"
- OTP sent to registered mobile for unlock
- Attempt logged in security audit

TEST CASE 5: Suspicious Transaction Detection

Test Steps:
1. Customer normally transfers ₹10,000-50,000
2. Suddenly transfer ₹9,50,000 (just below reporting limit)
3. Multiple small transfers in quick succession
Expected Result:
- Large transaction flagged
- Pattern detected (structuring/smurfing)
- STR generated automatically
- Compliance team alerted
```

---

## <a name="transactions"></a>Transaction Testing

### 💰 Transaction Testing Deep Dive

```
TRANSACTION TYPES TO TEST:

1. IMPS (Immediate Payment Service)
   - 24x7 availability
   - Instant transfer
   - Limit: ₹5 lakh per transaction
   - Requires: MMID + Mobile No. OR Account No. + IFSC
   - Charge: ₹5-25 depending on amount

2. NEFT (National Electronic Funds Transfer)
   - Batch processing (every 30 minutes)
   - Operating hours: 24x7 (since Dec 2019)
   - No minimum/maximum limit
   - Settlement in batches
   - Charge: ₹2.5-25 depending on amount

3. RTGS (Real Time Gross Settlement)
   - Real-time settlement
   - Minimum: ₹2 lakh
   - No maximum limit
   - Operating hours: 24x7
   - Charge: ₹25-50 depending on amount

4. UPI (Unified Payments Interface)
   - Instant transfer
   - Limit: ₹1 lakh per day (varies by bank)
   - Requires: VPA (Virtual Payment Address)
   - 24x7 availability
   - Free for customers
```

### 🔄 Transaction Flow Testing

```
COMPLETE FUND TRANSFER FLOW:

┌─────────────────┐
│ 1. LOGIN        │
│    - Authenticate user
│    - Validate credentials
│    - Generate session
└────────┬────────┘
         ↓
┌─────────────────┐
│ 2. SELECT       │
│    TRANSFER TYPE│
│    - IMPS/NEFT/RTGS/UPI
│    - Validate limits
└────────┬────────┘
         ↓
┌─────────────────┐
│ 3. BENEFICIARY  │
│    SELECTION    │
│    - Validate beneficiary exists
│    - Check cooling period
│    - Verify status (active/blocked)
└────────┬────────┘
         ↓
┌─────────────────┐
│ 4. ENTER AMOUNT │
│    - Validate min/max
│    - Check available balance
│    - Calculate charges
│    - Show total debit
└────────┬────────┘
         ↓
┌─────────────────┐
│ 5. REVIEW       │
│    - Show all details
│    - Beneficiary name
│    - Amount + charges
│    - Transaction type
└────────┬────────┘
         ↓
┌─────────────────┐
│ 6. AUTHENTICATE │
│    - Generate OTP
│    - Send to registered mobile
│    - Validate OTP
│    - Check transaction PIN
└────────┬────────┘
         ↓
┌─────────────────┐
│ 7. PROCESS      │
│    TRANSACTION  │
│    - Debit sender account
│    - Credit beneficiary account
│    - Generate transaction ID
│    - Update ledger
└────────┬────────┘
         ↓
┌─────────────────┐
│ 8. CONFIRMATION │
│    - Show success/failure
│    - Display transaction ID
│    - Send SMS/Email
│    - Update passbook
└─────────────────┘
```

### ⚠️ Transaction Edge Cases

```
EDGE CASES TO TEST:

1. BALANCE EDGE CASES
   □ Exact balance transfer (balance becomes 0)
   □ Balance - ₹1 (should fail)
   □ Balance + ₹1 transfer (should fail)
   □ Pending debits considered?
   □ Held amount excluded?

2. TIMING EDGE CASES
   □ Transaction at 23:59:59 (day change)
   □ Transaction during batch processing
   □ Transaction during system maintenance
   □ Transaction during holiday
   □ Transaction in different timezone

3. AMOUNT EDGE CASES
   □ ₹0.01 (minimum possible)
   □ ₹0 (should fail)
   □ Negative amount (should fail)
   □ Very large amount (₹99,99,99,999)
   □ Amount with decimals (₹100.50)
   □ Round figure (₹10,000)

4. CONCURRENT TRANSACTIONS
   □ Two transfers at same time
   □ Transfer while EMI auto-debit processing
   □ Transfer while interest credited
   □ Transfer from joint account (other holder also transacting)

5. NETWORK FAILURE SCENARIOS
   □ OTP not received
   □ OTP entered wrong 3 times
   □ Network timeout during transaction
   □ Power failure mid-transaction
   □ App crash during confirmation

6. DUPLICATE TRANSACTIONS
   □ Click submit button multiple times
   □ Browser back button after transaction
   □ Refresh page after transaction
   □ Retry failed transaction immediately
```

---

## <a name="scenarios"></a>Real Banking Scenarios

### 💼 Scenario 1: Salary Credit + Auto Debits

```
SCENARIO:
Customer's salary credited on 1st of month.
Multiple auto-debits scheduled on same day.

TEST FLOW:
1. Salary of ₹1,00,000 credited (1st, 9:00 AM)
2. Home Loan EMI: ₹35,000 (auto-debit, 1st, 10:00 AM)
3. Car Loan EMI: ₹15,000 (auto-debit, 1st, 10:00 AM)
4. Mutual Fund SIP: ₹10,000 (1st, 10:00 AM)
5. Insurance Premium: ₹5,000 (1st, 10:00 AM)
6. Customer manually transfers: ₹20,000 (1st, 9:30 AM)

EXPECTED BEHAVIOR:
- All auto-debits should process in priority order
- Sufficient balance should be maintained
- If insufficient, some should fail gracefully
- Customer should receive alerts for each
- No overdraft unless facility exists

BUG TO CATCH:
If auto-debits process before salary credit:
- All auto-debits fail (insufficient balance)
- Customer penalized for no-fault
- This happened in real bank!

FIX:
Implement debit priority and timing logic.
```

### 💼 Scenario 2: FD Premature Withdrawal

```
SCENARIO:
Customer wants to break FD before maturity.

TEST FLOW:
1. FD Details:
   - Principal: ₹5,00,000
   - Rate: 7% per annum
   - Tenure: 5 years
   - Booked: 01-Jan-2024
   - Maturity: 01-Jan-2029
   
2. Premature Withdrawal: 01-Jul-2025 (1.5 years)
   - Applicable rate: 5% (for 1-2 year slab)
   - Penalty: 1% deduction

3. Calculation:
   Principal: ₹5,00,000
   Interest @ 5% for 1.5 years: ₹37,500
   Penalty (1% of principal): ₹5,000
   Net Interest: ₹32,500
   Total Payable: ₹5,32,500

TEST CASES:
□ Interest calculation correct?
□ Penalty applied correctly?
□ TDS deducted (if applicable)?
□ Amount credited to linked account?
□ FD status updated to "Closed"?
□ Advice/statement generated?
□ Core banking system updated?
```

### 💼 Scenario 3: Failed UPI Transaction - Money Reversal

```
SCENARIO:
Customer's money debited but UPI transaction failed.

TEST FLOW:
1. Customer initiates UPI payment: ₹5,000
2. Money debited from account
3. Beneficiary doesn't receive money
4. Transaction shows "Failed" status
5. Customer calls support

EXPECTED REVERSAL PROCESS:
Day 0: Transaction failed
Day 0-1: System auto-investigates
Day 1-3: Money reversed automatically
Day 3: If not reversed, manual intervention
Day 5: Escalation to nodal officer
Day 7: Compensation if delay (₹100/day)

TEST CASES:
□ Auto-reversal triggered?
□ Reversal within T+1 day?
□ Customer notified?
□ Transaction status updated?
□ Complaint logged?
□ Compensation calculated (if delay)?
□ Root cause identified?

REAL BUG:
One bank's UPI reversal took 15 days.
RBI imposed penalty of ₹1 crore.
```

### 💼 Scenario 4: Joint Account - Either or Survivor

```
SCENARIO:
Joint account with "Either or Survivor" mandate.
Two holders: Mr. Sharma and Mrs. Sharma.

TEST CASES:
□ Mr. Sharma can login and view account? ✓
□ Mrs. Sharma can login and view account? ✓
□ Mr. Sharma can transfer funds? ✓
□ Mrs. Sharma can transfer funds? ✓
□ Both can transfer simultaneously? (Should handle)
□ If Mr. Sharma blocks card, Mrs. Sharma's card also blocked? (Should NOT)
□ If Mr. Sharma changes mobile, Mrs. Sharma's OTP affected? (Should NOT)
□ If one holder dies, other can operate? ✓
□ Both signatures needed for cheque above limit? (As per mandate)

EDGE CASE:
If mandate is "Former or Survivor":
- Only FIRST holder can operate
- Second holder can only operate after first's death
- This should be enforced in internet banking
```

### 💼 Scenario 5: Home Loan Prepayment

```
SCENARIO:
Customer wants to prepay home loan partially.

LOAN DETAILS:
- Principal Outstanding: ₹50,00,000
- Interest Rate: 8.5% per annum
- Remaining Tenure: 18 years
- EMI: ₹45,000 per month

PREPAYMENT: ₹10,00,000

OPTIONS TO TEST:
Option 1: Reduce EMI
- New Principal: ₹40,00,000
- Tenure: Same (18 years)
- New EMI: ~₹36,000 (reduced)

Option 2: Reduce Tenure
- New Principal: ₹40,00,000
- EMI: Same (₹45,000)
- New Tenure: ~11 years (reduced)

TEST CASES:
□ Prepayment amount within limits? (min/max)
□ Prepayment charges calculated? (0% for floating rate)
□ Interest recalculated correctly?
□ Amortization schedule updated?
□ New EMI/Tenure reflected?
□ Confirmation generated?
□ Core system updated?
□ Next EMI date unchanged?
```

---

## <a name="bugs"></a>Common Banking Bugs

### 🐛 Real Banking Bugs Found in Production

```
BUG 1: Interest Calculation Error (CRITICAL)

Description:
FD interest calculated with wrong formula for leap year.

Impact:
- 50,000+ customers affected
- Bank paid ₹2 crore extra interest
- Reputation damage

Root Cause:
Formula used 365 days instead of 366 for leap year.
Interest = (P × R × T) / 100
Where T = days/365 (should be days/366 for leap year)

How to Test:
□ Test FD interest for period crossing Feb 29
□ Test RD interest for leap year
□ Verify formula in code
□ Compare with manual calculation
□ Test for 10+ different tenures

BUG 2: Duplicate Transaction Processing (CRITICAL)

Description:
Customer clicked "Submit" twice, money debited twice.

Impact:
- Customer account debited double
- Liquidity issue for customer
- Bank had to reverse urgently

Root Cause:
- No duplicate transaction check
- Button not disabled after first click
- Session not invalidated

How to Test:
□ Click submit button multiple times rapidly
□ Check for duplicate transaction ID
□ Verify idempotency of API
□ Test with slow network (button clicked before response)
□ Browser back/refresh after transaction

BUG 3: Beneficiary Name Not Validated (HIGH)

Description:
Money transferred to wrong account due to similar name.

Scenario:
Customer added beneficiary: "Rajesh Kumar"
System suggested: "Rajesh Kumar - Account XXXX"
Customer selected, transferred ₹5 lakh
Actual beneficiary was different "Rajesh Kumar"

Root Cause:
- Name matching algorithm too loose
- No account number confirmation
- No IFSC validation

How to Test:
□ Add beneficiary with common name
□ Verify account number displayed clearly
□ Verify IFSC branch details shown
□ Confirm name matches account exactly
□ Test with similar names

BUG 4: Balance Not Updated After Transfer (HIGH)

Description:
Money transferred but available balance not updated.

Impact:
- Customer saw old balance
- Customer initiated another transfer
- Second transfer failed (but customer already sent money)

Root Cause:
- Cache not invalidated after transaction
- Balance API returning cached value

How to Test:
□ Transfer money, immediately check balance
□ Refresh balance manually
□ Check balance from different screen
□ Check balance after logout-login
□ Verify passbook shows updated balance

BUG 5: OTP Bypass Vulnerability (CRITICAL)

Description:
OTP could be bypassed by manipulating request.

Impact:
- Unauthorized transactions possible
- Security breach
- Regulatory penalty

Root Cause:
- OTP validation was client-side only
- Server didn't validate OTP properly
- Request could be modified

How to Test:
□ Try transaction without OTP
□ Try with wrong OTP (should fail)
□ Try with expired OTP
□ Intercept request, modify OTP field
□ Check server-side validation

BUG 6: EMI Calculation Rounding Error (MEDIUM)

Description:
EMI calculation had ₹1-2 rounding error per month.

Impact:
- Over 20 years, error accumulated to ₹500+
- Customer complaints
- Manual adjustment needed

Root Cause:
- Rounding at each step instead of final
- Floating point precision issue

How to Test:
□ Calculate EMI for long tenure (20-30 years)
□ Verify total interest over tenure
□ Compare with manual calculation
□ Check rounding at each step
□ Test for different rates and tenures

BUG 7: Statement Download - Wrong Balance (MEDIUM)

Description:
Downloaded statement showed wrong closing balance.

Impact:
- Customer confused
- Support calls increased
- Trust issue

Root Cause:
- Statement query didn't consider pending transactions
- Balance calculated at statement date, not end of day

How to Test:
□ Download statement for current month
□ Verify opening balance matches last closing
□ Verify closing balance matches current
□ Check transactions in date range
□ Compare with passbook

BUG 8: Mobile App - Screen Overlay Attack (CRITICAL)

Description:
Malicious app could overlay banking app and capture credentials.

Impact:
- Credential theft
- Fraudulent transactions
- Security breach

Root Cause:
- App didn't prevent overlay
- No secure flag set

How to Test:
□ Install overlay app, try to access banking app
□ Check if app detects overlay
□ Verify secure flag in Android
□ Test screenshot prevention
□ Check app integrity
```

---

## <a name="test-cases"></a>Test Cases Examples

### 📝 Fund Transfer Test Cases

```
TEST CASE ID: TC_BANK_FT_001
Title: Successful IMPS Transfer to Existing Beneficiary

Preconditions:
- User logged in to internet banking
- Beneficiary already added and cooling period over
- Sufficient balance available

Test Steps:
1. Navigate to Fund Transfer → IMPS
2. Select beneficiary: "John Doe - HDFC - XXXX1234"
3. Enter amount: ₹10,000
4. Click "Proceed"
5. Review details (beneficiary, amount, charges)
6. Enter transaction password
7. Enter OTP received on registered mobile
8. Click "Confirm"

Expected Result:
- Transaction successful
- ₹10,000 + charges debited from sender account
- ₹10,000 credited to beneficiary account
- Transaction ID generated
- SMS sent to both sender and beneficiary
- Entry in transaction history
- Available balance updated

Test Data:
- Beneficiary: John Doe, HDFC Bank, A/c 1234567890, IFSC HDFC0001234
- Amount: ₹10,000
- Charges: ₹5 (IMPS)
- Total Debit: ₹10,005

Status: [To be filled]

─────────────────────────────────────────────────

TEST CASE ID: TC_BANK_FT_002
Title: NEFT Transfer - Insufficient Balance

Preconditions:
- User logged in
- Beneficiary added
- Account balance: ₹5,000

Test Steps:
1. Navigate to Fund Transfer → NEFT
2. Select beneficiary
3. Enter amount: ₹10,000
4. Click "Proceed"

Expected Result:
- Error message: "Insufficient balance"
- Transaction not processed
- No charges deducted
- Error logged

Status: [To be filled]

─────────────────────────────────────────────────

TEST CASE ID: TC_BANK_FT_003
Title: Add New Beneficiary - Cooling Period Validation

Preconditions:
- User logged in
- No existing beneficiary

Test Steps:
1. Navigate to Fund Transfer → Add Beneficiary
2. Enter beneficiary details:
   - Name: Test User
   - Account No: 9876543210
   - IFSC: SBIN0001234
   - Nickname: Test
3. Click "Add Beneficiary"
4. Enter OTP
5. Beneficiary added successfully
6. Immediately try to transfer money to this beneficiary

Expected Result:
- Beneficiary added successfully
- Transfer attempt blocked
- Message: "Beneficiary added. Can transfer after 4 hours"
- After 4 hours, transfer should be allowed

Status: [To be filled]

─────────────────────────────────────────────────

TEST CASE ID: TC_BANK_FT_004
Title: RTGS Transfer - Minimum Amount Validation

Preconditions:
- User logged in
- Sufficient balance (₹5,00,000)

Test Steps:
1. Navigate to Fund Transfer → RTGS
2. Select beneficiary
3. Enter amount: ₹1,50,000 (below minimum)
4. Click "Proceed"

Expected Result:
- Error message: "Minimum amount for RTGS is ₹2,00,000"
- Transaction not processed
- Suggestion to use NEFT/IMPS

Status: [To be filled]

─────────────────────────────────────────────────

TEST CASE ID: TC_BANK_FT_005
Title: Scheduled Transfer - Future Date

Preconditions:
- User logged in
- Beneficiary added
- Sufficient balance

Test Steps:
1. Navigate to Fund Transfer → NEFT
2. Select beneficiary
3. Enter amount: ₹25,000
4. Select "Schedule Transfer"
5. Select date: 7 days from today
6. Confirm scheduling
7. Check scheduled transfers list
8. Cancel scheduled transfer

Expected Result:
- Transfer scheduled successfully
- Entry in "Scheduled Transfers"
- Amount not debited immediately
- On scheduled date, auto-debit happens
- Cancel successful, no debit on scheduled date

Status: [To be filled]
```

### 📝 Account Services Test Cases

```
TEST CASE ID: TC_BANK_ACC_001
Title: View Account Balance - Multiple Accounts

Preconditions:
- User has multiple accounts (Savings, Current, FD)
- User logged in

Test Steps:
1. Login to internet banking
2. View dashboard
3. Check balance displayed for each account
4. Click on Savings account
5. View detailed balance
6. Check available vs ledger balance

Expected Result:
- All accounts displayed
- Savings balance correct
- Current balance correct
- FD principal displayed
- Available balance = Ledger balance - Holds
- Last transaction date shown

Status: [To be filled]

─────────────────────────────────────────────────

TEST CASE ID: TC_BANK_ACC_002
Title: Download Account Statement - Custom Date Range

Preconditions:
- User logged in
- Transactions exist in account

Test Steps:
1. Navigate to Accounts → Statement
2. Select account: Savings
3. Select date range: 01-Jan-2026 to 31-Jan-2026
4. Select format: PDF
5. Click "Download"
6. Open downloaded PDF

Expected Result:
- Statement downloaded successfully
- Opening balance (as on 01-Jan) correct
- All January transactions listed
- Closing balance (as on 31-Jan) correct
- PDF password protected
- Bank logo and details present
- Transaction details complete (date, description, debit, credit, balance)

Status: [To be filled]

─────────────────────────────────────────────────

TEST CASE ID: TC_BANK_ACC_003
Title: Block Debit Card - Immediate Effect

Preconditions:
- User has active debit card
- User logged in

Test Steps:
1. Navigate to Cards → Debit Card Services
2. Select card to block
3. Select reason: "Lost/Stolen"
4. Confirm blocking
5. Try to use card (simulated)

Expected Result:
- Card blocked immediately
- Status updated to "Blocked"
- SMS sent to registered mobile
- Card cannot be used for transactions
- ATM transactions declined
- Online transactions declined
- Entry in service request history

Status: [To be filled]
```

### 📝 Security Test Cases

```
TEST CASE ID: TC_BANK_SEC_001
Title: Account Lockout After Failed Login Attempts

Preconditions:
- Valid user account
- Know wrong password

Test Steps:
1. Go to login page
2. Enter valid username
3. Enter wrong password
4. Repeat 5 times
5. Try 6th attempt with correct password

Expected Result:
- After 5 failed attempts, account locked
- 6th attempt with correct password also fails
- Message: "Account locked due to multiple failed attempts"
- OTP sent to registered mobile for unlock
- Entry in security audit log
- Alert sent to customer

Status: [To be filled]

─────────────────────────────────────────────────

TEST CASE ID: TC_BANK_SEC_002
Title: Session Timeout After Inactivity

Preconditions:
- User logged in

Test Steps:
1. Login successfully
2. Leave idle for 5 minutes
3. Try to click any menu
4. Try to initiate transaction

Expected Result:
- Session timed out after 5 minutes
- Redirected to login page
- Message: "Session timed out due to inactivity"
- Any unsaved data lost (warning should be given before timeout)

Status: [To be filled]

─────────────────────────────────────────────────

TEST CASE ID: TC_BANK_SEC_003
Title: Password Complexity Validation

Preconditions:
- User wants to change password

Test Steps:
1. Navigate to Profile → Change Password
2. Try passwords:
   a) "test123" (too short)
   b) "TestPassword" (no number/special char)
   c) "test123456" (no uppercase/special)
   d) "Test@123" (valid)
   e) "Test@123" (same as current - should fail)

Expected Result:
- a, b, c should fail with appropriate messages
- d should be accepted
- e should fail (password history check)
- Rules displayed clearly

Status: [To be filled]
```

---

## <a name="interview"></a>Interview Questions

### 💼 Banking Domain Interview Questions

#### **Q1: Banking domain testing में क्या-क्या test करते हो?**

```
ANSWER:
"Banking domain में main focus areas:

1. FUND TRANSFERS
   - IMPS, NEFT, RTGS, UPI
   - Beneficiary management
   - Transaction limits
   - Cooling period

2. ACCOUNT SERVICES
   - Balance inquiry
   - Statement download
   - Passbook update
   - Cheque services

3. CARD SERVICES
   - Debit/Credit card operations
   - PIN setting
   - Block/unblock
   - Limit management

4. LOAN SERVICES
   - Loan application
   - EMI calculation
   - Prepayment
   - Statement

5. SECURITY
   - Authentication
   - Authorization
   - Encryption
   - Audit logging

6. COMPLIANCE
   - KYC verification
   - AML checks
   - RBI guidelines
   - Reporting"
```

#### **Q2: FD interest calculation कैसे test करते हो?**

```
ANSWER:
"FD interest test करने के लिए:

1. VERIFY FORMULA
   Simple Interest: (P × R × T) / 100
   Compound Interest: P(1 + R/n)^nt - P

2. TEST CASES
   □ Different tenures (7 days to 10 years)
   □ Different rates (based on amount and tenure)
   □ Senior citizen rate (extra 0.5%)
   □ Premature withdrawal (penalty applicable)
   □ Leap year calculation
   □ Tax deduction (TDS)

3. MANUAL CALCULATION
   Excel में calculate करो
   Bank के calculation से compare करो

4. EDGE CASES
   □ Month end booking
   □ Quarter end interest credit
   □ Holiday maturity
   □ Auto-renewal"
```

#### **Q3: Transaction failure के बाद money reversal कैसे test करते हो?**

```
ANSWER:
"Money reversal testing:

1. AUTO-REVERSAL TEST
   □ Failed transaction immediately reversed?
   □ T+1 day में reversal?
   □ Reversal SMS/email sent?

2. STATUS CHECK
   □ Transaction status updated to 'Failed'?
   □ Balance updated correctly?
   ✓ Debit reversed?

3. SCENARIOS
   □ Timeout failure
   □ Beneficiary bank down
   □ Invalid account
   □ Network failure
   □ Insufficient balance (after hold)

4. VERIFICATION
   □ Passbook entry
   □ Statement reflection
   □ Available balance
   □ Complaint auto-logged"
```

#### **Q4: Banking app में security testing कैसे करते हो?**

```
ANSWER:
"Security testing approach:

1. AUTHENTICATION
   □ Password complexity
   □ Account lockout
   □ Session timeout
   □ Two-factor auth
   □ Biometric login

2. AUTHORIZATION
   □ User can access only own accounts
   □ Transaction limits
   □ Role-based access

3. DATA PROTECTION
   □ HTTPS everywhere
   □ Data encryption
   □ Password masking
   □ Card number masking

4. VULNERABILITY TESTING
   □ SQL injection
   □ XSS
   □ CSRF
   □ Session hijacking
   □ Man-in-the-middle

5. COMPLIANCE
   □ RBI guidelines
   □ Data localization
   □ Audit logging
   □ Privacy policy"
```

#### **Q5: UPI payment failure के common reasons क्या हैं?**

```
ANSWER:
"Common UPI failure reasons:

1. TECHNICAL
   □ Network timeout
   □ Bank server down
   □ NPCI server issue
   □ App crash

2. VALIDATION
   □ Wrong VPA
   □ Invalid PIN
   □ Expired PIN
   □ Account not linked

3. LIMITS
   □ Daily limit exceeded
   □ Per transaction limit
   □ Insufficient balance
   □ Bank-specific limits

4. BENEFICIARY
   □ VPA not registered
   □ Bank not UPI-enabled
   □ Account inactive

5. SECURITY
   □ Suspicious transaction
   □ Fraud alert
   □ Account blocked
   □ Device change

TESTING APPROACH:
हर failure type के लिए reversal test करो,
proper error message verify करो,
और retry mechanism test करो।"
```

#### **Q6: EMI calculation कैसे test करते हो?**

```
ANSWER:
"EMI calculation testing:

1. FORMULA VERIFICATION
   EMI = [P × R × (1+R)^N] / [(1+R)^N-1]
   
   Where:
   P = Principal
   R = Monthly interest rate (Annual/12/100)
   N = Tenure in months

2. TEST CASES
   □ Different loan amounts
   □ Different interest rates
   □ Different tenures (1 year to 30 years)
   □ Fixed vs floating rate
   □ Prepayment impact
   □ Part-payment impact

3. COMPONENTS
   □ Principal component
   □ Interest component
   □ Total EMI
   □ Total interest over tenure
   □ Amortization schedule

4. EDGE CASES
   □ Leap year interest
   □ Month with 31 days
   □ Holiday EMI debit
   □ Rate change (floating)

5. COMPARISON
   Excel में EMI function use करो
   Bank calculation से match करो"
```

#### **Q7: Banking domain में priority कैसे decide करते हो bugs की?**

```
ANSWER:
"Bug priority in banking:

CRITICAL (Fix immediately):
□ Money calculation wrong
□ Security vulnerability
□ Data loss/corruption
□ Transaction duplicate
□ Unauthorized access possible

HIGH (Fix within 24 hours):
□ Transaction failure without reversal
□ Balance not updating
□ Statement wrong
□ Card blocking not working
□ OTP not sending

MEDIUM (Fix within 1 week):
□ UI issues in transaction flow
□ Slow performance
□ Error messages unclear
□ Download failing occasionally

LOW (Fix in next release):
□ Cosmetic issues
□ Spelling mistakes
□ Alignment issues
□ Non-critical enhancements

DECISION FACTORS:
□ Customer impact
□ Financial impact
□ Number of users affected
□ Regulatory implication
□ Reputation risk"
```

---

## 🎯 Key Takeaways

```
✓ Banking testing requires domain knowledge
✓ Security is top priority
✓ Calculations must be 100% accurate
✓ Compliance testing mandatory
✓ Transaction reversal testing critical
✓ Real-world scenarios practice करो
✓ RBI guidelines follow करो
```

---

## 📚 Next Steps

अब तुम जानते हो:
- ✓ Banking features और unको test कैसे करना है
- ✓ Security requirements
- ✓ Compliance testing
- ✓ Transaction testing
- ✓ Real bugs और scenarios

अगला: 📖 **17_Ecommerce_Domain_Testing** - E-commerce applications को test करना!

---

*Created: 2026*  
*Level: Advanced*  
*Language: Hinglish*  
*Domain: Banking & Financial Services*
