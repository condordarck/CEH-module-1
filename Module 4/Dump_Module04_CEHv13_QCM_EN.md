# CEH v13 Dump — Module 04 : Enumeration
## Exam-Style Practice Questions (312-50) — With Answer Key

> 60 multiple-choice questions based on Module 04 content. Answer key at the end.

---

## Questions

### Part A — Enumeration Concepts & NetBIOS (Q1–Q14)

**Q1.** **Enumeration** is best defined as:
- A) The process of extracting user names, machine names, network resources, shares, and services from a system
- B) The process of passively gathering open-source information about a target
- C) The process of identifying open ports on a target network
- D) The process of exploiting a known vulnerability on the target

**Q2.** Enumeration techniques operate in which environment?
- A) The Internet (external network)
- B) An intranet environment
- C) A DMZ only
- D) Cloud environments only

**Q3.** Which of the following is an information that attackers **enumeration** extracts from a target?
- A) Routing tables and audit/service settings
- B) Credit card numbers
- C) Encryption keys of the OS
- D) BIOS passwords

**Q4.** Which statement about the **legality of enumeration** is TRUE?
- A) Enumeration is always legal
- B) Enumeration may be illegal depending on the organization's policies and applicable laws
- C) Enumeration is never monitored
- D) Enumeration only becomes illegal after exploitation

**Q5.** During enumeration, an attacker who stumbles on an **IPC$ share** typically:
- A) Ignores it as it is not exploitable
- B) Probes it to brute-force admin credentials and access the file system
- C) Uses it to reset the machine's clock
- D) Uses it to perform a zone transfer

**Q6.** A NetBIOS name is a unique ASCII string of **16 characters** where the **16th character** is reserved for:
- A) The domain name
- B) The service or name type
- C) The MAC address
- D) The operating system version

**Q7.** Which ports are used by NetBIOS?
- A) TCP 445 only
- B) UDP 137, UDP 138, and TCP 139
- C) UDP 161 and UDP 162
- D) TCP 389 and TCP 636

**Q8.** In the NetBIOS name code table, which code represents the **Server service** running on a host?
- A) `<hostname> <00>`
- B) `<hostname> <20>`
- C) `<hostname> <03>`
- D) `<domain> <1E>`

**Q9.** Which NetBIOS code identifies the **Primary Domain Controller (PDC)**?
- A) `<domain> <1D>`
- B) `<domain> <1B>`
- C) `<domain> <00>`
- D) `<hostname> <03>`

**Q10.** Which `nbtstat` option displays the **NetBIOS name table of a remote computer given its IP address**?
- A) `-a`
- B) `-A`
- C) `-c`
- D) `-n`

**Q11.** Which `nbtstat` option lists the contents of the **NetBIOS name cache**?
- A) `-c`
- B) `-n`
- C) `-r`
- D) `-R`

**Q12.** Which utility from the **PsTools** suite displays users connected both locally and via resource shares?
- A) PsList
- B) PsLoggedOn
- C) PsInfo
- D) PsGetSid

**Q13.** Which command shows **ALL shares of a computer, including hidden administrative shares** such as `ADMIN$`, `C$`, and `IPC$`?
- A) `net view \\<computername> /ALL`
- B) `net view /domain`
- C) `net use \\<computername>`
- D) `nbtstat -S`

**Q14.** Which of the following is NOT a NetBIOS enumeration tool mentioned in the module?
- A) NetBIOS Enumerator
- B) Global Network Inventory
- C) Advanced IP Scanner
- D) OpUtils

---

### Part B — SNMP & LDAP (Q15–Q27)

**Q15.** SNMP operates on which ports?
- A) TCP 161 and TCP 162
- B) UDP 161 (agent) and UDP 162 (trap/notifications)
- C) TCP 389 and TCP 636
- D) UDP 123 only

**Q16.** In SNMP, the **community string** acts as:
- A) An encryption key
- B) A password
- C) A certificate
- D) A routing metric

**Q17.** Which community strings are commonly used as **defaults** on SNMP devices?
- A) `admin` and `root`
- B) `public` (read-only) and `private` (read/write)
- C) `user` and `password`
- D) `snmp` and `trap`

**Q18.** Which SNMP PDU is used by the **manager to modify the value of an object** on the agent?
- A) Get Request
- B) Set Request
- C) GetNext Request
- D) Trap

**Q19.** Which SNMP PDU is sent **asynchronously by the agent** to report an event and is **NOT acknowledged**?
- A) Response
- B) Inform Request
- C) Trap
- D) GetBulk Request

**Q20.** Which version of SNMP provides **authentication, integrity, and encryption** of messages?
- A) SNMPv1
- B) SNMPv2c
- C) SNMPv3
- D) SNMPv2u

**Q21.** Which Nmap script is used to **brute-force the SNMP community strings**?
- A) `snmp-sysdescr`
- B) `snmp-brute`
- C) `snmp-processes`
- D) `snmp-interfaces`

**Q22.** Which Linux command **walks the MIB tree** of an SNMP device?
- A) `snmpwalk`
- B) `snmputil get`
- C) `nmap -sT`
- D) `ldapsearch`

**Q23.** LDAP servers typically listen on which ports?
- A) UDP 137 and UDP 138
- B) TCP 389 (LDAP) and TCP 636 (LDAPS)
- C) TCP 25 and TCP 587
- D) UDP 500 and UDP 4500

**Q24.** In LDAP, a **DN (Distinguished Name)** such as `CN=users,DC=htb,DC=local`:
- A) Identifies the IP address of the server
- B) Uniquely identifies an entry in a directory
- C) Is the encryption certificate of the directory
- D) Specifies the port number of the server

**Q25.** What is the correct `ldapsearch` syntax to list all entries of a directory base?
- A) `ldapsearch -h <IP> -x -b "DC=htb,DC=local" '(objectclass=*)'`
- B) `ldapsearch -p <IP> -s "DC=htb,DC=local" '*'
- C) `ldapsearch -h <IP> -x -b <DC> query`
- D) `ldapsearch -d <IP> -b '(objectclass=*)'`

**Q26.** Which LDAP directory component is the **server-side component** that provides access to a directory?
- A) DN
- B) DSA (Directory System Agent)
- C) RDN
- D) BER

**Q27.** LDAP uses which encoding rules to transmit its messages?
- A) Base64
- B) BER (Basic Encoding Rules)
- C) DER only
- D) UTF-16

---

### Part C — NTP, NFS, RPC & Unix/Linux (Q28–Q42)

**Q28.** NTP operates on which port and protocol?
- A) TCP 123
- B) UDP 123
- C) UDP 161
- D) TCP 389

**Q29.** Which NTP utility **traces the chain of NTP servers back to its source** to determine where a host obtains its time?
- A) ntpdate
- B) ntptrace
- C) ntpdc
- D) ntpq

**Q30.** Which NTP tool has replaced `ntpd` on many modern Linux distributions and uses the `chronyc` command-line interface?
- A) ntpdate
- B) chronyd
- C) ptpd
- D) openntpd

**Q31.** NFS listens on which TCP port by default?
- A) 389
- B) 2049
- C) 445
- D) 111

**Q32.** Which command lists the **RPC programs** running on a target host?
- A) `rpcinfo -p <IP>`
- B) `showmount -e <IP>`
- C) `rpcinfo -e`
- D) `showmount -a`

**Q33.** Which command lists the **NFS exports (shares)** available on a target host?
- A) `rpcinfo -p <IP>`
- B) `showmount -e <IP>`
- C) `nfsls -e <IP>`
- D) `exportfs -v`

**Q34.** The NFS export configuration file is:
- A) `/etc/nfs`
- B) `/etc/exports`
- C) `/etc/mtab`
- D) `/etc/nfsconfig`

**Q35.** A misconfiguration of NFS exports can lead to:
- A) Only a denial of service
- B) Remote control of the file system, privilege escalation, and backdoors
- C) Sniffing of clear-text emails
- D) DNS cache poisoning

**Q36.** Which tool scans RPC services for common vulnerabilities?
- A) RPCScan
- B) SuperEnum
- C) nbtstat
- D) svmap

**Q37.** Which service listens on TCP/UDP **port 111** and is used to map RPC services to their ports?
- A) NetBIOS
- B) portmapper (rpcbind)
- C) LDAP
- D) NTP

**Q38.** Which files contain the **user accounts** and the **hashed passwords** on Unix/Linux systems?
- A) `/etc/hosts` and `/etc/resolv.conf`
- B) `/etc/passwd` and `/etc/shadow`
- C) `/etc/group` and `/etc/nologin`
- D) `/var/log/passwd` and `/etc/secret`

**Q39.** Which classic command is used to enumerate **user accounts** on Unix/Linux hosts?
- A) `finger`
- B) `showmount`
- C) `svmap`
- D) `snmpwalk`

**Q40.** Which command lists the **shared resources** on an SMB target from Linux?
- A) `net view \\<host>`
- B) `smbclient -L //<IP>`
- C) `nbtstat -S`
- D) `rpcinfo -p <IP>`

**Q41.** SMB directly hosted on TCP uses which port?
- A) 139
- B) 445
- C) 143
- D) 4450

**Q42.** Which of the following is NOT a recommended SMB countermeasure?
- A) Using strong passwords (12+ characters)
- B) Allowing empty passwords for local accounts
- C) Disabling NetBIOS when not required
- D) Blocking ports 139 and 445 at the firewall

---

### Part D — SMTP, DNS, IPsec, VoIP & Countermeasures (Q43–Q60)

**Q43.** Which SMTP command is used to **verify whether a user account exists** on the mail server?
- A) EXPN
- B) VRFY
- C) HELO
- D) DATA

**Q44.** Which SMTP command **expands a mailing list**?
- A) VRFY
- B) EXPN
- C) RCPT TO
- D) RESET

**Q45.** During SMTP enumeration, a response of **`250`** to a VRFY request indicates:
- A) The user account does not exist
- B) The user account exists
- C) The server is an open relay
- D) The server is offline

**Q46.** Which Nmap script **enumerates users** on an SMTP server using RCPT, VRFY, and EXPN?
- A) `smtp-commands`
- B) `smtp-enum-users`
- C) `smtp-open-relay`
- D) `smtp-brute`

**Q47.** Which Metasploit auxiliary module is used to **enumerate SMTP users**?
- A) `auxiliary/scanner/smtp/smtp_enum`
- B) `auxiliary/scanner/smtp/smtp_relay`
- C) `auxiliary/scanner/smtp/options`
- D) `auxiliary/scanner/smtp/login`

**Q48.** Which DNS technique reveals **all named hosts, subzones, and their IP addresses** when a name server is misconfigured?
- A) DNS cache snooping
- B) DNS zone transfer
- C) DNSSEC zone walking
- D) DNS recursion

**Q49.** Which command performs a **DNS zone transfer** using `dig`?
- A) `dig @<IP> <domain> AXFR`
- B) `dig @<IP> <domain> TXT`
- C) `dig -x <IP>`
- D) `dig @<IP> <domain> +norecurse`

**Q50.** Which `nslookup` command sequence performs a **zone transfer** in interactive mode?
- A) `set type=any` then `ls -d <domain>`
- B) `set type=soa` then `ls -t <domain>`
- C) `set recurse` then `ls -e <domain>`
- D) `set type=ns` then `ls -z <domain>`

**Q51.** The **cache snooping** technique allows an attacker to determine:
- A) The encryption keys of the DNS server
- B) Which DNS records the target server has recently cached
- C) The DNS server's IP address
- D) The TTL of the root servers

**Q52.** Which method of cache snooping checks the **TTL decreasing** over time to confirm a cached record?
- A) Non-recursive method (RD=0)
- B) Recursive method (TTL)
- C) The Traceroute method
- D) The brute-force method

**Q53.** **DNSSEC zone walking** uses which record type to enumerate the records of a zone?
- A) SOA
- B) NSEC
- C) AAAA
- D) MX

**Q54.** Which DNSSEC mechanism makes **zone walking practically impossible**?
- A) NSEC
- B) NSEC3
- C) RRSIG
- D) DS

**Q55.** Which OWASP tool is used for **DNS enumeration and mapping of external attack surfaces**?
- A) Amass
- B) dnsrecon
- C) dnsenum
- D) SuperEnum

**Q56.** IPsec's ISAKMP/IKE protocol operates on which port?
- A) UDP 500
- B) TCP 500
- C) UDP 4500
- D) TCP 53

**Q57.** Which tool is used to **discover and fingerprint IPsec VPN gateways** and can crack pre-shared keys with `psk-crack`?
- A) svmap
- B) ike-scan
- C) rpcscan
- D) snmpwalk

**Q58.** VoIP/SIP signaling typically uses which ports?
- A) UDP 500 and UDP 4500
- B) TCP/UDP 5060 and 5061
- C) TCP 22 and TCP 25
- D) TCP 139 and TCP 445

**Q59.** Which Metasploit auxiliary module **enumerates VoIP extensions**?
- A) `auxiliary/scanner/sip/options`
- B) `auxiliary/scanner/sip/enumerator`
- C) `auxiliary/scanner/voip/extensions`
- D) `auxiliary/scanner/sip/register`

**Q60.** Which of the following is an **effective countermeasure against DNS zone walking**?
- A) Disabling DNSSEC entirely
- B) Using DNSSEC with NSEC3 (hashing)
- C) Allowing recursive queries from anyone
- D) Increasing the DNS TTL to 86400

---

## Answer Key

### Part A
| Q | Answer | Explanation |
|---|---|---|
| 1 | **A** | Enumeration extracts user names, machine names, network resources, shares, and services |
| 2 | **B** | Enumeration techniques operate in an intranet environment |
| 3 | **A** | Routing tables and audit/service settings are enumerated; along with shares, SNMP details, machine names, users/groups, applications/banners |
| 4 | **B** | Enumeration may be illegal; a proper authorization is always required |
| 5 | **B** | An IPC$ share is probed to brute-force admin credentials and gain access to the file system |
| 6 | **B** | The 16th character of a NetBIOS name indicates the service or name type |
| 7 | **B** | NetBIOS uses UDP 137 (names), UDP 138 (datagrams), TCP 139 (sessions) |
| 8 | **B** | `<hostname> <20>` = Server service; `<00>` = hostname, `<03>` = Messenger |
| 9 | **B** | `<domain> <1B>` = Primary Domain Controller (PDC); `<1D>` = master browser |
| 10 | **B** | `-A` = remote name table by IP; `-a` = by NetBIOS name; `-c` = name cache; `-n` = local names |
| 11 | **A** | `-c` lists the NetBIOS name cache; `-r` counts resolved names; `-R` purges the cache |
| 12 | **B** | PsLoggedOn shows users connected locally and via resource shares (NetSessionEnum) |
| 13 | **A** | `net view \\<host> /ALL` shows all shares including hidden `ADMIN$`, `C$`, `IPC$` |
| 14 | **D** | OpUtils is an IP/port management tool (SNMP section); NetBIOS tools: NetBIOS Enumerator, Global Network Inventory, Advanced IP Scanner, Hyena |

### Part B
| Q | Answer | Explanation |
|---|---|---|
| 15 | **B** | SNMP uses UDP 161 (agent) and UDP 162 (traps/notifications) |
| 16 | **B** | The community string acts as a password |
| 17 | **B** | Default community strings: `public` (read-only) and `private` (read/write) |
| 18 | **B** | Set Request modifies the value of an object on the agent |
| 19 | **C** | Trap = asynchronous, unsolicited, and unacknowledged notification (sent to port 162) |
| 20 | **C** | SNMPv3 provides authentication, integrity, and encryption |
| 21 | **B** | `snmp-brute.nse` brute-forces SNMP v1 community strings |
| 22 | **A** | `snmpwalk` walks the MIB tree (e.g., `snmpwalk -v1 -c public <IP>`) |
| 23 | **B** | LDAP = TCP 389; LDAPS = TCP 636 |
| 24 | **B** | A DN uniquely identifies an entry in a directory (RDN separated by commas) |
| 25 | **A** | `ldapsearch -h <IP> -x -b "DC=htb,DC=local" '(objectclass=*)'` |
| 26 | **B** | DSA (Directory System Agent) is the server-side component |
| 27 | **B** | LDAP uses BER (Basic Encoding Rules) to transmit messages |

### Part C
| Q | Answer | Explanation |
|---|---|---|
| 28 | **B** | NTP operates on UDP 123 |
| 29 | **B** | `ntptrace` traces the NTP chain to its source |
| 30 | **B** | `chronyd` (package `chrony`) replaces `ntpd`; queried via `chronyc` |
| 31 | **B** | NFS uses TCP 2049 by default |
| 32 | **A** | `rpcinfo -p <IP>` lists the RPC programs and their ports |
| 33 | **B** | `showmount -e <IP>` lists the NFS exports |
| 34 | **B** | The NFS export configuration is stored in `/etc/exports` |
| 35 | **B** | Misconfigured NFS exports lead to remote control, privilege escalation, and backdoors |
| 36 | **A** | RPCScan checks RPC communications and common vulnerabilities |
| 37 | **B** | The portmapper (rpcbind) listens on TCP/UDP 111 and maps RPC services |
| 38 | **B** | `/etc/passwd` = user accounts; `/etc/shadow` = hashed passwords |
| 39 | **A** | `finger` enumerates user accounts on Unix/Linux hosts |
| 40 | **B** | `smbclient -L //<IP>` lists SMB shares from Linux |
| 41 | **B** | SMB directly hosted (without NetBIOS) uses TCP 445 |
| 42 | **B** | Empty passwords are a weakness; strong passwords (12+) are required |

### Part D
| Q | Answer | Explanation |
|---|---|---|
| 43 | **B** | VRFY verifies whether a user account exists |
| 44 | **B** | EXPN expands a mailing list |
| 45 | **B** | `250` = the user exists; `550` = the user does not exist |
| 46 | **B** | `smtp-enum-users.nse` enumerates users via RCPT, VRFY, and EXPN |
| 47 | **A** | `auxiliary/scanner/smtp/smtp_enum` enumerates SMTP users in Metasploit |
| 48 | **B** | A DNS zone transfer reveals all named hosts, subzones, and IPs if misconfigured |
| 49 | **A** | `dig @<IP> <domain> AXFR` performs a zone transfer |
| 50 | **A** | `set type=any` then `ls -d <domain>` in nslookup |
| 51 | **B** | Cache snooping reveals which DNS records the target server has cached recently |
| 52 | **B** | The recursive (TTL) method observes the TTL decreasing to confirm the cached record |
| 53 | **B** | Zone walking uses NSEC records to enumerate the zone in canonical order |
| 54 | **B** | NSEC3 (hashing) makes zone walking practically impossible |
| 55 | **A** | Amass (OWASP) maps external attack surfaces and performs DNS enumeration |
| 56 | **A** | ISAKMP/IKE operates on UDP 500 |
| 57 | **B** | ike-scan discovers/fingerprints IPsec gateways and cracks PSKs with psk-crack |
| 58 | **B** | SIP uses TCP/UDP 5060 (plain) and 5061 (TLS) |
| 59 | **B** | `auxiliary/scanner/sip/enumerator` enumerates VoIP extensions |
| 60 | **B** | DNSSEC with NSEC3 hashing prevents zone walking |

---

## Indicative scoring
- **50–60 correct**: excellent — ready for the exam
- **40–49**: good — review the missed sections
- **30–39**: average — restudy the course, then retry
- **< 30**: re-read the complete Module 04 course document

---

*Dump generated from the content of CEH v13 Module 04 (Enumeration). In case of OCR transcription errors, the official EC-Council PDF remains the reference.*




