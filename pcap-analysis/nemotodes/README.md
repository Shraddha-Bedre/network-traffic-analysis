# Nemotodes — Network Traffic Incident Report

## Overview

This exercise involved analyzing a PCAP file containing suspicious network activity from a Windows workstation.

The investigation was performed using Wireshark to identify the affected host, user information, external communication, suspicious domains, and other Indicators of Compromise (IOCs).

**Date of Activity:** 26 November 2024

## Tools Used

- Wireshark
- PCAP file
- Malware Traffic Analysis dataset

---

## 1. Executive Summary

On 26 November 2024, suspicious network activity was identified from a Windows workstation associated with `nemotodes.health`.

The infected host generated a large amount of outbound traffic and repeatedly communicated with external IP addresses. The packet capture showed communication patterns that may indicate malware activity and possible Command and Control (C2) communication.

Multiple suspicious domains and external servers were also observed during the investigation.

---

## 2. Victim Details

| Information | Result |
|---|---|
| Hostname | `DESKTOP-B8TQK49` |
| IP Address | `10.11.26.183` |
| MAC Address | `d0:57:7b:ce:fc:8b` |
| Windows User | `oboomwald` |

### Hostname

The hostname was identified from the network traffic as:

`DESKTOP-B8TQK49`

![Identifying Hostname](screenshots/1-Identifying%20Hostname.png)

### IP Address

The affected Windows workstation was identified with the IP address:

`10.11.26.183`

![Identification of IP Address](screenshots/2-Identification%20of%20the%20IP%20Address.png)

### MAC Address

The MAC address associated with the workstation was:

`d0:57:7b:ce:fc:8b`

![Identifying MAC Address](screenshots/3-Identifying%20mac-address.png)

### Windows User Account

The Windows user account identified from the traffic was:

`oboomwald`

![Identification of User Account](screenshots/4-Identification%20of%20User%20Account%20Name.png)

### Full User Name

The full name was investigated using the packet information in Wireshark.

![Identifying Full Username](screenshots/5-Identifying%20full%20username.png)

> The full name is not included in the written investigation results available for this exercise, so it has not been guessed.

---

## 3. Indicators of Compromise (IOCs)

### IP Addresses

The following external IP addresses were observed during the investigation:

| IP Address | Observation |
|---|---|
| `193.42.38.139` | Hosting environment associated with a malicious payload drop |
| `213.246.109.5` | Hosting environment associated with the initial redirect site |
| `173.222.49.101` | Additional external IP observed during traffic analysis |

### Suspicious Domains

The following suspicious domains were identified:

- `modandcrackedapk.com`
- `classicgrand.com`
- `confirmsubscription.com`
- `geo.netsupportsoftware.com`

### URL

The following URL/domain was observed:

`Geo.netsupportsoftware.com`

### SHA256

No malware binaries were extracted from the PCAP, so no SHA256 hash was available.

---

## 4. Traffic Analysis

The host `10.11.26.183` generated significantly higher traffic compared with other hosts in the PCAP.

The hostname associated with the host was:

`DESKTOP-B8TQK49`

The workstation repeatedly communicated with external infrastructure, including:

- `193.42.38.139`
- `213.246.109.5`
- `173.222.49.101`

DNS queries were also observed for multiple suspicious domains.

The observed traffic patterns indicate potentially malicious activity and possible communication with external infrastructure.

---

## 5. Key Observations

- A Windows workstation generated unusually high network traffic.
- Multiple external IP addresses were contacted repeatedly.
- DNS requests were made to suspicious domains.
- The traffic included infrastructure associated with potentially malicious activity.
- No malware binary was extracted, so no SHA256 hash was available.

---

## 6. Conclusion

The PCAP analysis identified a potentially compromised Windows workstation and several Indicators of Compromise associated with suspicious network activity.

The investigation identified the affected host, IP address, MAC address, Windows user account, suspicious external IP addresses, and domains.

This exercise demonstrates how network traffic analysis can be used to identify potentially compromised systems and collect useful IOCs for further investigation.

## Purpose

This project is part of my cybersecurity learning journey and is intended for educational and authorized security-analysis purposes.