**VAPT Practical Question Bank – Solution Notes**

_Answers prepared from student (1).DOCX_

Prepared in an easy-to-read, exam-friendly format.  
_Use only on authorized lab systems and academic test environments._

| Format | Recite-and-perform practical answers |
| --- | --- |
| Purpose | Quick writing help + command recall during viva/practical |

**How to use this document:** For each question, start with the concept, write the command or steps, and end with a short analysis/observation line.

# Q1. Metasploit auxiliary vulnerability scanning

Use Metasploit auxiliary scanners to identify services and weaknesses on a lab target.

*   Open Metasploit, select a scanner module, set the target, then run the scan.

Suggested command(s):

msfconsole

search auxiliary scanner

use auxiliary/scanner/portscan/tcp

set RHOSTS <target-ip>

run

What to write in analysis / conclusion:

*   Analyze the open ports and detected services. Note any outdated or exposed services for further verification.

# Q2. Nikto web server scan

Nikto scans a web server for common vulnerabilities, default files, dangerous scripts, and insecure headers.

Suggested command(s):

nikto -h http://<target>

What to write in analysis / conclusion:

*   Document findings such as missing headers, outdated server version, exposed admin paths, and risky files.

# Q3. Physical layer attack

Physical layer attacks target hardware, cables, signals, or transmission media.

What to write in analysis / conclusion:

*   Example: wiretapping. An attacker taps a cable or device port to capture raw electrical/optical signals.

# Q4. Create dedicated SSH user and allow only that user

Create a user, set a password, and restrict SSH access through sshd\_config.

Suggested command(s):

sudo adduser sshuser

sudo nano /etc/ssh/sshd\_config

AllowUsers sshuser

sudo systemctl restart ssh

What to write in analysis / conclusion:

*   This ensures only the listed account can log in through SSH.

# Q5. Footprinting with Netcraft and DNSDumpster

Use Netcraft for hosting/server details and DNSDumpster for DNS intelligence.

What to write in analysis / conclusion:

*   Record hosting provider, IP addresses, NS records, MX records, subdomains, and any exposed infrastructure details.

# Q6. Application layer attack

Application layer attacks target web apps, email, DNS, or other user-facing services.

What to write in analysis / conclusion:

*   Example: SQL injection. Malicious input is inserted into a query to read, modify, or bypass database logic.

# Q7. tcpdump capture and analysis

Capture packets for HTTP/HTTPS, DNS, and ICMP, then inspect the traffic.

Suggested command(s):

sudo tcpdump -i <iface> port 80 or port 443 -w web.pcap

sudo tcpdump -i <iface> port 53 -w dns.pcap

sudo tcpdump -i <iface> icmp -w icmp.pcap

What to write in analysis / conclusion:

*   HTTP/HTTPS shows web communication, DNS shows name lookups, and ICMP shows ping/troubleshooting packets.

# Q8. DNS footprinting with Fierce

Fierce is used to enumerate DNS records, subdomains, and name servers.

Suggested command(s):

fierce --domain <target-domain>

What to write in analysis / conclusion:

*   Write down subdomains, NS servers, and any DNS information that expands the attack surface.

# Q9. Network layer attack

Network layer attacks target IP routing and packet delivery.

What to write in analysis / conclusion:

*   Example: IP spoofing. The attacker forges the source IP address to hide identity or bypass simple trust rules.

# Q10. DNS analysis with nslookup and dig

Use nslookup and dig to retrieve multiple DNS records and compare output style.

Suggested command(s):

nslookup <domain>

dig <domain> A

dig <domain> MX

dig <domain> NS

dig <domain> SOA

dig <domain> TXT

What to write in analysis / conclusion:

*   nslookup is simple and interactive. dig is more detailed and shows TTL, flags, and answer sections clearly.

# Q11. Google hacking / advanced search operators

Use operators to find indexed pages, exposed files, or public information about an organization.

Suggested command(s):

site:example.com

intitle:index of

inurl:admin

filetype:pdf site:example.com

allintext:confidential example

What to write in analysis / conclusion:

*   Document publicly exposed files, login panels, directory listings, and metadata visible through search engines.

# Q12. Data link layer attack

Data link layer attacks target MAC addresses, switches, and LAN communication.

What to write in analysis / conclusion:

*   Example: ARP spoofing. The attacker sends forged ARP replies to redirect local traffic through their system.

# Q13. Burp Intruder parameter testing

Capture a request in Burp, send it to Intruder, mark the input positions, load payloads, and start the attack.

What to write in analysis / conclusion:

*   Observe differences in response length, status code, or error messages to identify weak input validation.

# Q14. theHarvester footprinting

theHarvester gathers emails, employee names, hosts, and public intelligence from search engines and other sources.

Suggested command(s):

theHarvester -d <target-domain> -b all

What to write in analysis / conclusion:

*   Document employee emails, names, subdomains, and technologies inferred from job posts or public references.

# Q15. Transport layer attack

Transport layer attacks target TCP/UDP communication and connection management.

What to write in analysis / conclusion:

*   Example: SYN flood. The attacker sends many SYN packets and leaves connections half-open, exhausting resources.

# Q16. Exploitation of a vulnerable FTP service with Metasploit (lab only)

Demonstrate exploitation only on an authorized vulnerable VM such as Metasploitable.

Suggested command(s):

msfconsole

search ftp

use exploit/unix/ftp/vsftpd\_234\_backdoor

set RHOSTS <target-ip>

run

What to write in analysis / conclusion:

*   If successful, Metasploit opens a session. Record the vulnerable version and explain the risk of outdated services.

# Q17. Social media footprinting with Sherlock

Sherlock checks whether a username exists across many social media platforms.

Suggested command(s):

sherlock <username>

What to write in analysis / conclusion:

*   List the matching profiles discovered and note any intelligence gained from reused usernames.

# Q18. Session layer attack

Session layer attacks target session creation, maintenance, or hijacking.

What to write in analysis / conclusion:

*   Example: session hijacking. An attacker steals a valid session token and impersonates the logged-in user.

# Q19. MITM with Responder and Wireshark (authorized lab only)

Responder can capture name-resolution traffic in a lab. Wireshark is used to monitor the resulting packets.

Suggested command(s):

sudo responder -I <iface>

wireshark

What to write in analysis / conclusion:

*   Active MITM replies to requests and poisons resolution. Passive MITM mainly observes and records traffic without injection.

# Q20. Operating system detection

Use Nmap OS detection to guess the remote operating system based on TCP/IP fingerprints.

Suggested command(s):

nmap -O <target-ip>

nmap --osscan-guess <target-ip>

nmap --osscan-limit <target-ip>

What to write in analysis / conclusion:

*   Document the likely OS, device type, confidence level, and any reasons the result may be uncertain.

# Q21. Presentation layer attack

Presentation layer attacks target encoding, encryption, compression, or data translation.

What to write in analysis / conclusion:

*   Example: SSL stripping. The attacker downgrades a secure HTTPS session toward insecure HTTP when protections are weak.

# Q22. DNS records, TTL, and reverse lookup

Find the MX record with nslookup, retrieve A/MX/NS/SOA/TXT with dig, check TTL, and perform reverse lookup.

Suggested command(s):

nslookup -type=mx <domain>

dig <domain> A

dig <domain> MX

dig <domain> NS

dig <domain> SOA

dig <domain> TXT

dig <domain> A +ttlunits

nslookup <ip-address>

What to write in analysis / conclusion:

*   TTL shows how long a record may be cached. Reverse lookup maps IP address to domain name when PTR exists.

# Q23. Shodan search

Use Shodan to search internet-facing devices and filter by port/country.

Suggested command(s):

port:80

port:80 country:IN

What to write in analysis / conclusion:

*   Analyze banner information such as software, title, server string, and exposed service details. Recommend patching, header hardening, and limiting unnecessary exposure.

# Q24. Session layer attack

This repeats the session layer question.

What to write in analysis / conclusion:

*   Example: session fixation. The attacker forces a known session ID and waits for the victim to authenticate with it.

# Q25. Burp Repeater

Capture a request in Burp Suite, send it to Repeater, modify one parameter at a time, and resend.

What to write in analysis / conclusion:

*   Compare responses to identify weak validation, injection points, authorization issues, or information leakage.

# Q26. Skipfish scan

Skipfish performs automated web security crawling and vulnerability checks.

Suggested command(s):

skipfish -o skipfish\_out http://<target>

What to write in analysis / conclusion:

*   Document possible vulnerabilities, security misconfigurations, and suitable mitigations such as input validation, secure headers, and patching.

# Q27. Directory and file discovery with DirBuster and GoBuster

Use wordlists to brute-force hidden directories and files on a lab web app.

Suggested command(s):

gobuster dir -u http://<target> -w /usr/share/wordlists/dirb/common.txt

DirBuster -> set target URL -> choose wordlist -> Start

What to write in analysis / conclusion:

*   Record hidden paths, endpoints, backup files, and admin panels discovered.

# Q28. Password strength analysis with Medusa

Run a controlled brute-force test only on an authorized lab target.

Suggested command(s):

medusa -h <target-ip> -u <user> -P pass.txt -M ssh

What to write in analysis / conclusion:

*   Weak credentials indicate poor password strength. Record any discovered credential in the lab report only if allowed.

# Q29. SMB enumeration with smbclient

Use smbclient to list and access SMB shares.

Suggested command(s):

smbclient -L //<target-ip> -N

smbclient //<target-ip>/<share> -N

What to write in analysis / conclusion:

*   Document readable, writable, and restricted shares and note the risk of misconfigured access.

# Q30. Password strength analysis with John the Ripper

Use John to test password hash strength.

Suggested command(s):

john hash.txt

john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt

What to write in analysis / conclusion:

*   Weak or quickly cracked passwords show poor password complexity and reuse risk.

# Q31. SMBMap on Metasploitable

SMBMap enumerates SMB shares and permissions.

Suggested command(s):

smbmap -H 192.168.56.101

smbmap -H 192.168.56.101 -u msfadmin -p msfadmin

smbmap -H 192.168.56.101 -u msfadmin -p msfadmin -R tmp

What to write in analysis / conclusion:

*   Valid credentials usually reveal more shares and more accurate READ/WRITE permissions than anonymous access. Recursive listing displays all files and subfolders inside the chosen share.

# Q32. traceroute / tracert

Write commands for Linux and Windows to trace the route to an IP or domain.

Suggested command(s):

Linux: traceroute <ip-or-domain>

Windows: tracert <ip-or-domain>

What to write in analysis / conclusion:

*   The time values represent round-trip time to each hop. traceroute is Linux/Unix; tracert is the Windows equivalent.

# Q33. Active and passive banner grabbing

Passive banner grabbing collects service information without direct interaction, usually from observed traffic or public data.

What to write in analysis / conclusion:

*   Active banner grabbing directly connects to the service, for example with Telnet, Netcat, or Nmap version detection.

# Q34. John / Medusa / Hydra commands

This question asks for direct commands.

Suggested command(s):

john hash.txt

john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt

medusa -h 192.168.56.101 -u msfadmin -P pass.txt -M ssh

hydra -l msfadmin -P pass.txt ssh://192.168.56.101

What to write in analysis / conclusion:

*   Dictionary attacks work well because many people use predictable passwords found in common wordlists.

# Q35. Banner grabbing using Telnet and Netcat

Use Telnet or Netcat to connect to a port and read the service response.

Suggested command(s):

telnet <target> 80

telnet <target> 21

nc -v <target> 22

nc <target> 80

What to write in analysis / conclusion:

*   On HTTP, send HEAD / HTTP/1.0 and press Enter twice. Telnet is interactive; Netcat is lighter and more script-friendly.

# Q36. Enum4linux enumeration

Enum4linux can enumerate users, shares, and password policy from SMB services.

Suggested command(s):

enum4linux -U 192.168.56.101

enum4linux -S 192.168.56.101

enum4linux -P 192.168.56.101

What to write in analysis / conclusion:

*   User enumeration helps map valid accounts. Share enumeration reveals exposed resources. Password policy helps assess password strength requirements.