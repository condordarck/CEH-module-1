# Module 07 — Malware Threats (CEH v13)

> **QCM de révision (anglais, 72 questions) :** voir [`Dump_Module07_CEHv13_QCM_EN.md`](./Dump_Module07_CEHv13_QCM_EN.md)

> Notes de cours en français basées sur le support officiel **CEH v13 — Module 07 : Malware Threats** (EC-Council, 312-50).
> Révision pour l'examen CEH : concepts de malware, Trojans, backdoors, virus, vers, ransomwares et PUAs ; menaces persistantes avancées (APT) et leur cycle de vie ; fileless malware ; malware basé sur l'IA ; analyse statique et dynamique de malware (outils et méthodologie) ; techniques de détection de virus (scanning, integrity checking, interception, code emulation, heuristique) ; contremesures et logiciels anti-malware (anti-Trojan, antivirus, EDR/XDR).

---

## Objectifs d'apprentissage

- Décrire les concepts de **malware** et les techniques de propagation
- Expliquer les **PUAs** (Potentially Unwanted Applications) et l'**adware**
- Décrire les concepts d'**APT** (Advanced Persistent Threat) et son **cycle de vie**
- Décrire les concepts de **Trojans**, leurs types et la façon dont ils infectent les systèmes
- Expliquer les concepts de **virus**, leurs types et la façon dont ils infectent les fichiers
- Expliquer le concept de **vers** (computer worms)
- Expliquer les concepts de **fileless malware** et comment ils infectent les fichiers
- Expliquer les concepts de **malware basé sur l'IA**
- **Analyser un malware** (analyse statique et dynamique) et détecter la présence de malware
- Adopter des **contremesures** contre le malware

---

## Objectif 01 — Explain Malware and Advanced Persistent Threat (APT) Concepts

### 1.1 Qu'est-ce qu'un malware ?

Le **malware (malicious software)** est un programme créé pour endommager, perturber, voler ou obtenir un accès non autorisé à un système. Le terme couvre les **Trojans, backdoors, ransomwares, virus, vers, rootkits, PUAs, fileless malware et AI-based malware**.

**Indications d'une attaque par malware** : lenteur du système, messages d'erreur, programmes inconnus en cours d'exécution, connexions réseau suspectes, pop-ups, modification des paramètres, etc.

### 1.2 Techniques de propagation du malware

| Vecteur | Description |
|---|---|
| **Email** | Pièces jointes infectées, liens malveillants, phishing |
| **Téléchargements** | Logiciels piratés, cracks, keygens, « freeware » empoisonnés |
| **P2P / réseaux de partage** | Fichiers partagés infectés (torrents, partages de fichiers) |
| **Médias amovibles** | Clés USB, disques durs externes (autorun) |
| **Navigation web** | Drive-by downloads, pop-ups, publicités malveillantes (malvertising) |
| **Réseau** | Vers auto-propagés, exploitation de vulnérabilités SMB, etc. |
| **Social engineering** | Pièges via ingénierie sociale, faux logiciels de sécurité |

### 1.3 PUAs (Potentially Unwanted Applications) et adware

- **PUAs** : applications dont l'utilisateur ignore les fonctionnalités indésirables (souvent fournies en bundle avec un logiciel légitime). Ce sont des programmes que l'utilisateur aurait probablement choisi de ne pas installer s'il les avait connus.
- **Adware** : logiciel qui affiche des publicités automatiquement (pop-ups, bannières) sans le consentement de l'utilisateur, souvent installé en parallèle d'une autre application. Il collecte des données de navigation et ralentit le système.

### 1.4 Advanced Persistent Threats (APT)

Un **APT** est une **attaque réseau** dans laquelle un attaquant obtient un accès non autorisé à un réseau et **reste indétecté pendant une longue période** pour extraire des informations sensibles.

| Terme | Signification |
|---|---|
| **Advanced** | Utilisation de techniques sophistiquées exploitant des vulnérabilités (souvent zero-day) |
| **Persistent** | Système de **commande et contrôle (C&C)** externe qui extrait les données en continu et surveille le réseau |
| **Threat** | **Intervention humaine** dans la coordination de l'attaque |

**Objectifs des APT** : obtenir des informations sensibles — documents classifiés, identifiants, informations personnelles, transactions, cartes bancaires, propriété intellectuelle, données financières, stratégie commerciale, données de contrôle système, emails…

**Caractéristiques des APT** (selon Bodmer, Kilger, Jones, Carpenter) :
- **Objectives** : obtenir de façon répétée des données sensibles (gain illégal, espionnage politique/stratégique)
- **Timeliness** : rapide d'un point de vue technique, mais durable dans le temps
- **Resources** : moyens importants (compétences, réseaux, outils spécifiques)
- **Risk tolerance** : capable de risquer la détection, plusieurs tentatives jusqu'au succès
- **Skills & methods** : utilisent des vulnérabilités inconnues, dissimulent les traces, coordonnent les actions
- **Actions** : suivent plusieurs phases (reconnaissance, accès, exfiltration…)
- **Attack origination points** : ciblent des sites précis ; initialisation depuis des serveurs compromis
- **Numbers** : nombre de systèmes hôtes impliqués
- **Knowledge source** : publiques, commerciales ou acquises illégalement
- **Multiphased** : l'attaque suit plusieurs phases pour atteindre l'objectif
- **C&C infrastructure** : réseau sophistiqué de serveurs C&C, protocoles non conventionnels (IRC, HTTP, DNS…)
- **Militant** : traite un objectif précis, activité coordonnée
- **Persistent** : durée de vie longue (mois/années), présence maintenue

### 1.5 Cycle de vie d'une APT (APT Lifecycle)

| Phase | Actions |
|---|---|
| **1. Preparation** | Définir la cible, rechercher la cible, organiser l'équipe, construire/acquérir les outils, tester la détection |
| **2. Initial Intrusion** | Déploiement du malware, établissement d'une connexion sortante |
| **3. Persistence** | Maintenir l'accès (mécanismes de persistance) |
| **4. Expansion** | Étendre l'accès, obtenir des identifiants (compromission d'autres systèmes) |
| **5. Search and Exfiltration** | Rechercher les données cibles et les **exfiltrer** |
| **6. Cleanup** | Couvrir les traces, rester indétectable |

---

## Objectif 02 — Explain Trojan, Virus, and Worm Concepts

### 2.1 Qu'est-ce qu'un Trojan ?

Un **Trojan (cheval de Troie)** est un programme qui **se fait passer pour un logiciel légitime** mais qui, une fois exécuté, réalise des actions malveillantes (vol de données, contrôle à distance, destruction…). Il **ne se reproduit pas** et **ne peut pas s'exécuter tout seul** : il exige une action de l'utilisateur. Les chevaux de Troie peuvent être embarqués dans des jeux, animations, messages électroniques, sites web, etc.

**Modes d'infection** : téléchargements de jeux/applications, pièces jointes, clickers, browser hijackers, chevaux de Troie intégrés à des programmes « gratuits », etc.

### 2.2 Types de Trojans

| # | Type | Description |
|---|---|---|
| 1 | **Remote Access Trojans (RAT)** | Contrôle total du système victime (accès fichiers, captures écran/caméra, keylogging, exécution de commandes). Le Trojan agit comme un serveur qui écoute sur un port ; ex. **njRAT**, **Remcos RAT** (propagé via fichiers `.vhd` + scripts PowerShell) |
| 2 | **Backdoor Trojans** | Ouvrent une porte dérobée sur la machine victime |
| 3 | **Botnet Trojans** | Intègrent la machine à un botnet contrôlé par l'attaquant |
| 4 | **Rootkit Trojans** | Dissimulent la présence du malware au niveau du noyau |
| 5 | **E-Banking Trojans** | Volent les identifiants bancaires en ligne (ex. **Coyote**, Zeus, Emotet) |
| 6 | **Point-of-Sale (POS) Trojans** | Ciblent les terminaux de paiement pour voler les données de cartes |
| 7 | **Defacement Trojans** | Modifient l'apparence de sites web |
| 8 | **Service Protocol Trojans** | Utilisent un protocole de service pour communiquer |
| 9 | **Mobile Trojans** | Ciblent les smartphones/tablettes |
| 10 | **IoT Trojans** | Ciblent les objets connectés |
| 11 | **Security Software Disabler Trojans** | Désactivent les logiciels de sécurité (antivirus, firewall) |
| 12 | **Destructive Trojans** | Détruisent des fichiers/programmes |
| 13 | **DDoS Attack Trojans** | Utilisent la machine pour lancer des attaques DDoS |
| 14 | **Command Shell Trojans** | Fournissent un shell distant à l'attaquant |

### 2.3 RAT et reverse connections

Les **RAT** infectent via phishing, drive-by downloads, USB infectés ou lecteurs réseau. Le **reverse connection Trojan** établit une connexion **sortante** vers l'attaquant (souvent via le **port 80** ou **443**), ce qui **contourne les firewalls** qui bloquent les connexions entrantes. L'attaquant obtient alors 100 % de contrôle de la machine victime.

### 2.4 Ports utilisés par les Trojans (à retenir pour l'examen)

| Port | Trojan |
|---|---|
| 20/21 (FTP) | Back Construction, Blade Runner, Cattivik FTP Server |
| 22 | Shaft |
| 23 (Telnet) | NetBus, Fire Flies, The Spy |
| 25 (SMTP) | Antigen, Email Password Sender, Terminator |
| 53 (DNS) | Remote Administration Tool |
| 68 | Mspy |
| 69 (TFTP) | Passive Capture |
| 80 (HTTP) | Necurs, W32.Bobax, NetWire, Ratenjay, Virus.Agent, Subseven 2.2, Backdoor.HtRtk |
| 88 (Kerberos) | Krb_replay |
| 110 (POP3) | ProMail Trojan |
| 113 | Shiver |
| 119 (NNTP) | Happy99 |
| 135 | Windows Defender |
| 139 | Nuker, Dragonfly, GodMessage |
| 443 (HTTPS) | Carbanak, PlugX, Sockshill, TrickBot, Lazarus, RedLeaf, Wirenet, Trojan.Scieron, IcedID |
| 445 | WannaCry, Petya, NotPetya, EternalBlue |
| 456 | Hackers Paradise |
| 512 | BugBear |
| 513 | GrLogin |
| 555 | Ini-Killer, Stealth Spy |
| 666 | Satanz Backdoor, Dark FTP |
| 1001 | Silencer, WebEx |
| 1011 | Doly Trojan |
| 1024 | NetSpy |
| 1177 | (exemple d'activité malveillante relevée dans le cours) |
| 1243 | SubSeven |
| 1492 | FTP99CMP |
| 1509 | Psyber Stream Server |
| 1600 | Shivka-Burka |
| 1807 | SpySender |
| 2774 | SubSeven 2.1 |
| 2989 | Rat |
| 3129 | Masters Paradise |
| 3700 | Portal of Doom |
| 4092 | WinCrash |
| 4321 | BoBo |
| 5000 | UPX |
| 5550 | Xtcp |
| 5880 | Y3K RAT |
| 7000 | Remote Grab |
| 7300/7301/7306/7308 | NetMonitor |
| 7597 | Qaz |
| 7626 | Gdoor |
| 7777 | GodMsg |
| 8080 | Zeus, APT 37, Maazben |
| 8012 | Ptakks |
| 8443 | FELIXROOT |
| 8787 | BackOrifice 2000 |
| 9989 | iNi-Killer |
| 12345/12346 | NetBus |
| 20000 | Millenium |
| 31337/31338/31339 | Net Spy, Back Orifice |
| 54321 | BackOrifice 2000 |

### 2.5 HTTP RAT et ICMP Trojans

- **HTTP RAT** : Trojan qui se dissimule dans le trafic HTTP/HTTPS (port 80/443) pour échapper aux firewalls ; le trafic malveillant ressemble à de la navigation web légitime.
- **ICMP Trojans** : le payload est transporté dans les **messages ICMP echo request/echo reply** (ping) — technique de **tunneling ICMP** souvent utilisée pour exfiltrer des données ou établir un canal C2 invisible.

### 2.6 Backdoors

Une **backdoor (porte dérobée)** est un moyen de contourner l'authentification normale pour accéder à un système à distance. Elle peut être installée par un Trojan, un rootkit ou une vulnérabilité. Le malware ouvre des **ports** pour établir des connexions avec des systèmes, réseaux ou serveurs distants. Les backdoors peuvent aussi viser le **hardware** (firmware), laissant des vulnérabilités discrètes et persistantes.

### 2.7 Concepts de virus

Un **virus** est un code auto-réplicatif qui s'attache à un programme ou fichier légitime. Il **ne peut pas se lancer tout seul** (contrairement au ver) : il a besoin d'un **événement déclencheur** (exécution d'un programme infecté, pièce jointe, etc.). Il possède deux phases :
- **Infection phase** : le virus se charge en mémoire, cherche un exécutable, y **appende son code malveillant** (sans autorisation), et l'infection se propage aux autres programmes à chaque exécution.
- **Attack phase** : déclenchée par un événement (« trigger » ou « direct attack »), le virus attaque les programmes intégrés, l'antivirus, les fichiers de données, les paramètres de démarrage, etc.

### 2.8 Cycle de vie d'un virus

1. **Design** : développement du code (langage de programmation ou construction kit)
2. **Replication** : le virus se réplique dans le système cible puis se propage
3. **Launch** : activation lorsque l'utilisateur effectue une action (exécuter un programme infecté)
4. **Detection** : identification du virus par les outils de sécurité
5. **Incorporation** : intégration des défenses (mises à jour des signatures, correctifs)

### 2.9 Types de virus

| Type | Description |
|---|---|
| **System/Boot Sector Virus** | Infecte le secteur de démarrage (MBR) ; s'active au boot |
| **File Virus** | S'attache à un fichier exécutable |
| **Multipartite Virus** | Combine infection du boot sector et des fichiers |
| **Macro Virus** | Code dans les macros de documents Office |
| **Cluster Virus** | Modifie l'entrée du répertoire pour pointer vers le code viral |
| **Stealth/Tunneling Virus** | Se cache du système et intercepte les appels pour masquer son activité |
| **Encryption Virus** | Code chiffré avec une clé variable |
| **Sparse Infector Virus** | Infecte rarement pour rester discret |
| **Polymorphic Virus** | Change sa signature (déchiffreur muté) à chaque réplication |
| **Metamorphic Virus** | Réécrit entièrement son code pour ne jamais avoir deux copies identiques |
| **Overwriting File/Cavity Virus** | Écrase ou se cache dans les espaces libres d'un fichier |
| **Companion/Camouflage Virus** | Crée un fichier compagnon avec un nom ressemblant |
| **Shell Virus** | S'enveloppe autour du code hôte |
| **File Extension Virus** | Change les extensions de fichiers |
| **FAT Virus** | Corrompt la table FAT |
| **Logic Bomb Virus** | S'active à une date/événement précis |
| **Web Scripting Virus** | Code malveillant dans des scripts web (non-persistant → dans la mémoire du navigateur ; persistant → dans un fichier permanent sur le serveur) ; vol de cookies/session via XSS |
| **Email Virus** | Se propage par emails (envoi automatique aux contacts) |
| **Armored Virus** | Protégé contre l'analyse (anti-debug, anti-disassembly) |
| **Add-on Virus** | Ajoute son code à la fin du fichier hôte |
| **Intrusive Virus** | S'écrit dans le fichier hôte en le remplaçant partiellement |
| **Direct Action/Transient Virus** | S'exécute quand l'hôte est exécuté puis quitte |
| **TSR (Terminate and Stay Resident)** | Reste en mémoire après l'exécution de l'hôte |

**Virus hoaxes** : faux avertissements de virus propagés par emails — une perte de temps et un vecteur de désinformation. **Fake antivirus (rogueware)** : faux logiciels de sécurité qui prétendent détecter des infections pour escroquer l'utilisateur.

### 2.10 Ransomware

Le **ransomware** est un malware qui **restreint l'accès** aux fichiers/dossiers de la victime (chiffrement ou verrouillage) et **demande une rançon** pour les libérer. Il se propage souvent via les macros Office, phishing, SMB (WannaCry/Petya/NotPetya). Familles connues : **Mallox**, **STOP/Djvu**, **Qilin**, **GhostLocker 2.0** (GhostSec, chiffre les fichiers et ajoute l'extension `.ghost`, exfiltre les fichiers `.doc/.docx/.xls/.xlsx`, « double extorsion » : fuite des données + rançon). Outil de construction : **Chaos Ransomware Builder v4**.

### 2.11 Vers (Computer Worms)

Un **ver (worm)** est un logiciel malveillant qui **se propage automatiquement à travers le réseau** en exploitant des vulnérabilités, **sans intervention de l'utilisateur** (contrairement au virus). Il peut consommer la bande passante, créer des backdoors et transporter des payloads (ransomware, bots). Exemples : WannaCry, Stuxnet.

### 2.12 Outils de création de Trojans/virus et exemples

- **njRAT** : RAT permettant de générer un payload, établir une connexion persistante, exécuter des commandes, surveiller le bureau, enregistrer les frappes.
- **JPS Virus Maker** : outil de création de virus personnalisés (désactiver Task Manager, changer le mot de passe Windows, persistance…).
- **Trojan Horse Construction Kit** : kits de construction de chevaux de Troie.
- **Coyote** (banking trojan) : chargeur via **Squirrel installer** + application **NodeJS/Electron** + **Nim loader** (exécute un `.NET` en mémoire via le **CLR**), obfuscation des chaînes par **AES** (IV en tête de chaque bloc base64), persistance via `HKCU\Environment\UserInitMprLogonScript`, communication **C2 en SSL avec authentification mutuelle** (certificat), commandes à distance (capture d'écran, overlay d'une fausse app bancaire, tuer un processus, keylogger, déplacer le curseur, éteindre la machine…).

---

## Objectif 03 — Explain Fileless Malware Concepts

### 3.1 Qu'est-ce qu'un fileless malware ?

Le **fileless malware (malware sans fichier)** est un malware **non-fichier** : il réside dans la **mémoire (RAM)** et exploite les **outils légitimes du système** (living-off-the-land) — PowerShell, WMI, macros — sans rien écrire sur le disque, ce qui lui permet **d'échapper aux antivirus basés sur les signatures**.

**Comment il fonctionne** : injection dans des processus légitimes (explorer.exe, navigateurs), ou exécution directe depuis la mémoire ; aucune trace sur le disque dur.

### 3.2 Taxonomie des menaces fileless (Microsoft)

Selon les **traces laissées** sur la machine victime :

| Type | Description | Exemple |
|---|---|---|
| **Type 1 — No File Activity** | Aucun fichier écrit sur le disque | Paquets malveillants exploitant une vulnérabilité → backdoor dans la **mémoire du noyau** ; code malveillant dans le **firmware** |
| **Type 2 — Indirect File Activity** | Utilisation indirecte de fichiers, mais présence fileless | Injection d'une commande PowerShell dans le **dépôt WMI** pour configurer un filtre d'exécution périodique |
| **Type 3 — Required Files to Operate** | Des fichiers sont nécessaires, mais l'attaque ne s'exécute pas depuis ces fichiers | Document avec **macro/Java/Flash/EXE** qui injecte un payload en mémoire puis maintient la persistance sans fichiers |

**Classification par point d'entrée :**
- **Exploits** : file-based (exploitent exécutables, Flash, Java, documents → shellcode → payload en mémoire) ou network-based (vulnérabilités de protocoles réseau comme **SMB**)
- **Hardware** : firmware des cartes réseau/disques, CPU (firmware de management), **USB** (firmware réécrit), BIOS, **hyperviseur**
- **Execution and Injection** : file-based (EXE/DLL/LNK), macro-based, script-based (PowerShell), disk-based (réécriture du boot record)

### 3.3 Vecteurs d'attaque fileless

| Vecteur | Description |
|---|---|
| **Document Exploits** | Exploitation de vulnérabilités de documents (Word, Flash, Adobe PDF Reader) pour exécuter un script |
| **In-Memory Exploits** | Exploitation directe en mémoire (aucun fichier sur le disque) |
| **Script-based Injection** | Injection de scripts malveillants (JavaScript, PowerShell, VBScript) dans la mémoire |
| **Exploitation of System Admin Tools** | Abus des outils d'administration légitimes (PowerShell, WMIC, WMI, AppLocker…) — technique **living-off-the-land (LOL)** |
| **Phishing** | Emails de phishing exécutant des scripts/macros |
| **Windows Registry** | Manipulation du registre pour exécuter du code (clés `Run`, `RunOnce`, etc.) |

### 3.4 Techniques d'obfuscation fileless (pour contourner l'antivirus)

Chiffrement, encodage (base64), compression, injection dans des processus légitimes, abus des outils système, suppression des traces après exécution, exploitation des **LOLBins** (living-off-the-land binaries).

### 3.5 Exemple réel : PyLoose

**PyLoose** (découvert mi-2023 via le Wiz Runtime Sensor) est un **malware fileless Python** ciblant les **workloads cloud** (conteneurs, Jupyter Notebook mal configuré) pour du **cryptomining Monero** (XMRig) :
- **Stage 1 (Pre-exploitation)** : accès via un service **Jupyter Notebook** public avec des restrictions de commandes inadéquates ; téléchargement du payload depuis un service de partage (paste.c-net.org) via **HTTPS GET** — aucun fichier écrit sur le disque.
- **Stage 2 (Exploitation)** : décodage **base64** + décompression **zlib**, puis **chargement direct en mémoire** via le descripteur `memfd_create` (syscall 319, flags MFD_CLOSEXEC) — script de 9 lignes (`fileless-elf-exec`), argv[0] = `smd`.
- **Stage 3 (Post-exploitation)** : connexion du mineur **XMRig v6.19.3** aux pools **MoneroOcean** ; les fonds sont transférés vers le wallet Monero de l'attaquant.
- **IOCs** : hashes SHA-1/SHA-256/MD-5 du loader et du payload, endpoints des pools (`51.75.64.249:20128`, `gulf.moneroocean.stream`…), adresse de wallet Monero.

---

## Objectif 04 — Explain AI-based Malware Concepts

### 4.1 Qu'est-ce qu'un malware basé sur l'IA ?

Le **AI-based malware** utilise l'**intelligence artificielle** — machine learning, deep learning, traitement du langage naturel (NLP) — pour **apprendre de son environnement**, **s'adapter** et **échapper à la détection**. Il peut choisir dynamiquement la meilleure technique d'attaque, imiter des comportements légitimes et auto-modifier son code.

**Flux de fonctionnement** : **Infiltration** (entrée sur le système) → **Establishment** (mise en place de la présence et du C2) → **Exécution** des objectifs malveillants.

### 4.2 Indicateurs de malware basé sur l'IA

- Comportement anormal et imprévisible
- Capacité à générer des variantes/polymorphisme dynamique
- Adaptabilité aux réponses des défenses (feedback loop)
- Utilisation de modèles ML/DL/NLP pour cibler les victimes (ingénierie sociale personnalisée)

### 4.3 Techniques utilisées dans le développement

Machine learning (classification, clustering), deep learning (réseaux de neurones profonds, ANN/RNN), NLP (phishing et spear-phishing générés), modèles génératifs (contenu légitime imité).

### 4.4 Exemple réel : FakeGPT

**FakeGPT** (Guardio Labs, 2023) est une campagne de **malvertising** exploitant la popularité de **ChatGPT** via une **extension Chrome malveillante** (« Quick access to Chat GPT ») :
1. **Discovery and Propagation** : diffusion via **posts sponsorisés Facebook**
2. **Malvertising and Installation** : l'extension collecte les **cookies des sessions actives** et vole les comptes Facebook
3. **Abusing Browser Context** : abus de la **Meta Graph API** pour agir au nom de l'utilisateur
4. **Circumventing Security Measures** : manipulation du **declarativeNetRequest API de Chrome** pour falsifier les en-têtes (les requêtes semblent provenir de facebook.com) — aucun trace
5. **Data Harvesting and Exfiltration** : collecte des données (comptes, soldes, cookies…) et envoi au **C2** via une série d'API
6. **Account Takeover** : enregistrement automatique d'une **application Facebook rogue** avec des permissions étendues (contrôle admin total)
7. **Propagation to Other Accounts** : armée de **bots Facebook** autopropagés, publicités payées avec les ressources des victimes

---

## Objectif 05 — Demonstrate Malware Analysis Process

### 5.1 Introduction à l'analyse de malware

L'analyse de malware vise à comprendre **l'intention malveillante** et le **comportement** d'un programme pour : identifier des **IOCs**, répondre à des questions métier (comment l'attaque s'est produite, quelles données ont été volées, comment détecter), développer des contre-mesures et des signatures de détection.

**Types d'analyse** :
- **Static Malware Analysis** : examen du binaire **sans exécution** (structure du fichier, métadonnées, imports, chaînes, signatures)
- **Dynamic Malware Analysis** : **exécution contrôlée** (VM, sandbox) pour observer le comportement (fichiers créés, ports, URLs, processus, services, registre, réseau…)

### 5.2 Guidelines pour l'analyse

- Analyser dans un **environnement isolé** (machines virtuelles, sandboxes) pour éviter la propagation
- Capturer chaque mouvement du malware (outils de monitoring)
- Utiliser plusieurs outils et croiser les résultats
- Ne **jamais** exécuter le malware sur le réseau de production ; utiliser des snapshots pour restaurer l'environnement

### 5.3 Analyse statique

| Technique | Description / Outils |
|---|---|
| **File fingerprinting (empreinte)** | Calcul des hashes **MD5, SHA-1, SHA-256** pour identifier le fichier ; outils : `md5sum`/`sha1sum`/`sha256sum`, HashCalc, HashMyFiles |
| **Inspection du format PE** | Vérifier s'il s'agit d'un exécutable PE valide ; détecter le **packing** (UPX…) ; outils : **Detect It Easy (DIE)**, PEiD, Pestudio |
| **Recherche de chaînes (strings)** | Extraction des chaînes lisibles (URLs, IP, noms de fichiers, instructions) ; outils : `strings`, BinText |
| **Vérification des antimalwares** | Multi-scanners en ligne (VirusTotal, **Hybrid Analysis**) |
| **Disassembly / Reverse engineering** | Analyse des instructions assembleur et du flux de contrôle ; outils : **IDA**, **OllyDbg**, Ghidra |
| **Dependency Walker** | Affiche l'arbre hiérarchique des **DLL importées** : `WSock32.dll` (ancienne API réseau), `Ws2_32.dll` (API Winsock moderne), `Wininet.dll` (fonctions réseau de haut niveau) — des imports réseau anormaux signalent un comportement malveillant |
| **Analyse des documents Office (OLE)** | Suite **oletools** : `oleid` (composants suspects, macros VBA), `oledump` (streams contenant des macros — marqués « M »), `olevba` (code source des macros, keywords suspects AutoOpen/URLDownloadToFileA, **IOCs** comme `http://…/test.exe`), `mraptor` |
| **Analyse des PDF** | **PDFiD** (mots-clés et types d'objets suspects, JavaScript), **PDFStreamDumper** (inspection et extraction des streams/objets, Exploits Scan → détection d'exploits comme **CVE-2008-2992 util.printf**), puis recherche sur https://www.cve.org |
| **Règles YARA** | Détection par **pattern matching** (chaînes texte, hexadécimales, regex) ; structure d'une règle : `rule` header (nom + tags), `meta:` (métadonnées), `strings:` (chaînes), `condition:` (logique) ; commande : `yara <rulefile.yar> <suspicious file>` |

### 5.4 Analyse dynamique

L'analyse dynamique exécute le malware dans un environnement sûr et comprend **deux étapes** : **System Baselining** (snapshot de l'état du système avant exécution) et **Host Integrity Monitoring** (comparaison avec l'état après exécution avec les mêmes outils).

| Domaine de monitoring | Outils / Commandes |
|---|---|
| **Port Monitoring** | `netstat` (`-a` toutes connexions/ports en écoute, `-e` statistiques Ethernet, `-n` adresses numériques, `-o` PID, `-p` protocole, `-r` table de routage, `-s` statistiques par protocole), **TCPView** (tous les endpoints TCP/UDP + Tcpvcon CLI), **CurrPorts**, TCP Port/Telnet Monitoring, PRTG, SolarWinds Open Port Scanner |
| **Process Monitoring** | **Process Monitor** (fusion de Filemon + Regmon : activité temps réel fichiers/registre/processus/threads, filtres, thread stacks), **Process Explorer**, OpManager, Monit, ESET SysInspector, System Explorer |
| **Registry Monitoring** | Clés exécutées automatiquement : `Run`, `RunServices`, `RunOnce`, `RunServicesOnce`, `HKEY_CLASSES_ROOT\exefile\shell\open\command` ; outils : **jv16 PowerTools** (Registry Cleaner, Duplicate Finder), Reg Organizer, Registry Viewer, **RegScanner**, regshot |
| **Windows Services Monitoring** | Le malware s'installe en **service** (souvent en **SERVICE account**) et manipule `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services` ; outils : **SrvMan (Windows Service Manager)** — `srvman.exe add/delete/start/stop/restart/run` —, Netwrix Service Monitor, AnVir Task Manager, Service+, Advanced Windows Service Manager, Process Hacker |
| **Startup Programs Monitoring** | Vérifications manuelles : registre (Windows/Explorer/Microsoft Edge startup settings), `C:\Windows\System32\drivers`, `bcdedit` (bootmgr), `services.msc` (trier par Startup Type), dossiers Startup (`C:\ProgramData\…\Start Menu\Programs\Startup`, `%AppData%\…\Startup` ou `shell:startup`) ; outil : **Autoruns for Windows** (option *Hide Signed Microsoft Entries*), WinPatrol, Autorun Organizer, Quick Startup, StartEd Pro |
| **Event Logs Monitoring** | **Event Viewer** : Windows Logs (System, Security…), Applications and Services Logs ; outil SIEM : **Splunk** (forwarders → dashboard), ManageEngine Event Log Analyzer, Solarwinds Loggly, Netwrix Event Log Manager, New Relic |
| **Installation Monitoring** | Détection des installations cachées du malware ; outils : **Mirekusoft Install Monitor**, SysAnalyzer, Advanced Uninstaller PRO, REVO Uninstaller PRO, Comodo Programs Manager |
| **Files and Folders Monitoring** | Intégrité des fichiers/dossiers modifiés par le malware ; outils : **PA File Sight** (détecte/bloque le ransomware réseau), **Tripwire**, Netwrix Auditor, Verisys, CSP File Integrity Checker, NNT Change Tracker |
| **Device Drivers Monitoring** | Vérification des pilotes chargés (source des pilotes non fiables) ; chemin : `Run > msinfo32 > Software Environment > System Drivers` ; outil : **DriverView** (adresse de chargement, description, version, éditeur), Driver Booster, Driver Reviver, Driver Easy, Driver Fusion, Driver Genius |
| **Network Traffic Monitoring** | Capture du trafic réseau du malware ; outils : **Wireshark**, **SolarWinds NetFlow Traffic Analyzer**, **Capsa (Colasoft) Network Analyzer**, PRTG, GFI LanGuard, insightIDR |
| **DNS Monitoring** | Vérification des serveurs DNS contactés (malware type **DNSChanger** modifie les paramètres DNS) ; outil : **DNSQuerySniffer** (queries DNS, type A/AAAA/NS/MX…), DNSstuff, UltraDNS, Sonar Lite, DNSCheck, Dotcom-Monitor |
| **API Calls Monitoring** | Traçage des appels Win32 API (interaction avec l'OS : fichiers, registre, réseau, noyau) ; outil : **API Monitor**, API Call Monitoring, Runscope, AlertSite |
| **System Calls Monitoring** | Interface application ↔ noyau ; outil Linux : **strace** — `strace -p <PID>` (attacher à un processus), `strace -P <path> ls /var/empty` (syscalls sur un chemin), `strace -c ls` (compte temps/appels/erreurs), `strace -o out.txt ./<sample>` (sortie fichier) |
| **Scheduled Tasks Monitoring** | Détection des **logic bombs** / tâches déclenchées par date/événement ; outils : `schtasks`, Windows Task Scheduler, ADAudit Plus, CronitorCLI, SolarWinds Windows Scheduled Task Monitor |
| **Browser Activity Monitoring** | Les malwares utilisent le navigateur pour joindre les **C&C** via les **ports 80/443/8080** ; vérifier caches web, logs, filtrage URL ; outils : **Wireshark**, **Colasoft Portable Network Analyzer**, OmniPeek, Observer Analyzer, NetFlow Analyzer |

### 5.5 Méthodes de détection de virus

| Méthode | Description |
|---|---|
| **Scanning** | Recherche des **signatures** (chaînes caractéristiques) du virus ; ne détecte que les virus **connus** ; avantages : vérifie avant exécution ; inconvénients : obsolescence rapide des scanners |
| **Integrity Checking** | Lecture/enregistrement des données intégrées pour créer une **signature/baseline** des fichiers et secteurs ; inconvénient : ne différencie pas corruption par bug vs par virus |
| **Interception** | Intercepte les requêtes de l'OS (accès réseau, actions dangereuses) et demande confirmation ; objectif : dévier **logic bombs** et **Trojans** |
| **Code Emulation** | Exécution du code suspect dans une **machine virtuelle** (mimétisme CPU/mémoire) ; très efficace contre les virus **chiffrés et polymorphes** ; inconvénient : lent si la boucle de déchiffrement est longue ; détecte aussi les virus **métamorphes** |
| **Heuristic Analysis** | Détecte les virus **inconnus** (variantes) ; **statique** = analyse du format du fichier et de la structure du code ; **dynamique** = émulation du code suspect ; inconvénient : **faux positifs** |

### 5.6 Emulation et instrumentation de code

- **Malware code emulation** : crée un environnement virtuel isolé (processeur, mémoire, disque, réseau, registre) pour exécuter le malware avec contrôle total (breakpoints) ; moins de ressources qu'une sandbox ; outils : **Kaspersky Lab emulator**, **Unicorn**, **QEMU**, **SCEMU** (émulateur x86 32/64 bits, 2 M d'instructions/s, bibliothèque iced-x86 Rust), **Speakeasy**, Windows_Malware_Emulator
- **Malware code instrumentation** : injection de code à des points précis du binaire pour journaliser les événements (appels de fonctions, allocations mémoire, communications réseau) en temps réel ; outils : **Frida**, **HawkEye** (basé sur Frida ; modes : spawn d'un échantillon ou hook d'un PID ; rapport web)

### 5.7 Exemples complets d'analyse (études de cas du cours)

| Malware | Faits marquants |
|---|---|
| **Coyote** (banking trojan) | Chargeur **Squirrel installer** (package NuGet) → app NodeJS/Electron (preload.js obfusqué) → **Nim loader** → exécution d'un `.NET` en mémoire via **CLR** ; persistance via `HKCU\Environment\UserInitMprLogonScript` ; obfuscation des chaînes par **AES** ; C2 en **SSL (authentification mutuelle)** ; commandes : screenshot, overlay fausse app bancaire, kill process, keylogger, déplacement curseur, shutdown |
| **GhostLocker 2.0** (ransomware GhostSec) | Écrit en **Golang** ; extension `.ghost` ; **RaaS** avec panel C2 (`94[.]103[.]91[.]246`) ; **double extorsion** ; exfiltration `.doc/.docx/.xls/.xlsx` via `/upload` ; persistance dans le dossier **Startup** (fichier 32 octets aléatoires) ; JSON d'infection envoyé à `/addinfection`, exécution `/incrementLaunch` ; évite le dossier `C:\Windows` pendant le chiffrement ; note de rançon `Ransomnote.html` |
| **PyLoose** (fileless) | Python, cloud/Jupyter, `memfd_create`, XMRig, pools MoneroOcean, wallet Monero |
| **FakeGPT** (AI-based) | Extension Chrome, malvertising Facebook, Graph API, declarativeNetRequest, vol de comptes/annonces |

---

## Objectif 06 — Explain Malware Countermeasures

### 6.1 Contremesures générales contre le malware

- Ne pas ouvrir les pièces jointes de sources inconnues
- **Bloquer tous les ports inutiles** au niveau de l'hôte + firewall
- Éviter les téléchargements depuis des sources non fiables et les programmes échangés par messagerie instantanée
- **Durcir les configurations** par défaut faibles, désactiver les fonctionnalités/protocoles/services inutilisés
- Surveiller le trafic réseau interne (ports anormaux, trafic chiffré)
- **Installer les patches et mises à jour** de sécurité de l'OS et des applications
- Restreindre les permissions du bureau, vérifier l'intégrité des fichiers (checksums, audit, port scanning)
- Utiliser un antivirus, firewall et IDS basés sur l'hôte ; activer les protections mémoire (**DEP**, **ASLR**)
- Désactiver **AutoRun** pour les périphériques externes ; vérifier l'authenticité **SSL** des sites e-commerce
- Passer par un FAI avec anti-spam robuste ; ne pas cliquer sur les pop-ups non sollicités
- Mots de passe forts et uniques, changés régulièrement ; extensions de sécurité du navigateur

### 6.2 Contremesures contre les Trojans

Mêmes mesures générales + : ne pas accepter de programmes par messagerie instantanée, éviter le P2P, déployer des **host-based IDS/IPS** (surveillance des modifications de fichiers et injections de processus), utiliser la **FIM** (file integrity monitoring), activer **DEP/ASLR**, installer des solutions anti-Trojan (voir 6.8).

### 6.3 Contremesures contre les backdoors

- Antivirus commerciaux (scan automatique des backdoors avant dommage)
- Éduquer les utilisateurs ; éviter les logiciels non fiables ; firewall sur chaque appareil
- Inspecter les paquets réseau avec des **outils de monitoring de protocoles**
- Si infection : redémarrer en **mode sans échec avec réseau**, exécuter des outils de **monitoring du registre**, supprimer le programme installé, les entrées de registre malveillantes et les fichiers liés
- Activer l'**auto-update** ; analyser les backdoors **hardware** (pipeline emission analysis), éviter le matériel de sources douteuses
- **FIM** sur les fichiers/systèmes critiques ; fermer les services et ports non requis

### 6.4 Contremesures contre les virus et vers

- Installer et **mettre à jour régulièrement** l'antivirus ; politique antivirus distribuée au personnel
- Scans réguliers planifiés de tous les lecteurs ; **sauvegardes de données régulières**
- Ne pas ouvrir les pièces jointes inconnues ; ne pas accepter de disques/programmes non vérifiés
- **Popup blockers** + firewall Internet ; nettoyage du disque et scan du registre hebdomadaire
- Anti-spyware/anti-adware hebdomadaire ; ne pas ouvrir les fichiers à **double extension**
- Filtre email efficace ; **désactiver AutoRun** ; mots de passe forts et uniques changés périodiquement

### 6.5 Contremesures contre le fileless malware

- Restreindre PowerShell/WMI (désactiver quand inutilisé) ; **Windows AppLocker / Group Policy**
- Désactiver les **macros** (uniquement macros signées de confiance) ; désactiver le **JavaScript des lecteurs PDF** et **Flash**
- **Whitelisting** d'applications (ex. McAfee Application Control) ; **2FA** pour les systèmes critiques
- **Sécurité multi-couches** pour les malwares résidents en mémoire ; **UBA** (User Behavior Analytics)
- Détecter les scripts PowerShell/WMIC masqués (dossiers TEMP) ; NGAV (ML/AI), **EPP** avancés
- MDR (Managed Detection and Response) ; outils : **Blackberry Cylance**, **Microsoft EMET**, **AITFS**
- Endpoint security avec monitoring actif ; segmentation du réseau ; audit des changements de comportement vs baselines

### 6.6 Contremesures contre l'AI-based malware

- Scanner les motifs anormaux (transmissions de données inhabituelles, modifications système)
- Déployer des solutions **alimentées par l'IA** : **NGAV**, **EDR**, **NTA** (network traffic analysis)
- Méthodes de détection d'anomalies (analyse statistique, clustering, apprentissage non supervisé)
- **Explainable AI (XAI)** pour la transparence des solutions ; réponses automatisées (threat hunting, orchestration)
- Conformité (GDPR, HIPAA, NIST) ; SOC doté d'outils avancés ; flux de **threat intelligence** ; formation des employés

### 6.7 Contremesures contre l'adware et les APT

- **Adware** : antimalware réputé à jour, mises à jour OS/applications, sources de téléchargement fiables, installation **personnalisée** (décocher les bundles), ad blockers, scans réguliers, **lecture des EULA**, nettoyage système, désinstallation des programmes non autorisés.
- **APT** : **zero-trust**, évaluations de risques régulières, **segmentation réseau** (limiter le mouvement latéral), NGAV/EDR, sécurité email (**SPF/DKIM/DMARC**), **threat hunting proactif**, chiffrement des données (au repos et en transit), **DLP**, MFA, monitoring continu du réseau, **SIEM** + détection d'anomalies, **déception** (honeypots/décoys).

### 6.8 Anti-malware software

- **Anti-Trojan** : **Avast One** (protection temps réel Trojans/ransomware/rootkits, VPN, optimisation), Bitdefender Total Security, Panda Dome, Norton 360, G DATA Total Security, TotalAV, Surfshark Antivirus, NordVPN Threat Protection, Sophos, Trend Micro Maximum Security, Malwarebytes, Avira, Emsisoft, HitmanPro
- **Antivirus** : méthodes **génériques** (recherche d'un comportement « virus-like », faux positifs possibles) vs **spécifiques** (signatures connues) ; exemples : **McAfee Total Protection** (antivirus, firewall, antispam, VPN, File Shredder, protection d'identité), Kaspersky Anti-Virus, Norton AntiVirus Plus, Bitdefender Antivirus Plus, Avast Premier, Intego, TotalAV Pro, Webroot SecureAnywhere, ESET Internet Security, Avira Pro, Panda Total Protection

### 6.9 Outils de détection et de protection contre le fileless malware

- **Détection** : **Cynet NGAV** (détection/stoppe fileless, ransomware, zero-day ; ML non supervisé ; monitoring des processus), Apex One (Trend Micro), Cortex XDR (Palo Alto), ManageEngine NGAV, Kaspersky Total Security, Xcitium Advanced (EPP+EDR)
- **Protection** : **Microsoft Defender for Endpoint** (utilise l'**AMSI** — Antimalware Scan Interface — pour les attaques script-based ; ML cloud), FortiEDR, Kaspersky Endpoint Security for Business, **Sophos Intercept X**, CylanceENDPOINT (Blackberry), IBM Security QRadar EDR

### 6.10 Outils de détection/analyse de malware alimentés par l'IA

- **Malware.AI** : convertit les fichiers en **images** analysées par **deep learning** (détection sans signature) ; étapes : upload → comparaison aux campagnes → analyse heuristique statique → réduction dimensionnelle → découpage en chunks → application de l'IA → amplification des prédictions → classification finale (score de malveillance) → retour à l'utilisateur
- Autres : Sophos Intercept X, Elastic Security, Bitdefender GravityZone, Vipre Endpoint Security, Webroot SecureAnywhere

### 6.11 Outils EDR/XDR

L'**EDR** (Endpoint Detection and Response) surveille/détecte/répond aux menaces sur les endpoints ; l'**XDR** (Extended Detection and Response) étend à plus de couches (réseau, email, cloud).

- **CrowdStrike Falcon Insight XDR** (détection alimentée par l'IA, faible taux de faux positifs, compatible Windows/Chrome OS/macOS/Linux)
- Microsoft Defender for Endpoint, Tanium Endpoint Management, Cisco XDR, Trellix Endpoint Security (ENS), VMware Carbon Black

---

## Aide-mémoire examen (à retenir absolument)

- **Malware** = logiciel malveillant ; **PUAs** = applications potentiellement indésirables ; **adware** = publicités automatiques.
- **APT** : accès non autorisé **durable et furtif** ; « advanced » = techniques sophistiquées/zero-day, « persistent » = C&C externe, « threat » = intervention humaine. Cycle de vie : **Preparation → Initial Intrusion → Persistence → Expansion → Search & Exfiltration → Cleanup**.
- **Trojan** : programme qui se fait passer pour légitime, **ne se reproduit pas**, nécessite une action utilisateur ; 14 types (RAT, backdoor, botnet, rootkit, e-banking, POS, defacement, service protocol, mobile, IoT, security disabler, destructive, DDoS, command shell).
- **RAT** : contrôle total de la victime ; **reverse connection** via port 80/443 pour contourner les firewalls ; outil **njRAT**.
- **Ports des Trojans** (indispensables) : **80** (Necurs, NetWire, Subseven 2.2), **443** (Carbanak, PlugX, TrickBot, Lazarus, IcedID), **445** (WannaCry/Petya), **666** (Satanz), **1001** (Silencer/WebEx), **8080** (Zeus), **8787/54321** (BackOrifice 2000), **12345/12346** (NetBus), **31337** (Net Spy/Back Orifice), **7000** (Remote Grab), **7626** (Gdoor).
- **HTTP RAT** = trafic web ; **ICMP Trojan** = payload dans les messages ping (tunneling ICMP).
- **Virus** : auto-réplicatif, s'attache à un hôte, **ne démarre pas seul** (événement déclencheur) ; cycle de vie : **Design → Replication → Launch → Detection → Incorporation** ; phases d'infection et d'attaque.
- Types de virus à connaître : **boot sector, file, multipartite, macro, polymorphique, métamorphe, stealth/tunneling, encryption, web scripting (persistant/non-persistant), email, logic bomb, TSR, companion**.
- **Ver (worm)** : se propage seul via le réseau (packet malware), sans intervention utilisateur.
- **Ransomware** : restriction d'accès + rançon ; WannaCry/Petya (445), GhostLocker 2.0 (`.ghost`, RaaS, double extorsion, GhostSec).
- **Fileless malware** : réside en **mémoire**, exploite les outils légitimes (PowerShell/WMI), **living-off-the-land** ; types 1/2/3 (traces laissées) ; vecteurs : documents, in-memory, scripts, outils admin, phishing, registre ; exemple **PyLoose** (memfd_create → XMRig).
- **AI-based malware** : ML/DL/NLP ; flux **Infiltration → Establishment** ; exemple **FakeGPT** (extension Chrome, Graph API Facebook).
- **Analyse statique** (sans exécution) : hashes MD5/SHA-1/SHA-256, **Detect It Easy**, strings, **Dependency Walker** (WSock32.dll/Ws2_32.dll/Wininet.dll), **oletools** (oleid/oledump/olevba), **PDFiD/PDFStreamDumper**, règles **YARA** (`rule/meta/strings/condition`).
- **Analyse dynamique** (exécution contrôlée) : **System Baselining + Host Integrity Monitoring** ; outils par domaine : `netstat`/**TCPView**/CurrPorts (ports), **Process Monitor** (processus), **jv16 PowerTools** (registre), **SrvMan** (services), **Autoruns** (démarrage), **Splunk** (logs), **Mirekusoft** (installation), **Tripwire/PA File Sight** (fichiers), **DriverView** (pilotes), **Wireshark/NetFlow** (réseau), **DNSQuerySniffer** (DNS), **API Monitor** (APIs), **strace** (syscalls Linux), `schtasks` (tâches), Wireshark (activité navigateur, ports 80/443/8080).
- Détection de virus : **Scanning, Integrity Checking, Interception, Code Emulation, Heuristic Analysis** (statique/dynamique).
- **Code emulation** (SCEMU, QEMU, Unicorn) vs **instrumentation** (Frida, HawkEye).
- Contremesures clés : firewall + ports bloqués, patches, **DEP/ASLR**, désactiver macros/PowerShell/AutoRun, **whitelisting**, **AppLocker**, 2FA, FIM, NGAV/EDR/XDR, **AMSI** (Defender), zero-trust + segmentation (APT), SPF/DKIM/DMARC, honeypots.
- Outils marquants : **Avast One** (anti-Trojan), **McAfee Total Protection** (antivirus), **Cynet NGAV** / **Microsoft Defender for Endpoint** (fileless), **Malware.AI** (IA, deep learning sur images), **CrowdStrike Falcon Insight XDR** (EDR/XDR).

## Synthèse du module

Ce module a couvert l'ensemble des **menaces liées aux malwares** :

1. **Concepts de malware et APT** : définition, propagation, PUAs/adware, indicateurs de compromission, caractéristiques des APT et leur cycle de vie en six phases.
2. **Trojans, virus et vers** : les 14 types de Trojans (dont les RAT), la table des **ports** utilisés par les Trojans, les backdoors, les types de virus et leur cycle de vie, les vers, les ransomwares et les kits de construction (njRAT, JPS Virus Maker, Trojan Horse Construction Kit, Chaos Ransomware Builder) ; études de cas (Coyote, Remcos RAT, GhostLocker 2.0).
3. **Fileless malware** : taxonomie Microsoft (types 1/2/3), points d'entrée (exploits, hardware, exécution/injection), vecteurs (documents, mémoire, scripts, outils d'administration, phishing, registre), obfuscation et étude de cas **PyLoose**.
4. **AI-based malware** : techniques ML/DL/NLP, indicateurs, et étude de cas **FakeGPT** (extension Chrome/Facebook).
5. **Analyse de malware** : méthodologie statique (hashes, DIE, strings, Dependency Walker, oletools, PDFiD/PDFStreamDumper, YARA) et dynamique (baselining + host integrity monitoring, avec les outils de monitoring par domaine), méthodes de détection de virus, émulation/instrumentation de code et analyses détaillées (Coyote, GhostLocker 2.0, PyLoose, FakeGPT).
6. **Contremesures** : contre Trojans, backdoors, virus/vers, fileless, AI-based, adware et APT, ainsi que les familles d'outils de défense (anti-Trojan, antivirus, détection/protection fileless, outils IA et EDR/XDR).

Le prochain module abordera le **sniffing** (Module 08) — comment les attaquants et les pentesters collectent des informations sur une cible.
