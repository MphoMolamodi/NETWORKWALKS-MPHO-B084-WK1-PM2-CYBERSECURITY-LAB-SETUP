# NETWORKWALKS-MPHO-B084-WK1-PM2-CYBERSECURITY-LAB-SETUP

## Pentesting and zenmap 



## Pentester Name 
(Cybersecurity Professional) 

    Mpho Molamodi 

## Program/Batch 

B082-Networkwalks 

## Date 

14 November 2026 

## Modules completed 

W2-PM1 (Multiple Kali Tools) 

W2-PM5 (Zenmap Scanning) 

## Client/Target 

1. Networkwalks (secured written permission already) 

2. My own local LAN Network 

## Permission secured from client? 

Yes 

## Phases covered


Phase 1: Reconnaissance & Footprinting 
Phase 2: Scanning & Network Discovery 



## 1. Liability Disclaimer 

I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. Do not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorised access is a crime even when nothing is damaged.


## 2. Introduction 

This report covers footprinting the networkwalks.com domain using multiple Kali Linux tools (W2-PM1) and scanning my own local network with Zenmap (W2-PM5). One module covers the footprinting phase and the other covers the scanning phase, so together they show how an attacker moves from gathering public information to mapping live hosts on a network. It is the Week 2 part of my ongoing internship program at Networkwalks. 

All commands were run in Kali Linux (footprinting) and on a Windows PC with Zenmap installed (scanning). Every step below includes the exact command used, the result I observed, a screenshot as evidence, and a short note on why the finding matters from an attacker's point of view. 

 

## 3. Tools Used 



# Kali Linux & Windows 

Operating systems used for reconnaissance activities 

# WHOIS 

Find domain registration details (owner, dates, name servers). 

# whatweb 

Fingerprint web technologies (server, CMS, plugins, IP). 

# nslookup 

Resolve the domain name to its IP address using DNS. 

# curl -I 

Read the HTTP response headers of the website. 

# wafw00f 

Detect whether a Web Application Firewall protects the site. 

# dnsrecon 

Enumerate all DNS records (NS, MX, SPF, TXT, SRV). 

# Zenmap (Nmap GUI) 

Scan the local subnet to find live hosts, IPs and MAC addresses. 

# Windows CMD 

Local IP and MAC address identification 




## 4.1 Footprinting & Reconnaissance 

 

I performed reconnaissance against the networkwalks.com domain using six Kali Linux tools: WHOIS, WhatWeb, Nslookup, Curl, Wafw00f and DNSRecon. Each tool was used to collect a different type of information about the target. 

First, I used WHOIS to obtain publicly available domain registration information and identify the domain’s name servers. The results provided information about the domain registration and hosting infrastructure. 

I then used WhatWeb to identify technologies used by the website. The results identified WordPress 7.0.4 and WP Download Manager 3.3.58, along with other information exposed by the website. 

Using Nslookup, I resolved the domain name to its IP address. The provided result identified 192.232.216.135. 

I used Curl with the -I option to inspect the HTTP response headers. This provided additional information about the web application and exposed the WordPress REST API endpoint /wp-json/. 

Next, I used Wafw00f to determine whether a Web Application Firewall was protecting the website. The result identified ModSecurity (SpiderLabs). 

Finally, I used DNSRecon to enumerate DNS records. The results provided information relating to name servers, mail servers, SPF/TXT records, service records and DNS software information. 

 

 

## 4.2 Network Scanning with Zenmap 

For the second activity, I used Zenmap to perform network discovery on my local network. The practical required me to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, and generate a network topology. 

I first used the Windows ipconfig command to identify my local IP address and LAN subnet. I then entered the subnet into Zenmap and selected Ping Scan to identify active hosts. 

The example results provided in the practical identified One host: 

192.168.38.223

The example results also included one MAC addresses. 

After completing the scan, I opened the Topology section in Zenmap, enabled the legend and saved the network topology in PDF format as required by the practical task. 




## 5. Risk Analysis / Impact 

Based on the information collected during the footprinting and network scanning activities, I identified the following potential risks. 



Risk / Finding 

Evidence / Observation 

Potential Impact 

Risk Level 



## 1 Web technology information exposed 

WhatWeb identified WordPress and WP Download Manager 

Attackers may use exposed technology/version information to identify software requiring further security review 

● Medium 



## 2 Server IP address identifiable 

Nslookup resolved the domain to 192.232.216.135 

Provides information about the network location of the web service 

● Low 



## 3 HTTP technical information exposed 

Curl returned HTTP response headers and exposed /wp-json/ 

May assist technology fingerprinting and further enumeration 

● Low 



## 4 WAF technology identifiable 

Wafw00f identified ModSecurity (SpiderLabs) 

Reveals information about the web application’s security architecture 

● Low 



## 5 DNS infrastructure information exposed 

DNSRecon identified DNS, mail and service-related records 

DNS information can help build a broader infrastructure profile 

● Medium 

 

## 6 Multiple live hosts visible on local network 

Zenmap identified one live host in the example network 

Unknown or unauthorized devices may potentially be present on a network 

● Medium 



## 6. Recommendations 

Based on the observations from these activities, I recommend the following security improvements: 

Review publicly exposed technology information 
Organizations should regularly review what information about their web technologies, CMS and plugins is publicly visible. 

Keep software updated 
CMS platforms, plugins and other web technologies should be regularly updated and reviewed against current security advisories. 

Review HTTP headers 
HTTP response headers should be reviewed to determine whether unnecessary technical information is being exposed. 


## 7 Evidence



 <img width="1535" height="805" alt="Screenshot 2026-11-12 222550" src="https://github.com/user-attachments/assets/2080035e-842a-4eb8-8c5d-4026d6cf896d" />




 
<img width="1920" height="922" alt="Screenshot 2026-11-12 222458" src="https://github.com/user-attachments/assets/defa6d52-b065-4996-a37e-5fa8cee804ad" />





<img width="1920" height="922" alt="Screenshot 2026-11-12 221010" src="https://github.com/user-attachments/assets/089fc166-0a58-4863-bd6f-44d50246011b" />




<img width="1920" height="922" alt="wafw00f" src="https://github.com/user-attachments/assets/70c720a1-a411-4e88-b381-d0461de8c167" />




<img width="1920" height="922" alt="dnsrecon" src="https://github.com/user-attachments/assets/98606432-a363-4744-82a9-58b98c4df5a4" />




<img width="1920" height="922" alt="nslookup" src="https://github.com/user-attachments/assets/118d1eec-3b0c-432f-ba12-f6bb4905f2dd" /> 



  
<img width="1920" height="922" alt="curl" src="https://github.com/user-attachments/assets/777823de-b482-43b8-b676-8dc2073e69e2" />



  
<img width="1920" height="922" alt="whatweb" src="https://github.com/user-attachments/assets/f758ef01-a58f-404b-8017-63de05e39e7d" />




<img width="1920" height="923" alt="whois" src="https://github.com/user-attachments/assets/600a9131-19d3-4fd6-a5d6-c47f5ee88e33" />







