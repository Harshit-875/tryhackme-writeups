# Cyber Kill Chain — TryHackMe Writeup

## Introduction

The Cyber Kill Chain is a cybersecurity framework developed by Lockheed Martin in 2011. It helps organizations understand how cyber attacks are performed step-by-step so defenders can detect and stop attacks before they succeed.

The Cyber Kill Chain consists of seven phases:

1. Reconnaissance
2. Weaponization
3. Delivery
4. Exploitation
5. Installation
6. Command and Control (C2)
7. Actions on Objectives

---

# Task 1 — Introduction

The Cyber Kill Chain explains the lifecycle of a cyber attack from information gathering to achieving the attacker's final goal.

### Question:

How many phases comprise the Cyber Kill Chain?

### Answer:

`7`

---

# Task 2 — Reconnaissance

Reconnaissance is the information-gathering phase where attackers collect details about the target.

## Types of Reconnaissance

### Passive Reconnaissance

* WHOIS lookup
* DNS enumeration
* Social media analysis
* Google Dorking

### Active Reconnaissance

* Port scanning
* Vulnerability scanning
* Social engineering

---

### Question 1:

What is the term for using search engines to reveal sensitive information and confidential files?

### Answer:

`Google Dorking`

---

### Question 2:

What type of reconnaissance is it where the attacker checks the social media pages?

### Answer:

`Passive Reconnaissance`

---

# Task 3 — Weaponization

In this phase, attackers create malicious payloads based on vulnerabilities discovered during reconnaissance.

Examples:

* Malicious Office documents
* Malware
* RATs
* Exploit kits

Attackers often use obfuscation to avoid antivirus detection.

---

### Question 1:

What technique is mentioned to evade detection by making it challenging to analyse the malicious code?

### Answer:

`Obfuscation`

---

### Question 2:

What built-in feature makes creating a malicious MS Office document possible?

### Answer:

`Macros`

---

# Task 4 — Delivery

The attacker delivers the malicious payload to the victim.

## Delivery Methods

* Phishing emails
* Spear phishing
* Malicious links
* File-sharing platforms
* Malvertising
* Smishing
* USB attacks

---

### Question 1:

What method involves showing advertisements on legitimate websites to redirect users to malicious pages?

### Answer:

`Malvertising`

---

### Question 2:

What phishing attack sends text messages with malicious links or instructions to download malware?

### Answer:

`Smishing`

---

# Task 5 — Exploitation

The exploitation phase occurs when the attacker successfully exploits a vulnerability.

Examples:

* Weak passwords
* SQL Injection
* Buffer Overflow
* Zero-day vulnerabilities

Countermeasures include:

* MFA
* Patch management
* WAF
* IPS

---

### Question 1:

What type of exploit is used before the vendor becomes aware of a vulnerability?

### Answer:

`Zero-Day`

---

### Question 2:

What technology is mentioned to prevent an attacker from gaining access even with valid login credentials?

### Answer:

`MFA`

---

# Task 6 — Installation

After successful exploitation, attackers establish persistence on the compromised system.

## Common Techniques

* Scheduled tasks
* Cron jobs
* Rootkits
* Backdoors
* Web shells
* LOLBins

A web shell allows attackers to execute commands via a web browser interface.

---

### Question 1:

What tactic allows attackers to execute operating system commands on a target via a web browser interface?

### Answer:

`Web Shell`

---

### Question 2:

What technique is mentioned to prevent the execution of unauthorised or malicious software by only allowing approved applications to run?

### Answer:

`Allowlisting`

---

# Task 7 — Command and Control (C2)

The attacker establishes communication between the compromised system and attacker infrastructure.

## Common C2 Protocols

* HTTP
* HTTPS
* DNS
* SMTP

## Advanced Techniques

* DNS Tunneling
* Fast Flux
* DGA (Domain Generation Algorithm)

---

### Question 1:

What is the name of the tactic where data is hidden within DNS queries?

### Answer:

`DNS Tunneling`

---

### Question 2:

What protocol would the attacker use to smuggle his data as encrypted web traffic?

### Answer:

`HTTPS`

---

# Task 8 — Actions on Objectives

The attacker performs the final objectives after establishing access.

## Common Objectives

* Data exfiltration
* Ransomware attacks
* Lateral movement
* Financial theft
* Industrial system manipulation

---

### Question 1:

What is the term for stealing sensitive files from a target network?

### Answer:

`Data Exfiltration`

---

### Question 2:

What principle limits who can access sensitive systems and data to minimise damage caused by an attacker?

### Answer:

`Principle of Least Privilege`

---

### Question 3:

What type of attack involves encrypting files and demanding payment in exchange for the decryption key?

### Answer:

`Ransomware`

---

# Conclusion

The Cyber Kill Chain framework helps organizations understand how attackers operate and how defenders can break the attack lifecycle at different stages.

Understanding each phase is important for:

* SOC Analysts
* Penetration Testers
* Threat Hunters
* Incident Responders
* Security Researchers

This room provided practical knowledge about:

* Attack lifecycle
* Exploitation techniques
* Persistence mechanisms
* C2 communication
* Defensive countermeasures

---

# Tools & Concepts Learned

* Google Dorking
* Port Scanning
* Exploit Kits
* Phishing
* SQL Injection
* MFA
* Web Shells
* DNS Tunneling
* Fast Flux
* Data Exfiltration

---

# Platform

TryHackMe

Room: Cyber Kill Chain

https://tryhackme.com

---

# Disclaimer

This writeup is created for educational purposes only.

---

# Author

Harshit Gupta

GitHub: https://github.com/Harshit-875
