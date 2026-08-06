# CEH v13 — Module 01 : Online Practice Questions (Compilation)
## Questions récupérées depuis des sites gratuits d'entraînement — en anglais (format examen)

> Compilation de questions d'entraînement **gratuites et légales**, récupérées depuis des sites publics de préparation CEH.
> Sources : OpenExamPrep, Examzify, Quizlet.
> Ce ne sont pas des questions officielles d'examen — uniquement du matériel de préparation.
> Rendu du document : le cours officiel (texte OCR) reste la référence en cas de divergence.

---

## Section 1 — OpenExamPrep (open-exam-prep.com/practice/ceh)

**Q1. What is the primary purpose of ethical hacking?**
- A) To illegally access systems for personal gain
- B) To identify vulnerabilities and strengthen security defenses
- C) To steal confidential information from competitors
- D) To disable security systems for testing purposes

> **Réponse : B.** Ethical hacking is the practice of deliberately penetrating systems **with permission** to identify vulnerabilities before malicious hackers can exploit them. The goal is to improve the security posture.

**Q2. Which of the following best describes the difference between a black hat and white hat hacker?**
- A) Black hats use more advanced tools than white hats
- B) Black hats operate without authorization; white hats have explicit permission
- C) Black hats only target government systems
- D) Black hats work during nighttime hours

> **Réponse : B.** The primary distinction is **authorization**. Both may use similar techniques and tools, but intent and legal standing differ fundamentally.

**Q3. What legal document is required before conducting a penetration test?**
- A) A service level agreement (SLA)
- B) A rules of engagement (ROE) document with written authorization
- C) An insurance policy
- D) A non-disclosure agreement (NDA) only

> **Réponse : B.** A **Rules of Engagement (ROE)** with explicit written authorization is essential. It defines scope, timing, methods, and boundaries. NDAs are common but do NOT authorize testing.

**Q4. In the context of penetration testing, what does the term "scope" refer to?**
- A) The budget allocated for the engagement
- B) The specific systems, networks, and assets authorized for testing
- C) The timeline for completing the assessment
- D) The number of vulnerabilities to be discovered

> **Réponse : B.** Scope defines the boundaries of authorized activity (IPs, domains, systems, physical locations). Testing outside scope is unauthorized and potentially illegal.

**Q5. Which phase of the ethical hacking methodology involves gathering information about the target without directly interacting with it?**
- A) Scanning
- B) Reconnaissance
- C) Exploitation
- D) Post-exploitation

> **Réponse : B.** **Reconnaissance** (footprinting) = passive info gathering (public info, DNS records, social media, open sources).

**Q6. What is the term for a hacker who operates between ethical and malicious boundaries, often hacking without permission but claiming to have good intentions?**
- A) White hat
- B) Black hat
- C) Gray hat
- D) Red hat

> **Réponse : C.** A **gray hat** sometimes accesses systems without permission but without intent to harm. Their actions are still technically illegal (no authorization).

**Q7. According to the CEH methodology, what are the five phases of ethical hacking in correct order?**
- A) Reconnaissance, Scanning, Gaining Access, Maintaining Access, Covering Tracks
- B) Scanning, Reconnaissance, Exploitation, Pivoting, Reporting
- C) Information Gathering, Vulnerability Assessment, Exploitation, Persistence, Cleanup
- D) Footprinting, Enumeration, Exploitation, Backdoor Installation, Log Deletion

> **Réponse : A.** 1) Reconnaissance, 2) Scanning, 3) Gaining Access, 4) Maintaining Access, 5) Covering Tracks.

**Q8. Which of the following is NOT a type of information security control?**
- A) Physical controls
- B) Technical controls
- C) Administrative controls
- D) Financial controls

> **Réponse : D.** The three categories are Physical, Technical, and Administrative. Financial controls relate to accounting, not information security.

**Q9. What is the primary difference between vulnerability assessment and penetration testing?**
- A) Vulnerability assessment is automated; penetration testing is manual
- B) Vulnerability assessment identifies weaknesses; penetration testing exploits them
- C) Vulnerability assessment is cheaper than penetration testing
- D) Vulnerability assessment is illegal; penetration testing is legal

> **Réponse : B.** VA identifies/catalogs weaknesses; **pen testing actually exploits** them to demonstrate real-world impact.

**Q10. Which regulation in the United States requires organizations to protect the confidentiality, integrity, and availability of electronic protected health information (ePHI)?**
- A) GDPR
- B) HIPAA
- C) PCI DSS
- D) SOX

> **Réponse : B.** **HIPAA** Security Rule mandates administrative, physical, and technical safeguards for ePHI.

---

## Section 2 — Examzify (cehv13mod1.examzify.com)

**Q11. What is the consequence of a breach of integrity in information security?**
- A) Unauthorized access
- B) Compromised data trustworthiness
- C) Loss of confidentiality
- D) Increased availability issues

> **Réponse : B.** Integrity ensures data remains accurate and unaltered. A breach compromises the **trustworthiness** of the data. (Unauthorized access relates to confidentiality, not integrity.)

**Q12. What is a standard in the context of compliance and regulation?**
- A) A document established by consensus and approved by a recognized body
- B) An unofficial guideline for best practices
- C) A project plan for organizational improvement
- D) A law enforced by government bodies

> **Réponse : A.** A standard is established by consensus and approved by a recognized body. Laws are mandatory legal requirements, different from consensus-driven standards.

---

## Section 3 — Quizlet — Practice Questions Module 1 (quizlet.com/411356720, 72 flashcards)

**Q13.** A security team implements security controls but not all risks are mitigated. What is the next best step?
- Continue applying controls until all risk is eliminated / Ignore remaining risk as "best effort controlled" / **Ensure remaining risk is residual or low and accept the risk** / Remove all controls
> **Réponse :** Accept the residual risk if it is residual or low.

**Q14.** A Certified Ethical Hacker follows a methodology. Which step comes after footprinting in the CEH methodology? (Scanning, Enumeration, Reconnaissance, Application attack)
> **Réponse :** Scanning.

**Q15.** Which of the following best describes a newly discovered flaw in a software application?
> **Réponse :** Zero-day.

**Q16.** Which type of security control is met by encryption?
> **Réponse :** Preventative.

**Q17.** You're on a pen test team. The client wants the attack to simulate a normal user who finds ways to elevate privileges and create attacks. Which test type does the client want?
> **Réponse :** A gray box test.

**Q18.** What is defined as ensuring enforcement of organizational security policy does not rely on voluntary user compliance by assigning sensitivity labels on information and comparing this to the security level a user is operating at?
> **Réponse :** Mandatory Access Control (MAC).

**Q19.** You begin a pen test by checking IP address ranges owned by the target, domain name registration details, and visiting job boards and financial websites to gather technical information online. What activity are you performing?
> **Réponse :** Passive footprinting.

**Q20.** Which best defines a formal written document defining what employees are allowed to use organization systems for, what is not allowed, and the repercussions for breaking the rules?
> **Réponse :** Information security policy (ISP).

**Q21.** An ethical hacker is given no prior knowledge of the network, has a framework to work in, and the agreement specifies boundaries, NDAs, and a completion date. Which of the following is true?
> **Réponse :** A white hat is attempting a black-box test.

**Q22.** Which of the following is a detective control?
> **Réponse :** Audit trail.

**Q23.** As part of a pen test on a U.S. government system, you discover files with Social Security numbers and PII. You are asked about controls on the dissemination of this information. Which act should you check?
> **Réponse :** Privacy Act.

**Q24.** During an audit, Joe discovers a user has a dial-out modem installed on a PC. Which security policy should be checked to see whether modems are allowed?
> **Réponse :** Remote access policy.

**Q25.** A hacker gets frustrated and starts a DoS attack against a server. Which security control is the hacker affecting?
> **Réponse :** Availability.

**Q26.** In which phase of the ethical hacking methodology would a hacker discover available targets on a network?
> **Réponse :** Scanning and Enumeration.

**Q27.** Which of the following are potential drawbacks to a black-box test?
> **Réponse :** The client does not get a focused picture of an internal attacker dedicated to their systems; this test takes the longest amount of time to complete.

---

## Section 4 — Quizlet — Vocabulaire clé CEHv13 Module 01 (quizlet.com/950748441, 178 termes)

| Terme | Définition |
|---|---|
| **Elements of Information Security** | Confidentiality, Integrity, Availability, Authenticity, Non-repudiation |
| **Confidentiality** | Assurance that information is accessible only to those authorized to have access |
| **Integrity** | The trustworthiness of data or resources in terms of preventing improper or unauthorized changes |
| **Availability** | Assurance that systems responsible for delivering, storing, and processing information are accessible when required by authorized users |
| **Authenticity** | The quality of being genuine / not counterfeit |
| **Non-repudiation** | Guarantee that the sender cannot deny having sent the message and the recipient cannot deny having received it |
| **Entity** | Something that makes use of a resource or communication channel |
| **Hacking** | Exploiting system vulnerabilities and compromising security controls to gain unauthorized or inappropriate access to a system |
| **Hacker** | A person who breaks into a system or network without authorization to destroy, steal sensitive data, or perform malicious acts |
| **Script Kiddie** | Inexperienced hackers using premade scripts and tools without understanding them |
| **White Hat Hacker** | A cybersecurity professional who increases security by conducting penetration tests and vulnerability assessments |
| **Black Hat Hacker** | Individuals with malicious intent who violate security |
| **Grey Hat Hacker** | Skilled hackers operating between ethical and unethical lines |
| **Hacktivists** | Politically or socially motivated individuals or groups |
| **State Sponsored Hackers** | Highly trained professionals working for government agencies |
| **Cyber Terrorists** | Extremists using cyber attacks to promote political or religious beliefs |

---

## Liens vers les sources (pour t'entraîner en ligne)

| Site | Lien | Gratuit |
|---|---|---|
| OpenExamPrep (212+ questions CEH v13) | https://open-exam-prep.com/practice/ceh | ✅ oui |
| Examzify Module 1 (20 questions gratuites) | https://cehv13mod1.examzify.com/ | ✅ oui (limité) |
| Passetra Module 1 (221+ questions) | https://cehv13mod1.passetra.com/ | ✅ oui (aperçu) |
| Quizlet Flashcards Module 1 (72) | https://quizlet.com/411356720/ | ✅ oui |
| Quizlet Vocabulaire CEHv13 M01 (178) | https://quizlet.com/950748441 | ✅ oui |
| aguidetocloud (20 questions gratuites, 250 pour $9) | https://www.aguidetocloud.com/guided/eccouncil-ceh-v13/ | ✅ partiellement |

---

*Compilation à but pédagogique personnel. Tous les droits sur les questions restent à leurs auteurs respectifs (OpenExamPrep, Examzify, Quizlet et leurs contributeurs).*
