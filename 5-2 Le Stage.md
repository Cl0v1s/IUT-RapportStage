# Présentation du stage, des missions et responsabilités confiées

(TODO: insérer ici l'offre de stage)

## Description de la mission première du stage: Migration de l'intranet

**D**ans le cadre du stage réalisé au sein de la SGAC, il s'agissait de migrer l'intranet précédemment décrit à deux niveaux, premièrement mettre à jour le code pour un nouvel environnement d'exécution et deuxièmement, le transférer d'un serveur vieillissant à une machine plus moderne.  

### Concernant le code 

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

## L'objectif secondaire: Installation de GestSup

**G**estSup est, selon la page internet qui lui est dédiée, est "un logiciel de GESTion de SUPport 100% web, [qui] permet la gestion de tickets et de matériels."
Son rôle est de fournir une solution logicielle permettant eux salariés de l'entreprise de signaler l'existence de tout matériel défectueux aux services généraux chargés de la maintenance et de l'approvisionnement en fournitures diverses et variées.

Historiquement, la SGAC utilisait un logiciel développé par son service informatique dans les années 2000 associé au service de travail collaboratif Lotus Note (aujourd'hui IBM Notes). Dans le cadre de l'abandon de ladite plateforme de travail de "Big Blue" (vers la solution de mailing de Microsoft, Outlook), il était nécessaire de trouver une solution de remplacement. Le choix se porta initialement sur GestSup. 

Cependant, suite à des discussions internes à l'équipe du service informatique, en relation avec les services généraux et en vue de la complexité d'intégration du logiciel de ticketing (qui n'est pas compatible avec le système de gestion d'authentification et des droits de la SGAC), il a été décidé que le service informatique développerait, par mon intermédiaire, sa propre solution de gestion de tickets. 

Ainsi la tâche originelle qui consistait en l'installation d'un logiciel web développé en PHP sur une machine Debian s'est mué en une mission de développement d'une solution en C#, de type client léger (.NET 4.5) installé sur le serveur intranet, en tant qu'application intranet à part entière. 

## Quelques tâches auxilliaires 

**E**n plus de ces deux principaux objectifs, j'eu à atteindre quelques objectifs secondaires comme en premier lieu, configurer les outils que nous allions utiliser (présentés plus bas) ainsi que, dans un second temps migrer l'ensemble du code source produit par le service ces 10 dernières années vers une nouvelle plateforme de versionning. Il est important de souligner également qu'une tâche d'importance non négligeable qui m'incomba fut de rédiger quelques élements documentaires sur les grandes lignes du système et de mon travail. Elements que vous pourrez retrouver à divers endroits de ce rapports, placés dans un objectif d'illustration. 

## Des responsabilités certaines

**L**'ensemble des logiciels de l'intranet est indispensable au bon fonctionnement de la SGAC. En effet, ceux-ci sont utiles à tout les corps de métiers, des fonctions supports (Gestion des ressources humaines, Services généraux...) aux services au coeur de l'activité de la société d'assainissement (maintenance réseau, gestion usine de traitement etc..). Aussi, toute interruption du fonctionnement des logiciels, de quelque nature qu'elle soit (erreur de manipulation des machines, applications fortement bugguées) durant les heures de travail des salariés (8H30 - 16H30) n'est pas envisageable. Aussi, il fut nécessaire d'apporter un soin tout particulier à la fluidité de la transition afin de limiter l'impact sur les habitudes des utilisateurs, objectif atteint avec plus ou moins de succès. 

## Les outils à notre disposition

**A**fin d'atteindre nos objectifs le plus rapidement possible, tout en assurant une qualité de fonctionnement maximale, en vue de nos moyens, le choix des armes se porta sur une collection d'outils Microsoft consituée des élements suivants: 

* Deux machines virtuelles de développement Microsoft Windows Server 2012...
* ...Equipées chacune d'une version de Visual Studio 2015 édition professionelle, l'environnement de développement intégré, accès sur la conception WYSIWYG (What You See Is What You Get) et l'utilisation des langages de programmation de la multinationale (C#, VB, Visual C++).
* ...Connectées à un serveur Team Foundation Server (TFS), la plateforme de développement en équipe associée à un système de versionning lui aussi propulsé par Microsoft. 

Il est à noter l'absence de documentation à proprement parler, en effet, il semblerait que le service, comme les peuplades d'Afrique Centrale, préfère une tradition orale à la rédaction de documentations. Tâche (trop ?) chronophage s'il en est, au vues des faibles ressources humaines misent à la disposition du service informatique et de la qualité du code fournit. De fait, ormis les quelques commentaires éparses présents dans le code, nous dûmes travailler en découvrant l'architecture du système logiciel au fur et à mesure de notre progression, en nous aidant des connaissances acquises par Monsieur Thierry Fernandez au cours de ses propres explorations dans le code.

<hr>

**T**out au long de cette partie, nous avons décris les objectifs à atteindre, leurs enjeux, ainsi que la nature des moyens mis en oeuvre. Dans la section qui va suivre, nous allons donc nous pencher sur le déroulement de ces tâches et les divers problèmes rencontré, ainsi que les solutions qui y furent opposées.
