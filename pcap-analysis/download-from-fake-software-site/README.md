# Download from Fake Software Site — PCAP Traffic Analysis

## Overview

This exercise is based on a PCAP file from the Malware Traffic Analysis platform. The objective was to investigate suspicious network traffic using Wireshark and identify the Windows client involved in the activity.

The investigation also focused on identifying the likely domain used for a fake Google Authenticator page and the IP addresses associated with possible Command and Control (C2) servers.

## Tools Used

- Wireshark
- PCAP file
- Malware Traffic Analysis dataset

## Investigation Objectives

The investigation focused on identifying:

- IP address of the Windows client
- MAC address
- Hostname
- Windows user account
- Full name of the user
- Likely domain name used for the fake Google Authenticator page
- IP addresses used by possible C2 servers
- Suspicious network activity

## Findings

| Information | Result |
|---|---|
| Client IP | `10.1.17.215` |
| Hostname | `DESKTOP-L8C5GSJ` |
| MAC Address | `00:d0:b7:26:4a:74` |
| Windows User | `shutchenson` |
| Full Name | `Steve Hutchenson` |
| Main Destination | `45.125.66.32` |
| Packets Observed | `10,940` |

## Analysis Performed

### 1. Identifying the IP Address

Wireshark's **Statistics → Endpoints** section was used to examine the active hosts in the PCAP.

The host `10.1.17.215` generated significantly higher network traffic compared with the other hosts and was selected for further investigation.

![Identification of IP Address](screenshots/1-Identification%20of%20the%20IP%20Address.png)

### 2. Analyzing Conversations

The **Statistics → Conversations** section was used to examine communication between hosts.

The main communication identified was:

- Source: `10.1.17.215`
- Destination: `45.125.66.32`
- Packets: `10,940`

![Conversations](screenshots/2-conversations.png)

### 3. Identifying the Hostname

The `nbns` protocol filter was used to identify the hostname associated with the Windows system.

The hostname identified was:

`DESKTOP-L8C5GSJ`

![Identifying Hostname](screenshots/3-Identifying%20Hostname.png)

### 4. Identifying the MAC Address

Ethernet information in Wireshark was examined to identify the MAC address associated with the client.

The MAC address identified was:

`00:d0:b7:26:4a:74`

![Identifying MAC Address](screenshots/4-Identifying%20mac-address.png)

### 5. Identifying the Windows User Account

Kerberos, NTLM, SMB, and SMB2 traffic was examined to identify the Windows user account.

The user account identified was:

`shutchenson`

![Windows User Account](screenshots/5.1-Identification%20of%20User%20Account%20Name.png)

The `kerberos.CNameString` field was also used to confirm the username.

![Windows User Account Details](screenshots/5.2-Identification%20of%20User%20Account%20Name.png)

### 6. Identifying the Full User Name

Wireshark's **Find Packet** feature was used to search packet details and identify the user's full name.

The full name identified was:

`Steve Hutchenson`

![Full User Name](screenshots/6-Identifying%20full%20username.png)

## Fake Google Authenticator Page

The network traffic was also investigated to identify the likely domain name associated with the fake Google Authenticator page.

The domain should be confirmed from the relevant DNS/HTTP traffic in the PCAP before being added to this section.

> **Note:** The domain name was not included in the investigation results provided for this exercise, so it has not been guessed or added as an IOC.

## Possible C2 Server IP Addresses

The PCAP was also examined for IP addresses associated with possible Command and Control (C2) communication.

These addresses should be confirmed from the relevant network traffic before being documented as C2 infrastructure.

> **Note:** Specific C2 IP addresses were not included in the investigation results currently available, so they have not been guessed.

## Conclusion

This exercise demonstrated how Wireshark can be used to investigate suspicious network traffic and identify important details about a Windows client.

The investigation identified the client's IP address, hostname, MAC address, Windows user account, and full name. Network conversations were also examined to investigate suspicious external communication and activity related to a fake software download scenario.

## Purpose

This project is part of my cybersecurity learning journey and is intended for educational and authorized security-analysis purposes.