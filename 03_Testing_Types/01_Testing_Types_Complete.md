# 03_Testing_Types

## Manual Testing के विभिन्न प्रकार को गहराई से समझो
### Complete Guide to Different Types of Testing

---

## 📚 Overview

Testing के **50+ types** हैं, लेकिन हम manual testing के लिए सबसे common types पर focus करेंगे:

```
Main Categories:
├── FUNCTIONAL TESTING (सब कुछ काम करता है?)
├── NON-FUNCTIONAL TESTING (कैसे काम करता है?)
├── MAINTENANCE TESTING (Changes के बाद ok है?)
├── SPECIALTY TESTING (Specific needs के लिए)
└── BUSINESS TESTING (Business rules follow हो रहे हैं?)
```

---

## 🎯 Functional Testing

### मतलब: क्या software वह करता है जो करना चाहिए?

#### **1. Smoke Testing** 🚬

```
Definition:
"नया build मिलने के बाद, basic functionality check करना।"

Scope:
- सिर्फ CRITICAL features
- Surface-level testing
- Quick checks

Duration:
30 minutes to 2 hours

When:
- हर नया build मिले
- Deployment से पहले

How:
✓ Application launch हो?
✓ Login काम करता है?
✓ Basic navigation ok?
✓ कोई obvious crash तो नहीं?

If FAILS:
- Build reject करो
- Dev को भेज दो
- Full testing न करो

If PASSES:
- Full testing proceed करो

Real Example:
Amazon का नया version release हुआ।
QA first 1 hour में:
- Site load होती है? ✓
- Search काम करता है? ✓
- Cart add/remove काम करता है? ✓
- Checkout starts? ✓

अगर कोई fail हो, तो सब testing hold।
```

#### **2. Functional Testing** 🎮

```
Definition:
"सब features को detail में test करना कि वो expected तरीके से काम करते हैं।"

Scope:
- सभी features
- Expected behaviors
- User workflows

Duration:
Days to Weeks

What We Check:
✓ सब buttons काम करते हैं?
✓ Forms submit होते हैं?
✓ Data correctly save होता है?
✓ Navigation flows काम करते हैं?
✓ Business logic correct है?
✓ Edge cases handle हो रहे हैं?

Test Case Example:
Test: User को profile update करना चाहिए

Steps:
1. Login करो
2. Go to profile
3. Update name
4. Change email
5. Upload profile picture
6. Save changes
7. Logout
8. Re-login
9. Verify data saved

Expected: सब data correctly save होना चाहिए

Real Example:
Instagram का new feature: Reels

Functional tests:
✓ Reels upload हो सकते हैं?
✓ Editing features काम करते हैं?
✓ Effects apply होते हैं?
✓ Music add हो सकता है?
✓ Share हो सकते हैं?
✓ Like/comment काम करते हैं?
✓ Views update हो रहे हैं?
```

#### **3. Regression Testing** 🔄

```
Definition:
"Previous functionality को verify करना कि नए changes से break न हो गई।"

When:
- नई features add होने के बाद
- Bug fixes के बाद
- Performance improvements के बाद

Scope:
- सभी existing features
- Previously working functionality
- Critical paths

Process:
1. डिफाइन करो क्या test करना है (smoke + important paths)
2. Execute करो सब tests
3. Report करो results

Real Example:
Online shopping website में:

Release 1:
- User can add items to cart ✓
- User can checkout ✓
- Payment works ✓

Release 2:
नया feature: "Wishlist"

Regression Testing में:
- सब पुराने features अभी भी काम करते हैं?
- Wishlist new feature काम करता है?
- कोई side effects?

Test Case:
पुराना: Add to cart
नया: Add to wishlist

दोनों काम करने चाहिए।
कोई feature दूसरे को affect न करे।

Timeline: Usually 3-5 days per cycle
```

#### **4. Sanity Testing** 🧪

```
Definition:
"Build की basic sanity को verify करना।"

Difference from Smoke Testing:
- Smoke = हर नए build में
- Sanity = Bug fix के बाद

When:
- Build को accept करने से पहले
- Minor changes के बाद
- Quick verification के लिए

Duration:
30 minutes to 1 hour

Scope:
- Specific area (जहाँ changes हैं)
- Related features

Real Example:
Login feature में bug था:
"User को premium login page दिख रहा था"

Fix:
Developer ने condition change की।

Sanity Test (QA):
1. पहले premium login दिखना चाहिए? ✗
2. अब normal login दिखना चाहिए? ✓
3. अब bug fixed है?

अगर yes, तो full regression test proceed करो।

यह basic sanity check था।
```

#### **5. Exploratory Testing** 🔍

```
Definition:
"बिना predefined test cases के freely testing करना।"

Approach:
- Plan करते हुए execute करना
- उसी समय learn करते हुए test करना
- Creativity को freedom देना

Duration:
1-2 hours continuous

Who Does:
- Senior testers
- Experience वाले testers
- Product experts

How:
1. Application को deeply explore करो
2. "क्या होगा अगर..." सवाल पूछो
3. Unusual scenarios try करो
4. Hidden bugs खोजो

Example:
Gmail का exploratory test:

Tester सोचता है:
"क्या होगा अगर:
- मैं 1000 emails एक साथ delete करूँ?
- My storage limit exceed हो जाए?
- मैं offline mode में काम करूँ?
- मैं slow internet पर use करूँ?
- Attachment की size बहुत बड़ी हो?
- मैं special characters use करूँ?
"

और test करता है!

Benefits:
✓ Unexpected bugs मिलते हैं
✓ Creative testing
✓ Real-world scenarios
✓ Best bugs खोजता है

Real Story:
Facebook में एक tester ने exploratory testing में:
पाया कि अगर username में emoji use करो,
तो notification fail हो जाते हैं।

यह bug production में नहीं पकड़ा गया होता!
```

---

## 📊 Non-Functional Testing

### मतलब: कैसे काम करता है? (Quality attributes)

#### **1. Performance Testing** ⚡

```
Definition:
"Application कितनी तेजी से respond करता है?"

मापते हैं:
✓ Page Load Time (कितने seconds में खुलता है?)
✓ Response Time (एक request का जवाब कितने में आता है?)
✓ Throughput (कितने requests/sec handle कर सकता है?)
✓ Resource Utilization (CPU/Memory कितना use हो रहा है?)

Example:
Amazon पर एक product search:
- Load हो सकता है 2 seconds में?
- Results display 1 second में?
- Acceptable होना चाहिए 80% users के लिए

Tools:
- Postman (API performance)
- LoadRunner (Heavy load testing)
- JMeter (Performance testing)
- WebDriver (Selenium based)

Real Scenario:
Black Friday Sale पर Amazon:
- 100k users एक साथ access करें
- सब को 2 second में load होना चाहिए
- कोई crash नहीं

अगर Performance issue हो, तो:
"Add to cart" delay हो, customers गुस्से में!

Testers Check करते हैं:
- High traffic में क्या होता है?
- Database query कितनी देर में?
- Server response कैसा है?
```

#### **2. Load Testing** 📊

```
Definition:
"System कितने users/load को handle कर सकता है?"

मापते हैं:
- Normal load पर performance
- Peak load पर performance
- Breaking point कहाँ है?

Example:
Office में 100 employees हैं।
सब एक साथ salary slip download करें:
- Server crash हो जाए? ❌
- Slow हो जाए? (but working) ⚠️
- Fast और smooth? ✓

Test:
100 concurrent requests भेजो
→ सब successful होने चाहिए

Load Testing Steps:
1. 10 users simultaneously
2. 50 users simultaneously
3. 100 users simultaneously
4. 200 users simultaneously
5. 500 users simultaneously
...जब तक break न हो जाए

Acceptable Level:
Peak users के load को handle कर सके।

Business Impact:
अगर Black Friday पर crash हो,
तो लाखों का loss!
```

#### **3. Stress Testing** 💥

```
Definition:
"System कितने ज्यादा load को handle कर सकता है?"

Load Testing से difference:
- Load Testing = Normal + Peak load
- Stress Testing = Breaking point तक

How:
continuously load बढ़ाते जाओ:
100 users → 500 users → 1000 users → 5000 users → ...
जब तक system break न हो जाए

क्या चेक करते हैं:
✓ At what point does it break?
✓ क्या error messages आ रहे हैं?
✓ Recovery time कितनी है?
✓ Data loss तो नहीं हुआ?

Real Example:
Twitter trend हो जाता है:
Suddenly 10x normal traffic!

Stress Testing में:
सब कुछ बर्दाश्त करना चाहिए।

अगर Twitter crash हो, तो:
- Users गुस्से में
- Reputation damage
- Competitors को advantage
```

#### **4. Usability Testing** 👤

```
Definition:
"Application use करना कितना आसान है?"

मापते हैं:
✓ क्या समझ आ जाता है?
✓ सीखना आसान है?
✓ Navigation intuitive है?
✓ Experienced users के लिए efficient है?
✓ Accessibility अच्छी है?

Who Does:
- User Experience testers
- Real users (sometimes)
- Accessibility testers

Example:
Banking App का usability test:

Test Case 1: Money Transfer
Step: "Money transfer करो अपने friend को"
Expected: User को easily transfer कर सकना चाहिए

Observation:
- User को 5 clicks लगे (Good)
- User को clear instructions मिले (Good)
- Button labels clear थे (Good)
- Process समझने में 2 minutes लगे (Good)

अगर:
- 10 clicks लगें ✗
- Instructions confusing हों ✗
- Button labels unclear हों ✗
- 10 minutes लगे ✗

तो Usability issue है!

Real Feedback:
"मुझे नहीं समझ आया कि बेनिफिशियरी add कब करूँ?"
→ Button label change करो: "Add New Beneficiary"
```

#### **5. Security Testing** 🔐

```
Definition:
"क्या data और system secure हैं?"

मापते हैं:
✓ Authentication काम करता है?
✓ Authorization सही है?
✓ SQL injection से protect है?
✓ Cross-site scripting (XSS) से protect है?
✓ Password encrypted है?
✓ Data at-rest और in-transit encrypted है?

Example Hacks:
1. SQL Injection
   Input: '; DROP TABLE users; --
   Bad: Database delete हो जाता है
   Good: Input sanitized होना चाहिए

2. XSS Attack
   Script: <script>alert('hacked')</script>
   Bad: Script execute हो जाता है
   Good: Script block होना चाहिए

3. Weak Password
   123456, password, admin
   Bad: आसानी से crack हो जाते हैं
   Good: Strong password policy

Manual Security Testing:
- Try करो invalid inputs
- Try करो malicious code
- Try करो direct URL manipulation
- Try करो unauthorized access

Real Example:
Facebook में एक vulnerability:
Private photos को public link से access कर सकते थे।

Security Testing में:
यह issue catch होता था।

जरूरी है:
- API security
- Data encryption
- Access control
- Secure password handling
```

#### **6. Compatibility Testing** 🌐

```
Definition:
"Application सभी platforms/browsers/devices में काम करता है?"

Devices:
- Desktop (Windows, Mac, Linux)
- Mobile (iOS, Android)
- Tablets

Browsers:
- Chrome
- Firefox
- Safari
- Edge
- Internet Explorer (legacy)

OS Versions:
- Windows 10, 11
- macOS 10, 11, 12
- Android 10, 11, 12, 13, 14
- iOS 14, 15, 16

Example:
Website को test करना:
1. Windows 10 + Chrome ✓
2. Windows 11 + Edge ✓
3. Mac + Safari ✓
4. Ubuntu + Firefox ✓
5. iPhone + Safari ✓
6. Android + Chrome ✓

अगर एक browser में issue हो:
"Safari में checkout button काम नहीं कर रहा"
→ Browser-specific CSS/JavaScript issue
→ Fix करना होगा

Tools:
- BrowserStack (Multiple devices)
- CrossBrowserTesting
- Virtual machines

Real Challenge:
Internet Explorer का code कभी-कभी अलग तरीके से काम करता है।
सब browsers में same behavior चाहिए।
```

---

## 🔄 Maintenance Testing

#### **1. Bug Fix Testing (Retesting)**

```
Definition:
"Bug को fix करने के बाद verify करना।"

Process:
Bug Report मिलता है → Developer fix करता है → 
QA retest करता है

Status Options:
✓ VERIFIED - Bug fixed है
✗ NOT FIXED - Bug अभी है
⚠️ PARTIALLY FIXED - आधा fix हुआ
? UNABLE TO REPRODUCE - फिर से नहीं आ सका

Real Example:
Bug: "Login में गलत email accept हो रहा है"
Expected: केवल valid email accept होना चाहिए

Retest करते हो:
✓ abc@gmail.com - PASS
✗ abc.com (no @) - FAIL (अभी भी बुरा)
✗ abc@ - FAIL (अभी भी बुरा)

Report: "Bug NOT FIXED"
Developer को फिर से भेज दो।
```

#### **2. Patch Testing**

```
Definition:
"Security patch या bug fix release को test करना।"

Emergency fix के लिए quick testing।

Process:
1. Patch apply करो
2. सभी critical functionality check करो
3. Patch specific fixes verify करो
4. No regressions हैं?
5. Sign-off दो

Timeline: Usually 1-2 days
```

---

## 🎯 Specialty Testing

#### **1. End-to-End Testing** 🔗

```
Definition:
"Complete user workflow को test करना start से end तक।"

Example: Online Shopping

E2E Flow:
User Login → Search Product → Apply Filter → 
Add to Cart → Apply Coupon → Checkout → 
Payment → Order Confirmation → Track Order

सब steps एक साथ काम करने चाहिए।

अगर एक step fail हो:
पूरा flow fail है।

टेस्ट किया:
1. Valid user, valid product, valid coupon,
   valid payment → Success ✓

2. Invalid coupon, सही otherwise → Reject coupon message ✓

3. Payment fail, retry करो → Retry work करे ✓

Real Importance:
Individual features अलग-अलग काम करें
पर E2E में problem हो सकता है।
```

#### **2. Production Testing (Live Testing)**

```
Definition:
"Production environment में testing करना।"

Limited Testing (सावधानी से!):
✓ Basic functionality verify करना
✓ Data integrity check करना
✓ Performance actual users के साथ
✓ Critical bugs catch करना

Risk:
अगर कुछ गलत हो तो real users affect होंगे।

इसलिए:
- Experienced testers करते हैं
- Read-only operations
- Small data sets
- Guided explicitly

Real Example:
कोई issue production में दिख रहा है।
QA को test करना है live environment में।

Steps:
1. पहले staging में reproduce करो
2. फिर production में verify करो (carefully!)
3. Issue log करो
4. Development को दो
```

---

## 📋 Testing Comparison Chart

```
Type              When              Duration    Scope
────────────────────────────────────────────────────
Smoke             हर build         30 min-1h   Critical paths
Functional        Features ready   Days-weeks  All features
Regression        After changes    Days-weeks  All affected
Sanity            Quick verify      30-60 min   Specific area
Exploratory       Anytime          1-2 hours   Creative
Performance       Before release   1-2 weeks   Load handling
Security          Before release   1-2 weeks   Vulnerabilities
Usability         Release time     1-2 weeks   User experience
E2E               Before release   Days-weeks  Complete flow
```

---

## 🎯 Interview Questions

#### **Q1: Smoke vs Sanity Testing में क्या फर्क है?**

```
Answer:
Smoke Testing:
- हर नए build में
- Surface-level check
- 30 min to 1 hour
- Build reject करने के लिए

Sanity Testing:
- Bug fix के बाद
- Specific area check
- 30-60 minutes
- Build accept करने के लिए

आसान भाषा में:
Smoke = "क्या app launch होता है?"
Sanity = "क्या fix काम कर गया?"
```

#### **Q2: Performance Testing में क्या चेक करते हो?**

```
Answer:
✓ Page load time
✓ Response time
✓ Throughput
✓ Resource usage (CPU/Memory)
✓ Concurrent users handling
✓ Breaking point
✓ Behavior under stress

Tools का use करते हो:
- Postman
- JMeter
- LoadRunner
```

#### **Q3: Exploratory Testing क्यों जरूरी है?**

```
Answer:
"Exploratory testing में:
- बिना predefined cases के freely test करते हो
- Creative scenarios सोच सकते हो
- Hidden bugs find कर सकते हो
- Real-world usage simulate कर सकते हो

Planned testing सब typical cases cover करती है।
लेकिन users unusual तरीकों से use करते हैं।

Exploratory में वो unusual scenarios catch होते हैं।
सबसे महत्वपूर्ण bugs यहीं मिलते हैं।"
```

---

## 🎯 Key Takeaways

```
✓ 50+ types of testing हैं
✓ Manual testing में commonly use होने वाले types सीखे
✓ Functional = क्या काम करता है
✓ Non-functional = कैसे काम करता है
✓ सब types important हैं
✓ Different scenarios के लिए different types
```

---

## 📚 Next Steps

अब तुम समझ गए:
- ✓ Testing के different types
- ✓ कब कौन सा type use होता है
- ✓ हर type की importance

अगला: 📖 **04_Test_Case_Design_Techniques** - अब test cases लिखना सीखेंगे!

---

*Created: 2026*  
*Level: Beginner*  
*Language: Hinglish*
