# Module 06 — System Hacking (CEH v13)

> Notes de cours en français basées sur le support officiel **CEH v13 — Module 06 : System Hacking** (EC-Council, 312-50).
> Révision pour l'examen CEH : les quatre phases du système hacking (gaining access, escalating privileges, maintaining access, covering tracks), cracking de mots de passe et attaques d'authentification (Kerberos, NTLM, LLMNR/NBT-NS), élévation de privilèges (DLL hijacking, buffer overflows), maintien de l'accès (backdoors, spyware, rootkits, stéganographie, domination du domaine) et effacement des traces.

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
- Utiliser les techniques d'élévation de privilèges Windows et Linux (DLL hijacking, SUID, buffer overflow…)
- Décrire les outils de maintien d'accès : keyloggers, spyware, rootkits, stéganographie
- Expliquer les techniques de domination du domaine (Pass-the-Hash, Golden/Silver Ticket, skeleton key)
- Décrire les techniques d'effacement des traces (auditpol, wevtutil, nettoyage BASH…)

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
| **Silver Ticket** | Forger un ST pour une ressource spécifique avec le hash NTLM du compte de service |

### 1.4 Techniques de cracking de mots de passe

**Types d'attaques sur les mots de passe :**

| Type | Exemples |
|---|---|
| **Non-électroniques** | Shoulder surfing, social engineering, dumpster diving |
| **Actives en ligne** | Trojan/Spyware/Keylogger, injection de hash (PtH), phishing, LLMNR/NBT-NS poisoning, SMB Relay, downgrade attacks |
| **Passives en ligne** | Sniffing du réseau, MitM, rejeu (replay) |
| **Hors ligne (offline)** | Attaque par dictionnaire, rainbow tables, hybride, attaque par anniversaire (birthday), rule-based |
| **Mots de passe par défaut** | Devinés via les listes de mots de passe par défaut des fabricants |

**Techniques de cracking :**
- **Dictionary attack** — essai de chaque mot d'un dictionnaire (liste de mots courants)
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

| Outil | Description |
|---|---|
| **Spytech SpyAgent** | Surveillance complète : keylogging, captures d'écran, suivi des applications et sites web |
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

### 2.2 Techniques d'élévation de privilèges Linux

- **SUID binaries** : recherche de binaires avec le bit SUID/SGID pour exécuter des commandes avec les droits du propriétaire :
  - `find / -perm -u=s -type f 2>/dev/null`
  - `find / -perm -g=s -type f 2>/dev/null`
  - `find / -perm -3000 -ls 2>/dev/null`
- Exploitation de vulnérabilités du noyau (kernel exploits)
- Services et applications vulnérables
- Fichiers de configuration mal protégés, cron jobs, etc.
- **Scripts de démarrage (Startup scripts)** : modifier les scripts exécutés au démarrage/déconnexion pour exécuter du code malveillant (ex. scripts réseau logon, RC scripts `rc.local`/`rce.common`, Startup Items macOS `/Library/StartupItems` avec `StartupParameters.plist`).

### 2.3 Techniques d'élévation de privilèges Windows

- **Vulnerable services** : services exécutés avec des privilèges élevés exploitables
- **Unquoted service paths** : chemins de services non quotés → injection d'exécutable
- **AlwaysInstallElevated** : installation MSI avec élévation automatique
- **Credential dumping** : extraction des identifiants (Mimikatz…)
- **Fichiers de configuration sensibles**, dossiers avec permissions faibles
- **DLL hijacking / DLL side-loading** (voir 2.4)

### 2.4 DLL Hijacking

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
- **Dylib Hijack Scanner** — détecte les vulnérabilités de hijacking des bibliothèques dynamiques macOS (dylib)
- **Dependency Walker** — analyse les dépendances DLL des exécutables et leur ordre de chargement
- Contremesures : utiliser des chemins absolus, valider les DLL chargées, exécuter avec les privilèges minimaux.

### 2.5 Exploitation de vulnérabilités — Buffer Overflow Windows

Démarche classique d'exploitation d'un buffer overflow (BOF) :
1. **Spiking** — identification d'un paramètre vulnérable (ex. `!mona`)
2. **Fuzzing** — envoi de chaînes croissantes pour provoquer le crash
3. **Identifier l'offset** — trouver le point d'écrasement de l'EIP (`pattern_create`, `pattern_offset`)
4. **Overwrite EIP** — contrôle du pointeur d'instruction
5. **Identifier les bad characters** — caractères interdits à exclure du shellcode
6. **Identifier le bon module** — recherche d'un module sans protections (ex. ASLR/DEP désactivés)
7. **Générer le shellcode** — payload d'exploitation
8. **Exploitation** — obtention d'un shell distant

### 2.6 Metasploit : payloads, encoders et evasion

Le framework **Metasploit** génère/sélectionne des payloads malveillants qui sont injectés dans le système cible.

| Composant | Rôle |
|---|---|
| **Payloads** | Code exécuté sur la cible après exploitation (ex. reverse shell, meterpreter) |
| **Encoders** | Ré-encodent les payloads pour **éviter la détection** (contournement des mécanismes de signature/AV) |
| **Evasion modules** | Modifient les caractéristiques du payload/exploit pour échapper aux systèmes de sécurité |
| **NOP generators** | Génèrent des instructions NOP pour stabiliser l'exploitation |

**Outils associés :**
- **Windows Exploit Suggester - Next Generation (WES-NG)** : outil Python qui compare les patchs du système à la base CVE pour suggérer des exploits d'élévation
- **BloodHound** : cartographie des chemins d'attaque du domaine (Active Directory) via les relations (Kerberoastable users, Shortest Paths to Domain Admins…)
- **Seatbelt** : évaluation de la configuration du système (recherche de credentials, fichiers Windows, audit policies, RDP settings, AutoRuns, etc.)

### 2.7 Contremesures

- Appliquer les correctifs (kernel, OS, applications) rapidement
- Restreindre l'usage de SUID/des services à privilèges élevés
- Utiliser des comptes aux privilèges minimaux, LUA (Least User Access)
- Surveiller et auditer les chargements de DLL et les chemins de services

---

## Objectif 03 — Maintaining Access (Maintien de l'accès)

### 3.1 Concepts

Après avoir obtenu l'accès et élevé les privilèges, l'attaquant **maintient son accès** pour exploiter davantage le système ou s'en servir comme base de lancement contre d'autres machines du réseau. Il exécute à distance des programmes malveillants (keyloggers, spyware, rootkits) et cache ses fichiers (stéganographie, NTFS streams) pour voler des informations critiques.

### 3.2 Backdoors et Trojans

Les **backdoors** (portes dérobées) permettent un retour furtif sur le système compromis :
- **RATs (Remote Access Trojans)** — contrôle à distance complet
- **Backdoors réseau** — écoute sur un port ouvert (ex. Netcat)
- **Outils de domination du domaine** (voir 3.6) et **living off the land**

### 3.3 Keyloggers et Spyware (rappel outils)

- **Keyloggers** : enregistreurs de frappe matériels ou logiciels (cf. 1.7)
- **Spyware** : capture d'écrans, enregistrement, exfiltration vers un serveur (cf. 1.8) — ex. **Spytech SpyAgent**, **Spyrix Personal Monitor**

### 3.4 Rootkits

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

### 3.5 Stéganographie et stéganalyse

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

**Outils :**
- **OpenStego** (https://www.openstego.com) — stéganographie d'image
- **Steghide** — dissimulation dans images/audio (`steghide embed/extract`)
- **Snow** — dissimulation dans les fichiers texte par ajout d'espaces/tabulations en fin de ligne
- **QuickStego**, **Crypture**, **Invoke-Stegano** (PowerShell)…
- **StegExpose** — outil de stéganalyse/détection

**Watermarking vs stéganographie :** le filigrane (watermarking) marque le média pour en revendiquer la propriété (signature de copyright), alors que la stéganographie sert au secret de communication. Un filigrane peut être visible (logo) ou invisible.

**Stéganalyse — contremesures :** utiliser des outils de détection (analyse statistique, comparaison d'histogrammes, StegExpose…), surveiller les fichiers volumineux anormaux, contrôler les canaux d'exfiltration.

### 3.6 Maintien de la persistance (Persistence)

Techniques pour survivre aux redémarrages et conserver l'accès :
- **Clés de registre Run/RunOnce** — exécution au démarrage (Windows)
- **Services** et **drivers** auto-démarrés
- **Tâches planifiées (scheduled tasks)**
- **Scripts de démarrage** (startup items, logon scripts, rc scripts)
- **Fichiers de profil utilisateur** (`.bashrc`, `.bash_profile`…)
- **Planting Flags** : créer des fichiers/drapeaux sur le système pour « marquer » les machines compromises (parfois utilisé dans les environnements de test/examens)

### 3.7 Domination du domaine (Domain Dominance)

Une fois le contrôle d'une machine de domaine obtenu, l'attaquant cherche la **domination complète du domaine** (Domain Controller).

| Technique | Description |
|---|---|
| **Pass-the-Hash (PtH)** | Utiliser le hash NTLM d'un utilisateur pour s'authentifier sans mot de passe |
| **Pass-the-Ticket (PtT)** | Rejouer un TGT/ST volé |
| **Overpass-the-Hash** | Obtenir un TGT à partir du hash NTLM |
| **Golden Ticket** | TGT forgé avec le hash **KRBTGT** → contrôle total et durable du domaine |
| **Silver Ticket** | ST forgé pour un service spécifique |
| **Skeleton Key attack** | Patch de la mémoire de **LSASS** sur le contrôleur de domaine : un « master password » universel est injecté, valide pour **tous les comptes** du domaine |
| **DCSync** | Réplication Active Directory simulée pour extraire les hashes (dont KRBTGT) |
| **Kerberoasting / AS-REP Roasting** | Cracking de tickets pour des comptes de service/AS-REP |

**Skeleton Key — outils :**
- **mimikatz** : `misc::skeleton` (mode interactif) — exécuté avec `privilege::debug`
- **PowerShell (Invoke-Mimikatz)** :
  `Invoke-Mimikatz -Command '"privilege::debug" "misc::skeleton"'`
- **Empire** : module `powershell/persistence/misc/skeleton_key`
- Le mot de passe « master » standard est **`mimikatz`** (toute modification de mot de passe utilisateur par la suite exige de re-patcherafter le master password).

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

### 4.5 Défense contre l'effacement des traces

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
- **DLL hijacking** : exploite l'ordre de recherche des DLL ; défense : chemins absolus.
- Recherche de binaires **SUID** : `find / -perm -u=s -type f 2>/dev/null`.
- **Buffer overflow** : spiking → fuzzing → offset → overwrite EIP → bad chars → bon module → shellcode.
- **Rootkits** : user-mode, kernel-mode, bootkits, hypervisor, firmware ; détection par **signature**, **heuristique/comportement**, **profilage du chemin d'exécution** ; outil emblématique **GMER**.
- **LSB insertion** (bit de poids faible des pixels) et domaine fréquentiel (**DCT/FFT/wavelet**) en stéganographie d'image ; outils **OpenStego**, **Steghide**, **Snow** ; la **stéganalyse** détecte.
- **Skeleton key** : `misc::skeleton` dans mimikatz patche **LSASS** → mot de passe universel pour tous les comptes du domaine.
- **auditpol** : `auditpol /set /category:"system","account logon" /success:disable`.
- **wevtutil cl** efface les logs Windows ; **fsutil behavior set disablelastaccess 1** désactive les timestamps d'accès.
- BASH : `export HISTSIZE=0`, `history -c`, `cat /dev/null > ~/.bash_history && history -c && exit`, `shred ~/.bash_history`.
- Défense : logging centralisé, serveur de logs DMZ, append-only, immutable logging, FIM, SIEM, UEBA.

## Synthèse du module

Ce module a couvert en détail les **quatre phases du system hacking** :

1. **Gaining Access** : cracking de mots de passe (dictionnaire, brute-force, rainbow tables, hybride, rule-based), outils (hashcat, John, THC-Hydra, Responder…), attaques d'authentification Windows/Kerberos (LLMNR/NBT-NS poisoning, SMB relay, Kerberoasting, Pass-the-Ticket…), keyloggers, spyware, établissement de sessions à distance et dissimulation de fichiers (NTFS ADS).
2. **Escalating Privileges** : élévation verticale/horizontale, techniques Windows et Linux (SUID, services vulnérables, DLL hijacking), exploitation de buffer overflows, framework Metasploit (payloads, encoders, evasion) et outils d'audit (WES-NG, BloodHound, Seatbelt).
3. **Maintaining Access** : backdoors, keyloggers/spyware, rootkits (types, détection, outils), stéganographie et stéganalyse, persistance, et domination du domaine (Pass-the-Hash/Ticket, Golden/Silver Ticket, skeleton key, DCSync).
4. **Clearing Logs** : désactivation de l'audit (auditpol), effacement des logs (wevtutil, CCleaner, BleachBit…), désactivation de fonctionnalités Windows (hibernation, pagefile, timestamps), effacement de l'historique BASH, et contremesures défensives (logging centralisé, FIM, SIEM, UEBA).

Le prochain module abordera les **malware threats** (Module 07).
