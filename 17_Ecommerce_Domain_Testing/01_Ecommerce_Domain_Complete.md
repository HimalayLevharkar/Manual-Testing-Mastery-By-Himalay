# 17_Ecommerce_Domain_Testing

## E-commerce Applications को Professional तरीके से Test करना
### Complete Guide to E-commerce Domain Testing with Real-World Scenarios

---

## 📋 Table of Contents

1. [E-commerce Domain Overview](#overview)
2. [E-commerce Features to Test](#features)
3. [Shopping Cart Testing](#cart)
4. [Payment Gateway Testing](#payment)
5. [Order Management](#orders)
6. [Inventory Management](#inventory)
7. [User Experience Testing](#ux)
8. [Security Testing](#security)
9. [Real E-commerce Scenarios](#scenarios)
10. [Common Bugs in E-commerce](#bugs)
11. [Test Cases Examples](#test-cases)
12. [Interview Questions](#interview)

---

## 🎯 E-commerce Domain Overview {#overview}

### What is E-commerce Testing?

E-commerce testing ka matlab hai online shopping platforms ko thoroughly test karna to ensure:
- ✅ All features work correctly
- ✅ Transactions are secure
- ✅ User experience is smooth
- ✅ Inventory is accurate
- ✅ Payments process correctly
- ✅ Orders are fulfilled properly

### Why E-commerce Testing is Critical?

```
Business Impact of Bugs in E-commerce:

💰 Direct Revenue Loss
   - Failed checkout = Lost sale
   - Payment issues = Cart abandonment
   - Wrong pricing = Revenue loss OR customer trust loss

📉 Customer Trust Loss
   - Security issues = Never return
   - Wrong orders = Negative reviews
   - Poor UX = Competitor switch

🏆 Brand Reputation
   - Social media amplifies bad experiences
   - One viral complaint = Thousands lose trust
   - Recovery takes months/years
```

### E-commerce Testing Challenges

| Challenge | Why It's Hard | Testing Focus |
|-----------|---------------|---------------|
| **Multiple Payment Methods** | Cards, UPI, Wallets, COD, EMI | Each flow different |
| **Inventory Sync** | Real-time updates needed | Race conditions |
| **Third-party Integrations** | Payment gateways, shipping, SMS | External dependencies |
| **High Traffic Spikes** | Sales, festivals | Performance testing |
| **Complex Promotions** | Coupons, offers, cashback | Calculation accuracy |
| **Multi-device Experience** | Web, mobile web, apps | Consistency |

---

## 🛒 E-commerce Features to Test {#features}

### Complete Testing Checklist

### 1️⃣ User Registration & Login

```
□ Email registration with OTP verification
□ Social login (Google, Facebook, Apple)
□ Phone number login with OTP
□ Password strength validation
□ Forgot password flow
□ Account lockout after failed attempts
□ Session management
□ Multi-device login handling
□ Guest checkout option
```

### 2️⃣ Product Catalog

```
□ Product listing with filters
□ Product search functionality
□ Product categories & subcategories
□ Product images (zoom, multiple angles)
□ Product descriptions & specifications
□ Price display (MRP, discount, final)
□ Stock availability indicator
□ Product ratings & reviews
□ Related products suggestions
□ Recently viewed products
```

### 3️⃣ Shopping Cart

```
□ Add to cart functionality
□ Update quantity
□ Remove items
□ Cart persistence (login/logout)
□ Price recalculation
□ Stock validation
□ Expiry of cart items
□ Cross-device cart sync
□ Abandoned cart recovery
□ Cart sharing option
```

### 4️⃣ Checkout Process

```
□ Address selection/addition
□ Address validation
□ Delivery options
□ Delivery time slots
□ Payment method selection
□ Coupon code application
□ Gift card redemption
□ Order summary
□ Terms & conditions checkbox
□ Order confirmation
```

### 5️⃣ Payment Processing

```
□ Credit/Debit cards
□ Net banking
□ UPI payments
□ Digital wallets
□ EMI options
□ Cash on delivery
□ Payment gateway integration
□ Payment failure handling
□ Refund processing
□ Payment confirmation
```

### 6️⃣ Order Management

```
□ Order confirmation email/SMS
□ Order tracking
□ Order history
□ Order cancellation
□ Return/Replacement requests
□ Refund status
□ Invoice generation
□ Delivery updates
□ Failed order handling
□ Partial order fulfillment
```

### 7️⃣ Inventory Management

```
□ Real-time stock updates
□ Low stock alerts
□ Out of stock handling
□ Backorder management
□ Pre-order functionality
□ Multi-warehouse sync
□ Inventory reservation
□ Stock reconciliation
□ Damaged goods handling
□ Return to inventory
```

### 8️⃣ Shipping & Delivery

```
□ Shipping cost calculation
□ Free shipping thresholds
□ Express delivery options
□ Delivery pincode validation
□ Courier partner integration
□ Shipping label generation
□ Tracking number assignment
□ Delivery exceptions handling
□ Failed delivery attempts
□ COD remittance tracking
```

### 9️⃣ Customer Support

```
□ Contact us form
□ Live chat integration
□ Chatbot functionality
□ Ticket creation
□ Ticket status tracking
□ FAQ section
□ Return policy display
□ Refund policy display
□ Escalation matrix
□ Feedback collection
```

### 🔟 Promotions & Offers

```
□ Coupon code validation
□ Discount calculations
□ Cashback offers
□ Loyalty points
□ Referral bonuses
□ Flash sales
□ Bundle offers
□ Bank offers
□ Seasonal sales
□ First-time user offers
```

---

## 🛍️ Shopping Cart Testing Deep Dive {#cart}

### Shopping Cart Test Scenarios

### Add to Cart Testing

```
Test Case: Add Single Item
- Select product
- Click "Add to Cart"
- Verify:
  ✓ Cart icon shows count = 1
  ✓ Success message displayed
  ✓ Product appears in cart
  ✓ Price matches product page
  ✓ Quantity = 1 (default)
  ✓ Continue shopping OR checkout options

Test Case: Add Multiple Items
- Add 5 different products
- Verify:
  ✓ Cart count = 5
  ✓ All items listed
  ✓ Individual prices correct
  ✓ Subtotal calculation correct
  ✓ Delivery charges (if any)
  ✓ Grand total accurate
```

### Cart Quantity Updates

```
Test Case: Increase Quantity
- Go to cart
- Click + button
- Verify:
  ✓ Quantity increments
  ✓ Price recalculates
  ✓ Stock availability check
  ✓ "Out of stock" if exceeds limit

Test Case: Decrease Quantity
- Go to cart
- Click - button
- Verify:
  ✓ Quantity decrements
  ✓ Price recalculates
  ✓ Remove option appears at qty = 1

Test Case: Direct Quantity Input
- Go to cart
- Type quantity = 10
- Verify:
  ✓ Accepts if in stock
  ✓ Shows error if exceeds limit
  ✓ Updates price accordingly
```

### Cart Edge Cases

```
🔴 Edge Case 1: Add Out of Stock Item
- Product goes out of stock after adding to cart
- Expected: Show "Out of Stock" warning
- Expected: Disable checkout for that item
- Expected: Suggest similar products

🔴 Edge Case 2: Price Change in Cart
- Product price changes while in cart
- Expected: Show "Price updated" notification
- Expected: Display old vs new price
- Expected: Ask user to confirm

🔴 Edge Case 3: Cart Abandonment
- User adds items, leaves without checkout
- Expected: Cart persists for X days
- Expected: Send abandoned cart email
- Expected: Show items on return

🔴 Edge Case 4: Multiple Devices
- Add item on mobile
- Login on desktop
- Expected: Cart syncs across devices
- Expected: No duplicate items
- Expected: Real-time updates
```

### Cart Calculations

```
Calculation Test Cases:

Subtotal = Σ(Product Price × Quantity)

Discount = Subtotal × (Discount % / 100)
         OR fixed amount

Shipping = Based on:
  - Weight
  - Distance
  - Delivery speed
  - Order value (free above X)

Tax = (Subtotal - Discount) × (Tax % / 100)

Grand Total = Subtotal - Discount + Shipping + Tax

✅ Verify each calculation manually
✅ Verify rounding (2 decimal places)
✅ Verify negative values don't appear
✅ Verify zero-value edge cases
```

---

## 💳 Payment Gateway Testing {#payment}

### Payment Methods to Test

### Credit/Debit Card Testing

```
Test Fields:
□ Card Number (16 digits validation)
□ Card Holder Name
□ Expiry Date (MM/YY format)
□ CVV (3-4 digits)
□ Billing Address
□ Save card option (PCI compliant)

Validation Tests:
□ Invalid card number format
□ Expired card
□ Invalid CVV length
□ Missing mandatory fields
□ Card number with spaces/dashes
□ Future expiry date validation

Integration Tests:
□ Successful payment
□ Payment declined
□ Insufficient funds
□ Card blocked
□ 3D Secure authentication
□ OTP verification
□ Payment timeout
□ Duplicate payment prevention
```

### UPI Payment Testing

```
UPI Flow Testing:
□ Select UPI option
□ Enter UPI ID
□ Validate UPI ID format
□ Generate payment request
□ User approves in UPI app
□ Payment confirmation
□ Update order status
□ Send confirmation

UPI Test Scenarios:
□ Valid UPI ID
□ Invalid UPI ID format
□ UPI ID not registered
□ Payment declined by user
□ Payment timeout
□ Network failure during payment
□ Duplicate UPI requests
□ Partial payment scenarios
□ Refund to UPI ID
```

### Net Banking Testing

```
Bank Selection:
□ List all supported banks
□ Search bank functionality
□ Popular banks highlighted
□ Bank logo display

Redirection Testing:
□ Redirect to bank page
□ Bank login
□ Bank authentication
□ Payment approval
□ Redirect back to e-commerce
□ Order confirmation

Error Handling:
□ Bank server down
□ Session timeout at bank
□ Transaction failed at bank
□ User cancelled at bank
□ Network interruption
```

### Digital Wallet Testing

```
Supported Wallets:
□ Paytm
□ PhonePe
□ Google Pay
□ Amazon Pay
□ FreeCharge
□ Mobikwik

Wallet Flow:
□ Select wallet
□ Redirect to wallet
□ Wallet authentication
□ Payment approval
□ Return to e-commerce
□ Order confirmation

Wallet Scenarios:
□ Insufficient wallet balance
□ Wallet payment failed
□ Wallet session expired
□ Wallet not linked
□ Cashback credited to wallet
```

### EMI Options Testing

```
EMI Calculation:
□ Select EMI option
□ Choose tenure (3/6/9/12/18/24 months)
□ Verify EMI amount
□ Verify interest rate
□ Verify processing fee
□ Verify total payable amount

Bank EMI:
□ Eligible cards
□ Bank-specific offers
□ No-cost EMI
□ Standard EMI
□ Down payment options

Cardless EMI:
□ Eligibility check
□ Approval process
□ Documentation
□ Activation
□ Repayment terms
```

### Cash on Delivery (COD) Testing

```
COD Availability:
□ Pincode serviceability
□ Order value limits
□ Product category restrictions
□ User eligibility (new users?)
□ Frequency limits per user

COD Restrictions:
□ High-value orders
□ Certain pincodes
□ Certain products
□ New account restrictions
□ Previous COD failure history

COD Flow:
□ Select COD option
□ Confirm order
□ Generate order
□ Dispatch
□ Delivery attempt
□ Cash collection
□ COD remittance tracking
```

### Payment Failure Scenarios

```
Critical Failure Tests:

🔴 Payment Deducted but Order Failed
- Money debited from account
- E-commerce site shows failure
- Expected: Auto-reversal in 3-5 days
- Expected: Manual refund option
- Expected: Customer support escalation

🔴 Payment Timeout
- User completes payment
- Timeout before confirmation
- Expected: Payment status check
- Expected: Retry option
- Expected: Order confirmation on success

🔴 Duplicate Payment
- User clicks pay twice
- Network lag
- Expected: Prevent duplicate
- Expected: Refund duplicate
- Expected: Single order created

🔴 Partial Payment
- Split payment (wallet + card)
- One part succeeds, one fails
- Expected: Rollback successful part
- Expected: Clear error message
- Expected: Retry full payment
```

---

## 📦 Order Management Testing {#orders}

### Order Lifecycle

```
Order Status Flow:

1. ORDER PLACED
   ↓
2. PAYMENT CONFIRMED
   ↓
3. PROCESSING
   ↓
4. SHIPPED
   ↓
5. OUT FOR DELIVERY
   ↓
6. DELIVERED
   ↓
7. COMPLETED

Alternative Flows:
- CANCELLED (any stage before delivery)
- RETURNED (after delivery)
- REFUNDED (after return)
- FAILED (payment/order creation)
```

### Order Creation Testing

```
Order Creation Flow:
□ Cart validation
□ Address confirmation
□ Payment confirmation
□ Inventory reservation
□ Order number generation
□ Confirmation email
□ Confirmation SMS
□ Order visible in history

Order Details:
□ Order number (unique)
□ Order date & time
□ Items list with quantities
□ Prices (item-wise, subtotal, tax, shipping)
□ Delivery address
□ Payment method
□ Payment status
□ Estimated delivery date
□ Tracking information
```

### Order Cancellation Testing

```
Cancellation Scenarios:

Before Shipment:
□ User cancels from order history
□ Verify cancellation allowed
□ Refund initiated
□ Cancellation confirmation
□ Email/SMS sent

After Shipment:
□ Cancellation not allowed
□ Show "Return after delivery" option
□ OR intercept shipment (if possible)

Refund Processing:
□ Refund to source (card/wallet/UPI)
□ Refund timeline (3-5 days)
□ Refund status tracking
□ Refund failure handling
```

### Order Tracking Testing

```
Tracking Features:
□ Real-time status updates
□ Tracking number
□ Courier partner link
✓ Expected delivery date
✓ Delivery attempts
✓ Delivery agent details
✓ Live location (if available)

Tracking Scenarios:
□ Order just placed
□ Order dispatched
□ In transit
□ Out for delivery
□ Delivered
□ Delivery failed
□ Rescheduled delivery
```

### Return & Replacement Testing

```
Return Flow:
□ Initiate return request
□ Select reason
□ Upload images (if needed)
□ Pickup scheduled
□ Item picked up
□ Quality check
□ Refund/Replacement processed

Return Reasons:
□ Wrong item delivered
□ Damaged/Defective
□ Missing parts
□ Quality issues
□ Size/Color change
□ No longer needed
□ Extra items delivered

Replacement Flow:
□ Request replacement
□ Same item availability check
□ Pickup original item
□ Send replacement
□ Track replacement
□ Close request

Refund Flow:
□ Return approved
□ Refund amount calculated
□ Refund method (original/source)
□ Refund processed
□ Refund credited
□ Refund status visible
```

---

## 📊 Inventory Management Testing {#inventory}

### Inventory Test Scenarios

### Stock Level Testing

```
Low Stock Alerts:
□ Threshold configuration
□ Alert to admin
□ "Only X left" message to users
□ Urgency indicator

Out of Stock Handling:
□ Product page shows "Out of Stock"
□ Add to cart disabled
□ Notify me option
□ Similar products suggestion
□ Expected restock date (if known)

Backorder Management:
□ Accept orders beyond stock
□ Clear communication to user
□ Expected ship date
□ Partial fulfillment option
```

### Inventory Sync Testing

```
Real-time Sync:
□ Multiple users viewing same product
□ One user buys last item
□ Other users see "Out of Stock" immediately
□ Cart items validated at checkout

Race Condition Testing:
□ 10 users try to buy last item simultaneously
□ Only 1 succeeds
□ Others get "Out of Stock" at checkout
□ No overselling

Multi-warehouse Sync:
□ Inventory across warehouses
□ Nearest warehouse allocation
□ Transfer between warehouses
□ Central inventory view
```

### Inventory Edge Cases

```
🔴 Overselling Prevention
- 5 items in stock
- 10 users add to cart
- 7 users complete checkout
- Expected: Only 5 orders confirmed
- Expected: 2 orders cancelled with apology

🔴 Flash Sale Scenarios
- 100 items at 90% discount
- 10000 users trying to buy
- Expected: Queue system
- Expected: Fair allocation
- Expected: Clear communication

🔴 Inventory Reservation
- User adds to cart
- Item reserved for 10 minutes
- After 10 minutes, released
- Expected: Clear messaging
- Expected: Timer display (optional)
```

---

## 🎨 User Experience Testing {#ux}

### UX Testing Checklist

### Page Load Performance

```
Performance Metrics:
□ Homepage load < 3 seconds
□ Product listing < 2 seconds
□ Product page < 2 seconds
□ Cart page < 1 second
□ Checkout < 2 seconds
□ Payment < 3 seconds
□ Order confirmation < 2 seconds

Performance Tools:
□ Google PageSpeed Insights
□ GTmetrix
□ WebPageTest
□ Lighthouse
```

### Mobile Responsiveness

```
Mobile Testing:
□ All screens responsive
□ Touch-friendly buttons
□ Easy navigation
□ Readable text without zoom
□ Images scale properly
□ Forms easy to fill
□ Checkout mobile-optimized
□ Payment mobile-friendly

Device Testing:
□ Small phones (5" screen)
□ Large phones (6.5" screen)
□ Tablets (7-10")
□ Different orientations
```

### Navigation & Search

```
Navigation Testing:
□ Categories clear
□ Breadcrumbs visible
□ Easy to go back
□ Home button accessible
□ Cart always accessible
□ Search always visible
□ Account menu accessible

Search Testing:
□ Search by product name
□ Search by category
□ Search by brand
□ Search by price range
□ Autocomplete suggestions
□ Recent searches
□ Popular searches
□ No results handling
□ Spell correction
```

### Accessibility Testing

```
Accessibility Checklist:
□ Alt text for images
□ Keyboard navigation
□ Screen reader compatibility
□ Color contrast (WCAG)
□ Font size options
□ Focus indicators
□ ARIA labels
□ Skip to content option
```

---

## 🔒 Security Testing for E-commerce {#security}

### Security Testing Areas

### Authentication Security

```
□ Strong password enforcement
□ OTP for login
□ Session timeout
□ Multi-device session management
□ Suspicious login detection
□ Account takeover prevention
□ 2FA option
```

### Payment Security

```
□ PCI DSS compliance
□ Card data not stored
□ Secure payment gateway
□ HTTPS for all payment pages
□ No card data in logs
□ Tokenization
□ 3D Secure authentication
```

### Data Protection

```
□ Personal data encryption
□ Address data protected
□ Phone number masked
□ Email not exposed
□ Order history private
□ Account data secure
□ GDPR compliance (if applicable)
```

### Common E-commerce Vulnerabilities

```
OWASP Top 10 for E-commerce:

1. SQL Injection
   - Search functionality
   - Login forms
   - Order lookup

2. XSS (Cross-Site Scripting)
   - Product reviews
   - User-generated content
   - Search results

3. CSRF (Cross-Site Request Forgery)
   - Add to cart
   - Change address
   - Update profile

4. Broken Authentication
   - Weak passwords
   - Session fixation
   - Credential stuffing

5. Sensitive Data Exposure
   - Unencrypted data
   - Data in URLs
   - Insecure APIs

6. Broken Access Control
   - View other's orders
   - Modify other's addresses
   - Access admin pages

7. Security Misconfiguration
   - Default credentials
   - Verbose errors
   - Directory listing

8. Insecure Deserialization
   - Session data
   - API payloads

9. Using Components with Known Vulnerabilities
   - Outdated libraries
   - Unpatched software

10. Insufficient Logging & Monitoring
    - No fraud detection
    - Delayed breach discovery
```

---

## 🎬 Real E-commerce Scenarios {#scenarios}

### Scenario 1: Flash Sale Testing

```
Context:
Big Billion Day sale - 50% off on electronics
100 iPhones at ₹10,000 (worth ₹50,000)
Sale starts at midnight
Expected traffic: 1 million users in first minute

Testing Approach:

Pre-Sale Testing:
□ Load testing (1M concurrent users)
□ Stress testing (beyond capacity)
□ Database performance
□ Caching effectiveness
□ CDN configuration
□ Queue system testing
□ Inventory locking

During Sale:
□ Monitor server health
□ Monitor response times
□ Monitor error rates
□ Monitor queue wait times
□ Monitor inventory sync

Post-Sale:
□ Order confirmation delivery
□ Payment processing
□ Inventory reconciliation
□ Failed user communication
□ Refund processing (if needed)

Expected Issues:
- Site slowdown
- Queue wait times
- Payment timeouts
- Cart issues
- Inventory sync delays

Mitigation:
- Auto-scaling
- Queue system
- Clear messaging
- Customer support ready
```

### Scenario 2: Festival Sale (Diwali/EID)

```
Context:
Week-long festival sale
Multiple offers running simultaneously
High traffic throughout week
COD orders increase 3x

Testing Focus:

Promotion Testing:
□ All offers working
□ Offer stacking rules
□ Bank offers
□ Coupon codes
□ Cashback offers
□ Exchange offers

Performance Testing:
□ Sustained high traffic
□ Peak hour handling
□ Database optimization
□ Caching strategy

Inventory Testing:
□ Real-time updates
□ Multi-warehouse sync
□ Overselling prevention
□ Restock updates

Payment Testing:
□ All payment methods
□ COD limits
□ Payment gateway capacity
□ Refund processing

Delivery Testing:
□ Pincode validation
□ Delivery timelines
□ Courier capacity
□ COD handling
```

### Scenario 3: New Product Launch

```
Context:
Latest smartphone launch
Pre-orders start next week
Limited stock for first sale
High anticipation

Testing Approach:

Pre-Launch:
□ Product page ready
□ Pre-order flow
□ Payment authorization (not capture)
□ Inventory allocation
□ Email notifications

Launch Day:
□ Real-time inventory
□ Queue management
□ Payment processing
□ Order confirmations
□ Customer communication

Post-Launch:
□ Order tracking
□ Delivery scheduling
□ Customer support
□ Return handling (if any)
```

### Scenario 4: Cart Abandonment Recovery

```
Context:
70% cart abandonment rate
Need recovery mechanism
Business wants automated emails

Testing Flow:

Abandonment Detection:
□ User adds to cart
□ User leaves without checkout
□ Timer starts (1 hour, 24 hours, 7 days)
□ Cart persisted

Email Triggers:
□ 1 hour: Gentle reminder
□ 24 hours: Urgency ("Items selling fast")
□ 7 days: Final reminder + discount

Email Content:
□ Cart items shown
□ Images included
□ Direct checkout link
□ Offer code (if any)
□ Unsubscribe option

Testing:
□ Email delivery
□ Email rendering
□ Links working
□ Personalization
□ Timing accuracy
□ Unsubscribe working
□ Frequency capping
```

### Scenario 5: International Expansion

```
Context:
E-commerce expanding to new country
New currency
New payment methods
New shipping partners

Testing Areas:

Currency:
□ Price conversion
□ Display format
□ Rounding
□ Multiple currency support

Payment Methods:
□ Country-specific methods
□ Local cards
□ Local wallets
□ COD availability

Shipping:
□ International shipping
□ Customs calculation
□ Delivery timelines
□ Tracking integration

Localization:
□ Language support
□ Date formats
□ Address formats
□ Phone number formats

Compliance:
□ Local regulations
□ Tax calculation
□ Import restrictions
□ Data privacy laws
```

---

## 🐛 Common Bugs in E-commerce {#bugs}

### Real Production Bugs

### Bug 1: Cart Total Calculation Error

```
Title: Cart shows incorrect total when multiple coupons applied

Severity: HIGH
Priority: CRITICAL

Steps to Reproduce:
1. Add items worth ₹5000 to cart
2. Apply coupon "SAVE500" (₹500 off)
3. Apply coupon "EXTRA10" (10% off)
4. Check cart total

Expected:
- Subtotal: ₹5000
- SAVE500: -₹500
- EXTRA10: -₹450 (10% of 4500)
- Total: ₹4050

Actual:
- Total shown: ₹4100 (10% calculated on ₹5000, not ₹4500)

Root Cause:
- Coupon stacking logic incorrect
- Second coupon applied on original amount, not after first coupon

Impact:
- Revenue loss
- Customer complaints
- Trust issues

Fix:
- Apply coupons sequentially
- Recalculate after each coupon
- Add validation tests
```

### Bug 2: Payment Deducted but Order Failed

```
Title: Payment successful at bank but order shows failed

Severity: CRITICAL
Priority: CRITICAL

Steps to Reproduce:
1. Add item to cart
2. Proceed to checkout
3. Select card payment
4. Complete 3D Secure authentication
5. Bank shows payment successful
6. E-commerce site shows "Order Failed"

Expected:
- Order confirmed
- Order number displayed
- Confirmation email sent

Actual:
- Money debited from account
- Order failed message
- No order number
- No confirmation email

Root Cause:
- Timeout in payment gateway callback
- Bank response delayed
- Site marked as failed before confirmation

Impact:
- Customer panic
- Support tickets spike
- Trust loss
- Refund requests

Fix:
- Payment status polling
- Retry mechanism
- Clear communication
- Auto-reversal process
- Manual escalation path
```

### Bug 3: Inventory Overselling

```
Title: Orders accepted beyond available stock

Severity: CRITICAL
Priority: CRITICAL

Steps to Reproduce:
1. Product has 5 units in stock
2. 10 users add to cart simultaneously
3. 8 users complete checkout
4. All 8 orders confirmed

Expected:
- Only 5 orders confirmed
- 3 users get "Out of Stock" notification

Actual:
- 8 orders confirmed
- Only 5 units available
- 3 orders to be cancelled

Root Cause:
- Inventory check at cart add, not at checkout
- Race condition in inventory update
- No locking mechanism

Impact:
- Order cancellations
- Customer dissatisfaction
- Refund processing
- Brand damage

Fix:
- Inventory reservation at cart add
- Inventory lock during checkout
- Atomic inventory updates
- Queue for high-demand items
```

### Bug 4: Wrong Discount Applied

```
Title: 50% off shown on MRP but applied on selling price

Severity: HIGH
Priority: HIGH

Steps to Reproduce:
1. Product MRP: ₹1000
2. Selling price: ₹800 (20% off already)
3. Flash sale: 50% off
4. Add to cart

Expected:
- 50% of MRP = ₹500
- Final price: ₹500

Actual:
- 50% of selling price = ₹400
- Final price: ₹400
- OR vice versa (₹600 instead of ₹500)

Root Cause:
- Discount calculation logic unclear
- MRP vs selling price confusion
- Multiple discount layers

Impact:
- Revenue loss OR customer trust loss
- Pricing complaints
- Manual corrections needed

Fix:
- Clear discount policy
- MRP-based calculations
- Thorough testing
- Price audit logs
```

### Bug 5: Address Saved for Wrong User

```
Title: User can see other user's saved addresses

Severity: CRITICAL
Priority: CRITICAL

Steps to Reproduce:
1. Login as User A
2. Go to saved addresses
3. See addresses of User B

Expected:
- Only User A's addresses visible

Actual:
- Random user's addresses visible
- Privacy breach

Root Cause:
- Session mix-up
- User ID not validated properly
- Caching issue

Impact:
- Privacy violation
- Security concern
- Legal implications
- Trust loss

Fix:
- Proper session validation
- User ID verification
- Clear cache
- Security audit
```

### Bug 6: COD Not Available but Shown

```
Title: COD option shown but unavailable after order

Severity: MEDIUM
Priority: HIGH

Steps to Reproduce:
1. Add items to cart
2. Proceed to checkout
3. COD option visible and selectable
4. Place order
5. Call from support: "COD not available for your pincode"

Expected:
- COD option hidden for unsupported pincodes
- OR clear message before order

Actual:
- COD shown as available
- Order placed
- Later informed COD not available

Root Cause:
- Pincode validation missing for COD
- Serviceability check incomplete

Impact:
- Customer inconvenience
- Order modification needed
- Delivery delay

Fix:
- Pincode-based COD validation
- Real-time serviceability check
- Clear communication
```

### Bug 7: Return Window Expired but Allowed

```
Title: Return accepted after return window expired

Severity: MEDIUM
Priority: MEDIUM

Steps to Reproduce:
1. Order delivered on Jan 1
2. Return window: 10 days
3. User initiates return on Jan 15
4. Return accepted

Expected:
- Return not allowed
- Message: "Return window expired"

Actual:
- Return request accepted
- Pickup scheduled

Root Cause:
- Return window calculation wrong
- Date comparison logic error
- Timezone issues

Impact:
- Inventory issues
- Refund for ineligible return
- Policy violation

Fix:
- Correct date calculation
- Timezone handling
- Validation at multiple stages
```

### Bug 8: Email Sent to Wrong Recipient

```
Title: Order confirmation email sent to wrong email

Severity: HIGH
Priority: HIGH

Steps to Reproduce:
1. User places order with email A
2. Updates email to B in profile
3. New order placed
4. Confirmation email sent to email A

Expected:
- Email sent to current email (B)

Actual:
- Email sent to old email (A)
- User B doesn't receive confirmation

Root Cause:
- Cached email used
- Profile update not synced
- Email fetched from wrong source

Impact:
- User confusion
- Order communication issues
- Support tickets

Fix:
- Use current profile email
- Clear cache on update
- Verify email before sending
```

---

## 📝 Test Cases Examples {#test-cases}

### Test Case 1: Complete Checkout Flow

```
Test Case ID: TC_CHECKOUT_001
Test Case Name: Complete Checkout with Card Payment
Test Type: Functional
Priority: HIGH

Preconditions:
- User is logged in
- Cart has at least 1 item
- User has saved address

Test Steps:

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Click on Cart icon | Cart page opens |
| 2 | Verify cart items | All items displayed correctly |
| 3 | Click "Proceed to Checkout" | Checkout page opens |
| 4 | Select delivery address | Address selected |
| 5 | Click "Continue" | Delivery options shown |
| 6 | Select delivery speed | Delivery option selected |
| 7 | Click "Continue" | Payment page opens |
| 8 | Select "Card Payment" | Card form displayed |
| 9 | Enter card details | All fields accept input |
| 10 | Click "Pay Now" | 3D Secure page opens |
| 11 | Complete 3D Secure | Authentication successful |
| 12 | Verify order confirmation | Order number displayed |
| 13 | Verify email | Confirmation email received |
| 14 | Verify SMS | Confirmation SMS received |
| 15 | Check order history | Order visible in history |

Postconditions:
- Order created successfully
- Inventory reduced
- Payment captured
- User notified

Pass Criteria:
- All steps complete successfully
- Order number generated
- Confirmations received
```

### Test Case 2: Coupon Code Application

```
Test Case ID: TC_COUPON_001
Test Case Name: Apply Valid Coupon Code
Test Type: Functional
Priority: HIGH

Preconditions:
- Cart has items worth ₹2000
- Valid coupon: "SAVE200" (₹200 off on ₹2000+)

Test Steps:

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Go to cart page | Cart displayed |
| 2 | Click "Apply Coupon" | Coupon input shown |
| 3 | Enter "SAVE200" | Coupon code entered |
| 4 | Click "Apply" | Coupon applied |
| 5 | Verify discount | ₹200 discount shown |
| 6 | Verify total | Total reduced by ₹200 |
| 7 | Verify coupon message | "Coupon applied successfully" |

Postconditions:
- Discount applied
- Cart total updated

Pass Criteria:
- Correct discount amount
- Total recalculated
- Success message shown

Test Data:
- Cart value: ₹2000
- Coupon: SAVE200
- Expected discount: ₹200
- Expected total: ₹1800
```

### Test Case 3: Out of Stock Handling

```
Test Case ID: TC_STOCK_001
Test Case Name: Product Goes Out of Stock in Cart
Test Type: Edge Case
Priority: HIGH

Preconditions:
- Product has 1 unit in stock
- User A adds to cart
- User B buys the same product

Test Steps:

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | User A adds product to cart | Item added |
| 2 | User B buys same product | Order confirmed for B |
| 3 | User A proceeds to checkout | Warning displayed |
| 4 | Verify cart message | "Item out of stock" |
| 5 | Verify checkout button | Disabled/greyed out |
| 6 | Verify suggestions | Similar products shown |

Postconditions:
- User A cannot checkout
- Clear communication
- Alternatives provided

Pass Criteria:
- Out of stock warning shown
- Checkout prevented
- Helpful suggestions provided
```

### Test Case 4: Payment Failure Recovery

```
Test Case ID: TC_PAYMENT_001
Test Case Name: Payment Failure with Money Deducted
Test Type: Error Handling
Priority: CRITICAL

Preconditions:
- User has valid card
- Sufficient balance in account
- Order in checkout

Test Steps:

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Complete payment | Payment processed at bank |
| 2 | Simulate timeout | E-commerce site shows failure |
| 3 | Check bank account | Money debited |
| 4 | Check order status | Order shows failed |
| 5 | Wait 24 hours | Auto-reversal initiated |
| 6 | Check bank account | Money credited back |
| 7 | Verify communication | Email about reversal |

Postconditions:
- Money returned to user
- Clear communication
- No manual intervention needed

Pass Criteria:
- Auto-reversal within SLA
- User informed
- No duplicate charges
```

### Test Case 5: Return Request Flow

```
Test Case ID: TC_RETURN_001
Test Case Name: Initiate Product Return
Test Type: Functional
Priority: HIGH

Preconditions:
- Order delivered 5 days ago
- Return window: 10 days
- Product is returnable

Test Steps:

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Go to order history | Orders listed |
| 2 | Select delivered order | Order details shown |
| 3 | Click "Return Item" | Return form opens |
| 4 | Select return reason | Reason selected |
| 5 | Add comments (optional) | Comments saved |
| 6 | Upload images (optional) | Images uploaded |
| 7 | Select return type | Refund/Replacement |
| 8 | Submit request | Return request created |
| 9 | Verify pickup date | Pickup scheduled |
| 10 | Verify confirmation | Email/SMS received |

Postconditions:
- Return request created
- Pickup scheduled
- User notified

Pass Criteria:
- Return request successful
- Pickup scheduled within 2 days
- Confirmation received
```

### Test Case 6: Flash Sale Queue

```
Test Case ID: TC_FLASH_001
Test Case Name: Flash Sale Queue System
Test Type: Performance
Priority: CRITICAL

Preconditions:
- Flash sale starts at 12:00 PM
- 100 items available
- 10000 users waiting

Test Steps:

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Users join queue at 11:59 | Queue page displayed |
| 2 | Sale starts at 12:00 | Users enter queue |
| 3 | Queue processes users | Fair ordering |
| 4 | First 100 users | Can complete purchase |
| 5 | Remaining users | See "Sold Out" |
| 6 | Verify inventory | Exactly 100 sold |
| 7 | Verify wait time | Reasonable queue time |

Postconditions:
- Fair allocation
- No overselling
- Clear communication

Pass Criteria:
- No system crash
- Fair queue processing
- Accurate inventory
- Proper messaging
```

---

## 🎤 E-commerce Domain Interview Questions {#interview}

### Q1: How do you test an e-commerce website?

**Answer:**

E-commerce website testing requires comprehensive approach covering multiple areas:

**1. Functional Testing:**
- User registration and login
- Product search and filtering
- Add to cart functionality
- Checkout process
- Payment integration
- Order management
- Return/refund process

**2. UI/UX Testing:**
- Responsive design across devices
- Page load performance
- Navigation ease
- Search functionality
- Mobile experience

**3. Payment Testing:**
- All payment methods (cards, UPI, wallets, COD)
- Payment gateway integration
- Payment failure handling
- Refund processing
- Security compliance (PCI DSS)

**4. Security Testing:**
- Authentication security
- Data encryption
- Payment security
- Session management
- OWASP Top 10 vulnerabilities

**5. Performance Testing:**
- Load testing (normal traffic)
- Stress testing (flash sales)
- Scalability testing
- Database performance

**6. Integration Testing:**
- Payment gateway
- Shipping partners
- SMS/Email services
- Inventory management
- CRM systems

**7. Compatibility Testing:**
- Multiple browsers
- Multiple devices
- Multiple OS versions

**Key Focus Areas:**
- Cart calculations accuracy
- Inventory sync
- Payment security
- Order tracking
- Customer data protection

---

### Q2: How do you handle flash sale testing?

**Answer:**

Flash sale testing is critical because of high traffic and business impact:

**Pre-Sale Testing:**

1. **Load Testing:**
   - Simulate expected traffic (10x, 100x normal)
   - Identify breaking points
   - Optimize bottlenecks

2. **Stress Testing:**
   - Beyond capacity testing
   - System behavior under extreme load
   - Recovery testing

3. **Queue System Testing:**
   - Fair user ordering
   - Queue wait times
   - Queue timeout handling

4. **Inventory Testing:**
   - Overselling prevention
   - Real-time sync
   - Race condition testing

**During Sale:**

1. **Monitoring:**
   - Server health
   - Response times
   - Error rates
   - Queue metrics

2. **Quick Issue Resolution:**
   - Hotfix ready
   - Rollback plan
   - Communication templates

**Post-Sale:**

1. **Order Processing:**
   - Confirmation delivery
   - Payment capture
   - Inventory reconciliation

2. **Customer Communication:**
   - Success notifications
   - Failure apologies
   - Refund processing

**Key Considerations:**
- Auto-scaling configured
- CDN for static content
- Database connection pooling
- Caching strategy
- Clear user messaging

---

### Q3: What are the critical test scenarios for payment gateway?

**Answer:**

Payment gateway testing is most critical in e-commerce:

**Positive Scenarios:**
1. Successful payment with all methods
2. 3D Secure authentication
3. Payment confirmation and order creation
4. Receipt generation

**Negative Scenarios:**

1. **Payment Failures:**
   - Insufficient funds
   - Card declined
   - Invalid card details
   - Expired card
   - Wrong CVV
   - Network timeout

2. **Edge Cases:**
   - Payment deducted but order failed
   - Duplicate payment attempts
   - Partial payment (split payments)
   - Payment timeout
   - Gateway downtime

3. **Security Testing:**
   - Card data not stored
   - HTTPS enforcement
   - PCI DSS compliance
   - Session hijacking prevention
   - CSRF protection

4. **Integration Testing:**
   - Multiple gateways
   - Fallback mechanism
   - Retry logic
   - Status polling

5. **Refund Testing:**
   - Full refund
   - Partial refund
   - Refund to source
   - Refund failure
   - Refund timeline

**Most Critical:**
- Money deducted but order failed scenario
- Auto-reversal mechanism
- Clear customer communication

---

### Q4: How do you test inventory management in e-commerce?

**Answer:**

Inventory testing ensures no overselling and accurate stock:

**Key Test Scenarios:**

1. **Stock Level Testing:**
   - Add to cart when in stock
   - Prevent add to cart when out of stock
   - Low stock alerts
   - Stock threshold notifications

2. **Concurrency Testing:**
   - Multiple users buying same item
   - Last item race condition
   - Atomic inventory updates
   - Locking mechanism

3. **Inventory Sync:**
   - Real-time updates across channels
   - Multi-warehouse sync
   - Website and app sync
   - Marketplace integration

4. **Reservation Testing:**
   - Cart reservation timeout
   - Inventory release after timeout
   - Reservation during checkout
   - Inventory confirmation on payment

5. **Edge Cases:**
   - Flash sale scenarios
   - Bulk orders
   - Partial fulfillment
   - Backorder handling
   - Pre-order scenarios

**Test Approach:**
- Automated tests for calculations
- Manual tests for edge cases
- Performance tests for concurrency
- Integration tests for sync

---

### Q5: What security tests do you perform on e-commerce sites?

**Answer:**

Security is paramount in e-commerce due to financial transactions:

**Authentication Security:**
- Strong password validation
- OTP verification
- Session management
- Account lockout
- Multi-factor authentication
- Suspicious login detection

**Payment Security:**
- PCI DSS compliance
- Card data encryption
- Tokenization
- 3D Secure implementation
- No card data in logs
- Secure payment gateway

**Data Protection:**
- Personal data encryption
- Address privacy
- Order history privacy
- GDPR compliance
- Data minimization
- Right to deletion

**Common Vulnerability Testing:**

1. **SQL Injection:**
   - Search functionality
   - Login forms
   - Order lookup

2. **XSS:**
   - Product reviews
   - User-generated content
   - Profile fields

3. **CSRF:**
   - Add to cart
   - Address changes
   - Profile updates

4. **Access Control:**
   - View other's orders
   - Modify other's data
   - Admin access

5. **Session Security:**
   - Session fixation
   - Session hijacking
   - Concurrent sessions

**Security Tools:**
- OWASP ZAP
- Burp Suite
- SQLMap
- XSS Evaluator

---

### Q6: How do you handle testing for cart abandonment scenarios?

**Answer:**

Cart abandonment is a major business metric:

**Abandonment Detection:**
- User adds to cart
- User leaves without checkout
- Session timeout
- Cart persistence period

**Recovery Mechanism Testing:**

1. **Email Triggers:**
   - 1 hour reminder
   - 24 hour urgency email
   - 7 day final email with offer
   - Email content personalization
   - Direct checkout link

2. **Push Notifications:**
   - App users receive push
   - Timing optimization
   - Frequency capping

3. **Cart Persistence:**
   - Cart saved across sessions
   - Cross-device sync
   - Login required for persistence

**Test Scenarios:**
- Email delivery timing
- Email rendering
- Link functionality
- Offer code working
- Unsubscribe option
- Frequency limits

**Metrics to Track:**
- Abandonment rate
- Recovery rate
- Email open rate
- Click-through rate
- Conversion rate

---

### Q7: What metrics do you monitor for e-commerce performance?

**Answer:**

Key performance metrics for e-commerce:

**Technical Metrics:**

1. **Page Load Times:**
   - Homepage: < 3 seconds
   - Product listing: < 2 seconds
   - Product page: < 2 seconds
   - Checkout: < 2 seconds
   - Payment: < 3 seconds

2. **Core Web Vitals:**
   - LCP (Largest Contentful Paint): < 2.5s
   - FID (First Input Delay): < 100ms
   - CLS (Cumulative Layout Shift): < 0.1

3. **Server Metrics:**
   - Response time: < 200ms
   - Error rate: < 0.1%
   - Uptime: > 99.9%
   - Concurrent users capacity

**Business Metrics:**

1. **Conversion Metrics:**
   - Cart abandonment rate
   - Checkout completion rate
   - Conversion rate
   - Average order value

2. **User Metrics:**
   - Active users
   - Session duration
   - Pages per session
   - Return visitor rate

3. **Performance Metrics:**
   - Orders per minute
   - Payment success rate
   - Search success rate
   - Return rate

**Monitoring Tools:**
- Google Analytics
- New Relic
- Datadog
- Google PageSpeed Insights
- Lighthouse

---

## ✅ E-commerce Testing Quick Reference

### Pre-Testing Checklist

```
□ Test environment ready
□ Test data prepared
□ Payment gateway test credentials
□ Multiple test accounts
□ Test devices ready
□ Performance tools configured
□ Security tools ready
□ Monitoring dashboards set up
```

### Critical Test Areas

```
Priority 1 (Must Test):
□ Checkout flow
□ Payment processing
□ Order creation
□ Inventory sync
□ Security (auth, payment, data)

Priority 2 (Should Test):
□ Search functionality
□ Cart operations
□ Order tracking
□ Returns/Refunds
□ Email/SMS notifications

Priority 3 (Nice to Test):
□ Recommendations
□ Reviews
□ Loyalty program
□ Social sharing
□ Wishlist
```

### Common Issue Patterns

```
High Frequency Issues:
- Cart calculation errors
- Payment timeouts
- Inventory sync delays
- Email delivery failures
- Mobile responsiveness

Medium Frequency Issues:
- Coupon validation
- Address validation
- Shipping calculation
- Search relevance
- Image loading

Low Frequency but High Impact:
- Security vulnerabilities
- Data breaches
- Payment fraud
- Overselling
- Privacy violations
```

---

## 📊 E-commerce Testing Summary

### Key Takeaways

```
✅ E-commerce testing requires comprehensive coverage
✅ Payment testing is most critical
✅ Security cannot be compromised
✅ Performance during sales is crucial
✅ Mobile experience is equally important
✅ Inventory sync prevents major issues
✅ Customer communication is key
✅ Monitoring helps quick issue detection
```

### Career Advice for E-commerce Testers

```
📌 Learn payment gateway integrations
📌 Understand PCI DSS requirements
📌 Practice performance testing
📌 Master security testing basics
📌 Get familiar with e-commerce platforms
📌 Stay updated with payment trends
📌 Build expertise in fraud detection
📌 Learn about international e-commerce
```

---

*E-commerce Domain Testing Module*  
*For QA Professionals & Aspirants*  
*Language: Hinglish (Hindi + English)*  
*Created: 2026*

**Happy Testing! 🛒✅**
