# Module 06 — System Hacking (CEH v13)

> Notes de cours en français basées sur le support officiel **CEH v13 — Module 06 : System Hacking** (EC-Council, 312-50).
> Révision pour l'examen CEH : les quatre phases du système hacking (gaining access, escalating privileges, maintaining access, covering tracks), cracking de mots de passe et attaques d'authentification (Kerberos, NTLM, LLMNR/NBT-NS), élévation de privilèges (DLL/Dylib hijacking, UAC, services, buffer overflows), maintien de l'accès (backdoors, spyware, rootkits, stéganographie, persistance, domination du domaine) et effacement des traces (logs, anti-forensique).

---

## Objectifs d'apprentissage

- Démontrer différentes techniques de **cracking de mots de passe** et d'**exploitation de vulnérabilités** pour obtenir l'accès au système
- Utiliser différentes techniques d'**élévation de privilèges** pour obtenir des privilèges administratifs
- Utiliser différentes techniques pour **cacher les programmes malveillants** et maintenir un accès distant au système
- Démontrer des techniques pour **dissimuler les preuves de compromission**

**À la fin du module, vous saurez :**
- Comprendre le concept de System Hacking (les 4 étapes : Gaining Access, Escalating Privileges, Maintaining Access, Clearing Logs)
- Décrire les techniques et outils de cracking de mots de passe (dictionnaire, brute-force, rainbow tables…)
- Expliquer les attaques sur les protocoles d'authentification (Kerberos, NTLM, LLMNR/NBT-NS)
- Utiliser les techniques d'élévation de privilèges Windows et Linux (DLL/Dylib hijacking, UAC, services misconfigurés, NFS, SUID, buffer overflow…)
- Décrire les outils de maintien d'accès : keyloggers, spyware, rootkits, stéganographie et stéganalyse
- Expliquer les techniques de persistance et de domination du domaine (Pass-the-Hash, Golden/Silver Ticket, skeleton key, AdminSDHolder)
- Décrire les techniques d'effacement des traces et d'anti-forensique (auditpol, wevtutil, nettoyage BASH, dissimulation d'artefacts…)

---

## Objectif 01 — Gaining Access (Accès non autorisé au système)

### 1.1 Vue d'ensemble du System Hacking

La méthodologie de hacking CEH (CHM) décrite au Module 01 se décompose en **quatre étapes** appliquées au système :

| Étape | Objectif |
|---|---|
| **Gaining Access** | Crack de mots de passe, exploitation de buffer overflows, exploitation des vulnérabilités identifiées |
| **Escalating Privileges** | Obtention de privilèges administratifs à partir des identifiants collectés |
| **Maintaining Access** | Exécution de keyloggers, spyware et autres programmes malveillants ; dissimulation via rootkits, stéganographie, NTFS streams |
| **Clearing Logs** | Suppression des traces/tracks laissées dans le système |

### 1.2 Authentification Microsoft : stockage des mots de passe dans la SAM

- Windows stocke les mots de passe dans la base **SAM** (Security Accounts Manager) ou dans la base **Active Directory** (en environnement de domaine).
- Les mots de passe **ne sont jamais stockés en clair** : ils sont hachés puis stockés dans la SAM.
- Les mots de passe sont protégés par **SYSKEY** : une clé de 128 bits qui chiffre les informations de mots de passe de la SAM (réduit les attaques hors ligne).
- **NTLM** : protocole d'authentification réseau ; le hash NTLM peut être obtenu par des outils comme **pwdump7**, **fgdump** ou **Mimikatz** (lecture de la mémoire du processus **LSASS**).

**Outils d'extraction des hashes de mots de passe :**
- **pwdump7** — extrait les hashes LM et NTLM du fichier SAM
- **Mimikatz** — extrait mots de passe en clair, Kerberos tickets, hashes NTLM depuis la mémoire de LSASS
- **fgdump**, **DSiInternals**, **Hashcat (--dump)**…

### 1.3 Protocole Kerberos et attaques associées

Kerberos est le protocole d'authentification le plus utilisé pour les entités réseau (port **88/TCP**). Son fonctionnement implique :
- **KDC (Key Distribution Center)** et **TGS (Ticket Granting Service)**
- **TGT (Ticket Granting Ticket)** — délivré à l'authentification initiale
- **ST (Service Ticket)** — obtenu pour accéder à un service spécifique
- **Pre-authentication** — option de compte ; si désactivée, le compte devient vulnérable à l'**AS-REP Roasting**

**Attaques Kerberos notables :**

| Attaque | Description |
|---|---|
| **Kerberoasting** | Cracker les **TGS tickets** de comptes de service pour récupérer leurs mots de passe (souvent des comptes privilégiés). Utilise des outils comme **Rubeus**, **Kerbrute** |
| **AS-REP Roasting** | Cracker le **TGT** (encodé avec le hash NTLM de l'utilisateur) pour des comptes sans pré-authentification |
| **Pass-the-Ticket (PtT)** | Voler un TGT/ST valide et l'utiliser pour s'authentifier sans connaître le mot de passe |
| **Pass-the-Hash (PtH)** | Utiliser le hash NTLM volé pour s'authentifier (attaque par injection de hash) |
| **Overpass-the-Hash** | Utiliser le hash NTLM pour obtenir un TGT |
| **Golden Ticket** | Forger des TGT pour l'ensemble de l'AD en compromettant le compte **KRBTGT** (mimikatz : `lsadump::dcsync /user:krbtgt` puis `kerberos::golden`) ; l'attaquant définit lui-même la validité du ticket |
| **Silver Ticket** | Forger un ST pour un service spécifique avec le hash NTLM du compte de service |

### 1.4 Techniques de cracking de mots de passe

**Types d'attaques sur les mots de passe :**

| Type | Exemples |
|---|---|
| **Non-électroniques** | Shoulder surfing, social engineering, dumpster diving |
| **Actives en ligne** | Trojan/Spyware/Keylogger, injection de hash (PtH), phishing, **password spraying**, LLMNR/NBT-NS poisoning, SMB Relay, downgrade attacks |
| **Passives en ligne** | Sniffing du réseau, MitM, rejeu (replay) |
| **Hors ligne (offline)** | Attaque par dictionnaire, rainbow tables, hybride, attaque par anniversaire (birthday), rule-based |
| **Mots de passe par défaut** | Devinés via les listes de mots de passe par défaut des fabricants |

**Techniques de cracking :**
- **Dictionary attack** — essai de chaque mot d'un dictionnaire (liste de mots courants) ; incorpore aussi les **mots de passe issus de data breaches** (réutilisation fréquente des mots de passe)
- **Password spraying** — utilisation de quelques mots de passe courants contre de nombreux comptes (évite les verrouillages de compte)
- **Brute-force attack** — essai systématique de toutes les combinaisons de caractères
- **Hybrid attack** — ajoute des caractères, nombres ou symboles aux mots du dictionnaire (ex. « password123 »)
- **Rule-based attack** — applique des règles de mutation (leetspeak, casse…) sur un dictionnaire
- **Markov attack** — exploite la probabilité de transition entre caractères
- **Combinator attack** — combine deux listes de mots
- **Rainbow table attack** — tables précalculées de hashes pour inverser les hachages (compromis temps/mémoire)
- **Birthday attack** — recherche de collisions de hachage (2^n/2 essais au lieu de 2^n)

### 1.5 Outils de cracking de mots de passe

| Outil | Description |
|---|---|
| **hashcat** | Cracker multi-mode (GPU) ; attaques brute-force, dictionnaire, masks, combinator |
| **John the Ripper** | Cracker de hashes polyvalent ; fichier de config `john.conf`, wordlists (ex. rockyou) |
| **L0phtcrack (LC7)** | Audit et récupération de mots de passe Windows (SNMP, Pwdump, hashes…) |
| **Ophcrack** | Cracking par tables rainbow (LM/NTLM) |
| **RainbowCrack** | Cracking par rainbow tables |
| **Cain & Abel** | Récupération de mots de passe (crack, sniffing, replay…) |
| **THC-Hydra** | Attaques de connexion en ligne (spraying, brute-force de services distants) |
| **Ncrack** | Cracker d'authentification haute performance (réseau) |
| **Medusa** | Brute-force parallèle de services distants |
| **Kerbrute** | Énumération et attaque brute-force Kerberos |
| **Elcomsoft Distributed Password Recovery** | Récupération distribuée de mots de passe |
| **hashes.org** | Base de données communautaire de hashes crackés |

**Commandes hashcat types :**
- Spécifier le mode : `-m` (ex. `-m 0` = MD5, `-m 1000` = NTLM)
- Spécifier l'attaque : `-a` (0 = straight, 3 = brute-force)
- Masques : `?l` (minuscules), `?u` (majuscules), `?d` (chiffres), `?s` (symboles), `?a` (tout)
- Exemple : `hashcat -a 3 -m 0 md5_hashes.txt ?l?l?l?d?d?d`
- Incrément : `-i --increment-min=6 --increment-max=10`

### 1.6 Attaques d'authentification réseau

**LLMNR / NBT-NS Poisoning :**
- LLMNR (port 5355/UDP) et NBT-NS (port 137/UDP) résolvent les noms en l'absence de DNS.
- L'attaquant **empoisonne** les réponses en se faisant passer pour la machine demandée → capture du hash NTLMv2 de la victime.
- Outil : **Responder**.

**SMB Relay Attack :**
- Le hash NTLMv2 capturé est **relayé** vers une autre machine (SMB) pour s'authentifier à sa place.
- Outil : `impacket-ntlmrelayx.py -of <dump SAM-NTLMv2> -tf <cibles>`.
- Contremesures : **SMB signing** (signature SMB) obligatoire.

**Downgrade Attack :**
- Forcer le passage à un protocole plus faible (ex. du protocole de chiffrement fort vers NTLMv1) pour faciliter le cracking.

**Internal Monologue Attack :**
- Variante de Mimikatz : obtention des hashes Net-NTLMv1/NTLM **sans toucher à la mémoire de LSASS** (évite Credential Guard et l'antivirus).

### 1.7 Keyloggers (enregistreurs de frappe)

Un keylogger enregistre **chaque frappe** de clavier, connecte l'utilisateur à un fichier, ou envoie les logs à l'attaquant.

| Type | Description |
|---|---|
| **Hardware keyloggers** | Placés entre le clavier et l'OS (connexion physique, câble, BIOS-based…) |
| **Software keyloggers** | Application installée ; types : basés sur noyau (kernel-based), basés sur hooks (hook-based), basés sur remplacement de DLL, clavier virtuel, keylogger BIOS |
| **Acoustic / Electromagnetic** | Analyse des sons de frappe ou des émissions électromagnétiques |
| **Keylogger par enregistrement d'écran** | Capture d'écrans régulière |

**Contremesures :** anti-keyloggers (détection comportementale), gestionnaire de mots de passe, authentification multifacteur, clavier virtuel.

### 1.8 Spyware

Le spyware est un programme installé à l'insu de l'utilisateur pour **collecter discrètement des informations** (frappes clavier, captures d'écran, historique…).

**Propagation du spyware :** drive-by download, installation de logiciels « piggybacked » (bundlés), usurpation d'anti-spyware, add-ons navigateur, exploitation de vulnérabilités du navigateur, cookies publicitaires.

**Ce que peut faire le spyware :** voler les informations personnelles, surveiller l'activité en ligne, afficher des pop-ups, rediriger le navigateur, voler les mots de passe, capturer l'écran, activer le microphone/webcam, distribuer des spams, collecter les configurations matériel/logiciel/réseau.

| Outil | Description |
|---|---|
| **Spytech SpyAgent** | Surveillance complète : keylogging, captures d'écran, suivi des applications et sites web, livraison des logs par email/FTP |
| **Spyrix Personal Monitor** | Enregistrement des frappes, captures d'écran, suivi des applications, mot de passe |

### 1.9 Dissimulation de fichiers

- **NTFS Alternate Data Streams (ADS)** : attacher des données cachées à un fichier légitime via le format `fichier:flux`. Détection avec **Stream Detector**, **LADS** ou **GMER**.
- **Stéganographie** : dissimuler des données dans des médias (détaillé en Objectif 03).
- **Attributs cachés** : utilisation de l'attribut « hidden » pour passer inaperçu.

### 1.10 Établissement de sessions à distance

Outils pour prendre le contrôle du système compromis :
- **RDP** (Remote Desktop Protocol) et clients RDP
- **PsExec** (`psexec \\<RemoteSystem> -i ...`)
- **VNC** et autres clients de bureau à distance
- Outils comme **TeamViewer**, **AnyDesk**

---

## Objectif 02 — Escalating Privileges (Élévation de privilèges)

### 2.1 Concepts de base

L'élévation de privilèges est la **deuxième étape** du system hacking : à partir des mots de passe obtenus, l'attaquant cherche des droits plus élevés sur la machine.

| Forme | Description |
|---|---|
| **Vertical privilege escalation** | Passage d'un utilisateur bas à un utilisateur haut (ex. standard → admin/root) |
| **Horizontal privilege escalation** | Passage d'un utilisateur à un autre de même niveau de privilège |

### 2.2 Exploitation de vulnérabilités (généralités)

L'attaquant exploite des **flaws de programmation** (programme, service, OS, kernel) pour exécuter du code avec des privilèges supérieurs ou contourner les mécanismes de sécurité. Il recherche des exploits selon l'OS et les applications sur des sites publics :
- **Exploit Database** (https://www.exploit-db.com)
- **VulDB** (https://vuldb.com)

### 2.3 DLL Hijacking (Windows)

Le **DLL hijacking** consiste à placer une DLL malveillante dans le chemin de recherche d'une application afin qu'elle soit chargée à la place de la DLL légitime.

**Ordre de recherche des DLL (DLL search order) :**
1. Répertoire de l'application
2. Répertoire système (System32)
3. Répertoire système 16 bits
4. Répertoire Windows
5. Répertoire courant
6. Répertoires de la variable d'environnement **PATH**

**Défenses et détection :**
- **DLLSpy** — analyse les fuites d'informations sur le chargement des DLL
- **Dependency Walker** — analyse les dépendances DLL des exécutables et leur ordre de chargement
- Contremesures : utiliser des chemins absolus, valider les DLL chargées, exécuter avec les privilèges minimaux.

### 2.4 Dylib Hijacking (macOS)

- Comme Windows, macOS est vulnérable aux attaques de bibliothèques dynamiques (**dylib**).
- Le chargeur macOS cherche les dylibs dans plusieurs répertoires ; si l'attaquant place une **dylib malveillante** dans un des répertoires primaires, elle est exécutée à la place de la dylib originale.
- Variables d'environnement comme **DYLD_INSERT_LIBRARIES** forcent le chargement de bibliothèques malveillantes dans un processus en cours.
- Usages malveillants : persistance furtive, injection de processus au runtime, contournement des logiciels de sécurité et de **Gatekeeper**.
- Outil : **Dylib Hijack Scanner** (détecte les dylibs vulnérables au hijacking).

### 2.5 Spectre et Meltdown (vulnérabilités CPU)

- Vulnérabilités dans la conception des processeurs modernes (**AMD, ARM, Intel**), dues aux optimisations de performance : **branch prediction, out-of-order execution, caching, speculative execution**.
- Permettent de lire la mémoire adjacente d'un processus (mémoire noyau, mémoire physique) → vol de credentials, clés secrètes, frappes clavier.
- **Spectre** : trompe le processeur pour qu'il exécute spéculativement une lecture avant le bound checking → lecture hors limites ; peut aussi être exploité **via JavaScript (web)**.
- **Meltdown** : force un processus non privilégié à lire la mémoire noyau/mémoire physique → révèle credentials et clés privées.

### 2.6 Named Pipe Impersonation

- Les **named pipes** Windows permettent une communication légitime entre processus (via un fichier) ; le serveur du pipe peut utiliser le **contexte de sécurité du client**.
- L'attaquant crée un **pipe server à faibles privilèges** et force la connexion d'un **client à privilèges élevés** → impersonation.
- Outil : **Metasploit** (commande **`getsystem`** pour obtenir des privilèges administratifs et extraire les hashes ; `getuid`).

### 2.7 Services misconfigurés (Misconfigured Services)

| Technique | Description |
|---|---|
| **Unquoted Service Paths** | Service dont le chemin d'exécutable n'est pas entre guillemets avec des espaces → le système recherche le binaire dans chaque dossier du chemin ; l'attaquant place un exécutable malveillant. Souvent des services tournant en **SYSTEM** |
| **Service Object Permissions** | Permissions mal configurées → l'attaquant modifie le service (change le chemin du binaire vers un exécutable malveillant, ajoute des utilisateurs au groupe administrateurs local) |
| **Unattended Installs** | Le fichier **Unattend.xml** stocke la configuration d'installation (comptes locaux, noms d'utilisateurs, mots de passe décodés). Emplacements : `C:\Windows\Panther\`, `C:\Windows\Panther\UnattendGC\`, `C:\Windows\System32\`, `C:\Windows\System32\sysprep\` |

Outil de détection des services misconfigurés : **PowerSploit** (exécuté via Metasploit).

### 2.8 NFS misconfiguré (Linux)

- **NFS (Network File System)** partage des fichiers sur l'intranet via **RPC sur le port 2049**.
- Un NFS mal configuré permet d'obtenir un **accès root** depuis un compte utilisateur à faibles privilèges.

**Démarche d'exploitation :**
1. Vérifier le service : `nmap -sV <IP cible>`
2. Installer le client : `sudo apt-get install nfs-common`
3. Lister les partages : `showmount -e <IP cible>`
4. Monter le partage : `mkdir /tmp/nfs` puis `sudo mount -t nfs <IP>:/<Partage> /tmp/nfs`
5. Copier un shell (ex. `bash`) dans le partage monté avec les droits du groupe propriétaire
6. Connexion SSH : `ssh -l <utilisateur> <IP cible>` puis exécution du shell SUID → root

### 2.9 Contournement de l'UAC (Windows)

L'UAC (User Account Control) peut être contourné même avec une protection élevée, via des applications Windows abusées. Techniques Metasploit :

| Exploit Metasploit | Principe |
|---|---|
| **bypassuac** | Contourne l'UAC par **process injection** (génère un shell sans drapeau UAC), puis `getsystem` / `getuid` |
| **bypassuac_injection** | Injection **reflective DLL** (seulement des binaires DLL) → privilèges `AUTHORITY\SYSTEM` |
| **bypassuac_fodhelper** | Hijack d'une clé du registre **HKCU** attachée à `fodhelper.exe` → commandes exécutées quand fodhelper est lancé |
| **Eventvwr / COM Handler Hijacking** | Contournement via la clé registre `eventvwr` ou hijacking de **COM handlers** |

### 2.10 Scripts d'initialisation boot/logon

| Technique | Description |
|---|---|
| **Logon Script (Windows)** | Persistance/escalade via la clé registre `HKEY_CURRENT_USER\Environment\UserInitMprLogonScript` |
| **Logon Script (macOS)** | Les **login hooks** s'exécutent automatiquement à la connexion **en tant que root** |
| **Network Logon Scripts** | Alloués via **AD/GPO**, exécutés avec des credentials utilisateur valides → credentials locaux/administrateur selon la configuration |
| **RC Scripts (Unix)** | Scripts de démarrage Unix (`rc.common`, `rc.local`) — injecter un shell/binaire malveillant → accès root au reboot |
| **Startup Items (macOS)** | Dossier `/Library/StartupItems`, configuré via **StartupParameters.plist** (racine) ; exécutés au boot **avec privilèges root** |

### 2.11 Modification de la politique de domaine

- Modification du **Group Policy** : modifier `ScheduledTasks.xml` (`<GPO_PATH>\Machine\Preferences\ScheduledTasks\`) pour créer une tâche planifiée malveillante (ex. script `New-GPOImmediateTask`).
- Modification des **trusts de domaine** : `nltest /domain_trusts` (collecter les domaines de confiance et modifier leurs réglages).
- **Implantation d'un faux contrôleur de domaine** pour maintenir un point d'appui et élever les privilèges.

### 2.12 Abus des services de certificats Active Directory (ADCS)

- **ADCS** gère les certificats des applications, utilisateurs et systèmes dans l'AD.
- Des **templates ADCS mal configurés** (ex. vulnérabilité **ESC1**) permettent à un utilisateur à faibles privilèges d'**enrôler et demander des certificats pour n'importe quel objet du domaine** (ex. Domain Admin).
- Outil : **Certipy** — `certipy find -u '<user>@<domain>' -p <password> -dc-ip <DC_IP> -vulnerable -enabled`, puis `certipy req ... -template <template> -upn <user cible>` pour obtenir un certificat valide d'un compte privilégié.

### 2.13 Autres techniques d'élévation (Windows)

| Technique | Description |
|---|---|
| **Access Token Manipulation** | Modifier les jetons d'accès pour que le processus apparaisse appartenir à un autre utilisateur (ex. commande `runas`) |
| **Parent PID Spoofing** | Spoofing du **PPID** (parent process ID) via l'API `CreateProcess` pour hériter des privilèges d'un processus parent (ex. `svchost.exe`, `consent.exe` via UAC) |
| **Application Shimming** | Le framework de compatibilité Windows (**shims**) interpose un « buffer » entre le programme et l'OS (`%WINDIR%\AppPatch\sysmain.sdb`) ; certains shims peuvent bypasser l'UAC (**RedirectEXE**), injecter des DLL (**InjectDLL**), capturer des adresses mémoire (**GetProcAddress**) |
| **Filesystem Permission Weakness** | Remplacer un binaire légitime exécuté par un processus à privilèges élevés par un binaire malveillant |
| **Path Interception** | Placer un exécutable sur le chemin de recherche (chemins non quotés, variable PATH, search order hijacking) |
| **Accessibility Features** | Remplacer les fonctionnalités d'accessibilité (lancées avant la connexion) par `cmd.exe` : **sethc.exe** (sticky keys), **osk.exe** (clavier virtuel), **Magnify.exe** (loupe), **Narrator.exe**, **DisplaySwitch.exe**, **AtBroker.exe** → accès backdoor au login screen |
| **SID-History Injection** | Injecter le SID d'un compte admin dans l'attribut **SID-history** d'un compte compromis (migration de domaines) |
| **COM Hijacking** | Remplacer des références d'objets **COM** dans le registre (ex. `HKEY_CURRENT_USER\Software\Classes\CLSID\`) pour exécuter du code malveillant quand l'objet est utilisé |
| **Scheduled Tasks (Windows)** | `at` / `schtasks` / Task Scheduler pour exécuter du code au démarrage, à distance (via RPC) |
| **Scheduled Tasks (Linux)** | **cron/crond** : modifier les scripts exécutés depuis `/etc/crontab` |
| **Abus des fichiers MSI** | Les **Custom Actions** de fichiers MSI (stockés dans `C:\Windows\Installer\`) peuvent s'exécuter en **NT AUTHORITY\SYSTEM** via la fonctionnalité « réparation » → escalade |
| **Windows Filtering Platform (WFP) — NoFilter** | Exploiter la WFP sur Windows 11 : récupérer un handle vers le jeton d'accès d'un processus **SYSTEM** (via `RpcOpenToken`, outil **RPC Mapper**), dupliquer le jeton (composant **WfpAleProcessTokenReference**, connexion **IPsec**) → escalade au niveau OS |

### 2.14 Exploitation de buffer overflow Windows

Démarche classique d'exploitation d'un buffer overflow (BOF) :
1. **Spiking** — identification d'un paramètre vulnérable (ex. `!mona`)
2. **Fuzzing** — envoi de chaînes croissantes pour provoquer le crash
3. **Identifier l'offset** — trouver le point d'écrasement de l'EIP (`pattern_create`, `pattern_offset`)
4. **Overwrite EIP** — contrôle du pointeur d'instruction
5. **Identifier les bad characters** — caractères interdits à exclure du shellcode
6. **Identifier le bon module** — recherche d'un module sans protections (ex. ASLR/DEP désactivés)
7. **Générer le shellcode** — payload d'exploitation
8. **Exploitation** — obtention d'un shell distant

### 2.15 Metasploit : payloads, encoders et evasion

Le framework **Metasploit** génère/sélectionne des payloads malveillants qui sont injectés dans le système cible.

| Composant | Rôle |
|---|---|
| **Payloads** | Code exécuté sur la cible après exploitation (ex. reverse shell, meterpreter) |
| **Encoders** | Ré-encodent les payloads pour **éviter la détection** (contournement des mécanismes de signature/AV) |
| **Evasion modules** | Modifient les caractéristiques du payload/exploit pour échapper aux systèmes de sécurité |
| **NOP generators** | Génèrent des instructions NOP pour stabiliser l'exploitation |

### 2.16 Outils d'élévation de privilèges

| Outil | Description |
|---|---|
| **Windows Exploit Suggester NG (WES-NG)** | Outil Python : compare les patchs du système à la base CVE pour suggérer des exploits |
| **BeRoot** | Post-exploitation : vérifie les misconfigurations courantes (permissions de services, dossiers inscriptibles, clés de démarrage) |
| **pwncat** | Énumère et exploite les vulnérabilités d'utilisateurs/sessions (`escalate list`, `escalate list -u root`, `escalate run`) |
| **PowerSploit** | Détection des services misconfigurés (chemins non quotés, permissions) |
| **BloodHound** | Cartographie du domaine AD et des chemins d'attaque (Kerberoastable users, Shortest Paths to Domain Admins…) |
| **Seatbelt** | Évaluation de la configuration du système (credentials, fichiers Windows, audit policies, AutoRuns…) |
| **linpostexp** | Post-exploitation Linux |
| **Traitor, PEASS-ng, FullPowers** | Autres outils de détection d'escalade de privilèges |

### 2.17 Défense contre l'élévation de privilèges

- Restreindre les privilèges de logon interactif et **exécuter les utilisateurs/applications avec les privilèges les plus bas** (principe du moindre privilège)
- Implémenter la **MFA**, la séparation des privilèges (privilege separation), faire tourner les services avec des comptes non privilégiés
- Chiffrer les données sensibles, réduire la quantité de code exécuté avec un privilège donné
- Déboguer avec des **bounds checkers** et tests de stress ; tester les erreurs de codage ; **patcher le noyau** régulièrement
- Passer l'UAC sur **« Always Notify »** ; utiliser des **chemins qualifiés complets** ; placer les exécutables dans des répertoires protégés en écriture
- Surveiller en continu les permissions du système de fichiers ; **whitelisting** ; rendre les `plist` macOS en lecture seule ; bloquer les utilitaires non voulus

---

## Objectif 03 — Maintaining Access (Maintien de l'accès)

### 3.1 Concepts

Après avoir obtenu l'accès et élevé les privilèges, l'attaquant **maintient son accès** pour exploiter davantage le système ou s'en servir comme base de lancement contre d'autres machines du réseau. Il exécute à distance des programmes malveillants (keyloggers, spyware, rootkits) et cache ses fichiers (stéganographie, NTFS streams) pour voler des informations critiques.

### 3.2 Exécution de code à distance (Remote Code Execution)

Techniques utilisées après la compromission initiale pour étendre l'accès :

| Technique | Description |
|---|---|
| **Exploitation for Client Execution** | Exploitation côté client : **navigateur web** (spear phishing, drive-by compromise), **applications Office** (documents malveillants), **applications tierces** (Adobe Reader, Flash…) |
| **Service Execution** | Créer/modifier un **service Windows** (via Service Control Manager) pour exécuter des binaires |
| **Windows Management Instrumentation (WMI)** | Plateforme d'accès aux ressources Windows (locale/à distance) ; exécution de code et mouvement latéral via **DCOM (port 135)** et **WinRM (ports 5985 HTTP / 5986 HTTPS)** |
| **Windows Remote Management (WinRM)** | Protocole d'exécution à distance (fichiers exécutables, services, registre) ; commande `winrm` pour mouvement latéral |

### 3.3 Backdoors et Trojans

Les **backdoors** (portes dérobées) permettent un retour furtif sur le système compromis :
- **RATs (Remote Access Trojans)** — contrôle à distance complet
- **Backdoors réseau** — écoute sur un port ouvert (ex. Netcat)
- **Outils de domination du domaine** (voir 3.9) et **living off the land**

### 3.4 Keyloggers et Spyware (outils et détail)

- **Keyloggers** : enregistreurs de frappe matériels ou logiciels (cf. 1.7) ; possibilité d'établir un keylogger via **Metasploit**.
- **Spyware** : capture d'écrans, enregistrement, exfiltration vers un serveur (cf. 1.8) — ex. **Spytech SpyAgent**, **Spyrix Personal Monitor**.

### 3.5 Rootkits

Un **rootkit** est un programme (ou ensemble de programmes) qui permet à l'attaquant de **garder un accès privilégié** tout en dissimulant sa présence et ses activités au système et aux utilisateurs.

**Composants d'un rootkit :**
- Programmes backdoors
- Programmes DDoS
- Packet sniffers
- Log-wiping utilities (nettoyeurs de logs)
- IRC bots

**Types de rootkits :**

| Type | Description |
|---|---|
| **User-mode (application) rootkits** | Interceptent les appels API et remplacent les fichiers binaires |
| **Kernel-mode rootkits** | Installent des drivers/dlls dans le noyau ; interception des appels système |
| **Bootkits** | Remplacent le bootloader du système (ex. MBR, firmware) — chargés avant l'OS |
| **Hypervisor/virtual rootkits** | Exécutent la cible dans une machine virtuelle (attaque « below the OS ») |
| **Firmware rootkits** | Intègrent le malware dans le firmware du matériel (BIOS/UEFI, cartes réseau…) |

**Mécanismes d'action :** injection DLL, interception d'appels système (hook), détournement du flux d'exécution, patching en mémoire.

**Techniques de détection des rootkits :**
- **Détection par signature (signature-based)** — comparaison à une base de signatures connues
- **Détection heuristique / comportementale (heuristic/behavior-based)** — analyse du comportement anormal
- **Profilage du chemin d'exécution (runtime execution path profiling)** — comparaison du chemin d'exécution réel au chemin attendu pour détecter les détournements
- **Analyse croisée** — comparer les résultats d'outils système avec des appels directs (inconsistances)
- **Différence de mémoire / de disque** — fichiers présents en mémoire mais pas sur disque

**Outils de détection des rootkits :**
- **GMER** (http://www.gmer.net) — détection et suppression de rootkits (aussi utilisé pour détecter les NTFS streams)
- **Rootkit Revealer**, **Helios**, **IceSword**, **Radar**, **WindowSentry**, **Process Guard**, **F-Secure BlackLight**, **VirusTotal**…

**Contremesures :** booter sur un média propre, restaurer depuis une source fiable, mettre à jour OS/firmware, utiliser des signatures, éviter d'exécuter des programmes non fiables.

### 3.6 Stéganographie, stéganalyse et stéganographie sur fichiers

La **stéganographie** dissimule l'existence même d'un message (contrairement au chiffrement qui ne cache que le contenu). La **stéganalyse** est l'art de détecter et extraire ces messages cachés.

**Types de stéganographie :**

| Support | Description |
|---|---|
| **Image** | Modification des pixels ; LSB insertion, domaines fréquentiels (FFT, DCT, wavelet), masking/filtering |
| **Audio** | Insertion dans les bits de poids faible des échantillons, écho, phase |
| **Vidéo** | Dissimulation dans les trames vidéo (grand volume de données) |
| **Document** | Espaces et tabulations invisibles (ex. **Snow**), modification de métadonnées |
| **Dossier / système de fichiers** | NTFS ADS, slack space |

**Stéganographie d'image — techniques clés :**
- **LSB insertion** : remplacement du bit de poids faible (LSB, le bit le plus à droite) de chaque pixel par un bit du message. La modification est imperceptible.
- **Transform domain (frequency domain)** : transformation de l'image (ex. **DCT** en JPEG), puis insertion des données dans les coefficients fréquentiels. Technique plus robuste : **FFT**, **DCT**, **wavelet transformation**.
- **Masking / Filtering** : superposition du message sur l'image (robuste à la compression).

**Outils de stéganographie :**
- **OpenStego** (https://www.openstego.com) — stéganographie d'image
- **Steghide** — dissimulation dans images/audio (`steghide embed/extract`)
- **Snow** — dissimulation dans les fichiers texte par ajout d'espaces/tabulations en fin de ligne
- **QuickStego**, **Crypture**, **Invoke-Stegano** (PowerShell)…

**Watermarking vs stéganographie :** le filigrane (watermarking) marque le média pour en revendiquer la propriété (signature de copyright), alors que la stéganographie sert au secret de communication. Un filigrane peut être visible (logo) ou invisible.

**Stéganalyse — attaques (types d'attaque) :**

| Attaque | Description |
|---|---|
| **Stego-only** | Seul le stego-objet est disponible ; essai de tous les algorithmes |
| **Known-stego** | L'algorithme de stéganographie + objets original et stego sont connus |
| **Known-message** | Le message et le stego-medium sont disponibles → déduire la technique |
| **Known-cover** | Le stego-objet et le cover original sont connus → comparaison |
| **Chosen-message** | Un message connu est utilisé pour générer des stego-objets → identifier l'algorithme |
| **Chosen-stego** | Le stego-objet et l'outil/algorithme sont connus |
| **Chi-square** | Analyse de probabilité : teste si le stego-objet et l'original diffèrent |
| **Distinguishing statistical** | Analyse des changements statistiques et de la longueur des données intégrées |
| **Blind classifier** | Un détecteur « aveugle » est entraîné sur des données originales pour distinguer les stego-objets |

**Détection selon le type de fichier :**
- **Texte** : motifs inhabituels, espaces supplémentaires et caractères invisibles en fin de ligne
- **Image** : distorsions, bruit exagéré, anomalies de couleur/luminance/pixels ; l'analyse statistique des **LSB** (les LSB deviennent non aléatoires)
- **Audio** : analyse statistique (modifications LSB), fréquences inaudibles, distorsions
- **Vidéo** : combinaison des méthodes image + audio, signes/codes spéciaux

**Outils de détection (stéganalyse) :**
- **zsteg** — détecte les données cachées dans les images **PNG et BMP**
- **StegoVeritas**, **Stegextract**, **StegoHunt MP** (Wetstone), **Steganography Studio**, **Virtual Steganographic Laboratory (VSL)**, **StegExpose**

### 3.7 Maintien de la persistance (Persistence)

Techniques pour survivre aux redémarrages et conserver l'accès :

| Technique | Description |
|---|---|
| **Sticky Keys** | Exploiter la fonctionnalité « Sticky Keys » (5× Shift) : module Metasploit `sticky_keys` → après reboot, 5× Shift ouvre une **invite de commandes au niveau système** |
| **Registry Run Keys** | Exécution automatique au démarrage via les clés **Run** (enumérable avec **WinPEAS** : `winPEASx64.exe quiet applicationinfo`) |
| **Startup Folder** | Injecter des RAT dans le dossier de démarrage (permissions vérifiées avec **`icacls`** ou **accesschk.exe**) |
| **Boot/Logon autostart** | Abus des mécanismes d'auto-exécution au boot/logon (cf. 2.10) |
| **Scheduled tasks** | Tâches planifiées au démarrage |
| **Fichiers de profil utilisateur** | `.bashrc`, `.bash_profile`… |
| **Planting Flags** | Créer des fichiers/drapeaux sur le système pour « marquer » les machines compromises |

### 3.8 Post-exploitation (Linux et Windows)

**Linux — commandes de fichiers et d'information :**
- `find / -perm -4000 -ls 2>/dev/null` — binaires SUID
- `find / -path /sys -prune -o -path /proc -prune -o -type f -perm -o=w -ls 2>/dev/null` — fichiers world-writable
- `find / -path /sys -prune -o -path /proc -prune -o -type d -perm -o=w -ls 2>/dev/null` — dossiers world-writable
- `chmod o-w file` — supprime l'accès en écriture
- `find / -name "*.txt" -ls 2>/dev/null` — fichiers .txt
- `sudo -l` — liste des commandes autorisées/interdites
- `ps -ef`, `mount`, `route -n`, `/sbin/ifconfig -a`, `cat /etc/crontab` — informations système

**Windows — commandes (WMIC, services, exécution distante) :**
- `dir /a:h` — répertoires avec attribut caché ; `findstr /E ".txt" > txt.txt` — fichiers texte
- `wmic os where Primary='TRUE' reboot` — reboot ; `wmic /node:"" product get name,version,vendor` — logiciels installés ; `wmic cpu get` ; `wmic useraccount get name,sid`
- `sc queryex type=service state=all` — liste des services ; `net start/stop` — gestion des services
- `netsh advfirewall set allprofiles state off` — désactive le firewall pour tous les profils
- `wmic /node:<IP> /user:administrator /password:$PASSWORD bios get serialnumber` — numéro de série à distance
- `taskkill.exe /S <IP> /U domain\username /F /FI "eset"` ; `tasklist.exe /S <IP> /U domain\username /FI "USERNAME eq NT AUTHORITY\SYSTEM"`

### 3.9 Domination du domaine (Domain Dominance)

Une fois le contrôle d'une machine de domaine obtenu, l'attaquant cherche la **domination complète du domaine** (Domain Controller).

| Technique | Description |
|---|---|
| **Pass-the-Hash (PtH)** | Utiliser le hash NTLM d'un utilisateur pour s'authentifier sans mot de passe |
| **Pass-the-Ticket (PtT)** | Rejouer un TGT/ST volé |
| **Overpass-the-Hash** | Obtenir un TGT à partir du hash NTLM |
| **Golden Ticket** | TGT forgé avec le hash **KRBTGT** → contrôle total et durable du domaine |
| **Silver Ticket** | ST forgé pour un service spécifique |
| **Skeleton Key attack** | Patch de la mémoire de **LSASS** sur le contrôleur de domaine : un « master password » universel est injecté, valide pour **tous les comptes** du domaine |
| **Malicious Replication / DCSync** | Réplication Active Directory simulée pour extraire les hashes (dont KRBTGT) |
| **Remote Code Execution (RCE)** | Exécution de code malveillant sur le DC via CLI/WMI (ex. `wmic /node:<DC> process call create "net user /add PiratedProcess Du**Y01"` puis ajout au groupe Admins) |
| **Abusing DPAPI** | Obtenir la **clé maîtresse** de DPAPI depuis le DC pour décrypter les fichiers protégés DPAPI |
| **Kerberoasting / AS-REP Roasting** | Cracking de tickets pour des comptes de service/AS-REP |

**Skeleton Key — outils :**
- **mimikatz** : `misc::skeleton` (mode interactif) — exécuté avec `privilege::debug`
- **PowerShell (Invoke-Mimikatz)** :
  `Invoke-Mimikatz -Command '"privilege::debug" "misc::skeleton"'`
- **Empire** : module `powershell/persistence/misc/skeleton_key`
- Le mot de passe « master » standard est **`mimikatz`** ; l'attaque nécessite des **droits d'administrateur de domaine** et l'accès au DC ; c'est un **virus résident en mémoire** difficile à distinguer des authentifications légitimes.

**Golden Ticket — étapes (mimikatz) :**
1. Obtenir le nom de domaine et le **SID** (`whoami`)
2. Voler le hash NTLM de **KRBTGT** : `lsadump::dcsync /domain:<domaine> /user:krbtgt` (ou DCSync)
3. Forger le ticket : `kerberos::golden /domain:<domaine> /sid:<SID> /rc4:<hash KRBTGT> /id:<valeur> /user:<utilisateur>`
4. Maintenir la persistance en réglant la validité du ticket

**Persistence de domaine via AdminSDHolder :**
- **AdminSDHolder** est un objet AD qui protège les comptes/groupes très privilégiés contre les modifications accidentelles de permissions.
- Le processus **SDProp** (Security Descriptor Propagator) récupère la liste ACL d'AdminSDHolder et l'applique (réplication toutes les heures).
- L'attaquant admin de domaine ajoute un compte à l'ACL pour obtenir des droits **GenericAll** (équivalents admin de domaine) :
  - `Add-ObjectAcl -TargetADSprefix 'CN=AdminSDHolder,CN=System' -PrincipalSamAccountName Martin -Verbose -Rights All`
  - `net group "Domain Admins" Martin /add /domain`
- Le réglage de la fréquence de SDProp peut être modifié : `REG ADD HKLM\SYSTEM\CurrentControlSet\Services\NTDS\Parameters /V AdminSDProtectFrequency /T REG_DWORD /F /D 300`

**Contremesures :** protéger les identifiants KRBTGT (rotation régulière), activer le SMB signing, durcir les comptes de service, surveiller les logs de réplication (DCSync), détecter les appels à LsaAdjustPrivileges.

---

## Objectif 04 — Clearing Logs (Effacement des traces)

### 4.1 Concepts de l'effacement des traces (Covering Tracks)

L'effacement des traces est la **dernière étape** du system hacking : supprimer les preuves de la compromission (logs, historiques, fichiers temporaires).

**Techniques utilisées :**

| Surface | Techniques |
|---|---|
| **Réseau** | Reverse HTTP shells (le trafic HTTP semble normal pour les firewalls/DMZ), tunnels ICMP reverse (payload TCP encapsulé dans les paquets ICMP echo — les pare-feux ne vérifient que les paquets ICMP entrants), DNS tunneling (exfiltration dans les requêtes/réponses DNS), canaux cachés via paramètres TCP (Identification field, acknowledgement number, initial sequence number) |
| **OS** | Utilisation des NTFS streams pour cacher les fichiers malveillants |
| **Audit / Logs** | Désactivation de l'auditing (auditpol), effacement des logs |
| **Fonctionnalités Windows** | Désactivation des timestamps d'accès, hibernation, mémoire virtuelle, points de restauration, cache de vignettes, prefetch |

### 4.2 Désactivation de l'audit : Auditpol

**auditpol.exe** est l'utilitaire en ligne de commande pour modifier les paramètres de sécurité d'audit au niveau catégories et sous-catégories.

- Désactiver l'audit : `auditpol /set /category:"system","account logon" /success:disable`
- Réactiver l'audit après la mission : `auditpol /set /category:"system","account logon" /success:enable`
- Afficher la configuration : `auditpol /get /category:*`

### 4.3 Effacement des logs Windows

- **Windows Event Logs** : journaux Application, Security, System…
- Effacement par commande : **`wevtutil cl <nom du log>`** (ex. `wevtutil cl Security`)
- Outils de nettoyage des traces (cookies, historique Internet, fichiers temporaires, logs, caches) :

| Outil | Description |
|---|---|
| **CCleaner** (ccleaner.com) | Optimisation, vie privée, nettoyage des traces Internet et fichiers inutilisés |
| **DBAN** (dban.org) | Effacement complet de disques |
| **Privacy Eraser Free** (cybertronsoft.com) | Nettoyage des traces de navigation et fichiers temporaires |
| **Wipe** (privacyroot.com) | Effacement sécurisé |
| **BleachBit** (bleachbit.org) | Nettoyage multi-plateforme (Linux/Windows) |
| **east-tec Eraser** (east-tec.com) | Effacement sécurisé des traces |

**Désactivation de fonctionnalités Windows pour couvrir les traces :**
- **Timestamps d'accès (last access)** :
  `fsutil behavior set disablelastaccess 1` (1 = timestamps désactivés ; 0 = activés)
- **Hibernation** : supprimer/empêcher la création de `Hiberfil.sys` (fichier caché à la racine) via le registre (`HibernateEnabled` = 0) ou `powercfg -h off`
- **Mémoire virtuelle (paging file)** : désactiver `pagefile.sys` (les données résiduelles pourraient révéler des secrets)
- **Points de restauration système** : désactiver les System Restore Points
- **Cache de vignettes (Thumbnail Cache)** : empêcher la génération des vignettes
- **Prefetch** : désactiver la fonctionnalité Prefetch (traces d'exécution des programmes)

### 4.4 Effacement des traces BASH / Linux

Bash (Bourne Again Shell) stocke l'historique des commandes dans `~/.bash_history`. L'attaquant le nettoie pour supprimer la preuve des commandes utilisées.

| Commande | Effet |
|---|---|
| `export HISTSIZE=0` | Désactive l'enregistrement de l'historique (taille 0) |
| `history -c` | Efface l'historique stocké |
| `history -w` | Efface l'historique du shell courant uniquement |
| `cat /dev/null > ~/.bash_history && history -c && exit` | Efface l'historique complet (shell courant + autres) puis quitte |
| `shred ~/.bash_history` | Déchiquette (shred) le fichier → contenu illisible |
| `shred ~/.bash_history && cat /dev/null > ~/.bash_history && history -c && exit` | Shred + suppression + effacement des preuves d'utilisation |

### 4.5 Modification des horodatages et suppression sécurisée

**Dissimulation de fichiers dans les NTFS ADS (Windows) :**
- Cacher : `type C:\SecretFile.txt > C:\LegitFile.txt:SecretFile.txt`
- Afficher : `more < C:\SecretFile.txt`

**Modification des dates et heures :**
- **timestomp** (Metasploit) : `timestomp <fichier> -z "<Date> <heure>"`
- **Windows (PowerShell)** : `powershell -Command "(Get-Item $File_name).LastWriteTime = $(Get-Date).AddHours(-10)"`
- **Linux** : `touch -a -d '<date> <time>' $File` (accès) et `touch -m -d '<date> <time>' $File` (modification)

**Suppression sécurisée avec Cipher.exe (Windows) :**
- `cipher /w:<lettre>:\<dossier>` — écrasement des fichiers supprimés d'un dossier
- `cipher /w:<lettre>:` — écrasement de tous les fichiers supprimés d'un lecteur
- Principe : réécriture avec des **0x00**, puis des **0xFF**, puis des **nombres aléatoires** pour empêcher toute récupération.

### 4.6 Dissimulation d'artefacts (Windows, Linux, macOS)

| OS | Technique |
|---|---|
| **Windows — fichiers/dossiers** | `attrib +h +s +r <Dossier>` (caché + système + lecture seule) |
| **Windows — utilisateurs** | Créer un compte caché : `net user <User> /add`, puis `net user <User> /active:yes` (actif) / `/active:no` (caché) |
| **Windows — comptes utilisateurs** | Masquer un compte à l'écran de connexion via le registre : `HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\CEH_Account1\CEH_Account2\` avec une valeur **DWORD** portant le nom du compte |
| **Linux — fichiers/dossiers** | Préfixer le nom d'un point `.` : `mv MaliciousFile.txt .MaliciousFile.txt` ; `mkdir .HiddenMaliciousFiles` ; afficher avec `ls -a` / `ls -al` |
| **macOS — fichiers/dossiers** | `defaults write com.apple.finder AppleShowAllFiles FALSE` + `killall Finder` ; ou `chflags hidden <fichier>` |

### 4.7 Anti-forensique (Anti-forensics for Covering Tracks)

L'**anti-forensique** regroupe les techniques utilisées par les attaquants pour cacher leurs activités malveillantes (effacer, altérer ou dissimuler les actions de compromission).

| Technique | Description |
|---|---|
| **Data/file deletion** | Suppression des fichiers ; sous Windows la suppression normale passe par la **Corbeille** (éviter avec Shift+Delete) ; supprimer les métadonnées associées |
| **Password protection** | Protéger/chiffrer les fichiers contre les outils de récupération |
| **Steganography** | Cacher des informations (source code d'outils, listes de serveurs compromis, plans) quand le chiffrement est inadapté |
| **Data hiding in file system structures** | Cacher des données dans **SBadClus** (sparse file à allocation illimitée), **HPAs** (Host-Protected Areas), **DPAs** et **slack spaces** (invisibles au BIOS/OS) |
| **Trail obfuscation** | Supprimer les preuves : log tampering, faux en-têtes d'email, modifications de timestamps avec **Timestomp** / **Transmogrify**, log cleaners, comptes zombies, spoofing |
| **Artifact wiping** | Destruction définitive des preuves (file-wiping, disk-cleaning, degaussing, formatage) — outils : **BCWipe**, **Total WipeOut**, **DriveScrubber**, **Disk Wipe**, **KillDisk**, **R-Wipe & Clean**, **BitRaser File Eraser**, **Blancco File Eraser** |
| **Overwriting data/metadata** | Écraser toutes les zones adressables du média avec des caractères aléatoires (déletion simple, **data shredding**, data wiping) |
| **Program packers** | Compresser/chiffrer les fichiers dans des conteneurs (protégés par mot de passe) — outils : **UPX**, **PECompact**, **BurnEye**, **Exe Stealth Packer**, **Smart Packer Pro** |
| **Minimizing footprints** | Laisser un minimum de traces : identités volées, machines virtuelles, cloud, Live USB/external HDD |
| **Access anonymization** | Anonymiser l'accès : proxies, services d'anonymisation, **Tor**, traffic padding, canaux de communication anonymes |

### 4.8 Défense contre l'effacement des traces

- Activer la journalisation (logging) sur tous les systèmes critiques
- Auditer périodiquement les systèmes pour vérifier la conformité du logging à la politique de sécurité
- Empêcher l'écrasement des anciennes entrées par les nouvelles quand la limite de stockage est atteinte
- Configurer des permissions minimales (ACL restreintes) pour lire/écrire les fichiers de logs
- Maintenir un **serveur de logs séparé dans la DMZ** (DNS, mail, web) pour centraliser les logs critiques
- Mettre à jour et patcher OS, applications et firmware ; fermer les ports/services inutilisés
- **Chiffrer les fichiers de logs avec un logging immuable** (immutable logging) — non modifiables sans la clé de déchiffrement
- Mode « **append only** » sur les fichiers de logs pour empêcher la suppression de lignes
- Sauvegarder périodiquement les logs sur un support non altérable
- **Gestion centralisée des logs** (centralized log management) : collecter et stocker les logs de tous les systèmes
- **FIM (File Integrity Monitoring)** : surveiller les fichiers système/configurations contre les modifications non autorisées
- **SIEM** : analyse en temps réel des alertes de sécurité, corrélation des événements, détection de modifications/suppressions de logs
- **IDS/IPS** : surveiller les activités réseau/système malveillantes
- **UEBA (User and Entity Behavior Analytics)** : détecter les anomalies de comportement indiquant des tentatives d'effacement de traces

---

## Aide-mémoire examen (à retenir absolument)

- Les **4 phases** du system hacking : **Gaining Access → Escalating Privileges → Maintaining Access → Clearing Logs**.
- Les mots de passe Windows sont stockés **hachés** dans la **SAM**, protégée par **SYSKEY** (128 bits).
- **pwdump7** et **Mimikatz** (lecture mémoire de **LSASS**) extraient les hashes.
- **Kerberoasting** = cracker les **TGS** ; **AS-REP Roasting** = cracker les **TGT** ; **Golden Ticket** = hash **KRBTGT** (forgé via `kerberos::golden`) ; **Silver Ticket** = hash du compte de service.
- **Responder** empoisonne **LLMNR/NBT-NS** (ports 137, 5355) ; **ntlmrelayx** fait le **SMB Relay** ; le **SMB signing** est la contre-mesure clé.
- **hashcat** : `-m` = mode de hash, `-a` = type d'attaque, `?d/?l/?u/?s` = masques.
- **Élévation verticale** (bas → haut) vs **horizontale** (même niveau).
- **DLL hijacking** : exploite l'ordre de recherche des DLL ; **Dylib hijacking** = équivalent macOS (DYLD_INSERT_LIBRARIES, Gatekeeper).
- **Spectre/Meltdown** = vulnérabilités CPU (branch prediction, speculative execution, out-of-order execution, caching).
- **Named pipe impersonation** : `getsystem` (Metasploit). **Services misconfigurés** : unquoted paths, service permissions, **Unattend.xml**.
- **NFS** : port **2049**, `showmount -e`, `mount -t nfs`.
- **UAC bypass** Metasploit : `bypassuac`, `bypassuac_injection`, `bypassuac_fodhelper`.
- **Accessibility features** : remplacer **sethc.exe** (sticky keys), osk, magnify par cmd.exe.
- **ADCS/ESC1** + **Certipy** : obtenir un certificat de Domain Admin depuis un template mal configuré.
- **Scheduled tasks** : `at`/`schtasks` (Windows), **cron** `/etc/crontab` (Linux). **MSI Custom Actions** = SYSTEM.
- **NoFilter/WFP** : duplication de token SYSTEM via la Windows Filtering Platform.
- Recherche de binaires **SUID** : `find / -perm -u=s -type f 2>/dev/null`.
- **Buffer overflow** : spiking → fuzzing → offset → overwrite EIP → bad chars → bon module → shellcode.
- **Rootkits** : user-mode, kernel-mode, bootkits, hypervisor, firmware ; détection par **signature**, **heuristique/comportement**, **profilage du chemin d'exécution** ; outil emblématique **GMER**.
- **LSB insertion** (bit de poids faible des pixels) et domaine fréquentiel (**DCT/FFT/wavelet**) en stéganographie d'image ; outils **OpenStego**, **Steghide**, **Snow** ; détection : **zsteg** (PNG/BMP), steganalyse (chi-square, known-cover…).
- **Persistence** : Sticky Keys (5× Shift → cmd système), registry Run keys, startup folder, tâches planifiées.
- **Skeleton key** : `misc::skeleton` dans mimikatz patche **LSASS** → mot de passe universel pour tous les comptes du domaine ; Empire : `powershell/persistence/misc/skeleton_key`.
- **AdminSDHolder** : abus du processus **SDProp** (réplication horaire) pour la persistance de domaine.
- **auditpol** : `auditpol /set /category:"system","account logon" /success:disable`.
- **wevtutil cl** efface les logs Windows ; **fsutil behavior set disablelastaccess 1** désactive les timestamps d'accès.
- BASH : `export HISTSIZE=0`, `history -c`, `cat /dev/null > ~/.bash_history && history -c && exit`, `shred ~/.bash_history`.
- Dissimulation : `attrib +h +s +r` (Windows), préfixe `.` (Linux, fichiers placés dans /dev, /tmp, /etc), `chflags hidden` (macOS) ; cache dans NTFS ADS via `type fichier > fichier:flux`.
- Modification des dates : **timestomp**, `touch -a -d` / `touch -m -d`, PowerShell `LastWriteTime` ; suppression sécurisée : **`cipher /w:`** (0x00, 0xFF, aléatoire).
- **Anti-forensique** : trail obfuscation (Timestomp), artifact wiping (BCWipe, KillDisk), packers (UPX), HPA/slack spaces.
- Défense : logging centralisé, serveur de logs DMZ, append-only, immutable logging, FIM, SIEM, UEBA.

## Synthèse du module

Ce module a couvert en détail les **quatre phases du system hacking** :

1. **Gaining Access** : cracking de mots de passe (dictionnaire, brute-force, rainbow tables, hybride, rule-based, password spraying), outils (hashcat, John, THC-Hydra, Responder…), attaques d'authentification Windows/Kerberos (LLMNR/NBT-NS poisoning, SMB relay, Kerberoasting, Pass-the-Ticket…), keyloggers, spyware, établissement de sessions à distance et dissimulation de fichiers (NTFS ADS).
2. **Escalating Privileges** : élévation verticale/horizontale, exploitation de vulnérabilités (Exploit-DB, VulDB, Spectre/Meltdown), DLL/Dylib hijacking, named pipe impersonation, services misconfigurés, NFS, contournement UAC, scripts boot/logon, politique de domaine, ADCS/ESC1, token manipulation, shims, accessibility features, SID-history, COM hijacking, tâches planifiées, MSI, NoFilter/WFP, buffer overflows, Metasploit (payloads, encoders, evasion) et outils d'audit (WES-NG, BeRoot, pwncat, BloodHound, Seatbelt).
3. **Maintaining Access** : exécution de code à distance (WMI/WinRM), backdoors, keyloggers/spyware, rootkits (types, détection, outils), stéganographie et stéganalyse (attaques et outils), persistance (Sticky Keys, autostart, AdminSDHolder), post-exploitation Linux/Windows, et domination du domaine (Pass-the-Hash/Ticket, Golden/Silver Ticket, skeleton key, DCSync, DPAPI).
4. **Clearing Logs** : désactivation de l'audit (auditpol), effacement des logs (wevtutil, CCleaner, BleachBit…), désactivation de fonctionnalités Windows (hibernation, pagefile, timestamps), effacement de l'historique BASH, dissimulation d'artefacts (Windows/Linux/macOS), anti-forensique et contremesures défensives (logging centralisé, FIM, SIEM, UEBA).

Le prochain module abordera les **malware threats** (Module 07).
