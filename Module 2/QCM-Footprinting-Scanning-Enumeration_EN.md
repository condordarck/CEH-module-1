# CEH Practice Questions — Footprinting, Scanning & Enumeration
## Real QCM format (English) — 103 questions

> Practice exam based on the official CEH v13 dumps (Module 02 - Footprinting & Reconnaissance,
> Module 03 - Scanning Networks, Module 04 - Enumeration).
> Choose the **best answer** for each question. **Answers & explanations are at the bottom.**

---

## SECTION 1 — FOOTPRINTING OSINT (Q1–Q36)

**Q1.** Which of the following search engine tools helps an attacker use an image as a search query and track the original source and details of images, such as photographs, profile pictures, and memes?
- A) Mention
- B) Intelius
- C) Sublist3r
- D) TinEye

**Q2.** Which of the following web services provides useful information about a target company, such as the market value of the company's shares, company profile, and competitor details?
- A) investing.com
- B) linkup.com
- C) dice.com
- D) indeed.com

**Q3.** Which of the following deep and dark web searching tools helps an attacker obtain information about official government or federal databases and navigate anonymously without being traced?
- A) Spokeo
- B) Whitepages
- C) ExoneraTor
- D) Been Verified

**Q4.** Which of the following web services is a repository that contains a collection of user-submitted notes or messages on various subjects and topics?
- A) People search services
- B) NNTP Usenet newsgroups
- C) Business profile sites
- D) Online reputation services

**Q5.** Which of the following activities of an organization on social networking sites helps an attacker footprint or collect information regarding the type of business handled by the organization?
- A) Background checks to hire employees
- B) Promotion of products
- C) User support
- D) User surveys

**Q6.** Which of the following activities of a user on social networking sites helps an attacker footprint or collect the identity of the user's family members, the user's interests, and related information?
- A) Creating events
- B) Maintaining the profile
- C) Sharing photos and videos
- D) Playing games and joining groups

**Q7.** In website footprinting, which of the following information is acquired by the attacker when they examine the cookies set by the server?
- A) Contact details of the web developer or admin
- B) File-system structure and script type
- C) Comments present in the source code
- D) Software in use and its behavior

**Q8.** Sean works as a professional ethical hacker and penetration tester. He is assigned a project for information gathering on a client's network. He started penetration testing and was trying to find out the company's internal URLs, looking for any information about the different departments and business units. Sean was unable to find any information. What should Sean do to get the information he needs?
- A) Sean should use Sublist3r tool
- B) Sean should use WayBackMachine in Archive.org
- C) Sean should use website mirroring tools
- D) Sean should use email tracking tools

**Q9.** You are doing research on SQL injection attacks. Which of the following combination of Google operators will you use to find all Wikipedia pages that contain information about SQL, injection attacks, or SQL injection techniques?
- A) SQL injection site:Wikipedia.org
- B) site:Wikipedia.org related:"SQL Injection"
- C) allinurl: Wikipedia.org intitle:"SQL Injection"
- D) site:Wikipedia.org intitle:"SQL Injection"

**Q10.** Which of the following tools consists of a publicly available set of databases that contain personal information of domain owners?
- A) Metadata extraction tools
- B) WHOIS lookup tools
- C) Traceroute tools
- D) Web spidering tools

**Q11.** What information is gathered about the victim using email tracking tools?
- A) Information on an organization's web pages since their creation
- B) Targeted contact data, extracts the URL and meta tag for website promotion
- C) Recipient's IP address, geolocation, proxy detection, operating system, and browser information
- D) Username of the clients, operating systems, email addresses, and list of software

**Q12.** Which Google search query can you use to find mail lists dumped on pastebin.com?
- A) allinurl: pastebin.com intitle:*@*.com:*
- B) site:pastebin.com intext:*@*.com:*
- C) cache: pastebin.com intitle:*@*.com:*
- D) allinurl: pastebin.com intitle:"mail lists"

**Q13.** Which of the following DNS record types indicates the authority for a domain of the target DNS server?
- A) CNAME
- B) PTR
- C) SOA
- D) SRV

**Q14.** Which of the following types of DNS records points to a host's IP address?
- A) NS
- B) A
- C) TXT
- D) HINFO

**Q15.** Which of the following is the direct approach technique that serves as the primary source for attackers to gather competitive intelligence?
- A) Social engineering
- B) Search engines, Internet, and online databases
- C) Support threads and reviews
- D) Social media postings

**Q16.** Which of the following tools is used for gathering email account information from different public sources and checking whether an email was leaked using the haveibeenpwned.com API?
- A) Metagoofil
- B) Infoga
- C) Professional Toolset
- D) Octoparse

**Q17.** Which results will be returned with the following Google search query? `site:target.com -site:Marketing.target.com accounting`
- A) Results from matches on the site marketing.target.com that are in the domain target.com but do not include the word accounting
- B) Results matching all words in the query
- C) Results matching "accounting" in domain target.com but not on the site Marketing.target.com
- D) Results for matches on target.com and Marketing.target.com that include the word "accounting"

**Q18.** Which Google search query will search for any files a target certifiedhacker.com may have?
- A) site: certifiedhacker.com ext:xml || ext:conf || ext:cnf || ext:reg || ext:inf || ext:rdp || ext:cfg || ext:txt || ext:ora || ext:ini
- B) site: certifiedhacker.com intext:xml | intext:conf | intext:cnf | intext:reg | intext:inf | intext:rdp | intext:cfg | intext:txt | intext:ora | intext:ini
- C) site: certifiedhacker.com filetype:xml | filetype:conf | filetype:cnf | filetype:reg | filetype:inf | filetype:rdp | filetype:cfg | filetype:txt | filetype:ora | filetype:ini
- D) allinurl: certifiedhacker.com ext:xml | ext:conf | ext:cnf | ext:reg | ext:inf | ext:rdp | ext:cfg | ext:txt | ext:ora | ext:ini

**Q19.** What is the output returned by search engines when extracting critical details about a target from the Internet?
- A) Advanced search operators
- B) Search engine results pages ("SERPs")
- C) Open ports and services
- D) Operating systems, location of web servers, users, and passwords

**Q20.** Which of the following techniques is used to create complex search engine queries?
- A) DuckDuckGo
- B) Bing search
- C) Yahoo search
- D) Google hacking

**Q21.** James, a professional hacker, targeted the employees of an organization to establish footprints in their network. For this purpose, he employed an online reconnaissance tool to extract information on individuals belonging to the target organization. The tool assisted James in obtaining employee information such as phone numbers, email addresses, address history, age, date of birth, family members, and social profiles. Identify the tool employed by James in the above scenario.
- A) Nikto
- B) KFSensor
- C) Spokeo
- D) Photon

**Q22.** Sean works as a penetration tester in ABC firm. He was asked to gather information about the target company. Sean begins with social engineering by following the steps: secretly observes the target to gain critical information; looks at employee's password or PIN code with the help of binoculars or a low-power telescope. Based on the above description, identify the social engineering technique.
- A) Shoulder surfing
- B) Phishing
- C) Dumpster diving
- D) Tailgating

**Q23.** Which of the following tools allows an attacker to extract information such as sender identity, mail server, sender's IP address, location, and so on?
- A) Web updates monitoring tools
- B) Metadata extraction tools
- C) Email tracking tools
- D) Website mirroring tools

**Q24.** Which of the following is a query and response protocol used for querying databases that store the registered users or assignees of an Internet resource, such as a domain name, an IP address block, or an autonomous system?
- A) TCP/IP
- B) Traceroute
- C) Whois lookup
- D) DNS lookup

**Q25.** Robert, an attacker, targeted a high-level executive of an organization and wanted to obtain information about the executive on the Internet. He employed a tool through which he discovered the target user on various social networking sites, along with the complete URL. What is the tool used by Robert in the above scenario?
- A) Sherlock
- B) OpUtils
- C) BeRoot
- D) Sublist3r

**Q26.** Jacob, a professional hacker, targeted an organization's website to find a way into its network. To achieve his goal, he employed a footprinting tool that helped him in gathering confidential files and other relevant information related to the target website from public source-code repositories. Identify the footprinting tool employed by Jacob in the above scenario.
- A) Reverse Lookup
- B) Netcraft
- C) ShellPhish
- D) Recon-ng

**Q27.** Which of the following is a visualization and exploration tool that allows attackers to explore and understand graphs, create hypotheses, and discover hidden patterns between social networking connections?
- A) Netcraft
- B) Gephi
- C) Mention
- D) theHarvester

**Q28.** Which of the following tools are useful in extracting information about the geographical location of routers, servers, and IP devices in a network?
- A) Email tracking tools
- B) Web spidering tools
- C) Website mirroring tools
- D) Traceroute tools

**Q29.** Steve, an attacker, wants to track the most shared content that belongs to the target organization. For this purpose, he used an advanced social search engine that displayed shared activity across all major social networks including Twitter, Facebook, LinkedIn, Google Plus, and Pinterest. What is the tool employed by Steve in the above scenario?
- A) Wireshark
- B) Vindicate
- C) BuzzSumo
- D) Robber

**Q30.** Which of the following tools allows attackers to search for people belonging to the target organization?
- A) Spokeo
- B) GFI LanGuard
- C) OpenVAS
- D) Netcraft

**Q31.** Which of the following tools is a command-line search tool for Exploit-DB that allows taking a copy of the Exploit database for remote use?
- A) Spokeo
- B) SearchSploit
- C) DroidSniff
- D) Spyse

**Q32.** Peter, a professional hacker, targeted an organization's network to gather as much information as possible to perform future attacks. For this purpose, he employed a reconnaissance framework that helped him gather confidential information such as private Secure Shell (SSH) and Secure Sockets Layer (SSL) keys as well as dynamic libraries from an online third-party repository. Identify the online third-party repository targeted by Peter in the above scenario.
- A) Sublist3r
- B) GitLab
- C) MITRE ATT&CK framework
- D) BeRoot

**Q33.** Which of the following tools allows attackers to construct and analyze social networks and obtain critical information about the target organization/users?
- A) Burp Suite
- B) Mention
- C) HTTrack Web Site Copier
- D) NodeXL

**Q34.** Jude, a professional hacker, targeted an organization's web server. Jude wanted to extract the information removed from older copies or archived links of the target website. For this purpose, he employed an exploration tool that assisted him in retrieving the archived URLs of the target website. Identify the tool employed by Jude in the above scenario.
- A) Gephi
- B) Netcraft
- C) Photon
- D) Burp Suite

**Q35.** Which of the following commands allows attackers to retrieve the archived URLs of a target website from archive.org?
- A) theHarvester -d microsoft -1 200 -b linkedin
- B) cewl www.certifiedhacker.com
- C) theHarvester -d microsoft.com -1 200 -b linkedin
- D) photon.py -u http//www.certifiedhacker.com -1 3 -t 200 --wayback

**Q36.** Which of the following tools allows attackers to retrieve archived URLs of a target website from archive.org?
- A) Burp Suite
- B) Photon
- C) SecurityTrails
- D) Sublist3r


---

## SECTION 2 — ADVANCED FOOTPRINTING TOOLS (Q37–Q49)

**Q37.** Which of the following features in FOCA allows an attacker to find more servers in the same segment of a determined address?
- A) IP resolution
- B) DNS search
- C) PTR scanning
- D) Web search

**Q38.** Which of the following is an online platform that can be used to collect and analyze information about devices and websites available on the Internet?
- A) Zimperium's zIPS
- B) FTK Imager
- C) Dependency Walker
- D) Spyse

**Q39.** Which of the following tools allows attackers to collect information such as subdomains, IP addresses, HTTP response status, SSL/TLS certificates, vulnerability scores, and DNS records of the target domain or website?
- A) Spyse
- B) THC-Hydra
- C) L0phtCrack
- D) Nagios

**Q40.** Which of the following practices helps security specialists protect a network against footprinting attempts?
- A) Configure mail servers to ignore mails from anonymous individuals
- B) Do not keep the domain name profile private
- C) Never disable or delete the accounts of employees who left the organization
- D) Enable the geo-tagging functionality on cameras to allow geolocation tracking

**Q41.** Which of the following practices allows security professionals to defend an organization's network against footprinting attempts?
- A) Never use TCP/IP and IPsec filters for defense in depth
- B) Disable or delete the accounts of employees who left the organization
- C) Always enable protocols that are not required
- D) Reveal location or travel plans on social networking sites

**Q42.** Which of the following options of Sublist3r allows the user to specify a comma-separated list of search engines?
- A) -o
- B) -e
- C) -p
- D) -d

**Q43.** Which of the following should NOT be followed when securing an organization from footprinting attacks?
- A) Opting for privacy services on the Whois lookup database
- B) Enabling the geo-tagging functionality on cameras
- C) Educating employees to use pseudonyms on blogs, groups, and forums
- D) Ensuring that critical information is not revealed in press releases, annual reports, product catalogs, and so on

**Q44.** Which of the following countermeasures should be followed to safeguard the privacy, data, and reputation of an organization and to prevent information disclosure?
- A) Enabling directory listings in the web servers
- B) Keeping the domain name profile public
- C) Avoiding domain-level cross-linking for critical assets
- D) Turning on geolocation access on all mobile devices

**Q45.** Which of the following tools does an attacker use to perform a query on the platforms included in OSRFramework?
- A) mailfy.py
- B) searchfy.py
- C) usufy.py
- D) domainfy.py

**Q46.** Which of the following utilities is used by Recon-Dog to detect technologies existing in the target system?
- A) wappalyzer.com
- B) Whois lookup
- C) findsubdomains.com
- D) shodan.io

**Q47.** Which of the following options of Sublist3r allows the user to specify a comma-separated list of search engines?
- A) -e
- B) -p
- C) -o
- D) -d

**Q48.** Which of the following features in FOCA allows an attacker to find more servers in the same segment of a determined address?
- A) PTR scanning
- B) Web search
- C) DNS search
- D) IP resolution

**Q49.** Which of the following practices helps security specialists protect a network against footprinting attempts?
- A) Never disable or delete the accounts of employees who left the organization
- B) Configure mail servers to ignore mails from anonymous individuals
- C) Do not keep the domain name profile private
- D) Enable the geo-tagging functionality on cameras to allow geolocation tracking

---

## SECTION 3 — PING / NETWORK SCANNING (Q50–Q59)

**Q50.** Which of the following ping methods is effective in identifying active hosts similar to the ICMP timestamp ping, specifically when the administrator blocks the conventional ICMP ECHO ping?
- A) UDP ping scan
- B) ICMP ECHO ping scan
- C) ICMP ECHO ping sweep
- D) ICMP address mask ping scan

**Q51.** Which of the following protocols uses the port number 88/TCP and can verify the identity of a user or host connected to a network?
- A) TFTP
- B) Finger
- C) Kerberos
- D) NTP

**Q52.** Which of the following scans detects when a port is open after completing the three-way handshake, establishes a full connection, and closes the connection by sending an RST packet?
- A) IDLE/IPID header scan
- B) Stealth scan
- C) TCP connect scan
- D) ACK flag probe scan

**Q53.** Which of the following Nmap options is used by an attacker to perform an SCTP COOKIE ECHO scan?
- A) -sZ
- B) -sY
- C) -sL
- D) -sU

**Q54.** In which of the following scanning techniques does an attacker send a spoofed source address to a computer to determine the available services?
- A) ACK flag probe scan
- B) Inverse TCP flag scan
- C) TCP Maimon scan
- D) IDLE/IPID header scan

**Q55.** While performing a UDP scan of a subnet, you receive an ICMP reply of Code 3/Type 3 for all the pings you have sent out. What is the most likely cause of this?
- A) UDP port is closed.
- B) The host does not respond to ICMP packets.
- C) The firewall is dropping the packets.
- D) UDP port is open.

**Q56.** A security engineer is attempting to perform scanning on a company's internal network to verify security policies of their networks. The engineer uses the following NMAP command: `nmap –n –sS –P0 –p 80 ***.***.**.**`. What type of scan is this?
- A) Quick scan
- B) Intense scan
- C) Comprehensive scan
- D) Stealth scan

**Q57.** A penetration tester is conducting a port scan on a specific host. The tester found several open ports that were confusing in concluding the operating system (OS) version installed. Considering the NMAP result below, which of the following is likely to be installed on the target machine by the OS?

```
NMAP scan report for 172.16.40.65
PORT      STATE    SERVICE
21/tcp    open     ftp
23/tcp    open     telnet
80/tcp    open     http
139/tcp   open     netbios-ssn
515/tcp   open     (LPD)
631/tcp   open     ipp
9100/tcp  open     (raw printing)
MAC Address: 00:00:48:0D:EE:89
```
- A) The host is likely a printer.
- B) The host is likely a router.
- C) The host is likely a Linux machine.
- D) The host is likely a Windows machine.

**Q58.** Which NMAP command combination would let a tester scan every TCP port from a class C network that is blocking ICMP with fingerprinting and service detection?
- A) NMAP -P0 -A -O -p1-65535 192.168.0/24
- B) NMAP -PN -A -O -sS 192.168.2.0/24
- C) NMAP -PN -O -sS -p 1-1024 192.168.0/8
- D) NMAP -P0 -A -sT -p0-65535 192.168.0/16

**Q59.** Which protocol and port number might be needed to send log messages to a log analysis tool that resides behind a firewall?
- A) UDP 514
- B) UDP 123
- C) UDP 415
- D) UDP 541


---

## SECTION 4 — TCP FLAGS / HPING / NMAP (Q60–Q69)

**Q60.** Which of the following TCP communication flags confirms the receipt of a transmission and identifies the next expected sequence number?
- A) FIN flag
- B) SYN flag
- C) ACK flag
- D) RST flag

**Q61.** Which of the following TCP communication flags notifies the transmission of a new sequence number and represents the establishment of a connection between two hosts?
- A) PSH flag
- B) SYN flag
- C) RST flag
- D) FIN flag

**Q62.** Which of the following types of scanning involves the process of checking the services running on a target computer by sending a sequence of messages to break in?
- A) Vulnerability scanning
- B) Banner grabbing
- C) Network scanning
- D) Port scanning

**Q63.** Which of the following TCP communication flags is set to "1" to announce that no more transmissions will be sent to the remote system and the connection established by the SYN flag is terminated?
- A) ACK flag
- B) FIN flag
- C) SYN flag
- D) RST flag

**Q64.** Which of the following is NOT an objective of network scanning?
- A) Discover the network's live hosts
- B) Discover the services running
- C) Discover usernames and passwords

**Q65.** Which of the following hping commands is used by an attacker to collect the initial sequence number (ISN)?
- A) hping3 192.168.1.103 -Q -p 139 -s
- B) hping3 -2 10.0.0.25 –p 80
- C) hping3 –A 10.0.0.25 –p 80
- D) hping3 -S 72.14.207.99 -p 80 --tcp-timestamp

**Q66.** Which of the following scanning tools is a mobile app for Android and iOS that provides complete network information, such as the IP address, MAC address, device vendor, and ISP location?
- A) Netcraft
- B) Fing
- C) Maltego
- D) Nmap

**Q67.** If a tester is attempting to ping a target that exists but receives no response or a response that states the destination is unreachable, ICMP may be disabled and the network may be using TCP. Which other option could the tester use to get a response from a host using TCP?
- A) Traceroute
- B) TCP ping
- C) Broadcast ping
- D) Hping

**Q68.** Which of the following open-source tools would be the best choice to scan a network for potential targets?
- A) Cain & Abel
- B) NMAP
- C) hashcat
- D) John the Ripper

**Q69.** Which of the following Hping3 command is used to perform an ACK scan?
- A) hping3 -2 <IP Address> –p 80
- B) hping3 -1 <IP Address> –p 80
- C) hping3 –A <IP Address> –p 80
- D) hping3 -8 50-60 –S <IP Address> –V

---

## SECTION 5 — BANNER GRABBING / SPOOFING COUNTERMEASURES (Q70–Q77)

**Q70.** Which of the following countermeasures is used to avoid banner grabbing attacks?
- A) Turn on unnecessary services on the network host to limit information disclosure
- B) Never display false banners to mislead or deceive attackers
- C) Use ServerMask tools to disable or change banner information
- D) Enable the details of the vendor and version in the banners

**Q71.** Which of the following types of techniques is used to prevent IP spoofing by blocking outgoing packets with a source address that is not inside?
- A) Egress filtering
- B) Random initial sequence numbers
- C) Ingress filtering
- D) Access-control lists

**Q72.** Which of the following practices can make the organization's network susceptible to port scanning attempts?
- A) Test how the network firewall and IDS manages fragmented packets using fragtest and fragroute
- B) Avoid using proxy servers to block fragmented or malformed packets
- C) Configure commercial firewalls to protect the network against fast port scans and SYN floods
- D) Block inbound ICMP message types and all outbound ICMP type-3 unreachable messages at border routers arranged in front of the company's main firewall

**Q73.** Which of the following practices helps security professionals prevent banner grabbing attempts on the host?
- A) Never display false banners to mislead or deceive attackers.
- B) Turn on unnecessary services on the network host to limit information disclosure.
- C) Never use server masking tools to disable or change banner information.
- D) Modify the value of Server Tokens from Full to Prod in Apache's httpd.conf file to prevent disclosure of the server version.

**Q74.** Which of the following practices can make the target device or system vulnerable to banner grabbing attacks?
- A) Change the ServerSignature line to ServerSignatureOff in the httpd.conf file.
- B) Enable HTTP methods such as Connect, Put, Delete, and Options from web application servers.
- C) For Apache 2.x with the mod_headers module, use a directive in the httpd.conf file to change the banner information header and set the server as New Server Name.
- D) Disable the details of the vendor and version in the banners.

**Q75.** Which of the following countermeasure helps organizations to prevent information disclosure through banner grabbing?
- A) Disable the DNS zone transfers to the untrusted hosts
- B) Disable open relay feature
- C) Restrict anonymous access through RestrictNullSessAccess parameter from the Windows registry
- D) Display false banners

**Q76.** Which of the following practices helps security professionals defend a network or service against port scanning attempts?
- A) Ensure that TCP wrappers limit access to the network based on domain names or IP addresses.
- B) Never use port scanning tools against hosts on the network.
- C) Never configure firewall and intrusion detection system (IDS) rules to block probes.
- D) Never use a custom rule set to lock down the network and block unwanted ports at the firewall.

**Q77.** Which of the following practices allows attackers to spoof the IP addresses of users to enter a network illegitimately?
- A) Enhance the integrity and confidentiality of websites by migrating from IPv4 to IPv6 during development.
- B) Use a secure VPN while accessing public Internet services such as free Wi-Fi and hotspots.
- C) Avoid configuring routers to verify the data packets using their signatures by storing the arriving data packet digests.
- D) Implement digital certificate authentication mechanisms such as domain and two-way auth certificate verification.


---

## SECTION 6 — OS FINGERPRINTING & IDS/FIREWALL EVASION (Q78–Q85)

**Q78.** Which of the following OS discovery techniques is used by an attacker to identify a target machine's OS by observing the TTL values in the acquired scan result?
- A) OS discovery using Unicornscan
- B) OS discovery using Nmap
- C) OS discovery using IPv6 fingerprinting
- D) OS discovery using Nmap Script Engine

**Q79.** What type of OS fingerprinting technique sends specially crafted packets to the remote OS and analyzes the received response?
- A) Distributive
- B) Reflective
- C) Passive
- D) Active

**Q80.** Which of the following IDS/firewall evasion techniques is used by an attacker to bypass Internet censors and evade certain IDS and firewall rules?
- A) Source port manipulation
- B) IP address decoy
- C) Sending bad checksums
- D) Anonymizers

**Q81.** Which of the following IDS/firewall evasion techniques helps an attacker increase their Internet anonymity?
- A) Source port manipulation
- B) Proxy chaining
- C) IP address decoy
- D) Source routing

**Q82.** Which of the following commands allows attackers to auto-generate a random MAC address and attach it to the packets in place of the original MAC address while performing host scanning?
- A) nmap -sU -v [Target IP]
- B) nmap -sT -Pn –spoof-mac [new MAC] [Target IP]
- C) Cewl www.certifiedhacker.com
- D) nmap -sT -Pn –spoof-mac 0 [Target IP]

**Q83.** Which of the following techniques helps the attacker in identifying the OS used on the target host in order to detect vulnerabilities on a target system?
- A) Port scanning
- B) IP address decoy
- C) Banner grabbing
- D) Source routing

**Q84.** Which of the following is the active banner grabbing technique used by an attacker to determine the OS running on a remote target system?
- A) Banner grabbing from page extensions
- B) Sniffing of network traffic
- C) TCP sequence ability test
- D) Banner grabbing from error messages

**Q85.** Which NMAP feature can a tester implement or adjust while scanning for open ports to avoid detection by the network's IDS?
- A) Timing options to slow the speed that the port scan is conducted
- B) Fingerprinting to identify which operating systems are running on the network
- C) ICMP ping sweep to determine which hosts on the network are not available
- D) Traceroute to control the path of the packets sent during the scan

---

## SECTION 7 — ENUMERATION & PORTS (Q86–Q97)

**Q86.** In which of the following enumeration techniques does an attacker take advantage of different error messages generated during the service authentication process?
- A) Brute-force Active Directory
- B) Extracting information using default passwords
- C) Extracting usernames using email IDs
- D) Extracting usernames using SNMP

**Q87.** Which of the following protocols uses TCP port 179 to enable routers for establishing sessions between them?
- A) SIP
- B) BGP
- C) LDAP
- D) SNMP

**Q88.** Which of the following port numbers is used by the Windows NetBIOS session service for both null-session establishment as well as file and printer sharing?
- A) TCP/UDP 53
- B) TCP 23
- C) TCP 139
- D) TCP/UDP 389

**Q89.** Which of the following ports provides a name-resolution service for computers running NetBIOS that is also known as the Windows Internet Name Service (WINS)?
- A) UDP 137
- B) TCP 135
- C) UDP 161
- D) TCP 22

**Q90.** Which of the following protocols is widely used by Internet service providers (ISPs) to maintain huge routing tables and efficiently process Internet traffic?
- A) TFTP
- B) FTP
- C) SIP
- D) BGP

**Q91.** Which of the following information is collected using enumeration?
- A) Operating systems, location of web servers, users, and passwords
- B) Email Recipient's system IP address and geolocation
- C) Network resources, network shares, and machine names
- D) Open ports and services

**Q92.** Which of the following port numbers is used to exploit vulnerabilities within DNS servers to launch attacks?
- A) TCP 139
- B) TCP/UDP 53
- C) TCP/UDP 135
- D) UDP 137

**Q93.** Which of the following protocols uses TCP or UDP as its transport protocol over port 389?
- A) SNMP
- B) LDAP
- C) SMTP
- D) SIP

**Q94.** Which of the following protocols provides reliable multiprocess communication service in a multinetwork environment?
- A) SNMP
- B) UDP
- C) SMTP
- D) TCP

**Q95.** An attacker identified that port 139 on the victim's Windows machine is open and he used that port to identify the resources that can be accessed or viewed on the remote system. What is the protocol that allowed the attacker to perform this enumeration?
- A) SNMP
- B) LDAP
- C) NetBIOS
- D) SMTP

**Q96.** What is the default port used by IPSEC IKE protocol?
- A) Port 50
- B) Port 4500
- C) Port 500
- D) Port 51

**Q97.** Jake, an attacker, is performing an attack on a target organization to gather sensitive information. In this process, he exploited the protocol running on port 23 to perform banner grabbing on other protocols, such as SSH and SMTP, as well as brute-forcing attacks on login credentials. Which of the following protocols is running on port 23?
- A) Secure Shell
- B) Telnet
- C) File Transfer Protocol
- D) Border Gateway Protocol

---

## SECTION 8 — LDAP ENUMERATION (Q98–Q103)

**Q98.** Which of the following LDAP enumeration tools is used by an attacker to access the directory listings within Active Directory or other directory services?
- A) HULK
- B) AD Explorer
- C) Slowloris
- D) XOIC

**Q99.** Which of the following protocols is responsible for accessing distributed directories and access information such as valid usernames, addresses, departmental details, and so on?
- A) SMTP
- B) NTP
- C) DNS
- D) LDAP

**Q100.** Which of the following tools can be used to perform LDAP enumeration?
- A) AD Explorer
- B) SuperScan
- C) Nsauditor network security auditor
- D) SoftPerfect network scanner

**Q101.** Edward, a professional hacker, was tasked with hacking critical information of a target organization. For this purpose, Edward initiated an LDAP enumeration process. Using a Python script, he successfully established a connection with the target LDAP server and executed the following script:
```
>>> connection.search(search_base='DC=DOMAIN,DC=DOMAIN', search_filter='(&(objectClass=*))', search_scope='SUBTREE', attributes='*')
True
>>> connection.entries
```
Which of the following did Edward accomplish using the above Python script?
- A) Listed all applications
- B) Retrieved the DSA-specific entry (DSE) naming contexts
- C) Retrieved all directory objects
- D) Created a connection object

**Q102.** Identify the tool used by attackers to enumerate AD users and perform different searches using specific filters.
- A) PortQry
- B) DNSRecon
- C) Ladpsearch
- D) netstat

**Q103.** Which of the following tools allows attackers to perform LDAP enumeration on the target network?
- A) Euromonitor
- B) nbtstat
- C) DNSRecon
- D) AD Explorer


---

# ANSWERS & EXPLANATIONS

## SECTION 1 — FOOTPRINTING OSINT

**Q1. D) TinEye** — Reverse image search tool (with Google Image Search, Yahoo, Bing) used to find the source/origin of an image. *Others:* Mention = online reputation monitoring; Intelius = people search; Sublist3r = subdomain enumeration.

**Q2. A) investing.com** — Financial services (Google Finance, MSN Money, Yahoo Finance, Investing.com) provide share market value, company profile, competitor details, financial reports. *Others:* indeed.com, dice.com, linkup.com = online job services.

**Q3. C) ExoneraTor** — Deep/dark web search tool (with Tor Browser, OnionLand) to gather confidential info anonymously. *Others:* Spokeo, Been Verified, Whitepages = people search services (surface web).

**Q4. B) NNTP Usenet newsgroups** — Repository of user-submitted notes/messages on various subjects. *Others:* People search = names/contacts; Business profile sites = business info; Online reputation services = brand monitoring.

**Q5. A) Background checks to hire employees** — Mapping table: Background check → **Type of business**. *Others:* User surveys → business strategies; Promote products → product profile; User support → social engineering.

**Q6. C) Sharing photos and videos** — Mapping table: Share photos/videos → identity of family members, interests. *Others:* Maintain profile → contact info/location; Play games/join groups → interests; Create events → activities.

**Q7. D) Software in use and its behavior** — Examining cookies reveals the software running and its behavior (sessions, scripting platforms). *Others:* contact admin, file-system structure, comments = gathered from **HTML source code**, not cookies.

**Q8. A) Sublist3r** — Enumerates subdomains (internal URLs → departments/business units) using OSINT across many sources. *Others:* WayBackMachine = archived pages; website mirroring = offline copy; email tracking = recipient info.

**Q9. A) SQL injection site:Wikipedia.org** — `site:` restricts to wikipedia.org; the goal is pages containing the terms anywhere (not only in title). *Others:* intitle:/allinurl: restrict to title/URL; related: shows similar pages.

**Q10. B) WHOIS lookup tools** — Whois databases (maintained by RIRs) store personal info of domain owners, port 43/TCP. *Others:* Metadata extraction = file metadata; Traceroute = packet path; Web spidering = crawling.

**Q11. C) Recipient's IP address, geolocation, proxy detection, OS, and browser information** — Email tracking collects exactly these. *Others:* archived web pages (WayBack); URL/meta extraction (promotion); usernames/OS/email lists (other context).

**Q12. B) site:pastebin.com intext:*@*.com:*** — `site:` restricts to pastebin.com + `intext:*@*.com:*` finds email pattern in text. *Others:* intitle: (title only), cache: (cached page), allinurl: (URL).

**Q13. C) SOA** — Start Of Authority indicates authority for a domain. *Others:* CNAME = alias; PTR = IP→hostname; SRV = service records.

**Q14. B) A** — A record points to a host's IP address. *Others:* NS = name server; TXT = text; HINFO = CPU/OS.

**Q15. A) Social engineering** — Direct approach (trade shows, social engineering of employees/customers) is the primary source of competitive intelligence. *Others:* search engines, support threads, social media = **indirect** approach.

**Q16. B) Infoga** — Gathers email info from public sources + checks leaks via haveibeenpwned.com API. *Others:* Metagoofil = document metadata; Professional Toolset = DNS interrogation; Octoparse = web scraping.

**Q17. C) Results matching "accounting" in domain target.com but not on the site Marketing.target.com** — `-site:` excludes the subdomain.

**Q18. C) site: certifiedhacker.com filetype:xml | filetype:conf | ...** — `filetype:` restricts results to pages ending with that extension. *Others:* intext: = text content; ext:/allinurl: = wrong placement.

**Q19. B) Search engine results pages ("SERPs")** — Search engines return SERPs when extracting critical details.

**Q20. D) Google hacking** — Using advanced Google operators for complex queries to extract sensitive/hidden info. *Others:* DuckDuckGo, Bing, Yahoo = simple search engines.

**Q21. C) Spokeo** — People search service: phones, emails, address history, age, DOB, family, social profiles, court records. *Others:* Nikto = web server scanner; KFSensor = honeypot IDS; Photon = archived URLs.

**Q22. A) Shoulder surfing** — Observing/looking over someone's shoulder, even with binoculars or small cameras. *Others:* Phishing = fake sites; Dumpster diving = trash; Tailgating = following someone through access.

**Q23. C) Email tracking tools** — Extract sender identity, mail server, sender IP, location. *Others:* web updates monitoring, metadata extraction, website mirroring.

**Q24. C) Whois lookup** — Query/response protocol (port 43/TCP) for databases storing registered users/assignees of Internet resources. *Others:* TCP/IP = protocol suite; Traceroute = packet path; DNS lookup = zone data.

**Q25. A) Sherlock** — Finds a username on many social networks and returns the complete URL. *Others:* OpUtils = SNMP/supervision; BeRoot = privilege escalation; Sublist3r = subdomains.

**Q26. D) Recon-ng** — Full-featured reconnaissance framework; gathers confidential files from public source-code repositories. *Others:* Reverse Lookup = reverse IP/PTR; Netcraft = anti-phishing; ShellPhish = phishing tool.

**Q27. B) Gephi** — Visualization/exploration of graphs and social networks, hidden patterns. *Others:* Netcraft = anti-phishing; Mention = reputation; theHarvester = OSINT emails.

**Q28. D) Traceroute tools** — Extract geographical location of routers, servers, IP devices (hop-by-hop, reverse tracing, ping plotting, reverse DNS). *Others:* email tracking, web spidering, website mirroring.

**Q29. C) BuzzSumo** — Advanced social search engine for the most shared content across major social networks. *Others:* Wireshark = traffic capture; Vindicate = LLMNR/NBNS spoof detection; Robber = DLL hijacking.

**Q30. A) Spokeo** — Search for people belonging to the target org. *Others:* GFI LanGuard = vulnerability scan; OpenVAS = vulnerability framework; Netcraft = anti-phishing/OS detection.

**Q31. B) SearchSploit** — Command-line search tool for Exploit-DB, offline copy of the repository. *Others:* Spokeo = people search; DroidSniff = Android account capture; Spyse = devices/sites platform.

**Q32. B) GitLab** — Source-code repositories (GitHub, GitLab, SourceForge, BitBucket) contain configs, private SSH/SSL keys, dynamic libraries. *Others:* Sublist3r = subdomains; MITRE ATT&CK = knowledge base; BeRoot = privesc.

**Q33. D) NodeXL** — Tools to construct/analyze social networks (with Gephi, SocNetV). *Others:* Burp Suite = web app testing; Mention = reputation; HTTrack = site copier.

**Q34. C) Photon** — Retrieves archived URLs of the target website from archive.org. *Others:* Gephi = graphs; Netcraft = anti-phishing; Burp Suite = web testing.

**Q35. D) photon.py -u http//www.certifiedhacker.com -1 3 -t 200 --wayback** — `--wayback` retrieves archived URLs from archive.org. *Others:* theHarvester -b linkedin = LinkedIn users; -b baidu = emails via Baidu; cewl = unique words.

**Q36. B) Photon** — Archived URLs from archive.org. *Others:* Burp Suite = web testing; SecurityTrails = DNS map; Sublist3r = subdomains.

---

## SECTION 2 — ADVANCED FOOTPRINTING TOOLS

**Q37. C) PTR scanning** — FOCA feature: finds more servers in the same segment of a determined address (PTR log scan). *Others:* Web Search = hosts via URLs; DNS Search = hosts in NS/MX/SPF; IP Resolution = resolves hostnames to IPs.

**Q38. D) Spyse** — Online platform to collect/analyze info about devices and websites. *Others:* zIPS = mobile IPS; FTK Imager = forensic imaging; Dependency Walker = Windows module debugging.

**Q39. A) Spyse** — Subdomains, IPs, HTTP status, SSL/TLS certs, vulnerability scores, DNS records. *Others:* THC-Hydra = login cracker; L0phtCrack = Windows password audit; Nagios = monitoring.

**Q40. A) Configure mail servers to ignore mails from anonymous individuals** — Valid footprinting countermeasure. *Others:* the three others are bad practices (public profile, kept accounts, geo-tagging enabled).

**Q41. B) Disable or delete the accounts of employees who left the organization** — Valid countermeasure. *Others:* never using TCP/IP+IPsec, always enabling protocols, revealing location = all bad practices.

**Q42. B) -e** — `-e --engines` = comma-separated list of search engines. *Others:* -o = output file; -p = port scan; -d = domain.

**Q43. B) Enabling the geo-tagging functionality on cameras** — MUST disable geo-tagging. Question asks what should NOT be followed → the bad practice. *Others:* privacy services, pseudonyms, not revealing critical info = good practices.

**Q44. C) Avoiding domain-level cross-linking for critical assets** — Countermeasure to prevent information disclosure. *Others:* directory listings enabled, public profile, geolocation on = bad practices.

**Q45. B) searchfy.py** — Performs a query on the OSRFramework platforms. *Others:* usufy = user profiles on 290 platforms; mailfy = email existence; domainfy = domain existence.

**Q46. A) wappalyzer.com** — Recon-Dog uses wappalyzer.com to detect 1000+ technologies. *Others:* Whois lookup = whois; findsubdomains.com = subdomains; shodan.io = honeypot detection.

**Q47. A) -e** — Same as Q42.

**Q48. A) PTR scanning** — Same as Q37.

**Q49. B) Configure mail servers to ignore mails from anonymous individuals** — Same as Q40.

---

## SECTION 3 — PING / NETWORK SCANNING

**Q50. D) ICMP address mask ping scan** — Effective like timestamp ping when the admin blocks the traditional ICMP Echo ping. *Others:* ECHO ping/sweep = blocked by admin; UDP ping = UDP packets, not ICMP method.

**Q51. C) Kerberos** — Port 88/TCP, verifies identity of a user/host. *Others:* TFTP = 69; Finger = 79; NTP = 123.

**Q52. C) TCP connect scan** — Completes the 3-way handshake, then closes with RST. *Others:* Stealth = resets before handshake completion (half-open); ACK probe = TTL/WINDOW analysis; IDLE/IPID = blind scan with IPID.

**Q53. A) -sZ** — SCTP COOKIE ECHO scan. *Others:* -sY = SCTP INIT; -sU = UDP; -sL = list scan.

**Q54. D) IDLE/IPID header scan** — Sends a spoofed source address for a complete blind scan. *Others:* ACK probe = no spoof; Inverse TCP = FIN/URG/PSH; TCP Maimon = FIN/ACK (BSD).

**Q55. A) UDP port is closed** — ICMP Type 3 Code 3 = Port Unreachable (closed port). Open port = no response; no response could also be open|filtered.

**Q56. D) Stealth scan** — `-sS` = TCP SYN scan = stealth (half-open). *Others:* Quick/Intense/Comprehensive = Zenmap profiles.

**Q57. A) The host is likely a printer** — Ports 515 (LPD), 631 (IPP), 9100 (raw printing) + MAC = printer. *Others:* routers/Linux/Windows don't typically open 515/9100.

**Q58. B) NMAP -PN -A -O -sS 192.168.2.0/24** — -PN (skip host discovery, ICMP blocked) + -A (OS+services+scripts) + -O (fingerprint) + -sS (SYN) + /24 (class C). *Others:* -P0 = IP protocol ping (not "no ping"); missing -sS/-A/-O or wrong CIDR.

**Q59. A) UDP 514** — syslog listens on UDP 514. *Others:* 123 = NTP; 415/541 = non-standard for syslog.

---

## SECTION 4 — TCP FLAGS / HPING / NMAP

**Q60. C) ACK flag** — Confirms receipt and identifies next expected sequence number. *Others:* SYN = new seq/establishment; FIN = end of transmissions; RST = error/abort.

**Q61. B) SYN flag** — Notifies new sequence number, establishes connection (3-way handshake). *Others:* PSH = push data; RST = error; FIN = end.

**Q62. D) Port scanning** — CEH definition: checking services by sending a sequence of messages to break in. *Others:* Network scanning = active hosts; Vulnerability scanning = exploitable weaknesses; Banner grabbing = OS determination.

**Q63. B) FIN flag** — Set to 1 to announce no more transmissions. *Others:* ACK = receipt; SYN = establishment; RST = error.

**Q64. C) Discover usernames and passwords** — NOT an objective. Real objectives: live hosts/IPs/ports, OS/architecture, services, applications/versions, vulnerabilities.

**Q65. A) hping3 192.168.1.103 -Q -p 139 -s** — -Q -s = collect initial sequence number. *Others:* -A = ACK scan; -2 = UDP scan; -S --tcp-timestamp = firewall/timestamps.

**Q66. B) Fing** — Mobile app (Android/iOS): IP, MAC, vendor, ISP location, Wi-Fi device discovery. *Others:* Netcraft = anti-phishing; Maltego = relationship analysis; Nmap = PC scanner.

**Q67. D) Hping** — Packet crafting tool; ACK scan (-A) gets an RST response from a live host when ICMP is blocked. *Others:* Traceroute = path; TCP ping/broadcast ping = not the standard solution here.

**Q68. B) NMAP** — Open-source network scanner for hosts/services. *Others:* Cain & Abel, hashcat, John the Ripper = password crackers.

**Q69. C) hping3 –A <IP Address> –p 80** — ACK scan. *Others:* -1 = ICMP ping; -2 = UDP scan; -8 50-60 -S = SYN scan of a range.

---

## SECTION 5 — BANNER GRABBING / SPOOFING COUNTERMEASURES

**Q70. C) Use ServerMask tools to disable or change banner information** — Valid countermeasure. *Others:* turning on services, never displaying false banners, enabling vendor/version = bad practices.

**Q71. A) Egress filtering** — Blocks OUTGOING packets with a source address that is not inside. *Others:* Ingress = blocks spoofed traffic ENTERING; Random ISN = sequence numbers; ACLs = access control.

**Q72. B) Avoid using proxy servers to block fragmented or malformed packets** — Question asks the BAD practice. You SHOULD use proxies to block fragmented/malformed packets. *Others:* fragtest/fragroute, commercial firewalls, ICMP blocking = good practices.

**Q73. D) Modify the value of Server Tokens from Full to Prod in Apache's httpd.conf** — Prevents server version disclosure. *Others:* never displaying false banners, turning on services, never using masking = bad.

**Q74. B) Enable HTTP methods such as Connect, Put, Delete, and Options** — Question asks the BAD practice. These methods should be disabled. *Others:* ServerSignature Off, mod_headers banner change, disabling vendor/version = good practices.

**Q75. D) Display false banners** — Countermeasure against banner grabbing. *Others:* disable DNS zone transfers (DNS enum), disable open relay (SMTP enum), RestrictNullSessAccess (SMB enum) = enumeration countermeasures, not banner grabbing.

**Q76. A) Ensure that TCP wrappers limit access to the network based on domain names or IP addresses** — Port scanning countermeasure. *Others:* never using scan tools, never configuring IDS, never using custom rules = bad practices.

**Q77. C) Avoid configuring routers to verify the data packets using their signatures** — Question asks the BAD practice. Routers SHOULD verify packets via signatures (digests). *Others:* IPv6 migration, secure VPN, digital certificates = valid anti-spoofing countermeasures.

---

## SECTION 6 — OS FINGERPRINTING & IDS/FIREWALL EVASION

**Q78. A) OS discovery using Unicornscan** — Identifies OS by observing TTL values in scan results (`unicornscan <IP>`). *Others:* Nmap = -O option (not TTL); NSE = scripts; IPv6 fingerprinting = same function as IPv4.

**Q79. D) Active** — Active fingerprinting sends specially crafted packets and analyzes responses (vs passive = sniffing). *Others:* Distributive/Reflective = not valid terms here.

**Q80. D) Anonymizers** — Bypass Internet censors and evade certain IDS/firewall rules. *Others:* decoy = fake IPs; bad checksums = invalid checksums; source port manipulation = common ports.

**Q81. B) Proxy chaining** — More proxies = more anonymity. *Others:* source port manipulation = evasion; decoy = fake IPs; source routing = specified path.

**Q82. D) nmap -sT -Pn –spoof-mac 0 [Target IP]** — `--spoof-mac 0` = auto-generate random MAC. *Others:* `--spoof-mac [MAC]` = manual MAC; -sU -v = UDP scan; cewl = words from URL.

**Q83. C) Banner grabbing** — OS fingerprinting to detect vulnerabilities. *Others:* port scanning = services; decoy/source routing = evasion.

**Q84. C) TCP sequence ability test** — ACTIVE banner grabbing technique. *Others:* error messages, sniffing, page extensions = PASSIVE techniques.

**Q85. A) Timing options to slow the speed that the port scan is conducted** — Evades threshold-based IDS/IPS (--delay, --rate). *Others:* fingerprinting, ping sweep, traceroute = not evasion.

---

## SECTION 7 — ENUMERATION & PORTS

**Q86. A) Brute-force Active Directory** — Design error in AD: with "logon hours" enabled, authentication attempts produce different error messages → info leak. *Others:* SNMP = community strings; email IDs = username before @; default passwords = manufacturer defaults.

**Q87. B) BGP** — Port 179/TCP, sessions between routers. *Others:* SIP = VoIP; LDAP = 389; SNMP = 161.

**Q88. C) TCP 139** — NetBIOS Session Service: null-session + file/printer sharing. *Others:* 53 = DNS; 23 = Telnet; 389 = LDAP.

**Q89. A) UDP 137** — NetBIOS name resolution / WINS. *Others:* 135 = RPC; 161 = SNMP; 22 = SSH.

**Q90. D) BGP** — ISPs use BGP for huge routing tables. *Others:* TFTP = 69; FTP = 21; SIP = VoIP.

**Q91. C) Network resources, network shares, and machine names** — Collected by enumeration. *Others:* OS/web servers/users/passwords = footprinting; email IP/geolocation = email tracking; open ports/services = scanning.

**Q92. B) TCP/UDP 53** — DNS vulnerabilities. *Others:* 139 = NetBIOS; 135 = RPC; 137 = NetBIOS-NS.

**Q93. B) LDAP** — Port 389 (TCP/UDP). *Others:* SNMP = 161; SMTP = 25; SIP = 5060.

**Q94. D) TCP** — Reliable, connection-oriented multiprocess communication. *Others:* UDP = unreliable; SNMP/SMTP = applications.

**Q95. C) NetBIOS** — Port 139 identifies accessible resources. *Others:* SNMP = 161; LDAP = 389; SMTP = 25.

**Q96. C) Port 500** — ISAKMP/IKE default port. *Others:* 50 = ESP; 4500 = NAT-T; 51 = AH.

**Q97. B) Telnet** — Port 23. *Others:* SSH = 22; FTP = 21; BGP = 179.

---

## SECTION 8 — LDAP ENUMERATION

**Q98. B) AD Explorer** — Access directory listings within Active Directory / directory services. *Others:* HULK, Slowloris, XOIC = DoS tools.

**Q99. D) LDAP** — Access distributed directories: valid usernames, addresses, departmental details. *Others:* SMTP = mail; NTP = time; DNS = name resolution.

**Q100. A) AD Explorer** — LDAP enumeration tool. *Others:* SuperScan, Nsauditor, SoftPerfect = port/network scanners, not LDAP.

**Q101. C) Retrieved all directory objects** — `(&(objectClass=*))` + scope SUBTREE + attributes='*' returns all directory objects. *Others:* listing apps = different filter; DSE naming contexts = RootDSE; connection object = created before search.

**Q102. C) Ladpsearch (ldapsearch)** — Enumerates AD users with specific filters. *Others:* PortQry = port queries; DNSRecon = DNS; netstat = network connections.

**Q103. D) AD Explorer** — LDAP enumeration. *Others:* Euromonitor = market research; nbtstat = NetBIOS; DNSRecon = DNS.

---

## QUICK REVIEW — COMMON TRAPS (CEH)

| Confusion | Correct answer |
|---|---|
| Egress vs Ingress filtering | Egress = OUTGOING; Ingress = INCOMING |
| searchfy vs usufy vs mailfy | searchfy = query on OSRFramework platforms |
| -sY vs -sZ | -sY = SCTP INIT; **-sZ = SCTP COOKIE ECHO** |
| Network scanning vs Port scanning | Port scanning = "sending messages to break in" |
| Active vs Passive banner grabbing | Active = TCP sequence ability test; Passive = error messages/sniffing |
| Photon vs Wayback | Photon = tool to retrieve archived URLs from archive.org |
| -Pn vs -P0 | -Pn/-PN = skip host discovery; -P0 = IP protocol ping |
| Random vs manual MAC | `--spoof-mac 0` = random; `--spoof-mac XX:XX` = manual |
| Enumerated info vs scanned info | Enumeration = resources/shares/machine names; Scanning = open ports/services |

*Good luck on the exam!*
