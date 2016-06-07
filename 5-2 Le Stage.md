# Présentation du stage, des missions et responsabilités confiées

(TODO: insérer ici l'offre de stage)

# La mission première: Migration et mise à jour de l'Intranet

**D**ans le cadre du stage réalisé au sein de la SGAC, il s'agissait de migrer l'intranet précédemment décrit à deux niveaux, premièrement mettre à jour le code pour un nouvel environnement d'exécution et deuxièmement, le transférer d'un serveur vieillissant à une machine plus moderne.  

## Le contexte

### Le code, l'existant et la problématique  

**L**'ensemble de l'intranet repose sur des technologies de développement et d'exécution proposées par Microsoft: les outils Visual Studio, et le runtime .NET, dans sa déclinaison WEB (dans le cas des clients légers) , ASP.NET. 
Celui-ci fut développé durant une période s'étendant de 1999 pour les plus vieilles applications à 2006. 
En examinant les différents élements constituant ledit système, On trouve donc un panel d'applications (de type client lourd et client léger) relativement hétéroclyte fonctionnant avec différentes versions du runtime .NET, de sa version 1.1 à sa version 3.5.

(TODO: insérer ici schéma fonctionnement applications .NET)

Bien que la rétrocompatibilité fut majoritairement assurée au fil des versions, il était des plus intéressant, en 2016, de convertir l'ensemble du code pour qu'il fonctionne avec une version nettement plus récente de l'environnement d'exécution de Microsoft, et ce afin de gagner en homogénéité mais aussi en performances ainsi qu'en terme de pérénité du parc applicatif. Concernant ce dernier point, il peut paraître important de préciser que les applications web furent développer pour fonctionner sur NETSCAPE (ayant totalement disparu aujourd'hui) ainsi que sur Internet Explorer 5. Il était donc relativement urgent, pour des raisons de sécurité notamment de faire évoluer le code. 

(TODO: insérer ici schéma organisation type application ASP.NET)

Cette mise à jour des sources présentera quelques problèmes, regroupables en deux grandes catégories:

* Les problèmes liés à l'évolution du runtime .NET (essentiellement relatifs à des changements liés aux options présentes dans les fichiers de configuration des applications, voir schéma organisation type application ASP.NET)
* Les problèmes liés à l'évolution des standards WEB. Etant donné que les applications furent prévues pour des navigateurs plus que vétustes et la vitesse d'évolutions des technologies de l'internet, bon nombre du code coté client (HTML, CSS et Javascript) était totalement dépassé et il fut nécessaire de reprendre bon nombre de ces élements. 

Durant cette période de trois mois, il s'agissait donc, concernant le code, de convertir les applications, de corriger les problèmes issus de cette convertion mais également de, si possible, d'améliorer l'existant. 


### Concernant le serveur 

**L**'intranet fut hébergé pendant plus de 10 ans sur un serveur virtuel fonctionnant sous Windows Server 2003 exécutant le gestionnaire de base de données SQL Server 2008 (Chronologiquement SQL Server 2000, 2005 puis 2008) ainsi qu'IIS (Internet Information Server), la solution de serveur Web de Microsoft. (TODO: trouver version). Il s'agissait donc, toujours dans le cadre de cette mise à jour importante, de transférer l'ensemble des applications sur une nouvelle machine Windows Server 2012 R2 prévue au préalable par M. Fernandez, équipée d'IIS 7 ainsi que de SQL Server 2012. Les objectifs qui me furent affectés ici sont:

* Configurer IIS 7
* Configurer SQL Server 2012
* Configurer SQL Report Server 2010
* Migrer l'ensemble des bases de données depuis l'ancien serveur vers le nouveau 
* Installer sur le nouveau serveur l'ensemble des applications d'administration planifiées (appelées tâches planifiées par la suite). 

Ces tâches, nécessaires à la réalisation de la mise à jour du code furent exécutées en priorité, et durant les premièrs jours du stage. 

## Des responsabilités certaines

**L**'ensemble des logiciels de l'intranet est indispensable au bon fonctionnement de la SGAC. En effet, ceux-ci sont utiles à tout les corps de métiers, des fonctions supports (Gestion des ressources humaines, Services généraux...) aux services au coeur de l'activité de la société d'assainissement (maintenance réseau, gestion usine de traitement etc..). Aussi, toute interruption du fonctionnement des logiciels, de quelque nature qu'elle soit (erreur de manipulation des machines, applications fortement bugguées) durant les heures de travail des salariés (8H30 - 16H30) n'est pas envisageable. Aussi, il fut nécessaire d'apporter un soin tout particulier à la fluidité de la transition afin de limiter l'impact sur les habitudes des utilisateurs, objectif atteint avec plus ou moins de succès. 

## Les outils à notre disposition

**A**fin d'atteindre nos objectifs le plus rapidement possible, tout en assurant une qualité de fonctionnement maximale, en vue de nos moyens, le choix des armes se porta sur une collection d'outils Microsoft consituée des élements suivants: 

* Deux machines virtuelles de développement Microsoft Windows Server 2012...
* ...Equipées chacune d'une version de Visual Studio 2015 édition professionelle, l'environnement de développement intégré, accès sur la conception WYSIWYG (What You See Is What You Get) et l'utilisation des langages de programmation de la multinationale (C#, VB, Visual C++).
* ...Connectées à un serveur Team Foundation Server (TFS), la plateforme de développement en équipe associée à un système de versionning lui aussi propulsé par Microsoft. 

L'installation de l'ensemble de ces outils consititua d'ailleurs la première tâche que j'eu l'occasion d'accomplir au sein de l'entreprise.

Il est à noter l'absence de documentation à proprement parler, en effet, il semblerait que le service, comme les peuplades d'Afrique Centrale, préfère une tradition orale à la rédaction de documentations. Tâche (trop ?) chronophage s'il en est, au vues des faibles ressources humaines misent à la disposition du service informatique et de la bonne qualité du code fournit. De fait, ormis les quelques commentaires présents dans le code, nous dûmes travailler en découvrant l'architecture du système logiciel au fur et à mesure de notre progression, en nous aidant des connaissances acquises par Monsieur Thierry Fernandez au cours de ses propres explorations dans le code.

## Les applications à migrer

### Description de l'objet du travail réalisé

L'intranet est dans les faits consitué de deux groupes d'applications distincts, en plus du portail. 

Nous constatons la présence, d'une part, des applications de type client léger qui permettent à la fois aux différents services d'atteindre leurxs objectifs mais une une meilleur transmission de l'information au sein de l'entreprise tout entière (ce qui permet des gains de productivité notables, tout en aidant à la prise de décision). 
Il est a noté qu'un site Web appelé Portail Intranet permet l'accès aux différentes applications, tout en en gérant le système d'authentification. 

D'autre part, il existe un certain nombre d'applications client lourds, de type logiciel windows, reposant aussi sur des élements de l'intranet tels que la base de données, ou les fonctions d'authentification du portail. Etant donné que nous faisions évoluer ces élements de base; une évolution des clients lourds s'imposa (elle était de toute manière tout aussi essentielle que la migration de l'intranet en lui-même). A noté que j'appris l'existence de telles applications a postériori de la migration, élement relativement important par la suite. 

### De l'organisation de travail 

Afin d'atteindre les objectifs définis plus haut, l'organisation de travail se fit comme suit:

Avant toute chose, l'objectif était de préparer l'environnement de développement. C'est à dire les outils à proprement parler (tels que définis plus haut), mais aussi le futur serveur intranet et son ensemble logiciel.

Dans un second temps, étant donné l'absence de documentation, il s'agissait de prendre le code en main. Cet examen pris la forme d'une observation totale et complète du code avant de procéder à la moindre manipulation et ce pour deux raisons: 

* Comprendre la logique du développeur ayant produit ces élements
* Identifier les élements pouvant poser problème durant une migration type. 

Une fois la prise en main terminée, le code de chacune des applications de type client léger (ainsi que du portail) fut deployé sur un serveur de développement (alors futur serveur de production).

Une fois ces applications testée, il s'agissait de mettre à exécution la migration, en transférant le serveur intranet sur la nouvelle machine, jusqu'alors serveur de développement.   
Etant donné l'importance relativement conséquente de ces applications, des données présentent dans les bases et du fait qu'il n'est pas possible de rendre l'intranet innacessible durant les heures de travail, un plan de migration fut mis au point. 

(TODO: insérer ici le plan de migration)

Celui-ci devait être exécuté après la débauche du jour J et avant l'embauche du lendemain (J+1). Cette migration ne fut pas des plus calmes, notamment suite à la découvertes des problématiques liées aux logiciels de type client lourds mais nous y reviendrons plus bas. 

Une fois la migration à proprement parler terminée, il devait m'être possible de me consacrer à d'autres missions, tout en continuant à assurer une correction de bug rapide et efficace basée sur la réactivité du service.

### Concernant les tests

Etant donné l'énorme quantité d'applications (et donc de fonctionnalités à tester), le manque de documentation, de moyens humains et ma méconaissance de la façon dont s'utilise les applications, les tests réalisés avant la mise en production se cantonnaient à réaliser un ensemble d'examens statiques, relatifs au code en lui-même. 

Les fonctionnalitées elle, seraient testée et les bugs corrigés en flux-tendus. C'est à dire que les applications devaient être mises en ligne tel quel, et les utilisateurs, prévenus à l'avance devaient signaler le moindre comportement anormal, qui serait immédiatement corrigé. 

## Les problèmes rencontrés et autres difficultées

### Un code ancestral 

L'élement récurrent qui posa le plus de problème tout au long de la réalisation de cette mission est évidemment la vetusté du code, ou plutôt, le grand âge des technologies sur lesquelles il repose (portail prévue pour IE 5.5 et ... Netscape 3).
En effet, à bon nombre de reprise, il fallut rechercher des équivalent aux bibliothèques de l'époque, celle-ci n'ayant pas conservé la totalité de leur fonctionnalité ou ayant tout simplement disparu. 

### La dépendance

Il est important également de souligner que, comme présenté plus haut, l'interdépendance des différents élements composant l'intranet est excessivement forte, ce qui en l'absence de documentation ou de cartographie quelconque se révèla plus que problématique tout au long de la migration. 
En effet, il arriva plusieurs fois que la moindre modification d'une application entraîne des répercussions imprévues non seulement à l'intérieur même de l'application (ce qui semble normal) mais également au sein d'autres constituantes avec lequel le lien logique n'est pas toujours clair, lorsqu'on ne maîtrise pas totalement l'articuliation des activités de la société comme se fut mon cas. 

Ces dépendances peuvent être de trois natures: 

* Les bibliothèques: bon nombre des élements applicatifs sont en fait des bibliothèques de méthodes et de classes utilisées par plusieurs projets. Modifier une bibliothèques pour un projet peut entrainer des répercussion sur une autre application qui en dépend. 
* Les données: De même, certaines applications reposent sur une même base de données. La modifier pour une application peut être source de problèmes. 
* Les Webservices: sorte d'interfaces web qui permettent à deux programmes de fonctionner eux s'echangeant des données, à la manière d'une API Web. Etant donné leur utilité même, il apparait que les modifier peut entrainer l'apparition de comportements non désirés sur les applications qui en dépendent. Ceux-ci furent problématiques non seulement parce que les déplacer casse leurs liens avec les applications clients mais aussi suite à des problèmes de version. Un WebService en .NET 4.5 n'est pas compatible avec un client en .NET 4.0 par exemple. 

### De SQL Report Server et du manque de ressources

Autre source de problème plutôt conséquent: Microsoft SQL Report Server. Ce service, fonctionnant de concert avec SQL Server, permet de créer des rapports simplement, qui rendent possible la visualisation simple des données présentes dans la base. Et ce notamment afin d'aider à la prise de décision ou simplement de constater l'état actuelle des installations et de l'entreprise. 
Bon nombre d'applications de l'intranet font appel à ce service afin de présenter les données sans avoir à coder les différentes requètes ni à construire de nouvelles interfaces. Or, suite à différents problèmes liés au mode d'authentification utilisé par SQL Report Server, et au manque de ressources disponibles sur le sujet, tant au sein du service informatique que sur Internet, ce système nous fit perdre un temps monstrueux. La compréhension de l'origine des problèmes n'ayant été comprise que bien tard, leur résolution se fit jusque là à tâton, par "hasard".

### Les clients lourds

D'autre part, et comme introduit plus haut, L'existence d'applications de type client lourds ne fut porté à ma connaissance qu'une fois la migration effective, lorsque bon nombre d'entre elles ne fonctionnèrent plus normalement. Situation qu'il fallut corriger dans une situation d'urgence relative.L'une d'entre elle, tout particulièrement, demanda une quantité de travail plus qu'importante. 
Celle-ci, sobrement nommée "Application Intranet", permet d'accéder depuis les postes utilisateurs à des informations présentes sur le site. Elle rassemble un client IPPOP (base de donnée patrimoine d'entreprise), un client Métrologie (qui fut au centre de tout les problèmes) ainsi qu'une interface présentant un ensemble de rapports (utilisant SQL Report Server précedemment présenté).

(TODO: insérer ici screenshot metro)

Outre les éternels soucis relatifs à SQL Report Server (qui furent premièrement contournés puis réellement résolus), la majeure partie des problèmes liés à cette application proviennent de son client Métrologie. 

En effet, la particularité de l'application Intranet et qu'elle propose de fonctionner en deux modes distincts, le mode connecté (qui affiche directement les données présnetes sur le site) et le mode déporté. Ce mode déporté permet, dans les faits, aux salariés de travailler sur un instantané de leur base de donnée de travail dans des zones non couvertes par le réseau de la SGAC (sur le terrain). Le coeur du problème rencontré provient du fait que la technologie usitée, SQL Server Compact 3.5 ne permet plus aujourd'hui la copie d'instantanés, il fallut donc lui trouver un remplaçant (d'abord SQL Server Compact 4.0, sans succès, puis Microsoft Sync Framework) et adapter le code. Là encore, les problématiques furent nombreuses, toutes liées au fait que les machines des techniciens utilisant l'application fonctionnent sous Windows XP, système paru en 2003. 

Constatant la vétustée des machines la décision fut prise de déployer sur les machines des utilisateurs une version temporaire, en attendant la configuration de Windows 7 sur leur machines, qui permettra de profiter de technologies plus récentes et performantes. 

Ainsi, l'application Intranet dispose aujourd'hui de deux versions, une temporaire fonctionnant sous windows XP et une plus pérenne prévue pour fonctionner sous Windows 7.   

### La problématique de l'envoi de mail

Enfin, dans le but d'illustrer les problématiques liées à l'intégration croissante, nous pouvons exposer les difficultées relatives à l'envoi de mails automatiques par le système. 
Afin de comprendre l'obstacle, il est nécessaire d'expliquer que le portail dispose d'une fonctionnalité simple mais essentielle.En effet, l'accès aux services de l'intranet est permis grâce à l'utilisation d'un login et d'un mot de passe. Or, la plupart des utilisateurs ne retiennent pas ce mot de passe (et ne le changent pas), se contentant de demander un nouveau mot de passe au besoin. Or, suite à la migration le fonctionnement normal de cette fonctionnalité fut perturbée, interdisant de fait l'accès à l'intranet à beaucoup de salariés.  

Dans les faits, le fonctionnement de ce système d'envoi de mails est assuré par un logiciel tournant en tâche de fond sur le serveur, chargé d'attendre les requètes de mails et de la transmettre au serveur SMTP se trouvant sur une autre machine. Le logiciel, lancé à la main, fonctionnait de manière tout à fait normale. En observant le trafique réseau, il nous fut possible de constater que les requètes d'envoi de mail n'atteignaient jamais le serveeur SMTP qui les refusait. En prenant contact avec le service national, il s'avera que le pare-feu situé entre le serveur Intranet et le serveur SMTP empêchait toute communication, et ce malgré la demande pourtant réalisée au préalable par M. Thierry Fernandez (demande qui fut effecutée d'ailleurs, le blocage revint sans raison apparente).   
Cette problématique aurait été anodine si nous n'avions pas perdu un temps plus que conséquent ) examiner de notre coté le code du logiciel chargé de transmettre les demandes. De fait, malgré des avantages certains, il ne faut pas perdre de vue que l'externalisation de certains élements critiques peut parfois être source d'une perte de temps non négligeable (Il est à noté tout de même, que le code de l'application mail fut à reprendre à postériori). 

### L'évolution des standards du web

Les standards du web sont mis en point par le W3C, organisme chargé de veiller au bon développement des technologies de l'internet. Relativement stables depuis l'apparition de HTML5, la façon dont traitaient Javascript les navigateur auparavant étaient plus qu'aléatoire. Le code ayant été prévu pour fonctionner sur une vieille version d'internet explorer, une quantité assez importante du code javascript présent dans les pages est problématique. L'essentiel des corrections de bugs rapide ayant eu lieu vers la fin du stage est lié à des problèmes d'interprétation du langage de script coté client. 

## La documentation

Constatant le temps perdu à comprendre le fonctionnement de l'Intranet, et les problèmes liés à la non documentation de celui-ci, une des tâches qui me fut confié était de réaliser un certain nombre de guide d'installation, concernant certaines applications récalcitrantes, ainsi que de cartographie les interdépendance, tout en assurant une certaine documentation de ma propre production. 

Ainsi, entre autre, furent produite une cartographie des interdépendances entre les applications: 

(TODO: insérere ici carto)

Ainsi qu'un schéma présentant l'organisation du code du portail, largement modifié par mes soins:

(TODO: inséer ici schéma âortail)

# L'objectif secondaire: La gestion des demandes faites aux services généraux

## Description du besoin

Afin d'assurer le confort des salariés, leur producitvité et le bon fonctionnement de l'entreprise, la SGAC dispose de services généraux, chargés d'intervenir, à la demande des salariés sur l'ensemble des problématiques matérielles (hors informatique).  
Afin de bien fonctionner, il est nécessaire de la mise en relation entre le salarié ayant détécté un problème, et les techniciens des services généraux se fasse de la manière la plus rapide et fluide qui soit. 

**G**estSup est, selon la page internet qui lui est dédiée, est "un logiciel de GESTion de SUPport 100% web, [qui] permet la gestion de tickets et de matériels."
Son rôle est de fournir une solution logicielle permettant eux salariés de l'entreprise de signaler l'existence de tout matériel défectueux aux services généraux chargés de la maintenance et de l'approvisionnement en fournitures diverses et variées.

Historiquement, la SGAC utilisait un logiciel développé par son service informatique dans les années 2000 associé au service de travail collaboratif Lotus Note (aujourd'hui IBM Notes). Dans le cadre de l'abandon de ladite plateforme de travail de "Big Blue" (vers la solution de mailing de Microsoft, Outlook), il était nécessaire de trouver une solution de remplacement. Le choix se porta initialement sur GestSup. 

## Discussions et changement de l'objectif de la mission

Cependant, suite à des discussions internes à l'équipe du service informatique, en relation avec les services généraux et en vue de la complexité d'intégration du logiciel de ticketing (qui n'est pas compatible avec le système de gestion d'authentification et des droits de la SGAC), il a été décidé que le service informatique développerait, par mon intermédiaire, sa propre solution de gestion de tickets. 

Ainsi la tâche originelle qui consistait en l'installation d'un logiciel web développé en PHP sur une machine Debian s'est mué en une mission de développement d'une solution en C#, de type client léger (.NET 4.5) installé sur le serveur intranet, en tant qu'application à part entière. 

A noté qu'étant donné que la production de documents ne fait pas partie de la culture du service informatique, l'essentiel de la conception se réalisa en se basant sur de simples notes et sur la collaboration rapprochée des services généraux, futurs utilisateurs de l'application et jouant ici le rôle de "clients". La production en elle-même est en revanche parfaitement documentée. 

## Description de l'existant 

Le logiciel précédent, fonctionnant au sein de l'ensemble Lotus Notes fonctionne de la manière suivante:

1. Le salarié repère un problème
2. Il lance l'application, et accède à l'interface de création d'un ticket. Un ticket correspond dans les faits à un bon de rapport de problématique matérielle. 
3. Le salarié remplit ce bon en précisant sur quel site de l'entreprise le problème existe. 
4. Le ticket est transmis au responsable des services généraux associé au site. 
5. Celui-ci estime de la priorité du problème et prévoit une intervention en affectant un opérateur (technicien des services généraux) au ticket. 
6. L'intervention a lieu, l'opérateur répare le problème. 
7. Il accède à l'application et indique que le problème a lieu. 

## Les objectifs

Après discussion avec le responsable des services généraux du site Louis Fargues et des différents responsables du service informatique au cours d'une réunion, il apparu qu'il était évidemment nécessaire que la nouvelle application dispose des fonctionnalités exposées précedemment tout en améliorant certains points, les voici:

* L'application ne doit pas nécessiter d'authentification supplémentaire 
* Le design de l'application doit être mis au point en prenant en compte son ergonomie et son esthétique. 
* Etant donné que certaines opérations sont réalisées par des sous-traitant, ceux-ci doivent être mis au courant de l'évolution des problèmes auxquels ils sont affectés. 
* L'opérateur et le chef de service doivent être en mesure d'entrer en contact simplement avec le salarié à l'origine de la demande. 
* Le salarié à l'origine de la demande doit être mis au courant de l'avancé de sa demande
* Les problèmes doivent disposer d'une catégorie 
* Il doit être possible d'obtenir des statistiques relatives à l'avancement et à la résolution des tickets

## La solution 

Avant de débuter la réalisation de la solution, une courte phase de conception s'imposa durant laquelle modèle de donnée, apparence et choix technologique furent effectués.

### Les technologies 

Le choix des technologies fut relativement limité. En effet, dans une optique de standardisation de l'architecture applicative de la SGAC, il était nnécessaire de développer l'application en C#, en se basant sur les technologies fournies par ASP.NET 4.5.   

ASP.NET permet la création de pages web divisées en deux sous-ensembles. D'une part, nous avons le code de l'interface, en HTML mélé à des élements spécifiques à ASP, et d'autre part le codebehind, responsable du traitement des données et de faire répondre l'interface eux interractions des utilisateurs. 

(TODO: insérer ici schéma codebehind etc.. )

Néanmoins, le système de mise en relation avec la base de donnée étant libre, décision fut prise d'user de l'ENTITY FRAMEWORK dans sa version 6. 

(TODO: insérer ici logo entity framework + schéma )

Celui-ci a l'avantage de permettre un lien avec le modèle des données tout à fait transparent, et des plus simple en étant parfaitement compatible avec LINQ, la technologie de requète sur collections d'objet de Microsoft. De fait, nul besoin pour le développeur d'user directement de SQL, tout le travail de transaction avec le système de gestion de base de données se réalisant de manière parfaitement transparente. 

(TODO: insérer ici logo linq) 

Constatant les problématiques posées par l'usage de javascript au long terme, nous avons préféré mettre de côté le fameux langage de script coté client pour réaliser la totalité des traitements coté serveur. 

### Le modèle de données

Une fois les choix de technologies effecutés, la phase de conception passa par l’élaboration d’un modèle conceptuel de données (MCD). Cette représentation graphique permet de mieux visualiser les tables nécessaires à l’application et les liens entre elles. Après discussion en interne en compagnie de M. Thierry Fernandez, le modèle suivant fut conceptualisé...

(TODO: insérer ici le MCD)

...Et intégré au sein de l'instance de SQL Server 2012 fonctionnant sur le serveur intranet et sur laquelle repose l'ensemble des application de ce dernier. 

### Le maquettage

Enfin, concernant l'apparence de l'application, décision fut prise d'user d'aplats de couleur des plus modernes, à grand renfort d'élements interractifs imposants, à noter que l'usage du bleu comme couleur de mise en avant provient du portail intranet lui-même.

L'objectif était de fournir l'interface la plus simple possible, tout en restant pratique et sobre. Afin de répondre à ces objectifs, la phase de conception se termina part la mise au point de maquette. 

(TODO: insérer ici les maquettes)

A noter l'usage massif de tableaux, qui à defaut d'être "à la mode" en terme de webdesign, ont l'avantage de présenter les informations de manière claire. 

### La méthode de travail

L'ensemble du développement se déroula sans aucun problème, la relation avec le responsable des services généraux se faisant de manière régulière afin de confirmer que le développement de la solution répondait bien à ses besoins. 

L'usage d'ASP.NET se révéla être un excellent choix tant le framework dispose d'outils rendant le développement d'interfaces plus rapide et facile comme le concepteur de vue au sein visual studio, le système de validation de formulaire ou encore d'authentification intégré.  

Suite à un travail intensif durant une période d'environ une semaine, une première version de l'application fut prête à subire les tests. 

### Les tests

Etant donné la non-complexité apparente des algorithmes, il n'apparut pas nécessaire de les tester à l'aide de méthodes lourdes telles que les tests unitaires. De plus étant donné la prépondérance de l'interface et sa forte interdépendance avec la logique de l'application, le contrôle de la qualité logiciel pris la forme de différents tests fonctionnels, d'abord réalisé en interne, au sein du service, puis en compagnie du responsable des services généraux, l'application étant déployée et certains utilisateurs sélectionnés redirigés vers elle. 

L'ensemble des bugs ainsi détectés furent corrigés à la volé, sans que l'on rencontre de problèmes majeurs. 

### Optimisation et documentation du code

Etant donné le faible temps passé sur la réalisation, nous avions à notre disposition un temps important, qui fut consacré à l'optimisation du code de l'application. 

Cette optimisation pris la forme d'une refactorisation relativement importante, associée à un ajout de commentaires massifs et ce notamment grâce à l'outils de conception de documentation intégré à Visual Studio, qui permet de générer facilement et simplement de la documentation sur chacun des élements du code.

(TODO: insérer ici schéma doc xml)

