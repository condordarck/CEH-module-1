# Module 01 — Introduction au Hacking Éthique (CEH v13)
## Cours complet expliqué en français

> Document pédagogique basé sur le PDF **« CEHv13 - Module 01 - Introduction to Ethical Hacking »** d'EC-Council (certification **CEH**, examen **312-50**).
> Ce document reprend et **explique** tout le contenu du module, chapitre par chapitre.

---

# Table des matières

1. [Le contexte : la certification CEH](#1-le-contexte--la-certification-ceh)
2. [Les concepts de sécurité de l'information](#2-les-concepts-de-sécurité-de-linformation)
3. [Le hacking et les classes de hackers](#3-le-hacking-et-les-classes-de-hackers)
4. [Le hacking éthique](#4-le-hacking-éthique)
5. [Le hacking éthique piloté par l'IA](#5-le-hacking-éthique-piloté-par-lia)
6. [Les méthodologies et frameworks de hacking](#6-les-méthodologies-et-frameworks-de-hacking)
7. [Les contrôles de sécurité de l'information](#7-les-contrôles-de-sécurité-de-linformation)
8. [Les lois et standards de la sécurité de l'information](#8-les-lois-et-standards-de-la-sécurité-de-linformation)
9. [Aide-mémoire final pour l'examen](#9-aide-mémoire-final-pour-lexamen)

---

# 1. Le contexte : la certification CEH

## 1.1 C'est quoi le CEH ?

Le **Certified Ethical Hacker (CEH)** est une certification délivrée par **EC-Council**, organisation fondée en 2001 qui forme et certifie les professionnels de la sécurité de l'information. Le CEH est aujourd'hui considéré comme une référence mondiale : il est proposé dans plus de **145 pays** par plus de **950 centres de formation agréés**.

L'idée centrale du CEH est résumée par une phrase célèbre : *« Pour arrêter les hackers, il faut d'abord pénétrer leur esprit. »* La philosophie : **pour attraper un voleur, il faut penser comme un voleur**. Un hacker éthique doit donc maîtriser les mêmes outils, techniques et méthodes que les hackers malveillants, mais les utiliser **légalement et avec autorisation**.

## 1.2 L'examen CEH 312-50

| Caractéristique | Détail |
|---|---|
| Titre | Certified Ethical Hacker (CEH) |
| Code examen | 312-50 |
| Durée | 4 heures |
| Nombre de questions | 125 |
| Score de réussite | Variable (voir cert.eccouncil.org) |
| Plateforme | Pearson VUE / EC-Council Exam Portal |

## 1.3 Les prérequis conseillés

Avant de suivre ce cours, il est recommandé d'avoir des bases sur :
- les systèmes d'exploitation et les systèmes de fichiers ;
- les réseaux informatiques et les protocoles TCP/IP ;
- les contrôles de sécurité de l'information ;
- le dépannage réseau de base, la sauvegarde des données et la gestion des risques.

## 1.4 Les objectifs pédagogiques du Module 01

À la fin de ce module, vous saurez :
1. Décrire les **éléments de la sécurité de l'information** (confidentialité, intégrité, disponibilité, authenticité, non-répudiation).
2. Expliquer les **attaques** contre la sécurité de l'information et la **guerre de l'information**.
3. Décrire les **concepts de hacking** et les **classes de hackers**.
4. Expliquer les **concepts du hacking éthique** et le **hacking éthique piloté par l'IA**.
5. Décrire les **méthodologies et frameworks de hacking** (CEH framework, Cyber Kill Chain, MITRE ATT&CK, Diamond Model).
6. Comprendre les **contrôles de sécurité** (information assurance, défense en profondeur, gestion des risques, threat intelligence, modélisation des menaces, gestion des incidents, IA/ML).
7. Comprendre les **lois et standards** de la sécurité de l'information.

---

# 2. Les concepts de sécurité de l'information

## 2.1 Définition

> La **sécurité de l'information** est l'état de bien-être de l'information et de l'infrastructure dans lequel la possibilité de vol, de falsification ou de perturbation de l'information et des services est **faible ou tolérable**.

Elle protège l'information **et** les systèmes qui la stockent, la transmettent et la traitent, contre l'accès, la divulgation, la modification ou la destruction non autorisés.

## 2.2 Les 5 piliers de la sécurité de l'information

### a) Confidentialité
La garantie que l'information n'est **accessible qu'aux personnes autorisées**.

- Exemples de violation : mauvaise manipulation des données, tentative de piratage.
- Contrôles : **classification des données**, **chiffrement**, destruction correcte des supports (DVD, clés USB, disques).

### b) Intégrité
La **fiabilité** des données ou des ressources : prévenir les **modifications non autorisées ou inappropriées**.

- Contrôles : **checksum** (fonction mathématique qui vérifie qu'un bloc de données n'a pas changé), **contrôle d'accès** (seules les personnes autorisées peuvent modifier/ajouter/supprimer des données).

### c) Disponibilité
La garantie que les systèmes qui délivrent, stockent et traitent l'information sont **accessibles quand les utilisateurs autorisés en ont besoin**.

- Contrôles : **baies de disques redondantes**, machines **en cluster**, **antivirus**, systèmes de prévention **DDoS**.

### d) Authenticité
La qualité de ce qui est **authentique ou non corrompu** : une communication, un document ou des données réellement d'origine.

- Contrôles : **biométrie**, **cartes à puce**, **certificats numériques**.

### e) Non-répudiation
La garantie qu'un **expéditeur ne peut pas nier avoir envoyé** un message, et qu'un **destinataire ne peut pas nier l'avoir reçu**.

- Contrôle : **signatures numériques**.

> 💡 **À retenir** : on parle souvent des 3 premiers (le célèbre **triade CIA** : Confidentiality, Integrity, Availability) mais le module CEH en ajoute deux : l'**authenticité** et la **non-répudiation**.

## 2.3 Les attaques : motifs, buts et objectifs

### La formule fondamentale

> **Attaque = Motif (But) + Méthode (TTP) + Vulnérabilité**

Un **motif** naît de l'idée que le système cible stocke ou traite quelque chose de **précieux**, ce qui déclenche la menace d'une attaque. L'attaquant utilise ensuite divers **outils et techniques (TTP)** pour exploiter des **vulnérabilités**.

### Les principaux motifs des attaques
- Perturber la **continuité d'activité** de l'entreprise ;
- Voler des **informations** ;
- **Manipuler** des données ;
- Créer la peur et le chaos en perturbant les **infrastructures critiques** ;
- Causer des **pertes financières** ;
- Propager des **croyances religieuses ou politiques** ;
- Atteindre les **objectifs militaires** d'un État ;
- **Nuire à la réputation** de la cible ;
- Se **venger** ;
- Exiger une **rançon**.

## 2.4 Les TTP : Tactiques, Techniques et Procédures

Les **TTP** désignent les schémas d'activités et méthodes associés à des acteurs de menace spécifiques ou à des groupes. Elles servent à **analyser les menaces** et à **profiler les acteurs de menace**.

| Notion | Définition |
|---|---|
| **Tactique** | La **stratégie** adoptée par l'attaquant pour mener l'attaque du début à la fin |
| **Technique** | Les **méthodes techniques** utilisées pour obtenir des résultats intermédiaires pendant l'attaque |
| **Procédure** | L'**approche systématique** suivie par les acteurs de menace pour lancer l'attaque |

Comprendre les tactiques permet de **prédire et détecter** les menaces émergentes ; comprendre les techniques permet d'**identifier les vulnérabilités** et de mettre en place des défenses ; analyser les procédures permet de savoir **ce que l'attaquant cherche** dans l'infrastructure de l'organisation.

## 2.5 Les vulnérabilités

### Définition
Une **vulnérabilité** est une faiblesse dans la conception ou l'implémentation d'un système qui peut être **exploitée** pour compromettre sa sécurité. C'est souvent une faille qui permet à un attaquant d'entrer dans le système en **contournant l'authentification**.

### Les causes courantes des vulnérabilités

1. **Mauvaise configuration matérielle ou logicielle** — ex. utilisation de protocoles non chiffrés, pare-feu mal configurés, périphériques réseau sans protection par mot de passe.
2. **Conception insuffisante ou peu sûre du réseau et des applications** — ex. pare-feu, IDS, VPN mal implémentés.
3. **Faiblesses technologiques inhérentes** — ex. protocoles TCP/IP comme HTTP, FTP, ICMP, SNMP, SMTP intrinsèquement peu sûrs ; OS non patchés ; navigateurs obsolètes.
4. **Négligence des utilisateurs finaux** — ex. partage d'identifiants, connexion à des réseaux non sécurisés, fallait à l'ingénierie sociale.
5. **Actes intentionnels des utilisateurs** — ex. ex-employés qui conservent un accès aux partages et divulguent des informations sensibles.

### Exemples de vulnérabilités technologiques
| Type | Exemples |
|---|---|
| Protocoles TCP/IP | HTTP, FTP, ICMP, SNMP, SMTP intrinsèquement peu sûrs |
| Systèmes d'exploitation | OS intrinsèquement peu sûrs, non patchés |
| Équipements réseau | Absence de protection par mot de passe, absence d'authentification, protocoles de routage non sûrs, vulnérabilités de pare-feu |

### Exemples de vulnérabilités de configuration
| Type | Exemples |
|---|---|
| Comptes utilisateurs | Transmission non sécurisée des identifiants (username/password) sur le réseau |
| Comptes système | Mots de passe faibles définis pour les comptes système |
| Services Internet | JavaScript activé, IIS/Apache/FTP/Terminal services mal configurés |
| Équipements réseau | Mots de passe et paramètres par défaut laissés en place, équipements mal configurés |

## 2.6 La classification des attaques (norme IATF)

La norme **IATF (Information Assurance Technical Framework)** classe les attaques en **5 catégories** :

### 1. Attaques passives
Interception et **surveillance** du trafic réseau sans altérer les données. Très **difficiles à détecter** car elles ne modifient rien.

- Exemples : **footprinting**, **sniffing** et **eavesdropping** (écoute clandestine), **analyse du trafic réseau**, **décryptage** du trafic faiblement chiffré.

### 2. Attaques actives
**Altération** des données en transit ou **perturbation** des communications/services pour contourner ou pénétrer des systèmes sécurisés. Elles sont **détectables** car elles envoient activement du trafic.

- Exemples : **DoS**, attaques de **pare-feu et IDS**, contournement de protections, **profiling**, **malware** (virus, vers, ransomware), exécution de code arbitraire, **escalade de privilèges**, modification d'informations, **backdoor**, **spoofing**, attaques de cryptographie, **replay attacks**, **SQL injection**, attaques par mot de passe, **XSS**, **session hijacking**, **directory traversal**, **MITM**, **empoisonnement DNS et ARP**, attaques par clé compromise.

### 3. Attaques de proximité (« close-in »)
Menées lorsque l'attaquant est **physiquement proche** du système ou du réseau cible, pour recueillir, modifier ou perturber l'accès à l'information.

- Exemples : **ingénierie sociale** (eavesdropping, **shoulder surfing** — regarder par-dessus l'épaule, **dumpster diving** — fouiller les poubelles).

### 4. Attaques internes (« insider »)
Menées par des **personnes de confiance** ayant un **accès physique** aux actifs critiques. Elles contournent facilement les règles de sécurité.

- Exemples : eavesdropping et **wiretapping** (mise sur écoute), **pod slurping** (extraction de données via un appareil externe), vol de dispositifs physiques, installation de **keyloggers**, **backdoors** ou **malware**, ingénierie sociale, vol et spoliation de données.

### 5. Attaques de distribution
Altération du **matériel ou du logiciel avant son installation**, à la source ou **en transit**.

- Exemples : **backdoors créées par les fabricants** de logiciels ou de matériel à la fabrication, modification pendant la production ou la distribution.

## 2.7 La guerre de l'information (InfoWar)

> La **guerre de l'information** consiste à utiliser les **TIC (technologies de l'information et de la communication)** pour obtenir un **avantage compétitif** sur un adversaire.

Armes de guerre de l'information : virus, vers, chevaux de Troie, bombes logiques, trappes, brouillage électronique, exploits et outils de pénétration.

### Les 7 catégories de Martin Libicki

1. **Guerre commandement et contrôle (C2 warfare)** : impact d'un attaquant sur un système/réseau compromis qu'il contrôle.
2. **Guerre fondée sur le renseignement** : technologie basée sur des capteurs qui corrompt directement des systèmes technologiques (conception, protection, déni de systèmes).
3. **Guerre électronique** : techniques radio-électroniques (attaquer les moyens physiques d'envoyer l'information) et cryptographiques (perturber la transmission par bits et octets).
4. **Guerre psychologique** : propagande et terreur pour **démoraliser** l'adversaire.
5. **Guerre des hackers** : arrêt de systèmes, erreurs de données, vol d'informations/services, surveillance de systèmes, faux messages, accès aux données — via virus, bombes logiques, chevaux de Troie, sniffers.
6. **Guerre économique** : blocage du **flux d'information** pour affecter l'économie d'une entreprise ou d'une nation.
7. **Cyberguerre** : la plus vaste, usage de systèmes d'information contre les « personnes virtuelles » d'individus ou de groupes — inclut le **terrorisme informationnel**, les **attaques sémantiques** (prise de contrôle d'un système tout en laissant croire qu'il fonctionne normalement) et la **simula-guerre** (guerre simulée).

### Deux volets complémentaires
- **Guerre défensive** : toutes les stratégies pour se défendre contre les attaques sur les actifs TIC (prévention, dissuasion, alertes, détection, préparation aux urgences, réponse).
- **Guerre offensive** : attaques contre les actifs TIC de l'adversaire (attaques web/serveurs, malware, MITM, hacking de systèmes).

---

# 3. Le hacking et les classes de hackers

## 3.1 Qu'est-ce que le hacking ?

> Le **hacking** consiste à **exploiter les vulnérabilités** d'un système et à **compromettre les contrôles de sécurité** pour obtenir un accès **non autorisé ou inapproprié** aux ressources d'un système.

Il implique de modifier des fonctionnalités du système ou des applications pour atteindre un objectif **au-delà de l'usage prévu par le créateur**. Il peut être utilisé pour voler ou redistribuer de la **propriété intellectuelle**, entraînant des pertes commerciales.

Techniques de hacking réseau : virus et vers, attaques **DoS**, connexions à distance non autorisées via **trojans/backdoors**, **botnets**, **packet sniffing**, **phishing**, **cracking de mots de passe**.

**Motivations** : vol d'informations critiques, frisson, défi intellectuel, curiosité, expérimentation, connaissance, gain financier, prestige, pouvoir, reconnaissance par les pairs, vengeance.

## 3.2 Qui est un hacker ?

Un **hacker** est une personne **intelligente** avec d'excellentes compétences informatiques, capable de créer et d'explorer logiciels et matériels. C'est généralement un ingénieur ou programmeur expérimenté qui connaît les langages de programmation et les systèmes informatiques.

- Pour certains, le hacking est un **hobby** : combien de machines peuvent-ils compromettre ?
- Pour d'autres, c'est **malveillant** : vol de données professionnelles, numéros de cartes de crédit, numéros de sécurité sociale, mots de passe email.

## 3.3 Les classes de hackers

### Les classes principales

| Classe | Profil | Activités | Motivations | Cibles |
|---|---|---|---|---|
| **Script Kiddies** | Jeunes, inexpérimentés, utilisent des scripts/outils tout faits sans les comprendre | DDoS, défiguration de sites web | Frisson, reconnaissance, fun | Petits sites, jeux en ligne, forums |
| **White Hat** (chapeaux blancs) | Professionnels de la cybersécurité | Tests d'intrusion, évaluations de vulnérabilité | Améliorer la sécurité, salaire, réputation | Entreprises, agences gouvernementales |
| **Black Hat** (chapeaux noirs / crackers) | Individus aux compétences extraordinaires | Création de malware, phishing, ransomware, fuites de données | Gain financier, vol de données, causer du tort | Institutions financières, particuliers, entreprises |
| **Gray Hat** (chapeaux gris) | Hackers compétents entre l'éthique et l'illégalité | Découverte de vulnérabilités **sans permission**, parfois signalées ensuite | Reconnaissance, curiosité, gain financier | Diverses, dont organisations de haut profil |
| **Hacktivistes** | Individus motivés politiquement/socialement | DDoS, défiguration de sites, fuites de données | Promouvoir une cause, justice sociale | Sites gouvernementaux, entreprises, groupes politiques |
| **Hackers sponsorisés par un État** | Professionnels très entraînés travaillant pour des agences gouvernementales | Cyber espionnage, sabotage d'infrastructures, vol de données | Sécurité nationale, espionnage, objectifs politiques | Agences d'autres nations, entreprises |
| **Cyberterroristes** | Extrémistes | Attaques sur les infrastructures critiques, diffusion de propagande | Répandre la peur, objectifs politiques/religieux | Infrastructures critiques, services publics |
| **Espions industriels** | Individus embauchés par des entreprises | Espionnage industriel, vol de données, espionnage | Gain financier, avantage concurrentiel | Entreprises concurrentes |
| **Blue Hat** | Professionnels de sécurité embauchés temporairement | Audits de sécurité, tests d'intrusion avant lancement de produit | Améliorer la sécurité du produit, réputation | Sociétés technologiques, éditeurs de logiciels |
| **Red Hat** | Vigilantes ciblant les black hats | Hacking d'infrastructures black hat, désactivation de réseaux malveillants | Justice cyber, perturbation des activités malveillantes | Groupes cybercriminels, black hats |
| **Green Hat** | Nouveaux venus désireux d'apprendre | Apprentissage, expérimentation d'attaques simples, forums | Apprentissage, curiosité, reconnaissance | Cibles à faible risque |
| **Suicide Hackers** | Individus prêts à tout pour une « cause » | Sabotage d'infrastructures critiques | Sacrifice, indifférence aux conséquences | Infrastructures critiques |

### Autres acteurs de menace

- **Hacker Teams** : consortiums de hackers expérimentés disposant de leurs propres technologies, capables de détecter des vulnérabilités et d'exécuter des attaques planifiées.
- **Insiders** : employés de confiance ayant accès aux actifs critiques — employés mécontents, licenciés ou mal formés.
- **Syndicats criminels** : groupes hiérarchisés organisés pour des activités criminelles prolongées ; utilisent des appareils loués, des **botnets** et des services de **crimeware** ; volent de l'argent et vendent des informations au plus offrant ; peuvent rester indétectés longtemps.

---

# 4. Le hacking éthique

## 4.1 Qu'est-ce que le hacking éthique ?

> Le **hacking éthique** consiste à utiliser les **outils, astuces et techniques de hacking** pour **identifier les vulnérabilités** et garantir la sécurité d'un système.

- Il **simule** les techniques des attaquants pour **vérifier l'existence de vulnérabilités exploitables**.
- Il est réalisé par des **White Hats** (analystes de sécurité) **avec la permission** des autorités concernées (le propriétaire du système/réseau).
- Les éthiques hackers **signalent toutes les vulnérabilités** au propriétaire pour qu'il les corrige.

### La différence fondamentale : le consentement
> La différence la plus importante entre un **éthique hacker** et un **cracker** est le **consentement**. Les crackers tentent d'accéder aux systèmes sans autorisation ; les éthiques hackers sont **transparents** sur ce qu'ils font et comment ils le font. **Le hacking éthique est donc toujours légal.**

### Les 3 questions fondamentales de l'éthique hacker
1. **Que peut voir un attaquant sur le système cible ?** (phase de reconnaissance/scanning)
2. **Que peut faire un intrus avec cette information ?** (phases d'accès et de maintien d'accès)
3. **Les tentatives des attaquants sont-elles remarquées sur le système cible ?** (phases de reconnaissance et d'effacement des traces)

Et aussi :
- Qu'est-ce que l'organisation essaie de protéger ?
- Contre qui ou quoi ?
- Tous les composants sont-ils protégés, mis à jour, patchés ?
- Combien de temps, d'effort et d'argent le client veut-il investir ?
- Les mesures respectent-elles les normes industrielles et légales ?

## 4.2 Pourquoi le hacking éthique est-il nécessaire ?

> **Pour battre un hacker, il faut penser comme lui !**

Le hacking éthique permet de **contrer les attaques** des hackers malveillants en **anticipant leurs méthodes** et en corrigeant les vulnérabilités **avant** qu'elles ne soient exploitées. Les tests de vulnérabilité et les audits de sécurité seuls ne suffisent pas — il faut adopter une approche de **défense en profondeur** en pénétrant ses propres réseaux.

**Pourquoi les organisations recrutent des éthiques hackers :**
- Empêcher les hackers d'accéder aux systèmes d'information ;
- Découvrir les vulnérabilités et explorer leur potentiel de risque ;
- Analyser et renforcer la posture de sécurité (politiques, infrastructure réseau, pratiques des utilisateurs finaux) ;
- Mettre en place des mesures préventives pour éviter les brèches ;
- Protéger les données clients ;
- Renforcer la sensibilisation à la sécurité à tous les niveaux de l'entreprise.

## 4.3 Portée et limites du hacking éthique

### Portée
- Composante clé de l'**évaluation des risques**, de l'**audit**, de l'**anti-fraude** et des bonnes pratiques de sécurité des systèmes d'information.
- Permet d'identifier les risques, de mettre en évidence les actions correctives et de **réduire les coûts TIC** en résolvant les vulnérabilités.
- Souvent réalisé par des **« Tiger Teams »** : groupes qui testent tous les aspects du réseau (intrusion physique et système).

### Règles d'or de l'éthique hacker
1. **Obtenir l'autorisation** du client avec un **contrat signé** autorisant le test.
2. **Signer une NDA** (accord de non-divulgation) pour les informations confidentielles divulguées pendant le test — ne rien révéler à un tiers.
3. **Ne pas dépasser les limites convenues** — ex. ne faire un test DoS que si cela a été convenu au préalable (sinon risque de perte de revenus, de bonne volonté et pire).

### Cadre d'un audit de sécurité éthique (7 étapes)
1. Discuter avec le client des besoins à traiter pendant le test.
2. Préparer et signer les documents NDA.
3. Organiser l'équipe de hacking éthique et préparer le calendrier des tests.
4. Conduire le test.
5. Analyser les résultats et préparer un rapport.
6. Présenter les conclusions au client.

### Limites
- À moins que l'entreprise ne sache **ce qu'elle cherche** et **pourquoi** elle engage un prestataire externe, il n'y aura pas grand-chose à gagner.
- Un éthique hacker aide l'organisation à mieux comprendre son système de sécurité, mais **c'est à l'organisation de mettre en place les bonnes protections** sur son réseau.

## 4.4 Les compétences de l'éthique hacker

### Compétences techniques
- Connaissance approfondie des principaux environnements OS : Windows, Unix, Linux, Macintosh ;
- Connaissance approfondie des concepts réseaux, technologies et matériel/logiciels associés ;
- Expert informatique dans les domaines techniques ;
- Connaissance des domaines de sécurité et des problèmes associés ;
- Haute connaissance technique pour lancer des attaques sophistiquées.

### Compétences non techniques
- Capacité à apprendre et adopter rapidement de nouvelles technologies ;
- Forte éthique de travail, bonnes compétences en résolution de problèmes et en communication ;
- Engagement envers les politiques de sécurité de l'organisation ;
- Connaissance des normes et lois locales.

---

# 5. Le hacking éthique piloté par l'IA

## 5.1 Pourquoi l'IA change la donne

Les avancées de l'**intelligence artificielle (IA)** ont rendu les cybermenaces plus sophistiquées : les hackers utilisent de plus en plus des outils pilotés par l'IA pour **automatiser et augmenter** leurs tentatives d'attaque.

Le **hacking éthique piloté par l'IA** est une approche moderne où les technologies d'IA (algorithmes d'IA, modèles de **machine learning**, frameworks d'automatisation) **améliorent les capacités des éthiques hackers** et permettent de **mitiger les risques de manière proactive**.

## 5.2 Les 4 grands bénéfices

| Bénéfice | Explication |
|---|---|
| **Efficacité** | L'IA traite rapidement de grandes quantités de données, rendant le hacking éthique plus rapide et efficace |
| **Précision** | Réduit l'erreur humaine et augmente la précision des évaluations de vulnérabilité |
| **Scalabilité** | Les solutions IA peuvent être étendues pour gérer la complexité et le volume croissants des cybermenaces |
| **Coût-efficacité** | L'automatisation et les gains d'efficacité réduisent les coûts globaux de la cybersécurité |

## 5.3 Les applications de l'IA dans le hacking éthique

- **Sécurité réseau** : surveillance du trafic réseau pour détecter des activités suspectes et des brèches potentielles ;
- **Sécurité applicative** : test des applications web et mobiles avec des outils alimentés par l'IA ;
- **Sécurité cloud** : identification et mitigation des risques dans les environnements cloud ;
- **Sécurité IoT** : protection des objets connectés contre les cybermenaces ;
- **Threat Intelligence** : collecte et analyse des données de menaces pour fournir des renseignements actionnables.

## 5.4 Comment l'IA aide l'éthique hacker (10 façons)

1. **Automatisation des tâches répétitives** — scan de vulnérabilités, surveillance du trafic, identification des menaces → l'éthique hacker se concentre sur les tâches complexes.
2. **Analyse prédictive** — les algorithmes prédisent les brèches en analysant les schémas et anomalies ; les modèles ML apprennent des attaques passées.
3. **Détection avancée de menaces** — détection de menaces sophistiquées et inconnues (**zero-day**) via le deep learning et l'analyse d'anomalies.
4. **Prise de décision améliorée** — insights et recommandations basés sur l'analyse des données.
5. **Apprentissage adaptatif** — les systèmes IA apprennent en continu de nouvelles cyberattaques.
6. **Reporting renforcé** — rapports détaillés et précis sur les vulnérabilités et leur impact potentiel.
7. **Simulation et test** — simulation d'attaques réelles pour tester la résilience.
8. **Scalabilité** — gestion d'environnements étendus et complexes plus efficacement que les méthodes manuelles.
9. **Surveillance continue** — évaluation en temps réel de la posture de sécurité.
10. **Mécanismes de défense adaptatifs** — l'IA s'adapte aux nouvelles menaces en mettant à jour ses algorithmes et stratégies.

## 5.5 Le mythe : « l'IA va remplacer les éthiques hackers »

**FAUX.** L'IA est un **outil précieux** dans l'arsenal de l'éthique hacker, **pas un remplacement**.

- L'IA peut automatiser certains aspects et améliorer l'efficacité, mais elle ne peut pas remplacer la **créativité**, la **pensée critique** et la **connaissance complexe** que les éthiques hackers humains apportent.
- Les humains comprennent en profondeur les systèmes et réseaux, peuvent **penser comme des attaquants**, identifier des points d'entrée et créer des stratégies de mitigation sur mesure.
- La **supervision humaine** est essentielle pour interpréter les résultats, valider les découvertes et prendre des jugements éclairés basés sur le **contexte** et les **principes éthiques**.
- Le meilleur résultat : **IA + humains travaillant ensemble**.

## 5.6 Les outils d'IA propulsés par ChatGPT

### Fonctionnalités clés
- **Collecte et configuration de données** depuis réseaux sociaux, forums, sites web, bases de données publiques ;
- **Assistance en temps réel et automatisation de tâches** via NLP et ML (scan de vulnérabilités, analyse de menaces, reporting) ;
- **Intégration avec des bases de données de threat intelligence**.

### Liste des outils (et leur rôle)
| Outil | Rôle |
|---|---|
| **ShellGPT** | Outil en ligne de commande : navigation dans des systèmes complexes, complétion de commandes, écriture de snippets de code sécurisés, création de commentaires/documentation, réponse aux questions dans le terminal |
| **AutoGPT** | Automatisation de l'exécution de tâches et du traitement des données |
| **WormGPT** | Génération automatisée de scripts et payloads de type ver |
| **ChatGPT avec prompt DAN** | Version personnalisée de ChatGPT utilisant le prompt « Do Anything Now » pour plus de flexibilité |
| **FreedomGPT** | Accès sans restriction à l'IA, contournement des filtres de contenu |
| **FraudGPT** | Détection et prévention des activités frauduleuses |
| **ChaosGPT** | Simulation et compréhension des comportements chaotiques |
| **PoisonGPT** | Introduction de modèles malveillants dans des systèmes IA de confiance (étude des implications) |
| **HackerGPT** | Assistance en temps réel et automatisation de tâches complexes pour identifier les vulnérabilités |
| **BurpGPT** | Intégration avec Burp Suite pour améliorer la précision de détection des vulnérabilités et réduire les faux positifs |
| **BugBountyGPT** | Pour les chasseurs de bugs : détection automatisée et intégration avec les plateformes de bug bounty |
| **PentestGPT** | Assistance aux pentesters : automatisation des évaluations de vulnérabilité et génération de rapports |
| **GPT White Hack** | Évaluation des risques et détection de menaces avec recommandations en temps réel |
| **CybGPT** | Outil complet de cybersécurité : intégration de la threat intelligence, automatisation des évaluations, réponse aux incidents pilotée par l'IA |
| **BugHunterGPT** | Identification et reporting de bugs/vulnérabilités avec analyses et recommandations IA |
| **Hacking APIs GPT** | Identification des vulnérabilités d'API et automatisation du scan |
| **h4ckGPT** | Outil polyvalent : assistance en temps réel, identification automatisée des vulnérabilités |
| **HackerNewsGPT** | Actualités et mises à jour en temps réel sur la cybersécurité |
| **Ethical Hacker GPT** | Évaluations de vulnérabilité, assistance de hacking en temps réel, reporting complet |
| **GP(en)T(ester)** | Automatisation des workflows de red teaming, identification des vulnérabilités, rapports détaillés |

---

# 6. Les méthodologies et frameworks de hacking

Comprendre les méthodologies et frameworks aide les éthiques hackers à comprendre les **phases** des tentatives de hacking ainsi que les **TTP** des vrais hackers, pour renforcer la sécurité.

## 6.1 Le framework CEH (CEH Ethical Hacking Framework)

Le framework CEH d'EC-Council définit le **processus pas à pas** pour réaliser du hacking éthique. Il suit le **même processus qu'un attaquant** — seules les **finalités et stratégies** diffèrent.

### Les 5 phases

#### Phase 1 : Reconnaissance (footprinting)
Phase préparatoire : l'attaquant collecte le **maximum d'informations** sur la cible avant d'attaquer : plage d'adresses IP, namespace, employés.

- **Reconnaissance passive** : pas d'interaction directe avec la cible — informations publiques, communiqués de presse, méthodes sans contact.
- **Reconnaissance active** : interaction directe — détection des ports ouverts, hôtes accessibles, localisation des routeurs, cartographie réseau, détails des OS et applications.
- **Scanning** : identification des hôtes actifs, ports ouverts et services inutiles activés.
- **Énumération** : connexions actives et requêtes directes — listes d'utilisateurs réseau, tables de routage, failles de sécurité, utilisateurs/groupes partagés, applications, bannières.

#### Phase 2 : Scan de vulnérabilités
Évaluation de la capacité d'un système/application à **résister à une attaque**, y compris ses procédures et contrôles de sécurité actuels. L'attaquant identifie, mesure et classe les vulnérabilités pour les exploiter ensuite.

#### Phase 3 : Gaining Access (obtention d'accès)
L'attaquant obtient l'accès à l'**OS ou aux applications** d'un ordinateur ou réseau. Les chances dépendent de l'architecture/configuration du système, du niveau de compétence de l'attaquant et du niveau d'accès initial obtenu.

- **Escalade de privilèges** : après un accès avec un compte à faibles privilèges, l'attaquant tente de passer au niveau **administrateur** pour effectuer des opérations protégées.

#### Phase 4 : Maintaining Access (maintien d'accès)
L'attaquant tente de **conserver la possession** du système. Avec des privilèges admin/root, il peut :
- utiliser le système comme **tremplin** pour scanner/exploiter d'autres systèmes ;
- téléverser/télécharger/manipuler des données, applications et configurations ;
- transférer des identifiants et autres informations via des logiciels malveillants ;
- maintenir le contrôle longtemps en **fermant les vulnérabilités** pour empêcher d'autres hackers de les exploiter.

#### Phase 5 : Clearing Tracks (effacement des traces)
Pour rester indétecté, l'attaquant **modifie ou supprime les logs** du système à l'aide d'utilitaires de nettoyage, supprimant toute preuve de sa présence.

**Outils cités dans le framework** : Nmap, Wireshark, Burp Suite, Metasploit, SET (Social Engineering Toolkit).

**Domaines couverts** : hacking système, web, réseau, mobile, sans fil, OT/IoT, cloud, IA ; mots de passe, malware, ingénierie sociale, brute force, DoS/DDoS, SQL injection, sniffing, session hijacking, cryptanalyse.

## 6.2 La Cyber Kill Chain (Lockheed Martin)

La **Cyber Kill Chain** est un composant de la **défense pilotée par le renseignement** pour l'identification et la prévention des intrusions malveillantes. Basée sur le concept militaire de « chaîne d'anéantissement », elle comporte **7 phases**.

### Les 7 phases

1. **Reconnaissance** — collecter un maximum d'informations sur la cible : recherche sur Internet, ingénierie sociale, réseaux sociaux, sites web visités, monitoring du site de l'organisation, **Whois**, **DNS**, **footprinting réseau**, scan des ports/services.
2. **Weaponization (armement)** — analyser les données collectées, choisir/créer un **payload malveillant sur mesure** (arme d'accès à distance = exploit + backdoor) ; créer une campagne de phishing ; exploiter des kits d'exploit et botnets.
3. **Delivery (livraison)** — transmettre le payload à la victime : **email de phishing**, lien malveillant, application web vulnérable, **clé USB**, attaques **watering hole**.
4. **Exploitation** — déclencher le code malveillant pour exploiter une vulnérabilité de l'OS, de l'application ou du serveur : attaques d'authentification/authorisation, exécution de code arbitraire, menaces physiques, mauvaise configuration.
5. **Installation** — télécharger et installer plus de logiciels malveillants (backdoors) pour **maintenir l'accès** à long terme ; techniques de dissimulation (chiffrement) ; propagation aux autres systèmes.
6. **Command and Control (C2)** — créer un **canal de communication bidirectionnel** entre le système victime et le serveur contrôlé par l'adversaire (via trafic web, email, DNS) ; souvent chiffré ; escalation de privilèges.
7. **Actions on Objectives (actions sur les objectifs)** — accomplir les buts : accès aux données confidentielles, perturbation des services, destruction de la capacité opérationnelle, point de départ d'autres attaques.

### L'analyse des TTP dans la pratique

- **Tactiques** : décrivent comment l'acteur de menace opère durant les différentes phases (collecte d'infos, exploitation initiale, escalation, mouvement latéral, persistance). Profiler les acteurs selon leurs tactiques aide à les identifier.
- **Techniques** : les outils et méthodes pour obtenir des résultats intermédiaires (au début : outils de collecte d'infos, ingénierie sociale ; au milieu : exploits, mauvaise configuration ; à la fin : chiffrement, exfiltration, nettoyage de logs).
- **Procédures** : séquences d'actions pour exécuter les étapes du cycle de vie d'une attaque. Un acteur avancé utilise des procédures plus complexes (plus d'actions) pour augmenter le taux de succès et réduire la détection.

### Adversary Behavioral Identification (identification des comportements adverses)

Comportements à surveiller pour renforcer la détection :
- **Reconnaissance interne** — énumération de systèmes/hôtes/processus, commandes inhabituelles (scripts Batch, PowerShell), capture de paquets ;
- **Usage de PowerShell** — vérifier les logs de transcript et les Windows Event Logs ;
- **Activités de proxy indéterminées** — domaines multiples pointant vers le même hôte, changements rapides de domaines ;
- **Usage de la ligne de commande (CLI)** — création de comptes, téléchargement de code malveillant ;
- **HTTP User Agent modifié** — contenu inhabituel du champ user agent ;
- **Serveurs Command and Control** — sessions chiffrées vers l'extérieur, ports ouverts inhabituels ;
- **DNS tunneling** — obfuscation du trafic malveillant dans le trafic DNS légitime ;
- **Web shells** — coquilles dans les sites web pour un accès distant au serveur ;
- **Data staging** — collecte/combinaison de données sensibles avant exfiltration ou destruction.

### Indicators of Compromise (IoC)

> Les **IoC** sont les indices, artefacts et données forensiques trouvés sur un réseau ou un OS indiquant une **intrusion potentielle** ou une activité malveillante.

- Les IoC ne sont pas de l'intelligence, mais des **points de données** dans le processus de renseignement. Les standards **STIX** et **TAXII** permettent de partager ces rapports standardisés.
- **Types d'IoC** : **atomiques** (indivisibles — adresse IP, email), **calculés** (extraits des données d'un incident — hashs, expressions régulières), **comportementaux** (regroupement d'atomiques et calculés selon une logique).
- **4 catégories** :
  - **Email** : adresse de l'expéditeur, sujet, pièces jointes/liens ;
  - **Réseau** : URLs, noms de domaine, adresses IP ;
  - **Host-based** : noms de fichiers, hashs de fichiers, clés de registre, DLLs, mutex ;
  - **Comportementaux** : exécution de scripts PowerShell, exécution de commandes à distance.
- **Exemples d'IoC clés** : trafic sortant inhabituel, activité inhabituelle d'un compte privilégié, anomalies géographiques, échecs de connexion multiples, augmentation du volume de lecture de la base de données, grande taille de réponse HTML, requêtes multiples pour le même fichier, trafic port-application incompatible, modifications suspectes du registre/fichiers système, requêtes DNS inhabituelles, patchage inattendu des systèmes, signes d'activité DDoS, paquets de données aux mauvais endroits, trafic web « comportement surhumain ».

## 6.3 Le framework MITRE ATT&CK

> **MITRE ATT&CK** est une **base de connaissances** mondialement accessible des **tactiques et techniques adverses**, basée sur des **observations du monde réel**.

Elle sert de fondation au développement de modèles de menaces et de méthodologies dans le secteur privé, le gouvernement et la communauté des produits/services de cybersécurité.

### Les 3 matrices
- **Enterprise** : 14 catégories de tactiques, dérivées des **stades avancés** (exploit, control, maintain, execute) des 7 stades de la Cyber Kill Chain ;
- **Mobile** ;
- **PRE-ATT&CK** : phases amont (reconnaissance, weaponization, delivery).

### Les 14 tactiques ATT&CK Enterprise
1. **Reconnaissance**
2. **Resource Development** (développement de ressources)
3. **Initial Access** (accès initial)
4. **Execution** (exécution)
5. **Persistence** (persistance)
6. **Privilege Escalation** (escalade de privilèges)
7. **Defense Evasion** (évasion de la défense)
8. **Credential Access** (accès aux identifiants)
9. **Discovery** (découverte)
10. **Lateral Movement** (mouvement latéral)
11. **Collection**
12. **Command and Control** (C2)
13. **Exfiltration**
14. **Impact**

### Cas d'usage d'ATT&CK Enterprise
- Prioriser les efforts de développement/acquisition de capacités de défense ;
- Réaliser des analyses d'alternatives entre capacités de défense ;
- Déterminer la « couverture » d'un ensemble de capacités de défense ;
- Décrire une chaîne d'événements d'intrusion de bout en bout avec une référence commune ;
- Identifier les similitudes et caractéristiques distinctives entre les tactiques adverses ;
- Connecter mitigations, faiblesses et adversaires.

## 6.4 Le Diamond Model of Intrusion Analysis

Le **Diamond Model** offre un framework et des procédures pour reconnaître les **clusters d'événements corrélés** sur les systèmes d'une organisation. L'élément atomique vital de toute intrusion est appelé **« Diamond Event »** (événement diamant).

### Les 4 caractéristiques de base

| Caractéristique | Rôle | Question |
|---|---|---|
| **Adversaire** | L'opposant derrière l'attaque | **Qui** ? |
| **Victime** | La cible exploitée | **Où** ? |
| **Capacité** | Stratégies, méthodes, procédures, outils, malware | **Comment** ? |
| **Infrastructure** | Matériel/logiciel utilisés pour atteindre la victime | **Quoi** ? |

Le modèle est nommé « diamant » car, disposées selon leurs relations, les caractéristiques forment une structure en forme de losange.

### Les méta-caractéristiques additionnelles
- **Timestamp** : date/heure de l'événement (début/fin, périodicité) ;
- **Phase** : progression de l'attaque (phases du kill chain) ;
- **Result** : résultat — succès, échec, inconnu ; ou CIA compromis ;
- **Direction** : sens de l'attaque (victime→infrastructure, adversaire→infrastructure, infra→infra, bidirectionnel) ;
- **Methodology** : technique utilisée (spear-phishing, DDoS, drive-by-compromise…) ;
- **Resource** : ressources externes (matériel, logiciel, accès, connaissance, données).

### Le modèle étendu
- **Méta-caractéristique socio-politique** : relation adversaire ↔ victime, motivation (gain financier, espionnage d'entreprise, hacktivisme) ;
- **Méta-caractéristique technologique** : relation infrastructure ↔ capacité, technologie de communication/opération.

---

# 7. Les contrôles de sécurité de l'information

Les **contrôles de sécurité** préviennent la survenue d'événements indésirables et réduisent le risque sur les actifs d'information. Concepts fondamentaux : la triade CIA (confidentialité, intégrité, disponibilité) pour l'information, et l'authentification/authorisation/non-répudiation pour les personnes.

## 7.1 Information Assurance (IA)

> L'**IA** est la garantie que l'intégrité, la disponibilité, la confidentialité et l'authenticité de l'information et des systèmes d'information sont protégées pendant l'**usage**, le **traitement**, le **stockage** et la **transmission**.

Elle s'appuie sur des contrôles **physiques**, **techniques** et **administratifs**.

**Processus clés de l'IA :**
- Développer des politiques, processus et directives locales ;
- Concevoir des stratégies de réseau sécurisé et d'authentification des utilisateurs ;
- Identifier les vulnérabilités et menaces réseau ;
- Identifier les problèmes et besoins en ressources ;
- Créer des plans pour les besoins de ressources identifiés ;
- Appliquer les contrôles d'IA appropriés ;
- Effectuer la **certification et l'accréditation (C&A)** des systèmes ;
- Fournir une **formation à l'assurance de l'information**.

## 7.2 La stratégie de sécurité continuelle/adaptative

Les organisations doivent adopter une stratégie de sécurité adaptative combinant **4 approches** :

1. **Prédire** : évaluation des risques et des vulnérabilités, analyse de la surface d'attaque, consommation de threat intelligence.
2. **Protéger** : stratégie de défense en profondeur — protection des endpoints, du réseau et des données (mesures administratives, techniques, physiques).
3. **Détecter** : surveillance continue des menaces, monitoring régulier du trafic réseau.
4. **Répondre** : réponse aux incidents, investigation, confinement, mitigation de l'impact, éradication.

## 7.3 La défense en profondeur

> La **défense en profondeur** est une stratégie de sécurité où **plusieurs couches de protection** sont placées tout au long d'un système d'information.

- Principe militaire : il est plus difficile de vaincre une défense complexe et multicouche qu'une seule barrière.
- Une brèche dans une couche ne fait qu'**amener l'attaquant à la couche suivante**.
- Couches typiques : **physique**, **hôte**, **données** (+ périmètre réseau, application).
- Minimise l'impact d'un accès et donne aux administrateurs le temps de déployer des contre-mesures.

## 7.4 Le risque et la gestion des risques

### Qu'est-ce que le risque ?

> Le **risque** est le degré d'incertitude ou l'attente qu'un événement indésirable puisse **causer des dommages** au système ou à ses ressources.

**Formules clés :**
- **RISQUE = Menaces × Vulnérabilités × Impact**
- **RISQUE = Menace × Vulnérabilité × Valeur de l'actif**
- **Niveau de risque = Conséquence × Vraisemblance**

Le risque combine la **probabilité d'occurrence** d'un événement indésirable et sa **conséquence**.

### Les niveaux de risque et la matrice de risque
- 4 niveaux : **extrême**, **élevé**, **moyen**, **faible**.
- La **matrice de risque** représente visuellement la probabilité et les conséquences (impact) pour comparer les risques.

| Risque | Action |
|---|---|
| **Extrême ou très élevé** | Des mesures **immédiates** doivent être prises pour combattre le risque |
| **Élevé** | Identifier et imposer des contrôles pour réduire le risque à un niveau raisonnablement bas |
| **Moyen** | Mettre en œuvre des contrôles **dès que possible** pour réduire le risque |
| **Faible** | Prendre des mesures préventives pour atténuer les effets du risque |

### Les phases de la gestion des risques
1. **Identification du risque** : identifier les sources, causes, conséquences des risques internes/externes ;
2. **Évaluation du risque** : estimer la vraisemblance et l'impact ; processus itératif qui définit les priorités de mitigation ;
3. **Traitement du risque** : sélectionner et mettre en œuvre des contrôles appropriés (méthode, responsables, coûts, bénéfices, probabilité de succès, mesures d'évaluation) ;
4. **Suivi et revue du risque** : s'assurer que les contrôles sont implémentés, calculer les chances de nouveaux risques, évaluer la performance des stratégies.

## 7.5 Cyber Threat Intelligence (CTI)

> La **CTI** est la **collecte et l'analyse d'informations** sur les menaces et adversaires, et l'établissement de schémas permettant de prendre des **décisions éclairées** pour la préparation, la prévention et la réponse aux cyberattaques.

L'objectif : transformer les **menaces inconnues** en **menaces connues** pour anticiper les attaques et construire une posture de cybersécurité **proactive**.

### Les 4 types de threat intelligence

| Type | Contenu | Consommateurs | Horizon |
|---|---|---|---|
| **Stratégique** | Informations de haut niveau : posture de cybersécurité, impact financier des cyberactivités, tendances d'attaques, attribution, paysage des menaces | Direction, CISO, management | Long terme |
| **Tactique** | **TTPs** des acteurs de menace, campagnes, malware, rapports forensiques | Managers IT/SOC, NOC, administrateurs, architectes | Moyen terme |
| **Opérationnelle** | **Menaces spécifiques** contre l'organisation, contexte des événements/incidents, investigations | Gestionnaires de sécurité, défenseurs réseau, forensique, anti-fraude | Court terme |
| **Technique** | **IoC spécifiques** : IP, domaines, hashs de malware, en-têtes de phishing | Personnel SOC, équipes IR | Très court terme |

### Le cycle de vie de la threat intelligence (5 phases)
1. **Planification et direction** : définir les exigences de renseignement, former l'équipe, faire un plan de collecte ;
2. **Collecte** : collecter les données (HUMINT, IMINT, MASINT, SIGINT, OSINT, IoC, tierces parties) ;
3. **Traitement et exploitation** : transformer les données brutes en informations exploitables (structuration, décryptage, traduction, parsing, réduction, filtrage, corrélation, agrégation) ;
4. **Analyse et production** : combiner les sources en une entité unique, inclure faits, constats et prévisions ; l'analyse doit être **objective, opportune, précise et actionnable** ;
5. **Dissémination et intégration** : distribuer aux consommateurs (stratégique, opérationnel, tactique, technique) et recueillir le **feedback**.

## 7.6 La modélisation des menaces (Threat Modeling)

> Le **threat modeling** est une approche d'évaluation des risques pour analyser la sécurité d'une application en **capturant, organisant et analysant** toutes les informations qui affectent sa sécurité.

Trois blocs fondamentaux : comprendre la perspective de l'adversaire, caractériser la sécurité du système, déterminer les menaces.

### Les 5 étapes du processus
1. **Identifier les objectifs de sécurité** (CIA) — quelles données protéger ? Exigences de conformité ? QoS ? Actifs immatériels ?
2. **Vue d'ensemble de l'application** — composants, flux de données, limites de confiance ; identification des rôles, scénarios d'usage clés, technologies (OS, serveur web, base de données, langages) et mécanismes de sécurité (validation des entrées, authentification/authorisation, données sensibles, gestion de configuration, gestion de session, manipulation de paramètres, cryptographie, gestion des exceptions, audit/logging).
3. **Décomposer l'application** — limites de confiance, flux de données, **points d'entrée** et **points de sortie**.
4. **Identifier les menaces** — via une approche par questions, en regroupant les menaces par catégorie de vulnérabilité applicative.
5. **Identifier les vulnérabilités** — faiblesses liées aux menaces trouvées, à corriger avant l'exploitation.

## 7.7 La gestion des incidents

> La **gestion des incidents** est un ensemble de processus définis pour **identifier, analyser, prioriser et résoudre** les incidents de sécurité afin de **restaurer les opérations normales** le plus rapidement possible et de **prévenir la récurrence**.

**Inclus** : analyse de vulnérabilité, analyse d'artefacts, formation à la sensibilisation à la sécurité, détection d'intrusion, surveillance publique/technologique.

**Objectifs** : améliorer la qualité de service, résoudre les problèmes de manière proactive, réduire l'impact des incidents, respecter les exigences de disponibilité, augmenter l'efficacité du personnel, améliorer la satisfaction, aider à gérer les futurs incidents.

### Incident Handling & Response (IH&R) — les 9 étapes

| Étape | Description |
|---|---|
| 1. **Préparation** | Audit des ressources/actifs, définition des règles/politiques/procédures, constitution et formation de l'équipe, rassemblement des outils, formation des employés |
| 2. **Enregistrement et assignation** | Rapport et enregistrement initiaux de l'incident, plans de communication, tickets |
| 3. **Triage** | Analyse, validation, catégorisation et priorisation ; détails de l'attaque (type, gravité, cible, impact, méthode de propagation, vulnérabilités exploitées) |
| 4. **Notification** | Information des parties prenantes (management, fournisseurs tiers, clients) |
| 5. **Confinement (containment)** | Empêcher la propagation de l'infection et les dommages supplémentaires |
| 6. **Collecte de preuves et analyse forensique** | Rassembler toutes les preuves, analyse forensique (méthode d'attaque, vulnérabilités exploitées, mécanismes de sécurité contournés, équipements infectés, applications compromises) |
| 7. **Éradication** | Supprimer la cause racine, fermer tous les vecteurs d'attaque |
| 8. **Récupération (recovery)** | Restaurer les systèmes, services, ressources et données affectés |
| 9. **Activités post-incident** | Documentation, clôture de l'investigation, évaluation de l'impact, divulgation, revue/révision des politiques |

## 7.8 Le rôle de l'IA et du ML en cybersécurité

### Les deux types de machine learning
- **Apprentissage supervisé** : algorithmes entraînés sur des **données étiquetées** pour apprendre les différences entre étiquettes → sous-catégories : **classification** (classes discrètes) et **régression** (données continues).
- **Apprentissage non supervisé** : algorithmes sur des **données non étiquetées** pour déduire les catégories par eux-mêmes → sous-catégories : **clustering** (regroupement par similarités) et **réduction de dimensionnalité**.

### Les 10 façons dont l'IA/ML préviennent les cyberattaques
1. **Protection des mots de passe et authentification** — amélioration de la biométrie et de la reconnaissance faciale ;
2. **Détection et prévention du phishing** — différenciation des sites web malveillants/légitimes ;
3. **Détection de menaces** — analyse logique des données, notification constante des menaces imminentes ;
4. **Gestion des vulnérabilités** — scan dynamique de toutes les vulnérabilités, prévision de l'exploitation ;
5. **Analyse comportementale** — détection des déviations par rapport aux schémas d'usage réguliers d'un utilisateur ;
6. **Sécurité réseau** — analyse du trafic, génération de politiques de sécurité ;
7. **Antivirus basé sur l'IA** — détection d'anomalies de comportement au lieu de signatures virales ;
8. **Détection de fraude** — détection d'anomalies dans les transactions ;
9. **Détection de botnets** — alertes sur le comportement suspect du réseau, détection d'intrusions non autorisées ;
10. **L'IA pour combattre les menaces IA** — détection des attaques augmentées par l'IA avant compromission.

---

# 8. Les lois et standards de la sécurité de l'information

> Une **loi** est un système de règles et directives appliqué par un pays ou une communauté. Un **standard** est un document établi par consensus et approuvé par un organisme reconnu, fournissant des règles, directives ou caractéristiques pour des activités ou leurs résultats.

## 8.1 PCI DSS (Payment Card Industry Data Security Standard)

**Standard de sécurité** pour les organisations qui traitent des **données de titulaires de cartes** (débit, crédit, prépayé, e-purse, ATM, POS). S'applique à tous : commerçants, processeurs, acquéreurs, émetteurs et prestataires de services.

**Les 6 objectifs de haut niveau :**
1. **Construire et maintenir un réseau sécurisé** — installer/maintenir une configuration de pare-feu protégeant les données des titulaires ; ne pas utiliser les paramètres par défaut du fournisseur pour les mots de passe système.
2. **Protéger les données des titulaires** — protéger les données stockées ; chiffrer la transmission sur les réseaux publics ouverts.
3. **Maintenir un programme de gestion des vulnérabilités** — utiliser/mettre à jour régulièrement un antivirus ; développer et maintenir des systèmes/applications sécurisés.
4. **Mettre en œuvre des mesures de contrôle d'accès strictes** — restreindre l'accès « need-to-know » ; attribuer un ID unique à chaque personne ; restreindre l'accès physique.
5. **Surveiller et tester régulièrement les réseaux** — suivre/monitorer tous les accès ; tester régulièrement les systèmes et processus.
6. **Maintenir une politique de sécurité de l'information** — pour tout le personnel.

**Conséquences** : amendes ou **perte du droit de traiter les paiements par carte**.

## 8.2 Les normes ISO/IEC

| Norme | Rôle / Description |
|---|---|
| **ISO/IEC 27001:2022** | **SMSS** (Système de Management de la Sécurité de l'Information) : exigences et cadre pour établir, mettre en œuvre, maintenir et améliorer un ISMS. Objectifs : approche structurée des risques, conformité réglementaire, renforcement de la posture, amélioration continue, confiance des parties prenantes, avantage concurrentiel, soutien à la digitalisation, travail à distance/BYOD, Industrie 4.0 et cloud, communication des rôles/responsabilités |
| **ISO/IEC 27701:2019** | **Extension de 27001** pour la gestion de la vie privée, protection des **PII** (données personnelles), implémentation d'un **PIMS** (Privacy Information Management System) |
| **ISO/IEC 27002:2022** | **Bonnes pratiques et objectifs de contrôle** pour les domaines critiques : contrôle d'accès, cryptographie, personnel de sécurité |
| **ISO/IEC 27005:2022** | Lignes directrices pour la **gestion des risques** de sécurité de l'information (appui à l'ISO 27001) |
| **ISO/IEC 27018:2019** | Code de pratique pour la protection des **PII dans le cloud public** |
| **ISO/IEC 27032:2023** | Vue d'ensemble des relations Internet/Web/sécurité réseau/cybersécurité, identification des parties prenantes |
| **ISO/IEC 27033-7:2023** | Lignes directrices pour la **sécurité de la virtualisation réseau** |
| **ISO/IEC 27036-3:2023** | Sécurisation des **chaînes d'approvisionnement** (matériel, logiciel, services) |
| **ISO/IEC 27040:2024** | **Sécurité du stockage de données** : exigences techniques et guide (planification, conception, documentation, implémentation) |

## 8.3 HIPAA (USA — santé)

La **HIPAA** (Health Insurance Portability and Accountability Act) protège les **informations de santé personnellement identifiables**. Ses règles d'« Administrative Simplification » :

- **Electronic Transactions and Code Set Standards** : normes uniformes pour les transactions électroniques de soins de santé (EDI) ;
- **Privacy Rule** : protections fédérales pour les informations de santé personnelles ; droits des patients (examiner, obtenir une copie, demander des corrections) ;
- **Security Rule** : sauvegardes **administratives, physiques et techniques** pour assurer la confidentialité, l'intégrité et la disponibilité de l'**e-PHI** (informations de santé électroniques protégées) ;
- **National Identifier Requirements** : le **NPI** (National Provider Identifier) — identifiant numérique unique de 10 chiffres pour les prestataires ;
- **Enforcement Rule** : application des règles, pénalités civiles.

## 8.4 Sarbanes-Oxley Act (SOX — USA, 2002)

Adopté en 2002, le **SOX** vise à protéger le public et les investisseurs en renforçant la **responsabilité d'entreprise**, les **divulgations financières** et la lutte contre la **fraude comptable et d'entreprise**. Organisé en **11 titres** :

| Titre | Contenu |
|---|---|
| I | **PCAOB** : conseil de surveillance des cabinets d'audit (enregistrement, inspection, application) |
| II | **Indépendance des auditeurs** : limites des conflits d'intérêt (pas de services de conseil pour les mêmes clients) |
| III | **Responsabilité d'entreprise** : les dirigeants sont individuellement responsables de l'exactitude des rapports financiers |
| IV | **Divulgations financières renforcées** : transactions hors bilan, contrôles internes, audits, reporting des changements matériels |
| V | **Conflits d'intérêt des analystes** : code de conduite des analystes de valeurs mobilières |
| VI | **Ressources et autorité de la Commission** : autorité de la SEC de censurer/radier des professionnels |
| VII | **Études et rapports** : études du Contrôleur général et de la SEC |
| VIII | **Responsabilité en cas de fraude corporative et criminelle** : peines pour manipulation/destruction de dossiers, protection des lanceurs d'alerte |
| IX | **Majoration des peines pour crimes en col blanc** : pénalités renforcées, défaut de certification pénalisé |
| X | **Déclarations fiscales d'entreprise** : le PDG signe la déclaration de revenus de la société |
| XI | **Responsabilité en cas de fraude d'entreprise** : fraude d'entreprise et falsification de dossiers = infractions pénales ; gel de transactions « importantes/inhabituelles » |

## 8.5 DMCA (Digital Millennium Copyright Act — USA)

Loi américaine sur le droit d'auteur implémentant deux traités **WIPO** de 1996 (Copyright Treaty et Performances and Phonograms Treaty). Interdit la **circonvention des mesures techniques de protection** et l'altération des informations de gestion des droits d'auteur. **5 titres :**

- **Titre I** : implémentation des traités WIPO (nouvelles interdictions de circonvention) ;
- **Titre II** : limitation de la responsabilité des FAI pour contrefaçon en ligne (communications transitoires, caching système, stockage dirigé par l'utilisateur, outils de localisation d'informations) ;
- **Titre III** : maintenance/réparation d'ordinateurs (copies autorisées) ;
- **Titre IV** : dispositions diverses (autorité du Copyright Office, enregistrements éphémères, éducation à distance, bibliothèques/archives, webcasting, paiements résiduels) ;
- **Titre V** : Vessel Hull Design Protection Act (protection de designs d'origine).

## 8.6 FISMA (Federal Information Security Management Act — USA, 2002)

Fournit un **cadre complet** pour assurer l'efficacité des contrôles de sécurité sur les ressources fédérales :
- Standards de **catégorisation** des informations et systèmes par impact de mission ;
- Standards d'**exigences minimales de sécurité** ;
- Guide de **sélection des contrôles** de sécurité ;
- Guide d'**évaluation des contrôles** et de détermination de leur efficacité ;
- Guide pour l'**autorisation de sécurité** des systèmes.

## 8.7 GDPR (Règlement Général sur la Protection des Données — UE)

En vigueur le **25 mai 2018**. L'une des lois de protection des données les plus strictes au monde ; s'applique à toute organisation qui **cible ou collecte des données de personnes dans l'UE**. Amendes pouvant atteindre **des dizaines de millions d'euros**.

**Les 7 principes de protection des données (Article 5) :**
1. **Licéité, loyauté et transparence** : traitement licite, loyal et transparent pour la personne concernée ;
2. **Limitation des finalités** : les données ne sont traitées que pour des finalités spécifiées explicitement ;
3. **Minimisation des données** : ne collecter que les données nécessaires ;
4. **Exactitude** : données exactes et à jour ;
5. **Limitation de la conservation** : conservation uniquement le temps nécessaire ;
6. **Intégrité et confidentialité** : sécurité appropriée (ex. chiffrement) ;
7. **Responsabilité (accountability)** : le responsable du traitement doit démontrer sa conformité.

## 8.8 Data Protection Act 2018 (DPA — Royaume-Uni)

Cadre de la protection des données au Royaume-Uni. **Remplace le DPA 1998**, en vigueur le **25 mai 2018**, modifié le **1er janvier 2021** pour refléter la sortie de l'UE. Protège les personnes dans le **traitement de leurs données personnelles** en exigeant un traitement **licite et loyal** (consentement ou autre base légale), en conférant des **droits** aux personnes concernées (information, rectification) et en conférant des **fonctions à l'Information Commissioner** (surveillance et application).

## 8.9 Les cyberlois dans différents pays

> Le **cyberdroit** (ou droit de l'Internet) couvre l'accès et l'usage d'Internet, la vie privée, la liberté d'expression et la juridiction. Il varie selon les pays ; les violations entraînent des peines allant d'amendes à l'emprisonnement.

### États-Unis
- Copyright Law (Section 107 — « fair use ») ; Online Copyright Infringement Liability Limitation Act ;
- Lanham (Trademark) Act (15 USC §§ 1051-1127) ;
- Electronic Communications Privacy Act ; Foreign Intelligence Surveillance Act ; Protect America Act 2007 ;
- Privacy Act 1974 ; Computer Security Act 1987 ; **National Information Infrastructure Protection Act of 1996** ; Freedom of Information Act (FOIA) ;
- **Computer Fraud and Abuse Act (CFAA)** ; Identity Theft and Assumption Deterrence Act ;
- **CCPA** (California Consumer Privacy Act) ; **CPRA** (California Privacy Rights Act 2020).

### Royaume-Uni
- **Computer Misuse Act 1990** ; Communications Act 2003 ;
- Regulation of Investigatory Powers Act 2000 ; Investigatory Powers Act 2016 ;
- Network and Information Systems Regulations 2018 ;
- The Privacy and Electronic Communications (EC Directive) Regulations 2003 ;
- Trademarks Act 1994 ; Copyright, Etc. and Trademarks (Offenses and Enforcement) Act 2002.

### Australie
- **Cybercrime Act 2001** ; Copyright Act 1968 ; Trademarks Act 1995 ; Patents Act 1990.

### Inde
- **Information Technology Act** ; Copyright Act 1957 ; Patents (Amendment) Act 1999 ; Trade Marks Act 1999.

### Allemagne
- § 202a Espionnage de données ; § 303a Altération de données ; § 303b Sabotage informatique.

### Autres pays
- **Italie** : Code pénal article 615 ter ; **Japon** : Trademark Law (Law No. 127 de 1959) ;
- **Canada** : Copyright Act, Trademarks Act, Criminal Code § 342.1, **PIPEDA** ;
- **Singapour** : Computer Misuse Act ; **Afrique du Sud** : Copyright Act 1978, Trademarks Act 194 de 1993 ;
- **Corée du Sud** : Copyright Act (amendé 2023), Industrial Design Protection Act ;
- **Belgique** : Copyright Law 1994, Computer Hacking ; **Brésil** : **LGPD** ;
- **Hong Kong** : Article 139 de la Basic Law ; **Philippines** : Republic Act No. 10175 ;
- **Chine** : Copyright Law et Trademark Law de la RPC.

---

# 9. Aide-mémoire final pour l'examen

## Les formules à connaître absolument
| Formule | Signification |
|---|---|
| **Attaque = Motif + Méthode (TTP) + Vulnérabilité** | Les 3 composantes de toute attaque |
| **Risque = Menace × Vulnérabilité × Impact** | Modélisation du risque IT |
| **Niveau de risque = Conséquence × Vraisemblance** | Calcul du niveau de risque |

## Les listes à retenir

**5 piliers de la sécurité** : Confidentialité, Intégrité, Disponibilité, Authenticité, Non-répudiation.

**5 catégories d'attaques (IATF)** : Passives, Actives, Close-in, Insider, Distribution.

**5 phases du framework CEH** : Reconnaissance → Scan de vulnérabilités → Gaining Access → Maintaining Access → Clearing Tracks.

**7 phases de la Cyber Kill Chain** : Reconnaissance → Weaponization → Delivery → Exploitation → Installation → Command & Control → Actions on Objectives.

**14 tactiques MITRE ATT&CK Enterprise** : Reconnaissance, Resource Development, Initial Access, Execution, Persistence, Privilege Escalation, Defense Evasion, Credential Access, Discovery, Lateral Movement, Collection, Command and Control, Exfiltration, Impact.

**4 caractéristiques du Diamond Model** : Adversaire, Victime, Capacité, Infrastructure (+ méta-caractéristiques : timestamp, phase, résultat, direction, méthodologie, ressources).

**4 types de threat intelligence** : Stratégique (direction), Tactique (TTPs), Opérationnelle (menaces spécifiques), Technique (IoC).

**5 phases du cycle de vie CTI** : Planification → Collecte → Traitement → Analyse → Dissémination.

**9 étapes de l'IH&R** : Préparation → Enregistrement → Triage → Notification → Confinement → Preuves/Forensique → Éradication → Récupération → Post-incident.

## Le mot-clé le plus important
> ✅ **Consentement / autorisation écrite (contrat + NDA)** : c'est ce qui distingue le **hacking éthique** (légal) du **hacking malveillant** (illégal).

## Les lois/standards majeurs à connaître
- **Cartes de paiement** : PCI DSS
- **Standards internationaux** : ISO 27001, 27701, 27002, 27005, 27018, 27032, 27033-7, 27036-3, 27040
- **USA** : HIPAA (santé), SOX (finance), DMCA (droit d'auteur), FISMA (fédéral), CFAA (fraude informatique), CCPA/CPRA (Californie)
- **Europe** : GDPR
- **Royaume-Uni** : DPA 2018, Computer Misuse Act 1990
- **Inde** : Information Technology Act ; **Brésil** : LGPD

---

*Document généré le 05/08/2026 à partir du contenu intégral du Module 01 « Introduction to Ethical Hacking » du cursus CEH v13 (EC-Council). Contenu extrait via OCR (RapidOCR) des 137 pages du PDF.*
