# Protocols and Servers 1 - TryHackMe Writeup

## Room Overview

This room introduces common network protocols and demonstrates how they work at a low level using Telnet and other command-line tools.

Protocols covered:

* Telnet
* HTTP
* FTP
* SMTP
* POP3
* IMAP

The room focuses on understanding:

* Client-server communication
* Cleartext protocols
* Authentication mechanisms
* Security weaknesses in legacy protocols

---

# Task 1 - Introduction

The room requires starting:

* AttackBox
* Target VM

The objective is to manually interact with network protocols to understand how applications communicate behind the scenes.

---

# Task 2 - Telnet

## About Telnet

Telnet is a protocol used for remote terminal access.

Default Port:

```text
23
```

Example connection:

```bash
telnet MACHINE_IP
```

After successful authentication:

```text
login: frank
password: D2xc9CgD
```

A shell is provided:

```bash
frank@machine:~$
```

## Security Issue

Telnet is insecure because:

* Username is sent in cleartext
* Password is sent in cleartext
* Traffic can be sniffed easily

SSH replaced Telnet due to encryption support.

## Answer

### Default Telnet Port

```text
23
```

---

# Task 3 - HTTP

## About HTTP

HTTP (HyperText Transfer Protocol) is used for web communication.

Default Port:

```text
80
```

## Manual HTTP Request

Connect using Telnet:

```bash
telnet MACHINE_IP 80
```

Send request:

```http
GET /flag.thm HTTP/1.1
host: telnet
```

## Important Headers

Example:

```http
Server: nginx/1.18.0
```

This reveals:

* Web server software
* Version information

Useful during reconnaissance.

## Flag

```text
THM{e3eb0a1df437f3f97a64aca5952c8ea0}
```

---

# Task 4 - FTP

## About FTP

FTP (File Transfer Protocol) is used for file transfers.

Default Port:

```text
21
```

FTP uses:

* Control connection
* Separate data connection

## FTP Login

```bash
ftp MACHINE_IP
```

Credentials:

```text
Username: frank
Password: D2xc9CgD
```

Useful commands:

```bash
ls
get filename
```

## Security Issue

FTP transfers:

* Credentials in cleartext
* Files in cleartext

Secure alternatives:

* SFTP
* FTPS

## Flag

```text
THM{364db6ad0e3ddfe7bf0b1870fb06fbdf}
```

---

# Task 5 - SMTP

## About SMTP

SMTP (Simple Mail Transfer Protocol) is used to send emails.

Common Ports:

```text
25
587
465
```

## SMTP Commands

Connect:

```bash
telnet MACHINE_IP 25
```

Commands:

```text
helo test
mail from:
rcpt to:
data
```

End message using:

```text
.
```

## Security Issue

SMTP originally lacked sender verification.

This enables:

* Email spoofing
* Phishing attacks

## Flag

```text
THM{5b31ddfc0c11d81eba776e983c35e9b5}
```

---

# Task 6 - POP3

## About POP3

POP3 (Post Office Protocol Version 3) is used to download emails from a mail server.

Default Port:

```text
110
```

## POP3 Commands

Connect:

```bash
telnet MACHINE_IP 110
```

Authentication:

```text
USER frank
PASS D2xc9CgD
```

Useful commands:

```text
STAT
LIST
RETR
```

## STAT Response

```text
+OK 0 0
```

Meaning:

* 0 emails
* 0 bytes

## Security Issue

POP3 sends credentials in cleartext.

Captured credentials may lead to:

* Mailbox compromise
* Password reset abuse
* Information disclosure

## Answers

### STAT Response

```text
+OK 0 0
```

### Number of Emails

```text
0
```

---

# Task 7 - IMAP

## About IMAP

IMAP (Internet Message Access Protocol) synchronizes emails across devices.

Default Port:

```text
143
```

Unlike POP3:

* Emails stay on server
* Read/unread state syncs
* Multiple device access supported

## IMAP Commands

Connect:

```bash
telnet MACHINE_IP 143
```

Authentication:

```text
c1 LOGIN frank D2xc9CgD
```

Useful commands:

```text
LIST
EXAMINE INBOX
LOGOUT
```

## Security Issue

Plaintext IMAP exposes:

* Credentials
* Mailbox contents
* Historical email data

Compromised IMAP access can lead to:

* Business email compromise
* Password reset abuse
* Persistent mailbox access

## Answer

### Default IMAP Port

```text
143
```

---

# Key Takeaways

* Many older protocols transmit data in cleartext.
* Attackers can capture credentials using packet sniffing.
* Modern secure alternatives include:

  * SSH instead of Telnet
  * HTTPS instead of HTTP
  * SFTP instead of FTP
  * IMAPS/POP3S instead of plaintext mail protocols

Understanding these protocols is essential for:

* Networking
* Penetration Testing
* Web Security
* Incident Response
* Cybersecurity Fundamentals

---


# Conclusion

This room provided a strong introduction to legacy network protocols and demonstrated how insecure cleartext communication can be exploited.

It also highlighted why encryption and secure protocol replacements are essential in modern cybersecurity environments.
