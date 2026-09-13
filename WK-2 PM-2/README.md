# Week 2 Penetration Testing Project

## Overview

This project documents the **Week 2 penetration testing activities**, focusing on **footprinting, reconnaissance, DNS enumeration, web technology identification, and local network scanning**.

The assessment was carried out using various cybersecurity tools, including WHOIS, WhatWeb, Nslookup, Curl, Wafw00f, DNSRecon, and Zenmap/Nmap.

---

## Objectives

The objectives of this week's exercise were to:

* Gather information about a target domain.
* Identify web technologies and server information.
* Enumerate DNS records.
* Identify potential Web Application Firewall technology.
* Identify the local network configuration.
* Perform network and service discovery using Zenmap/Nmap.
* Analyze identified risks and provide security recommendations.
* Document the findings in a professional penetration testing report.

---

## Tools Used

| Tool              | Purpose                                       |
| ----------------- | --------------------------------------------- |
| **WHOIS**         | Domain registration and ownership information |
| **WhatWeb**       | Web technology and server fingerprinting      |
| **Nslookup**      | DNS resolution                                |
| **Curl**          | HTTP response-header inspection               |
| **Wafw00f**       | Web Application Firewall detection            |
| **DNSRecon**      | DNS enumeration                               |
| **Zenmap / Nmap** | Network and service scanning                  |
| **ipconfig**      | Local network configuration                   |

---

## Web Reconnaissance

### Target

```text
networkwalks.com
```

The reconnaissance phase collected information about the target's domain registration, DNS infrastructure, web technologies, HTTP responses, and WAF.

## Zenmap / Nmap Implementation

The local network configuration identified the following:

```text
IPv4 Address : 192.168.1.54
Subnet Mask  : 255.255.255.0
MAC Address  : F8-34-41-96-F8-44
Hostname     : DESKTOP-LDVC073
Network      : 192.168.1.0/24
```



## Risk Summary

| Risk / Finding                     |  Level |
| ---------------------------------- | :----: |
| Web technology information exposed | Medium |
| Public web server IP identifiable  |   Low  |
| HTTP/API information exposed       |   Low  |
| WAF technology identifiable        |   Low  |
| DNS infrastructure exposed         | Medium |
| SMB/RPC services exposed           | Medium |
| Additional services exposed        |   Low  |
| DNSSEC unsigned                    |   Low  |

> These findings represent observations from reconnaissance and network scanning. An open port or exposed technology does **not automatically mean that the system is vulnerable**.


## Project Structure

```text
Week-2-Penetration-Testing/
│
├── README.md
│
├── reconnaissance/
│   ├── whois
│   ├── whatweb
│   ├── nslookup
│   ├── curl
│   ├── wafw00f
│   └── dnsrecon
│
├── network-scanning/
│   └── zenmap-nmap
│
├── evidence/
│   └── screenshots/
│
└── report/
    └── W2-PM-FINAL - Report .pdf
```

## Conclusion

Week 2 focused on developing practical penetration-testing skills through **reconnaissance and network scanning**. The exercise demonstrated how different tools can be combined to identify publicly available domain information, web technologies, DNS infrastructure, and services exposed by a local host.

The results were documented, analyzed, and used to develop appropriate security recommendations.
