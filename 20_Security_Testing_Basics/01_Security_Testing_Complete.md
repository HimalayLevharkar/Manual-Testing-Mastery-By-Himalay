# 20_Security_Testing_Basics

## Security Testing Fundamentals
### Complete Guide to Security Testing with Real-World Scenarios

---

## 📋 Table of Contents

1. [Security Testing Overview](#overview)
2. [Why Security Testing Matters](#why)
3. [Security Testing Types](#types)
4. [OWASP Top 10 Deep Dive](#owasp)
5. [Security Testing Process](#process)
6. [Vulnerability Assessment](#va)
7. [Penetration Testing](#pentest)
8. [Security Testing Tools](#tools)
9. [Authentication & Authorization Testing](#auth)
10. [Data Protection Testing](#data)
11. [Real Security Scenarios](#scenarios)
12. [Common Security Vulnerabilities](#vulnerabilities)
13. [Security Test Cases](#test-cases)
14. [Security Checklist](#checklist)
15. [Interview Questions](#interview)

---

## 🎯 Security Testing Overview {#overview}

### What is Security Testing?

Security Testing ek type of testing hai jo verify karta hai ki software application:
- ✅ Unauthorized access se protected hai
- ✅ Data confidential rehta hai
- ✅ Data integrity maintain rehti hai
- ✅ Authentication proper hai
- ✅ Authorization correctly implemented hai
- ✅ Attacks se resilient hai

### Simple Definition:

```
Security Testing = Testing system's ability to protect data and 
maintain functionality against malicious attacks.
```

### Security Testing Goals (CIA Triad)

```
                    SECURITY
                      │
        ┌─────────────┼─────────────┐
        │             │             │
    CONFIDENTIALITY   INTEGRITY   AVAILABILITY
        │             │             │
        │             │             │
    Data secret   Data accurate   Data accessible
    & private     & complete      when needed
        │             │             │
    Encryption    Hashing        Redundancy
    Access Ctrl   Digital Sig    Load Balancing
```

### CIA Triad Explained:

```
1. CONFIDENTIALITY (गोपनीयता)
   - Data sirf authorized users ko dikhe
   - Unauthorized access se protected
   - Example: Password encrypt hona chahiye
   
2. INTEGRITY (अखंडता)
   - Data modify na ho unauthorized tarike se
   - Data accurate aur complete rahe
   - Example: Transaction amount change na ho sake
   
3. AVAILABILITY (उपलब्धता)
   - Authorized users ko jab chahiye access mile
   - System uptime maintain ho
   - Example: DDoS attack se protection
```

---

## 💡 Why Security Testing Matters {#why}

### Real-World Impact of Security Breaches

```
Case Study 1: Equifax Data Breach (2017)

What Happened:
- Vulnerability: Apache Struts vulnerability (CVE-2017-5638)
- Impact: 147 million people's data breached
- Data Exposed: SSN, birth dates, addresses, credit cards

Consequences:
💰 Financial: $1.4 billion in costs
📉 Reputation: Massive trust loss
⚖️ Legal: Multiple lawsuits, regulatory fines
👥 Leadership: CEO resigned

Root Cause:
- Known vulnerability not patched for 2 months
- No security testing done
- Poor vulnerability management

Lesson:
✓ Regular security testing critical
✓ Patch management essential
✓ Vulnerability scanning mandatory
```

```
Case Study 2: Target Breach (2013)

What Happened:
- Attackers entered through HVAC vendor
- Installed malware on POS systems
- 40 million credit cards stolen

Consequences:
💰 Financial: $202 million in costs
📉 Reputation: Customer trust damaged
⚖️ Legal: Multiple settlements
👥 Leadership: CEO and CIO fired

Root Cause:
- Network segmentation missing
- Vendor access not properly controlled
- Security alerts ignored

Lesson:
✓ Third-party security important
✓ Network segmentation necessary
✓ Security monitoring critical
```

```
Case Study 3: Indian Context - Aadhaar Data Leak

What Happened:
- Multiple reports of Aadhaar data exposure
- Journalists could buy data for ₹500
- Names, addresses, phone numbers exposed

Consequences:
📉 Public trust impacted
⚖️ Regulatory scrutiny
🔒 Policy changes required

Lesson:
✓ Critical infrastructure needs extra security
✓ Access controls must be strict
✓ Regular security audits mandatory
```

### Why Security Testing is Critical?

```
Business Impact:

💰 Financial Loss
   - Direct theft
   - Regulatory fines (GDPR: up to 4% of global revenue)
   - Lawsuit costs
   - Remediation costs
   - Business disruption

📉 Reputation Damage
   - Customer trust loss
   - Brand value impact
   - Competitive disadvantage
   - Social media backlash

⚖️ Legal & Compliance
   - Regulatory fines
   - Criminal charges
   - License cancellation
   - Contract breaches

🔒 Operational Impact
   - System downtime
   - Data recovery costs
   - Customer support load
   - Emergency response costs
```

### When Security Testing is Required?

```
Mandatory Scenarios:

✓ New application before production
✓ Major version upgrade
✓ New features with security impact
✓ Infrastructure changes
✓ Third-party integration
✓ After security incident
✓ Compliance requirements (PCI DSS, HIPAA, GDPR)
✓ Annual security audit
✓ Before handling sensitive data
✓ After vulnerability disclosure
```

---

## 📊 Security Testing Types {#types}

### Complete Security Testing Landscape

```
                SECURITY TESTING
                     │
       ┌─────────────┼─────────────┐
       │             │             │
   Vulnerability   Penetration   Security
   Assessment      Testing       Audit
       │             │             │
       │             │             │
   Automated     Manual +       Compliance
   Scanning      Automated      Check
```

### 1. Vulnerability Assessment (VA)

```
Purpose: System mein vulnerabilities dhundhna aur categorize karna

Characteristics:
- Automated scanning
- Comprehensive coverage
- Known vulnerabilities
- Prioritized findings

Process:
1. Scan systems/applications
2. Identify vulnerabilities
3. Categorize by severity
4. Report with remediation

Tools:
- Nessus
- Qualys
- OpenVAS
- Nexpose

When to Use:
✓ Regular security checks
✓ Compliance requirements
✓ Before penetration testing
✓ After changes
```

### 2. Penetration Testing (Pentest)

```
Purpose: Real attacker ki tarah attack karke vulnerabilities exploit karna

Characteristics:
- Manual + Automated
- Exploitation focused
- Business impact analysis
- Detailed attack scenarios

Types:
┌─────────────────┬─────────────────────────────────────┐
│ Type            │ Description                         │
├─────────────────┼─────────────────────────────────────┤
│ Black Box       │ No prior knowledge (external hacker)│
│ White Box       │ Full knowledge (internal threat)    │
│ Gray Box        │ Partial knowledge                   │
└─────────────────┴─────────────────────────────────────┘

Process:
1. Reconnaissance (information gathering)
2. Scanning (vulnerability identification)
3. Exploitation (gaining access)
4. Post-exploitation (maintaining access)
5. Reporting

When to Use:
✓ Before production
✓ After major changes
✓ Compliance requirements
✓ High-security applications
```

### 3. Security Audit

```
Purpose: Security policies and controls ka compliance check karna

Characteristics:
- Policy verification
- Compliance focused
- Documentation review
- Control testing

Focus Areas:
- Access controls
- Security policies
- Incident response
- Business continuity
- Compliance requirements

When to Use:
✓ Regulatory compliance
✓ Annual audits
✓ After incidents
✓ Customer requirements
```

### 4. Security Scanning

```
Purpose: Automated tools se vulnerabilities dhundhna

Types:

Web Application Scanning:
- OWASP Top 10 vulnerabilities
- Configuration issues
- Missing security headers

Network Scanning:
- Open ports
- Service versions
- Network vulnerabilities

Code Scanning:
- SAST (Static Application Security Testing)
- DAST (Dynamic Application Security Testing)
- SCA (Software Composition Analysis)

When to Use:
✓ In CI/CD pipeline
✓ Before deployments
✓ Regular intervals
✓ After code changes
```

### 5. Security Configuration Review

```
Purpose: Systems aur applications ki configuration verify karna

Check Areas:
□ Server hardening
□ Database security
□ Network security
□ Application security
□ Access controls
□ Logging configuration
□ Encryption settings

When to Use:
✓ New infrastructure
✓ After changes
✓ Compliance requirements
✓ Security incidents
```

### 6. Code Review (Security Focus)

```
Purpose: Source code mein security vulnerabilities dhundhna

Approach:
- Manual code review
- Automated SAST tools
- Threat modeling
- Security pattern checking

Common Issues Found:
□ SQL injection vulnerabilities
□ XSS vulnerabilities
□ Hardcoded credentials
□ Insecure cryptography
□ Missing input validation

When to Use:
✓ Before production
✓ Critical features
✓ After security training
✓ Regular intervals
```

### 7. Risk Assessment

```
Purpose: Security risks identify aur prioritize karna

Process:
1. Identify assets
2. Identify threats
3. Assess vulnerabilities
4. Calculate risk (Risk = Threat × Vulnerability × Impact)
5. Prioritize remediation

Output:
- Risk register
- Risk treatment plan
- Mitigation priorities
- Residual risk acceptance

When to Use:
✓ Project initiation
✓ Before major releases
✓ After incidents
✓ Annual planning
```

### 8. Red Team Assessment

```
Purpose: Complete simulated attack (multi-vector, long-term)

Characteristics:
- Real-world attack simulation
- Multiple attack vectors
- Long duration (weeks/months)
- Detection testing
- Response testing

Scope:
- Physical security
- Network security
- Application security
- Social engineering
- Insider threats

When to Use:
✓ Mature security programs
✓ Critical infrastructure
✓ Advanced threat preparation
✓ Security team training
```

---

## 🚨 OWASP Top 10 Deep Dive {#owasp}

### What is OWASP?

**Open Web Application Security Project (OWASP)** - Non-profit organization jo web application security standards aur guidelines banata hai.

### OWASP Top 10 (2021)

```
1. Broken Access Control
2. Cryptographic Failures
3. Injection
4. Insecure Design
5. Security Misconfiguration
6. Vulnerable and Outdated Components
7. Identification and Authentication Failures
8. Software and Data Integrity Failures
9. Security Logging and Monitoring Failures
10. Server-Side Request Forgery (SSRF)
```

### A01: Broken Access Control

```
What is it?
Users can access resources/functionalities they shouldn't have access to.

Common Scenarios:

1. Vertical Privilege Escalation
   - Regular user accessing admin functions
   - Example: /admin/users endpoint access

2. Horizontal Privilege Escalation
   - Accessing another user's data
   - Example: Viewing another user's orders

3. Directory Traversal
   - Accessing files outside intended directory
   - Example: ../../etc/passwd

Real Example:
URL: https://bank.com/account?account_id=12345
Attacker changes: account_id=12346
Result: Accesses another user's account!

How to Test:
□ Try accessing admin URLs as regular user
□ Modify ID parameters to access other records
□ Check API authorization
□ Test file access controls
□ Verify CORS configuration

Prevention:
✓ Implement proper access control
✓ Deny by default
✓ Log access control failures
✓ Invalidate tokens on logout
✓ Implement rate limiting
```

### A02: Cryptographic Failures

```
What is it?
Sensitive data properly encrypt/protect na karna.

Common Scenarios:

1. Data in Transit Not Encrypted
   - HTTP instead of HTTPS
   - Internal traffic unencrypted

2. Data at Rest Not Encrypted
   - Passwords in plain text
   - Credit card numbers unencrypted
   - PII in logs

3. Weak Cryptography
   - Using MD5, SHA1
   - Weak keys
   - Outdated algorithms

4. Poor Key Management
   - Hardcoded keys
   - Keys in source code
   - No key rotation

Real Example:
Database breach reveals:
- Passwords: plain text (NOT hashed!)
- Credit cards: unencrypted
- SSN: unencrypted

Impact:
- 1 million users affected
- Identity theft risk
- Regulatory fines

How to Test:
□ Check if sensitive data encrypted at rest
□ Verify TLS for data in transit
□ Check password hashing (bcrypt, argon2)
□ Look for sensitive data in logs
□ Test certificate validation
□ Check for weak algorithms

Prevention:
✓ Encrypt sensitive data (at rest and transit)
✓ Use strong algorithms (AES-256, RSA-2048+)
✓ Hash passwords (bcrypt, argon2, scrypt)
✓ Implement key management
✓ Don't log sensitive data
```

### A03: Injection

```
What is it?
Untrusted data as command/query bhejna aur execute karwana.

Types:

1. SQL Injection (SQLi)
   Input: ' OR '1'='1
   Query: SELECT * FROM users WHERE username='' OR '1'='1'
   Result: All users returned!

2. Command Injection
   Input: ; rm -rf /
   Command: ping google.com; rm -rf /
   Result: Dangerous command executed!

3. XSS (Cross-Site Scripting)
   Input: <script>alert('XSS')</script>
   Result: Script executes in victim's browser!

4. LDAP Injection
   Input: *)(uid=*))(|(uid=*
   Result: LDAP query manipulated!

Real Example - SQL Injection:
Login form:
Username: admin' --
Password: anything

Query becomes:
SELECT * FROM users WHERE username='admin' --' AND password='xxx'
-- comments out password check!
Result: Admin access without password!

How to Test:
□ Test all input fields with special characters
□ Try SQL injection payloads
□ Test for XSS with script tags
□ Check error messages for SQL details
□ Use SQLMap for automated testing

Prevention:
✓ Use prepared statements/parameterized queries
✓ Input validation (whitelist approach)
✓ Output encoding
✓ Use ORM frameworks
✓ Implement WAF
✓ Least privilege database accounts
```

### A04: Insecure Design

```
What is it?
Application design mein security considerations missing hona.

Common Scenarios:

1. Missing Security Controls
   - No rate limiting
   - No account lockout
   - No session timeout

2. Poor Session Management
   - Predictable session IDs
   - Session fixation
   - No session invalidation

3. Business Logic Flaws
   - Price manipulation
   - Quantity bypass
   - Workflow bypass

Real Example - Business Logic Flaw:
E-commerce checkout:
Step 1: Add item (₹1000)
Step 2: Apply coupon (100% off)
Step 3: Modify quantity to -1
Step 4: Total becomes negative
Step 5: System refunds negative amount!

How to Test:
□ Review architecture for security
□ Threat modeling sessions
□ Test business logic flows
□ Check for missing controls
□ Review session management
□ Test for race conditions

Prevention:
✓ Threat modeling
✓ Secure design patterns
✓ Security requirements
✓ Security code review
✓ Automated testing for business logic
```

### A05: Security Misconfiguration

```
What is it?
Systems/applications insecure tarike se configure hona.

Common Scenarios:

1. Default Credentials
   - admin/admin
   - root/password
   - Default database passwords

2. Verbose Error Messages
   - Stack traces to users
   - Database errors exposed
   - Internal IPs revealed

3. Unnecessary Features Enabled
   - Default applications
   - Unused services running
   - Debug mode enabled

4. Missing Security Headers
   - No Content-Security-Policy
   - No X-Frame-Options
   - No X-XSS-Protection

Real Example:
Error message shows:
"SQLException: SELECT * FROM users WHERE id=1
at com.app.UserDAO.getUser(UserDAO.java:45)
Database: MySQL 8.0.23
Server: Apache Tomcat 9.0"

Attacker now knows:
- Database type and version
- Application structure
- Server software

How to Test:
□ Check for default credentials
□ Trigger errors and check messages
□ Scan for open ports
□ Check security headers
□ Look for debug endpoints
□ Check directory listing

Prevention:
✓ Hardening guidelines follow karna
✓ Disable unnecessary features
✓ Custom error pages
✓ Security headers implement
✓ Regular configuration reviews
✓ Automated configuration scanning
```

### A06: Vulnerable and Outdated Components

```
What is it?
Libraries, frameworks, aur components jo vulnerable ya outdated hain.

Common Scenarios:

1. Outdated Libraries
   - jQuery 1.x (known XSS)
   - Log4j 2.x (Log4Shell)
   - Struts 2.x (known RCE)

2. Unsupported Software
   - Windows Server 2008
   - PHP 5.x
   - Old framework versions

3. Unknown Components
   - Transitive dependencies
   - Unused dependencies
   - Untracked components

Real Example - Log4Shell (2021):
Vulnerability: CVE-2021-44228
Impact: Remote Code Execution
Affected: Any application using Log4j 2.0-2.14.1
Result: Complete server compromise possible!

How to Test:
□ Inventory all components
□ Check versions against CVE databases
□ Use SCA tools
□ Monitor for new vulnerabilities
□ Check transitive dependencies

Prevention:
✓ Maintain component inventory
✓ Regular updates
✓ Use SCA tools (OWASP Dependency-Check)
✓ Remove unused dependencies
✓ Monitor vulnerability databases
✓ Have patching process
```

### A07: Identification and Authentication Failures

```
What is it?
Authentication aur session management properly implement na hona.

Common Scenarios:

1. Weak Password Policies
   - No complexity requirements
   - No minimum length
   - Common passwords allowed

2. No Brute Force Protection
   - No account lockout
   - No rate limiting
   - No CAPTCHA

3. Session Management Issues
   - Session fixation
   - No session timeout
   - Session not invalidated on logout

4. Credential Stuffing
   - No MFA
   - No breach password checking
   - No unusual login detection

Real Example - Credential Stuffing:
Attacker:
1. Gets breached credentials from dark web
2. Tries same credentials on your site
3. Users reuse passwords = Success!
4. Account takeover

How to Test:
□ Try weak passwords
□ Test brute force (100+ attempts)
□ Check session fixation
□ Test session timeout
□ Verify logout invalidation
□ Check for MFA implementation

Prevention:
✓ Strong password policies
✓ Multi-factor authentication
✓ Account lockout after failed attempts
✓ Rate limiting
✓ Session management best practices
✓ Check passwords against breach databases
✓ Monitor for unusual login patterns
```

### A08: Software and Data Integrity Failures

```
What is it?
Software aur data ki integrity verify na karna.

Common Scenarios:

1. Insecure Updates
   - Updates without signature verification
   - Updates from untrusted sources
   - No integrity checking

2. Deserialization Vulnerabilities
   - Untrusted serialized data
   - No validation before deserialization
   - Remote code execution risk

3. CI/CD Pipeline Compromise
   - Unauthorized code changes
   - Compromised build process
   - No code signing

Real Example - Insecure Deserialization:
Attacker sends serialized object with malicious payload
Application deserializes without validation
Malicious code executes
Complete server compromise!

How to Test:
□ Check update mechanisms
□ Test deserialization endpoints
□ Verify code signing
□ Review CI/CD security
□ Check integrity validations

Prevention:
✓ Verify digital signatures
✓ Use secure deserialization
✓ Implement integrity checks
✓ Secure CI/CD pipeline
✓ Code signing for releases
✓ Don't trust serialized data from untrusted sources
```

### A09: Security Logging and Monitoring Failures

```
What is it?
Proper logging aur monitoring na hona jisse attacks detect na ho paayein.

Common Scenarios:

1. Insufficient Logging
   - Failed logins not logged
   - Authorization failures not logged
   - Input validation failures not logged

2. Logs Not Monitored
   - No alerting
   - No SIEM integration
   - Logs not reviewed

3. Sensitive Data in Logs
   - Passwords logged
   - Credit card numbers in logs
   - PII in logs

4. Log Tampering
   - Logs not protected
   - No integrity checking
   - Easy to delete/modify

Real Example:
Attacker tries 10,000 passwords over 3 days
- No alerts triggered
- Logs not monitored
- Breach successful
- No way to investigate (insufficient logs)

How to Test:
□ Check what events are logged
□ Verify log content (no sensitive data)
□ Test alerting mechanisms
□ Check log protection
□ Review incident response

Prevention:
✓ Log all security events
✓ Implement real-time monitoring
✓ Set up alerting
✓ Protect log integrity
✓ Don't log sensitive data
✓ Regular log reviews
✓ SIEM integration
```

### A10: Server-Side Request Forgery (SSRF)

```
What is it?
Attacker server ko internal resources pe request bhejne ke liye force karna.

Common Scenarios:

1. Internal Service Access
   - Accessing internal APIs
   - Accessing metadata services
   - Accessing admin interfaces

2. Cloud Metadata Access
   - AWS: http://169.254.169.254/
   - Azure: http://169.254.169.254/metadata/
   - GCP: http://metadata.google.internal/

3. Port Scanning
   - Scanning internal network
   - Accessing internal services

Real Example - AWS Metadata:
Attacker input: http://169.254.169.254/latest/meta-data/iam/security-credentials/
Server fetches this URL
Result: AWS credentials exposed!
Impact: Complete AWS account compromise!

How to Test:
□ Test URL parameters
□ Try internal IP addresses
□ Test cloud metadata URLs
□ Check for port scanning
□ Test with different protocols

Prevention:
✓ Validate all URLs
✓ Block internal IP ranges
✓ Block cloud metadata IPs
✓ Use allowlists for URLs
✓ Disable unnecessary URL schemes
✓ Implement network segmentation
```

---

## 🔄 Security Testing Process {#process}

### Complete Security Testing Lifecycle

```
         SECURITY TESTING PROCESS
                  │
    ┌─────────────┴─────────────┐
    │                           │
1. Planning              6. Exploitation
    │                           │
2. Discovery             7. Post-Exploitation
    │                           │
3. Vulnerability         8. Reporting
   Assessment                    │
    │                           │
4. Risk Analysis         9. Remediation
    │                           │
5. Testing              10. Re-testing
```

### Step 1: Test Planning

```
Activities:
□ Define scope (what to test, what not to test)
□ Define objectives
□ Identify constraints
□ Get proper authorization
□ Define rules of engagement
□ Sign NDA and contracts

Test Plan Document:

┌─────────────────────────────────────────┐
│     SECURITY TEST PLAN                  │
├─────────────────────────────────────────┤
│ 1. Scope                                │
│    - Web application: app.example.com   │
│    - API: api.example.com               │
│    - Mobile app (iOS, Android)          │
│    - Out of scope: Third-party services │
│                                         │
│ 2. Objectives                           │
│    - Identify OWASP Top 10              │
│    - Test authentication/authorization  │
│    - Check data protection              │
│    - Compliance verification            │
│                                         │
│ 3. Testing Type                         │
│    - Gray box (partial knowledge)       │
│    - Manual + Automated                 │
│                                         │
│ 4. Timeline                             │
│    - Start: January 15, 2026            │
│    - End: January 25, 2026              │
│                                         │
│ 5. Authorization                        │
│    - Signed by: CTO                     │
│    - Emergency contacts listed          │
└─────────────────────────────────────────┘
```

### Step 2: Discovery/Reconnaissance

```
Activities:
□ Information gathering
□ Application mapping
□ Technology identification
□ Entry point identification

Information to Gather:

┌─────────────────────────────────────────┐
│ Application Information                 │
├─────────────────────────────────────────┤
│ - All URLs and endpoints                │
│ - Input fields and forms                │
│ - API endpoints                         │
│ - Authentication mechanisms             │
│ - Session management                    │
│ - User roles and permissions            │
│ - Technologies used                     │
│ - Third-party integrations              │
│ - Error messages                        │
│ - File upload functionality             │
└─────────────────────────────────────────┘

Tools Used:
- Burp Suite (Proxy, Scanner)
- OWASP ZAP
- Nikto (web server scanning)
- Wappalyzer (technology detection)
- theHarvester (email/subdomain discovery)
```

### Step 3: Vulnerability Assessment

```
Activities:
□ Automated scanning
□ Manual vulnerability identification
□ Categorization by severity
□ Initial analysis

Vulnerability Categories:

┌─────────────┬─────────────────────────────┐
│ Severity    │ Description                 │
├─────────────┼─────────────────────────────┤
│ Critical    │ Immediate exploitation      │
│             │ possible, severe impact     │
├─────────────┼─────────────────────────────┤
│ High        │ Exploitation possible,      │
│             │ significant impact          │
├─────────────┼─────────────────────────────┤
│ Medium      │ Exploitation difficult,     │
│             │ moderate impact             │
├─────────────┼─────────────────────────────┤
│ Low         │ Hard to exploit, minimal    │
│             │ impact                      │
├─────────────┼─────────────────────────────┤
│ Informational│ Best practice violations   │
└─────────────┴─────────────────────────────┘
```

### Step 4: Risk Analysis

```
Activities:
□ Assess business impact
□ Calculate risk score
□ Prioritize vulnerabilities
□ Define remediation timeline

Risk Calculation:

Risk Score = Likelihood × Impact

Likelihood (1-5):
1 = Very Unlikely
2 = Unlikely
3 = Possible
4 = Likely
5 = Very Likely

Impact (1-5):
1 = Minimal
2 = Minor
3 = Moderate
4 = Major
5 = Critical

Risk Matrix:
                    IMPACT
              1    2    3    4    5
            ┌─────────────────────┐
          1 │ 1  2  3  4  5       │
          2 │ 2  4  6  8  10      │
    L     3 │ 3  6  9  12 15      │
    I     4 │ 4  8  12 16 20      │
    K     5 │ 5  10 15 20 25      │
    E     └─────────────────────┘
    L
    I
    H
    O
    O
    D

Risk Levels:
- 1-5: Low Risk (Green)
- 6-12: Medium Risk (Yellow)
- 15-20: High Risk (Orange)
- 25: Critical Risk (Red)
```

### Step 5: Security Testing

```
Testing Areas:

Authentication Testing:
□ Default credentials
□ Password policies
□ Brute force protection
□ Account lockout
□ Multi-factor authentication
□ Password reset functionality
□ Session management

Authorization Testing:
□ Vertical privilege escalation
□ Horizontal privilege escalation
□ Access control bypass
□ Directory traversal
□ Insecure direct object references

Input Validation Testing:
□ SQL injection
□ XSS (Cross-Site Scripting)
□ Command injection
□ XXE (XML External Entity)
□ File upload vulnerabilities
□ Path traversal

Business Logic Testing:
□ Workflow bypass
□ Price manipulation
□ Quantity manipulation
□ Race conditions
□ Time-based attacks

API Security Testing:
□ Authentication
□ Authorization
□ Rate limiting
□ Input validation
□ Error handling
□ Data exposure
```

### Step 6: Exploitation

```
Activities:
□ Attempt to exploit vulnerabilities
□ Gain unauthorized access
□ Escalate privileges
□ Access sensitive data
□ Document exploitation steps

Important Notes:
⚠ Only within authorized scope
⚠ Document all steps carefully
⚠ Minimize impact on production
⚠ Have rollback plan
⚠ Emergency contacts ready

Exploitation Documentation:

┌─────────────────────────────────────────┐
│ Exploitation Record                     │
├─────────────────────────────────────────┤
│ Vulnerability: SQL Injection            │
│ Target: /api/users endpoint             │
│ Steps:                                  │
│ 1. Identified injection point           │
│ 2. Tested with ' OR '1'='1              │
│ 3. Confirmed data extraction possible   │
│ 4. Extracted user table schema          │
│ 5. Extracted user credentials           │
│                                         │
│ Impact: Complete database compromise    │
│ Evidence: Screenshots, logs attached    │
│                                         │
│ Remediation: Use parameterized queries  │
└─────────────────────────────────────────┘
```

### Step 7: Post-Exploitation

```
Activities:
□ Document what data was accessible
□ Check persistence possibilities
□ Assess lateral movement potential
□ Clean up any test data
□ Restore any changes

Important:
✓ Remove any test accounts created
✓ Delete any uploaded test files
✓ Clear any modified data
✓ Document what was accessed
✓ Verify system is clean
```

### Step 8: Reporting

```
Security Test Report Structure:

┌─────────────────────────────────────────┐
│     SECURITY TEST REPORT                │
├─────────────────────────────────────────┤
│ Executive Summary                       │
│ - Test conducted and scope              │
│ - Overall security posture              │
│ - Key findings summary                  │
│ - Risk rating                           │
│                                         │
│ Test Methodology                        │
│ - Approach (black/white/gray box)       │
│ - Tools used                            │
│ - Standards followed                    │
│                                         │
│ Detailed Findings                       │
│ - Vulnerability 1 (Critical)            │
│   - Description                         │
│   - Steps to reproduce                  │
│   - Impact                              │
│   - Proof of concept                    │
│   - Remediation                         │
│ - Vulnerability 2 (High)                │
│ - ...                                   │
│                                         │
│ Summary Statistics                      │
│ - Critical: 2                           │
│ - High: 5                               │
│ - Medium: 10                            │
│ - Low: 15                               │
│ - Informational: 8                      │
│                                         │
│ Recommendations                         │
│ - Immediate actions                     │
│ - Short-term improvements               │
│ - Long-term strategy                    │
│                                         │
│ Appendix                                │
│ - Tool outputs                          │
│ - Screenshots                           │
│ - References                            │
└─────────────────────────────────────────┘
```

### Step 9: Remediation

```
Activities:
□ Work with development team on fixes
□ Provide guidance on remediation
□ Prioritize based on risk
□ Track remediation progress

Remediation Tracking:

┌──────────────┬────────────┬─────────────┬────────────┐
│ Finding      │ Severity   │ Due Date    │ Status     │
├──────────────┼────────────┼─────────────┼────────────┤
│ SQL Injection│ Critical   │ Immediate   │ In Progress│
├──────────────┼────────────┼─────────────┼────────────┤
│ XSS          │ High       │ 1 week      │ Pending    │
├──────────────┼────────────┼─────────────┼────────────┤
│ Auth Bypass  │ Critical   │ Immediate   │ Fixed      │
└──────────────┴────────────┴─────────────┴────────────┘
```

### Step 10: Re-testing

```
Activities:
□ Verify fixes are implemented
□ Test that vulnerabilities are fixed
□ Check for regression
□ Update risk assessment
□ Sign-off on remediation

Re-testing Checklist:
□ All critical findings addressed
□ All high findings addressed
□ Medium findings planned for fix
□ No new vulnerabilities introduced
□ Documentation updated
□ Final report issued
```

---

## 🔍 Vulnerability Assessment {#va}

### What is Vulnerability Assessment?

Systematic process of identifying, quantifying, and prioritizing vulnerabilities in a system.

### VA Process

```
1. Asset Discovery
   - What systems exist?
   - What applications are running?
   - What services are exposed?

2. Vulnerability Scanning
   - Automated scanning
   - Manual verification
   - False positive elimination

3. Vulnerability Analysis
   - Root cause analysis
   - Impact assessment
   - Exploit availability check

4. Risk Assessment
   - Likelihood calculation
   - Impact calculation
   - Risk scoring

5. Remediation Planning
   - Prioritization
   - Timeline definition
   - Resource allocation
```

### Common Vulnerability Scanners

```
Web Application Scanners:
┌─────────────────┬──────────────┬─────────────┐
│ Tool            │ Type         │ Cost        │
├─────────────────┼──────────────┼─────────────┤
│ Burp Suite      │ Commercial   │ $$$$        │
│ OWASP ZAP       │ Open Source  │ Free        │
│ Acunetix        │ Commercial   │ $$$         │
│ Nessus          │ Commercial   │ $$$         │
│ Nikto           │ Open Source  │ Free        │
└─────────────────┴──────────────┴─────────────┘

Network Scanners:
┌─────────────────┬──────────────┬─────────────┐
│ Tool            │ Type         │ Cost        │
├─────────────────┼──────────────┼─────────────┤
│ Nessus          │ Commercial   │ $$$         │
│ OpenVAS         │ Open Source  │ Free        │
│ Nexpose         │ Commercial   │ $$$         │
│ Qualys          │ Cloud        │ Subscription│
│ Nmap            │ Open Source  │ Free        │
└─────────────────┴──────────────┴─────────────┘

Code Scanners (SAST):
┌─────────────────┬──────────────┬─────────────┐
│ Tool            │ Type         │ Cost        │
├─────────────────┼──────────────┼─────────────┤
│ SonarQube       │ Commercial   │ $$          │
│ Checkmarx       │ Commercial   │ $$$$        │
│ Fortify         │ Commercial   │ $$$$        │
│ Semgrep         │ Open Source  │ Free        │
│ Bandit (Python) │ Open Source  │ Free        │
└─────────────────┴──────────────┴─────────────┘
```

---

## ⚔️ Penetration Testing {#pentest}

### What is Penetration Testing?

Authorized simulated attack on a system to evaluate its security.

### Penetration Testing Methodology

```
PTES (Penetration Testing Execution Standard) Phases:

1. Pre-engagement Interactions
   - Scope definition
   - Rules of engagement
   - Legal agreements

2. Intelligence Gathering
   - Open source intelligence (OSINT)
   - Social engineering (if in scope)
   - Technical reconnaissance

3. Threat Modeling
   - Identify assets
   - Identify threats
   - Attack vector identification

4. Vulnerability Analysis
   - Automated scanning
   - Manual verification
   - Vulnerability validation

5. Exploitation
   - Gaining access
   - Privilege escalation
   - Data access

6. Post-Exploitation
   - Maintaining access
   - Lateral movement
   - Data exfiltration (simulated)

7. Reporting
   - Executive summary
   - Technical findings
   - Remediation recommendations
```

### Types of Penetration Testing

```
1. Network Penetration Testing
   - External network testing
   - Internal network testing
   - Wireless network testing
   - Firewall testing

2. Application Penetration Testing
   - Web application testing
   - Mobile application testing
   - API testing
   - Thick client testing

3. Social Engineering Testing
   - Phishing campaigns
   - Vishing (voice phishing)
   - Physical intrusion
   - USB drops

4. Physical Penetration Testing
   - Building access
   - Lock picking
   - Badge cloning
   - Tailgating

5. Cloud Penetration Testing
   - AWS/Azure/GCP testing
   - Container security
   - Serverless testing
   - Cloud configuration review
```

---

## 🛠️ Security Testing Tools {#tools}

### Essential Security Testing Tools

### 1. Burp Suite

```
Features:
✓ Proxy (intercept and modify requests)
✓ Scanner (automated vulnerability scanning)
✓ Intruder (automated attacks)
✓ Repeater (manual request manipulation)
✓ Decoder (encoding/decoding)
✓ Comparer (compare data)
✓ Extender (add extensions)

Best For:
- Web application testing
- API testing
- Manual security testing

Editions:
- Community: Free (limited features)
- Professional: $449/year (full features)
```

### 2. OWASP ZAP (Zed Attack Proxy)

```
Features:
✓ Proxy
✓ Automated scanner
✓ API scanner
✓ AJAX spider
✓ Passive scanner
✓ Fuzzer

Best For:
- Web application testing
- CI/CD integration
- Budget-conscious teams

Cost: Free and Open Source
```

### 3. SQLMap

```
Features:
✓ Automatic SQL injection detection
✓ Database fingerprinting
✓ Data extraction
✓ Database server access
✓ Command execution (if possible)

Best For:
- SQL injection testing
- Database security assessment

Command Example:
sqlmap -u "http://target.com/page?id=1" --dbs

Cost: Free and Open Source
```

### 4. Nikto

```
Features:
✓ Web server scanning
✓ Dangerous files detection
✓ Server configuration issues
✓ Outdated software detection

Best For:
- Web server security assessment
- Configuration review

Command Example:
nikto -h http://target.com

Cost: Free and Open Source
```

### 5. Nmap

```
Features:
✓ Host discovery
✓ Port scanning
✓ Service detection
✓ OS detection
✓ Script scanning

Best For:
- Network discovery
✓ Port and service enumeration
✓ Network security assessment

Command Example:
nmap -sV -sC target.com

Cost: Free and Open Source
```

### 6. Metasploit Framework

```
Features:
✓ Exploit development
✓ Exploit execution
✓ Payload generation
✓ Post-exploitation modules
✓ Auxiliary modules

Best For:
✓ Penetration testing
✓ Exploit development
✓ Security research

Cost: Free (Community), Paid (Pro)
```

### 7. John the Ripper

```
Features:
✓ Password cracking
✓ Multiple hash types
✓ Dictionary attacks
✓ Brute force attacks
✓ Rule-based attacks

Best For:
- Password security testing
- Hash cracking

Cost: Free and Open Source
```

### 8. Wireshark

```
Features:
✓ Packet capture
✓ Protocol analysis
✓ Traffic filtering
✓ Traffic statistics

Best For:
- Network traffic analysis
- Protocol debugging
- Security analysis

Cost: Free and Open Source
```

### Tool Selection Guide

```
┌──────────────────────┬─────────────────────────────────────┐
│ Testing Need         │ Recommended Tools                   │
├──────────────────────┼─────────────────────────────────────┤
│ Web App Testing      │ Burp Suite, OWASP ZAP               │
│ SQL Injection        │ SQLMap, Burp Suite                  │
│ Network Scanning     │ Nmap, Nessus, OpenVAS               │
│ Password Testing     │ John the Ripper, Hashcat            │
│ Traffic Analysis     │ Wireshark, tcpdump                  │
│ Exploitation         │ Metasploit                          │
│ Code Analysis        │ SonarQube, Checkmarx, Semgrep       │
│ API Testing          │ Burp Suite, Postman + security tests│
└──────────────────────┴─────────────────────────────────────┘
```

---

## 🔐 Authentication & Authorization Testing {#auth}

### Authentication Testing

```
What to Test:

1. Password Policies
□ Minimum length (should be 12+)
□ Complexity requirements
□ Password history
□ Password expiration
□ Common password blocking

2. Brute Force Protection
□ Account lockout after failed attempts
□ Rate limiting
□ CAPTCHA implementation
□ Progressive delays

3. Session Management
□ Session ID randomness
□ Session timeout
□ Session invalidation on logout
□ Secure cookie flags
□ Session fixation prevention

4. Multi-Factor Authentication
□ MFA enforcement
□ MFA bypass testing
□ Recovery code security
□ MFA code expiration

5. Password Reset
□ Token expiration
□ Token reuse prevention
□ Security questions
□ Email verification
```

### Authorization Testing

```
What to Test:

1. Access Control
□ Vertical privilege escalation
□ Horizontal privilege escalation
□ Admin function access
□ API endpoint authorization
□ File access control

2. Business Logic Authorization
□ Workflow enforcement
□ Approval requirements
□ Role-based restrictions
□ Data access restrictions

3. API Authorization
□ Token validation
□ Scope validation
□ Resource-level authorization
□ Method-level authorization
```

### Authentication Test Cases

```
Test Case: Password Policy Validation

Steps:
1. Try to register with password "123"
   Expected: Rejected (too short)

2. Try to register with password "password"
   Expected: Rejected (too common)

3. Try to register with password "MyStr0ng!Pass"
   Expected: Accepted

4. Try to reuse old password after reset
   Expected: Rejected (password history)
```

```
Test Case: Brute Force Protection

Steps:
1. Try 5 incorrect passwords
   Expected: Account locked OR CAPTCHA shown

2. Try to login immediately after lockout
   Expected: Login prevented

3. Wait for lockout period
   Expected: Login allowed again

4. Check if lockout logged
   Expected: Security event logged
```

```
Test Case: Session Management

Steps:
1. Login and capture session ID
2. Logout
3. Try to use old session ID
   Expected: Session invalid, login required

4. Login from two devices
   Expected: Both sessions work (or policy enforced)

5. Check cookie flags
   Expected: Secure, HttpOnly, SameSite flags set
```

---

## 🔒 Data Protection Testing {#data}

### Data Encryption Testing

```
What to Test:

1. Data in Transit
□ HTTPS enforced (no HTTP)
□ TLS 1.2+ used
□ Valid certificates
□ HSTS implemented
□ Certificate pinning (mobile)

2. Data at Rest
□ Database encryption
□ File encryption
□ Backup encryption
□ Key management

3. Sensitive Data Handling
□ Passwords hashed (bcrypt, argon2)
□ Credit cards encrypted/tokenized
□ PII protected
□ No sensitive data in logs
□ No sensitive data in URLs
```

### Data Protection Checklist

```
┌──────────────────────┬──────────┬──────────┐
│ Check                │ Expected │ Actual   │
├──────────────────────┼──────────┼──────────┤
│ HTTPS enforced       │ Yes      │          │
│ TLS version >= 1.2   │ Yes      │          │
│ Password hashing     │ bcrypt   │          │
│ Credit card encrypt  │ Yes      │          │
│ No PII in logs       │ Yes      │          │
│ No passwords in URL  │ Yes      │          │
│ Secure cookies       │ Yes      │          │
│ API keys encrypted   │ Yes      │          │
└──────────────────────┴──────────┴──────────┘
```

---

## 🎬 Real Security Scenarios {#scenarios}

### Scenario 1: E-commerce Security Assessment

```
Context:
- Large e-commerce platform
- Handles credit card payments
- 1 million+ users
- PCI DSS compliance required

Security Testing Approach:

Phase 1: Reconnaissance (Week 1)
- Map all application endpoints
- Identify technologies
- Document user flows
- Identify entry points

Phase 2: Vulnerability Assessment (Week 2)
- Automated scanning (Burp, Nessus)
- Manual vulnerability identification
- API security testing
- Infrastructure scanning

Phase 3: Penetration Testing (Week 3)
- SQL injection testing
- XSS testing
- Authentication bypass attempts
- Payment manipulation testing
- Business logic testing

Phase 4: Reporting & Remediation (Week 4)
- Detailed findings report
- Work with dev team on fixes
- Re-testing
- Compliance documentation

Key Findings:
1. SQL Injection in search (Critical)
2. XSS in product reviews (High)
3. Price manipulation possible (Critical)
4. Missing security headers (Medium)
5. Session fixation (High)

Remediation:
- Parameterized queries implemented
- Input validation added
- Price calculation moved to server
- Security headers added
- Session management fixed

Outcome:
✓ All critical/high findings fixed
✓ PCI DSS compliance achieved
✓ Security posture improved
✓ Regular security testing instituted
```

### Scenario 2: Banking App Security Testing

```
Context:
- Mobile banking application
- Handles sensitive financial data
- RBI compliance required
- 500,000+ users

Security Requirements:
- RBI cybersecurity guidelines
- Data localization
- Customer protection
- Fraud prevention

Testing Focus Areas:

1. Authentication Security
□ MFA implementation
□ Biometric authentication
□ Session management
□ Account lockout

2. Transaction Security
□ Transaction signing
□ Amount verification
□ Beneficiary verification
□ Duplicate prevention

3. Data Protection
□ End-to-end encryption
□ Data at rest encryption
□ Key management
□ No sensitive data in logs

4. API Security
□ Authentication
□ Authorization
□ Rate limiting
□ Input validation

5. Mobile-Specific Security
□ Root/jailbreak detection
□ App tampering detection
□ Secure storage
□ Certificate pinning

Key Findings:
1. MFA bypass possible (Critical)
2. Transaction replay possible (Critical)
3. Root detection bypass (High)
4. Insecure data storage (High)
5. Certificate pinning not enforced (Medium)

Remediation:
- MFA flow fixed
- Transaction tokens implemented
- Root detection improved
- Encrypted storage implemented
- Certificate pinning enforced

Outcome:
✓ All critical findings fixed
✓ RBI compliance achieved
✓ Customer trust maintained
✓ Zero security incidents
```

### Scenario 3: Healthcare Portal Security

```
Context:
- Patient health records portal
- HIPAA compliance required
- Doctors, patients, admin users
- Sensitive medical data

Security Requirements:
- HIPAA compliance
- Patient data privacy
- Audit logging
 Access controls
- Data breach prevention

Testing Focus:

1. Access Control Testing
□ Patient can only see own records
□ Doctor sees only assigned patients
□ Admin can't see medical records
□ Role-based access verification

2. Audit Logging
□ All access logged
□ Who accessed what and when
□ Failed access attempts logged
□ Logs protected from tampering

3. Data Privacy
□ PHI encrypted
□ No PHI in URLs
□ No PHI in logs
□ Secure data transmission

4. Session Security
□ Automatic timeout
□ Session invalidation
□ Concurrent session limits
□ Secure logout

Key Findings:
1. Horizontal access control bypass (Critical)
2. PHI in URL parameters (High)
3. Insufficient audit logging (High)
4. Session timeout not working (Medium)
5. No concurrent session limits (Medium)

Remediation:
- Access control fixed
- URLs cleaned of PHI
Audit logging enhanced
- Session timeout implemented
- Concurrent session limits added

Outcome:
✓ HIPAA compliance achieved
✓ Patient privacy protected
✓ Audit trail complete
✓ Zero breaches
```

### Scenario 4: Startup API Security Review

```
Context:
- Fast-growing startup
- REST API for mobile app
- Limited security resources
- Need quick but thorough review

Constraints:
- 1 week timeline
- Small team
- Budget constraints
- Production in 2 weeks

Approach:

Day 1-2: Automated Testing
- OWASP ZAP scan
- API security scan
- Dependency check
- Configuration review

Day 3-4: Manual Testing
- Authentication testing
- Authorization testing
- Input validation testing
- Business logic testing

Day 5: Reporting
- Priority findings only
- Quick wins identified
- Long-term recommendations

Key Findings:
1. No authentication on some endpoints (Critical)
2. API keys in client code (High)
3. No rate limiting (High)
4. Verbose error messages (Medium)
5. Outdated dependencies (Medium)

Quick Fixes (Before Launch):
✓ Add authentication to all endpoints
✓ Remove hardcoded API keys
✓ Implement rate limiting
✓ Update critical dependencies
✓ Fix error handling

Long-term Recommendations:
- Implement API gateway
- Add WAF
- Regular security testing
- Security training for devs
- Bug bounty program

Outcome:
✓ Critical issues fixed before launch
✓ Secure production deployment
✓ Security roadmap created
✓ No incidents in first 6 months
```

---

## 🐛 Common Security Vulnerabilities {#vulnerabilities}

### Vulnerability 1: SQL Injection

```
Description:
Attacker can execute arbitrary SQL commands.

How to Find:
- Test all input fields
- Look for database errors
- Use SQLMap for automation

Example:
Input: ' OR '1'='1
Result: Bypasses authentication

Impact:
- Data breach
- Data modification
- Authentication bypass
- Complete database access

Fix:
- Use parameterized queries
- Input validation
- Least privilege database accounts
```

### Vulnerability 2: Cross-Site Scripting (XSS)

```
Description:
Attacker can inject malicious scripts.

Types:
1. Reflected XSS - Script in URL
2. Stored XSS - Script in database
3. DOM XSS - Client-side injection

Example:
Input: <script>alert('XSS')</script>
Result: Script executes in victim's browser

Impact:
- Session hijacking
- Credential theft
- Malware distribution
- Defacement

Fix:
- Output encoding
- Input validation
- Content-Security-Policy header
- Sanitize user input
```

### Vulnerability 3: Broken Authentication

```
Description:
Authentication mechanism can be bypassed.

Common Issues:
- Weak passwords allowed
- No brute force protection
- Session fixation
- Credential stuffing

Example:
- Try 1000 passwords, no lockout
- Session ID in URL
- Predictable session IDs

Impact:
- Account takeover
- Unauthorized access
- Data breach

Fix:
- Strong password policies
- MFA implementation
- Account lockout
- Secure session management
```

### Vulnerability 4: Sensitive Data Exposure

```
Description:
Sensitive data not properly protected.

Common Issues:
- No encryption
- Weak encryption
- Data in logs
- Data in URLs

Example:
- Credit cards in plain text
- Passwords not hashed
- SSN in response

Impact:
- Data breach
- Identity theft
- Financial fraud
- Compliance violations

Fix:
- Encrypt sensitive data
- Hash passwords
- Minimize data collection
- Secure key management
```

### Vulnerability 5: XML External Entity (XXE)

```
Description:
XML parser processes external entities.

Example:
<?xml version="1.0"?>
<!DOCTYPE foo [
<!ENTITY xxe SYSTEM "file:///etc/passwd">
]>
<foo>&xxe;</foo>

Impact:
- File disclosure
- SSRF
- Denial of service

Fix:
- Disable external entities
- Use JSON instead of XML
- Input validation
- Updated XML parsers
```

### Vulnerability 6: Security Misconfiguration

```
Description:
System insecurely configured.

Common Issues:
- Default credentials
- Verbose errors
- Unnecessary features
- Missing security headers

Example:
- admin/admin works
- Stack traces shown
- Directory listing enabled

Impact:
- Information disclosure
- Unauthorized access
- Attack surface increase

Fix:
- Hardening guidelines
- Remove defaults
- Custom error pages
- Security headers
```

### Vulnerability 7: Insecure Deserialization

```
Description:
Untrusted serialized data processed.

Example:
Attacker sends malicious serialized object
Application deserializes it
Arbitrary code executes

Impact:
- Remote code execution
- Authentication bypass
- Data manipulation

Fix:
- Don't deserialize untrusted data
- Use signed serialized data
- Input validation
- Integrity checks
```

---

## 📝 Security Test Cases {#test-cases}

### Test Case 1: SQL Injection Testing

```
Test Case ID: TC_SEC_001
Test Case Name: SQL Injection in Login Form
Test Type: Security
Priority: CRITICAL

Objective:
Verify login form is not vulnerable to SQL injection

Test Steps:

| Step | Input | Expected Result |
|------|-------|-----------------|
| 1 | Username: admin' -- | Login fails |
|    | Password: anything  | (SQL comment prevents injection) |
| 2 | Username: ' OR '1'='1 | Login fails |
|    | Password: anything  | (Injection prevented) |
| 3 | Username: admin       | Normal behavior |
|    | Password: wrongpass  | "Invalid credentials" |
| 4 | Username: 1; DROP TABLE users;-- | Login fails |
|    | Password: anything  | (No SQL execution) |

Pass Criteria:
✓ All injection attempts fail
✓ No database errors shown
✓ Generic error messages
✓ Attempts logged
```

### Test Case 2: XSS Testing

```
Test Case ID: TC_SEC_002
Test Case Name: XSS in Comment Section
Test Type: Security
Priority: HIGH

Objective:
Verify comment section prevents XSS attacks

Test Steps:

| Step | Input | Expected Result |
|------|-------|-----------------|
| 1 | <script>alert('XSS')</script> | Script tags escaped |
| 2 | <img src=x onerror=alert(1)> | Code displayed as text |
| 3 | javascript:alert(1) | Not executed |
| 4 | <iframe src="evil.com"></iframe> | Blocked/escaped |

Pass Criteria:
✓ All scripts escaped
✓ No script execution
✓ Input displayed safely
✓ CSP headers present
```

### Test Case 3: Authentication Bypass

```
Test Case ID: TC_SEC_003
Test Case Name: Authentication Bypass Testing
Test Type: Security
Priority: CRITICAL

Objective:
Verify authentication cannot be bypassed

Test Steps:

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Access /admin without login | Redirect to login |
| 2 | Modify response to bypass login | Server validates |
| 3 | Access API without token | 401 Unauthorized |
| 4 | Reuse old session token | Session invalid |
| 5 | Access another user's data | Access denied |

Pass Criteria:
✓ All bypass attempts fail
✓ Proper authentication required
✓ Authorization enforced
✓ Attempts logged
```

### Test Case 4: Brute Force Protection

```
Test Case ID: TC_SEC_004
Test Case Name: Brute Force Protection
Test Type: Security
Priority: HIGH

Objective:
Verify system prevents brute force attacks

Test Steps:

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Try 5 incorrect passwords | Account locked OR CAPTCHA |
| 2 | Try 6th attempt | Login prevented |
| 3 | Wait 15 minutes | Lockout cleared |
| 4 | Check logs | Failed attempts logged |
| 5 | Try from different IP | Same protection applies |

Pass Criteria:
✓ Account locks after threshold
✓ CAPTCHA shown (if implemented)
✓ Attempts logged
✓ Lockout message clear
```

### Test Case 5: Session Management

```
Test Case ID: TC_SEC_005
Test Case Name: Session Security Testing
Test Type: Security
Priority: HIGH

Objective:
Verify session management is secure

Test Steps:

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Login and capture session ID | Session created |
| 2 | Logout | Session invalidated |
| 3 | Reuse old session ID | Login required |
| 4 | Check cookie flags | Secure, HttpOnly, SameSite |
| 5 | Wait for timeout period | Session expires |
| 6 | Try session fixation | New session issued |

Pass Criteria:
✓ Session properly invalidated
✓ Secure cookie flags set
✓ Timeout working
✓ Session fixation prevented
```

### Test Case 6: Data Encryption

```
Test Case ID: TC_SEC_006
Test Case Name: Data Encryption Verification
Test Type: Security
Priority: CRITICAL

Objective:
Verify sensitive data is properly encrypted

Test Steps:

| Step | Check | Expected Result |
|------|-------|-----------------|
| 1 | Check HTTPS enforcement | HTTP redirects to HTTPS |
| 2 | Check TLS version | TLS 1.2 or higher |
| 3 | Check password storage | Hashed (bcrypt/argon2) |
| 4 | Check database | Sensitive data encrypted |
| 5 | Check network traffic | Encrypted (Wireshark) |
| 6 | Check logs | No sensitive data in logs |

Pass Criteria:
✓ HTTPS enforced
✓ Strong encryption used
✓ Passwords properly hashed
✓ No sensitive data exposed
```

### Test Case 7: Access Control

```
Test Case ID: TC_SEC_007
Test Case Name: Horizontal Privilege Escalation
Test Type: Security
Priority: CRITICAL

Objective:
Verify users cannot access other users' data

Test Steps:

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Login as User A | Login successful |
| 2 | Access /api/orders/123 | Own order displayed |
| 3 | Change to /api/orders/124 | Access denied (other's order) |
| 4 | Try different user IDs | All denied except own |
| 5 | Check API responses | No data leakage |

Pass Criteria:
✓ Cannot access other users' data
✓ Proper authorization checks
✓ Error messages don't leak info
✓ Attempts logged
```

---

## ✅ Security Testing Checklist {#checklist}

### Pre-Testing Checklist

```
□ Scope clearly defined
□ Authorization obtained
□ Rules of engagement signed
□ Emergency contacts identified
□ Backup of test environment
□ Tools installed and configured
□ Test accounts created
□ Documentation templates ready
```

### Authentication Testing Checklist

```
□ Password policy enforced
□ Brute force protection working
□ Account lockout implemented
□ MFA functioning
□ Session management secure
□ Password reset secure
□ Remember me functionality secure
□ Logout properly invalidates session
```

### Authorization Testing Checklist

```
□ Vertical privilege escalation prevented
□ Horizontal privilege escalation prevented
□ Admin functions protected
□ API endpoints authorized
□ File access controlled
□ Direct object references secured
□ Business logic enforced
```

### Input Validation Checklist

```
□ SQL injection prevented
□ XSS prevented
□ Command injection prevented
□ XXE prevented
□ File upload secured
□ Path traversal prevented
□ CSRF protection implemented
□ SSRF prevented
```

### Data Protection Checklist

```
□ HTTPS enforced
□ TLS 1.2+ used
□ Passwords hashed properly
□ Sensitive data encrypted at rest
□ No sensitive data in logs
□ No sensitive data in URLs
□ Secure cookie flags set
□ Keys properly managed
```

### Configuration Checklist

```
□ No default credentials
□ Error messages generic
□ Security headers present
□ Unnecessary features disabled
□ Directory listing disabled
□ Debug mode disabled
□ CORS properly configured
□ Rate limiting implemented
```

### Logging & Monitoring Checklist

```
□ Security events logged
□ Failed logins logged
□ Access control failures logged
□ Input validation failures logged
□ Logs protected from tampering
□ Real-time monitoring enabled
□ Alerts configured
□ Log retention policy defined
```

---

## 🎤 Security Testing Interview Questions {#interview}

### Q1: What is the difference between Vulnerability Assessment and Penetration Testing?

**Answer:**

```
Vulnerability Assessment:
- Purpose: Identify and catalog vulnerabilities
- Approach: Automated scanning + manual verification
- Depth: Broad coverage, surface-level analysis
- Output: List of vulnerabilities with severity
- Analogy: Home inspection - lists all issues

Penetration Testing:
- Purpose: Exploit vulnerabilities to assess impact
- Approach: Manual exploitation + automated tools
- Depth: Deep dive into specific vulnerabilities
- Output: Exploitation proof + business impact
- Analogy: Burglar testing - actually tries to break in

Key Differences:

┌─────────────────┬──────────────────┬──────────────────┐
│ Aspect          │ VA               │ Pentest          │
├─────────────────┼──────────────────┼──────────────────┤
│ Goal            │ Find vulns       │ Exploit vulns    │
│ Automation      │ Mostly automated │ Mostly manual    │
│ Coverage        │ Broad            │ Deep             │
│ False Positives │ Possible         │ Verified         │
│ Cost            │ Lower            │ Higher           │
│ Frequency       │ Regular (monthly)│ Periodic (yearly)│
└─────────────────┴──────────────────┴──────────────────┘

My Approach:
I always recommend doing VA first to get broad coverage,
then pentesting for critical systems to understand real
world impact.
```

### Q2: How do you test for SQL Injection?

**Answer:**

```
My SQL Injection Testing Process:

1. Identify Injection Points
   - All input fields
   - URL parameters
   - HTTP headers
   - Cookie values
   - File uploads

2. Initial Testing
   - Single quote: '
   - Double quote: "
   - Boolean: ' OR '1'='1
   - Time-based: '; WAITFOR DELAY '0:0:5'--

3. Error Analysis
   - Database errors indicate vulnerability
   - Verbose errors help identify DB type
   - No errors doesn't mean safe

4. Confirmation Tests
   - Union-based: ' UNION SELECT NULL--
   - Boolean-based: ' AND 1=1-- vs ' AND 1=2--
   - Time-based: ' WAITFOR DELAY '0:0:5'--

5. Automated Tools
   - SQLMap for comprehensive testing
   - Burp Suite Scanner
   - OWASP ZAP

6. Manual Exploitation
   - Database fingerprinting
   - Schema extraction
   - Data extraction (if authorized)

Example from my testing:
Found SQLi in search parameter:
Input: ' UNION SELECT username, password FROM users--
Result: All usernames and password hashes extracted

Impact: Complete database compromise
Fix: Implemented parameterized queries

Prevention:
✓ Parameterized queries
✓ Input validation
✓ WAF rules
✓ Least privilege DB accounts
✓ Regular security testing
```

### Q3: What are the most critical security risks for web applications?

**Answer:**

```
Based on OWASP Top 10 and my experience:

1. Broken Access Control (Most Critical)
   - Users accessing unauthorized resources
   - Impact: Data breach, privilege escalation
   - Example: IDOR vulnerabilities

2. Injection Attacks
   - SQL, NoSQL, Command injection
   - Impact: Data breach, system compromise
   - Example: SQLi in login form

3. Cryptographic Failures
   - Unencrypted sensitive data
   - Weak encryption
   - Impact: Data exposure
   - Example: Plain text passwords

4. Authentication Failures
   - Weak passwords
   - No MFA
   - Session management issues
   - Impact: Account takeover

5. Security Misconfiguration
   - Default credentials
   - Verbose errors
   - Unnecessary features
   - Impact: Information disclosure, attacks

My Priority for Testing:
1. Authentication/Authorization
2. Injection vulnerabilities
3. Data protection
4. Configuration issues
5. Logging/monitoring

Business Impact Focus:
I always prioritize testing based on business impact.
For e-commerce: Payment security, business logic
For healthcare: Data privacy, access controls
For banking: Transaction security, authentication
```

### Q4: How do you stay updated with latest security vulnerabilities?

**Answer:**

```
My Information Sources:

Daily:
✓ Twitter security community
✓ Reddit r/netsec, r/cybersecurity
✓ Hacker News
✓ Security vendor blogs

Weekly:
✓ OWASP updates
✓ CVE databases
✓ Vendor security advisories
✓ SANS Internet Storm Center

Monthly:
✓ Security podcasts
✓ Webinars
✓ Research papers
✓ Industry reports

Key Resources:

Vulnerability Databases:
- CVE (Common Vulnerabilities and Exposures)
- NVD (National Vulnerability Database)
- OWASP Top 10
✓ CWE (Common Weakness Enumeration)

Security News:
- The Hacker News
- BleepingComputer
- Krebs on Security
- Dark Reading

Communities:
- OWASP local chapters
- Security conferences (DEF CON, Black Hat)
- LinkedIn security groups
- Discord security servers

Continuous Learning:
- Certified Ethical Hacker (CEH)
- Offensive Security Certified Professional (OSCP)
- GIAC certifications
- Online courses (Pluralsight, Coursera)

Practical Practice:
- HackTheBox
- TryHackMe
- Bug bounty programs
- CTF competitions
```

### Q5: What is your approach to security testing in CI/CD?

**Answer:**

```
My DevSecOps Approach:

Shift-Left Security:
Integrate security early and throughout the pipeline

CI/CD Pipeline Security Stages:

┌─────────────────────────────────────────────────────────┐
│                    CI/CD Pipeline                       │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  Code → Build → Test → Deploy → Production             │
│   │       │       │       │         │                  │
│   │       │       │       │         │                  │
│   ↓       ↓       ↓       ↓         ↓                  │
│ SAST   SCA      DAST    Container  RASP                │
│        Deps     IAST    Scanning    │                  │
│                                                         │
│  └─────────────────────────────────────────────────────┘│
│              Security Gates at Each Stage               │
└─────────────────────────────────────────────────────────┘

Stage 1: Code Commit
- Pre-commit hooks for secrets detection
- IDE security plugins
- Developer security training

Stage 2: Build
- SAST scanning (SonarQube, Checkmarx)
- Dependency scanning (OWASP Dependency-Check)
- Container image scanning
- Infrastructure as Code scanning

Stage 3: Test
- DAST scanning (OWASP ZAP, Burp)
- API security testing
- Penetration testing (periodic)
- Security regression tests

Stage 4: Deploy
- Configuration scanning
- Compliance validation
- Final security sign-off

Stage 5: Production
- RASP (Runtime Application Self-Protection)
- Continuous monitoring
- Vulnerability management
- Incident response

Security Gates:

┌──────────────────┬──────────────────────────────────────┐
│ Gate             │ Criteria                             │
├──────────────────┼──────────────────────────────────────┤
│ SAST Gate        │ No critical/high vulnerabilities     │
├──────────────────┼──────────────────────────────────────┤
│ Dependency Gate  │ No known vulnerable dependencies     │
├──────────────────┼──────────────────────────────────────┤
│ DAST Gate        │ No critical web vulnerabilities      │
├──────────────────┼──────────────────────────────────────┤
│ Manual Review    │ Required for critical changes        │
└──────────────────┴──────────────────────────────────────┘

Tools I Use:
- SAST: SonarQube, Semgrep
- SCA: OWASP Dependency-Check, Snyk
- DAST: OWASP ZAP, Burp Suite
- Container: Trivy, Clair
- Secrets: GitLeaks, TruffleHog

Key Success Factors:
✓ Fast feedback (developers shouldn't wait long)
✓ Clear remediation guidance
✓ False positive management
✓ Security champion program
✓ Regular training
✓ Metrics and reporting
```

### Q6: How do you report security vulnerabilities to developers?

**Answer:**

```
My Reporting Approach:

Principles:
1. Clear and actionable
2. Non-accusatory tone
3. Business impact focused
4. Include remediation guidance

Vulnerability Report Structure:

┌─────────────────────────────────────────┐
│ VULNERABILITY REPORT                    │
├─────────────────────────────────────────┤
│ Title: SQL Injection in User Search     │
│                                         │
│ Severity: CRITICAL                      │
│ CVSS Score: 9.8                         │
│                                         │
│ Description:                            │
│ The user search functionality is        │
│ vulnerable to SQL injection attacks.    │
│ An attacker can extract sensitive data  │
│ from the database.                      │
│                                         │
│ Location:                               │
│ URL: /admin/users/search                │
│ Parameter: search_query                 │
│                                         │
│ Steps to Reproduce:                     │
│ 1. Navigate to /admin/users/search      │
│ 2. Enter: ' OR '1'='1                   │
│ 3. Observe all users returned           │
│ 4. Enter: ' UNION SELECT ...            │
│ 5. Data extracted                       │
│                                         │
│ Proof of Concept:                       │
│ [Screenshot/Video attached]             │
│                                         │
│ Business Impact:                        │
│ - Complete database access possible     │
│ - Customer data at risk                 │
│ - Regulatory compliance violation       │
│ - Potential fines up to ₹X crore        │
│                                         │
│ Remediation:                            │
│ 1. Use parameterized queries            │
│ 2. Input validation                     │
│ 3. Implement least privilege            │
│                                         │
│ Code Example:                           │
│ [Before and After code]                 │
│                                         │
│ References:                             │
│ - OWASP SQL Injection                   │
│ - CWE-89                                │
└─────────────────────────────────────────┘

Communication Tips:

Do's:
✓ Focus on the vulnerability, not the person
✓ Explain business impact clearly
✓ Provide working remediation code
✓ Offer to help with fixes
✓ Follow up regularly

Don'ts:
✗ Don't blame or shame
✗ Don't use overly technical language
✗ Don't just dump findings
✗ Don't disappear after reporting
✗ Don't exaggerate severity

Developer Relationship:
I maintain good relationships with dev teams by:
- Being available for questions
- Providing working code examples
- Understanding their constraints
- Celebrating security wins together
- Regular security training sessions
```

---

## ✅ Security Testing Quick Reference

### Quick Vulnerability Reference

```
┌──────────────────────┬─────────────────────────────────────┐
│ Vulnerability        │ Quick Test                          │
├──────────────────────┼─────────────────────────────────────┤
│ SQL Injection        │ Input: ' OR '1'='1                  │
│ XSS                  │ Input: <script>alert(1)</script>    │
│ Command Injection    │ Input: ; ls -la                     │
│ Path Traversal       │ Input: ../../etc/passwd             │
│ SSRF                 │ Input: http://169.254.169.254/      │
│ XXE                  │ Inject XML with external entity     │
└──────────────────────┴─────────────────────────────────────┘
```

### Security Headers Checklist

```
Essential Security Headers:

□ Content-Security-Policy: default-src 'self'
□ X-Frame-Options: DENY
□ X-Content-Type-Options: nosniff
□ X-XSS-Protection: 1; mode=block
□ Strict-Transport-Security: max-age=31536000
□ Referrer-Policy: strict-origin-when-cross-origin
□ Permissions-Policy: [features you allow]
```

### Emergency Response Checklist

```
If Security Incident Found:

□ Stop testing immediately
□ Document what you found
□ Notify stakeholder immediately
□ Don't exploit beyond confirmation
□ Don't delete/modify data
□ Maintain confidentiality
□ Follow incident response plan
```

---

## 📊 Summary

### Key Takeaways

```
✅ Security testing is critical for all applications
✅ OWASP Top 10 is essential knowledge
✅ Combine automated and manual testing
✅ Report findings clearly with remediation
✅ Security is everyone's responsibility
✅ Stay updated with latest vulnerabilities
✅ Integrate security in CI/CD pipeline
✅ Regular testing is mandatory
```

### Career Advice

```
📌 Learn OWASP Top 10 thoroughly
📌 Master at least one security testing tool
📌 Understand common vulnerabilities
📌 Practice on vulnerable applications (DVWA, WebGoat)
📌 Get security certifications (CEH, OSCP, Security+)
📌 Participate in bug bounty programs
📌 Join security communities
📌 Stay updated continuously
```

---

*Security Testing Module*  
*For QA Professionals & Aspirants*  
*Language: Hinglish (Hindi + English)*  
*Created: 2026*

**Happy Security Testing! 🔒✅**
