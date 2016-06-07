# Historique des missions et constatations factuelles 

Tout au long de cette partie, nous détaillerons le déroulement des différents objectifs, précedemment décris. Afin d'être le plus clair possible, seuls les évenements importants et problèmes rencontrés seront présentés et ce dans un ordre chronologique.  

Il peut être important de souligner que nous resterons ici dans l'analyse purement factuelle, les constatations pratiques et personelles seront déroulées dans une autre partie. 

L'historique de ce stage peut être découpé en plusieurs périodes, identitifées par la nature des tâches qui me furent confiées, ou encore par le type des problèmes et obstacles rencontrés. 


## Première période (semaine 1 à 2): Découverte de l'entreprise, installation des outils et premières manipulations

Les première semaines du stage furent parmis les plus compliquées à mon niveau. En effet, je ne connaissais alors pas encore les subtilités de différents corps de métiers des autres services, ni l'organisation logicielle et matérielle de l'architecture mise en place par le service informatique. 
Etant donné les dimensions de l'entreprise, celle-ci dispose d'une organisation informatique plutôt complexe, complexité d'ailleurs amplifiée de par l'état de mutation (intégration croissante à l'échelle nationale) dans lequel se trouve la SGAC actuellement. 
Or, afin de mener à bien les missions qui allient m'être confiée, il allait être nécessaire d'intégrer et de comprendre l'agencement des différents élements qui allaient constituer mon environnement de travail au cours des prochains mois. 

Cette intégration du fonctionnement du service informatique allait se produire non sans rencontrer quelques difficultées, notamment au niveau de la compréhension des liaisons entre les différents réseaux de l'entreprise. Et ce d'autant plus que les premières tâches que je devais réaliser étaient celle permettant d'installer et de déployer mes futurs outils de travail. 

C'est ainsi que dès le premier jour, on me chargea d'installer une machine virtuelle sur le réseau bureautique qui allait devenir ma station de travail, c'est à dire le poste équipé des outils de développement à proprement parler tels que Sublime Text (éditeur de texte modulable), Visual Studio 2015 édition professionel (Environnement de développement intégré) ou encore l'interpréteur Python, qui allait me permettre de développer quelques scripts des plus utiles.
Ici, aucune difficultée ne fut rencontrée, ayant déjà eu par le passé l'occasion de me constituer plusieurs machine de travail pour mon usage personnel, je savais comment procéder. La seule différence résidant ici dans la configuration réseau de la machine, notamment vis à vis de sa connexion à internet, qui se doit de passer par le proxy installé sur le réseau bureautique. 

Puis, dans les jours qui suivirent, il était question d'installer le serveur TFS (Team Foundation Server) qui allait devenir un autre des mes outils principaux de travail, en me permettant d'héberger, de gérer et de versionner mon code source sur une machine autre que ma station de travail principale. Ce serveur fut lui aussi installé sur une machine virtuelle. En revanche, la machine devait être installée sur le réseau industriel (EQUANT) afin, notamment d'être isolée d'internet et donc par là, d'être protégée entre autre de potentielles attaques. 
Ce choix me permit de comprendre la situation de dépendance du service informatique de la SGAC vis à vis de son équivalent au niveau national. 
En effet, pour que je puisse travailler, il était nécessaire de permettre la liaison du serveur TFS (situé sur EQUANT) avec ma station de travail, située sur le réseau bureautique. Or, ces deux réseaux sont isolés l'un de l'autre par un Pare-Feu géré au niveau national. Il faut donc nécessaire de réaliser une demande et de la transmettre au service informatique à Paris pour que les ports soient ouverts et les liaisons entre les deux machines, permises. Il est à noter que l'exécution d'une telle demande peut prendre entre un et deux jours, ce qui est relativement handicapant, notamment lorsque la réactivité d'un service informatique est essentielle au bon fonctionnement des autres activités de l'entreprise. 
TFS de Microsoft peut fonctionner en deux modes distincts. D'une part, en usant de son propre système de versionning (nommé TFS) et de l'autre on fonctionnant avec GIT, la solution de versionning la plus populaire actuellement. Ma formation à l'IUT m'ayant permis de me familiariser avec GIT, j'ai donc choisis, sans consulter mon supérieur de l'utiliser, pensant gagner du temps en utilisant une technologie que je maitrise. Cependant, je n'avais simplement pas considéré que M. Thierry Fernandez allait à l'avenir travailler de concert avec moi. Or, M. Fernandez ne fut jamais formé à GIT, ayant toujours jusqu'à aujourd'hui utilisé le logiciel de versionning incorporé à TFS. Cette erreur de jugement fut, à plusieurs reprise, source de ralentissement lorsqu'il était nécessaire de travailler à deux sur les mêmes projets. 

Au bout de la première semaine, une fois les outils installés et l'ensemble des fichiers de code source migrés de TFS 2008 précedemment installé vers TFS 2012 configuré par mes soins, je pu enfin commencer la migration du code du portail Intranet. 
Là encore la période d'adaptation fut importante. En effet, je devais travailler sur du code source vieux de plus de 10 ans, relativement peu commenté et usant de "design patterns" (TODO: à ajouter dans le lexique) qui m'était inconnus. Il s'agissait donc de comprendre la logique de mon prédécesseur, d'étudier le code, de comprendre son architecture et les différents processus clés du système. Cette activité d'examen du code me pris entre deux et trois jours, durant lesquels je découvris quelques fonctionnalités de ASP.NET qui m'étaient inconnues telles que le système d'authentification intégrée ou encore les Webservices, sortent d'interface web qui permettent à deux programmes de fonctionner eux s'echangeant des données, à la manière d'une API Web. 

## Deuxième période (semaines 2 à 4): Mise à jour du code de l'intranet

Une fois le fonctionnement du portail étudié et compris, sa migration en elle-même ne fut pas d'une grande difficultée technique, les principaux problèmes provenant de ma connaissance encore imparfaite de l'agancement du code et de quelques subtilitées d'ASP.NET. 
Néanmoins, cette mise à jour fut relativement longue, étant donné ma volonté de réordonner l'architecture du projet, l'organisation des fichiers de code source afin de moderniser celle-ci et de simplifier sa compréhension future, en essayant de donner plus de sens au projet, non seulement à travers le nom des fichiers, mais aussi en les plaçant dans le projet en fonction de leur sémantique/utilité. 

(TODO: insérer ici schéma fonctionnement webservice)

C'est ainsi qu'au bout d'une semaine et demi, la migration du portail fut terminée. Ce qui n'était en revanche pas le cas des applications de l'intranet, auxquelles le portail permet justement d'accéder.

En effet, le portail, comme son nom l'indique est une interface, personnalisée selon les services qui leur expose les applications leur étant utiles. Ces applications de type client léger (il en existe (TODO: insérer ici le nombre d'applications)) permettent eux différentes fonctions de l'entreprise de mieux diffuser de mieux partager l'information au sein de l'organisation.
Ces applications, plus récentes que le portail en lui-même, furent développées en C# .NET 2, voir .NET 3.5 pour les plus "jeunes". De fait leur migration fut relativement simple, la plupart du temps, ma seule tâche consistant à mettre à jour leurs références vers les webservices du portail, dont l'adresse avait changé suite à la réorganisation précedemment exposée. Néanmoins, cette simplicité fut parfois relative, tant les applications sont interdépendantes les unes des autres. En effet, outre les dépendences liées aux webservices, certaines applications dépendent de bibliothèques (DLL) produites par d'autres projets, eux-même situés dans des solutions externes, au nom parfois nébuleux, sinon peu explicite, qu'il fallait donc migrer et recompiler à leur tour avant de pouvoir passer à l'application intranet suivante. 

(TODO: insérer ici schéma interdépendances des applications)

Autre source de problème plutôt conséquent: Microsoft SQL Report Server. Ce service, fonctionnant de concert avec SQL Server, permet de créer des rapports simplement qui rendent possible la visualisation simple des données présentes dans la base. Et ce notamment afin d'aider à la prise de décision ou simplement de constater l'état actuelle des installations et de l'entreprise. 
Bon nombre d'applications de l'intranet font appel à ce service afin de présenter les données sans avoir à coder les différentes requètes ni à construire de nouvelles interfaces. Or, suite à différents problèmes liés au mode d'authentification utilisé par SQL Report Server, et au manque de ressources disponibles sur le sujet, tant au sein du service informatique que sur Internet, ce système nous fit perdre un temps monstrueux. La compréhension de l'origine des problèmes n'ayant été comprise que bien plus tard (vers la semaine 6), leur résolution se fit jusque là à tâton, par "hasard".

## Troisième période (semaines 5 à 8): la migration (et les ennuis) à proprement parler commencent

Une fois l'ensemble du code web migré, nous nous pensions prêt avec M. Fernandez à nous lancer dans le coeur de la migration de l'intranet, c'est à dire couper l'ancien serveur intranet sous Windows Server 2003 et le remplacer par la nouvelle machine, jusqu'alors machine de développement-test, sous Windows Server 2012. 

Il faut savoir que, malgré l'importance capitale de cette tâche, le choix fut fait de ne pas passer plus de temps en tests et développement, de procéder directement à la migration en prévoyant la forte probabilité de bugs. Ainsi les utilisateurs étaient sensé nous rapporter les bugs, et nous, être assez réactifs pour les corriger rapidement et redéployer le code exempt desdits bugs. Ce choix, pouvant paraitre audacieux, sinon contestable, est tout à fait explicable de par le manque de ressources du service. En effet, nous ne pouvions nous permettre de tester l'ensemble des applications du fait de notre faible nombre (deux pour tester un nombre important d'applications) et du manque de temps, ma présence au sein de l'entreprise ne dépassant pas les trois mois (d'autant plus que ne connaissant pas l'usage des ces applications, et ne disposant d'aucune documentation, il nous était difficile d'en tester l'ensemble des fonctionnalités). 

En partant sur cette idée, nous nous mîmes d'accord sur un plan de migration. Il s'agissait de vérifier la configuration d'IIS sur les serveurs, de bloquer l'accès à l'ancien serveur, tout en redirigeant le nom DNS de l'intranet vers la nouvelle machine,de déplacer l'ensemble des bases de données de l'ancien serveur vers le nouveau, de déployer l'ensemble des applications depuis ma station de travail vers le Windows server 2012, d'activer les tâches planifiées et la sauvegarde des bases sur la nouvelle machine, puis enfin d'attendre les retours des utilisateurs. 

(TODO: insérer ici schéma plan de migration)

Etant donné que nous ne pouvions couper l'accès des salariés à l'intranet durant leur temps de travail, la migration ne devait perdurer dans le temps et être terminé avant la ré-embauche. De fait, celle-ci ne pouvait avoir lieu qu'entre 16h30 le jour J et 8h30 le lendemain. 

Une fois l'heure de la débauche arrivée, le travail débuta immédiatement, en revanche, les ennuis, eux n'attendèrent pas. En effet, afin de changer le serveur vers laquel l'adresse DNS de l'intranet pointait jusque là, nous avons du réaliser une demande nationale, en spécifiant explicitement que le changement d'adresse DNS devait se faire après 16h30 et pas avant. Cependant, cette information relative à l'horaire ne fut pas prise en compte par les techniciens du service national qui modifièrent l'adresse DNS dès 14h, ce qui eu pour résultat de bloquer l'intranet pour salariés, en ne manquant pas de générer leur grogne et une phase de stress intense chez M. Fernandez et moi-même. 

L'intranet fut donc bloqué tout l'après-midi et l'espoir d'une migration sans accrocs s'envola rapidement. A 16h30, nous reprîmes donc le déroulé original de notre plan, pour nous rendre compte de bon nombre de problèmes. 
En effet, nous ne nous étions concentré que sur l'intranet en lui-même, hors, quelques cliens lourds et tâches planifiées en sont dépendants.

Cette constatation marqua le début d'une période d'à-peu-prêt trois semaines relativement intense, caractérisée par des embauches vers 7h du matin (au lieu de 8h30-9h) et des débauches tardives. Relativement éprouvante dans mon cas, cette passe n'en fut pas moins enrichissante, en me permettant non seulement de découvrir la réalité du travail d'un service informatique, centre névralgique dans le cadre d'une entreprise connectée comme la SGAC. 

Ces trois semaines furent consituées de corrections de bugs relativement rapides et faciles ainsi que la mise à jour d'une application importante pour les activités de la SGAC. 

Cette application, nommée "Application Intranet" est en fait un client lourd permettant d'accéder depuis les postes utilisateurs à des informations présentes sur le site. Elle rassemble un client IPPOP (base de donnée patrimoine d'entreprise), un client Métrologie (qui fut au centre de tout les problèmes) ainsi qu'une interface présentant un ensemble de rapports (utilisant SQL Report Server précedemment présenté).

(TODO: insérer ici screenshot metro)

Outre les éternels soucis relatifs à SQL Report Server (qui furent premièrement contournés puis réellement résolus), la majeure partie des problèmes liés à cette application proviennent de son client Métrologie. 

En effet, la particularité de l'application Intranet et qu'elle propose de fonctionner en deux modes distincts, le mode connecté (qui affiche directement les données présnetes sur le site) et le mode déporté. Ce mode déporté permet, dans les faits, aux salariés de travailler sur un instantané de leur base de donnée de travail dans des zones non couvertes par le réseau de la SGAC (sur le terrain). Le coeur du problème rencontré provient du fait que la technologie usitée, SQL Server Compact 3.5 ne permet plus aujourd'hui la copie d'instantannés, il fallut donc lui trouver un remplaçant (d'abord SQL Server Compact 4.0, sans succès, puis Microsoft Sync Framework) et adapter le code. Là encore, les problématiques furent nombreuses, toutes liées au fait que les machines des techniciens utilisant l'application fonctionne sous Windows XP, un système paru en 2003. 

Constatant la vétustée des machines la décision fut prise de déployer sur les machines des utilisateurs une version temporaire, en attendant la configuration de Windows 7 sur leur machines, qui permettra de profiter de technologies plus récentes et performantes. 

Ainsi, l'application Intranet dispose aujourd'hui de deux versions, une temporaire fonctionnant sous windows XP et une plus pérenne prévue pour fonctionner sous Windows 7.

## Quatrième période (semaine 8 à fin du stage): La gestion des demandes utilisateurs et améliorations à l'intranet (TODO: à revoir le stage n'étant pas terminé)

La dernière période du stage se déroula sans problèmes particulier. Le gros des problèmes issus de la migration étant résolu, seuls des corrections de bugs mineurs furent à réaliser. 

Cette facilité apparente m'apparut comme relativement providentielle étant donné l'absence de M. Fernandez alors en congés. 

Néanmoins, la quantité de travail en elle-même n'en fut pas ammoindrie. En effet, en parallèle des corrections de bugs, je dû me concentrer sur la résolution du problème de la gestion des demandes utilisateur. 

Précedemment étudiée par le service informatique, en collaboration avec les services généraux (chargés de la résolution des problèmes matériels), la solution originellement prévue consistait en la mise en place d'un serveur habritant le logiciel client léger GESTSUP. Installation qui fut réglée en l'espace de quelques heure. Néanmoins, certains problèmes se présentèrent. Premièrement, les utilisateurs devaient se reconnecter, en usant d'informations de connexion propres à GESTSUP ce qui reste relativement problématique étant donné la tendance des salariés à constamment oublier leurs informations d'authentification. Deuxièmement, GESTSUP était peut être un peu trop complet, voir complexe pour l'utilisation relativement basique que les services généraux et les salariés peuvent en avoir. Après discussion, la décision fut prise de développer en interne une solution de gestion des demandes utilisateur. 

S'en suivit alors une réunion avec le responsable des services généraux qui exprima ses besoins et détailla sa manière d'utiliser la solution de ticketing actuellement mise en place (TODO: à ajouter au lexique). De là fut produit une rapide spécification fonctionelle et le développement démarra. Celui-ci se déroula sans accros et ne s'étala que sur une semaine et demi.    






