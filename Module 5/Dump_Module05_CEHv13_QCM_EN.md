# CEH v13 Dump — Module 05 : Vulnerability Analysis
## Exam-Style Practice Questions (312-50) — With Answer Key

> 60 multiple-choice questions based on Module 05 content. Answer key at the end.

---

## Questions

### Part A — Vulnerability Assessment Concepts (Q1–Q15)

**Q1.** Which of the following is NOT a category of vulnerability classification mentioned in Module 05?
- A) Misconfigurations / Weak configurations
- B) Application flaws
- C) Third-party risks
- D) Physical denial-of-service flaws

**Q2.** Insecure protocols transmit information **without encryption**, which leads to:
- A) Authentication and integrity issues
- B) Faster network performance
- C) Reduced bandwidth consumption
- D) Improved firewall security

**Q3.** A **buffer overflow** occurs when:
- A) An arithmetic function generates a value larger than the allocated memory space can store
- B) Content is written beyond the allocated size of the buffer
- C) A program fails to erase an assigned block of memory when no longer required
- D) A system depends on the timing of sequential process execution

**Q4.** Which tool, compatible with Unix/Linux, is used to **track memory leaks** and display the status of the software environment?
- A) Wireshark
- B) Nmap
- C) Valgrind
- D) Metasploit

**Q5.** The **Time of Check / Time of Use (TOC/TOU)** is a type of:
- A) Buffer overflow
- B) Race condition
- C) Memory leak
- D) Integer overflow

**Q6.** **Fail-open** is a security issue caused by:
- A) Improper input handling
- B) Improper error handling
- C) Code signing weakness
- D) Weak encryption

**Q7.** To protect private keys used during **code signing**, security professionals should store them in:
- A) Web servers
- B) Hardware Security Modules (HSMs)
- C) Plain text files
- D) Public repositories

**Q8.** Which of the following is an example of **poor patch management**?
- A) Using weak encryption algorithms
- B) Unpatched servers and unpatched firmware
- C) Open permissions
- D) Incorrect validation of data

**Q9.** Vulnerabilities due to **incorrect encryption or poor validation of data** are classified as:
- A) Application flaws
- B) Network misconfigurations
- C) Design flaws
- D) Third-party risks

**Q10.** **Zero-day vulnerabilities** are:
- A) Unknown vulnerabilities in software/hardware that are exposed but not yet patched
- B) Vulnerabilities in legacy platforms only
- C) Vulnerabilities caused by default passwords
- D) Vulnerabilities documented in the CVE dictionary

**Q11.** **System sprawl** refers to:
- A) An increase in the number of system or server connections without proper documentation
- B) A software bug that causes memory leaks
- C) The use of default passwords on devices
- D) The transmission of data over insecure protocols

**Q12.** Which of the following is a **network misconfiguration** example?
- A) Open permissions
- B) Unsecured root accounts
- C) Insecure protocols and open ports
- D) DLL injection

**Q13.** **Null pointer dereference** refers to:
- A) Loading a DLL file without specifying the complete path
- B) A pointer that is not designated to any valid object or invalid memory location
- C) Writing content beyond the buffer size
- D) A race condition between system processes

**Q14.** **DLL injection** can be prevented by:
- A) Always invoking DLLs by specifying the full path of the file location
- B) Loading all DLLs from user input
- C) Storing private keys in HSMs
- D) Using default credentials

**Q15.** A **resource exhaustion** attack is similar to:
- A) A man-in-the-middle attack
- B) A Denial-of-Service (DoS) attack
- C) An SQL injection attack
- D) A social engineering attack

### Part B — Scoring Systems and Databases (Q16–Q28)

**Q16.** The **CVSS** (Common Vulnerability Scoring System) is:
- A) A dictionary of standardized identifiers for vulnerabilities
- B) An open framework for communicating the characteristics and impacts of IT vulnerabilities
- C) A U.S. government repository of vulnerability data
- D) A category system for software weaknesses

**Q17.** Which organization provides CVSS scores for almost all known vulnerabilities?
- A) MITRE
- B) FIRST.Org
- C) NIST
- D) US-CERT

**Q18.** According to CVSS ratings, a base score of **6.5** corresponds to which severity level?
- A) Low
- B) Medium
- C) High
- D) Critical

**Q19.** According to CVSS ratings, a **Critical** vulnerability has a base score in the range:
- A) 7.0 – 8.9
- B) 4.0 – 6.9
- C) 0.1 – 3.9
- D) 9.0 – 10.0

**Q20.** Which metric group of CVSS represents the **intrinsic characteristics of a vulnerability** that are constant over time and across user environments?
- A) Base metric
- B) Threat metric
- C) Environmental metric
- D) Supplemental metric

**Q21.** Which CVSS metric group includes **Exploit Maturity**?
- A) Base metric
- B) Threat metric
- C) Environmental metric
- D) Supplemental metric

**Q22.** **CVE** is best described as:
- A) A database of exploit code
- B) A publicly available list or dictionary of standardized identifiers for common software vulnerabilities
- C) A U.S. government repository that performs vulnerability testing
- D) A commercial vulnerability scanner

**Q23.** CVE IDs are assigned by:
- A) CVE Numbering Authorities (CNAs) from around the world
- B) EC-Council
- C) FIRST.Org
- D) The U.S. Department of Homeland Security

**Q24.** The **NVD** (National Vulnerability Database) uses which protocol for automation?
- A) SCAP (Security Content Automation Protocol)
- B) SNMP
- C) SMTP
- D) SSH

**Q25.** Which statement about the **NVD** is TRUE?
- A) It actively performs vulnerability testing
- B) It relies on vendors, third-party researchers, and vulnerability coordinators for information
- C) It only lists Microsoft vulnerabilities
- D) It is a commercial product

**Q26.** The **CWE** (Common Weakness Enumeration) is sponsored by which organization?
- A) The MITRE Corporation
- B) FIRST.Org
- C) Tenable
- D) Greenbone Networks

**Q27.** How many categories of weaknesses does CWE have?
- A) More than 100
- B) More than 300
- C) More than 600
- D) More than 1,000

**Q28.** Which of the following is NOT one of the four CVSS metric groups?
- A) Base metric
- B) Threat metric
- C) Attack metric
- D) Supplemental metric

### Part C — Vulnerability Management Life Cycle (Q29–Q38)

**Q29.** The vulnerability management life cycle is divided into which three main phases?
- A) Pre-Assessment, Assessment, Post-Assessment
- B) Discovery, Exploitation, Cleanup
- C) Scan, Patch, Verify
- D) Plan, Do, Check

**Q30.** **Identifying assets and creating a baseline** is a task performed in:
- A) The Pre-Assessment Phase
- B) The Vulnerability Assessment Phase
- C) The Post-Assessment Phase
- D) The Monitoring Phase

**Q31.** Which of the following is a step in the **vulnerability assessment phase**?
- A) Creating a priority list of recommendations
- B) Identifying false positives and false negatives
- C) Applying patches and fixes
- D) Capturing lessons learned

**Q32.** The **Post-Assessment Phase** is also known as:
- A) The Recommendation Phase
- B) The Baseline Phase
- C) The Discovery Phase
- D) The Exploitation Phase

**Q33.** **Risk assessment** in the post-assessment phase involves:
- A) Only creating an asset inventory
- B) Identifying, characterizing, and classifying risks along with techniques to control their impact
- C) Rescanning systems to verify fixes
- D) Monitoring IDS/IPS logs

**Q34.** Remediation is the process of:
- A) Scanning the network for open ports
- B) Applying fixes on vulnerable systems to mitigate or reduce the impact and severity of vulnerabilities
- C) Creating a baseline of approved software
- D) Performing OSINT information gathering

**Q35.** For effective remediation, the process should be **SMART**, which stands for:
- A) Specific, Measurable, Attainable, Relevant, Time-bound
- B) Simple, Managed, Automated, Reliable, Tested
- C) Secure, Monitored, Assessed, Remediated, Tracked
- D) Systematic, Manual, Active, Rapid, Timely

**Q36.** Which phase involves **rescanning the systems** to assess if the required remediation is complete?
- A) Risk Assessment
- B) Remediation
- C) Verification
- D) Monitoring

**Q37.** Which phase uses tools such as **IDS/IPS, SIEM, and firewalls** for incident monitoring?
- A) Monitoring
- B) Remediation
- C) Verification
- D) Risk Assessment

**Q38.** Vulnerability **prioritization** helps to:
- A) Evaluate and decide a solution for the consequence of the assets failing
- B) Increase the number of open ports
- C) Disable the firewall
- D) Remove all monitoring tools

### Part D — Vulnerability Scanning (Q39–Q48)

**Q39.** **Vulnerability scanning** involves analyzing:
- A) Passwords and user credentials
- B) Protocols, services, and configurations to discover vulnerabilities and design flaws
- C) Financial transactions only
- D) Social media profiles

**Q40.** Vulnerabilities are classified based on:
- A) Severity level and exploit range
- B) OS type and vendor only
- C) Port number and protocol
- D) Network speed and bandwidth

**Q41.** Which approach to vulnerability scanning involves **direct interaction** with the target network?
- A) Active scanning
- B) Passive scanning
- C) Inference-based scanning
- D) Tree-based scanning

**Q42.** Which approach identifies vulnerabilities by **observing the TCP connection setup and teardown**?
- A) Active scanning
- B) Passive scanning
- C) Credentialed scanning
- D) External scanning

**Q43.** Which of the following is a **limitation of vulnerability scanning**?
- A) It can detect zero-day threats
- B) It cannot detect zero-day threats because it relies on known vulnerabilities
- C) It measures the strength of security controls
- D) It always provides accurate business impact analysis

**Q44.** Which type of scanning **scans the network from a hacker's perspective** to discover exploits accessible to the outside world?
- A) Internal scanning
- B) External scanning
- C) Host-based scanning
- D) Distributed scanning

**Q45.** **Credentialed scanning** is a security testing method that:
- A) Logs into the target system using valid credentials for a more thorough scan
- B) Assesses systems without using valid credentials
- C) Only scans wireless networks
- D) Only scans mobile applications

**Q46.** **Non-credentialed scanning** simulates:
- A) An internal privileged user
- B) An external attacker without access to user accounts
- C) A physical security assessment
- D) A database administrator

**Q47.** **Distributed scanning** is used by organizations with:
- A) A single on-premises server
- B) Assets such as servers and clients at different locations
- C) Only cloud infrastructure
- D) No network infrastructure

**Q48.** Which type of scanning tests databases such as MySQL, MSSQL, Oracle, and PostgreSQL?
- A) Application scanning
- B) Database scanning
- C) Wireless network scanning
- D) Host-based scanning

### Part E — Vulnerability Assessment Tools (Q49–Q60)

**Q49.** Which type of vulnerability assessment solution is **installed in the organization's internal network**?
- A) Product-based solutions
- B) Service-based solutions
- C) Tree-based assessments
- D) Inference-based assessments

**Q50.** In an **inference-based assessment**:
- A) The auditor selects different strategies for each machine
- B) Scanning starts by building an inventory of the protocols found on the machine, then detects ports, services, and selects relevant tests
- C) The organization hires third-party consulting firms
- D) The solution is installed behind the firewall

**Q51.** What are the **three steps** in the working of vulnerability scanning solutions?
- A) Locating nodes → Service and OS discovery → Testing services and OS for known vulnerabilities
- B) Reconnaissance → Exploitation → Cleanup
- C) Scan → Patch → Verify
- D) Footprinting → Enumeration → Privilege escalation

**Q52.** Which tool is a web server assessment tool that examines a web server to discover **potential problems and security vulnerabilities**?
- A) Nessus
- B) Nikto
- C) GFI LanGuard
- D) Qualys

**Q53.** **Nessus Essentials** is a product of which company?
- A) Greenbone
- B) Tenable
- C) Rapid7
- D) Qualys

**Q54.** **OpenVAS** is part of which company's commercial vulnerability management solution?
- A) Tenable
- B) Greenbone Networks
- C) Rapid7
- D) NIST

**Q55.** The OpenVAS feed contains more than **50,000**:
- A) Network Vulnerability Tests (NVTs)
- B) CVE records
- C) Attack signatures
- D) Plugin rules

**Q56.** Which feature is associated with **GFI LanGuard**?
- A) Patch management for operating systems and third-party applications
- B) Fuzzing arbitrary input to system interfaces
- C) Subdomain guessing only
- D) IoT device scanning only

**Q57.** **Qualys Vulnerability Management (VM)** is best described as:
- A) An open-source framework of services and tools
- B) A cloud-based service providing immediate, global visibility into where IT systems might be vulnerable
- C) A web server scanner with over 6,700 dangerous file checks
- D) A local host-based scanner

**Q58.** Which of the following is an **AI-powered vulnerability assessment tool**?
- A) Nikto
- B) Equixly
- C) OpenVAS
- D) GFI LanGuard

**Q59.** According to the module, the command **`nmap -sV --script=vuln www.moviescope.com -oN output.txt`** is used to:
- A) Perform OS fingerprinting only
- B) Perform a vulnerability scan using the Nmap Script Engine and save results in output.txt
- C) Crack passwords on the target
- D) Perform a DNS zone transfer

**Q60.** Which two types of vulnerability assessment reports are described in Module 05?
- A) Security vulnerability report and security vulnerability summary
- B) Executive report and technical report
- C) CVE report and CVSS report
- D) Network report and application report

---

## Answer Key

### Part A
| Q | Answer | Explanation |
|---|---|---|
| 1 | **D** | Physical denial-of-service flaws are not listed. Module categories: misconfigurations, application flaws, poor patch management, design flaws, third-party risks |
| 2 | **A** | Insecure protocols cause authentication and integrity issues because attackers can tamper with unencrypted data in transit |
| 3 | **B** | Buffer overflow = writing content beyond the allocated buffer size (insufficient bounds checking). A = integer overflow; C = memory leak; D = race condition |
| 4 | **C** | Valgrind, compatible with Unix/Linux, tracks memory leaks and displays the software environment status |
| 5 | **B** | TOC/TOU is a timing vulnerability that occurs as a result of a race condition |
| 6 | **B** | Fail-open (granting access after a system failure) is caused by improper error handling |
| 7 | **B** | Secure storage of private keys in HSMs helps defend against misuse of code-signing private keys |
| 8 | **B** | Unpatched servers, firmware, OS, and applications are examples of poor patch management |
| 9 | **C** | Design flaws include incorrect encryption and poor validation of data |
| 10 | **A** | Zero-day vulnerabilities are unknown, exposed but not yet patched, exploited before being acknowledged |
| 11 | **A** | System sprawl = increased number of system/server connections without proper documentation |
| 12 | **C** | Network misconfigurations include insecure protocols, open ports, errors, and weak encryption |
| 13 | **B** | Null pointer = a pointer not designated to any valid object / invalid memory location |
| 14 | **A** | Programmers must never load untrusted DLLs and must invoke DLLs by specifying the full path |
| 15 | **B** | Resource exhaustion is similar to a DoS attack — it compromises or exhausts system resources |

### Part B
| Q | Answer | Explanation |
|---|---|---|
| 16 | **B** | CVSS is an open framework for communicating the characteristics and impacts of IT vulnerabilities |
| 17 | **B** | FIRST.Org provides CVSS scores for almost all known vulnerabilities |
| 18 | **B** | Medium = 4.0 – 6.9 (6.5 falls in this range) |
| 19 | **D** | Critical = 9.0 – 10.0; High = 7.0–8.9; Medium = 4.0–6.9; Low = 0.1–3.9 |
| 20 | **A** | Base metric represents intrinsic characteristics constant over time and across environments |
| 21 | **B** | Threat metric includes Exploit Maturity |
| 22 | **B** | CVE is a free-to-use list/dictionary of standardized identifiers (a dictionary, not a database) |
| 23 | **A** | CVE IDs are assigned by CVE Numbering Authorities (CNAs) from around the world |
| 24 | **A** | NVD uses the Security Content Automation Protocol (SCAP) |
| 25 | **B** | NVD does not actively perform vulnerability testing; it relies on vendors and researchers |
| 26 | **A** | CWE is sponsored by the MITRE Corporation (National Cybersecurity FFRDC) |
| 27 | **C** | CWE has over 600 categories of weaknesses |
| 28 | **C** | The four groups are Base, Threat, Environmental, and Supplemental |

### Part C
| Q | Answer | Explanation |
|---|---|---|
| 29 | **A** | Pre-Assessment, Vulnerability Assessment, and Post-Assessment phases |
| 30 | **A** | The pre-assessment phase involves identifying assets and creating a baseline |
| 31 | **B** | Identifying false positives and false negatives is a step of the assessment phase |
| 32 | **A** | The post-assessment phase is also called the recommendation phase |
| 33 | **B** | Risk assessment identifies, characterizes, and classifies risks and how to control their impact |
| 34 | **B** | Remediation applies fixes on vulnerable systems to mitigate or reduce impact/severity |
| 35 | **A** | SMART = Specific, Measurable, Attainable, Relevant, Time-bound |
| 36 | **C** | Verification rescan systems to check whether the applied fix is effective |
| 37 | **A** | Monitoring uses IDS/IPS, SIEM, and firewalls for incident monitoring |
| 38 | **A** | Prioritization helps evaluate consequences of asset failure, examine risk tolerance, organize prioritization methods |

### Part D
| Q | Answer | Explanation |
|---|---|---|
| 39 | **B** | Vulnerability scanning analyzes protocols, services, and configurations |
| 40 | **A** | Vulnerabilities are classified by severity level (low/medium/high) and exploit range (local/remote) |
| 41 | **A** | Active scanning interacts directly with the target network |
| 42 | **B** | Passive scanning observes TCP connection setup/teardown without direct interaction |
| 43 | **B** | Vulnerability scanning relies on known vulnerabilities → cannot detect zero-day threats |
| 44 | **B** | External scanning views the network from a hacker's perspective |
| 45 | **A** | Credentialed scanning logs in with valid credentials for a thorough scan |
| 46 | **B** | Non-credentialed scanning simulates an external attacker without credentials |
| 47 | **B** | Distributed scanning simultaneously scans assets located at different locations with synchronization |
| 48 | **B** | Database scanning tests MySQL, MSSQL, Oracle, PostgreSQL for misconfiguration/injection vulnerabilities |

### Part E
| Q | Answer | Explanation |
|---|---|---|
| 49 | **A** | Product-based solutions are installed in the organization's internal network |
| 50 | **B** | Inference-based assessment builds a protocol inventory, then detects ports/services, then runs relevant tests |
| 51 | **A** | Locating nodes → Service and OS discovery → Testing services and OS for known vulnerabilities |
| 52 | **B** | Nikto is the open-source web server scanner (cirt.net) |
| 53 | **B** | Nessus Essentials is a Tenable product |
| 54 | **B** | OpenVAS is part of Greenbone Networks' commercial solution |
| 55 | **A** | The OpenVAS feed has over 50,000 Network Vulnerability Tests (NVTs) |
| 56 | **A** | GFI LanGuard features patch management, VA, web reporting console, virtual environment support |
| 57 | **B** | Qualys VM is a cloud-based service for global visibility into vulnerable IT systems |
| 58 | **B** | Equixly is an AI-powered tool (API security); the others are traditional scanners |
| 59 | **B** | `-sV` + `--script=vuln` performs a vulnerability scan via NSE; `-oN` saves to output.txt |
| 60 | **A** | The two report types are security vulnerability report and security vulnerability summary |

---

## Indicative scoring
- **50–60 correct**: excellent — ready for the exam
- **40–49**: good — review the missed sections
- **30–39**: average — restudy the course, then retry
- **< 30**: re-read the complete Module 05 course document

---

*Dump generated from the content of CEH v13 Module 05 (Vulnerability Analysis). In case of OCR transcription errors, the official EC-Council PDF remains the reference.*
