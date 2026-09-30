# Task 2 - Firewall Based Detection

## Objective

Identify network-based indicators associated with the malware sample and implement a firewall rule to prevent malicious communications.

---

## Malware Sample

| Property | Value |
|-----------|---------|
| File Name | sample2.exe |
| Classification | Trojan.Metasploit.A |
| MD5 | 4d661bf605d6b0b15915a533b572a6bd |
| SHA1 | 6878976974c27c8547cfc5acc90fb28ad2f0e975 |
| SHA256 | d576245e85e6b752b2fdffa43abaab1b2e1383556b0169fd04924d6cebc1cdf9 |

---

## Analysis Findings

The Malware Sandbox identified multiple suspicious activities:

### Malicious

- Metasploit payload detected

### Suspicious

- Connection to unusual IP address
- Connection to unusual port (4444)

### Host Reconnaissance

- Machine GUID enumeration
- LSA protection checks
- Computer name discovery
- Language enumeration

---

## Network Activity

### HTTP Request

| Process | Method | Destination |
|----------|----------|-------------|
| sample2.exe | GET | http://154.35.10.113:4444/uvLk8YI32 |

### TCP Connections

| Process | IP Address |
|----------|-------------|
| sample2.exe | 154.35.10.113:4444 |

---

## Indicator of Compromise

| IOC Type | Value |
|-----------|--------|
| IP Address | 154.35.10.113 |
| Port | 4444 |

---

## Detection Engineering

The malicious IP address identified during sandbox analysis was added to PicoSecure's firewall blocklist.

### Firewall Rule

```text
Block Outbound Traffic
Destination IP: 154.35.10.113
Port: 4444
Action: Deny
