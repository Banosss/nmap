# Nmap
This is a note for learning or recall the memory of nmap
--------------------------------------------------------------------
# Intro
Nmap (Network Mapper) is an open-source network discovery and security auditing tool. It is widely used by penetration testers, system administrators, and security analysts to:

Discover live hosts on a network using techniques like ICMP echo (ping), ARP requests, and TCP/ACK probes.

Identify open ports and the services running on them through various scanning methods (SYN, TCP, UDP, ACK).

Perform service and OS fingerprinting (-sV, -O) to determine software versions and operating systems.

Automate vulnerability detection using the Nmap Scripting Engine (NSE).

Nmap is highly flexible—it supports performance tuning (e.g., --min-rate), multiple output formats (-oN, -oG, -oX, -oA), and can be adapted for both quick host discovery and deep, full-port scans. This note serves as a quick-reference guide for the most common Nmap workflows, from scanning a local subnet to enumerating services on a single target.

---
# Usage
- list host
- multiple scanning method
---
# Command
```
nmap ip/subnet or sudo nmap 192.168.1.0/24 -sn -oN scans/alive-hosts 
(use sudo to get a faster result) 
this command will list out all the device in the specific ip address
               -sn  -->  disable port scanning 
can replace by -sS  -->  SYN Scan
               -sT  -->  Full TCP Scan
               -sA  -->  ACK Scan

scans/alive-hosts  -->  save the nmap file in ./scans/alive-hosts
               -oN  -->  to save the file as the default formet
can replace by -oG  -->  save as Greppable
               -oX  -->  save as XML
               -oA  -->  save as oN,oG,oX
```
---
### Make it fast
```
If you want to speed it up what you can do is 
sudo nmap 192.168.1.0/24 -sn -oN scans/alive-hosts -Pn -n
-Pn  --> disable ping requests
-n   --> disable DNS name resolution
```
---
```
sudo nmap -p- --min-rate 10000 -oA scans/nmap-alltcp 192.168.1.103
this command can scan all the port which is open 

-p- can manage to scan more than one port

if you want to scan port 22, 80, 443 and 445 then it should be
sudo nmap **-p22,80,443,445** --min-rate 10000 -oA scans/nmap-alltcp 192.168.1.103
to scan only 4 specific port

what if you want to scan a range of port, you can try
sudo nmap **-p1-100** --min-rate 10000 -oA scans/nmap-alltcp 192.168.1.103
to scan port 1 to port 100
```
---
```
sudo nmap -p- --min-rate 10000 -oA scans/nmap-alltcp 192.168.1.103 -sU
-sU --> scan UDP port
```
---
# Service Enumeration
```
sudo nmap -p[discovered,ports] -sV ip
sudo nmap -p21,22,23 -sV -oA scans/nmap-tcpscans 192.168.1.103
-sV --> to find out the version of the software and what service are running on which port
```
---
```
sudo nmap -O 192.168.1.101
-O --> to find out which operating system is running. such as Linux.
```
---
# Nmap Scripting
```
sudo nmap -p[discovered,ports] -sC ip

to be updated
```
---
```
nmap -p- 192.168.0.1
this command will list out all the port 
scanning same lan/subnet/scanner
ICMP ECHO (ping) requests
ARP requests
SYN and ACK requests
```
---
# Source
[Cyber Ryan | Cyber Security - Nmap for Beginners: A Complete Guide](https://youtu.be/z14HC3bJQpQ?si=d8nacpCGvDXhD14H)
---

