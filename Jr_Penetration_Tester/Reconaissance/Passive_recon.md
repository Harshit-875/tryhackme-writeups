# Passive Reconnaissance - TryHackMe Writeup

## Room Info

| Category   | Details                |
| ---------- | ---------------------- |
| Platform   | TryHackMe              |
| Room       | Passive Reconnaissance |
| Difficulty | Easy                   |
| Module     | Network Security       |

---

# Introduction

Passive reconnaissance is the process of gathering information about a target **without directly interacting** with its systems.

Unlike active reconnaissance, passive recon does not send packets to the target and is therefore stealthier and less likely to trigger detection systems.

In this room, we learned:

* WHOIS lookups
* DNS enumeration
* Subdomain discovery
* Certificate Transparency logs
* Shodan reconnaissance

---

# Task 1 - Introduction

The room introduces passive reconnaissance techniques using public internet data.

Important tools and concepts:

* WHOIS
* dig
* nslookup
* DNSDumpster
* crt.sh
* Shodan.io

---

# Task 2 - Passive vs Active Recon

## Passive Reconnaissance

Passive recon uses publicly available information.

### Examples

* Viewing company social media pages
* Searching DNS records
* Checking CT logs
* Searching GitHub repositories
* Using Shodan

### Answer

```text
P
```

---

## Active Reconnaissance

Active recon directly interacts with the target.

### Examples

* Pinging hosts
* Port scanning
* Directory brute forcing
* Social engineering

### Answers

```text
A
A
```

---

# Task 3 - WHOIS

WHOIS provides domain registration information.

## Command

```bash
whois tryhackme.com
```

## Information Gathered

* Registrar
* Registration dates
* Name servers
* Domain status
* Abuse contacts

## Answers

### Registration Date

```text
20180705
```

### Registrar

```text
namecheap.com
```

### Name Server Provider

```text
cloudflare.com
```

---

# RDAP

RDAP is the modern replacement for WHOIS.

## RDAP Example

```bash
curl -s https://rdap.verisign.com/com/v1/domain/tryhackme.com | jq .
```

Benefits of RDAP:

* HTTPS based
* JSON output
* Better privacy support
* Machine readable

---

# Task 4 - nslookup and dig

DNS enumeration allows us to gather DNS-related information.

---

## nslookup

### A Record Lookup

```bash
nslookup -type=A tryhackme.com
```

### MX Record Lookup

```bash
nslookup -type=MX tryhackme.com
```

---

## dig

### MX Record Query

```bash
dig @1.1.1.1 tryhackme.com MX
```

`dig` is preferred because:

* Cleaner output
* Better scripting support
* Shows TTL values

---

## TXT Record Flag

### Command

```bash
dig thmlabs.com TXT
```

### Flag

```text
THM{a5b83929888ed36acb0272971e438d78}
```

---

# Task 5 - DNSDumpster

DNSDumpster helps discover subdomains using passive OSINT sources.

## Features

* Subdomain discovery
* MX/TXT/CNAME records
* Infrastructure mapping
* Visual relationship graphs

---

## Certificate Transparency Logs

Using crt.sh we can enumerate subdomains from SSL certificates.

### Search Example

```text
%.tryhackme.com
```

---

## Answer

### Highest Service/Banner Count

```text
cloudflare
```

---

# Task 6 - Shodan.io

Shodan is a search engine for internet-connected devices.

## Information Gathered

* Open ports
* Service banners
* Hosting providers
* Geolocation
* Vulnerable services

---

## Search Example

```text
hostname:tryhackme.com
```

---

## Answers

### Country with Most Apache Servers

```text
United States
```

### 3rd Most Common Apache Port

```text
8080
```

### Most Common nginx Port

```text
80
```

---

# Key Takeaways

* Passive reconnaissance is stealthy and low risk.
* WHOIS and RDAP provide domain registration data.
* dig is preferred over nslookup for DNS queries.
* DNSDumpster and crt.sh are useful for subdomain discovery.
* Shodan reveals exposed internet-facing services.

---

# Tools Used

* whois
* dig
* nslookup
* DNSDumpster
* crt.sh
* Shodan.io

---

# Conclusion

This room provided a solid introduction to passive reconnaissance techniques used in penetration testing and bug bounty hunting.

Reconnaissance is one of the most important phases of ethical hacking because it helps identify the target's attack surface before active testing begins.
