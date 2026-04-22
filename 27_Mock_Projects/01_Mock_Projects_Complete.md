# Module 27: Mock Projects - Hands-On Practice

## वास्तविक परियोजनाओं जैसे व्यावहारिक अभ्यास

---

## 📋 Table of Contents

1. [Mock Project 1: E-Commerce App](#ecommerce)
2. [Mock Project 2: Banking App](#banking)
3. [Mock Project 3: Social Media App](#social-media)
4. [Testing Approach Guide](#testing-guide)
5. [Best Practices](#best-practices)

---

## Mock Project 1: E-Commerce Application

### Project Overview

```
Application: Online Shopping Platform
Type: Web-based e-commerce
Users: Customers, Admin, Sellers
Tech Stack: Java backend, React frontend, PostgreSQL
Current Phase: UAT (User Acceptance Testing)
Timeline: 3 weeks for complete testing
```

### Features to Test

#### **User Management**
```
☐ User Registration
  • Email validation
  • Password strength
  • Terms acceptance
  • Account creation

☐ User Login
  • Valid credentials
  • Invalid password
  • Non-existent user
  • Account locked after failed attempts
  • Remember me functionality

☐ User Profile
  • Update profile information
  • Change password
  • Add/manage addresses
  • Payment methods
  • Order history
```

#### **Product Features**
```
☐ Product Browsing
  • View product listing
  • Filter by category
  • Filter by price range
  • Search functionality
  • Sort by rating/price
  • Pagination

☐ Product Details
  • Display images
  • Show description
  • Display rating/reviews
  • Stock availability
  • Specifications
  • Add to cart
```

#### **Shopping Cart**
```
☐ Cart Management
  • Add item to cart
  • Remove item
  • Modify quantity
  • Apply coupon
  • Calculate total
  • Save cart (for later)
  • Clear cart
```

#### **Checkout & Payment**
```
☐ Checkout Process
  • Select shipping address
  • Select shipping method
  • Select payment method
  • Apply discount
  • Review order
  • Place order

☐ Payment Processing
  • Credit card payment
  • Debit card payment
  • Wallet payment
  • UPI payment
  • Payment success/failure handling
  • Invoice generation
```

#### **Order Management**
```
☐ Order Tracking
  • View order status
  • Track shipment
  • Estimated delivery
  • Seller information
  • Return/cancel order
  • Download invoice
```

### Test Scenarios

#### **Happy Path Scenarios**

```
Scenario 1: New User Purchase
1. Register new account
2. Browse products
3. Add item to cart
4. Apply valid coupon
5. Checkout
6. Process payment
7. Receive confirmation
Expected: Order successfully placed

Scenario 2: Returning User Repurchase
1. Login with existing account
2. Search for product
3. Add to cart
4. Use saved address
5. Use saved payment method
6. Place order
Expected: Quick checkout, order placed

Scenario 3: Cart Save & Later Purchase
1. Add items to cart
2. Save cart without checkout
3. Logout
4. Login next day
5. Cart items restored
6. Proceed with checkout
Expected: Cart persisted correctly
```

#### **Negative Scenarios**

```
Scenario 1: Invalid Payment
1. Add item to cart
2. Proceed to checkout
3. Enter invalid card details
4. Process payment
Expected: Payment rejected, error message shown

Scenario 2: Out of Stock Item
1. Add out-of-stock item to cart
2. Proceed to checkout
3. Try to place order
Expected: Error message, order not placed

Scenario 3: Expired Coupon
1. Add items to cart
2. Apply expired coupon
3. Try to proceed
Expected: Coupon rejected, normal price calculated
```

#### **Boundary Scenarios**

```
Scenario 1: Cart Limit
1. Add 100 items (max limit)
2. Try to add 101st item
Expected: Limit reached message

Scenario 2: Price Range Filter
1. Set min: ₹0, max: ₹999,999
2. Verify results
3. Set min: ₹100,000, max: ₹50,000 (invalid)
Expected: Invalid range error

Scenario 3: Coupon Discount
1. Apply coupon with 50% discount
2. Verify discount calculation
3. Cart total should be 50% of original
Expected: Correct calculation
```

### Test Cases to Write

```
Write at least 50 test cases covering:
- User registration (8 cases)
- User login (8 cases)
- Product browsing (10 cases)
- Shopping cart (10 cases)
- Checkout (10 cases)
- Payment processing (15 cases)

Requirements:
- Clear title
- Preconditions
- Step-by-step actions
- Expected results
- Test data
```

### Test Data Required

```
Users:
- Admin user (credentials)
- Test customer 1 (basic)
- Test customer 2 (premium)
- Test customer 3 (inactive)

Products:
- In-stock products (various prices)
- Out-of-stock products
- Low quantity products
- Featured products

Payment Data:
- Valid credit cards (test)
- Invalid cards
- Expired cards

Coupons:
- Valid coupons (various discounts)
- Expired coupons
- Used coupons
- Invalid codes

Addresses:
- Delivery addresses (various regions)
- Valid postal codes
- Invalid addresses
```

### Bug Report Examples

```
Bug 1: Cart quantity limit not enforced
- Summary: User can add more than max quantity
- Steps: Add item, increase qty to 1000, click update
- Expected: Max qty error message
- Actual: Qty accepted, total price incorrect
- Severity: High

Bug 2: Payment timeout not handled
- Summary: No error message after 30s timeout
- Steps: Initiate payment, wait 30+ seconds
- Expected: Timeout error message
- Actual: Page hangs, no response
- Severity: Critical

Bug 3: Coupon applies to wrong items
- Summary: Coupon discount applied to all items
- Steps: Apply category-specific coupon, add items from other category
- Expected: Discount only on category items
- Actual: Discount applied to all items
- Severity: Major
```

---

## Mock Project 2: Banking Application

### Project Overview

```
Application: Online Banking Portal
Type: Web-based banking system
Users: Customers, Agents, Managers, Admin
Regulations: RBI compliance, PCI DSS
Security: High level required
Phase: System Testing
Duration: 4 weeks
```

### Features to Test

#### **User Authentication**
```
☐ Login
  • Email/User ID
  • Password (min 8 chars)
  • OTP verification
  • Two-factor auth
  • Session management

☐ Account Recovery
  • Forgot password flow
  • Email verification
  • OTP-based reset
  • Security questions
  • Account unlock
```

#### **Account Management**
```
☐ View Accounts
  • Checking account
  • Savings account
  • Investment account
  • Loan account
  • Account balance
  • Transaction history

☐ Account Services
  • Update profile
  • Change password
  • Update contact info
  • Download statements
  • Set alerts
```

#### **Fund Transfer**
```
☐ Transfer Types
  • Same bank transfer
  • NEFT transfer
  • RTGS transfer
  • Domestic transfer
  • International transfer

☐ Transfer Process
  • Add beneficiary
  • Verify beneficiary
  • Enter amount
  • Review details
  • Confirm with OTP
  • Receipt generation
```

#### **Bill Payments**
```
☐ Utility Bills
  • Electricity
  • Water
  • Gas
  • Internet

☐ Insurance
  • Life insurance
  • Health insurance
  • Vehicle insurance

☐ Loan Payments
  • EMI payment
  • Loan prepayment
```

#### **Loan Management**
```
☐ Loan Application
  • Apply for loan
  • Submit documents
  • Track application
  • Loan approval

☐ Loan Monitoring
  • View balance
  • View EMI schedule
  • Track payments
  • Request modifications
```

### Security Test Cases

```
Security Test 1: SQL Injection
- Attempt to login with: admin' or '1'='1
- Expected: Login fails, error message
- Result: Should NOT provide access

Security Test 2: XSS (Cross-Site Scripting)
- Enter in search: <script>alert('XSS')</script>
- Expected: Script not executed, treated as text
- Result: No alert should appear

Security Test 3: Session Hijacking
- Login, copy session token
- Use token from different IP
- Expected: Session invalidated
- Result: Request should be rejected

Security Test 4: Password Security
- Try weak password: "123"
- Expected: Minimum 8 chars required
- Result: Rejected with error message

Security Test 5: Unauthorized Access
- Directly access: /admin/users
- Expected: 403 Forbidden
- Result: Should not display admin panel
```

### Compliance Checklist

```
RBI Compliance:
☐ Account number validation
☐ IFSC code validation
☐ KYC verification
☐ PAN validation
☐ Beneficiary limit checks
☐ Daily transaction limits
☐ Monthly transfer limits

PCI DSS Compliance:
☐ Data encryption (TLS 1.2+)
☐ No credit card storage
☐ Audit trails maintained
☐ Access control implemented
☐ Regular security testing
☐ Penetration testing done
☐ Vulnerability scanning passed

Data Protection:
☐ GDPR compliance (if EU users)
☐ Data retention policy
☐ Personal data encryption
☐ Right to be forgotten
☐ Privacy policy clarity
```

### Performance Requirements

```
Page Load Time:
- Login page: < 2 seconds
- Dashboard: < 3 seconds
- Transfer page: < 2 seconds
- Report generation: < 10 seconds

Throughput:
- Handle 10,000 concurrent users
- 5 MB/s data transfer
- 1000 transactions/second

Response Time:
- Account balance query: < 500ms
- Transaction history: < 1 second
- Fund transfer: < 2 seconds
- Report download: < 15 seconds
```

---

## Mock Project 3: Social Media Application

### Project Overview

```
Application: Social Networking Platform
Type: Web & Mobile app
Users: Regular users, Influencers, Brands
Features: Posts, Messaging, Groups, Events
Phase: Beta Testing
Duration: 2 weeks
```

### Features to Test

#### **User Profile**
```
☐ Profile Management
  • View profile
  • Edit profile
  • Upload profile picture
  • Add bio
  • Add interests
  • Privacy settings

☐ Follower System
  • Follow user
  • Unfollow user
  • Accept follow request
  • Reject follow request
  • View followers
  • View following
```

#### **Posts & Content**
```
☐ Create Post
  • Text post
  • Image post
  • Video post
  • Shared post
  • Post scheduling

☐ Post Interaction
  • Like post
  • Comment on post
  • Share post
  • Save post
  • Delete post
  • Edit post

☐ News Feed
  • Chronological feed
  • Algorithm-based feed
  • Trending posts
  • Following posts only
  • Infinite scroll
```

#### **Messaging**
```
☐ Direct Messaging
  • Send message
  • Receive message
  • View chat history
  • Delete message
  • Mark as read
  • Typing indicator

☐ Group Chat
  • Create group
  • Add members
  • Remove members
  • Send group message
  • Group mute
  • Leave group
```

#### **Notifications**
```
☐ Notification Types
  • Like notifications
  • Comment notifications
  • Follow notifications
  • Message notifications
  • Event notifications
  • Mention notifications

☐ Notification Management
  • View notifications
  • Mark as read
  • Delete notification
  • Notification settings
  • Mute notifications
```

### Usability Test Cases

```
Usability Test 1: First Time User
- Scenario: New user signup to first post
- Measure: Time taken, steps required
- Expected: < 5 minutes, intuitive
- Success: User completes without help

Usability Test 2: Profile Update
- Scenario: Update profile picture
- Measure: Steps required, clarity
- Expected: 2-3 clicks maximum
- Success: User finds & updates easily

Usability Test 3: Create Post
- Scenario: Create text + image post
- Measure: Clarity, options availability
- Expected: Clear formatting options
- Success: Post created with proper format

Usability Test 4: Navigation
- Scenario: Navigate between sections
- Measure: Menu clarity, hierarchy
- Expected: Clear menu structure
- Success: User finds sections easily

Usability Test 5: Settings
- Scenario: Change notification settings
- Measure: Settings discoverability
- Expected: Clear settings organization
- Success: User finds & changes settings
```

### Cross-Browser Testing

```
Browsers to Test:
✓ Chrome (latest 2 versions)
✓ Firefox (latest 2 versions)
✓ Safari (latest)
✓ Edge (latest)
✓ Mobile Chrome
✓ Mobile Safari

Issues to Check:
- Layout alignment
- Button functionality
- Form submission
- Media playback
- Performance
- Session persistence
```

---

## Testing Approach Guide

### 1. Preparation (Week 1)

```
Step 1: Requirements Review
- Read feature specifications
- Understand user flows
- Identify test scenarios
- Create test plan

Step 2: Test Case Design
- Write test cases
- Include positive/negative cases
- Add boundary scenarios
- Get approval

Step 3: Test Data Preparation
- Create test users
- Prepare test data
- Setup test environment
- Verify environment readiness
```

### 2. Execution (Week 2-3)

```
Daily Activities:
- Execute assigned test cases
- Report bugs immediately
- Verify fixes
- Update status

Weekly Activities:
- Status meeting
- Risk assessment
- Scope review
- Adjust schedule if needed
```

### 3. Reporting (Week 4)

```
Final Report Should Include:
- Test execution summary
- Defect summary
- Test coverage metrics
- Quality assessment
- Go/No-Go recommendation
```

---

## Best Practices

### Testing Best Practices

```
✅ DO:
- Test on clean environment
- Follow test case steps exactly
- Report bugs with evidence
- Communicate findings immediately
- Focus on user perspective
- Test edge cases
- Verify fixes thoroughly
- Document blockers

❌ DON'T:
- Assume, verify instead
- Test with production data
- Skip test setup
- Report vague bugs
- Test while tired
- Skip regression
- Assume fix works
- Rush through testing
```

### Bug Reporting Best Practices

```
✅ Effective Bug Report:
- Clear, specific summary
- Exact steps to reproduce
- Expected vs Actual result
- Screenshots/videos attached
- Environment details included
- Severity/Priority correct
- One issue per bug
- Recent findings first

❌ Poor Bug Report:
- Vague summary ("bug found")
- Unclear reproduction steps
- Missing expected result
- No supporting evidence
- Wrong severity level
- Multiple issues mixed
- Unclear impact statement
```

---

## Practice Tasks

### Task 1: E-Commerce Testing
```
Duration: 5 days
1. Write 50 test cases
2. Execute all cases
3. Report 10-15 bugs
4. Create test summary report
Deliverables: Test cases, bug reports, summary
```

### Task 2: Banking Testing
```
Duration: 4 days
1. Design security test cases
2. Execute functional tests
3. Verify compliance checklist
4. Performance test key features
5. Report critical issues
Deliverables: Test plan, results, compliance report
```

### Task 3: Social Media Testing
```
Duration: 3 days
1. Perform exploratory testing
2. Write test cases for critical paths
3. Execute cross-browser tests
4. Usability evaluation
5. Bug report compilation
Deliverables: Test cases, bug list, usability findings
```

---

## Summary

Mock projects help you:
- Gain practical testing experience
- Learn real-world scenarios
- Practice bug reporting
- Understand domain knowledge
- Build confidence
- Prepare for interviews
- Develop professional skills

Complete all 3 projects to gain comprehensive testing experience.

---

## Key Takeaways

✅ Test like real projects  
✅ Practice all phases  
✅ Write quality test cases  
✅ Report bugs properly  
✅ Complete all projects  

---

**Happy Practicing! 🚀**

---

*Module 27: Mock Projects - Complete Guide*  
*Created: 2026 | Language: Hinglish (Hindi + English)*  
*For: QA Professionals & Aspirants*
