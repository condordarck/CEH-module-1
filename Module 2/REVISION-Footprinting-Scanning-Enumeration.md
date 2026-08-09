# CEH — FOOTPRINTING, SCANNING & ENUMERATION (FICHIER COMPLET)
# ============================================================

> **Document unique de révision** fusionnant les réponses justifiées, la cartographie
> des outils, les options de commandes et l'aide-mémoire final.
> ⚠️ = question où tu avais faux (0/1) dans le dump — à revoir en priorité.

## PLAN DU FICHIER
1. Partie 1 — Cartographie des outils
2. Partie 2 — Options de commandes (Nmap, hping3, Sublist3r, Photon, etc.)
3. Partie 3 — Série 1 : Footprinting OSINT (justifié, 36Q)
4. Partie 4 — Série 2 : Outils avancés (justifié, 13Q)
5. Partie 5 — Série 3 : Ping / Scanning (justifié, 10Q)
6. Partie 6 — Série 4 : Flags TCP / hping (justifié, 10Q)
7. Partie 7 — Série 5 : Banner grabbing / spoofing (justifié, 8Q)
8. Partie 8 — Série 6 : OS fingerprinting / évasion (justifié, 8Q)
9. Partie 9 — Série 7 : Énumération & ports (justifié, 12Q)
10. Partie 10 — Série 8 : Énumération LDAP (justifié, 6Q)
11. Bonus — Tableaux anti-pièges
12. Aide-mémoire final + Les 13 erreurs à revoir


> Pour chaque question : **pourquoi ce choix** + **ce que font les autres options**.
> Suivi d'une cartographie complète des outils et des options de commandes.

---

## PARTIE 1 — CARTOGRAPHIE DES OUTILS (ce que fait chacun)

### A. Recherche de personnes / OSINT social
| Outil | Ce qu'il fait |
|---|---|
| **Spokeo** | People search : téléphones, emails, adresses, âge, DOB, membres de la famille, profils sociaux, casiers judiciaires. Recherche des personnes appartenant à l'org cible |
| **Sherlock** | Recherche un username sur des centaines de réseaux sociaux et renvoie l'URL complète du profil |
| **BuzzSumo** | Moteur de recherche sociale avancé : trouve le contenu le plus partagé d'un sujet/auteur/domaine sur Twitter, Facebook, LinkedIn, Google+, Pinterest |
| **Gephi** | Visualisation et exploration de graphes/réseaux sociaux, découverte de patterns cachés entre connexions sociales |
| **NodeXL** | Analyse des réseaux sociaux (avec Gephi, SocNetV) pour obtenir des infos critiques sur l'org/users |
| **Mention** | Surveillance de réputation en ligne : surveille le web, médias sociaux, forums, blogs pour en savoir plus sur la marque cible |
| **Google/Bing image search, TinEye** | Reverse image search : trouver la source/origine d'une image, photo, avatar, meme |

### B. Recherche sur le web / archivage / sources publiques
| Outil | Ce qu'il fait |
|---|---|
| **Photon** | Récupère les URLs archivées d'un site depuis archive.org (WayBack Machine) |
| **WayBack Machine (archive.org)** | Archive historique des pages web — on peut y retrouver les URLs internes/supprimées |
| **Sublist3r** | Énumère les sous-domaines d'un domaine via OSINT (Google, Yahoo, Bing, Baidu, Ask, Netcraft, VirusTotal, ThreatCrowd, DNSdumpster, ReverseDNS + brute force SubBrute) |
| **Recon-ng** | Framework de reconnaissance web complet ; récupère fichiers confidentiels depuis les dépôts de code source publics |
| **Infoga** | Collecte d'infos d'emails depuis différentes sources publiques + vérifie si un email a fuité via l'API haveibeenpwned.com |
| **SearchSploit** | Outil en ligne de commande pour Exploit-DB : copie locale de la base d'exploits pour recherche offline |
| **Metagoofil** | Extrait les métadonnées de documents publics (pdf, doc, xls, ppt, docx, pptx, xlsx) |
| **theHarvester** | OSINT pour déterminer la surface d'attaque externe (emails, sous-domaines, hôtes) |
| **cewl** | Récupère une liste de mots uniques présents dans une URL cible (utile pour mots de passe) |
| **Snapback** | Localise l'origine géographique d'un hacker/un réseau |
| **Web mirroring (HTTrack)** | Copie un site web complet en local (hors-ligne) — utile pour footprinting |
| **Octoparse** | Scraping web sans code : transforme des pages web en données structurées |

### C. Footprinting DNS / IP / serveurs
| Outil | Ce qu'il fait |
|---|---|
| **FOCA** | Recherche de métadonnées + fonctionnalités : Web Search, DNS Search, IP Resolution, **PTR Scanning** (trouve serveurs du même segment), Bing IP, Common Names |
| **Spyse** | Plateforme en ligne : sous-domaines, IP, statut HTTP, certifs SSL/TLS, scores de vulnérabilité, records DNS |
| **Professional Toolset (dnsstuff)** | Interrogation DNS |
| **SecurityTrails** | Énumération DNS avancée : carte DNS, records A/AAAA/NS/MX/SOA/TXT historiques et actuels |
| **Netcraft** | Anti-phishing, services de sécurité Internet, test d'applications, scan PCI ; détecte aussi l'OS |
| **Shodan / Censys** | Détection de l'OS et des devices connectés |
| **Reverse Lookup** | Reverse IP lookup : prend une IP, localise le record DNS PTR |
| **DNSRecon** | Énumération DNS (records, sous-domaines, zone transfers) |
| **Nmap / Zenmap** | Scanner réseau : hôtes, ports, services, OS, scripts (NSE) |
| **Unicornscan** | Identification de l'OS via les valeurs TTL du résultat de scan |
| **Fing** | App mobile (Android/iOS) : IP, MAC, vendor du device, localisation FAI, scan Wi-Fi |
| **Hping2/Hping3** | Packet crafting TCP/IP : scan, firewall testing, traceroute, OS fingerprinting, ISN |

### D. Plateformes / référentiels / bases de données
| Outil | Ce qu'il fait |
|---|---|
| **GitLab (GitHub, SourceForge, BitBucket)** | Dépôts de code source publics contenant configs, clés SSH/SSL privées, libs dynamiques |
| **WHOIS lookup** | Interroge les bases des assignés d'une ressource Internet : infos personnelles du propriétaire du domaine, RIRs, port 43/TCP |
| **ExoneraTor** | Recherche deep/dark web : infos gouvernementales confidentielles (cartes de crédit, passeports, SSN) en anonyme |
| **NNTP Usenet newsgroups** | Dépôt de notes/messages soumis par les utilisateurs sur divers sujets |
| **investing.com (Google Finance, MSN, Yahoo)** | Valeur boursière, profil société, infos concurrents, rapports financiers |
| **Spyse** | (voir C) collecte/analyse d'infos sur devices et sites |
| **OSRFramework** | Suite de scripts : usufy (profils sur 290 plateformes), mailfy (emails), searchfy (requêtes), domainfy (domaines), phonefy (téléphones), entify (entités) |
| **Recon-Dog** | Tout-en-un : Censys, NS lookup, port scan, détection CMS, Whois, honeypot (shodan), sous-domaines, reverse IP, technologies (wappalyzer) |
| **GHDB (Google Hacking Database)** | Base d'opérateurs Google pour le google hacking |
| **SecurityTrails** | (voir C) historique DNS |

### E. Énumération / annuaires
| Outil | Ce qu'il fait |
|---|---|
| **AD Explorer** | Énumération LDAP/AD : accès aux annuaires, listes des objets, filtres |
| **ldapsearch (Ladpsearch)** | Outil ligne de commande LDAP : énumération des users AD avec filtres |
| **SuperScan / SoftPerfect / Nsauditor** | Scanners réseau/ports (pas LDAP) |
| **nbtstat** | Statistiques NetBIOS |
| **PortQry** | Interrogation de ports |

### F. Autres outils croisés (pièges)
| Outil | Ce qu'il fait | Attention |
|---|---|---|
| **Burp Suite** | Plateforme de test de sécurité web (mapping + exploitation) | PAS du footprinting archive |
| **Nikto** | Scanner de serveur web (6700+ fichiers dangereux) | PAS du people search |
| **KFSensor** | Honeypot IDS Windows qui simule des services vulnérables | PAS du people search |
| **ShellPhish** | Outil de phishing de credentials sociaux | PAS du footprinting code source |
| **BeRoot** | Post-exploitation : vérifie les misconfigurations pour escalade de privilèges | PAS du footprinting |
| **OpUtils** | Énumération SNMP / supervision IT | PAS du social search |
| **Vindicate** | Détection de spoofing LLMNR/NBNS/mDNS | PAS du social search |
| **Robber** | Trouve des exécutables sujets au DLL hijacking | PAS du social search |
| **DroidSniff** | App Android : capture de comptes sur réseaux sans fil | PAS Exploit-DB |
| **Wireshark** | Capture et analyse de trafic réseau | PAS du social search |
| **Maltego** | Relations et liens réels entre personnes/orgs/sites/infrastructure | PAS app mobile |
| **THC-Hydra** | Craqueur de login parallélisé multi-protocoles | PAS footprinting |
| **L0phtCrack** | Audit/récupération de mots de passe Windows | PAS footprinting |
| **Nagios** | Monitoring infrastructure (SAN, disques, RAID) | PAS footprinting |
| **Zimperium zIPS** | IPS mobile (iOS/Android) | PAS plateforme OSINT |
| **FTK Imager** | Preview/imaging forensique | PAS plateforme OSINT |
| **Dependency Walker** | Débogage des modules Windows (chargement/exécution) | PAS plateforme OSINT |
| **GFI LanGuard** | Scan de vulnérabilités réseau + gestion | PAS people search |
| **OpenVAS** | Framework de scan de vulnérabilités | PAS people search |
| **Cain & Abel / hashcat / John the Ripper** | Craquage de mots de passe | PAS scan réseau |
| **DuckDuckGo / Bing / Yahoo** | Moteurs de recherche | « Google hacking » = opérateurs avancés |


---

## PARTIE 2 — OPTIONS DE COMMANDES

### Nmap / Zenmap
```
nmap [type de scan] [options] [cible]
```
| Option | Signification |
|---|---|
| `-sS` | TCP SYN scan (stealth scan) — half-open, ne complète pas le handshake |
| `-sT` | TCP Connect scan — handshake complet puis RST |
| `-sU` | UDP scan |
| `-sA` | ACK scan (probe ACK) |
| `-sY` | SCTP INIT scan |
| `-sZ` | SCTP COOKIE ECHO scan |
| `-sL` | List scan (liste des hôtes sans scan) |
| `-O` | OS fingerprinting (détection d'OS) |
| `-A` | Détection OS + services + versions + traceroute + scripts NSE |
| `-P0` / `-Pn` / `-PN` | Skip host discovery (pas de ping, considère l'hôte actif) |
| `-n` | Pas de résolution DNS (accélère le scan) |
| `-p` | Spécifier les ports (ex: `-p 80`, `-p1-65535`) |
| `--spoof-mac 0` | Génère une MAC **aléatoire** attachée aux paquets |
| `--spoof-mac [MAC]` | Fixe manuellement une MAC |
| `-v` | Verbose |
| `-D` | IP decoy (adresses de leurre) |
| `-f` | Fragmentation des paquets (évasion) |
| `--delay <time>` | Délai entre les probes (évasion IDS/IPS à seuil) |
| `--rate <rate>` | Envoie les probes à un débit donné |
| `-sV` | Détection de version de services |
| `-oG / -oN / -oX` | Formats de sortie (grepable, normal, XML) |

### hping3
```
hping3 [options] [cible]
```
| Option | Signification |
|---|---|
| `-1` | ICMP ping |
| `-2` | UDP scan (ex: `-2 10.0.0.25 -p 80`) |
| `-A` | ACK scan (ex: `-A 10.0.0.25 -p 80`) |
| `-S` | SYN scan (ex: `-8 50-60 -S <IP> -V`) |
| `-8` | Scan d'une plage de ports |
| `-Q` `-s` | Collecte du numéro de séquence initial (ISN) |
| `--tcp-timestamp` | Test firewall/timestamps TCP |
| `-V` | Verbose |
| `-p` | Port cible |

### Sublist3r
```
sublist3r [-d DOMAIN] [-b BRUTEFORCE] [-p PORTS] [-v VERBOSE] [-t THREADS] [-e ENGINES] [-o OUTPUT]
```
| Option | Longue | Signification |
|---|---|---|
| `-d` | `--domain` | Domaine dont on énumère les sous-domaines |
| `-b` | `--bruteforce` | Active le module brute force SubBrute |
| `-p` | `--ports` | Scanne les sous-domaines trouvés sur des ports TCP spécifiques |
| `-v` | `--verbose` | Mode verbeux, résultats en temps réel |
| `-t` | `--threads` | Nombre de threads pour le brute force SubBrute |
| `-e` | `--engines` | Liste des moteurs de recherche séparés par virgules |
| `-o` | `--output` | Sauvegarde les résultats dans un fichier texte |

### Photon
```
photon.py -u <URL cible> -l <niveau> -t <threads> --wayback
```
- `-u` : URL cible | `-l` : niveau de profondeur | `-t` : threads | `--wayback` : récupère les URLs archivées depuis archive.org

### theHarvester
- `theHarvester -d microsoft.com -l 200 -b linkedin` → énumère les users LinkedIn
- `theHarvester -d microsoft.com -l 200 -b baidu` → emails de microsoft.com via Baidu

### FOCA
| Fonction | Rôle |
|---|---|
| Web Search | Cherche hôtes et domaines via les URLs liées au domaine principal |
| DNS Search | Vérifie les hôtes configurés dans NS, MX, SPF pour découvrir de nouveaux hôtes/domaines |
| IP Resolution | Résout chaque hostname via DNS pour obtenir l'IP (analyse DNS interne) |
| **PTR Scanning** | **Trouve d'autres serveurs dans le même segment d'une adresse** (scan PTR) |
| Bing IP | Cherche de nouveaux domaines associés à une IP |
| Common Names | Attaque par dictionnaire contre le DNS |

### OSRFramework
- `usufy.py` → vérifie un profil utilisateur sur 290 plateformes
- `mailfy.py` → vérifie l'existence d'un email
- `searchfy.py` → **fait une requête sur les plateformes d'OSRFramework**
- `domainfy.py` → vérifie l'existence de domaines
- `phonefy.py` → vérifie l'existence d'une série de téléphones
- `entify.py` → extrait des entités avec des expressions régulières

### Recon-Dog
- Censys (censys.io) : infos massives sur une IP | NS lookup | Port scan | Détection CMS (400+) | Whois lookup | Détection honeypot (shodan.io) | Find subdomains (findsubdomains.com) | Reverse IP lookup | **Detect technologies (wappalyzer.com)** | All : toutes les fonctions

### Opérateurs Google (google hacking)
| Opérateur | Effet | Exemple |
|---|---|---|
| `site:` | Restreint au domaine/site | `site:certifiedhacker.com` |
| `-` | Exclut un terme/domaine | `site:target.com -site:Marketing.target.com` |
| `intext:` | Mot dans le texte de la page | `intext:*@*.com:*` |
| `intitle:` / `allintitle:` | Mot dans le titre | `intitle:"SQL Injection"` |
| `inurl:` / `allinurl:` | Mot dans l'URL | `allinurl: pastebin.com` |
| `filetype:` / `ext:` | Type de fichier | `filetype:xml`, `ext:conf` |
| `related:` | Pages similaires | `related:"SQL Injection"` |
| `cache:` | Version en cache de la page | `cache:pastebin.com` |
| `"..."` | Phrase exacte | `"SQL Injection"` |

### DNS records (footprinting)
| Record | Rôle |
|---|---|
| A | Pointe vers l'adresse IP d'un hôte |
| AAAA | Pointe vers une adresse IPv6 |
| MX | Pointe vers le serveur mail du domaine |
| NS | Pointe vers le name server de l'hôte |
| CNAME | Canonical name : permet des alias vers un hôte |
| **SOA** | Start Of Authority : **indique l'autorité d'un domaine** |
| SRV | Service records |
| PTR | Mappe une IP vers un hostname |
| RP | Personne responsable |
| HINFO | Type de CPU et OS de l'hôte |
| TXT | Records de texte non structurés |

### Ports réservés importants
| Port | Protocole | Service |
|---|---|---|
| 21/TCP | FTP | Transfert de fichiers |
| 22/TCP | SSH | Shell sécurisé |
| 23/TCP | Telnet | Connexion non sécurisée |
| 25/TCP | SMTP | Envoi de mail |
| 53/TCP+UDP | DNS | Résolution de noms |
| 69/TCP | TFTP | Trivial File Transfer |
| 79/TCP | Finger | Infos utilisateurs |
| **88/TCP** | **Kerberos** | **Authentification réseau** |
| 123/TCP | NTP | Synchronisation temps |
| 135/TCP+UDP | RPC | Appels de procédure |
| 137/UDP | NetBIOS-NS | Résolution de noms NetBIOS (**WINS**) |
| **139/TCP** | NetBIOS-SSN | **Session NetBIOS : null-session + partage fichiers/imprimantes** |
| 161/UDP | SNMP | Supervision réseau |
| **179/TCP** | **BGP** | **Sessions entre routeurs, grandes tables de routage (FAI)** |
| 389/TCP+UDP | **LDAP** | Annuaire |
| 443/TCP | HTTPS | Web sécurisé |
| **500/UDP** | ISAKMP/IKE | **IPSec** |
| 514/UDP | syslog | Envoi de logs |
| 515/TCP | LPD | Impression (printer) |
| 631/TCP | IPP | Impression Internet |
| 9100/TCP | Raw printing | Impression directe |


---

## PARTIE 3 — SÉRIE 1 : FOOTPRINTING OSINT (36 questions justifiées)

**Q1. Outil de recherche par image (source/origine) → TinEye**
- *Pourquoi* : TinEye est un outil de « reverse image search » (avec Google Image Search, Yahoo, Bing).
- *Autres* : **Mention** = surveillance de réputation/ marque. **Intelius** = people search. **Sublist3r** = énumération de sous-domaines.

**Q2. Valeur boursière, profil société, infos concurrents → investing.com**
- *Pourquoi* : services financiers (Google Finance, MSN Money, Yahoo Finance, Investing.com) fournissent valeur boursière, profil, concurrents, taux de change, rapports financiers.
- *Autres* : **indeed.com, dice.com, linkup.com** = sites de recherche d'emploi en ligne (job services).

**Q3. Infos des bases gouvernementales/fédérales en anonyme → ExoneraTor**
- *Pourquoi* : outils de recherche deep/dark web (Tor Browser, ExoneraTor, OnionLand) pour données confidentielles (cartes, passeports, SSN).
- *Autres* : **Spokeo, Been Verified, Whitepages** = services people search (pas le dark web).

**Q4. Dépôt de notes/messages soumis par utilisateurs → NNTP Usenet newsgroups**
- *Pourquoi* : les newsgroups Usenet (NNTP) sont un dépôt de notes/messages sur divers sujets.
- *Autres* : **People search services** = noms/adresses/contacts. **Business profile sites** = infos business d'une région. **Online reputation services** = surveiller ce que les gens disent de la marque.

**Q5. ⚠️ Activité de l'org qui permet de footprinter le type de business → Background checks to hire employees**
- *Pourquoi* : « Background check to hire employees → Type of business ». Tableau clé :
  - User surveys → stratégies business | Promote products → profil produit | User support → social engineering | Recruitment → infos plateforme/technologie | **Background check → type de business**
- *Autres* : **Promotion of products** = profil produit. **User support** = social engineering. **User surveys** = stratégies business.

**Q6. Activité d'un user révélant famille + intérêts → Sharing photos and videos**
- *Pourquoi* : « Share photos and videos → identité des membres de la famille, intérêts ».
- *Autres* : **Maintain profile** = infos contact/localisation. **Play games/join groups** = intérêts. **Create events** = activités.

**Q7. Examen des cookies → Software in use and its behavior**
- *Pourquoi* : les cookies révèlent le logiciel utilisé et son comportement ; le nom/valeur/domaine des cookies et les sessions permettent d'identifier la plateforme de scripting.
- *Autres* : **HTML source code** = contact développeur/admin, structure système de fichiers, script type, commentaires. → C'est l'examen du **code source** (pas des cookies) qui donne contact admin, structure FS, commentaires.

**Q8. ⚠️ URLs internes / départements → Sublist3r**
- *Pourquoi* : Sublist3r énumère les sous-domaines via OSINT (Google, Yahoo, Bing, Baidu, Ask, Netcraft, VirusTotal, ThreatCrowd, DNSdumpster, ReverseDNS) + brute force SubBrute. Les sous-domaines internes (intranet, RH, marketing…) révèlent les départements.
- *Autres* : **WayBackMachine (archive.org)** = URLs archivées/anciennes pages. **Website mirroring** = copie locale du site. **Email tracking** = suivi d'emails/IP du destinataire.

**Q9. ⚠️ Pages Wikipédia contenant SQL/injection → SQL injection site:Wikipedia.org**
- *Pourquoi* : `site:` restreint au domaine wikipedia.org ; la requête cherche la phrase dans tout le contenu. L'énoncé veut TOUTES les pages avec « SQL », « injection attacks » OU « SQL injection techniques » → pas de restriction intitle.
- *Autres* : **intitle:** restreint au titre (exclut les pages où le terme n'est que dans le texte). **related:** = pages similaires. **allinurl:** = tous les mots dans l'URL.

**Q10. Bases de données personnelles des propriétaires de domaines → WHOIS lookup**
- *Pourquoi* : WHOIS est un protocole requête/réponse (port 43/TCP) interrogeant les bases des assignés d'une ressource Internet (nom de domaine, bloc IP, AS). RIRs maintiennent ces bases.
- *Autres* : **Metadata extraction** = métadonnées de fichiers. **Traceroute** = chemin des paquets. **Web spidering** = exploration/crawl du web.

**Q11. Infos d'un email tracking → IP du destinataire, géolocation, proxy, OS, navigateur**
- *Pourquoi* : les outils de suivi d'email collectent IP système du destinataire, géolocation, email reçu/lu, durée de lecture, détection de proxy, liens, OS et navigateur, transfert, type de device.
- *Autres* : **archives des pages web** (WayBack) ; **extraction URL/meta pour promotion** ; **username/OS/emails/logiciels** (autre contexte).

**Q12. Mails listés sur pastebin → site:pastebin.com intext:*@*.com:***
- *Pourquoi* : `site:` restreint à pastebin.com et `intext:*@*.com:*` cherche le motif email dans le texte.
- *Autres* : **intitle:** dans le titre (pas bon pour emails dans le texte). **cache:** version en cache. **allinurl:** tous les mots dans l'URL.

**Q13. Record DNS d'autorité d'un domaine → SOA**
- *Pourquoi* : SOA (Start Of Authority) = indique l'autorité pour un domaine.
- *Autres* : **CNAME** = alias. **PTR** = IP→hostname. **SRV** = records de service.

**Q14. Record pointant vers l'IP d'un hôte → A**
- *Autres* : **NS** = name server. **TXT** = texte. **HINFO** = CPU/OS.

**Q15. ⚠️ Approche directe = source primaire de renseignement concurrentiel → Social engineering**
- *Pourquoi* : l'approche DIRECTE (salons professionnels, social engineering des employés/clients) est la source primaire.
- *Autres* : **Search engines, Internet, online databases / Support threads / Social media postings** = toutes des techniques de l'approche **INDIRECTE**.

**Q16. Email leaké via haveibeenpwned → Infoga**
- *Pourquoi* : Infoga collecte des infos d'emails depuis des sources publiques et vérifie via l'API haveibeenpwned.com.
- *Autres* : **Metagoofil** = métadonnées de documents publics. **Professional Toolset** = interrogation DNS. **Octoparse** = scraping web.

**Q17. `site:target.com -site:Marketing.target.com accounting` → accounting sur target.com mais PAS sur Marketing.target.com**
- *Pourquoi* : `site:` restreint au domaine ; `-site:` **exclut** le sous-domaine. Le `-` devant un opérateur = exclusion.

**Q18. Rechercher tous fichiers d'un domaine → site: certifiedhacker.com filetype:xml | filetype:conf | ...**
- *Pourquoi* : `filetype:` restreint aux pages dont le nom se termine par cette extension — c'est la bonne syntaxe pour les fichiers.
- *Autres* : **ext:** = variante (ici non listée en 1er choix). **intext:** = dans le texte (pas le type de fichier). **allinurl:** = dans l'URL.

**Q19. Sortie des moteurs de recherche → SERPs**
- *Pourquoi* : Search Engine Results Pages (SERPs) = la liste de résultats retournée.

**Q20. Créer des requêtes complexes → Google hacking**
- *Pourquoi* : le Google hacking = utilisation des opérateurs avancés de Google pour des requêtes complexes et extraire des infos sensibles/cachées.
- *Autres* : **DuckDuckGo/Bing/Yahoo** = simples moteurs de recherche.

**Q21. Employés : téléphones, emails, adresses, DOB, famille, profils sociaux → Spokeo**
- *Pourquoi* : Spokeo = people search service avec exactement ces infos.
- *Autres* : **Nikto** = scanner serveur web. **KFSensor** = honeypot IDS. **Photon** = URLs archivées.

**Q22. Observer avec jumelles le PIN → Shoulder surfing**
- *Pourquoi* : technique d'observer quelqu'un taper ses infos (par-dessus l'épaule), parfois avec jumelles/caméras.
- *Autres* : **Phishing** = faux sites/emails. **Dumpster diving** = fouiller les poubelles. **Tailgating** = suivre quelqu'un dans un accès physique.

**Q23. Identité expéditeur, mail server, IP, localisation → Email tracking tools**
- *Pourquoi* : les outils de tracking collectent IP, serveurs mail, FAI.
- *Autres* : **Web updates monitoring** = surveille les mises à jour de sites. **Metadata extraction** = métadonnées de fichiers. **Website mirroring** = copie du site.

**Q24. Protocole requête/réponse des bases des assignés d'une ressource → Whois lookup**
- *Pourquoi* : WHOIS (port 43/TCP), base maintenue par les RIRs.
- *Autres* : **TCP/IP** = suite de protocoles réseau. **Traceroute** = chemin des paquets. **DNS lookup** = zone data DNS.

**Q25. Username sur réseaux sociaux + URL → Sherlock**
- *Pourquoi* : Sherlock cherche un username sur de nombreux réseaux sociaux et renvoie l'URL complète.
- *Autres* : **OpUtils** = énumération SNMP/supervision. **BeRoot** = escalade de privilèges post-exploitation. **Sublist3r** = sous-domaines.

**Q26. Fichiers confidentiels depuis dépôts de code source → Recon-ng**
- *Pourquoi* : framework de reconnaissance qui collecte des infos depuis les dépôts de code source publics.
- *Autres* : **Reverse Lookup** = reverse IP/PTR. **Netcraft** = anti-phishing. **ShellPhish** = phishing de credentials sociaux.

**Q27. Visualiser graphes/patterns sociaux → Gephi**
- *Pourquoi* : Gephi explore/visualise les graphes et réseaux sociaux.
- *Autres* : **Netcraft** = anti-phishing. **Mention** = surveillance de marque. **theHarvester** = OSINT surface d'attaque.

**Q28. Géolocalisation routeurs/serveurs/IP → Traceroute tools**
- *Pourquoi* : traceroute trace les routeurs traversés, RTT, noms, affiliations réseau, localisations géographiques (hop-by-hop, reverse tracing, ping plotting, etc.).

**Q29. Contenu le plus partagé sur les réseaux sociaux → BuzzSumo**
- *Pourquoi* : BuzzSumo = moteur de recherche sociale avancée du contenu le plus partagé.
- *Autres* : **Wireshark** = capture de trafic. **Vindicate** = détection spoofing LLMNR/NBNS/mDNS. **Robber** = DLL hijacking.

**Q30. Chercher des personnes de l'org cible → Spokeo**
- *Autres* : **GFI LanGuard** = scan vulnérabilités. **OpenVAS** = framework vulnérabilités. **Netcraft** = anti-phishing / détection OS.

**Q31. Outil CLI Exploit-DB en local → SearchSploit**
- *Pourquoi* : SearchSploit = copie locale de la base Exploit-DB pour recherche offline.
- *Autres* : **Spokeo** = people search. **DroidSniff** = capture comptes Android. **Spyse** = plateforme devices/sites.

**Q32. Référentiel en ligne : clés SSH/SSL + libs dynamiques → GitLab**
- *Pourquoi* : les dépôts de code source (GitHub, GitLab, SourceForge, BitBucket) contiennent configs, clés SSH/SSL privées, code source, libs dynamiques.
- *Autres* : **Sublist3r** = sous-domaines. **MITRE ATT&CK** = base de connaissances des tactiques adverses. **BeRoot** = escalade de privilèges.

**Q33. Construire/analyser réseaux sociaux → NodeXL**
- *Pourquoi* : Gephi, SocNetV, NodeXL = outils d'analyse de réseaux sociaux.
- *Autres* : **Burp Suite** = test sécurité web. **Mention** = surveillance de marque. **HTTrack** = copie de site.

**Q34. ⚠️ URLs archivées depuis archive.org → Photon**
- *Pourquoi* : Photon récupère les URLs archivées depuis archive.org.
- *Autres* : **Gephi** = graphes sociaux. **Netcraft** = anti-phishing. **Burp Suite** = test web.

**Q35. Commande pour URLs archivées → photon.py -u http//www.certifiedhacker.com -1 3 -t 200 --wayback**
- *Pourquoi* : `--wayback` + URL = récupération des URLs archivées.
- *Autres* : **theHarvester -b linkedin** = users LinkedIn ; **-b baidu** = emails via Baidu. **cewl** = mots uniques du site.

**Q36. URLs archivées → Photon**
- *Autres* : **Burp Suite** = test web. **SecurityTrails** = DNS historique. **Sublist3r** = sous-domaines.


---

## PARTIE 4 — SÉRIE 2 : OUTILS DE FOOTPRINTING AVANCÉS (13 justifiées)

**Q1. FOCA : serveurs du même segment → PTR scanning**
- *Pourquoi* : « PTR Scanning - Finds more servers in the same segment of a determined address ».
- *Autres* : **Web Search** = hôtes/domaines via URLs liées. **DNS Search** = hôtes dans NS/MX/SPF. **IP Resolution** = résout hostname en IP.

**Q2. Plateforme en ligne devices/websites → Spyse**
- *Autres* : **Zimperium zIPS** = IPS mobile. **FTK Imager** = imaging forensique. **Dependency Walker** = débogage modules Windows.

**Q3. Collecter sous-domaines, IP, HTTP, SSL/TLS, vuln scores, DNS → Spyse**
- *Autres* : **THC-Hydra** = craqueur de login. **L0phtCrack** = audit mots de passe Windows. **Nagios** = monitoring (SAN/RAID).

**Q4. Contremesure footprinting → Configure mail servers to ignore mails from anonymous individuals**
- *Pourquoi* : contre-mesures listées : désactiver geo-tagging, supprimer comptes des employés partis, ignorer les mails anonymes, garder le profil de domaine privé.
- *Autres* : les 3 autres sont des MAUVAISES pratiques (profil public, comptes gardés, geo-tagging activé).

**Q5. Défense contre footprinting → Disable or delete accounts of employees who left**
- *Pourquoi* : compte employé parti doit être désactivé/supprimé.
- *Autres* : **ne jamais utiliser TCP/IP/IPsec** = faux. **toujours activer les protocoles inutiles** = faux. **révéler sa localisation** = faux.

**Q6. Sublist3r : liste de moteurs → -e (--engines)**
- *Pourquoi* : `-e --engines` = liste de moteurs séparés par virgules.
- *Autres* : **-o** = fichier de sortie. **-p** = scan ports. **-d** = domaine.

**Q7. À NE PAS suivre → Enabling the geo-tagging functionality on cameras**
- *Pourquoi* : il FAUT désactiver le geo-tagging pour éviter la géolocalisation. Question « should NOT be followed » → choisir la mauvaise pratique.
- *Autres* : opt for privacy services (Whois), éduquer employés à utiliser des pseudonymes, ne pas révéler d'infos critiques = bonnes pratiques.

**Q8. Contremesure confidentialité → Avoiding domain-level cross-linking for critical assets**
- *Pourquoi* : contremesures listées : éviter le cross-linking de domaines pour les actifs critiques, désactiver directory listings, garder le profil privé, etc.
- *Autres* : **Enabling directory listings** = mauvais. **Profil public** = mauvais. **Géolocalisation activée** = mauvais.

**Q9. ⚠️ Requête sur les plateformes OSRFramework → searchfy.py**
- *Pourquoi* : searchfy.py = « Performs a query on the platforms in OSRFramework ».
- *Autres* : **usufy.py** = profil user sur 290 plateformes. **mailfy.py** = existence d'un email. **domainfy.py** = existence de domaines.

**Q10. Recon-Dog : détecter technologies → wappalyzer.com**
- *Pourquoi* : « Detect technologies: Uses wappalyzer.com to detect 1000+ technologies ».
- *Autres* : **Whois lookup** = whois. **findsubdomains.com** = sous-domaines. **shodan.io** = honeypot.

**Q11. Sublist3r : liste de moteurs → -e** (idem Q6)

**Q12. FOCA : serveurs même segment → PTR scanning** (idem Q1)

**Q13. Protéger contre footprinting → Configure mail servers to ignore mails from anonymous individuals** (idem Q4)

---

## PARTIE 5 — SÉRIE 3 : PING / SCANNING RÉSEAU (10 justifiées)

**Q1. Ping efficace quand ICMP ECHO bloqué → ICMP address mask ping scan**
- *Pourquoi* : comme le timestamp ping, l'address mask ping identifie les hôtes actifs quand l'ECHO est bloqué.
- *Autres* : **ICMP ECHO ping scan** = envoyer des ECHO requests (bloqué par admin ici). **Ping sweep** = ECHO à plusieurs hôtes. **UDP ping scan** = envoi de paquets UDP (pas une méthode « ping » ICMP classique ici).

**Q2. Port 88/TCP qui vérifie l'identité → Kerberos**
- *Autres* : **TFTP** = 69. **Finger** = 79. **NTP** = 123.

**Q3. Handshake complet puis RST → TCP connect scan**
- *Pourquoi* : le connect scan établit une connexion complète (3-way handshake) puis ferme avec RST.
- *Autres* : **Stealth scan** = reset avant la fin du handshake (half-open). **ACK flag probe** = analyse TTL/WINDOW des RST. **IDLE/IPID** = scan aveugle avec IPID.

**Q4. ⚠️ Nmap SCTP COOKIE ECHO → -sZ**
- *Autres* : **-sY** = SCTP INIT. **-sU** = UDP. **-sL** = list scan.

**Q5. Source spoofée pour déterminer les services dispo → IDLE/IPID header scan**
- *Pourquoi* : l'IDLE scan envoie une adresse source spoofée (via une machine zombie) pour un scan aveugle complet.
- *Autres* : **ACK flag probe** = n'utilise pas de spoof, analyse TTL/WINDOW des RST. **Inverse TCP flag** = FIN/URG/PSH. **TCP Maimon** = FIN/ACK (BSD).

**Q6. UDP scan : ICMP Type 3 Code 3 → UDP port is closed**
- *Pourquoi* : port UDP fermé → ICMP Port Unreachable (Type 3, Code 3). Si port ouvert → pas de réponse. Si rien → open|filtered.
- *Autres* : hôte ne répond pas ICMP = pas de réponse du tout ; firewall drop = pas de réponse ; port ouvert = pas de réponse.

**Q7. `nmap -n -sS -P0 -p 80` → Stealth scan**
- *Pourquoi* : **-sS** = SYN scan = stealth scan (half-open).
- *Autres* : Quick/Intense/Comprehensive = profils Zenmap différents (contiennent plus d'options).

**Q8. Ports 21,23,80,139,515,631,9100 → The host is likely a printer**
- *Pourquoi* : ports **515 (LPD)** et **9100 (raw printing)** + 631 (IPP) → imprimante.
- *Autres* : routeur/Linux/Windows n'ouvrent pas typiquement 515/9100 de façon dominante.

**Q9. ⚠️ Classe C bloquant ICMP + fingerprinting + services → NMAP -PN -A -O -sS 192.168.2.0/24**
- *Pourquoi* : **-PN** (No Ping, skip host discovery) car ICMP bloqué ; **-A** = OS + services + versions + scripts ; **-O** = OS fingerprinting ; **-sS** = SYN scan ; **/24** = classe C (192.168.2.0/24, 256 hôtes).
- *Pourquoi pas -P0* : dans l'explication CEH, -Pn = No ping (skip host discovery) alors que -P0 (IP Protocol Ping) envoie des paquets IP avec un numéro de protocole. La bonne réponse CEH = -PN.
- *Autres* : -P0 -A -O -p1-65535 192.168.0/24 (mauvais /24, pas de -sS) ; -PN -O -sS -p 1-1024 (ports limités, pas de -A) ; -P0 -A -sT -p0-65535 (pas -sS, pas -O, /16).

**Q10. Logs vers un outil derrière un firewall → UDP 514 (syslog)**
- *Pourquoi* : syslog écoute sur UDP 514.
- *Autres* : **UDP 123** = NTP. **415/541** = non standards pour syslog.

---

## PARTIE 6 — SÉRIE 4 : FLAGS TCP / HPING / NMAP (10 justifiées)

**Q1. Flag confirmant réception + prochain seq number → ACK**
- *Pourquoi* : ACK confirme la réception et identifie le prochain numéro de séquence attendu (valeur 1 = à surveiller).
- *Autres* : **SYN** = nouveau seq number / établissement. **FIN** = fin des transmissions. **RST** = erreur/abandon.

**Q2. Flag nouveau seq number + établissement → SYN**
- *Autres* : **PSH** = push des données. **RST** = erreur. **FIN** = fin.

**Q3. ⚠️ Vérifier les services en envoyant des messages pour s'introduire → Port scanning**
- *Pourquoi* : définition CEH exacte du port scanning : « checking the services running on the target computer by sending a sequence of messages in an attempt to break in ».
- *Autres* : **Network scanning** = identifier les hôtes actifs. **Vulnerability scanning** = identifier les vulnérabilités exploitables. **Banner grabbing** = déterminer l'OS.

**Q4. Flag annonçant plus de transmissions → FIN**
- *Autres* : **ACK** = réception. **SYN** = établissement. **RST** = erreur.

**Q5. Objectif qui N'EST PAS du network scanning → Discover usernames and passwords**
- *Pourquoi* : objectifs = hôtes vivants/IP/ports, OS/architecture (fingerprinting), services, applications/versions, vulnérabilités.
- *Autres* : **hôtes vivants** et **services** = objectifs réels.

**Q6. hping : collecter ISN → hping3 192.168.1.103 -Q -p 139 -s**
- *Autres* : **-A** = ACK scan. **-2** = UDP scan. **-S --tcp-timestamp** = firewall/timestamps.

**Q7. App mobile Android/iOS infos réseau → Fing**
- *Pourquoi* : Fing = IP, MAC, vendor, ISP location, discovery des devices Wi-Fi.
- *Autres* : **Netcraft** = anti-phishing. **Maltego** = relations réelles. **Nmap** = scanner PC.

**Q8. ⚠️ Ping bloqué (ICMP désactivé) → Hping**
- *Pourquoi* : Hping2/Hping3 = packet crafting TCP/IP, peut faire un scan ACK (-A) pour obtenir une réponse RST d'un hôte vivant quand l'ICMP est bloqué.
- *Autres* : **Traceroute** = chemin des paquets. **TCP ping** = pas un outil standard ; **Broadcast ping** = ICMP (bloqué).

**Q9. Meilleur outil open-source pour scanner un réseau → NMAP**
- *Pourquoi* : Nmap = découverte d'hôtes et de services, carte du réseau.
- *Autres* : **Cain & Abel, hashcat, John the Ripper** = craquage de mots de passe.

**Q10. hping3 : scan ACK → hping3 -A <IP> -p 80**
- *Autres* : **-1** = ICMP ping. **-2** = UDP scan. **-8 50-60 -S** = SYN scan d'une plage.


---

## PARTIE 7 — SÉRIE 5 : CONTREMESURES BANNER GRABBING / SPOOFING (8 justifiées)

**Q1. Contremesure banner grabbing → Use ServerMask tools to disable or change banner information**
- *Pourquoi* : contremesures listées : faux banners, éteindre les services inutiles, ServerMask pour désactiver/changer les infos du banner, désactiver détails vendor/version.
- *Autres* : **Turn on unnecessary services** = faux (il faut les éteindre). **Never display false banners** = faux (il FAUT afficher de faux banners). **Enable details of vendor/version** = faux (il faut les désactiver).

**Q2. ⚠️ Bloquer les paquets SORTANTS avec source externe → Egress filtering**
- *Pourquoi* : **Egress filtering** = empêche le spoofing en bloquant les paquets sortants dont la source n'est pas interne.
- *Autres* : **Ingress filtering** = empêche le trafic spoofé d'ENTRER sur Internet (paquets entrants). **Random ISN** = nombres de séquence aléatoires contre la prédiction d'ISN. **ACLs** = contrôle d'accès général.

**Q3. Rendre le réseau vulnérable au port scanning → Avoid using proxy servers to block fragmented or malformed packets**
- *Pourquoi* : la question demande la MAUVAISE pratique. Il FAUT utiliser des proxys pour bloquer les paquets fragmentés/malformés.
- *Autres* : **fragtest/fragroute** = test du firewall/IDS (bonne pratique). **firewalls commerciaux** = bonne pratique. **bloquer ICMP entrant + ICMP type-3 sortant** = bonne pratique.

**Q4. Prévenir le banner grabbing sur l'hôte → Modify Server Tokens from Full to Prod**
- *Pourquoi* : Server Tokens = Prod → ne divulgue pas la version du serveur Apache.
- *Autres* : **Never display false banners** = faux. **Turn on unnecessary services** = faux. **Never use server masking tools** = faux.

**Q5. Rendre le système vulnérable au banner grabbing → Enable HTTP methods such as Connect, Put, Delete, Options**
- *Pourquoi* : il FAUT les désactiver. Les activer = vulnérabilité.
- *Autres* : **ServerSignature Off**, **mod_headers pour changer le banner**, **désactiver les détails vendor/version** = bonnes pratiques.

**Q6. Contremesure divulgation via banner grabbing → Display false banners**
- *Pourquoi* : contremesures : faux banners, éteindre services inutiles, ServerMask.
- *Autres* : **Disable DNS zone transfers** = contre l'énumération DNS. **Disable open relay** = contre l'énumération SMTP. **RestrictNullSessAccess** = contre l'énumération SMB. → Ce sont des contremesures d'ÉNUMÉRATION, pas de banner grabbing.

**Q7. Défense contre port scanning → Ensure that TCP wrappers limit access based on domain names or IP addresses**
- *Pourquoi* : contremesures port scanning : TCP wrappers, configurer firewall/IDS, run scans sur ses hôtes, peu de ports ouverts, firmware à jour, custom rule set (bloquer 135–159, 256–258, 389, 445, 1080, 1745, 3268).
- *Autres* : **Never use port scanning tools** = faux (il faut les utiliser pour tester). **Never configure firewall/IDS** = faux. **Never use custom rule set** = faux.

**Q8. Permettre le spoofing IP → Avoid configuring routers to verify data packets using their signatures**
- *Pourquoi* : question = MAUVAISE pratique. Il FAUT configurer les routeurs pour vérifier les paquets via leurs signatures (digests).
- *Autres* : **migrer IPv4→IPv6**, **VPN sécurisé**, **authentification par certificats digitaux** = contremesures valides contre le spoofing.

---

## PARTIE 8 — SÉRIE 6 : OS FINGERPRINTING & ÉVASION (8 justifiées)

**Q1. ⚠️ Identifier l'OS via les valeurs TTL → OS discovery using Unicornscan**
- *Pourquoi* : Unicornscan identifie l'OS en observant les TTL du résultat de scan (`#unicornscan <IP>`).
- *Autres* : **Nmap** = utilise **-O** (pas le TTL). **NSE** = scripts pour OS discovery. **IPv6 fingerprinting** = même fonction que IPv4 (probes + base de fingerprints).

**Q2. Envoyer des paquets spécialement conçus et analyser la réponse → Active**
- *Pourquoi* : fingerprinting ACTIF = envoie des paquets conçus, note les réponses, compare à une base. Les réponses varient selon l'implémentation TCP/IP.
- *Autres* : **Passive** = sniff sans envoyer. Distributive/Reflective = n'existent pas ici.

**Q3. Contourner les censures Internet + évader IDS/firewall → Anonymizers**
- *Pourquoi* : les anonymizers permettent de bypasser les censures Internet et d'évader certaines règles IDS/firewall.
- *Autres* : **IP address decoy** = IP de leurre. **Sending bad checksums** = checksums invalides. **Source port manipulation** = manipuler le port source.

**Q4. Augmenter l'anonymat Internet → Proxy chaining**
- *Pourquoi* : plus de proxys = plus d'anonymat.
- *Autres* : **Source port manipulation** = évader avec un port commun. **IP decoy** = leurres. **Source routing** = spécifier le chemin de routage.

**Q5. MAC aléatoire → nmap -sT -Pn --spoof-mac 0 [Target IP]**
- *Pourquoi* : `--spoof-mac 0` = MAC aléatoire auto-générée. `--spoof-mac [MAC]` = MAC manuelle.
- *Autres* : **-sU -v** = UDP scan. **-sT -Pn --spoof-mac [new MAC]** = MAC manuelle. **cewl** = mots du site.

**Q6. Identifier l'OS pour détecter vulnérabilités → Banner grabbing**
- *Pourquoi* : banner grabbing = OS fingerprinting, identifie l'OS pour choisir les exploits.
- *Autres* : **Port scanning** = services. **IP decoy** = évasion. **Source routing** = routage spécifié.

**Q7. Technique ACTIVE de banner grabbing → TCP sequence ability test**
- *Pourquoi* : actives = TCP sequence ability test, port unreachable. Passives = error messages, sniffing, page extensions.
- *Autres* : **error messages, sniffing, page extensions** = techniques PASSIVES.

**Q8. Éviter la détection par l'IDS pendant un scan → Timing options to slow the port scan**
- *Pourquoi* : les options de timing (--delay, --rate) évitent les IDS/IPS à seuil.
- *Autres* : **Fingerprinting** = identifier les OS (pas éviter détection). **ICMP ping sweep** = hôtes non dispo. **Traceroute** = chemin des paquets.

---

## PARTIE 9 — SÉRIE 7 : ÉNUMÉRATION & PORTS (12 justifiées)

**Q1. ⚠️ Profiter des messages d'erreur différents pendant l'authentification → Brute-force Active Directory**
- *Pourquoi* : design error de l'AD : si « logon hours » est activé, les tentatives d'authentification produisent des messages d'erreur différents → fuite d'infos.
- *Autres* : **SNMP** = deviner les community strings pour extraire des usernames. **email IDs** = username = partie avant le @. **default passwords** = mots de passe par défaut du fabriquant.

**Q2. Port 179/TCP, sessions entre routeurs → BGP**
- *Autres* : **SIP** = VoIP (5060). **LDAP** = 389. **SNMP** = 161.

**Q3. NetBIOS session : null-session + partage fichiers/imprimantes → TCP 139**
- *Autres* : **53** = DNS. **23** = Telnet. **389** = LDAP.

**Q4. Résolution de noms NetBIOS / WINS → UDP 137**
- *Autres* : **TCP 135** = RPC. **UDP 161** = SNMP. **TCP 22** = SSH.

**Q5. Grandes tables de routage des FAI → BGP**
- *Autres* : **TFTP** = 69. **FTP** = 21. **SIP** = VoIP.

**Q6. Infos collectées par l'énumération → Network resources, network shares, and machine names**
- *Pourquoi* : l'énumération collecte ressources réseau, partages, noms de machines, usernames, etc. (après le scan).
- *Autres* : **OS/location web servers/users/passwords** = footprinting. **Email IP/geolocation** = email tracking. **Open ports and services** = scanning.

**Q7. Exploiter les vulnérabilités DNS → TCP/UDP 53**
- *Autres* : **139** = NetBIOS. **135** = RPC. **137** = NetBIOS-NS.

**Q8. Port 389 → LDAP**
- *Autres* : **SNMP** = 161. **SMTP** = 25. **SIP** = 5060.

**Q9. Communication multiprocess fiable → TCP**
- *Pourquoi* : TCP = fiable (connexion, accusés de réception, retransmission).
- *Autres* : **UDP** = non fiable. **SNMP/SMTP** = applications (pas de service de communication générique).

**Q10. Port 139 pour identifier les ressources → NetBIOS**
- *Pourquoi* : NetBIOS (139) permet de lister les ressources/partages distants.
- *Autres* : **SNMP** = 161. **LDAP** = 389. **SMTP** = 25.

**Q11. Port par défaut IPSEC IKE → Port 500**
- *Autres* : **50** = ESP (protocole IP). **4500** = NAT-T. **51** = AH.

**Q12. Port 23 → Telnet**
- *Pourquoi* : Jake a utilisé Telnet (23) pour banner grabbing sur SSH/SMTP + brute force.
- *Autres* : **SSH** = 22. **FTP** = 21. **BGP** = 179.

---

## PARTIE 10 — SÉRIE 8 : ÉNUMÉRATION LDAP (6 justifiées)

**Q1. Accéder aux annuaires AD → AD Explorer**
- *Pourquoi* : AD Explorer (Sysinternals) = accès aux annuaires Active Directory / services d'annuaire.
- *Autres* : **HULK, Slowloris, XOIC** = outils DoS (HULK et Slowloris sont des attaques de déni de service).

**Q2. Accéder aux annuaires distribués (usernames, adresses, départements) → LDAP**
- *Autres* : **SMTP** = mail. **NTP** = temps. **DNS** = résolution de noms.

**Q3. Outil pour LDAP enumeration → AD Explorer**
- *Autres* : **SuperScan, Nsauditor, SoftPerfect network scanner** = scanners de ports/réseau, pas LDAP.

**Q4. Script python `connection.search(search_base=..., search_filter='(&(objectClass=*))', search_scope='SUBTREE', attributes='*')` → Retrieved all directory objects**
- *Pourquoi* : objectClass=* + scope SUBTREE + attributes=* = retourne tous les objets de l'annuaire.
- *Autres* : **Listed all applications** = filtre différent. **Retrieved the DSE naming contexts** = RootDSE. **Created a connection object** = avant le search (connection.bind).

**Q5. Énumérer les users AD avec filtres → Ladpsearch (ldapsearch)**
- *Pourquoi* : ldapsearch = outil ligne de commande LDAP pour énumérer/filtrer les users AD.
- *Autres* : **PortQry** = interroger les ports. **DNSRecon** = DNS. **netstat** = connexions réseau.

**Q6. Énumération LDAP → AD Explorer**
- *Autres* : **Euromonitor** = études de marché. **nbtstat** = NetBIOS. **DNSRecon** = DNS.

---

## BONUS — TABLEAUX PIÈGES RÉCURRENTS CEH

### Ports / services associés (à mémoriser par association)
| Port | Service | Question type |
|---|---|---|
| 23 | Telnet | banner grabbing + brute force |
| 88 | Kerberos | vérification d'identité |
| 137 | NetBIOS-NS / WINS | résolution de noms NetBIOS |
| 139 | NetBIOS-SSN | null-session, partage |
| 179 | BGP | sessions routeurs, FAI |
| 389 | LDAP | annuaire |
| 500 | ISAKMP/IKE | IPSec |
| 514 | syslog | logs (UDP) |
| 515 / 631 / 9100 | LPD / IPP / raw | imprimante |

### Paires à ne pas confondre
| Confusion classique | Bonne réponse |
|---|---|
| Egress vs Ingress filtering | Egress = paquets **sortants** ; Ingress = **entrants** |
| searchfy vs usufy vs mailfy | searchfy = requête sur plateformes OSRFramework |
| -sY vs -sZ | -sY = SCTP INIT ; **-sZ = SCTP COOKIE ECHO** |
| Network scanning vs Port scanning | Port scanning = « envoyer des messages pour s'introduire » |
| Banner grabbing actif vs passif | Actif = TCP sequence ability test ; passif = error messages/sniffing |
| Photon vs Wayback | Photon = outil pour récupérer les URLs archivées de archive.org |
| -Pn vs -P0 | -Pn/-PN = skip host discovery ; -P0 = IP protocol ping |
| Spoof MAC auto vs manuel | `--spoof-mac 0` = auto/aléatoire ; `--spoof-mac XX:XX` = manuel |

### Les 12 erreurs à revoir (déjà listées dans le doc de révision)
S1-Q5 (Background checks) • S1-Q8 (Sublist3r) • S1-Q9 (site:Wikipedia.org) • S1-Q15 (Social engineering) • S1-Q34 (Photon) • S2-Q9 (searchfy) • S3-Q4 (-sZ) • S3-Q9 (-PN -A -O -sS) • S4-Q3 (Port scanning) • S4-Q8 (Hping) • S5-Q2 (Egress) • S6-Q1 (Unicornscan) • S7-Q1 (Brute-force AD)


# ============================================================

## SÉRIE 1 — FOOTPRINTING OSINT

1. Recherche d'image inversée (source des photos) → **TinEye**
2. Valeur boursière, profil société, infos concurrents → **investing.com**
3. Obtenir infos des bases gouvernementales en anonyme → **ExoneraTor**
4. Dépôt de notes/messages soumis par utilisateurs → **NNTP Usenet newsgroups**
5. ⚠️ Activité de l'organisation qui permet de footprinter le type de business → **Background checks to hire employees** (les « background checks » révèlent le type de business)
6. Activité d'un utilisateur révélant identité des membres de la famille → **Sharing photos and videos**
7. Examen des cookies du serveur révèle → **Software in use and its behavior**
8. ⚠️ Trouver URLs internes / départements de l'entreprise → **Sublist3r** (énumération de sous-domaines)
9. ⚠️ Pages Wikipédia contenant « SQL », « injection », « SQL injection » → **SQL injection site:Wikipedia.org**
10. Bases de données publiques d'infos personnelles des propriétaires de domaines → **WHOIS lookup tools**
11. Infos collectées par les email tracking tools → **IP du destinataire, géolocalisation, détection proxy, OS et navigateur**
12. Mails listés sur pastebin.com → **site:pastebin.com intext:*@*.com:***
13. Enregistrement DNS indiquant l'autorité d'un domaine → **SOA**
14. Enregistrement DNS pointant vers l'adresse IP d'un hôte → **A**
15. ⚠️ Approche directe = source primaire de renseignement concurrentiel → **Social engineering** (techniques directes : salons, social engineering)
16. Vérifie si un email a fuité via haveibeenpwned.com → **Infoga**
17. `site:target.com -site:Marketing.target.com accounting` → **Résultats « accounting » sur target.com mais pas sur Marketing.target.com**
18. Rechercher tous fichiers d'un domaine → **site: certifiedhacker.com filetype:xml | filetype:conf | ...** (filetype)
19. Sortie des moteurs de recherche pour extraire des infos critiques → **SERPs** (Search Engine Results Pages)
20. Technique pour créer des requêtes complexes → **Google hacking**
21. Obtenir téléphones, emails, adresses, DOB, famille d'employés → **Spokeo**
22. Observer par-dessus l'épaule avec jumelles → **Shoulder surfing**
23. Extraire identité de l'expéditeur, serveur mail, IP, localisation → **Email tracking tools**
24. Protocole requête/réponse pour bases des assignés d'une ressource Internet → **Whois lookup**
25. Découvrir un username sur divers réseaux sociaux avec URL complète → **Sherlock**
26. Récupérer fichiers confidentiels depuis les dépôts de code source → **Recon-ng**
27. Visualisation de graphes, découvrir patterns cachés dans les connexions sociales → **Gephi**
28. Géolocalisation des routeurs, serveurs, périphériques → **Traceroute tools**
29. Suivre le contenu le plus partagé sur les réseaux sociaux → **BuzzSumo**
30. Rechercher des personnes appartenant à l'org cible → **Spokeo**
31. Outil CLI de recherche Exploit-DB en local → **SearchSploit**
32. Référentiel tiers en ligne : clés SSH/SSL privées, libs dynamiques → **GitLab** (dépôts de code source : GitHub, GitLab, SourceForge, BitBucket)
33. Construire/analyser des réseaux sociaux (NodeXL, Gephi, SocNetV) → **NodeXL**
34. ⚠️ Récupérer URLs archivées du site cible depuis archive.org → **Photon**
35. Commande pour récupérer les URLs archivées depuis archive.org → **photon.py -u http//www.certifiedhacker.com -1 3 -t 200 --wayback**
36. Récupérer URLs archivées depuis archive.org → **Photon**


---

## SÉRIE 2 — OUTILS DE FOOTPRINTING AVANCÉS

1. FOCA : trouver plus de serveurs dans le même segment d'adresse → **PTR scanning**
2. Plateforme en ligne pour collecter/analyser infos sur devices et sites → **Spyse**
3. Collecter sous-domaines, IP, statut HTTP, certifs SSL/TLS, scores de vulnérabilité, DNS → **Spyse**
4. Contremesure contre le footprinting → **Configure mail servers to ignore mails from anonymous individuals**
5. Défense contre le footprinting → **Disable or delete the accounts of employees who left the organization**
6. Sublist3r : option pour liste de moteurs de recherche séparés par virgules → **-e** (--engines)
7. À NE PAS suivre pour sécuriser l'organisation → **Enabling the geo-tagging functionality on cameras**
8. Contremesure pour protéger confidentialité/données/réputation → **Avoiding domain-level cross-linking for critical assets**
9. ⚠️ Faire une requête sur les plateformes OSRFramework → **searchfy.py** (usufy=profils, mailfy=emails, domainfy=domaines, phonefy=téléphones, entify=entités)
10. Recon-Dog : détecter les technologies du système cible → **wappalyzer.com**
11. Sublist3r : option liste de moteurs de recherche → **-e**
12. FOCA : trouver plus de serveurs dans le même segment → **PTR scanning**
13. Protéger le réseau contre le footprinting → **Configure mail servers to ignore mails from anonymous individuals**

### Rappel OSRFramework (piège récurrent)
- **usufy.py** → vérifie un profil utilisateur sur 290 plateformes
- **mailfy.py** → vérifie l'existence d'un email
- **searchfy.py** → requête sur les plateformes d'OSRFramework
- **domainfy.py** → existence de domaines
- **phonefy.py** → existence d'une série de téléphones
- **entify.py** → extrait des entités via regex

### Rappel FOCA
- Web Search / DNS Search / IP Resolution / **PTR Scanning** (serveurs du même segment) / Bing IP / Common Names (attaque dictio sur DNS)

---

## SÉRIE 3 — PING / SCANNING RÉSEAU

1. Méthode de ping efficace quand l'admin bloque l'ICMP ECHO → **ICMP address mask ping scan** (comme le timestamp ping)
2. Protocole sur port **88/TCP** qui vérifie l'identité d'un user/hôte → **Kerberos**
3. Scan détectant un port ouvert après handshake complet, ferme avec RST → **TCP connect scan**
4. ⚠️ Nmap : scan SCTP COOKIE ECHO → **-sZ** (-sY = INIT, -sU = UDP, -sL = list scan)
5. Envoyer une adresse source spoofée pour déterminer les services dispo → **IDLE/IPID header scan** (scan aveugle complet)
6. Scan UDP : réponse ICMP Type 3 / Code 3 (port unreachable) → **UDP port is closed**
7. `nmap –n –sS –P0 –p 80` → **Stealth scan** (SYN scan -sS)
8. Ports 21,23,80,139,515,631,9100 + MAC → **The host is likely a printer** (port 515 = LPD, port 9100 = impression)
9. ⚠️ Scanner tous les ports TCP d'un réseau classe C bloquant ICMP avec fingerprinting + services → **NMAP -PN -A -O -sS 192.168.2.0/24**
10. Protocole pour envoyer des logs à un outil d'analyse derrière un firewall → **UDP 514** (syslog)

### Points clés Nmap
- **-sS** = SYN stealth scan | **-sT** = connect scan | **-sU** = UDP | **-sZ** = SCTP COOKIE ECHO | **-sY** = SCTP INIT | **-sL** = list scan | **-sA** = ACK
- **-Pn / -PN** = skip host discovery | **-O** = OS fingerprinting | **-A** = OS + services + scripts + traceroute | **-p** = ports | **-n** = pas de résolution DNS
- **ICMP 3/3** = port UDP fermé ; pas de réponse = open|filtered

---

## SÉRIE 4 — FLAGS TCP / HPING / NMAP

1. Flag confirmant la réception + prochain numéro de séquence → **ACK flag**
2. Flag notifiant un nouveau numéro de séquence (établissement de connexion) → **SYN flag**
3. ⚠️ Vérifier les services d'une machine en envoyant des messages pour s'introduire → **Port scanning** (Network scanning = hôtes actifs ; Banner grabbing = OS)
4. Flag mis à 1 pour annoncer qu'il n'y aura plus de transmissions → **FIN flag**
5. Objectif qui N'EST PAS un objectif du network scanning → **Discover usernames and passwords**
6. hping : collecter le numéro de séquence initial (ISN) → **hping3 192.168.1.103 -Q -p 139 -s**
7. App mobile Android/iOS : IP, MAC, vendor, localisation FAI → **Fing**
8. ⚠️ Ping bloqué (ICMP désactivé) : alternative TCP pour obtenir une réponse → **Hping** (scan ACK -A)
9. Meilleur outil open-source pour scanner un réseau et trouver des cibles → **NMAP**
10. hping3 : effectuer un scan ACK → **hping3 –A <IP Address> –p 80**

### Rappel flags TCP
- **SYN** = établit la connexion | **ACK** = accuse réception | **FIN** = termine proprement | **RST** = erreur/abandon | **PSH** = push des données | **URG** = urgent

### Rappel hping3
- `-1` = ICMP ping | `-2` = UDP scan | `-A` = ACK scan | `-S` = SYN scan | `-8` = scan d'une plage | `-Q -s` = collecter ISN | `--tcp-timestamp` = firewall/timestamps


---

## SÉRIE 5 — CONTREMESURES BANNER GRABBING / SPOOFING

1. Contremesure contre le banner grabbing → **Use ServerMask tools to disable or change banner information**
2. ⚠️ Empêcher le spoofing en bloquant les paquets sortants avec source externe → **Egress filtering** (sortant) vs **Ingress filtering** (entrant)
3. Pratique rendant le réseau vulnérable au port scanning → **Avoid using proxy servers to block fragmented or malformed packets** (il FAUT utiliser des proxys)
4. Prévenir le banner grabbing sur l'hôte → **Modify the value of Server Tokens from Full to Prod in Apache's httpd.conf**
5. Pratique rendant le système vulnérable au banner grabbing → **Enable HTTP methods such as Connect, Put, Delete, and Options** (il faut les désactiver)
6. Contremesure contre la divulgation via banner grabbing → **Display false banners**
7. Défense contre le port scanning → **Ensure that TCP wrappers limit access to the network based on domain names or IP addresses**
8. Pratique permettant de spoof les IP pour entrer illégitimement → **Avoid configuring routers to verify the data packets using their signatures**

### Rappel contremesures banner grabbing
- Afficher de faux banners | Désactiver les services inutiles | ServerMask | masquer versions/vendors | ServerSignature Off | Server Tokens = Prod | désactiver CONNECT/PUT/DELETE/OPTIONS

### Rappel port scanning countermeasures
- Tester firewall/IDS avec fragtest/fragroute | bloquer ICMP entrant et ICMP type-3 sortant | firewalls commerciaux | proxys pour bloquer paquets fragmentés/malformés | TCP wrappers | peu de ports ouverts (filtrer 135–159, 256–258, 389, 445, 1080, 1745, 3268)

---

## SÉRIE 6 — OS FINGERPRINTING & ÉVASION IDS/FIREWALL

1. ⚠️ Identifier l'OS en observant les valeurs TTL du résultat de scan → **OS discovery using Unicornscan** (Nmap utilise -O, pas le TTL)
2. Type de fingerprinting qui envoie des paquets spécialement conçus et analyse la réponse → **Active** (passive = sniff)
3. Évasion IDS/firewall : contourner les censures Internet → **Anonymizers**
4. Augmenter l'anonymat Internet → **Proxy chaining** (plus de proxys = plus d'anonymat)
5. Générer automatiquement une MAC aléatoire pendant le scan → **nmap -sT -Pn --spoof-mac 0 [Target IP]** (0 = aléatoire ; valeur = MAC manuelle)
6. Identifier l'OS pour détecter les vulnérabilités → **Banner grabbing**
7. Technique ACTIVE de banner grabbing → **TCP sequence ability test** (passives : error messages, sniffing, page extensions)
8. Éviter la détection par l'IDS pendant un scan → **Timing options to slow the speed that the port scan is conducted** (--delay, --rate)

### Rappel évasion IDS/firewall
- IP address decoy | Source port manipulation | Sending bad checksums | Anonymizers | Proxy chaining | Source routing | Fragmenting packets | MAC spoofing

### Rappel fingerprinting
- Actif : envoie des paquets → analyse la réponse (ex. Nmap -O, TCP sequence ability test)
- Passif : sniff sans envoyer (error messages, network traffic, page extensions)

---

## SÉRIE 7 — ÉNUMÉRATION & PORTS

1. ⚠️ Profiter des messages d'erreur différents pendant l'authentification de service → **Brute-force Active Directory** (via « logon hours » de l'AD)
2. Port 179/TCP, sessions entre routeurs → **BGP**
3. Service session NetBIOS (null-session + partage fichiers/imprimantes) → **TCP 139**
4. Résolution de noms NetBIOS / WINS → **UDP 137** (netbios-ns)
5. Protocole utilisé par les FAI pour les grandes tables de routage → **BGP**
6. Informations collectées par l'énumération → **Network resources, network shares, and machine names**
7. Port utilisé pour exploiter les vulnérabilités DNS → **TCP/UDP 53**
8. Protocole sur port 389 (TCP/UDP) → **LDAP**
9. Communication multiprocess fiable dans un environnement multi-réseaux → **TCP**
10. Port 139 ouvert : identifier les ressources accessibles sur Windows → **NetBIOS**
11. Port par défaut du protocole IPSEC IKE → **Port 500**
12. Port 23 → **Telnet**

### Rappel ports
- 21 FTP | 22 SSH | 23 Telnet | 25 SMTP | 53 DNS | 69 TFTP | 79 Finger | 88 Kerberos | 123 NTP | 135 RPC | 137 NetBIOS-NS (WINS) | 139 NetBIOS-SSN | 161 SNMP | 179 BGP | 389 LDAP | 443 HTTPS | 500 ISAKMP/IKE | 514 syslog | 515 LPD (imprimante) | 631 IPP | 9100 impression

---

## SÉRIE 8 — ÉNUMÉRATION LDAP

1. Outil LDAP pour accéder aux annuaires Active Directory → **AD Explorer**
2. Protocole pour accéder aux annuaires distribués (usernames, adresses, départements) → **LDAP**
3. Outil pour faire de l'énumération LDAP → **AD Explorer**
4. Script Python (connection.search avec objectClass=*) → **Retrieved all directory objects**
5. Outil pour énumérer les users AD avec des filtres spécifiques → **Ladpsearch** (ldapsearch)
6. Outil permettant l'énumération LDAP → **AD Explorer**


---

## AIDE-MÉMOIRE FINAL

### Opérateurs Google (footprinting)
- `site:` restreint au domaine | `inurl:` / `allinurl:` dans l'URL | `intitle:` / `allintitle:` dans le titre | `intext:` dans le texte | `filetype:` type de fichier | `-` exclut un terme | `related:` pages similaires | `cache:` version en cache
- Exemples : `site:target.com filetype:xls` | `site:pastebin.com intext:*@*.com:*`

### Enregistrements DNS
- A = IP d'un hôte | AAAA = IPv6 | MX = serveur mail | NS = name server | CNAME = alias | SOA = autorité du domaine | SRV = services | PTR = IP → hostname | TXT = texte | HINFO = CPU/OS | RP = personne responsable

### Outils et leur usage (associer à la question)
- **TinEye** = reverse image | **Spokeo** = people search | **ExoneraTor** = deep/dark web | **Sublist3r** = sous-domaines | **Photon** = archive.org | **Recon-ng** = reconnaissance framework | **Sherlock** = username sur réseaux sociaux | **Infoga** = emails + haveibeenpwned | **SearchSploit** = Exploit-DB offline | **BuzzSumo** = contenu partagé | **Gephi/NodeXL** = analyse de graphes sociaux | **Fing** = app mobile scan réseau | **FOCA** = PTR scanning | **Spyse** = plateforme devices/sites | **Hping** = packet crafting | **Nmap/Zenmap** = scanner réseau | **Unicornscan** = TTL/OS

### Google hacking / techniques à connaître
- Direct vs Indirect approach (competitive intelligence) : direct = salons + social engineering ; indirect = ressources en ligne
- What Organizations Do → Type de business : **Background checks**
- What Users Do → Famille/interêts : **Sharing photos and videos**

### Pièges fréquents (d'où viennent tes 12 erreurs)
1. **searchfy.py** vs usufy/mailfy/domainfy (OSRFramework) — retiens la description exacte
2. **-sZ** = SCTP COOKIE ECHO (pas -sY)
3. **IDLE/IPID** = spoofé pour services dispo (pas ACK flag scan)
4. **Egress** (sortant) vs **Ingress** (entrant) filtering
5. **Unicornscan** = TTL ; **Nmap** = -O
6. **Port scanning** = « send messages to break in » ; **Network scanning** = hôtes actifs
7. **Hping** = alternative au ping quand ICMP bloqué (scan ACK)
8. **Photon** = archive.org (pas Burp/Netcraft)
9. **Brute-force AD** = erreurs d'authentification différentes (« logon hours »)
10. **-PN -A -O -sS** pour classe C bloquant ICMP

---

## TES 12 ERREURS À REVOIR AVANT L'EXAMEN
| Série | Q | Ta réponse | Bonne réponse |
|---|---|---|---|
| 1 | 5 | User surveys | **Background checks to hire employees** |
| 1 | 8 | WayBackMachine | **Sublist3r** |
| 1 | 9 | site:Wikipedia.org intitle:"SQL Injection" | **SQL injection site:Wikipedia.org** |
| 1 | 15 | Search engines | **Social engineering** |
| 1 | 34 | Gephi | **Photon** |
| 2 | 9 | usufy.py | **searchfy.py** |
| 3 | 4 | -sY | **-sZ** |
| 3 | 9 | -P0 -A -O -p1-65535 192.168.0/24 | **-PN -A -O -sS 192.168.2.0/24** |
| 4 | 3 | Banner grabbing | **Port scanning** |
| 4 | 8 | TCP ping | **Hping** |
| 5 | 2 | Ingress filtering | **Egress filtering** |
| 6 | 1 | OS discovery using Nmap | **OS discovery using Unicornscan** |
| 7 | 1 | Extracting usernames using email IDs | **Brute-force Active Directory** |

