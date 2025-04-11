# OWASP Payload Guide

This document provides payload examples, detection techniques, and exploitation commands for common OWASP Top 10 vulnerabilities. Each section contains a brief description, how to identify the vulnerability, and example payloads (primarily using `curl` or similar command-line tools).

---

## ✅ 1. Server-Side Request Forgery (SSRF)
### How to Identify:
- Any functionality that fetches a URL from user input.
- Look for parameters like `url=`, `redirect=`, `next=`, `stockApi=`, etc.

### Exploitation Examples (curl):
Refer to the document titled **SSRFF Payloads with Curl Examples** for detailed payloads.

---

## ✅ 2. Cryptographic Failures
### How to Identify:
- Weak or no encryption in transit (e.g., HTTP instead of HTTPS).
- Hardcoded secrets or keys in source code.
- Reuse of nonces, IVs, or predictable keys.
- Lack of password hashing, or use of weak algorithms (e.g., MD5, SHA1).
- Exposure of sensitive data in logs, URLs, or client-side code.

### How to Exploit:

#### 1. **Discovering Sensitive Data in Transit (Unencrypted)**
```
curl -I http://example.com/login
```
If the response is not redirected to HTTPS or sensitive data (like tokens) is being sent over plain HTTP, it's vulnerable.

#### 2. **Checking for Weak JWT Secrets**
Use [`jwt_tool`](https://github.com/ticarpi/jwt_tool) or `jwt-cracker`:
```
python3 jwt_tool.py eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9... -C -d wordlist.txt
```

#### 3. **Detecting Insecure Password Hashing (MD5 / SHA1)**
Intercept a registration/login request and analyze the hash value:
```
echo -n "password" | md5sum
```
If the hash matches, they're using unsalted MD5.

#### 4. **Hardcoded Keys in JS Files**
```
curl https://example.com/static/js/main.js | grep -i 'secret\|key\|token'
```
Look for sensitive information exposed in frontend source code.

#### 5. **Testing Reused IV or Plaintext Output**
If ciphertexts repeat or show patterns, reuse of IV/non-random generation is suspected.
Use tools like `CyberChef` or scripts to visualize patterns.

### Mitigation Checklist:
- Always use HTTPS.
- Use strong cryptographic algorithms (e.g., AES-GCM, bcrypt, PBKDF2).
- Never hardcode keys/secrets in client-side code.
- Use proper randomization for IVs, salts, tokens.
- Do not log sensitive information.

---

## 🔧 3. Security Misconfiguration
### How to Identify:
- Default credentials left unchanged.
- Admin interfaces exposed publicly.
- Directory listing enabled.
- Error messages leak stack traces or sensitive data.

### Exploitation:
```
curl http://example.com/admin
```
```
curl http://example.com/.git/config
```
If these return responses, misconfigurations exist.

### Tip:
Use tools like Nikto, Nmap scripts, or manual fuzzing to find exposed misconfigurations.

---

## ⚠️ 4. Vulnerable and Outdated Components
### How to Identify:
- Fingerprint software versions (headers, responses, etc).
- Use tools like Wappalyzer, WhatWeb, or `nmap --script http-headers`

### Example:
```
curl -I http://example.com
```
Look for headers like `Server: Apache/2.2.14 (Win32)`

### Exploitation:
Find known exploits using CVE search or Exploit-DB.

---

## 🔐 5. Identification and Authentication Failures
### How to Identify:
- Weak or no password policies.
- No MFA.
- Predictable or brute-forceable login.

### Exploitation Example:
Use `hydra` or `ffuf`:
```
hydra -l admin -P rockyou.txt http-post-form "/login:username=^USER^&password=^PASS^:Invalid"
```

---

## 🧬 6. Software and Data Integrity Failures
### How to Identify:
- Application loads code or plugins from remote sources without validation.
- No integrity check (e.g., missing Subresource Integrity - SRI in scripts).

### Exploitation Example:
Inject malicious JS in a third-party dependency the app loads:
```
curl https://cdn.example.com/mylib.js  # Check if it's modifiable or poisoned
```

---

## 📉 7. Security Logging and Monitoring Failures
### How to Identify:
- No logs for authentication, data access, admin actions.
- Logs don’t capture IPs, timestamps, or user IDs.

### Exploitation:
Perform attacks and see if there’s any alerting (e.g., brute force login, account enumeration).
If nothing happens and logs are blank or minimal, logging is poor.

### Example:
```
curl -X POST -d "username=admin&password=wrong" http://example.com/login
```
Repeat several times, then check logs if accessible (or notice lack of alerts).

---

Let me know which category you'd like to expand on next.

