# nmap
This is a note for learning or recall the memory of nmap
--------------------------------------------------------------------
# Intro

--------------------------------------------------------------------
# usage
- list host
- multiple scanning method
--------------------------------------------------------------------
# command
nmap ip/subnet or sudo nmap 192.168.1.0/24 -sn -oN scans/alive-hosts
(use sudo to get a faster result)
this command will list out all the device in the specific ip address
               -sn  -->  disable port scanning 
can replace by -sS  -->  SYN Scan
               -sT  -->  Full TCP Scan
               -sA  -->  ACK Scan
--------------------------------------------------------------------
 scans/alive-hosts  -->  save the nmap file in ./scans/alive-hosts
               -oN  -->  to save the file as the default formet
can replace by -oG  -->  save as Greppable
               -oX  -->  save as XML
               -oA  -->  save as oN,oG,oX
--------------------------------------------------------------------
## speed it up
If you want to speed it up what you can do is 
sudo nmap 192.168.1.0/24 -sn -oN scans/alive-hosts -Pn -n
-Pn  --> disable ping requests
-n   --> disable DNS name resolution 
--------------------------------------------------------------------
sudo nmap -p- --min-rate 10000 -oA scans/nmap-alltcp 192.168.1.103
this command can scan all the port which is open 

-p- can manage to scan more than one port

if you want to scan port 22, 80, 443 and 445 then it should be
sudo nmap **-p22,80,443,445** --min-rate 10000 -oA scans/nmap-alltcp 192.168.1.103
to scan only 4 specific port

what if you want to scan a range of port, you can try
sudo nmap **-p1-100** --min-rate 10000 -oA scans/nmap-alltcp 192.168.1.103
to scan port 1 to port 100
--------------------------------------------------------------------
sudo nmap -p- --min-rate 10000 -oA scans/nmap-alltcp 192.168.1.103 -sU
-sU --> scan UDP port
--------------------------------------------------------------------
# Service Enumeration
sudo nmap -p[discovered,ports] -sV ip
sudo nmap -p21,22,23 -sV -oA scans/nmap-tcpscans 192.168.1.103
-sV --> to find out the version of the software and what service are running on which port
--------------------------------------------------------------------
sudo nmap -O 192.168.1.101
-O --> to find out which operating system is running. such as Linux.
--------------------------------------------------------------------
Nmap Scripting
sudo nmap -p[discovered,ports] -sC ip

to be updated
--------------------------------------------------------------------
nmap -p- 192.168.0.1
this command will list out all the port 
scanning same lan/subnet/scanner
ICMP ECHO (ping) requests
ARP requests
SYN and ACK requests
--------------------------------------------------------------------

