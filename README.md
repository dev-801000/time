

# PRACTICAL NO 1

## AIM :- Google and Whois Reconnaissance
- Use Google search techniques to gather information about a specific target or organization.
- Utilize advanced search operators to refine search results and access hidden information.
- Perform Whois lookups to retrieve domain registration information and gather details about the target's infrastructure. [Source]

---

## SOLUTION :-
1. Search **“Prestashop”** on Google and take a screenshot of panel containing PrestaShop information.
2. Go to browser and open **https://who.is/**
3. Search for **www.prestashop.com**
4. Scroll down and study the information shown.
5. Click on **DNS Records**.
6. Click on **Diagnostics**.


---

# PRACTICAL NO 2

## AIM :- Password Encryption and Cracking with CrypTool and Cain and Abel
- Password Encryption and Decryption: Use CrypTool to encrypt passwords using the RC4 algorithm; decrypt and verify original values.
- Password Cracking and Wireless Network Password Decoding: Use Cain & Abel for dictionary attack (authorized/lab environment).

---

## SOLUTION :-

### A) Use CrypTool
1. Create one text file and save it.
2. Go to **Encrypt/Decrypt → Symmetric (modern) → RC4**.
3. Select key length (journal me 16 bits) and click **Encrypt**.
4. Save the encrypted output.
5. Decrypt karne ke liye same procedure repeat karke **Decrypt** karo.
6. Original message verify karo.\

### B) Use Cain & Abel (High-level / Authorized Only)
1. Install and open Cain & Abel tool.
2. Sniffer settings me appropriate network adapter configure karo.
3. Sirf **authorized accounts/networks** par dictionary attack/audit perform karo.
4. Observations document karo.


---

# PRACTICAL NO 3

## AIM :- Linux Network Analysis and ARP Poisoning
- Linux Network Analysis: `ifconfig`, `ping`, `netstat`, `traceroute` outputs analyze karna.
- ARP Poisoning: traffic redirection ka impact samajhna (lab/authorized).

---

## SOLUTION :-

### A) Linux Network Analysis
1. **ifconfig** run karke network interface details dekho.
2. **ping** se connectivity test karo aur output analyze karo.
3. **netstat** se active connections dekho.
4. **traceroute** se route/path observe karo.

### B) ARP Poisoning (Conceptual / Lab Only)
1. Controlled lab me ARP spoofing ka effect observe karo.
2. Risk analysis likho (MITM possibility).
3. Defensive points note karo: DAI, VLAN, static ARP, HTTPS/TLS, monitoring.


---

# PRACTICAL NO 4

## AIM :- Port Scanning with NMap
- ACK scan se ports filtered/unfiltered ka idea lena.
- SYN/FIN/NULL/XMAS scan ka study.
- Scan results analyze karke services ka overview lena (authorized only).
---

## SOLUTION :-
1. Nmap me **ACK scan** run karke filtering behavior observe karo.
2. **SYN scan** se open ports identify karne ka concept samjho.
3. **FIN scan** behavior study karo.
4. **NULL scan** behavior study karo.
5. **XMAS scan** behavior study karo.



---

# PRACTICAL NO 5

## AIM :- Network Traffic Capture and DoS Attack with Wireshark and Nemesy
- Wireshark me packets capture karke analysis karna.
- DoS attack ka impact (availability/performance) high-level samajhna (lab only). 

---

## SOLUTION :-

### A) Network Traffic Capture (Wireshark)
1. Wireshark open karo.
2. Correct interface select karke capture start karo.
3. Test web traffic generate karo (authorized test app).
4. HTTP filters use karke GET/POST requests observe karo. 

### B) DoS (High-level / Lab Only)
1. Controlled lab me excessive traffic ka effect observe karo.
2. Symptoms note karo: slow response, packet loss, service downtime.
3. Mitigations note karo: rate limit, firewall, WAF/IPS, monitoring.



---

# PRACTICAL NO 6

## AIM :- Persistent Cross-Site Scripting Attack
- Vulnerable web app (DVWA) me stored XSS ka concept samajhna (lab only).
- Risks aur prevention samajhna.

---

## SOLUTION :-
1. DVWA download/setup (local lab) karo.
2. Security level low karke stored XSS behavior observe karo (safe lab).
3. Prevention likho: output encoding, validation, CSP, secure coding.



---

# PRACTICAL NO 7

## AIM :- Session Impersonation with Firefox and Tamper Data
- HTTP requests/cookies ka role samajhna.
- Session management importance samajhna (high-level).

---

## SOLUTION :-
1. Session cookies ka concept study karo (login state).
2. Lab me request interception ka flow observe karo (high-level).
3. Defenses note karo: HttpOnly, Secure, SameSite, session rotation, MFA.



---

# PRACTICAL NO 8

## AIM :- SQL Injection Attack
- Vulnerable app me SQLi ka concept samajhna (lab only).
- Secure coding prevention samajhna. 
---

## SOLUTION :-
1. DVWA/local vulnerable lab app use karo.
2. Unsanitized input se query behavior change ka concept observe karo (high-level).
3. Prevention note karo: parameterized queries, ORM, least privilege, validation, WAF. 



---

# PRACTICAL NO 9

## AIM :- Creating a Keylogger with Python
- Keystroke logging ka concept aur risks samajhna.
- Defensive controls note karna (high-level). 

---

## SOLUTION :-
1. Keylogger kya hota hai aur kaise sensitive data leak kar sakta hai — concept study karo.
2. Defensive points: antivirus/EDR, least privilege, allowlisting, monitoring.

---
