# Network Reconnaissance & Security Assessment

This project provides a network security analysis using Nmap port scanning, service version detection, and packet capture analysis. It highlights open ports, the risks associated with exposed services, and potential vulnerabilities in the local network (192.168.0.0/24).

## 🔍 Project Contents

- `network.txt`: Basic TCP SYN scan result using Nmap (`-sS`) for host discovery and open port identification.
- `version.txt`: Service version detection scan using Nmap (`-sV`) to identify software running on discovered ports.
- `risksofopenports.txt`: Documented risks associated with open ports and suggested mitigation strategies.
- `packetcapture.pcapng`: A packet capture file for further deep-packet inspection (e.g., with Wireshark).

## 🛠 Tools Used

- [Nmap 7.95](https://nmap.org) for scanning and fingerprinting.
- Wireshark or Tshark for analyzing `pcapng` captures.
- Linux shell environment for scan execution.

## 📄 Nmap Scanning Summary

**Targets:** `192.168.0.0/24`  
**Hosts up:** 19  
**Common Open Ports Detected:**
- `80/tcp` (HTTP)
- `443/tcp` (HTTPS)
- `554/tcp` (RTSP)
- `8080/tcp` (HTTP-Proxy)
- `7070/tcp` (RealServer)
- `1723/tcp` (PPTP)

**Notable Devices:**
- TP-Link Routers with `uHTTPd`, `TP-LINK HTTPD/1.0`, and nginx 1.8.1
- Multiple Aditya Infotech devices with RTSP and d-s-n services

## ⚠️ Risks of Open Ports

Refer to `risksofopenports.txt` for full explanations.

| Risk Type                       | Example                                       |
|--------------------------------|-----------------------------------------------|
| Unauthorized Access            | Open SSH port with weak credentials           |
| Exploitable Services           | Outdated Apache or nginx                      |
| Network Fingerprinting         | Nmap scans revealing OS/services              |
| Misconfiguration               | Open internal DB services                     |
| Malware Communication          | C2 channels over unknown open ports           |
| Data Leakage                   | Anonymous FTP or open admin panels            |

## 📁 File Descriptions

| File                    | Purpose                                      |
|-------------------------|----------------------------------------------|
| `network.txt`           | Initial port discovery (SYN scan)            |
| `version.txt`           | Detailed service version identification      |
| `risksofopenports.txt`  | List of common risks and mitigation steps    |
| `packetcapture.pcapng`  | Network traffic capture for packet analysis  |

## 🧪 Usage Instructions

1. **Scan the Network:**
   ```bash
   sudo nmap -sS -oN network.txt 192.168.0.0/24
   sudo nmap -sV -oN version.txt 192.168.0.0/24

**Recommendations**
Close unused or unnecessary ports.

Regularly update and patch exposed services.

Use firewalls and access control lists.

Monitor unusual traffic or access patterns via logs or packet captures.
