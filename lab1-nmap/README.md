# Lab: Nmap Observation on Metasploitable through VMWare

**Date:** September 9, 2025
**Environment:** Kali Linux -> Metasploitable VM through VMWare

---

## Objective
Conduct observations on the vulnerable machine (Metasploitable) by employing various nmap scan types to detect open ports, active services, and possible vulnerabilities.

## Commands & Results 

- **Basic Version Scan**
```bash
nmap -sV 10.0.0.11
```

1. executed version detection:
   ```bash
   nmap -sV 10.0.0.11 (Metasploitable)
   ```
   - Identified Open Ports:
      - 21/tcp FTP
      - 22/tcp SSH
      - 80/tcp HTTP
      - 3306/tcp MySQL
   - FTP vsftpd 2.3.4 is prone to a backdoor vulnerability

3. executed an aggressive scan:
   ```bash
   sudo nmap -A 10.0.0.11
   ```
   - OS Detection and verified service versions

5. executed vulnerability script:
   ```bash
   sudo nmap --script vuln 10.0.0.11
   ```
   - vsftpd 2.3.4 backdoor HTTP: outdated Apache Server
  
7. executed TCP scanning:
   ```bash
   sudo nmap -sT -p 80, 443 10.0.0.11
   ```
   - Confirmed if ports 80 and 443 are open

9. executed nmap Stealth SYN scan:
    ```bash
    sudo nmap -sS -p 80 10.0.0.11
    ```
   - Establishes connection without 3-way handshake (SYN, SYN ACK, ACK)

11. detect Operating System:
    ```bash
    sudo nmap -O 10.0.0.11
    ```
   - Identified Linux OS
   
11. stealth scan with a decoy:
    ```bash
    sudo nmap -sS -D 10.0.0.15 10.0.0.11
    ```
   - generates traffic from multiple hosts

## Essential Findings
- distinction between connect and stealth scans
- Practiced the use of a multitude nmap scripts for detecting vulnerabilities
- understand attacker strategies (decoys)
