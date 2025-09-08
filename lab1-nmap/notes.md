September 9 2025
Lab: Nmap Observation on Metasploitable through VMWare

1. ran basic scan: nmap -sV 10.0.0.11 (Metasploitable)
   - Some ports found: 21/tcp FTP, 22/tcp SSH, 80/tcp HTTP, 3306/tcp MySQL
   - FTP vsftpd 2.3.4 is vulnerable

2. ran aggressive scan: sudo nmap -A 10.0.0.11
   - OS Detection and confirmed service versions

3. ran vuln script: sudo nmap --script vuln 10.0.0.11
   - vsftpd 2.3.4 backdoor HTTP: outdated Apache Server
  
4. ran TCP scanning: sudo nmap -sT -p 80, 443 10.0.0.11
   - Found if ports 80, 443 are open

5. ran nmap Stealth SYN scan: sudo nmap -sS -p 80 10.0.0.11
   - Finds connection without 3-way handshake (SYN, SYN ACK, ACK)

6. detect OS: sudo nmap -O 10.0.0.11

7. stealth scan with a decoy: sudo nmap -sS -D 10.0.0.15 10.0.0.11
   -adds traffic from multiple hosts
