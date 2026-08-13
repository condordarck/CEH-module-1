# CEH v13 Dump — Module 07 : Malware Threats
## Exam-Style Practice Questions (312-50) — With Answer Key

> 72 multiple-choice questions based on Module 07 content. Answer key at the end.

---

## Questions

### Part A — Malware & APT Concepts (Q1–Q10)

**Q1.** Which term describes software created to damage, disrupt, steal from, or gain unauthorized access to a system?
- A) Shareware
- B) Firmware
- C) Malware
- D) Adware

**Q2.** Which propagation vector involves infecting victims through malicious attachments and phishing links?
- A) Email
- B) P2P file sharing
- C) Removable media (autorun)
- D) Drive-by downloads

**Q3.** Potentially Unwanted Applications (PUAs) are best described as:
- A) Programs that self-replicate across the network
- B) Applications whose unwanted functionality the user is unaware of, often bundled with legitimate software
- C) Antivirus tools that display misleading warnings
- D) Legitimate open-source applications distributed under a free license

**Q4.** Adware is software that:
- A) Automatically displays advertisements (pop-ups, banners) without the user's consent
- B) Encrypts user files and demands a ransom
- C) Steals banking credentials through browser overlays
- D) Rootkits the kernel to hide its presence

**Q5.** In the APT acronym, the term "Advanced" refers to:
- A) The use of human intervention to coordinate the attack
- B) A long-lived external C&C infrastructure that continuously extracts data
- C) The use of sophisticated techniques that exploit vulnerabilities, often zero-day
- D) The number of systems compromised in the target network

**Q6.** In the APT acronym, the term "Persistent" refers to:
- A) The attacker's ability to quickly pivot between targets
- B) The use of public, commercial, or illegally acquired knowledge sources
- C) An external command-and-control (C&C) system that continuously extracts data and monitors the network
- D) The high-risk tolerance of the attacker

**Q7.** In the APT acronym, the term "Threat" refers to:
- A) Human intervention in the coordination of the attack
- B) The sophistication of the malware used
- C) The persistence mechanisms installed on the host
- D) The zero-day vulnerabilities leveraged during intrusion

**Q8.** Which is the **first** phase of the APT lifecycle?
- A) Initial Intrusion
- B) Persistence
- C) Preparation
- D) Expansion

**Q9.** In the APT lifecycle, targeted data is searched for and removed from the network during which phase?
- A) Expansion
- B) Search and Exfiltration
- C) Cleanup
- D) Initial Intrusion

**Q10.** An APT characteristic meaning the attack follows **several phases** to reach its objective is known as:
- A) Timeliness
- B) Multiphased
- C) Militant
- D) Persistent

### Part B — Trojan & Backdoor Concepts (Q11–Q22)

**Q11.** Which statement about a **Trojan horse** is **FALSE**?
- A) It disguises itself as legitimate software but performs malicious actions once executed
- B) It self-replicates and spreads on its own like a virus
- C) It can be embedded in games, animations, and email attachments
- D) It can act as a server listening on a port on the victim's machine

**Q12.** A Trojan **cannot run on its own** — it requires:
- A) An active network connection
- B) Administrator privileges at boot time
- C) A user action (e.g., executing a downloaded program)
- D) A reverse proxy configuration

**Q13.** A Remote Access Trojan (RAT) grants the attacker:
- A) Only the ability to log keystrokes
- B) Only the ability to capture screenshots
- C) Only the ability to steal browser cookies
- D) Total control of the victim's system (files, screen, camera, keylogging, command execution)

**Q14.** A **reverse connection** Trojan establishes:
- A) An outbound connection to the attacker, which bypasses firewalls that block inbound connections
- B) An inbound connection on the victim's high-numbered ports
- C) A direct connection to the victim's DNS server
- D) A persistent connection to the local database server

**Q15.** Reverse connection Trojans typically use which ports to evade firewall rules?
- A) 53 and 88
- B) 80 and 443
- C) 445 and 3389
- D) 20 and 21

**Q16.** The **NetBus** Trojan listens on which ports?
- A) 12345/12346
- B) 31337/31338
- C) 8080
- D) 666

**Q17.** **Back Orifice** and **Net Spy** use which Trojan port?
- A) 7000
- B) 7626
- C) 31337/31338/31339
- D) 8787

**Q18.** **TrickBot**, **Carbanak**, and **PlugX** communicate via which port?
- A) 80
- B) 443
- C) 53
- D) 110

**Q19.** The **Zeus** banking Trojan is known to use which port?
- A) 555
- B) 1001
- C) 666
- D) 8080

**Q20.** An **ICMP Trojan** carries its payload inside:
- A) HTTP GET and POST requests
- B) ICMP echo request/echo reply (ping) messages
- C) DNS TXT records
- D) SMTP email headers

**Q21.** An **HTTP RAT** evades detection by:
- A) Encrypting its payload with a self-modifying key
- B) Disguising its malicious traffic as legitimate web traffic over ports 80/443
- C) Hiding in the NTFS alternate data streams
- D) Spreading through removable media via autorun

**Q22.** A **backdoor** is best defined as:
- A) A worm that self-propagates across the network
- B) A legitimate remote administration utility provided by the OS
- C) A means of bypassing normal authentication to access a system remotely
- D) An adware bundle installed with free software

### Part C — Virus Concepts & Types (Q23–Q34)

**Q23.** Which statement about a **computer virus** is correct?
- A) It can launch itself and spread without any user action
- B) It is self-replicating code that attaches to a legitimate program/file and requires a trigger event
- C) It always writes its code to the master boot record
- D) It only targets email clients

**Q24.** During the **infection phase**, a virus:
- A) Loads into memory, locates an executable, and appends its malicious code to it
- B) Sends copies of itself to the victim's email contacts
- C) Replaces the MBR with a malicious boot loader
- D) Encrypts user documents and demands a ransom

**Q25.** The **attack phase** of a virus is triggered by:
- A) The first system reboot after infection
- B) An event such as a trigger condition or direct attack
- C) The antivirus signature update
- D) A user opening any file

**Q26.** What is the **correct order** of the virus lifecycle?
- A) Design → Launch → Replication → Detection → Incorporation
- B) Design → Replication → Launch → Detection → Incorporation
- C) Replication → Design → Launch → Incorporation → Detection
- D) Launch → Replication → Detection → Design → Incorporation

**Q27.** A **boot sector virus**:
- A) Infects the boot sector (MBR) and activates at system boot
- B) Attaches itself to executable files only
- C) Modifies the directory entry to point to the viral code
- D) Only spreads through document macros

**Q28.** A **polymorphic virus** evades detection by:
- A) Remaining entirely in memory without touching the disk
- B) Creating a companion file with a similar-looking name
- C) Changing its signature through a mutated decryption routine at each replication
- D) Encrypting its code with a fixed, hard-coded key

**Q29.** A **metamorphic virus**:
- A) Infects the boot sector and files at the same time
- B) Hides in the free space (cavities) of a file
- C) Uses macros in Office documents
- D) Rewrites its entire code so that no two copies are ever identical

**Q30.** A **macro virus** is a virus that:
- A) Corrupts the file allocation table (FAT)
- B) Contains its code in the macros of Office documents
- C) Targets the Windows registry startup keys
- D) Is transported inside ICMP ping packets

**Q31.** A **companion virus** works by:
- A) Creating a companion file whose name resembles a legitimate file
- B) Changing file extensions to hide itself
- C) Wrapping itself around the host code
- D) Adding its code at the end of the host file

**Q32.** A **logic bomb** activates when:
- A) The infected file is copied to a new drive
- B) The antivirus is uninstalled
- C) A specific date or event occurs
- D) The system connects to a C&C server

**Q33.** The **persistent** variant of a web scripting virus:
- A) Resides only in the browser's memory and disappears after closing
- B) Is stored in a permanent file on the server
- C) Only infects email attachments
- D) Modifies the DNS settings of the browser

**Q34.** A **TSR (Terminate and Stay Resident)** virus:
- A) Remains in memory after the host program finishes executing
- B) Executes only when the host is run, then exits and leaves no trace
- C) Overwrites the host file completely
- D) Protects itself against analysis (anti-debug, anti-disassembly)

### Part D — Ransomware & Worms (Q35–Q42)

**Q35.** Ransomware is malware that:
- A) Displays unsolicited advertisements
- B) Restricts access to the victim's files/folders and demands a ransom to release them
- C) Turns the victim's machine into a proxy for DDoS attacks
- D) Logs every keystroke made by the user

**Q36.** **WannaCry** and **Petya/NotPetya** propagate primarily through which protocol/port?
- A) RDP — port 3389
- B) HTTP — port 80
- C) SMB — port 445
- D) FTP — port 21

**Q37.** **GhostLocker 2.0** (GhostSec) encrypts files and appends which extension?
- A) `.ghost`
- B) `.lock`
- C) `.enc`
- D) `.pay`

**Q38.** GhostLocker 2.0 is best described as an example of:
- A) A fileless loader written in Python
- B) A rootkit that hides in the kernel
- C) An adware bundle distributed via Facebook ads
- D) A double-extortion ransomware-as-a-service (RaaS) written in Golang

**Q39.** Which tool is used to **build** ransomware?
- A) Trojan Horse Construction Kit
- B) Chaos Ransomware Builder
- C) JPS Virus Maker
- D) njRAT

**Q40.** A **computer worm** is malware that:
- A) Propagates automatically across the network without user intervention
- B) Requires a trigger event to activate its attack phase
- C) Attaches itself to an existing executable to survive
- D) Only spreads via email attachments

**Q41.** Which of the following is a well-known example of a **worm**?
- A) Coyote
- B) FakeGPT
- C) Stuxnet
- D) GhostLocker

**Q42.** The key difference between a worm and a virus is that:
- A) A virus consumes bandwidth, while a worm does not
- B) A worm self-propagates without user action, while a virus requires a trigger event
- C) A worm only targets boot sectors, while a virus targets files
- D) There is no difference — the terms are interchangeable

### Part E — Fileless Malware (Q43–Q48)

**Q43.** **Fileless malware** is characterized by:
- A) Residing in memory (RAM) and exploiting legitimate system tools such as PowerShell and WMI
- B) Always writing its payload to the disk before execution
- C) Replacing the master boot record with a malicious bootloader
- D) Requiring the user to install a fake antivirus

**Q44.** In Microsoft's fileless malware taxonomy, **Type 1 — No File Activity** means:
- A) Files are required, but the attack never executes from them
- B) No file is written to the disk (e.g., a backdoor in kernel memory or code in firmware)
- C) Files are used indirectly, but the presence remains fileless
- D) A macro document injects a payload in memory

**Q45.** **Type 2 — Indirect File Activity** in Microsoft's taxonomy refers to:
- A) An exploit packet that drops a file to disk
- B) A purely network-based exploit
- C) A PowerShell command injected into the WMI repository to configure periodic execution
- D) A firmware-level attack on the network card

**Q46.** **Type 3 — Required Files to Operate** describes:
- A) A document with a macro/Java/Flash/EXE that injects a payload into memory then maintains persistence without files
- B) Malicious packets that exploit a kernel vulnerability
- C) A rewrite of the boot record
- D) An attacker who only uses in-memory shellcode

**Q47.** The term **living-off-the-land** (LOL) refers to:
- A) Hiding malware in the NTFS alternate data streams
- B) Abusing legitimate system administration tools (PowerShell, WMIC, WMI, AppLocker)
- C) Using only USB firmware for persistence
- D) Stealing legitimate SSL certificates for C2

**Q48.** **PyLoose** is a fileless Python malware that:
- A) Targets cloud workloads for Monero cryptomining (XMRig), loading its payload in memory via `memfd_create`
- B) Encrypts local files and appends the `.ghost` extension
- C) Steals Facebook accounts through a malicious Chrome extension
- D) Acts as a banking Trojan using the Squirrel installer

### Part F — AI-based Malware (Q49–Q52)

**Q49.** AI-based malware uses machine learning, deep learning, and NLP to:
- A) Learn from its environment, adapt, and evade detection
- B) Only increase the speed of its encryption routine
- C) Replace the operating system kernel
- D) Automatically patch known vulnerabilities in the victim

**Q50.** What is the operating flow of an AI-based malware?
- A) Persistence → Escalation → Exfiltration
- B) Infiltration → Establishment → Execution of malicious objectives
- C) Reconnaissance → Scanning → Exploitation
- D) Preparation → Intrusion → Cleanup

**Q51.** Which is an **indicator** of AI-based malware?
- A) A fixed, unchanging file signature
- B) Dependence on a hard-coded C&C IP address
- C) The ability to dynamically generate polymorphic variants and adapt to defense responses
- D) A single-entry-point infection vector

**Q52.** **FakeGPT** (Guardio Labs, 2023) is a malvertising campaign that:
- A) Used a fake Windows update to drop a ransomware payload
- B) Spread via USB drives in corporate networks
- C) Turned victims' machines into Monero miners
- D) Abused a malicious Chrome extension and the Facebook Graph API to steal accounts and hijack advertising

### Part G — Static Malware Analysis (Q53–Q60)

**Q53.** **Static malware analysis** examines a binary:
- A) Without executing it — file structure, metadata, imports, strings, and signatures
- B) Inside a sandbox while observing runtime behavior
- C) On the production network to capture real traffic
- D) By attaching a debugger to the running process

**Q54.** Which of the following is used for **file fingerprinting** (computing MD5/SHA-1/SHA-256 hashes)?
- A) IDA Pro
- B) HashCalc
- C) Process Monitor
- D) Wireshark

**Q55.** **Detect It Easy (DIE)** is primarily used to:
- A) Monitor network connections of a running sample
- B) Extract VBA macros from Office documents
- C) Inspect the PE format and detect packing (e.g., UPX)
- D) Trace Win32 API calls in real time

**Q56.** **Dependency Walker** is used to:
- A) Display the hierarchical tree of DLLs imported by an executable
- B) Scan the file against multiple antivirus engines
- C) Compute the SHA-256 hash of a sample
- D) Extract readable strings from a binary

**Q57.** Which imported DLL represents the **modern Winsock** network API in a Windows executable?
- A) WSock32.dll
- B) Ws2_32.dll
- C) Wininet.dll
- D) user32.dll

**Q58.** From the oletools suite, which tool extracts the **VBA macro source code** and flags suspicious keywords such as AutoOpen and URLDownloadToFileA?
- A) olevba
- B) PDFiD
- C) Detect It Easy
- D) binwalk

**Q59.** Which tool analyzes PDF files for suspicious keywords and object types (e.g., JavaScript)?
- A) oledump
- B) PDFiD
- C) YARA
- D) ExifTool

**Q60.** A YARA rule consists of which four sections?
- A) `header`, `data`, `code`, `output`
- B) `name`, `info`, `pattern`, `action`
- C) `rule`, `tags`, `match`, `reject`
- D) `rule` header (name + tags), `meta:`, `strings:`, `condition:`

### Part H — Dynamic Malware Analysis (Q61–Q66)

**Q61.** Dynamic malware analysis comprises which two steps?
- A) System Baselining and Host Integrity Monitoring
- B) Signature scanning and heuristic analysis
- C) Disassembly and decompilation
- D) Packet capture and log analysis

**Q62.** Which GUI tool displays **all TCP and UDP endpoints** of the system in real time?
- A) CurrPorts only
- B) TCPView
- C) jv16 PowerTools
- D) Autoruns

**Q63.** The `netstat -o` option displays:
- A) Ethernet statistics
- B) The routing table
- C) The process ID (PID) associated with each connection
- D) The DNS servers in use

**Q64.** **Process Monitor** is a fusion of which two legacy tools?
- A) Filemon and Regmon
- B) Filemon and Tcpmon
- C) Regmon and Apimon
- D) Filemon and Netmon

**Q65.** Which virus detection method executes the suspicious code inside a virtual machine and is highly effective against **encrypted and polymorphic** viruses?
- A) Scanning
- B) Code Emulation
- C) Integrity Checking
- D) Interception

**Q66.** **Heuristic analysis** detects unknown virus variants but suffers from which drawback?
- A) It only works offline
- B) It cannot detect encrypted viruses
- C) False positives
- D) It requires a dedicated hardware appliance

### Part I — Countermeasures & Anti-Malware Tools (Q67–Q72)

**Q67.** Which memory protection mechanisms should be enabled to harden systems against malware exploitation?
- A) DEP and ASLR
- B) AMSI and UAC
- C) SMTP and POP3
- D) TLS and SSH

**Q68.** To counter **fileless malware**, an organization should:
- A) Disable NTFS and enable FAT32 on all endpoints
- B) Restrict or disable PowerShell and WMI when unused, and use application whitelisting such as AppLocker
- C) Open all inbound ports on the host firewall
- D) Rely exclusively on signature-based antivirus scanning

**Q69.** The **AMSI** (Antimalware Scan Interface) is used by:
- A) Microsoft Defender for Endpoint to detect script-based (in-memory) attacks
- B) Wireshark to capture malicious packets
- C) YARA to compile detection rules
- D) netstat to log open ports

**Q70.** The **Malware.AI** detection solution works by:
- A) Comparing file hashes against a known-good database
- B) Monitoring DNS queries for malicious domains
- C) Tracing Win32 API calls during execution
- D) Converting files into images analyzed by deep learning (signature-less detection)

**Q71.** An **XDR** (Extended Detection and Response) solution:
- A) Only protects endpoints, like classic antivirus
- B) Extends EDR to additional layers (network, email, cloud)
- C) Replaces the need for a SIEM entirely
- D) Only analyzes PDF and Office documents

**Q72.** Regarding antivirus detection methods:
- A) Generic detection matches known signatures, while specific detection looks for virus-like behavior
- B) Both generic and specific detection rely exclusively on signature databases
- C) Generic detection looks for virus-like behavior and may produce false positives, while specific detection matches known signatures
- D) Specific detection is immune to zero-day threats

---

## Answer Key

### Part A
| Q | Answer | Explanation |
|---|---|---|
| 1 | **C** | Malware = malicious software created to damage/disrupt/steal or gain unauthorized access |
| 2 | **A** | Email is a propagation vector (infected attachments, malicious links, phishing) |
| 3 | **B** | PUAs are bundled apps whose unwanted functionality the user is unaware of |
| 4 | **A** | Adware automatically displays ads without consent and collects browsing data |
| 5 | **C** | "Advanced" = sophisticated techniques exploiting vulnerabilities (often zero-day) |
| 6 | **C** | "Persistent" = external C&C continuously extracting data and monitoring the network |
| 7 | **A** | "Threat" = human intervention in the coordination of the attack |
| 8 | **C** | APT lifecycle begins with Preparation (define target, organize team, build tools) |
| 9 | **B** | Data is searched and exfiltrated during Search and Exfiltration |
| 10 | **B** | Multiphased = the attack follows several phases to reach its objective |

### Part B
| Q | Answer | Explanation |
|---|---|---|
| 11 | **B** | Trojans do NOT self-replicate; they require a user action to execute |
| 12 | **C** | A Trojan cannot run alone; it demands a user action (executing a program, opening a file) |
| 13 | **D** | RATs grant total control (files, screen, camera, keylogging, command execution) |
| 14 | **A** | Reverse connections are outbound to the attacker, bypassing inbound-blocking firewalls |
| 15 | **B** | Reverse connections commonly use ports 80/443 (web traffic) |
| 16 | **A** | NetBus listens on 12345/12346 |
| 17 | **C** | Net Spy and Back Orifice use 31337/31338/31339 |
| 18 | **B** | Carbanak, PlugX, TrickBot, Lazarus use port 443 |
| 19 | **D** | Zeus uses port 8080 |
| 20 | **B** | ICMP Trojans tunnel payloads in echo request/reply (ping) messages |
| 21 | **B** | HTTP RATs hide malicious traffic as legitimate web traffic on 80/443 |
| 22 | **C** | A backdoor bypasses normal authentication for remote access |

### Part C
| Q | Answer | Explanation |
|---|---|---|
| 23 | **B** | A virus is self-replicating, attaches to a host, and needs a trigger event |
| 24 | **A** | Infection phase: load in memory, find executable, append malicious code |
| 25 | **B** | The attack phase is triggered by an event (trigger/direct attack) |
| 26 | **B** | Design → Replication → Launch → Detection → Incorporation |
| 27 | **A** | Boot sector viruses infect the MBR and activate at boot |
| 28 | **C** | Polymorphic viruses mutate the decryptor to change their signature |
| 29 | **D** | Metamorphic viruses rewrite their code so no two copies are identical |
| 30 | **B** | Macro viruses live in Office document macros |
| 31 | **A** | Companion viruses create a companion file with a similar name |
| 32 | **C** | Logic bombs trigger at a specific date or event |
| 33 | **B** | Persistent web scripting viruses are stored in a permanent file on the server |
| 34 | **A** | TSR viruses remain in memory after the host finishes executing |

### Part D
| Q | Answer | Explanation |
|---|---|---|
| 35 | **B** | Ransomware restricts access and demands a ransom |
| 36 | **C** | WannaCry/Petya/NotPetya propagate via SMB port 445 (EternalBlue) |
| 37 | **A** | GhostLocker 2.0 encrypts files and adds the `.ghost` extension |
| 38 | **D** | GhostLocker 2.0 is a Golang RaaS with double extortion (GhostSec) |
| 39 | **B** | Chaos Ransomware Builder is used to construct ransomware |
| 40 | **A** | Worms self-propagate across the network without user intervention |
| 41 | **C** | Stuxnet is a well-known worm example |
| 42 | **B** | Worms spread alone; viruses need a trigger event |

### Part E
| Q | Answer | Explanation |
|---|---|---|
| 43 | **A** | Fileless malware resides in memory and abuses legitimate tools (PowerShell/WMI) |
| 44 | **B** | Type 1 = no file written to disk (kernel-memory backdoor, firmware code) |
| 45 | **C** | Type 2 = indirect file activity (e.g., PowerShell injected into the WMI repository) |
| 46 | **A** | Type 3 = files needed but the attack runs from memory (macro/Java/Flash/EXE) |
| 47 | **B** | Living-off-the-land = abusing legitimate admin tools (PowerShell, WMIC, WMI) |
| 48 | **A** | PyLoose: cloud workloads, Monero (XMRig), payload loaded via `memfd_create` |

### Part F
| Q | Answer | Explanation |
|---|---|---|
| 49 | **A** | AI malware learns, adapts, and evades detection via ML/DL/NLP |
| 50 | **B** | Flow: Infiltration → Establishment → Execution |
| 51 | **C** | Dynamic polymorphism and adaptability to defenses are AI-malware indicators |
| 52 | **D** | FakeGPT abused a Chrome extension + Facebook Graph API (malvertising) |

### Part G
| Q | Answer | Explanation |
|---|---|---|
| 53 | **A** | Static analysis inspects the binary without executing it |
| 54 | **B** | HashCalc (and md5sum/sha1sum) compute file hashes for fingerprinting |
| 55 | **C** | DIE inspects the PE format and detects packing (UPX) |
| 56 | **A** | Dependency Walker shows the DLL import tree |
| 57 | **B** | Ws2_32.dll is the modern Winsock API; WSock32.dll is the legacy API |
| 58 | **A** | olevba extracts and analyzes VBA macro source |
| 59 | **B** | PDFiD scans PDFs for suspicious keywords/object types (JavaScript) |
| 60 | **D** | YARA: `rule` (name+tags), `meta:`, `strings:`, `condition:` |

### Part H
| Q | Answer | Explanation |
|---|---|---|
| 61 | **A** | Dynamic analysis = System Baselining + Host Integrity Monitoring |
| 62 | **B** | TCPView shows all TCP/UDP endpoints in real time |
| 63 | **C** | `netstat -o` shows the PID of each connection |
| 64 | **A** | Process Monitor = Filemon + Regmon |
| 65 | **B** | Code emulation defeats encrypted and polymorphic viruses |
| 66 | **C** | Heuristic analysis detects unknowns but produces false positives |

### Part I
| Q | Answer | Explanation |
|---|---|---|
| 67 | **A** | DEP and ASLR are recommended memory protections |
| 68 | **B** | Restrict PowerShell/WMI and use whitelisting/AppLocker against fileless malware |
| 69 | **A** | Defender for Endpoint uses AMSI for script-based attacks |
| 70 | **D** | Malware.AI converts files into images analyzed by deep learning |
| 71 | **B** | XDR extends EDR to network, email, and cloud layers |
| 72 | **C** | Generic = virus-like behavior (false positives); specific = known signatures |

---

## Indicative scoring
- **60–72 correct**: excellent — ready for the exam
- **48–59**: good — review the missed sections
- **36–47**: average — restudy the course, then retry
- **< 36**: re-read the complete Module 07 course document

---

*Dump generated from the content of CEH v13 Module 07 (Malware Threats). In case of OCR transcription errors, the official EC-Council PDF remains the reference.*
