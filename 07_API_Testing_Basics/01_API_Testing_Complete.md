# Module 07: API Testing Basics

## API Testing Complete Guide - Manual Tester के लिए

**Last Updated:** January 2026  
**Reading Time:** 2.5 hours  
**Level:** Intermediate

---

## 📋 Table of Contents

1. [What is API?](#what-is-api)
2. [REST vs SOAP](#rest-vs-soap)
3. [HTTP Methods & Status Codes](#http-methods)
4. [Postman Setup & Tutorial](#postman-tutorial)
5. [API Test Cases Design](#api-test-cases)
6. [Request/Response Validation](#validation)
7. [Error Handling in APIs](#error-handling)
8. [Real API Testing Scenarios](#real-scenarios)
9. [API Testing Best Practices](#best-practices)
10. [20+ Interview Questions](#interview-questions)

---

## <a name="what-is-api"></a>What is API?

### API क्या है? Simple Language में

**API = Application Programming Interface**

**Simple Definition:**
```
API एक MIDDLEMAN है जो दो software applications के बीच 
बातचीत कराता है।
```

### Real World Example

```
RESTAURANT EXAMPLE:

You (Customer) → Menu Order → WAITER → Kitchen → Food
                    ↑
                  API (Waiter)

YOU = Frontend/UI
KITCHEN = Backend/Server
WAITER = API (jo order leta hai aur food lata hai)
```

### Technical Definition

```
API एक set of rules और protocols है जो:
├─ Define करता है कैसे communicate करना है
├─ Data format specify करता है
├─ Actions define करता है
└─ Security ensure करता है
```

### API Testing क्यों जरूरी है?

```
WITHOUT API TESTING:
✗ Backend bugs production में जा सकते हैं
✗ Data corruption हो सकता है
✗ Security vulnerabilities रह सकते हैं
✗ Performance issues miss हो सकते हैं

WITH API TESTING:
✓ Early bug detection
✓ Security validation
✓ Performance verification
✓ Data integrity check
✓ Integration confidence
```

### API Testing vs UI Testing

```
┌────────────────────────────────────────────────────────────┐
│              API TESTING vs UI TESTING                     │
├────────────────────────────────────────────────────────────┤
│ Aspect          │ API Testing        │ UI Testing          │
├────────────────────────────────────────────────────────────┤
│ Layer           │ Business Logic     │ User Interface      │
│ Speed           │ Fast               │ Slow                │
│ Coverage        │ Deep (backend)     │ Surface (frontend)  │
│ Early Testing   │ Possible           │ Late (after UI)     │
│ Cost            │ Low                │ High                │
│ Automation      │ Easy               │ Complex             │
│ Tools           │ Postman, curl      │ Selenium, Cypress   │
└────────────────────────────────────────────────────────────┘
```

---

## <a name="rest-vs-soap"></a>REST vs SOAP

### Overview

```
दोनों API architectures हैं, लेकिन अलग approaches के साथ:

SOAP (Simple Object Access Protocol)
└─ Old, strict protocol
└─ XML only
└─ Built-in security

REST (Representational State Transfer)
└─ Modern, flexible architecture
└─ Multiple formats (JSON, XML, Text)
└─ Lightweight
```

### Detailed Comparison

```
┌──────────────────────────────────────────────────────────────┐
│                  SOAP vs REST                                │
├──────────────────────────────────────────────────────────────┤
│ Feature          │ SOAP              │ REST                  │
├──────────────────────────────────────────────────────────────┤
│ Full Form        │ Simple Object     │ Representational      │
│                  │ Access Protocol   │ State Transfer        │
├──────────────────────────────────────────────────────────────┤
│ Type             │ Protocol          │ Architectural Style   │
├──────────────────────────────────────────────────────────────┤
│ Data Format      │ XML only          │ JSON, XML, Text, HTML │
├──────────────────────────────────────────────────────────────┤
│ Security         │ WS-Security       │ SSL/TLS, OAuth        │
├──────────────────────────────────────────────────────────────┤
│ Speed            │ Slow (heavy)      │ Fast (lightweight)    │
├──────────────────────────────────────────────────────────────┤
│ Caching          │ Not supported     │ Supported             │
├──────────────────────────────────────────────────────────────┤
│ State            │ Stateful          │ Stateless             │
├──────────────────────────────────────────────────────────────┤
│ Usage            │ Banking, Finance  │ Web, Mobile Apps      │
├──────────────────────────────────────────────────────────────┤
│ Learning Curve   │ Steep             │ Easy                  │
└──────────────────────────────────────────────────────────────┘
```

### SOAP Example

```xml
SOAP REQUEST (XML format):
┌─────────────────────────────────────────────────────────┐
│ <?xml version="1.0" encoding="UTF-8"?>                  │
│ <soap:Envelope xmlns:soap="http://www.w3.org/2003/05/   │
│   soap-envelope">                                       │
│   <soap:Header/>                                        │
│   <soap:Body>                                           │
│     <LoginRequest>                                      │
│       <Username>john@example.com</Username>             │
│       <Password>secret123</Password>                    │
│     </LoginRequest>                                     │
│   </soap:Body>                                          │
│ </soap:Envelope>                                        │
└─────────────────────────────────────────────────────────┘

SOAP RESPONSE:
┌─────────────────────────────────────────────────────────┐
│ <?xml version="1.0" encoding="UTF-8"?>                  │
│ <soap:Envelope>                                         │
│   <soap:Body>                                           │
│     <LoginResponse>                                     │
│       <Status>Success</Status>                          │
│       <Token>abc123xyz</Token>                          │
│     </LoginResponse>                                    │
│   </soap:Body>                                          │
│ </soap:Envelope>                                        │
└─────────────────────────────────────────────────────────┘
```

### REST Example

```json
REST REQUEST (JSON format):
┌─────────────────────────────────────────────────────────┐
│ POST https://api.example.com/login                      │
│ Content-Type: application/json                          │
│                                                         │
│ {                                                       │
│   "email": "john@example.com",                          │
│   "password": "secret123"                               │
│ }                                                       │
└─────────────────────────────────────────────────────────┘

REST RESPONSE:
┌─────────────────────────────────────────────────────────┐
│ HTTP/1.1 200 OK                                         │
│ Content-Type: application/json                          │
│                                                         │
│ {                                                       │
│   "status": "success",                                  │
│   "token": "abc123xyz",                                 │
│   "user": {                                             │
│     "id": 123,                                          │
│     "name": "John Doe"                                  │
│   }                                                     │
│ }                                                       │
└─────────────────────────────────────────────────────────┘
```

### When to Use What?

```
USE SOAP WHEN:
✓ Banking/Financial transactions
✓ High security requirements
✓ ACID transactions needed
✓ Enterprise systems integration
✓ Government projects

USE REST WHEN:
✓ Web/Mobile applications
✓ Public APIs
✓ Performance important है
✓ Multiple client types
✓ Cloud-based services
✓ Quick development needed
```

---

## <a name="http-methods"></a>HTTP Methods & Status Codes

### HTTP Methods (Verbs)

```
┌────────────────────────────────────────────────────────────┐
│                    HTTP METHODS                            │
├────────────────────────────────────────────────────────────┤
│ Method   │ Purpose              │ Example                 │
├────────────────────────────────────────────────────────────┤
│ GET      │ Data retrieve        │ Get user list           │
│ POST     │ Data create          │ Create new user         │
│ PUT      │ Data replace (full)  │ Update entire user      │
│ PATCH    │ Data update (partial)│ Update user email only  │
│ DELETE   │ Data delete          │ Delete user             │
│ HEAD     │ Headers only         │ Check if resource exists│
│ OPTIONS  │ Get supported methods│ Get API capabilities    │
└────────────────────────────────────────────────────────────┘
```

### HTTP Methods Visual

```
CRUD OPERATIONS MAPPING:

    CREATE          READ           UPDATE          DELETE
      │              │               │                │
      ▼              ▼               ▼                ▼
   ┌─────┐       ┌─────┐         ┌─────┐         ┌─────┐
   │POST │       │ GET │         │ PUT │         │DELTE│
   └─────┘       └─────┘         │PATCH│         └─────┘
                                 └─────┘

Example: User Management

POST /users          → Create new user
GET /users           → Get all users
GET /users/123       → Get user with ID 123
PUT /users/123       → Update user 123 (full)
PATCH /users/123     → Update user 123 (partial)
DELETE /users/123    → Delete user 123
```

### HTTP Status Codes

```
┌────────────────────────────────────────────────────────────┐
│              HTTP STATUS CODES (Complete Guide)            │
├────────────────────────────────────────────────────────────┤
│ Code Range │ Category        │ Meaning                    │
├────────────────────────────────────────────────────────────┤
│ 1xx        │ Informational   │ Request received, continue │
│ 2xx        │ Success         │ Request successful         │
│ 3xx        │ Redirection     │ Further action needed      │
│ 4xx        │ Client Error    │ Request error (your fault) │
│ 5xx        │ Server Error    │ Server error (their fault) │
└────────────────────────────────────────────────────────────┘
```

### Common Status Codes Detail

```
2xx SUCCESS CODES:
┌───────────────────────────────────────────────────────────┐
│ 200 OK                                                    │
│    → Request successful                                   │
│    → GET: Data returned                                   │
│    → PUT/PATCH: Updated data returned                     │
├───────────────────────────────────────────────────────────┤
│ 201 Created                                               │
│    → Resource successfully created                        │
│    → POST के बाद आता है                                   │
│    → Location header में new resource URL                 │
├───────────────────────────────────────────────────────────┤
│ 204 No Content                                            │
│    → Success but nothing to return                        │
│    → DELETE के बाद आता है                                 │
└───────────────────────────────────────────────────────────┘

3xx REDIRECTION CODES:
┌───────────────────────────────────────────────────────────┐
│ 301 Moved Permanently                                     │
│    → Resource permanently moved                           │
│    → New URL Location header में                          │
├───────────────────────────────────────────────────────────┤
│ 304 Not Modified                                          │
│    → Resource unchanged (use cached version)              │
│    → GET requests में                                     │
└───────────────────────────────────────────────────────────┘

4xx CLIENT ERROR CODES:
┌───────────────────────────────────────────────────────────┐
│ 400 Bad Request                                           │
│    → Invalid syntax                                       │
│    → Missing required fields                              │
│    → Invalid data format                                  │
├───────────────────────────────────────────────────────────┤
│ 401 Unauthorized                                          │
│    → Authentication required                              │
│    → Token missing या expired                             │
│    → Login needed                                         │
├───────────────────────────────────────────────────────────┤
│ 403 Forbidden                                             │
│    → Authenticated but no permission                      │
│    → Admin-only resource, normal user access कर रहा है   │
├───────────────────────────────────────────────────────────┤
│ 404 Not Found                                             │
│    → Resource doesn't exist                               │
│    → Wrong URL या deleted resource                        │
├───────────────────────────────────────────────────────────┤
│ 405 Method Not Allowed                                    │
│    → HTTP method supported नहीं है                        │
│    → GET किया जहाँ POST चाहिए था                         │
├───────────────────────────────────────────────────────────┤
│ 409 Conflict                                              │
│    → Resource conflict                                    │
│    → Duplicate entry, version mismatch                    │
├───────────────────────────────────────────────────────────┤
│ 422 Unprocessable Entity                                  │
│    → Valid syntax but semantic errors                     │
│    → Email format सही है पर already exists               │
└───────────────────────────────────────────────────────────┘

5xx SERVER ERROR CODES:
┌───────────────────────────────────────────────────────────┐
│ 500 Internal Server Error                                 │
│    → Generic server error                                 │
│    → Code crash, unhandled exception                      │
├───────────────────────────────────────────────────────────┤
│ 502 Bad Gateway                                           │
│    → Upstream server invalid response                     │
│    → Proxy/Load balancer issue                            │
├───────────────────────────────────────────────────────────┤
│ 503 Service Unavailable                                   │
│    → Server overloaded या down                            │
│    → Maintenance mode                                     │
├───────────────────────────────────────────────────────────┤
│ 504 Gateway Timeout                                       │
│    → Upstream server didn't respond                       │
│    → Timeout हो गया                                       │
└───────────────────────────────────────────────────────────┘
```

### Status Code Memory Trick

```
200 OK          → "Sab theek" ✅
201 Created     → "Ban gaya" ✨
204 No Content  → "Mita diya, kuch नहीं बचा" 🗑️

301 Moved       → "Shift हो गया" 🏠
304 Not Modified→ "Wahi पुराना है" 📦

400 Bad Request → "तुमसे गलती हुई" 👈
401 Unauthorized→ "Login कर, फिर आ" 🔐
403 Forbidden   → "तुम्हारी permission नहीं" 🚫
404 Not Found   → "मिला नहीं" 🔍
409 Conflict    → "टकराव हो गया" 💥

500 Server Error→ "Server का दोष" 🖥️
503 Unavailable → "बंद है, आओ मत" 🛑
```

---

## <a name="postman-tutorial"></a>Postman Setup & Tutorial

### Postman क्या है?

```
Postman = API testing का सबसे popular tool

Features:
✓ API requests send करना
✓ Responses view करना
✓ Test cases automate करना
✓ Collections organize करना
✓ Environment variables manage करना
✓ Documentation generate करना
✓ Team collaboration
```

### Installation & Setup

```
STEP 1: Download
└─ www.postman.com/downloads
└─ Free version download करो
└─ Install करो

STEP 2: Create Account (Optional but recommended)
└─ Sign up करो (free)
└─ Collections sync हो जाएंगे

STEP 3: First Request
└─ New → HTTP Request
└─ URL डालो
└─ Method select करो
└─ Send click करो
```

### Postman Interface

```
┌────────────────────────────────────────────────────────────┐
│                    POSTMAN INTERFACE                       │
├────────────────────────────────────────────────────────────┤
│                                                          │
│  [New] [Collections] [Environments] [API]                │
│     │                                                  │
│  ┌──────────────────────────────────────────────────┐   │
│  │ GET │ https://jsonplaceholder.typicode.com/users │🚀│   │
│  └──────────────────────────────────────────────────┘   │
│                                                          │
│  [Params] [Authorization] [Headers] [Body] [Pre-request]│
│     │                                                    │
│  Response Body:                                          │
│  ┌──────────────────────────────────────────────────┐   │
│  │ [                                                 │   │
│  │   { "id": 1, "name": "John Doe", ... },          │   │
│  │   { "id": 2, "name": "Jane Smith", ... }         │   │
│  │ ]                                                 │   │
│  └──────────────────────────────────────────────────┘   │
│                                                          │
│  Status: 200 OK │ Time: 245ms │ Size: 1.2KB            │
└────────────────────────────────────────────────────────────┘
```

### Postman में API Testing - Step by Step

#### Step 1: GET Request

```
1. New Request बनाओ
2. Method: GET select करो
3. URL: https://jsonplaceholder.typicode.com/users
4. Send click करो
5. Response देखो

Expected Response:
{
  "id": 1,
  "name": "Leanne Graham",
  "username": "Bret",
  "email": "Sincere@april.biz"
  ...
}
```

#### Step 2: POST Request

```
1. New Request बनाओ
2. Method: POST select करो
3. URL: https://jsonplaceholder.typicode.com/users
4. Body tab → raw → JSON select करो
5. JSON body डालो:

{
  "name": "Himanshu",
  "username": "himal",
  "email": "himal@example.com"
}

6. Send click करो
7. Response में 201 Created देखो
```

#### Step 3: PUT/PATCH Request

```
PUT (Full Update):
1. Method: PUT
2. URL: https://jsonplaceholder.typicode.com/users/1
3. Body:

{
  "id": 1,
  "name": "Himanshu Updated",
  "username": "himal_updated",
  "email": "himal.updated@example.com"
}

PATCH (Partial Update):
1. Method: PATCH
2. URL: https://jsonplaceholder.typicode.com/users/1
3. Body (only change name):

{
  "name": "Himanshu Only Name Changed"
}
```

#### Step 4: DELETE Request

```
1. Method: DELETE
2. URL: https://jsonplaceholder.typicode.com/users/1
3. Send click करो
4. Response में 200 या 204 देखो
```

### Collections बनाना

```
Collections = Related requests को group करना

CREATE COLLECTION:
1. Collections tab → New Collection
2. Name: "User Management API"
3. Description: "All user-related APIs"
4. Add requests:
   ├─ GET /users
   ├─ POST /users
   ├─ GET /users/:id
   ├─ PUT /users/:id
   └─ DELETE /users/:id

BENEFITS:
✓ Organized रहते हैं
✓ Share कर सकते हैं
✓ Run entire collection सकते हैं
```

### Environment Variables

```
Environments = Different setups के लिए variables

Example:
┌─────────────────────────────────────────────┐
│ LOCAL Environment       │ QA Environment   │
├─────────────────────────────────────────────┤
│ baseUrl = localhost:3000│ baseUrl = qa.api │
│ token = local_token     │ token = qa_token │
└─────────────────────────────────────────────┘

USE IN REQUEST:
{{baseUrl}}/users/{{userId}}

BENEFIT:
एक ही request, different environments में चला सकता है
```

### Writing Tests in Postman

```
Tests Tab में JavaScript लिख सकते हैं:

TEST 1: Status code check
┌─────────────────────────────────────────────┐
│ pm.test("Status code is 200", function () { │
│     pm.response.to.have.status(200);        │
│ });                                         │
└─────────────────────────────────────────────┘

TEST 2: Response time check
┌─────────────────────────────────────────────┐
│ pm.test("Response time < 500ms", function()│
│     pm.expect(pm.response.responseTime)     │
│       .to.be.below(500);                    │
│ });                                         │
└─────────────────────────────────────────────┘

TEST 3: Response body validation
┌─────────────────────────────────────────────┐
│ pm.test("Response has user data", function(){│
│     var jsonData = pm.response.json();      │
│     pm.expect(jsonData.name).to.exist;      │
│     pm.expect(jsonData.email).to.exist;     │
│ });                                         │
└─────────────────────────────────────────────┘

TEST 4: Multiple validations
┌─────────────────────────────────────────────┐
│ pm.test("User structure validation", () => {│
│     const response = pm.response.json();    │
│     pm.expect(response).to.have.property(   │
│       "id");                                │
│     pm.expect(response).to.have.property(   │
│       "name");                              │
│     pm.expect(response).to.have.property(   │
│       "email");                             │
│     pm.expect(response.email).to.include(   │
│       "@");                                 │
│ });                                         │
└─────────────────────────────────────────────┘
```

### Collection Runner

```
RUN ENTIRE COLLECTION:
1. Collection पे right-click
2. Run Collection
3. Iterations set करो
4. Delay set करो
5. Run click करो

RESULT:
├─ Total requests run
├─ Passed/Failed count
├─ Response time stats
└─ Detailed test results
```

---

## <a name="api-test-cases"></a>API Test Cases Design

### API Test Case Template

```
┌────────────────────────────────────────────────────────────┐
│                 API TEST CASE TEMPLATE                     │
├────────────────────────────────────────────────────────────┤
│ Test Case ID: API_TC_001                                  │
│ API Endpoint: POST /api/users                             │
│ Description: Create new user with valid data              │
│                                                           │
│ Pre-conditions:                                           │
│ - API server is running                                   │
│ - Authentication token available                          │
│                                                           │
│ Test Data:                                                │
│ {                                                         │
│   "name": "John Doe",                                     │
│   "email": "john@example.com",                            │
│   "role": "user"                                          │
│ }                                                         │
│                                                           │
│ Steps:                                                    │
│ 1. Send POST request to /api/users                        │
│ 2. Set Content-Type: application/json                     │
│ 3. Set Authorization: Bearer {{token}}                    │
│ 4. Send request body                                      │
│                                                           │
│ Expected Result:                                          │
│ - Status Code: 201 Created                                │
│ - Response contains user ID                               │
│ - Response contains submitted data                        │
│ - Email format validated                                  │
│                                                           │
│ Actual Result: [To be filled]                             │
│ Status: Pass/Fail                                         │
└────────────────────────────────────────────────────────────┘
```

### API Test Case Types

```
1. POSITIVE TEST CASES
   └─ Valid data के साथ successful requests

2. NEGATIVE TEST CASES
   └─ Invalid data के साथ error handling

3. BOUNDARY TEST CASES
   └─ Minimum/maximum values test

4. SECURITY TEST CASES
   └─ Authentication, authorization, injection

5. PERFORMANCE TEST CASES
   └─ Response time, load testing
```

### Complete API Test Suite Example

```
API: User Management (CRUD)

┌────────────────────────────────────────────────────────────┐
│ POSITIVE TEST CASES (Happy Path)                          │
├────────────────────────────────────────────────────────────┤
│ TC001: Create user with valid data → 201 Created          │
│ TC002: Get all users → 200 OK + user list                 │
│ TC003: Get user by ID → 200 OK + user data                │
│ TC004: Update user (PUT) → 200 OK + updated data          │
│ TC005: Update user (PATCH) → 200 OK + partial update      │
│ TC006: Delete user → 200/204 OK                           │
│ TC007: Create user with all optional fields → 201 Created │
└────────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────────┐
│ NEGATIVE TEST CASES (Error Handling)                      │
├────────────────────────────────────────────────────────────┤
│ TC008: Create user without name → 400 Bad Request         │
│ TC009: Create user without email → 400 Bad Request        │
│ TC010: Create user with invalid email → 422 Unprocessable │
│ TC011: Create user with duplicate email → 409 Conflict    │
│ TC012: Get non-existent user → 404 Not Found              │
│ TC013: Update non-existent user → 404 Not Found           │
│ TC014: Delete non-existent user → 404 Not Found           │
│ TC015: Create user with empty body → 400 Bad Request      │
│ TC016: Create user with invalid JSON → 400 Bad Request    │
└────────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────────┐
│ SECURITY TEST CASES                                       │
├────────────────────────────────────────────────────────────┤
│ TC017: GET without auth token → 401 Unauthorized          │
│ TC018: POST without auth token → 401 Unauthorized         │
│ TC019: DELETE without auth token → 401 Unauthorized       │
│ TC020: User tries to delete another user → 403 Forbidden  │
│ TC021: SQL injection in name field → 400/422              │
│ TC022: XSS in name field → 400/422                        │
│ TC023: Invalid/expired token → 401 Unauthorized           │
└────────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────────┐
│ BOUNDARY TEST CASES                                       │
├────────────────────────────────────────────────────────────┤
│ TC024: Name with 1 character → 201 Created                │
│ TC025: Name with 255 characters → 201 Created             │
│ TC026: Name with 256 characters → 422 Unprocessable       │
│ TC027: Email with 254 characters → 201 Created            │
│ TC028: Email with 255 characters → 422 Unprocessable      │
│ TC029: Minimum password length → 201 Created              │
│ TC030: Password below minimum → 422 Unprocessable         │
└────────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────────┐
│ PERFORMANCE TEST CASES                                    │
├────────────────────────────────────────────────────────────┤
│ TC031: GET users response time < 500ms                    │
│ TC032: POST user response time < 1000ms                   │
│ TC033: GET users under load (100 requests)                │
│ TC034: Concurrent user creation (10 parallel)             │
└────────────────────────────────────────────────────────────┘
```

---

## <a name="validation"></a>Request/Response Validation

### Request Validation Checklist

```
BEFORE SENDING REQUEST:

HEADERS:
□ Content-Type: application/json
□ Authorization: Bearer {{token}}
□ Accept: application/json
□ Custom headers (if required)

BODY:
□ JSON format valid है
□ Required fields present हैं
□ Data types correct हैं (string, number, boolean)
□ Field names spelling correct है
□ No extra commas या syntax errors

URL:
□ Base URL correct है
□ Endpoint path correct है
□ Path parameters replaced हैं
□ Query parameters added हैं
```

### Response Validation Points

```
1. STATUS CODE VALIDATION
   └─ Expected status code आया?
   └─ 200, 201, 400, 404, 500 etc.

2. RESPONSE BODY VALIDATION
   └─ JSON structure correct है?
   └─ Required fields present हैं?
   └─ Data types correct हैं?
   └─ Values accurate हैं?

3. RESPONSE TIME VALIDATION
   └─ SLA के अंदर है? (< 500ms, < 1s, etc.)

4. HEADERS VALIDATION
   └─ Content-Type: application/json
   └─ Security headers present
   └─ Caching headers correct

5. ERROR MESSAGE VALIDATION
   └─ Clear और helpful error message
   └─ No sensitive data exposed
   └─ Proper error code
```

### Response Validation Examples

```json
VALIDATE THIS RESPONSE:
{
  "id": 123,
  "name": "John Doe",
  "email": "john@example.com",
  "createdAt": "2026-01-26T10:30:00Z"
}

VALIDATION CHECKS:

1. Structure Check:
✓ Root is object
✓ Has id, name, email, createdAt fields

2. Data Type Check:
✓ id is number
✓ name is string
✓ email is string
✓ createdAt is string (ISO date)

3. Value Check:
✓ id > 0
✓ name not empty
✓ email contains @
✓ email contains .
✓ createdAt is valid ISO format

4. Business Rule Check:
✓ email unique है
✓ name length within limits
```

### Postman Validation Scripts

```javascript
// Complete Validation Example
pm.test("Complete User API Validation", () => {
    const response = pm.response.json();
    
    // Status code
    pm.response.to.have.status(200);
    
    // Response time
    pm.expect(pm.response.responseTime).to.be.below(500);
    
    // Structure validation
    pm.expect(response).to.have.property("id");
    pm.expect(response).to.have.property("name");
    pm.expect(response).to.have.property("email");
    pm.expect(response).to.have.property("createdAt");
    
    // Data type validation
    pm.expect(response.id).to.be.a("number");
    pm.expect(response.name).to.be.a("string");
    pm.expect(response.email).to.be.a("string");
    
    // Value validation
    pm.expect(response.id).to.be.greaterThan(0);
    pm.expect(response.name.length).to.be.greaterThan(0);
    pm.expect(response.email).to.include("@");
    pm.expect(response.email).to.include(".");
    
    // Date format validation
    pm.expect(new Date(response.createdAt)).to.be.valid;
});
```

---

## <a name="error-handling"></a>Error Handling in APIs

### Common API Errors

```
┌────────────────────────────────────────────────────────────┐
│                    ERROR PATTERNS                          │
├────────────────────────────────────────────────────────────┤
│ Error Type        │ Cause              │ Solution          │
├────────────────────────────────────────────────────────────┤
│ 400 Bad Request   │ Invalid input      │ Validate before   │
│                   │ Missing fields     │ sending           │
├────────────────────────────────────────────────────────────┤
│ 401 Unauthorized  │ No token           │ Login first       │
│                   │ Expired token      │ Refresh token     │
├────────────────────────────────────────────────────────────┤
│ 403 Forbidden     │ No permission      │ Check user role   │
│                   │ Wrong scope        │ Admin action?     │
├────────────────────────────────────────────────────────────┤
│ 404 Not Found     │ Wrong URL          │ Check endpoint    │
│                   │ Deleted resource   │ Resource exists?  │
├────────────────────────────────────────────────────────────┤
│ 409 Conflict      │ Duplicate entry    │ Check uniqueness  │
│                   │ Version mismatch   │ Get latest version│
├────────────────────────────────────────────────────────────┤
│ 422 Unprocessable │ Valid format,      │ Check business    │
│                   │ semantic error     │ rules             │
├────────────────────────────────────────────────────────────┤
│ 500 Server Error  │ Code bug           │ Contact dev team  │
│                   │ Unhandled exception│ Check logs        │
├────────────────────────────────────────────────────────────┤
│ 503 Unavailable   │ Server down        │ Retry later       │
│                   │ Maintenance        │ Check status page │
└────────────────────────────────────────────────────────────┘
```

### Error Response Format

```json
GOOD ERROR RESPONSE:
{
  "error": {
    "code": "USER_NOT_FOUND",
    "message": "User with ID 123 does not exist",
    "details": {
      "field": "id",
      "value": 123,
      "reason": "No user found with this ID"
    },
    "timestamp": "2026-01-26T10:30:00Z",
    "requestId": "req_abc123"
  }
}

BAD ERROR RESPONSE:
{
  "error": "Not found"
}

WORST ERROR RESPONSE:
(Empty body with 404 status)
```

### Error Testing Scenarios

```
TEST THESE ERROR SCENARIOS:

1. INVALID INPUT
   ├─ Wrong data types
   ├─ Missing required fields
   ├─ Invalid formats (email, date)
   └─ Out of range values

2. AUTHENTICATION ERRORS
   ├─ No token
   ├─ Expired token
   ├─ Invalid token
   └─ Malformed token

3. AUTHORIZATION ERRORS
   ├─ Wrong role
   ├─ Insufficient permissions
   └─ Accessing others' data

4. RESOURCE ERRORS
   ├─ Non-existent resource
   ├─ Already deleted resource
   └─ Conflicting resource

5. SERVER ERRORS
   ├─ Timeout scenarios
   ├─ Database connection failure
   └─ Third-party service down
```

---

## <a name="real-scenarios"></a>Real API Testing Scenarios

### Scenario 1: E-commerce Login API

```
API: POST /api/auth/login

REQUEST:
{
  "email": "user@example.com",
  "password": "SecurePass123"
}

TEST CASES:

Positive:
✓ Valid credentials → 200 OK + token
✓ Valid credentials with remember me → 200 OK + long-lived token

Negative:
✓ Wrong email → 401 Unauthorized
✓ Wrong password → 401 Unauthorized
✓ Empty email → 400 Bad Request
✓ Empty password → 400 Bad Request
✓ SQL injection in email → 400/422
✓ XSS in password field → 400/422

Boundary:
✓ Email with 254 chars → 200 OK
✓ Email with 255 chars → 422
✓ Password min length → 200 OK
✓ Password below min → 422

Security:
✓ No auth header needed (public endpoint)
✓ Rate limiting after 5 failed attempts
✓ Account lockout after 10 failed attempts
```

### Scenario 2: Payment API

```
API: POST /api/payments

REQUEST:
{
  "orderId": "ORD123",
  "amount": 999.00,
  "currency": "USD",
  "cardNumber": "4111111111111111",
  "expiry": "12/26",
  "cvv": "123"
}

TEST CASES:

Positive:
✓ Valid card → 200 OK + transaction ID
✓ Valid card with save option → 200 OK + card saved

Negative:
✓ Invalid card number → 402 Payment Required
✓ Expired card → 402 Payment Required
✓ Wrong CVV → 402 Payment Required
✓ Insufficient funds → 402 Payment Required
✓ Invalid expiry format → 400 Bad Request
✓ Amount negative → 400 Bad Request
✓ Amount zero → 400 Bad Request
✓ Order not found → 404 Not Found
✓ Already paid order → 409 Conflict

Security:
✓ Card number masked in response
✓ CVV not stored in response
✓ HTTPS required
✓ PCI-DSS compliance
```

### Scenario 3: File Upload API

```
API: POST /api/users/:id/profile-picture

REQUEST:
Content-Type: multipart/form-data
File: profile.jpg (2MB)

TEST CASES:

Positive:
✓ Valid JPG under 5MB → 200 OK + file URL
✓ Valid PNG under 5MB → 200 OK + file URL

Negative:
✓ File over 5MB → 413 Payload Too Large
✓ Wrong format (PDF) → 400 Bad Request
✓ No file attached → 400 Bad Request
✓ Corrupted file → 400 Bad Request
✓ User not found → 404 Not Found
✓ No auth token → 401 Unauthorized

Performance:
✓ Upload 1MB file < 5 seconds
✓ Upload 5MB file < 15 seconds
```

---

## <a name="best-practices"></a>API Testing Best Practices

### 10 Golden Rules

```
1. UNDERSTAND THE API FIRST
   └─ Documentation पढ़ो
   └─ Endpoints समझो
   └─ Data flow समझो

2. TEST POSITIVE AND NEGATIVE SCENARIOS
   └─ Happy path test करो
   └─ Error scenarios test करो
   └─ Edge cases test करो

3. VALIDATE STATUS CODES
   └─ Correct codes आ रहे हैं?
   └─ Consistent हैं?

4. VALIDATE RESPONSE STRUCTURE
   └─ JSON schema validate करो
   └─ Required fields check करो

5. CHECK RESPONSE TIME
   └─ SLA define करो
   └─ Monitor consistently

6. TEST AUTHENTICATION & AUTHORIZATION
   └─ Token validation
   └─ Permission checks

7. USE VERSION CONTROL
   └─ API versions track करो
   └─ Breaking changes identify करो

8. AUTOMATE REGRESSION
   └─ Critical flows automate करो
   └─ CI/CD में integrate करो

9. MONITOR IN PRODUCTION
   └─ API health monitor करो
   └─ Error rates track करो

10. DOCUMENT EVERYTHING
    └─ Test cases document करो
    └─ Known issues document करो
```

### API Testing Checklist

```
PRE-TESTING:
□ API documentation reviewed
□ Test environment ready
□ Test data prepared
□ Authentication tokens ready
□ Tools configured (Postman, etc.)

DURING TESTING:
□ All endpoints tested
□ Positive cases executed
□ Negative cases executed
□ Security tests done
□ Performance tests done
□ Errors properly logged

POST-TESTING:
□ Results documented
□ Bugs reported
□ Automation scripts updated
□ Knowledge shared with team
```

---

## <a name="interview-questions"></a>20+ Interview Questions

### Fundamentals (1-5)

**Q1. API क्या होता है?**
```
A: API (Application Programming Interface) एक interface है जो 
दो software applications के बीच communication कराता है। 
Example: जब आप Swiggy पर order करते हो, तो Swiggy का app 
payment gateway की API से बात करता है payment process 
करने के लिए।
```

**Q2. REST और SOAP में difference?**
```
A:
REST                          SOAP
- Architectural style         - Protocol
- JSON, XML, Text support     - XML only
- Lightweight, fast           - Heavy, slow
- Stateless                   - Stateful
- Web/Mobile apps में use     - Banking/Enterprise में use
```

**Q3. HTTP methods कौन-कौन से होते हैं?**
```
A:
- GET: Data retrieve करने के लिए
- POST: New data create करने के लिए
- PUT: Full update करने के लिए
- PATCH: Partial update करने के लिए
- DELETE: Data delete करने के लिए
```

**Q4. 200, 201, 404, 500 status codes क्या mean करते हैं?**
```
A:
- 200 OK: Request successful
- 201 Created: Resource successfully created (POST के बाद)
- 404 Not Found: Resource नहीं मिला
- 500 Internal Server Error: Server की गलती
```

**Q5. API testing क्यों जरूरी है?**
```
A:
- UI से पहले backend test करने के लिए
- Security vulnerabilities पकड़ने के लिए
- Performance verify करने के लिए
- Integration issues early find करने के लिए
- Automation easy है UI से
```

### Technical (6-12)

**Q6. Postman में test case कैसे लिखते हैं?**
```
A: Postman के Tests tab में JavaScript लिखते हैं:

pm.test("Status code is 200", () => {
    pm.response.to.have.status(200);
});

pm.test("Response has name", () => {
    const data = pm.response.json();
    pm.expect(data.name).to.exist;
});
```

**Q7. Authentication testing कैसे करते हैं?**
```
A:
1. Authorization tab में token add करते हैं
2. Bearer Token select करते हैं
3. Token value डालते हैं
4. Request send करते हैं
5. 401 आता है बिना token के, 200 आता है सही token के साथ
```

**Q8. API response validation कैसे करते हो?**
```
A:
- Status code check करते हैं
- Response body structure validate करते हैं
- Data types check करते हैं
- Required fields present हैं check करते हैं
- Response time SLA के अंदर है check करते हैं
- Error messages appropriate हैं check करते हैं
```

**Q9. Negative testing क्या है API में?**
```
A: Invalid inputs देकर error handling test करना:
- Invalid email format → 422
- Missing required field → 400
- Wrong authentication → 401
- No permission → 403
- Non-existent resource → 404
```

**Q10. API documentation में क्या देखते हो?**
```
A:
- Endpoints और methods
- Request/response format
- Required और optional fields
- Authentication requirements
- Error codes और meanings
- Rate limits
- Examples
```

**Q11. Collection और Environment क्या है Postman में?**
```
A:
Collection: Related requests का group
Environment: Variables का set (baseUrl, token, etc.)

Example: Local और QA environments के लिए अलग variables
```

**Q12. CI/CD में API testing कैसे integrate करते हैं?**
```
A:
- Postman collection को Newman से run करते हैं
- Jenkins/GitHub Actions में script add करते हैं
- हर commit पर API tests automatically run होते हैं
- Fail होने पर deploy block होता है
```

### Scenario-Based (13-18)

**Q13. API 500 error दे रही है। कैसे debug करोगे?**
```
A:
1. Request verify करूंगा (correct endpoint, data)
2. Response body में error details देखूंगा
3. Server logs check करने को कहूंगा
4. Same request दूसरे environment में try करूंगा
5. Third-party dependencies check करूंगा
6. Dev team को escalate करूंगा with full details
```

**Q14. API slow है। कैसे test करोगे performance?**
```
A:
- Response time measure करूंगा (multiple requests)
- Load testing करूंगा (concurrent requests)
- Stress testing करूंगा (high load)
- Database queries check करने को कहूंगा
- Caching implement है check करूंगा
- Network latency consider करूंगा
```

**Q15. Authentication token expire हो गया। कैसे handle करोगे?**
```
A:
- Pre-request script में token refresh logic add करूंगा
- 401 response पर auto-refresh करूंगा
- Retry mechanism implement करूंगा
- Token expiry time track करूंगा
```

**Q16. Two APIs dependent हैं। कैसे test करोगे?**
```
A:
- First API call करूंगा
- Response से data extract करूंगा (Postman में)
- Second API को उस data के साथ call करूंगा
- Chain testing करूंगा
- Dependency failure handle करूंगा
```

**Q17. API में breaking change कैसे identify करोगे?**
```
A:
- API version check करूंगा
- Response schema compare करूंगा
- Regression tests run करूंगा
- Documentation compare करूंगा
- Status codes change हुए हैं check करूंगा
- New required fields तो नहीं आए
```

**Q18. Rate limiting कैसे test करोगे?**
```
A:
- Loop में multiple requests भेजूंगा
- 429 Too Many Responses status check करूंगा
- Retry-After header verify करूंगा
- Collection runner से bulk requests भेजूंगा
```

### Advanced (19-22)

**Q19. GraphQL API testing कैसे करते हैं?**
```
A:
- POST request होता है
- Body में query और variables भेजते हैं
- Response में requested fields आते हैं
- Schema validation important है
- Over/under fetching test करते हैं
```

**Q20. Webhook testing कैसे करते हैं?**
```
A:
- Webhook endpoint create करते हैं (RequestBin, ngrok)
- Trigger event send करते हैं
- Webhook payload receive और validate करते हैं
- Retry mechanism test करते हैं
- Signature validation test करते हैं
```

**Q21. API security testing में क्या check करते हो?**
```
A:
- Authentication (token validation)
- Authorization (permission checks)
- Input validation (SQL injection, XSS)
- Rate limiting
- Sensitive data encryption
- CORS configuration
- Security headers
```

**Q22. Mock API testing क्या है?**
```
A: Mock API actual backend के बिना test करने का तरीका है।
Tools: Postman Mock Server, WireMock, MockServer

Use cases:
- Backend ready नहीं है
- Third-party API cost करता है
- Testing के लिए specific responses चाहिए
```

---

## 🎯 Quick Reference: API Testing Cheat Sheet

```
COMMON STATUS CODES:
200 OK          ✅ Success
201 Created     ✨ New resource
204 No Content  🗑️ Deleted
400 Bad Request 👈 Client error
401 Unauthorized 🔐 Login needed
403 Forbidden   🚫 No permission
404 Not Found   🔍 Doesn't exist
409 Conflict    💥 Duplicate
422 Unprocessable 📝 Validation error
500 Server Error 🖥️ Server problem

HTTP METHODS:
GET    → Read
POST   → Create
PUT    → Full Update
PATCH  → Partial Update
DELETE → Delete

API TESTING TOOLS:
- Postman (Most popular)
- Insomnia (Lightweight)
- curl (Command line)
- SoapUI (SOAP APIs)
- JMeter (Performance)
```

---

*Module 07 Complete ✅*  
*Next: Module 08 - Database Testing*
