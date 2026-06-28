# Active Reconnaissance - TryHackMe Writeup

## Room Overview

This room introduces the fundamentals of **Active Reconnaissance**.
Unlike passive reconnaissance, active reconnaissance directly interacts with the target system to gather information.

In this room, we learned:

* Web Browser Reconnaissance
* Ping
* Traceroute
* Telnet
* Netcat

---

# Task 1 - Introduction

## What is Active Reconnaissance?

Active reconnaissance involves directly interacting with the target by:

* Sending packets
* Connecting to ports
* Visiting websites
* Probing services

This can generate:

* Firewall logs
* IDS alerts
* WAF detections

### Examples

* `ping`
* `traceroute`
* `telnet`
* `netcat`

> Always perform active reconnaissance only on authorised targets.

---

# Task 2 - Web Browser

A web browser can be used as a reconnaissance tool.

## Useful Developer Tools Tabs

### Network Tab

Used to inspect:

* HTTP headers
* Status codes
* Cookies
* Server information

### Sources Tab

Useful for finding:

* Hidden API endpoints
* JavaScript files
* Internal directories
* Developer comments

### Application Tab

Inspect:

* Cookies
* Local Storage
* Session Storage

### Security Tab

View:

* SSL certificates
* SANs (Subject Alternative Names)

---

## Question

### Total number of questions on the webpage?

```bash
8
```

---

# Task 3 - Ping

`ping` is used to test whether a target host is reachable.

## Linux Command

```bash
ping -c 5 MACHINE_IP
```

## Windows Command

```bash
ping -n 5 MACHINE_IP
```

## Important Concepts

### ICMP

Ping uses:

* ICMP Echo Request
* ICMP Echo Reply

### TTL (Time To Live)

Common default TTL values:

* Linux → 64
* Windows → 128

---

## Questions & Answers

### Option used to set packet size?

```bash
-s
```

### ICMP header size?

```bash
8 bytes
```

### Does Windows Firewall block ping by default?

```bash
Y
```

### Number of ping replies received?

```bash
10
```

---

# Task 4 - Traceroute

`traceroute` maps the path packets take to reach a target.

## Linux

```bash
traceroute MACHINE_IP
```

## Windows

```bash
tracert MACHINE_IP
```

## How It Works

Traceroute uses TTL values:

* TTL expires at routers
* Routers send ICMP Time Exceeded messages
* Each hop is revealed one by one

---

## Questions & Answers

### Last hop IP in Traceroute A

```bash
172.67.69.208
```

### Last hop IP in Traceroute B

```bash
104.26.11.229
```

### Number of routers in Traceroute B

```bash
25
```

---

# Task 5 - Telnet

Telnet is an old remote administration protocol.

Default Port:

```bash
23
```

Since Telnet sends data in plaintext, SSH is preferred today.

---

## Banner Grabbing

Telnet can connect to TCP ports and read service banners.

Example:

```bash
telnet MACHINE_IP 80
```

HTTP request:

```http
GET / HTTP/1.1
host: telnet
```

---

## Questions & Answers

### Running server name

```bash
Apache
```

### Server version

```bash
2.4.61
```

---

# Task 6 - Netcat

Netcat (`nc`) is a versatile networking utility.

It supports:

* TCP
* UDP
* Client mode
* Server mode

---

## Banner Grabbing Using Netcat

```bash
nc MACHINE_IP 80
```

Example request:

```http
GET / HTTP/1.1
host: netcat
```

---

## Netcat Listener

Server:

```bash
nc -lvnp 1234
```

Client:

```bash
nc MACHINE_IP 1234
```

---

## Useful Flags

| Flag | Description       |
| ---- | ----------------- |
| `-l` | Listen mode       |
| `-v` | Verbose           |
| `-n` | No DNS resolution |
| `-p` | Specify port      |

---

## Question & Answer

### FTP server version on port 21

```bash
0.17
```

---

# Conclusion

This room covered the basic tools required for active reconnaissance:

* Browser Developer Tools
* Ping
* Traceroute
* Telnet
* Netcat

These tools form the foundation for:

* Host discovery
* Service enumeration
* Banner grabbing
* Network mapping

The next step after mastering these tools is learning advanced scanning using **Nmap**.

---


