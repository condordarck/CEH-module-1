# CEH v13 Dump — Module 03 : Scanning Networks
## Exam-Style Practice Questions (312-50) — With Answer Key

> 60 multiple-choice questions based on Module 03 content. Answer key at the end.

---

## Questions

### Part A — Network Scanning Concepts (Q1–Q14)

**Q1.** **Network scanning** is best defined as:
- A) The process of identifying live hosts, ports, and services in a network
- B) The process of directly exploiting open ports
- C) The process of cracking user passwords
- D) The process of installing backdoors on the target

**Q2.** Which type of scanning **lists the active hosts and IP addresses** of a network?
- A) Port scanning
- B) Network scanning
- C) Vulnerability scanning
- D) Banner grabbing

**Q3.** Which type of scanning shows the **presence of known weaknesses**?
- A) Port scanning
- B) Network scanning
- C) Vulnerability scanning
- D) Host discovery

**Q4.** Which of the following are the **six TCP control flags**?
- A) SYN, ACK, PSH, URG, FIN, RST
- B) SYN, ACK, PSH, SEQ, FIN, RST
- C) SYN, ACK, ECE, CWR, FIN, RST
- D) SYN, ACK, PSH, URG, FIN, CWR

**Q5.** According to the module, which TCP flag do **attackers use to scan hosts and identify open ports**?
- A) SYN
- B) RST
- C) URG
- D) PSH

**Q6.** The **three-way handshake** between a client and a server proceeds in which order?
- A) SYN → SYN+ACK → ACK
- B) SYN → ACK → SYN+ACK
- C) ACK → SYN → SYN+ACK
- D) SYN → RST → ACK

**Q7.** Which statement about the **TCP Connect (full-open) scan** (`-sT`) is TRUE?
- A) It requires super-user privileges
- B) It completes the three-way handshake and does NOT require super-user privileges
- C) It never completes the three-way handshake
- D) It only sends ICMP packets

**Q8.** The **PSH (Push)** flag:
- A) Notifies the emission of a new sequence number
- B) Orders the system to process data immediately
- C) Aborts the connection on error
- D) Announces that no more transmission will be sent

**Q9.** In the TCP header, each control flag has a size of:
- A) 1 byte
- B) 2 bits
- C) 1 bit
- D) 4 bits

**Q10.** Which TCP flag **announces the end of transmission** (no more data will be sent)?
- A) FIN
- B) SYN
- C) URG
- D) RST

**Q11.** The **SYN scanning** technique mainly involves which three flags?
- A) SYN, ACK, RST
- B) SYN, FIN, RST
- C) SYN, ACK, PSH
- D) FIN, URG, PSH

**Q12.** Which of the following is NOT a network scanning tool mentioned in the module?
- A) Nmap
- B) Hping3
- C) BitLocker
- D) NetScanTools Pro

**Q13.** In the network scanning process, the attacker:
- A) Sends TCP/IP probes, receives network information back, and creates a profile of the target organization
- B) Sends TCP/IP probes to directly exploit the target
- C) Only performs passive information gathering
- D) Skips the reconnaissance phase

**Q14.** Which statement about **open ports** is TRUE?
- A) A system with fewer open ports is always more secure than one with more open ports
- B) Ports are like doors and windows: the more open ports, the larger the attack surface, but fewer ports do not always mean higher security
- C) Open ports have no relation to system vulnerability
- D) Only UDP ports can be exploited

---

### Part B — Host Discovery (Q15–Q27)

**Q15.** What is the **first task** in the network scanning process?
- A) Port scanning
- B) Host discovery
- C) OS discovery
- D) Vulnerability scanning

**Q16.** Which Nmap host discovery technique is considered the **most efficient and accurate**?
- A) ARP ping scan (`-PR`)
- B) UDP ping scan (`-PU`)
- C) ICMP timestamp ping (`-PP`)
- D) IP protocol ping (`-PO`)

**Q17.** By default, the **UDP ping scan** (`-PU`) sends UDP packets to which port?
- A) 80
- B) 40125
- C) 53
- D) 443

**Q18.** The **ICMP ECHO ping scan** (`-PE`) sending echo requests to broadcast addresses does NOT work against:
- A) Linux machines
- B) UNIX machines
- C) Windows machines
- D) BSD machines

**Q19.** Which ICMP-based host discovery technique **obtains the current time** from the target and is effective when ICMP ECHO is blocked?
- A) ICMP timestamp ping (`-PP`)
- B) ICMP address mask ping (`-PM`)
- C) IP protocol ping (`-PO`)
- D) ARP ping scan

**Q20.** The **TCP SYN ping** (`-PS`) sends an empty TCP SYN packet to which default port and with which advantage?
- A) Port 53; it creates full connection logs
- B) Port 80; no connection is established, so no logs are created
- C) Port 443; it establishes full connections
- D) Port 25; it creates full connection logs

**Q21.** Why is the **TCP ACK ping** (`-PA`) effective at discovering hosts?
- A) Because it completes the three-way handshake
- B) Because firewalls usually block SYN packets while the ACK probe easily bypasses such rules
- C) Because it sends ICMP ECHO requests
- D) Because it uses the DNS protocol

**Q22.** By default, the **IP protocol ping** (`-PO`) probes which protocols?
- A) ICMP (1), IGMP (2), and IP-in-IP (4)
- B) TCP (6), UDP (17), and SCTP (132)
- C) ICMP (1), UDP (17), and TCP (6)
- D) ARP only

**Q23.** In Nmap, which option **disables port scanning** (ping scan only)?
- A) `-sS`
- B) `-sn`
- C) `-sU`
- D) `-sL`

**Q24.** Why would an attacker use **`--disable-arp-ping`**?
- A) To enable the ARP ping scan
- B) To disable Nmap's default ARP ping scan and perform other ping scans
- C) To disable ICMP
- D) To randomize the host order

**Q25.** An ICMP ECHO ping sweep packet contains:
- A) 64 bytes (56 bytes of data + 8 bytes of protocol header)
- B) 32 bytes total
- C) 128 bytes (56 bytes of data + 72 bytes of header)
- D) 512 bytes

**Q26.** **Angry IP Scanner** is a ping sweep tool that:
- A) Creates a separate scan thread for each IP address (multithreaded)
- B) Only scans UDP ports
- C) Only works on Windows Server
- D) Cannot record scan results

**Q27.** Which Hping3 command performs an **ICMP ping** (echo request)?
- A) `hping3 -1 10.0.0.25`
- B) `hping3 -A 10.0.0.25 -p 80`
- C) `hping3 -8 50-60 -S 10.0.0.25 -V`
- D) `hping3 -9 HTTP -I eth0`

---

### Part C — Port and Service Discovery (Q28–Q42)

**Q28.** The **TCP Connect (full-open) scan** (`-sT`):
- A) Completes the three-way handshake then sends an RST to close the connection
- B) Never completes the handshake
- C) Requires super-user privileges
- D) Cannot detect closed ports

**Q29.** The **stealth (half-open) scan** (`-sS`) works by:
- A) Sending an RST to the server before the three-way handshake completes
- B) Completing the full three-way handshake
- C) Sending UDP packets
- D) Using the zombie's IP address

**Q30.** In the **inverse TCP flag scan** (FIN/URG/PSH/NULL), an OPEN port responds with:
- A) RST
- B) RST/ACK
- C) No response
- D) SYN/ACK

**Q31.** The inverse TCP flag scan technique is only effective against which systems?
- A) Microsoft Windows
- B) UNIX-based operating systems (RFC 793-compliant BSD stack)
- C) Cisco routers
- D) Android devices

**Q32.** The **Xmas scan** (`-sX`) sends packets with which flags set?
- A) FIN, URG, PUSH
- B) SYN, ACK, FIN
- C) No flags (NULL)
- D) SYN only

**Q33.** The **NULL scan** (`-sN`) sends packets with:
- A) All flags set
- B) No flags set
- C) Only the FIN flag
- D) Only the ACK flag

**Q34.** The **Maimon scan** (`-sM`) uses which probe?
- A) FIN/ACK
- B) SYN
- C) URG/PSH/FIN
- D) UDP

**Q35.** In the **TTL-based ACK flag probe scan**, a port is considered OPEN when the TTL of the received RST packet is:
- A) Greater than 128
- B) Less than 64
- C) Equal to 255
- D) Exactly 128

**Q36.** In the **window-based ACK scan** (`-sW`), a port is considered OPEN when the window value is:
- A) Non-zero
- B) Zero
- C) Negative
- D) Always 65535

**Q37.** In the **idle (IPID header) scan** (`-sI`), the zombie's IPID must be incremented by how much to indicate an OPEN port on the target?
- A) 1
- B) 2
- C) 0
- D) 64

**Q38.** In the **UDP scan** (`-sU`), a port is considered CLOSED when:
- A) No response is received
- B) An ICMP port unreachable message is received
- C) An RST packet is received
- D) A SYN/ACK packet is received

**Q39.** The **SCTP INIT scan** (`-sY`) is based on which handshake?
- A) Three-way handshake
- B) Four-way handshake (INIT → INIT-ACK → COOKIE-ECHO → COOKIE-ACK)
- C) Two-way handshake
- D) No handshake

**Q40.** The **List scan** (`-sL`) is characterized by:
- A) Generating and printing a list of IPs/hostnames without actually scanning them (0 hosts up)
- B) Scanning all ports of the target
- C) Sending ICMP ECHO to all hosts
- D) Detecting the OS of hosts

**Q41.** **Service version discovery** (`-sV`) works by using:
- A) The `service-probes` database of Nmap
- B) The ARP cache
- C) The DNS zone file
- D) The TTL value only

**Q42.** Which statement about **IPv6 scanning** (`-6`) is TRUE?
- A) The IPv6 address space is 64 bits
- B) There are 2^64 possible addresses per subnet, making classic scanning infeasible
- C) IPv6 scanning uses the same address space as IPv4
- D) IPv6 addresses can be easily brute-forced

---

### Part D — OS Discovery, IDS/Firewall Evasion and Countermeasures (Q43–Q60)

**Q43.** **Active banner grabbing** (OS fingerprinting) is best described as:
- A) Sending specially designed packets to the remote OS and comparing the responses against a database to determine the OS
- B) Sniffing traffic to determine the OS
- C) Reading the target's log files
- D) Asking the administrator for OS details

**Q44.** A **TTL value of 128** in the first packet of a TCP session most likely indicates:
- A) Linux
- B) Windows
- C) Solaris
- D) Cisco router

**Q45.** A **TTL value of 255** most likely indicates:
- A) Windows
- B) Linux
- C) OpenBSD, Cisco routers, Solaris, or AIX
- D) FreeBSD always

**Q46.** Which OS is associated with a **TCP window size of 5840**?
- A) Windows
- B) Linux
- C) FreeBSD
- D) Solaris

**Q47.** In **passive fingerprinting**, a page extension of `.aspx` most likely indicates:
- A) An Apache server on Linux
- B) An IIS server on Windows
- C) An nginx server on FreeBSD
- D) A Tomcat server on Solaris

**Q48.** Nmap **OS detection** (`-O`) uses how many tests to determine the OS fingerprint?
- A) 5
- B) 9
- C) 18
- D) 12

**Q49.** Which Nmap Script Engine (NSE) script collects OS information from the target via the **SMB protocol**?
- A) `smb-os-discovery`
- B) `http-enum`
- C) `dns-zone-transfer`
- D) `ssh2-enum-algos`

**Q50.** **Packet fragmentation** as an IDS/firewall evasion technique (`-f`) works because:
- A) IDS/firewalls process fragments one by one and most are configured to skip fragmented packets during port scans
- B) Fragments are encrypted
- C) IDS cannot reassemble fragments
- D) Fragments use a different protocol

**Q51.** Which Nmap option lets the attacker set the source port to a **well-known port** (e.g., HTTP port 80) to bypass IDS/firewall rules?
- A) `-g 80`
- B) `-f`
- C) `-D RND:10`
- D) `--badsum`

**Q52.** The **IP address decoy** technique (`-D RND:10`) makes it appear that:
- A) The decoys and the real host are all scanning the network
- B) Only the real host is scanning
- C) The target is scanning the attacker
- D) No scanning is taking place

**Q53.** Why can an attacker NOT open a successful TCP connection using **IP address spoofing**?
- A) Because the three-way handshake cannot be completed (the SYN/ACK goes to the spoofed address)
- B) Because spoofed packets are always dropped
- C) Because TCP requires HTTPS
- D) Because the firewall blocks all spoofed traffic

**Q54.** In Nmap, **`--spoof-mac 0`**:
- A) Generates a completely random MAC address
- B) Uses the Dell vendor MAC address
- C) Uses the MAC address 00:01:02:25:56:AE
- D) Disables MAC spoofing

**Q55.** The **`--badsum`** option allows an attacker to:
- A) Send packets with invalid TCP/UDP checksums to evade certain firewall rules
- B) Create valid checksums for all packets
- C) Randomize the host order
- D) Fragment packets into smaller pieces

**Q56.** **Proxy chaining** provides greater anonymity because:
- A) Each proxy removes the user's identifying information before passing the request to the next proxy
- B) Proxies encrypt the final destination
- C) Proxies always use HTTPS
- D) The target cannot see any traffic

**Q57.** Which type of anonymizer transfers information through a **network of computers** connected to the Internet before passing it to the target website?
- A) Single-point anonymizer
- B) Networked anonymizer
- C) Proxy server
- D) NAT gateway

**Q58.** Which is an effective **countermeasure against ping sweep attacks**?
- A) Terminating the connection with any host sending more than 10 ICMP ECHO requests
- B) Allowing all ICMP ECHO traffic
- C) Disabling the IDS
- D) Using public IP addresses for internal devices

**Q59.** According to the module, which set of ports should be **filtered** to secure a network?
- A) 135-159, 256-258, 389, 445, 1080, 1745, 3268
- B) 80, 443, 53, 22
- C) 1-100 only
- D) 8000, 8080, 8888

**Q60.** To prevent the disclosure of the **server version** in the Apache banner, which directive should be set in `httpd.conf`?
- A) `ServerTokens Prod`
- B) `ServerTokens Full`
- C) `ServerSignature on`
- D) `RemoveServerHeader 1`

---

## Answer Key

### Part A
| Q | Answer | Explanation |
|---|---|---|
| 1 | **A** | Network scanning identifies live hosts, ports, and services in a network |
| 2 | **B** | Network scanning = listing active hosts and IP addresses |
| 3 | **C** | Vulnerability scanning reveals the presence of known weaknesses |
| 4 | **A** | The 6 TCP flags: SYN, ACK, PSH, URG, FIN, RST (1 bit each) |
| 5 | **B** | RST is set to 1 to abort a connection on error; attackers use it to scan hosts and identify open ports |
| 6 | **A** | SYN → SYN+ACK → ACK establishes a TCP session |
| 7 | **B** | TCP Connect scan completes the handshake and does NOT need super-user privileges; it is easily detectable |
| 8 | **B** | PSH orders the receiver to process data immediately |
| 9 | **C** | Each TCP control flag is 1 bit (TCP Flags section = 6 bits) |
| 10 | **A** | FIN announces that no more transmission will be sent (ends the connection) |
| 11 | **A** | SYN scanning mainly involves the SYN, ACK, and RST flags |
| 12 | **C** | BitLocker is Windows disk encryption, not a scanning tool (Nmap, Hping3, Metasploit, NetScanTools Pro are) |
| 13 | **A** | Attacker sends TCP/IP probes → network returns information → attacker creates a profile of the target |
| 14 | **B** | More open ports = more attack surface, but fewer ports do not always mean higher security |

### Part B
| Q | Answer | Explanation |
|---|---|---|
| 15 | **B** | Host discovery is the first task of the network scanning process |
| 16 | **A** | ARP ping scan (`-PR`) is the most efficient and accurate; it is Nmap's default on IPv4 local networks |
| 17 | **B** | UDP ping scan sends UDP packets to port 40125 by default |
| 18 | **C** | ICMP ECHO to broadcast addresses works on UNIX/Linux/BSD but NOT on Windows |
| 19 | **A** | ICMP timestamp ping (`-PP`) gets the current time and works when ECHO is blocked |
| 20 | **B** | TCP SYN ping uses port 80; no connection is established so no logs are created |
| 21 | **B** | Firewalls usually block SYN; the ACK probe bypasses such rules (target replies with RST) |
| 22 | **A** | IP protocol ping default probes ICMP (1), IGMP (2), and IP-in-IP (4) |
| 23 | **B** | `-sn` disables port scanning (ping scan only) |
| 24 | **B** | `--disable-arp-ping` turns off the default ARP ping scan to use other ping scans |
| 25 | **A** | A ping packet = 64 bytes (56 data + 8 protocol header) |
| 26 | **A** | Angry IP Scanner is multithreaded: one scan thread per IP address |
| 27 | **A** | `hping3 -1` = ICMP ping; `-A` = ACK scan; `-8` = scan mode; `-9` = listen mode |

### Part C
| Q | Answer | Explanation |
|---|---|---|
| 28 | **A** | TCP Connect completes the handshake (SYN→SYN+ACK→ACK) then sends RST to close |
| 29 | **A** | Stealth scan sends RST before the handshake completes (half-open connection) |
| 30 | **C** | In inverse flag scans an open port gives NO response; a closed port replies RST/ACK |
| 31 | **B** | Only RFC 793-compliant (UNIX/BSD) stacks respond correctly; Windows ignores RFC 793 |
| 32 | **A** | Xmas scan = FIN + URG + PUSH flags |
| 33 | **B** | NULL scan = no flags set |
| 34 | **A** | Maimon scan uses the FIN/ACK probe |
| 35 | **B** | TTL of the RST < 64 → port open; TTL ≥ 64 → closed |
| 36 | **A** | Non-zero window → open; zero window → closed |
| 37 | **B** | IPID increment of 2 → open port (the target sent a SYN/ACK to the zombie which answered RST); 1 → closed |
| 38 | **B** | ICMP port unreachable → closed; no response → open or filtered |
| 39 | **B** | SCTP uses a four-way handshake: INIT → INIT-ACK → COOKIE-ECHO → COOKIE-ACK |
| 40 | **A** | List scan only prints a list of targets without scanning (0 hosts up) |
| 41 | **A** | `-sV` uses the `service-probes` database of Nmap |
| 42 | **B** | IPv6 = 128 bits, 64-bit host space (2^64 addresses per subnet); classic scanning is infeasible |

### Part D
| Q | Answer | Explanation |
|---|---|---|
| 43 | **A** | Active banner grabbing sends designed packets and compares responses with a database |
| 44 | **B** | TTL 128 → Windows; TTL 64 → Linux/Unix; TTL 255 → OpenBSD/Cisco/Solaris/AIX |
| 45 | **C** | TTL 255 → OpenBSD, Cisco routers, Solaris, or AIX |
| 46 | **B** | Linux window size = 5840; FreeBSD = 65535; Solaris = 8760; OpenBSD/AIX = 16384 |
| 47 | **B** | `.aspx` extension → IIS server on Windows |
| 48 | **B** | Nmap OS detection uses 9 tests (SYN+ECN-Echo, NULL, URG+PSH+SYN+FIN, ACK, etc. + PU + TSeq) |
| 49 | **A** | `smb-os-discovery` collects OS info via SMB |
| 50 | **A** | IDS/firewalls process fragments one by one and often skip fragmented packets during port scans |
| 51 | **A** | `-g` / `--source-port` sets the source port (e.g., `-g 80`) |
| 52 | **A** | Decoys make it appear that many hosts (decoys + real IP) are scanning the target |
| 53 | **A** | Spoofed SYN → the SYN/ACK goes to the spoofed address, so the handshake cannot complete |
| 54 | **A** | `--spoof-mac 0` = random MAC; `[Vendor]` = vendor MAC; `[new MAC]` = manual MAC |
| 55 | **A** | `--badsum` sends invalid TCP/UDP checksums to evade firewall rules that skip checksum checks |
| 56 | **A** | Each proxy in the chain removes identifying info before forwarding the request |
| 57 | **B** | Networked anonymizers use a network of computers; single-point anonymizers use a single website |
| 58 | **A** | Terminating connections sending >10 ICMP ECHO requests is a ping sweep countermeasure |
| 59 | **A** | Filter ports: 135-159, 256-258, 389, 445, 1080, 1745, 3268 |
| 60 | **A** | `ServerTokens Prod` in Apache; IIS uses `RemoveServerHeader=1` in Urlscan.ini |

---

## Indicative scoring
- **50–60 correct**: excellent — ready for the exam
- **40–49**: good — review the missed sections
- **30–39**: average — restudy the course, then retry
- **< 30**: re-read the complete Module 03 course document

---

*Dump generated from the content of CEH v13 Module 03 (Scanning Networks). In case of OCR transcription errors, the official EC-Council PDF remains the reference.*
