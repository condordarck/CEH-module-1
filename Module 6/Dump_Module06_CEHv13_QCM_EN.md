# CEH v13 Dump — Module 06 : System Hacking
## Exam-Style Practice Questions (312-50) — With Answer Key

> 72 multiple-choice questions based on Module 06 content. Answer key at the end.

---

## Questions

### Part A — System Hacking Overview & Password Storage (Q1–Q10)

**Q1.** Which of the following is the **correct order** of the four stages of the system hacking methodology?
- A) Escalating Privileges → Gaining Access → Maintaining Access → Clearing Logs
- B) Gaining Access → Escalating Privileges → Maintaining Access → Clearing Logs
- C) Gaining Access → Maintaining Access → Escalating Privileges → Clearing Logs
- D) Clearing Logs → Gaining Access → Escalating Privileges → Maintaining Access

**Q2.** Windows stores local user passwords in the:
- A) Registry hive SYSTEM32
- B) Security Accounts Manager (SAM) database
- C) KDC database
- D) LSA secrets file only

**Q3.** The **SYSKEY** mechanism protects password information stored in the SAM by encrypting it with a:
- A) 56-bit DES key
- B) 128-bit encryption key
- C) 2048-bit RSA key
- D) 32-bit XOR key

**Q4.** Which tool extracts the **LM and NTLM password hashes** directly from the SAM file?
- A) pwdump7
- B) Responder
- C) Steghide
- D) BloodHound

**Q5.** **Mimikatz** extracts plaintext passwords, Kerberos tickets, and NTLM hashes from the memory of which process?
- A) winlogon.exe
- B) svchost.exe
- C) LSASS
- D) explorer.exe

**Q6.** The **Kerberos** authentication protocol operates on which port?
- A) 137/TCP
- B) 445/TCP
- C) 5355/UDP
- D) 88/TCP

**Q7.** **Kerberoasting** is an attack technique that targets the Kerberos protocol by cracking:
- A) TGS (Service Tickets)
- B) TGT (Ticket Granting Tickets) of accounts without pre-authentication
- C) NTLM hashes from the SAM file
- D) LLMNR responses

**Q8.** **AS-REP Roasting** (cracking the TGT) targets accounts that have:
- A) Kerberos pre-authentication enabled
- B) Kerberos pre-authentication disabled
- C) Smart card logon enabled
- D) The "password never expires" flag set

**Q9.** A **Golden Ticket** attack forges TGTs for the entire Active Directory by compromising the hash of the:
- A) KRBTGT (Key Distribution Service) account
- B) Default Administrator account
- C) Local SYSTEM account
- D) Domain Guest account

**Q10.** A **Silver Ticket** is a forged Kerberos ticket used to access:
- A) The entire Active Directory domain
- B) A specific service or resource
- C) Only the local SAM database
- D) Only the DNS server

### Part B — Password Cracking Techniques & Tools (Q11–Q20)

**Q11.** A **rainbow table attack** works by:
- A) Trying every possible character combination
- B) Using precomputed tables of hashes to reverse hash values
- C) Substituting the LSB of each pixel
- D) Sending specially crafted network probes

**Q12.** A **hybrid attack** combines dictionary words with:
- A) Only lowercase letters
- B) Appended characters, numbers, or symbols
- C) Hashes of other users
- D) Markov chains only

**Q13.** The **birthday attack** reduces the complexity of finding a hash collision to approximately:
- A) 2^n attempts
- B) 2^n/2 attempts
- C) 2 × n attempts
- D) n/2 attempts

**Q14.** In **hashcat**, the `-m` flag is used to specify the:
- A) Attack mode
- B) Hash mode (type of hash)
- C) Number of GPUs
- D) Output file format

**Q15.** The hashcat command `hashcat -a 3 -m 0 md5_hashes.txt ?l?l?d?d` performs:
- A) A dictionary attack
- B) A brute-force (mask) attack
- C) A rainbow table lookup
- D) A rule-based attack

**Q16.** Which tool is used to perform **LLMNR / NBT-NS poisoning** to capture NTLMv2 hashes?
- A) Responder
- B) Ophcrack
- C) John the Ripper
- D) WES-NG

**Q17.** The main countermeasure against **SMB relay attacks** is to:
- A) Disable the SMB signing requirement
- B) Enforce SMB signing (SMB signature)
- C) Enable NetBIOS name resolution
- D) Use LLMNR for name resolution

**Q18.** The **Internal Monologue attack** is similar to a Mimikatz attack, except that it:
- A) Dumps the LSASS memory directly
- B) Does not dump LSASS memory, thereby avoiding Windows Credential Guard and antivirus
- C) Only works on Linux systems
- D) Requires physical access to the keyboard

**Q19.** **THC-Hydra** is primarily used for:
- A) Offline cracking of hashes
- B) Online brute-force / password spraying of remote services
- C) Network sniffing
- D) Steganography detection

**Q20.** **Shoulder surfing** is classified as which type of password attack?
- A) Active online attack
- B) Passive online attack
- C) Offline attack
- D) Non-electronic attack

### Part C — Keyloggers, Spyware & Remote Sessions (Q21–Q30)

**Q21.** A **physical (hardware) keylogger** is typically placed:
- A) Inside the CPU
- B) Between the keyboard hardware and the operating system
- C) In the BIOS of the graphics card
- D) On the DNS server

**Q22.** A **kernel-based keylogger** operates at which level?
- A) Application level
- B) Kernel level (root privileges)
- C) Network level
- D) Boot loader level only

**Q23.** A keylogger records which of the following without the user's knowledge?
- A) Only mouse movements
- B) Each keystroke made on the computer keyboard
- C) Only network packets
- D) Only the MAC address

**Q24.** **Spytech SpyAgent** is an example of:
- A) A rootkit detection tool
- B) A spyware/surveillance tool (keylogging, screenshots, activity tracking)
- C) A password cracker
- D) A steganography tool

**Q25.** An attacker can **hide data** in an NTFS file by using:
- A) Alternate Data Streams (ADS)
- B) SUID bits
- C) SYSKEY
- D) Prefetch files

**Q26.** **PsExec** (from Microsoft/Sysinternals) is used to:
- A) Crack passwords offline
- B) Execute processes remotely on Windows systems
- C) Enumerate Kerberos tickets
- D) Wipe disk drives

**Q27.** **RDP (Remote Desktop Protocol)** is a technology used to:
- A) Establish remote desktop sessions
- B) Detect rootkits
- C) Poison DNS requests
- D) Encrypt the SAM database

**Q28.** Which of the following tools helps detect the creation of **additional NTFS streams**?
- A) Stream Detector or GMER
- B) hashcat
- C) John the Ripper
- D) Ophcrack

**Q29.** **Spyware** is malware that:
- A) Encrypts all files on the disk
- B) Secretly gathers information about users without their knowledge
- C) Replaces the bootloader
- D) Only displays pop-up ads

**Q30.** Which countermeasure helps mitigate the risk of **hardware keyloggers**?
- A) Using an on-screen (virtual) keyboard
- B) Disabling SMB signing
- C) Using default passwords
- D) Enabling LLMNR

### Part D — Privilege Escalation (Q31–Q40)

**Q31.** **Vertical privilege escalation** refers to:
- A) Moving from one user to another at the same privilege level
- B) Gaining higher privileges (e.g. standard user → administrator/root)
- C) Escalating across network segments
- D) Downgrading from admin to standard user

**Q32.** **Horizontal privilege escalation** refers to:
- A) Gaining higher privileges than the current user
- B) Moving to another account of the **same privilege level**
- C) Gaining access to the Domain Controller
- D) Clearing the logs of other users

**Q33.** **DLL hijacking** (DLL side-loading) exploits the fact that Windows loads DLLs according to a:
- A) Random order
- B) Fixed DLL search order
- C) Reverse alphabetical order
- D) Network load-balancing order

**Q34.** Which directory is searched **first** when Windows loads a DLL for an application?
- A) The system directory (System32)
- B) The application's directory
- C) The current working directory
- D) The PATH environment directories

**Q35.** Which command discovers **SUID-executable binaries** on a Linux system?
- A) `find / -perm -u=s -type f`
- B) `ls -la /etc/passwd`
- C) `ps aux`
- D) `df -h`

**Q36.** **Dylib Hijack Scanner** is a tool that detects hijacking vulnerabilities in dynamic libraries of which OS?
- A) Windows
- B) macOS
- C) Android
- D) Linux kernel modules

**Q37.** During a **Windows buffer overflow exploitation**, the attacker overwrites which register to redirect execution?
- A) ESP
- B) EAX
- C) EIP
- D) EBX

**Q38.** The primary purpose of **Metasploit encoder modules** is to:
- A) Speed up network scanning
- B) Transform payloads to avoid detection by security systems/antivirus
- C) Generate rainbow tables
- D) Compress log files

**Q39.** **Windows Exploit Suggester - Next Generation (WES-NG)** is a Python-based tool that:
- A) Compares the target's patches with a CVE database to suggest privilege escalation exploits
- B) Performs SMB relay attacks
- C) Detects NTFS streams
- D) Cracks NTLM hashes with GPU

**Q40.** **BloodHound** is used to:
- A) Map the domain and reveal attack paths in Active Directory
- B) Perform keystroke logging
- C) Hide messages in images
- D) Wipe system logs

### Part E — Maintaining Access: Rootkits & Steganography (Q41–Q50)

**Q41.** The main purpose of a **rootkit** is to:
- A) Encrypt the user's files
- B) Maintain privileged access to the system while hiding its presence and activities
- C) Speed up the operating system
- D) Clean browser history

**Q42.** A **bootkit** is a type of rootkit that:
- A) Only runs in user mode
- B) Replaces the system's bootloader (e.g. MBR), loading before the OS
- C) Only affects the DNS cache
- D) Cannot be used on Windows

**Q43.** A **kernel-mode rootkit** hides its presence by:
- A) Modifying the SAM database
- B) Intercepting system calls by installing drivers/DLLs in the kernel
- C) Replacing the desktop wallpaper
- D) Modifying only user-visible files

**Q44.** **Signature-based rootkit detection** works by:
- A) Profiling the runtime execution path
- B) Comparing the system against a database of known rootkit signatures
- C) Analyzing user behavior
- D) Scanning open ports

**Q45.** **Runtime execution path profiling** detects rootkits by:
- A) Comparing the actual execution path with the expected execution path to find deviations
- B) Hashing all files on disk
- C) Monitoring network bandwidth
- D) Checking the DNS cache

**Q46.** Which tool helps detect and remove rootkits and can also be used to detect NTFS streams?
- A) GMER
- B) Responder
- C) OpenStego
- D) hashcat

**Q47.** In **LSB insertion** (image steganography), the hidden data is inserted into:
- A) The most significant bit of each pixel
- B) The least significant bit (LSB) of each pixel
- C) The image header only
- D) The file extension

**Q48.** Which of the following are **transform-domain (frequency domain)** steganography techniques?
- A) FFT, DCT, and wavelet transformation
- B) LSB and masking only
- C) Snow and whitespace
- D) XOR and Caesar cipher

**Q49.** The **Snow** tool is used to conceal messages in:
- A) Images, by modifying pixels
- B) Text files, by appending tabs and spaces to lines
- C) Audio files, by adding echo
- D) Video frames

**Q50.** **Steganalysis** refers to:
- A) Hiding data in images
- B) Detecting and extracting hidden messages
- C) Watermarking media for copyright
- D) Encrypting log files

### Part F — Domain Dominance & Covering Tracks (Q51–Q60)

**Q51.** A **skeleton key attack** injects false credentials into domain controllers by patching:
- A) The SAM database
- B) LSASS (Local Security Authority Server Service)
- C) The DNS cache
- D) The Prefetch directory

**Q52.** After executing `misc::skeleton` with mimikatz, the attacker can masquerade as any domain user using the default master credentials:
- A) `admin`
- B) `mimikatz`
- C) `password`
- D) `root`

**Q53.** The skeleton key attack requires the attacker to have:
- A) Only standard user rights
- B) Domain administrator rights and access to the domain controller
- C) Physical access to the target workstation
- D) The victim's smart card

**Q54.** The **Empire** tool automates the skeleton key attack using which module?
- A) `powershell/persistence/misc/skeleton_key`
- B) `exploit/windows/smb/ms17_010`
- C) `auxiliary/scanner/ssh/ssh_login`
- D) `post/multi/recon/local_exploit_suggester`

**Q55.** A **Pass-the-Hash (PtH)** attack allows an attacker to:
- A) Crack a password offline with rainbow tables
- B) Authenticate to a remote system using a stolen NTLM hash without knowing the plaintext password
- C) Forge a TGT with the KRBTGT hash
- D) Clear the Bash history

**Q56.** Which command **disables security auditing** on the target Windows system?
- A) `auditpol /set /category:"system","account logon" /success:disable`
- B) `auditpol /get /category:*`
- C) `wevtutil cl Security`
- D) `fsutil behavior set disablelastaccess 1`

**Q57.** The `wevtutil cl` command is used to:
- A) Disable hibernation
- B) Clear Windows event logs
- C) Shred a file
- D) Create a shadow copy

**Q58.** `fsutil behavior set disablelastaccess 1` is used by attackers to:
- A) Disable the last access timestamps on files
- B) Enable the thumbnail cache
- C) Clear the Bash history
- D) Create a new user account

**Q59.** The command `export HISTSIZE=0` in a Bash shell:
- A) Clears the current shell history only
- B) Disables the Bash shell from saving command history
- C) Shreds the `~/.bash_history` file
- D) Displays the saved history

**Q60.** Which command **shreds the history file** so its contents become unreadable?
- A) `shred ~/.bash_history`
- B) `history -c`
- C) `cat /dev/null > ~/.bash_history`
- D) `export HISTSIZE=100`

### Part G — Privilege Escalation & Anti-Forensics Extras (Q61–Q72)

**Q61.** Which Metasploit exploit **bypasses UAC by hijacking a special key** from the HKCU registry hive attached to `fodhelper.exe`?
- A) `bypassuac`
- B) `bypassuac_fodhelper`
- C) `bypassuac_injection`
- D) `exploit/windows/local/ms16_075`

**Q62.** The **NFS** protocol provides communication between client and server through RPC on which port?
- A) 445
- B) 2049
- C) 3389
- D) 5985

**Q63.** Which file stores the configuration of **unattended installs** and may contain decoded passwords and local account details?
- A) `sysmain.sdb`
- B) `Unattend.xml`
- C) `Hiberfil.sys`
- D) `pagefile.sys`

**Q64.** Replacing **sethc.exe** with `cmd.exe` to obtain a backdoor at the login screen is an example of:
- A) Abusing accessibility features
- B) DLL search order hijacking
- C) Named pipe impersonation
- D) Application shimming

**Q65.** A **shim** named **RedirectEXE** in the Windows Application Compatibility Framework can be abused to:
- A) Capture memory addresses
- B) Bypass UAC
- C) Inject DLLs only
- D) Clear event logs

**Q66.** The **AdminSDHolder** object is periodically re-applied to privileged accounts by which process?
- A) DCSync
- B) SDProp (Security Descriptor Propagator)
- C) Skeleton Key
- D) WfpAleProcessTokenReference

**Q67.** In a **stego-only attack** (steganalysis), the analyst:
- A) Knows both the original and stego object
- B) Has access only to the stego-object and must try every possible algorithm
- C) Knows the message but not the cover
- D) Uses a chi-square test only

**Q68.** The **zsteg** tool is used to detect stegano-hidden data in which file types?
- A) PNG and BMP images
- B) MP3 audio
- C) Text files
- D) Executables

**Q69.** After exploiting the **Sticky Keys** feature with Metasploit's `sticky_keys` module, pressing **Shift five times** at the login screen:
- A) Opens a Command Prompt with system-level access
- B) Reboots the system
- C) Clears the Bash history
- D) Disables the firewall

**Q70.** **Trail obfuscation** (modifying timestamps, log tampering) can be performed using which tools?
- A) Timestomp and Transmogrify
- B) zsteg and Snow
- C) pwdump7 and fgdump
- D) GMER and Stream Detector

**Q71.** Windows **WMI** remote access can be performed via DCOM and WinRM, which use respectively the ports:
- A) 135 and 5985/5986
- B) 88 and 389
- C) 445 and 3389
- D) 137 and 5355

**Q72.** **Certipy** is a tool used to:
- A) Crack Kerberos tickets
- B) Identify and abuse misconfigured ADCS (Active Directory Certificate Services) templates
- C) Poison LLMNR/NBT-NS
- D) Wipe disk drives

---

## Answer Key

### Part A
| Q | Answer | Explanation |
|---|---|---|
| 1 | **B** | The CHM stages are Gaining Access → Escalating Privileges → Maintaining Access → Clearing Logs |
| 2 | **B** | Windows stores local user passwords (hashed) in the SAM database |
| 3 | **B** | SYSKEY protects SAM password info using a 128-bit encryption key |
| 4 | **A** | pwdump7 extracts LM and NTLM hashes from the SAM |
| 5 | **C** | Mimikatz reads credentials from the memory of LSASS |
| 6 | **D** | Kerberos operates on 88/TCP |
| 7 | **A** | Kerberoasting cracks TGS (service tickets) |
| 8 | **B** | AS-REP Roasting targets accounts with pre-authentication disabled |
| 9 | **A** | Golden Tickets are forged by compromising the KRBTGT account hash |
| 10 | **B** | Silver Tickets are forged for a specific service/resource |

### Part B
| Q | Answer | Explanation |
|---|---|---|
| 11 | **B** | Rainbow table attacks use precomputed hash tables |
| 12 | **B** | Hybrid attacks add characters/numbers/symbols to dictionary words |
| 13 | **B** | The birthday attack finds collisions in about 2^n/2 attempts |
| 14 | **B** | `-m` in hashcat sets the hash mode (hash type) |
| 15 | **B** | `-a 3` is the brute-force/mask attack in hashcat |
| 16 | **A** | Responder performs LLMNR/NBT-NS poisoning to capture NTLMv2 hashes |
| 17 | **B** | SMB signing (SMB signature) prevents SMB relay attacks |
| 18 | **B** | The Internal Monologue attack avoids dumping LSASS memory (bypasses Credential Guard/AV) |
| 19 | **B** | THC-Hydra performs online brute-force / password spraying of remote services |
| 20 | **D** | Shoulder surfing is a non-electronic attack |

### Part C
| Q | Answer | Explanation |
|---|---|---|
| 21 | **B** | Hardware keyloggers sit between the keyboard hardware and the OS |
| 22 | **B** | Kernel-based keyloggers run at the kernel level |
| 23 | **B** | Keyloggers record each keystroke made on the keyboard |
| 24 | **B** | Spytech SpyAgent is a spyware/surveillance tool |
| 25 | **A** | NTFS Alternate Data Streams (ADS) hide data in file streams |
| 26 | **B** | PsExec executes processes remotely on Windows |
| 27 | **A** | RDP establishes remote desktop sessions |
| 28 | **A** | Stream Detector and GMER detect additional NTFS streams |
| 29 | **B** | Spyware secretly gathers user information without knowledge |
| 30 | **A** | On-screen (virtual) keyboards mitigate hardware keyloggers |

### Part D
| Q | Answer | Explanation |
|---|---|---|
| 31 | **B** | Vertical escalation = gaining higher privileges |
| 32 | **B** | Horizontal escalation = another account at the same privilege level |
| 33 | **B** | DLL hijacking exploits the fixed DLL search order |
| 34 | **B** | The application's directory is searched first |
| 35 | **A** | `find / -perm -u=s -type f` discovers SUID binaries |
| 36 | **B** | Dylib Hijack Scanner targets macOS dylib libraries |
| 37 | **C** | The EIP (instruction pointer) is overwritten to redirect execution |
| 38 | **B** | Encoders transform payloads to avoid detection |
| 39 | **A** | WES-NG suggests exploits by comparing patches with CVE data |
| 40 | **A** | BloodHound maps AD and reveals attack paths |

### Part E
| Q | Answer | Explanation |
|---|---|---|
| 41 | **B** | Rootkits maintain privileged access while hiding presence/activity |
| 42 | **B** | Bootkits replace the bootloader and load before the OS |
| 43 | **B** | Kernel-mode rootkits intercept system calls via kernel drivers/DLLs |
| 44 | **B** | Signature-based detection compares against known signatures |
| 45 | **A** | Runtime execution path profiling compares actual vs expected execution path |
| 46 | **A** | GMER detects/removes rootkits (also used for NTFS streams) |
| 47 | **B** | LSB insertion hides data in the least significant bit of pixels |
| 48 | **A** | FFT, DCT, and wavelet are frequency-domain techniques |
| 49 | **B** | Snow appends tabs/spaces to text lines to hide messages |
| 50 | **B** | Steganalysis detects and extracts hidden messages |

### Part F
| Q | Answer | Explanation |
|---|---|---|
| 51 | **B** | The skeleton key patches LSASS on domain controllers |
| 52 | **B** | Default master credentials after `misc::skeleton` are `mimikatz` |
| 53 | **B** | The attack requires domain admin rights and DC access |
| 54 | **A** | Empire uses `powershell/persistence/misc/skeleton_key` |
| 55 | **B** | PtH authenticates using a stolen NTLM hash without the plaintext password |
| 56 | **A** | `auditpol /set ... /success:disable` disables auditing |
| 57 | **B** | `wevtutil cl` clears Windows event logs |
| 58 | **A** | `disablelastaccess 1` disables last access timestamps |
| 59 | **B** | `HISTSIZE=0` disables Bash history saving |
| 60 | **A** | `shred ~/.bash_history` makes the history file unreadable |

### Part G
| Q | Answer | Explanation |
|---|---|---|
| 61 | **B** | `bypassuac_fodhelper` hijacks a HKCU registry key attached to `fodhelper.exe` |
| 62 | **B** | NFS uses port 2049 via RPC |
| 63 | **B** | `Unattend.xml` stores unattended install config (usernames, possibly decoded passwords) |
| 64 | **A** | Replacing accessibility features (sethc.exe, osk.exe) = abusing accessibility features |
| 65 | **B** | The RedirectEXE shim can be used to bypass UAC |
| 66 | **B** | SDProp re-applies AdminSDHolder ACLs to privileged accounts |
| 67 | **B** | In a stego-only attack, only the stego-object is available |
| 68 | **A** | zsteg detects hidden data in PNG and BMP images |
| 69 | **A** | 5× Shift opens a system-level Command Prompt |
| 70 | **A** | Timestomp and Transmogrify modify date/time metadata |
| 71 | **A** | WMI uses DCOM (135) and WinRM (5985/5986) |
| 72 | **B** | Certipy identifies/abuses misconfigured ADCS templates (e.g. ESC1) |

---

## Indicative scoring
- **60–72 correct**: excellent — ready for the exam
- **48–59**: good — review the missed sections
- **36–47**: average — restudy the course, then retry
- **< 36**: re-read the complete Module 06 course document

---

*Dump generated from the content of CEH v13 Module 06 (System Hacking). In case of OCR transcription errors, the official EC-Council PDF remains the reference.*
