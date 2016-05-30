# Présentation du stage, des missions et responsabilités confiées

(TODO: insérer ici l'offre de stage)

## Description de la mission première du stage: Migration de l'intranet

Dans le cadre du stage réalisé au sein de la SGAC, il s'agissait de migrer l'intranet précédemment décrit à deux niveaux, premièrement mettre à jour le code pour un nouvel environnement d'exécution et deuxièmement, le transférer d'un serveur vieillissant à une machine plus moderne.  

### Concernant le code 

L'ensemble de l'intranet repose sur des technologies de développement et d'exécution proposées par Microsoft: les outils Visual Studio, et le runtime .NET, dans sa déclinaison WEB (dans le cas des clients légers) , ASP.NET. 
Celui-ci fut développé durant une période s'étendant de 1999 pour les plus vieilles applications à 2006. 
En examinant les différents élements constituant ledit système, On trouve donc un panel d'applications (de type client lourd et client léger) relativement hétéroclyte fonctionnant avec différentes versions du runtime .NET, de sa version 1.1 à sa version 3.5.

(TODO: insérer ici schéma fonctionnement applications .NET)

Bien que la rétrocompatibilité fut majoritairement assurée au fil des versions, il était des plus intéressant, en 2016, de convertir l'ensemble du code pour qu'il fonctionne avec une version nettement plus récente de l'environnement d'exécution de Microsoft, et ce afin de gagner en homogénéité mais aussi en performances ainsi qu'en terme de pérénité du parc applicatif. Concernant ce dernier point, il peut paraître important de préciser que les applications web furent développer pour fonctionner sur NETSCAPE (ayant totalement disparu aujourd'hui) ainsi que sur Internet Explorer 5. Il était donc relativement urgent, pour des raisons de sécurité notamment de faire évoluer le code. 

(TODO: insérer ici schéma organisation type application ASP.NET)

Cette mise à jour des sources présenta quelques problèmes, regroupables en deux grandes catégories:

* Les problèmes liés à l'évolution du runtime .NET (essentiellement relatifs à des changements liés aux options présentes dans les fichiers de configuration des applications, voir schéma organisation type application ASP.NET)
* Les problèmes liés à l'évolution des standards WEB. Etant donné que les applications furent prévues pour des navigateurs plus que vétustes et la vitesse d'évolutions des technologies de l'internet, bon nombre du code coté client (HTML, CSS et Javascript) était totalement dépassé et il fut nécessaire de reprendre bon nombre de ces élements. 

Durant cette période de trois mois, il s'agissait donc de convertir les applications, de corriger les problèmes issus de cette convertion mais également de, si possible, d'améliorer l'existant. 


### Concernant le serveur 

L'intranet fut hébergé pendant plus de 10 ans sur un serveur virtuel fonctionnant sous Windows Server 2003 exécutant le serveur de base de données SQL Server 2008 (Chronologiquement SQL Server 2000, 2005 puis 2008) ainsi qu'IIS (Internet Information Server), la solution de serveur Web de Microsoft. (TODO: trouver version). Il s'agissait donc, toujours dans le cadre de cette mise à jour importante, de transférer l'ensemble des applications sur une nouvelle machine Windows Server 2012 R2 prévue au préalable par M. Fernandez, équipée d'IIS 7 ainsi que de SQL Server 2012. Les objectifs qui me furent affectés ici sont:

* Configurer IIS 7
* Configurer SQL Server 2012
* Migrer l'ensemble des bases de données depuis l'ancien serveur vers le nouveau 
* Installer sur le nouveau serveur l'ensemble des applications d'administration planifiées (appelées tâches planifiées par la suite). 

Ces tâches, nécessaires à la réalisation de la mise à jour du code furent exécutées en priorité, et durant les premièrs jours du stage. 

## L'objectif secondaire: Installation de GestSup

GestSup est, selon la page internet qui lui est dédiée, est "un logiciel de GESTion de SUPport 100% web, [qui] permet la gestion de tickets et de matériels."
Son rôle est de fournir une solution logicielle permettant eux salariés de l'entreprise de signaler l'existence de tout matériel défectueux aux services généraux chargés de la maintenance et de l'approvisionnement en fournitures diverses et variées.

Historiquement, la SGAC utilisait un logiciel développé par son service informatique dans les années 2000 associé au service de travail collaboratif Lotus Note (aujourd'hui IBM Notes). Dans le cadre de l'abandon de ladite plateforme de travail de "Big Blue" (vers la solution de mailing de Microsoft, Outlook), il était nécessaire de trouver une solution de remplacement. Le choix se porta initialement sur GestSup. 

Cependant, suite à des discussions internes à l'équipe du service informatique, en relation avec les services généraux et en vue de la complexité d'intégration du logiciel de ticketing (qui n'est pas compatible avec le système de gestion d'authentification et des droits de la SGAC), il a été décidé que le service informatique développerait, par mon intermédiaire, sa propre solution de gestion de tickets. 

Ainsi la tâche originelle qui consistait en l'installation d'un logiciel web développé en PHP sur une machine Debian s'est mué en une mission de développement d'une solution en C#, de type client léger (.NET 4.5) installé sur le serveur intranet, en tant qu'application intranet à part entière. 

## Missions et responsabilités

## Les Moyens mis en oeuvre
