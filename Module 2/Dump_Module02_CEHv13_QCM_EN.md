# CEH v13 Dump — Module 02 : Footprinting and Reconnaissance
## Exam-Style Practice Questions (312-50) — With Answer Key

> 60 multiple-choice questions based on Module 02 content. Answer key at the end (page 8).

---

## Questions

### Part A — Footprinting Concepts (Q1–Q14)

**Q1.** In the CEH methodology, **footprinting and reconnaissance** is best defined as:
- A) The phase where the attacker actively exploits system vulnerabilities
- B) The first/preparatory phase during which the attacker gathers as much information as possible about the target before launching an attack
- C) The final phase where the attacker erases all traces of the attack
- D) The phase where the attacker installs backdoors for persistent access

**Q2.** Which statement best describes **passive footprinting**?
- A) It involves direct interaction with the target and can be detected
- B) It collects information without direct interaction, so the target is unaware of the collection
- C) It requires scanning every port of the target network
- D) It is only performed after an active scan

**Q3.** Which of the following is an **active footprinting** activity?
- A) Social networking sites
- B) DNS interrogation
- C) archive.org
- D) Whois lookup

**Q4.** **OSINT** stands for:
- A) Open Source Information Networks and Tools
- B) Open-Source Intelligence
- C) Online Security Intelligence Techniques
- D) Off-Site Intelligence

**Q5.** Which of the following belongs to the **organizational information** gathered by footprinting?
- A) Details of employees (names, contact addresses, job functions)
- B) IP addresses of reachable systems
- C) NetBlocks of the target
- D) DNS records

**Q6.** Which information category includes **domains, sub-domains, NetBlocks, and network topology**?
- A) System information
- B) Organizational information
- C) Network information
- D) Personal information

**Q7.** The **operating systems of the web servers** of the target are part of:
- A) Network information
- B) Organizational information
- C) System information
- D) Financial information

**Q8.** The threat of **competitive espionage** refers to:
- A) Employees leaking passwords through social engineering
- B) Competitors gathering sensitive data to launch similar products, alter prices, and weaken the target's position
- C) Loss of privacy due to privilege escalation
- D) Attackers selling stolen data for profit

**Q9.** A detailed footprint provides a:
- A) Blueprint of the organization's security profile
- B) Complete list of the organization's customers
- C) Backup of the target's databases
- D) List of all employees' salaries

**Q10.** Passive footprinting is **technically difficult** because:
- A) It requires physical access to the target premises
- B) No active traffic is sent toward the target, so only archived and stored information is collected
- C) The target blocks all search engines
- D) It requires expensive commercial tools

**Q11.** Which of the following is a **passive footprinting** technique?
- A) DNS interrogation
- B) Traceroute
- C) Social networking sites
- D) Email tracking

**Q12.** Which threat is enabled when hackers collect information through **persuasion** from willing employees, without any technical intrusion?
- A) Information leakage
- B) Social engineering
- C) Loss of privacy
- D) Competitive espionage

**Q13.** According to the footprinting methodology, which sequence correctly describes the passive footprinting phases?
- A) Footprinting via search engines → internet research services → social networking sites
- B) DNS interrogation → traceroute → email tracking
- C) Whois lookup → network scanning → port scanning
- D) Social engineering → eavesdropping → shoulder surfing

**Q14.** Which tool is commonly used to **automate footprinting tasks**?
- A) NetScanTools Pro
- B) Maltego
- C) eMailTrackerPro
- D) PingPlotter

---

### Part B — Search Engines and Internet Research Services (Q15–Q27)

**Q15.** Which Google search operator returns pages containing **all the specified terms in the URL**?
- A) `inurl:`
- B) `allinurl:`
- C) `intitle:`
- D) `intext:`

**Q16.** The operator `site:` is used to:
- A) Restrict results to a specific site or domain
- B) Show the cached version of a page
- C) Search for a specific file type
- D) Find related sites

**Q17.** Which operator searches for a term within the **body** of a web page?
- A) `intitle:`
- B) `inanchor:`
- C) `intext:`
- D) `info:`

**Q18.** According to Google's documentation, which operator **cannot be combined** with a normal keyword search?
- A) `site:`
- B) `link:`
- C) `filetype:`
- D) `cache:`

**Q19.** The **Google Hacking Database (GHDB)** is a subset of:
- A) Shodan
- B) Exploit-DB
- C) Censys
- D) theHarvester

**Q20.** **SearchSploit** is particularly useful when:
- A) The network is segmented or air-gapped (no Internet access)
- B) The target runs on Windows only
- C) Performing reverse image search
- D) Tracking email communications

**Q21.** **Shodan** is a search engine mainly used to:
- A) Index web pages for Google hacking
- B) Detect devices (including IoT) connected to the Internet and vulnerable networks
- C) Perform reverse image search
- D) Track social media mentions

**Q22.** Which of the following tools is used for **reverse image search**?
- A) TinEye
- B) Startpage
- C) NAPALM
- D) FileZilla

**Q23.** Which of the following are **FTP search engines**?
- A) Startpage, MetaGer, eTools.ch
- B) NAPALM FTP Indexer, FreewareWeb, Mamont
- C) BuzzSumo, Ubersuggest, Hashatit
- D) Spokeo, Intelius, pipl

**Q24.** **Meta search engines** such as Startpage and MetaGer:
- A) Maintain their own index of web pages
- B) Send the query to several third-party engines and mask the user's IP address
- C) Only search for FTP files
- D) Only index IoT devices

**Q25.** The **Tor Browser** helps an attacker on the dark web by:
- A) Encrypting the target's website database
- B) Acting as a VPN by default and bouncing the IP address through multiple servers
- C) Removing all traces from search engine caches
- D) Automatically cracking passwords

**Q26.** The **Internet Archive Wayback Machine (archive.org)** allows an attacker to:
- A) Retrieve information that has been deleted from the target's website
- B) Bypass the target's firewall
- C) Perform reverse DNS lookups
- D) Enumerate LinkedIn employees

**Q27.** Which tools can be used for **OS fingerprinting** (determining the target's operating system)?
- A) Netcraft, Shodan, Censys
- B) Spokeo, pipl, PeekYou
- C) Startpage, MetaGer, eTools.ch
- D) Maltego, FOCA, Recon-ng

---

### Part C — Social Networking Sites, Whois and DNS (Q28–Q42)

**Q28.** Footprinting through **social networking sites** differs from social engineering because the attacker:
- A) Tricks people into revealing information
- B) Gathers information that is already available on those sites
- C) Physically enters the target's premises
- D) Sends phishing emails to employees

**Q29.** Which tool is used to **enumerate employees of the target company on LinkedIn** along with their job titles?
- A) Sherlock
- B) theHarvester
- C) BuzzSumo
- D) Social Searcher

**Q30.** **Sherlock** is a tool used to:
- A) Track the most shared content across social networks
- B) Search a target username across a vast number of social networking sites
- C) Enumerate DNS records
- D) Analyze email headers

**Q31.** **BuzzSumo** allows an attacker to:
- A) Find the most shared content for a topic, author, or domain across major social networks
- B) Perform Whois lookups
- C) Track email delivery
- D) Scan network ports

**Q32.** The **Whois** protocol listens on which port?
- A) Port 53 (TCP)
- B) Port 43 (TCP)
- C) Port 25 (TCP)
- D) Port 80 (TCP)

**Q33.** Which Regional Internet Registry (RIR) covers **Europe**?
- A) ARIN
- B) APNIC
- C) RIPE NCC
- D) LACNIC

**Q34.** In the **Thin Whois (centralized) model**:
- A) All Whois information from all registrars is stored in one place
- B) Only the name of the Whois server of the registrar of a domain is stored
- C) Multiple independent entities manage the Whois database
- D) Whois information is encrypted

**Q35.** A **Whois lookup** returns information such as:
- A) NetRange, creation date, name servers, and registrar details
- B) The full source code of the target website
- C) The target's internal network topology
- D) The employees' passwords

**Q36.** **IP geolocation lookup** tools such as IP2Location reveal:
- A) The country, city, ISP, and timezone of an IP address
- B) The target's DNS zone transfer
- C) The target's browsing history
- D) The encryption keys of the target

**Q37.** Which DNS record points to a host's **IPv6 address**?
- A) A
- B) MX
- C) AAAA
- D) PTR

**Q38.** Which DNS record points to the domain's **mail server**?
- A) NS
- B) MX
- C) SOA
- D) CNAME

**Q39.** Which DNS record **maps an IP address to a hostname**?
- A) A
- B) HINFO
- C) PTR
- D) SRV

**Q40.** Which DNS record includes the **CPU type and operating system** of the host?
- A) RP
- B) HINFO
- C) TXT
- D) SOA

**Q41.** **SecurityTrails** is best described as:
- A) A DNS enumeration tool that creates a DNS map and enumerates current and historical DNS records and subdomains
- B) A social engineering framework
- C) An email tracking tool
- D) A Google hacking database

**Q42.** In Fierce, the option `--traverse 10` instructs the tool to:
- A) Perform 10 HTTP connections on discovered domains
- B) Search for contiguous blocks of IPs within a range of 10
- C) List 10 subdomains at a time
- D) Set the TTL to 10 hops

---

### Part D — Network and Email Footprinting, Social Engineering, Tools and Countermeasures (Q43–Q60)

**Q43.** According to the IANA, which block is reserved for **private internets**?
- A) 172.16.0.0 – 172.31.255.255
- B) 10.0.0.0 – 10.10.10.255
- C) 192.0.0.0 – 192.0.255.255
- D) 169.254.0.0 – 169.254.255.255

**Q44.** **Traceroute** works on the concept of the **ICMP protocol** and uses the:
- A) TTL (Time to Live) field in the header of ICMP packets
- B) Sequence number field of TCP packets
- C) Fragment offset field of IP packets
- D) Port number field of UDP packets

**Q45.** By default, **Windows** uses which traceroute utility?
- A) `traceroute`
- B) `tcptraceroute`
- C) `tracert`
- D) `pathping`

**Q46.** When ICMP traceroute messages are **blocked** by network devices, the attacker uses:
- A) UDP or TCP traceroute, also known as Layer 4 traceroute
- B) Reverse traceroute
- C) DNS traceroute
- D) SNMP traceroute

**Q47.** **PingPlotter** is a traceroute tool that allows the attacker to:
- A) Collect traceroute data and track latency and packet loss over time in readable graphs
- B) Enumerate email addresses
- C) Perform Whois lookups
- D) Create fake social media profiles

**Q48.** **Email tracking** allows an attacker to collect information such as:
- A) The recipient's IP address, geolocation, and operating system/browser details
- B) The recipient's bank account passwords
- C) The content of encrypted emails
- D) The target's DNS zone files

**Q49.** Which of the following can be found in an **email header**?
- A) The sender's IP address
- B) The recipient's current password
- C) The recipient's geolocation
- D) The sender's browser history

**Q50.** **eMailTrackerPro** is used to:
- A) Analyze email headers and extract the sender's geographical location and IP address
- B) Create fake email accounts
- C) Perform DNS enumeration
- D) Scan social networks for usernames

**Q51.** **Social engineering** is best defined as:
- A) The art of exploiting human behavior to extract confidential information
- B) The use of automated tools to scan ports
- C) The collection of information from public websites
- D) The process of encrypting confidential data

**Q52.** **Shoulder surfing** is a technique whereby the attacker:
- A) Intercepts any form of communication such as audio, video, or text
- B) Secretly observes the target to gain passwords, PINs, and credit card information
- C) Rummages through garbage bins for information
- D) Pretends to be a legitimate or authorized person

**Q53.** **Dumpster diving** involves:
- A) Collecting phone bills, contact information, and financial information from trash bins
- B) Observing keystrokes over the victim's shoulder
- C) Intercepting fax transmissions
- D) Creating fake profiles on social networks

**Q54.** **Impersonation** is a social engineering technique where the attacker:
- A) Pretends to be a legitimate or authorized person to mislead targets and trick them into revealing information
- B) Eavesdrops on telephone conversations
- C) Scans the target network for open ports
- D) Analyzes the target's email headers

**Q55.** In theHarvester, the option `-b` specifies:
- A) The number of results to retrieve
- B) The data source (e.g., linkedin, baidu)
- C) The target domain
- D) The output file format

**Q56.** **FOCA** (Fingerprinting Organizations with Collected Archives) is mainly used to:
- A) Find metadata and hidden information in scanned documents such as Office and PDF files
- B) Track the most shared content on social networks
- C) Perform Whois lookups
- D) Enumerate employees on LinkedIn

**Q57.** **Maltego** is an automated tool used to:
- A) Determine the relationships and real-world links between people, groups, organizations, websites, and Internet infrastructure
- B) Analyze email headers
- C) Perform shoulder surfing
- D) Bypass firewalls

**Q58.** **subfinder** is a tool that helps attackers:
- A) Discover valid subdomains for websites using passive online sources
- B) Create Google dorks
- C) Track email communications
- D) Perform IP geolocation

**Q59.** In the **OSINT Framework**, the indicator **(T)** means:
- A) The tool requires registration
- B) The link points to a tool that must be installed and run locally
- C) The entry is a Google dork
- D) The URL must be edited manually

**Q60.** Which of the following is an **effective footprinting countermeasure**?
- A) Setting apart internal and external DNS (split DNS) and restricting zone transfers to authorized servers
- B) Publishing business plans on the company website
- C) Allowing directory listings on web servers
- D) Keeping the geo-tagging feature enabled on cameras

---

## Answer Key

### Part A
| Q | Answer | Explanation |
|---|---|---|
| 1 | **B** | Footprinting = first/preparatory phase of gathering maximum info before an attack |
| 2 | **B** | Passive footprinting = no direct interaction; target unaware (OSINT, archived data) |
| 3 | **B** | DNS interrogation = active. Social networking sites, archive.org, Whois = passive |
| 4 | **B** | OSINT = Open-Source Intelligence |
| 5 | **A** | Organizational info: employees, phone numbers, branches, partners, history |
| 6 | **C** | Network info: domains, sub-domains, NetBlocks, topology, routers, IPs, Whois, DNS |
| 7 | **C** | System info: OS of web servers, server locations, emails, web technologies |
| 8 | **B** | Competitive espionage = competitors gather sensitive data to launch similar products |
| 9 | **A** | The footprint is a blueprint of the organization's security profile |
| 10 | **B** | No active traffic sent; only archived/stored information is collected |
| 11 | **C** | Social networking sites = passive (DNS interrogation, traceroute, email tracking = active) |
| 12 | **B** | Social engineering = collecting info via persuasion without technical intrusion |
| 13 | **A** | Passive phases: search engines → internet research services → social networking sites |
| 14 | **B** | Maltego, Recon-ng, FOCA, OSINT Framework are footprinting automation tools |

### Part B
| Q | Answer | Explanation |
|---|---|---|
| 15 | **B** | `allinurl:` = all terms in the URL (vs `inurl:` = any/one term) |
| 16 | **A** | `site:` restricts results to a site or domain |
| 17 | **C** | `intext:` searches the term in the body of the page |
| 18 | **B** | `link:` cannot be combined with a normal keyword search per Google's docs |
| 19 | **B** | GHDB is a subset of Exploit-DB |
| 20 | **A** | SearchSploit = local copy of Exploit-DB for offline/air-gapped use |
| 21 | **B** | Shodan detects Internet-connected devices (IoT) and vulnerable networks |
| 22 | **A** | TinEye = reverse image search tool |
| 23 | **B** | FTP search engines: NAPALM, FreewareWeb, Mamont, Globalfilesearch |
| 24 | **B** | Meta engines query several third-party engines and mask the user's IP |
| 25 | **B** | Tor acts as a default VPN and bounces the IP through multiple servers |
| 26 | **A** | archive.org retrieves deleted/archived versions of websites |
| 27 | **A** | OS fingerprinting tools: Netcraft, Shodan, Censys |

### Part C
| Q | Answer | Explanation |
|---|---|---|
| 28 | **B** | Social networking footprinting = gathering info available on the sites (not tricking people) |
| 29 | **B** | theHarvester enumerates LinkedIn employees + job titles |
| 30 | **B** | Sherlock searches a username across many social networking sites |
| 31 | **A** | BuzzSumo = most shared content for a topic/author/domain |
| 32 | **B** | Whois listens on port 43 (TCP) |
| 33 | **C** | RIPE NCC covers Europe |
| 34 | **B** | Thin Whois stores only the name of the registrar's Whois server |
| 35 | **A** | Whois returns NetRange, creation/expiry dates, name servers, registrar |
| 36 | **A** | IP geolocation: country, city, ISP, timezone, etc. |
| 37 | **C** | AAAA = host's IPv6 address (A = IPv4) |
| 38 | **B** | MX = mail server of the domain |
| 39 | **C** | PTR maps an IP address to a hostname (reverse DNS) |
| 40 | **B** | HINFO = CPU type and OS |
| 41 | **A** | SecurityTrails = DNS map, current + historical records, subdomains via brute-force |
| 42 | **B** | `--traverse 10` = search contiguous IP blocks within a range of 10 |

### Part D
| Q | Answer | Explanation |
|---|---|---|
| 43 | **A** | Private blocks: 10/8, 172.16/12 (172.16.0.0–172.31.255.255), 192.168/16 |
| 44 | **A** | Traceroute uses ICMP + the TTL field of the IP header |
| 45 | **C** | Windows uses `tracert` (ICMP); Linux `traceroute` (UDP) |
| 46 | **A** | TCP/UDP traceroute = Layer 4, used when ICMP is blocked |
| 47 | **A** | PingPlotter tracks latency and packet loss over time |
| 48 | **A** | Email tracking: recipient IP, geolocation, OS/browser, read time, device type |
| 49 | **A** | Email header contains the sender's IP address, dates, authentication system |
| 50 | **A** | eMailTrackerPro analyzes email headers (geo location, IP) |
| 51 | **A** | Social engineering = exploiting human behavior to extract confidential info |
| 52 | **B** | Shoulder surfing = secretly observing the target |
| 53 | **A** | Dumpster diving = rummaging trash bins for sensitive info |
| 54 | **A** | Impersonation = pretending to be a legitimate person to trick targets |
| 55 | **B** | `-b` = data source (linkedin, baidu, google, bing…); `-l` = results limit; `-d` = domain |
| 56 | **A** | FOCA finds metadata/hidden info in Office/PDF documents |
| 57 | **A** | Maltego determines relationships between people, organizations, websites, infrastructure |
| 58 | **A** | subfinder = passive subdomain discovery |
| 59 | **B** | (T) = tool to install and run locally; (D) = dork; (R) = registration; (M) = manual edit |
| 60 | **A** | Split DNS + restricted zone transfers is a footprinting countermeasure |

---

## Indicative scoring
- **50–60 correct**: excellent — ready for the exam
- **40–49**: good — review the missed sections
- **30–39**: average — restudy the course, then retry
- **< 30**: re-read the complete Module 02 course document

---

*Dump generated from the content of CEH v13 Module 02 (Footprinting and Reconnaissance). In case of OCR transcription errors, the official EC-Council PDF remains the reference.*
