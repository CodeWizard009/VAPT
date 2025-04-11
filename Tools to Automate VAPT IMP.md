# Tools and their Usage for Automated VAPT "Sn1per Excluded"
---

```markdown
# 🔍 All-in-One Vulnerability Scanners for OWASP Testing

This guide lists all-in-one vulnerability scanning tools you can install using `apt` or `pacman` on Linux distributions. These tools help automate the discovery of OWASP Top 10 vulnerabilities.

---

## ✅ OWASP ZAP (Zed Attack Proxy)

### 🔹 Description:
A full-featured scanner for web application security. Supports both GUI and CLI.

### 🔹 Detects:
- Broken Access Control  
- Injection (SQLi, XSS, etc.)  
- Cryptographic Failures  
- Security Misconfigurations  
- SSRF  
- Many more

### 🔹 Install:
```bash
# Debian/Ubuntu
sudo apt install zaproxy

# Arch/Garuda/Parrot
sudo pacman -S zaproxy
```

### 🔹 Usage (CLI):
```bash
zap-cli quick-scan --self-contained --start-options "-config api.disablekey=true" https://example.com
```

---

## ✅ Nikto

### 🔹 Description:
A lightweight web server scanner focused on misconfigurations, outdated software, and insecure files.

### 🔹 Detects:
- Security misconfigurations  
- Default credentials  
- Dangerous files  
- Outdated components

### 🔹 Install:
```bash
sudo apt install nikto
# or
sudo pacman -S nikto
```

### 🔹 Usage:
```bash
nikto -h https://example.com
```

---

## ✅ Nuclei (by ProjectDiscovery)

### 🔹 Description:
A fast and customizable vulnerability scanner using community-built templates.

### 🔹 Detects:
- All OWASP Top 10 vulnerabilities  
- CVEs  
- Tech stack misconfigurations  
- Subdomain takeover, SSRF, etc.

### 🔹 Install:
```bash
# Scripted install
curl -s https://install.nuclei.sh | bash

# (or if in repo)
sudo pacman -S nuclei
```

### 🔹 Usage:
```bash
nuclei -u https://example.com -o nuclei_report.txt
```

---

## ✅ Wapiti

### 🔹 Description:
A web application vulnerability scanner that scans all URLs and tries multiple attack payloads.

### 🔹 Detects:
- XSS  
- SQL Injection  
- Command Injection  
- File Disclosure  
- SSRF  
- CRLF, XXE, etc.

### 🔹 Install:
```bash
sudo apt install wapiti
# or
sudo pacman -S wapiti
```

### 🔹 Usage:
```bash
wapiti -u https://example.com -f html -o wapiti_report
```

---

## 🔚 Summary Table

| Tool     | Detects OWASP Top 10 | GUI/CLI | Installable |
|----------|----------------------|---------|--------------|
| **ZAP**      | ✅✅✅✅✅✅✅✅✅✅ | GUI + CLI | apt/pacman |
| **Nikto**    | ✅✅✅             | CLI only  | apt/pacman |
| **Nuclei**   | ✅✅✅✅✅✅✅✅✅✅ | CLI only  | Script/pacman |
| **Wapiti**   | ✅✅✅✅✅          | CLI only  | apt/pacman |

---

## 🛠️ Tips
- Run all scanners in parallel for maximum coverage.
- Combine `nmap` and `whatweb` for pre-enumeration.
- Always scan in authorized/controlled environments.

```

Let me know if you'd like the same format for Burp extensions or browser plugins too.
