# Module 05 — Vulnerability Analysis (CEH v13)

> Notes de cours en français basées sur le support officiel **CEH v13 — Module 05 : Vulnerability Analysis** (EC-Council, 312-50).
> Révision pour l'examen CEH : concepts d'évaluation de vulnérabilités, systèmes de scoring (CVSS), bases de vulnérabilités (CVE, NVD, CWE), cycle de vie de la gestion des vulnérabilités, types de scan, outils (Nessus, OpenVAS, Nikto, Qualys, GFI LanGuard…) et analyse des rapports.

---

## Objectifs d'apprentissage

- Résumer les concepts d'évaluation des vulnérabilités
- Utiliser les outils d'évaluation des vulnérabilités
- Analyser les rapports d'évaluation des vulnérabilités

**À la fin du module, vous saurez :**
- Comprendre la classification des vulnérabilités et les systèmes de scoring (CVSS)
- Décrire le cycle de vie de la gestion des vulnérabilités
- Utiliser divers outils d'évaluation des vulnérabilités
- Comprendre la recherche, le scan et l'analyse des vulnérabilités
- Comprendre les différents types de techniques de scanning
- Générer et analyser les rapports d'évaluation des vulnérabilités

---

## Objectif 01 — Concepts d'évaluation des vulnérabilités

### 1.1 Classification des vulnérabilités

Les vulnérabilités présentes dans un système ou un réseau sont classées dans les catégories suivantes :

| Type de vulnérabilité | Description | Exemples |
|---|---|---|
| **Misconfigurations / Configurations faibles** | Systèmes, applications ou périphériques mal configurés, laissant la porte ouverte à l'exploitation | Protocoles non sécurisés, ports ouverts, erreurs, chiffrement faible |
| **Flaws applicatifs (Application Flaws)** | Vulnérabilités dans les applications exploitées par les attaquants | Buffer overflows, fuites mémoire, épuisement des ressources, integer overflows, null pointer dereference, injection DLL, race conditions, mauvaise gestion des entrées/erreurs, faiblesse de signature de code |
| **Mauvaise gestion des correctifs (Poor Patch Management)** | Logiciels non corrigés qui restent vulnérables aux attaques | Serveurs non patchés, firmware non patché, OS non patché, applications non patchées |
| **Flaws de conception (Design Flaws)** | Failles logiques dans le fonctionnement du système | Chiffrement incorrect, mauvaise validation des données |
| **Risques tiers (Third-Party Risks)** | Services tiers ayant accès à des systèmes privilégiés | Gestion des fournisseurs, risques supply-chain, code sous-traité, stockage de données, risques cloud vs on-premises |

**Autres classifications importantes :**
- **Installations par défaut / Configurations par défaut** — ne pas changer les réglages par défaut permet à l'attaquant de deviner les paramètres pour pénétrer le système.
- **Failles d'OS (Operating System Flaws)** — Trojans, vers et virus exploitent les vulnérabilités de l'OS.
- **Mots de passe par défaut (Default Passwords)** — exposent aux attaques brute force et par dictionnaire.
- **Vulnérabilités zero-day** — vulnérabilités inconnues, exposées mais pas encore patchées, exploitées avant leur découverte par les développeurs.
- **Vulnérabilités de plateformes héritées (Legacy Platform)** — causées par des codes obsolètes ou familiers ; plateformes non supportées.
- **System sprawl / Actifs non documentés (Undocumented Assets)** — augmentation du nombre de systèmes connectés sans documentation ni maintenance, souvent négligés.
- **Gestion incorrecte des certificats et clés (Improper Certificate and Key Management)** — clés stockées sur les serveurs, vulnérables à l'interception.

#### Misconfigurations réseau (détail)
- **Protocoles non sécurisés** : transmettent les données en clair (problèmes d'authentification et d'intégrité) → l'attaquant capture les identifiants et accède au système.
- **Ports et services ouverts** : peuvent mener à la perte de données ou à des attaques DoS.
- **Erreurs** : les rapports d'erreur divulguent des informations utiles aux attaquants.
- **Chiffrement faible** : permet MitM, sniffing du trafic, usurpation du service légitime. Causes : algorithme faible, clés devinables, distribution de clés non sécurisée.

#### Misconfigurations hôte (détail)
- **Permissions ouvertes** : des permissions excessives permettent l'escalade de privilèges.
- **Comptes root non sécurisés** : identifiants admin par défaut → attaques brute force.

#### Flaws applicatifs (détail)
- **Buffer overflow** : écriture au-delà de la taille allouée du buffer → crash, instabilité, exécution de code.
- **Memory leak** : échec de libération de mémoire → DoS, hijack du flux de contrôle. Outil : **Valgrind** (Unix/Linux).
- **Resource exhaustion** : envoi de multiples requêtes de ressources → système suspendu ou crash.
- **Integer overflow** : stockage d'une valeur plus grande que la capacité mémoire → peut mener à un buffer overflow.
- **Null pointer/object dereference** : exploitation de l'exception pour contourner la logique de sécurité.
- **DLL injection** : chargement de DLL non fiables → exécution de code malveillant. Prévention : ne jamais charger de DLL non fiables, toujours spécifier le chemin complet.
- **Race conditions / TOC/TOU** : dépendance à l'ordre et au timing des processus. TOC/TOU = changement d'état entre le moment du check et le moment de l'utilisation.
- **Improper input handling** : validation d'entrée insuffisante → SQL injection, XSS, buffer overflow.
- **Improper error handling** : divulgation de dumps de base de données et stack traces. **Fail-open** = octroi d'accès après un échec du système.
- **Code signing weakness** : certificats invalides/expirés → vol de clés privées et authentification frauduleuse du code. Protection : **HSM (Hardware Security Modules)**.

#### Mauvaise gestion des correctifs (détail)
- **Serveurs non patchés** : point d'entrée dans le réseau.
- **Firmware non patché** : injection de code malveillant, contrôle du matériel à distance.
- **OS non patché** : vecteur d'infection, escalade de privilèges via malware root.
- **Applications non patchées** : exécution de code malveillant via des bugs connus.

### 1.2 Systèmes de scoring des vulnérabilités et bases de données

| Système | Description | URL |
|---|---|---|
| **CVSS** (Common Vulnerability Scoring System) | Standard publié, framework ouvert pour communiquer les caractéristiques et impacts des vulnérabilités IT. Produit un score numérique de sévérité (0.0 à 10.0). Fourni par **FIRST.Org**. | https://www.first.org |
| **CVE** (Common Vulnerabilities and Exposures) | Liste/dictionnaire publique et gratuite d'identifiants standardisés pour les vulnérabilités et expositions logicielles communes. Un identifiant = une vulnérabilité. **Dictionnaire** (pas une base de données). ID assignés par les **CVE Numbering Authorities (CNAs)**. | https://cve.mitre.org |
| **NVD** (National Vulnerability Database) | Référentiel du gouvernement américain pour les données de gestion des vulnérabilités basées sur les standards. Utilise le **SCAP** (Security Content Automation Protocol). Analyse les CVE publiées : associe métriques CVSS, types CWE, déclarations CPE. **Ne fait pas de tests actifs** — s'appuie sur les fournisseurs et chercheurs. | https://nvd.nist.gov |
| **CWE** (Common Weakness Enumeration) | Système de catégorisation des vulnérabilités et faiblesses logicielles, sponsorisé par MITRE. **Plus de 600 catégories** de faiblesses. Version 3.2 (janvier 2019). | https://cwe.mitre.org |

#### CVSS — Métriques
Le CVSS est composé de **quatre groupes de métriques** :

1. **Base metric** (constante dans le temps et les environnements) :
   - *Exploitability metrics* : Attack Vector (AV), Attack Complexity (AC), Attack Requirements (AT), Privileges Required (PR), User Interaction (UI)
   - *Impact metrics* : Confidentiality, Integrity, Availability (sur le système vulnérable ET le système subséquent)
2. **Threat metric** : Exploit Maturity
3. **Environmental metric** : version modifiée des métriques de base + exigences de confidentialité, intégrité, disponibilité
4. **Supplemental metric** : Automatable, Value Density, Recovery, Vulnerability Response Effort, Safety, Provider Urgency

**Ratings CVSS (scores) :**

| Sévérité | Plage de score de base |
|---|---|
| None | 0.0 |
| Low | 0.1 – 3.9 |
| Medium | 4.0 – 6.9 |
| High | 7.0 – 8.9 |
| Critical | 9.0 – 10.0 |

Le score CVSS est généré par une **chaîne vectorielle** (ex. `CVSS:4.0/AV:N/AC:L/AT:N/PR:N/UI:N/VC:H/VI:H/VA:H/SC:H/SI:H/SA:H`).

### 1.3 Cycle de vie de la gestion des vulnérabilités

Le cycle de vie se déroule en **trois phases** :

#### Phase 1 — Pré-évaluation (Pre-Assessment Phase)
**Identifier les actifs et créer une baseline :**
1. Identifier et comprendre les processus métier
2. Identifier les applications, données et services qui supportent les processus métier ; effectuer des revues de code
3. Identifier les logiciels, drivers et configurations de base approuvés de chaque système
4. Créer un inventaire de tous les actifs et classer/prioriser les actifs critiques
5. Comprendre l'architecture réseau et cartographier l'infrastructure
6. Identifier les contrôles déjà en place
7. Comprendre la mise en œuvre des politiques et la conformité aux standards
8. Définir le périmètre de l'évaluation
9. Créer des procédures de protection de l'information (planification, coordination, logistique)

#### Phase 2 — Évaluation des vulnérabilités (Vulnerability Assessment Phase)
Étapes :
1. Examiner et évaluer la sécurité physique
2. Vérifier les misconfigurations et erreurs humaines
3. Lancer des scans de vulnérabilités avec des outils
4. Sélectionner le type de scan selon l'organisation ou les exigences de conformité
5. Identifier et prioriser les vulnérabilités
6. Identifier les faux positifs et faux négatifs
7. Appliquer le contexte métier et technologique aux résultats du scanner
8. Effectuer de la collecte OSINT pour valider les vulnérabilités
9. Créer un rapport de scan de vulnérabilités

#### Phase 3 — Post-évaluation (Post Assessment Phase)
Également appelée **phase de recommandation**. Inclut :
- **Évaluation des risques (Risk Assessment)** : identifier, caractériser et classer les risques ; prioriser selon le niveau de risque (critique, haut, moyen, bas)
- **Remédiation (Remediation)** : appliquer des correctifs pour atténuer/réduire l'impact et la sévérité. Doit être **SMART** (spécifique, mesurable, atteignable, pertinent, limité dans le temps). Prioriser selon le classement des risques, analyse de cause racine, appliquer patchs/fixes, capture des leçons apprises, formation de sensibilisation, gestion des exceptions et acceptation des risques pour les vulnérabilités non remédiables
- **Vérification (Verification)** : re-scan des systèmes pour vérifier si le correctif est efficace. Moyens : systèmes de ticketing, scanners, rapports ; analyse dynamique ; revue de la surface d'attaque
- **Surveillance (Monitoring)** : monitoring continu avec IDS/IPS, SIEM, firewalls. Scan périodique, remédiation en temps utile, surveillance des logs IDS/IPS, mise en œuvre des politiques

### 1.4 Recherche de vulnérabilités (Vulnerability Research)

Un administrateur a besoin de la recherche de vulnérabilités pour :
- Collecter des informations sur les tendances de sécurité, menaces nouvellement découvertes, surfaces d'attaque, vecteurs et techniques d'attaque
- Trouver les faiblesses de l'OS et des applications et alerter l'administrateur avant une attaque
- Comprendre les informations qui aident à prévenir les problèmes de sécurité
- Savoir comment se remettre d'une attaque réseau
- Prioriser et appliquer efficacement les correctifs de sécurité
- Respecter les meilleures pratiques industrielles
- Effectuer des évaluations de risques précises

**Ressources pour la recherche de vulnérabilités :**
- **MSRC (Microsoft Security Response Center)** — https://msrc.microsoft.com
- **Packet Storm** — https://packetstormsecurity.com
- **Dark Reading** — https://www.darkreading.com
- **Trend Micro** — https://www.trendmicro.com
- **Security Magazine** — https://www.securitymagazine.com
- **PenTest Magazine** — https://pentestmag.com
- **SC Magazine** — https://www.scmagazine.com
- **Exploit Database** — https://www.exploit-db.com
- **Help Net Security** — https://www.helpnetsecurity.com
- **HackerStorm** — https://www.hackerstorm.co.uk
- **Computerworld** — https://www.computerworld.com
- **D'Crypt** — https://www.d-crypt.com

### 1.5 Scanning et analyse des vulnérabilités

**Définitions clés :**
- **Vulnerability scanning** : analyse des protocoles, services et configurations pour découvrir les vulnérabilités et failles de conception qui peuvent exposer un OS et ses applications à l'exploitation, l'attaque ou la mauvaise utilisation.
- **Vulnerability analysis** : processus systématique d'identification, d'évaluation et de priorisation des faiblesses de sécurité. Les vulnérabilités sont classées par **niveau de sévérité** (bas, moyen, haut) et **portée d'exploitation** (locale ou distante).

**Informations identifiables par les scanners de vulnérabilités :**
- Version de l'OS des ordinateurs/périphériques
- Ports TCP/UDP en écoute
- Applications installées
- Comptes avec mots de passe faibles
- Fichiers et dossiers avec permissions faibles
- Services et applications par défaut à désinstaller
- Erreurs de configuration de sécurité des applications courantes
- Ordinateurs exposés aux vulnérabilités connues ou publiquement signalées
- Informations EOL/EOS (fin de vie/fin de support)
- Correctifs et hotfixes manquants
- Configurations réseau faibles, ports risqués ou mal configurés
- Vérification de l'inventaire des périphériques

**Deux approches du scanning réseau :**
- **Active scanning** : l'attaquant interagit directement avec le réseau cible pour trouver les vulnérabilités (envoie des sondes et requêtes spécialement conçues). Simule une attaque.
- **Passive scanning** : l'attaquant trouve les vulnérabilités sans interagir directement (observe les informations exposées lors des communications normales, e.g. devine l'OS en observant les connexions TCP).

Outils de scan des vulnérabilités : **Nessus, Qualys, GFI LanGuard, OpenVAS**.

#### Limites du scanning des vulnérabilités
- Logiciel limité à détecter les vulnérabilités à un instant donné
- Doit être mis à jour quand de nouvelles vulnérabilités sont découvertes
- Ne mesure pas la force des contrôles de sécurité
- Non immunisé contre les flaws d'ingénierie logicielle
- **Le jugement humain est requis** pour identifier faux positifs et faux négatifs
- Ne peut pas définir l'impact d'une vulnérabilité sur les différentes opérations métier
- Les rapports ne sont pas toujours faciles à comprendre
- Outils à focus étroit : ne couvrent pas les vecteurs d'attaque comme le social engineering
- Capacité limitée pour les tests en direct des applications web
- **S'appuient sur les vulnérabilités connues → ne peuvent pas détecter les menaces zero-day**
- Peuvent ne pas prioriser selon le contexte (criticité du système affecté)
- Dépendent de la complétude des bases de données de vulnérabilités

### 1.6 Types de scanning des vulnérabilités

| Type | Description |
|---|---|
| **External Scanning** | Scanne le réseau du point de vue d'un hacker pour découvrir les exploits et vulnérabilités accessibles depuis l'extérieur (via firewalls, routeurs, serveurs). Évalue le niveau de sécurité du réseau externe et du firewall. |
| **Internal Scanning** | Scrute le réseau interne pour trouver des exploits et vulnérabilités. |
| **Host-based Scanning** | Contrôle de niveau configuration pour identifier les configurations système, répertoires utilisateur, systèmes de fichiers, paramètres du registre. |
| **Network-based Scanning** | Détermine les attaques réseau possibles ; découvre les ressources réseau et cartographie les ports/services. |
| **Application Scanning** | Analyse toute l'infrastructure web (misconfiguration, contenu obsolète, vulnérabilités connues). |
| **Database Scanning** | Teste les bases de données (MySQL, MSSQL, Oracle, PostgreSQL) pour misconfiguration ou vulnérabilités d'injection/exposition. |
| **Wireless Network Scanning** | Détermine les vulnérabilités des réseaux sans fil, identifie les réseaux non autorisés (rogue). |
| **Distributed Scanning** | Scan simultané des actifs distribués (serveurs/clients à différents endroits) avec synchronisation. |
| **Credentialed / Authenticated Scanning** | Le scanner se connecte au système cible avec des identifiants valides pour un scan plus complet. |
| **Non-Credentialed / Unauthenticated Scanning** | Évalue les systèmes sans identifiants valides — simule un attaquant externe. |
| **Manual Scanning** | Identification/évaluation/validation manuelle : inspection du code source, vérification des configurations, pentest. |
| **Automated Scanning** | Utilise des outils logiciels (Nessus, Qualys, GFI LanGuard) — règles prédéfinies, bases de vulnérabilités connues. |
| **Cloud-based Scanning** | Évalue la sécurité globale de l'infrastructure cloud selon les meilleures pratiques du fournisseur. |
| **Mobile Application Scanning** | Examine le code source et les contrôles de sécurité des applications mobiles et API. |
| **Physical Security Vulnerability Scanning** | Examen complet des actifs physiques. |
| **IoT Device Vulnerability Scanning** | Aperçu des faiblesses des dispositifs IoT connectés à Internet (matériel, logiciel, protocoles, échange de données). |

---

## Objectif 02 — Outils d'évaluation des vulnérabilités

### 2.1 Approches d'évaluation des vulnérabilités

Il existe **quatre types de solutions** d'évaluation :

| Solution | Description |
|---|---|
| **Product-Based** | Installées dans le réseau interne de l'organisation (espace privé/non routable ou adressable Internet). Si installées sur un réseau privé (derrière le firewall), ne peuvent pas toujours détecter les attaques extérieures. |
| **Service-Based** | Offertes par des tiers (sociétés d'audit/consulting). Inconvénient : les attaquants peuvent effectuer des scans depuis l'Internet/réseau externe. |
| **Tree-Based Assessment** | L'auditeur sélectionne différentes stratégies pour chaque machine/élément (ex. un scanner pour Windows/databases/web, un autre pour Linux). S'appuie sur les informations initiales et scanne en continu sans incorporer les nouvelles informations. |
| **Inference-Based Assessment** | Le scan commence par construire un inventaire des protocoles trouvés sur la machine, puis détecte les ports attachés aux services, puis sélectionne les vulnérabilités de chaque machine et exécute les tests pertinents. |

**Caractéristiques d'une bonne solution d'évaluation des vulnérabilités :**
- Couvre un large éventail d'actifs (réseaux, serveurs, endpoints, applications web, services cloud)
- Assure des résultats corrects en testant réseau, ressources, ports, protocoles, OS
- Utilise une approche **inference-based** bien organisée
- Scanne et vérifie automatiquement contre des bases de données continuellement mises à jour
- Crée des rapports courts, exploitables, personnalisables (par sévérité, tendances)
- Supporte plusieurs réseaux
- Suggère des remèdes et workarounds appropriés
- Imite le point de vue externe des attaquants
- Identifie les vulnérabilités avec un minimum de faux positifs/négatifs
- Supporte le scan en temps réel et des mises à jour fréquentes
- Supporte l'automatisation et l'intégration avec les outils d'orchestration de sécurité
- Incorpore la priorisation basée sur les risques (sévérité + criticité de l'actif + contexte)

### 2.2 Fonctionnement des solutions de scanning

Le scan de vulnérabilités s'effectue en **trois étapes** :
1. **Localiser les nœuds** (locating nodes) : localiser les hôtes vivants du réseau cible
2. **Découverte des services et de l'OS** (service and OS discovery) : énumérer les ports ouverts, services et OS
3. **Tester les services et l'OS** pour les vulnérabilités connues

### 2.3 Types d'outils d'évaluation des vulnérabilités

Il existe **six types** d'outils :
- **Host-based** : adaptés aux serveurs exécutant diverses applications ; détectent des niveaux élevés de vulnérabilités et fournissent des infos sur les correctifs
- **Application-layer** : orientés vers les serveurs web ou bases de données ; identification des vulnérabilités externes (DoS/DDoS, interception de données)
- **Depth assessment tools** : découvrent des vulnérabilités auparavant inconnues (fuzzers qui fournissent une entrée arbitraire à l'interface du système)
- **Scope assessment tools** : évaluent la sécurité en testant les vulnérabilités des applications et de l'OS ; fournissent des contrôles standards et une interface de rapport
- **Active tools** : effectuent des vérifications de vulnérabilités sur les fonctions réseau qui consomment des ressources ; bon contrôle du timing mais ne conviennent pas aux OS critiques
- **Passive tools** : observent les données système et les traitent sur une machine d'analyse séparée ; n'affectent pas significativement les ressources
- **Location and data examination tools** :
  - **Network-based scanner** : interagit uniquement avec la machine où il réside
  - **Agent-based scanner** : réside sur une seule machine mais peut scanner plusieurs machines du réseau
  - **Proxy scanner** : scanner basé réseau qui peut scanner depuis n'importe quelle machine du réseau
  - **Cluster scanner** : comme les proxy scanners, mais peut effectuer simultanément deux scans ou plus sur différentes machines

### 2.4 Choix d'un outil d'évaluation des vulnérabilités

**Exigences pour un bon outil :**
- Capable de tester de quelques dizaines à **30 000 vulnérabilités**
- Base de données de vulnérabilités saine et signatures d'attaque fréquemment mises à jour
- Correspond à l'environnement et à l'expertise
- Moteur de scan régulièrement mis à jour
- Cartographie réseau/applications précise et tests de pénétration
- Scripts de vulnérabilités régulièrement mis à jour pour les plateformes scannées
- Patchs appliqués (sinon faux positifs)
- Rapports nombreux, informatifs, exportables
- Différents niveaux de pénétration pour éviter les blocages
- Coûts de maintenance compensés par une utilisation efficace
- Scans rapides et précis, multiples protocoles
- Comprend et analyse la topologie réseau
- Haute allocation de bande passante (grands réseaux)
- Excellentes fonctions de limitation des requêtes (query throttling)
- Capacité à évaluer les systèmes fragiles et les actifs non traditionnels

**Critères de choix d'un outil :**
- Types de vulnérabilités évaluées
- Capacité de test du scan
- Capacité à fournir des rapports précis (courts, clairs, avec méthode de mitigation)
- Scan efficace et précis (temps par hôte, ressources requises, perte de services pendant le scan)
- Smart search (intelligence au moment du scan)
- Fonctionnalité d'écriture de ses propres tests (quand une signature manque)
- Planification des tests (scheduling — scanner quand le trafic réseau est faible)
- Vitesse
- Compatibilité (divers environnements IT, systèmes hérités)
- Support de configuration (on-premises et cloud)
- Conformité (standards industriels, réglementations)
- Modèle de licence et coût (par actif/périphérique/IP/utilisateur/module)
- Évolutivité et performance

**Meilleures pratiques pour la sélection :**
- Assurer que l'outil n'endommage pas le réseau/système pendant l'exécution
- Comprendre la fonction de l'outil et décider des informations nécessaires avant de commencer
- Décider de l'emplacement du scan (interne vs externe)
- Activer la journalisation et annoter tous les résultats et méthodologies
- Scanner fréquemment et surveiller régulièrement

### 2.5 Outils d'évaluation des vulnérabilités

| Outil | Description | URL |
|---|---|---|
| **Nessus Essentials** | Solution d'évaluation pour identifier vulnérabilités, problèmes de configuration et malware ; pénétration de réseaux. Supporte OS, périphériques réseau, hyperviseurs, bases de données, tablettes/téléphones, serveurs web, infrastructures critiques. **Détection malware/botnet, découverte rapide d'actifs.** | https://www.tenable.com |
| **GFI LanGuard** | Scanne, détecte, évalue et corrige les vulnérabilités de sécurité du réseau et des périphériques connectés. **Patch management, évaluation des vulnérabilités, console de rapport web, intégration avec les applications de sécurité, support des environnements virtuels.** | https://www.gfi.com |
| **OpenVAS** | Framework de plusieurs services et outils offrant une solution complète de scanning et de gestion des vulnérabilités (partie de la solution commerciale Greenbone). **Plus de 50 000 tests de vulnérabilités réseau (NVTs) dans le feed.** | https://www.openvas.org |
| **Nikto** | Scanner de serveur web open source (GPL) qui effectue des tests complets : **plus de 6 700 fichiers/programmes dangereux**, versions obsolètes de **plus de 1 250 serveurs**, problèmes spécifiques à la version sur **plus de 270 serveurs**. SSL, support proxy HTTP, rapports en texte/XML/HTML/NBE/CSV, techniques d'encodage IDS LibWhisker, devinette de sous-domaines, énumération utilisateurs Apache/cgiwrap, devinette d'identifiants pour les zones d'autorisation. | https://cirt.net |
| **Qualys VM** | Service cloud donnant une visibilité globale et immédiate sur les systèmes vulnérables. **Agent-based detection, monitoring constant, couverture complète, Zero-Day et Patch impact predictions, analyse de tendances.** | https://www.qualys.com |

**Autres outils :** InsightVM (Rapid7), Acunetix Web Vulnerability Scanner, Nexpose (Rapid7), Sniper, Tripwire IP360, SAINT Security Suite, BeSECURE, Core Impact Pro, Intruder, ManageEngine Vulnerability Manager Plus, Astra Pentest, Skybox, MaxPatrol TM.

### 2.6 Outils d'évaluation des vulnérabilités alimentés par l'IA

Les scanners IA apprennent en continu des nouvelles données (menaces émergentes, modèles de techniques d'attaque), s'adaptent, réduisent les faux positifs et fournissent des informations plus précises et exploitables.

**Comparaison Traditionnel vs IA :**

| Point | VA traditionnelle | VA alimentée par l'IA |
|---|---|---|
| Périmètre | Vulnérabilités connues basées sur règles prédéfinies | Analyse de grandes quantités de données, vulnérabilités connues et inconnues |
| Priorisation | Sévérité technique seule | Priorisation basée sur les risques (criticité de l'actif, conformité, probabilité d'exploitation) |
| Efficacité | Chronophage, intensive en ressources | Automatisation et algorithmes |
| Adaptabilité | Difficile d'adaptation aux nouvelles menaces | Apprentissage continu |

**Outils IA :**
- **Equixly** (https://equixly.com) : SaaS, sécurise les API via ML. Détection pilotée par l'IA, analyse automatisée des menaces, monitoring en temps réel, apprentissage adaptatif
- **SmartScanner** (https://www.thesmartscanner.com) : scanneur automatisé pour la sécurité des sites web. ML supervisé et non supervisé, établissement de baselines, détection d'anomalies, analyses et réponse en temps réel
- **CodeDefender** (https://codedefender.ro) : détecte, priorise et corrige les vulnérabilités dans les codebases
- **Corgea** (https://corgea.com) : génère et déploie automatiquement des correctifs de sécurité
- **Fluxguard** (https://fluxguard.com) : scan et détection des vulnérabilités sur diverses infrastructures IT (analyse comportementale du trafic réseau)
- **DryRun Security** (https://www.dryrun.security) : plateforme de VA et pentest utilisant l'IA
- **Pentest Copilot** (https://copilot.bugbase.ai) : assistant de pentest piloté par l'IA (de la reconnaissance à l'exploitation)
- **Beagle Security** (https://beaglesecurity.com) : plateforme de test de sécurité d'applications web (top 10 OWASP)
- **Hackules** (https://hackules.com) : plateforme VA + pentest utilisant NLP et ML
- **CoderBuds** (https://coderbuds.com) : plateformes de sécurité de code pilotées par l'IA

### 2.7 Évaluation des vulnérabilités avec l'IA (ChatGPT / sgpt)

Exemples de prompts :
- **Nikto** : « Launch nikto to execute a scan against the URL www.certifiedhacker.com to identify potential vulnerabilities. » → `nikto -h www.certifiedhacker.com`
- « Perform vulnerability scan on target url http://testphp.vulnweb.com with nikto and save the results in output.txt. » → `nikto -h http://testphp.vulnweb.com -o output.txt`
- **Nmap** : « Perform a vulnerability scan on target url www.moviescope.com with nmap and save the results in output.txt » → `nmap -sV --script=vuln www.moviescope.com -oN output.txt`
- **Script Python** : « Create a python script to run a fast but comprehensive Nmap scan on the IP addresses in scan1.txt and then execute vulnerability scanning using nikto against each IP address in scan1.txt » → script Python utilisant `subprocess.run(['nmap', '-T4', '-A', '-v', ip])` et `subprocess.run(['nikto', '-h', ip])`
- **Skipfish** : « Perform a vulnerability scan on target url http://testphp.vulnweb.com with Skipfish and display the output file index.html in Firefox » → `skipfish -o /tmp/skipfish_output http://testphp.vulnweb.com && firefox /tmp/skipfish_output/index.html`

---

## Objectif 03 — Analyse des rapports d'évaluation des vulnérabilités

### 3.1 Rapport d'évaluation des vulnérabilités

Un **rapport d'évaluation des vulnérabilités** est un document complet qui détaille les résultats d'une évaluation des vulnérabilités : faiblesses de sécurité identifiées, impact potentiel, sévérité et recommandations de remédiation. Il guide les parties prenantes dans la prise de mesures correctives pour atténuer les risques.

Les vulnérabilités sont catégorisées par sévérité en **trois niveaux : Haut, Moyen, Bas risque** :
- **High-risk** : permettent un accès non autorisé au réseau → doivent être corrigées immédiatement avant compromission.

**Contenu obligatoire du rapport :**
- Nom de la vulnérabilité et son **ID CVE mappé**
- Date de découverte
- Score basé sur les bases de données CVE
- Description détaillée de la vulnérabilité
- Impact de la vulnérabilité
- Détails sur les systèmes affectés
- Détails sur le processus de correction (patches, corrections de configuration, ports à bloquer)
- **Preuve de concept (PoC)** de la vulnérabilité si possible

### 3.2 Composants d'un rapport d'évaluation des vulnérabilités

1. **Résumé exécutif (Executive Summary)** :
   - Périmètre et objectifs de l'évaluation, but du scan, périmètre du scan
   - Narration des tests : OS scannés, adresses IP scannées, types de scans, date/heure (début, fin, durée)
   - Résumé des constatations : vulnérabilités critiques mises en évidence, nombre de vulnérabilités par sévérité (représentation graphique), OS identifiés, performance des systèmes pendant le scan, niveau de risque global, problèmes critiques à traiter
   - Résumé de la remédiation, résumé de conformité des composants
2. **Vue d'ensemble de l'évaluation (Assessment Overview)** :
   - Méthodologie d'évaluation
   - Informations de scan : type de scan, outils utilisés, versions, actifs scannés
   - Informations cible : nom et adresse du système
   - Outils impliqués
3. **Constatations (Findings)** :
   - Hôtes scannés (nom, adresse, OS, date), services vulnérables (noms et ports)
   - Actifs affectés, types de vulnérabilités identifiées
   - Informations détaillées sur les vulnérabilités identifiées (ID CVE, score CVSS, description de la menace, impact, remédiation, exploitabilité)
   - Notes décrivant les détails supplémentaires des résultats de scan
4. **Évaluation des risques (Risk Assessment)** :
   - Classification des vulnérabilités selon le niveau de risque : critique, haut, modéré ou bas
   - Vulnérabilités potentielles pouvant compromettre le système ou l'application
   - Hôtes critiques avec vulnérabilités sévères
5. **Recommandations (Recommendations)** :
   - Priorisation de la remédiation selon le classement des risques
   - Plan d'action pour chaque vulnérabilité identifiée
   - Analyse de cause racine, application de patches/fixes, leçons apprises, formation de sensibilisation, mise en œuvre d'évaluations périodiques, mise en œuvre de politiques/procédures/contrôles
6. **Annexes et informations de support (Appendices)** : journaux détaillés, fichiers de configuration, références à des ressources externes
7. **Conclusion** : résumé des constatations clés et recommandations
8. **Actions de suivi et calendrier (Follow-Up Actions and Timeline)** : calendrier de réévaluation et monitoring de l'efficacité des remédiations
9. **Glossaire des termes**

### 3.3 Types de rapports de vulnérabilités

| Type | Description |
|---|---|
| **Security Vulnerability Report** | Rapport combiné de tous les périphériques et serveurs scannés. Inclut : vulnérabilités nouvellement trouvées, ports ouverts et services détectés, suggestions de remédiation, liens vers les patches. |
| **Security Vulnerability Summary** | Produit pour chaque périphérique/serveur après le scan. Inclut : failles de sécurité actuelles, catégories de vulnérabilités, vulnérabilités nouvellement détectées, sévérité, vulnérabilités résolues. |

---

## Aide-mémoire examen (à retenir absolument)

| Concept | Détail clé |
|---|---|
| **Vulnerability analysis** | Processus systématique d'identification, évaluation et priorisation des faiblesses de sécurité |
| **Classification** | Misconfigurations, application flaws, poor patch management, design flaws, third-party risks |
| **Buffer overflow** | Écriture au-delà du buffer → crash/exécution de code (root cause : manque de bounds checking) |
| **Memory leak** | Outil : **Valgrind** (Unix/Linux) |
| **Fail-open** | Octroi d'accès après un échec du système (improper error handling) |
| **Code signing** | Protéger les clés privées dans des **HSM** |
| **Zero-day** | Vulnérabilité inconnue, non patchée, exploitée avant découverte |
| **CVSS** | Standard de scoring ouvert (FIRST.Org) ; score 0–10 ; groupes : Base, Threat, Environmental, Supplemental |
| **Ratings CVSS** | None 0.0 / Low 0.1-3.9 / Medium 4.0-6.9 / High 7.0-8.9 / Critical 9.0-10.0 |
| **CVE** | Dictionnaire d'identifiants standardisés (cve.mitre.org) ; IDs assignés par les **CNAs** |
| **NVD** | Référentiel US gouvernemental (nvd.nist.gov), utilise **SCAP**, analyse les CVE |
| **CWE** | Catégorisation des faiblesses (cwe.mitre.org), **600+ catégories**, sponsorisé MITRE |
| **Cycle de vie** | Pre-Assessment → Assessment → Post-Assessment (Risk Assessment, Remediation, Verification, Monitoring) |
| **Remediation SMART** | Spécifique, mesurable, atteignable, pertinent, limité dans le temps |
| **Active scanning** | Interaction directe avec le réseau cible |
| **Passive scanning** | Observation sans interaction directe (analyse des communications normales) |
| **Scanner limitations** | Ne détecte pas les **zero-day** ; faux positifs/négatifs ; dépend de la base de données |
| **External scan** | Point de vue du hacker, via firewall/routeurs |
| **Host-based scan** | Vérifie configurations, registre, permissions |
| **Credentialed scan** | Connexion avec identifiants valides → scan plus complet |
| **Non-credentialed scan** | Simule un attaquant externe sans identifiants |
| **Approches** | Product-based, service-based, tree-based, inference-based |
| **3 étapes du scan** | Locating nodes → Service & OS discovery → Testing for known vulnerabilities |
| **Outils location** | Network-based, agent-based, proxy, cluster scanner |
| **Nessus** | Tenable — détection malware/botnet, VA, compliance |
| **GFI LanGuard** | Patch management + VA, console de rapport web |
| **OpenVAS** | Greenbone, **50 000+ NVTs** |
| **Nikto** | Scanner web serveur : **6700+ fichiers dangereux**, 1250+ serveurs obsolètes, 270+ problèmes version |
| **Qualys VM** | Cloud, agent-based, Zero-Day & Patch impact predictions |
| **IA tools** | Equixly (API), SmartScanner, Corgea, Pentest Copilot, Beagle Security |
| **Nmap vuln scan IA** | `nmap -sV --script=vuln www.moviescope.com -oN output.txt` |
| **Nikto IA** | `nikto -h <URL> -o output.txt` |
| **Skipfish** | `skipfish -o /tmp/skipfish_output <URL> && firefox .../index.html` |
| **Rapport** | Nom + ID CVE + date + score CVE + description + impact + systèmes affectés + correction + **PoC** |
| **3 niveaux de risque** | High, Medium, Low |
| **2 types de rapports** | Security Vulnerability Report, Security Vulnerability Summary |
| **Contenu rapport** | Executive Summary, Assessment Overview, Findings, Risk Assessment, Recommendations, Appendices, Conclusion, Follow-Up, Glossary |

---

## Synthèse du module

Ce module a montré :
- Les différents types de vulnérabilités, le système de scoring CVSS et les bases de données (CVE, NVD, CWE)
- Le cycle de vie de la gestion des vulnérabilités et la recherche de vulnérabilités
- Le scanning des vulnérabilités, l'analyse et les différents types de techniques de scanning
- Les différentes solutions d'évaluation des vulnérabilités et leurs caractéristiques
- Les différents outils de test d'un hôte ou d'une application, avec les critères et meilleures pratiques de sélection
- L'analyse des rapports d'évaluation des vulnérabilités

**Le prochain module** montrera comment les attaquants, les hackers éthiques et les pentesters tentent le **system hacking** (Module 06) sur la base des informations collectées lors des phases de footprinting, scanning, énumération et analyse des vulnérabilités.
