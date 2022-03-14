# MSPR2

Votre tâche consiste à réaliser les missions suivantes :
• Mission M1 : Mise en place d’une infrastructure virtuelle
• Mission M2 : Hébergement du portail d’authentification sur un cluster Linux ACTIF/PASSIF
• Mission M3 : Synchronisation des fichiers au sein du cluster
• Mission M4 : Mise en place d’un service Active Directory / DNS / DHCP
• Mission M5 : Sécurisation du réseau via firewall
• Mission M6 : Sécurisation du cluster WEB
• Mission M7 : Mise en place d’une solution de supervision
• Mission M8 : Rédaction des livrables (cf section « livrables attendus ») et préparation de la soutenance

---------------------------------------------------------------------------------------------------------------------------------------

Mission M1 : Mise en place d’une infrastructure virtuelle

L’ensemble des services devront fonctionner sur une infrastructure virtuelle basée sur un ou plusieurs hyperviseurs de type 1.
Les différents réseaux seront également virtuels, la connexion avec le réseau physique se fera au niveau du bac à Sable EPSI.
Vous devez donc commencer le projet par la mise en place de l’infrastructure virtuelle en faisant en sorte que chaque membre du groupe puisse y accéder de manière autonome. Parallèlement à cette phase, il vous faudra découper l’ensemble du projet en tâches, évaluer leur durée et vous les répartir.

---------------------------------------------------------------------------------------------------------------------------------------

Mission M2 : Hébergement du portail d’authentification sur un cluster Linux Actif/Passif

Le portail WEB d’identification devra être hébergé sur un cluster ACTIF/PASSIF (au minimum) voire ACTIF/ACTIF de serveurs WEB.
Vous êtes libres dans le choix de la solution de cluster.

Vous n’avez pas à développer le portail WEB mais à des fins de test, il faudra mettre en place une page de formulaire avec quelques images pour le simuler. L’application WEB doit donc être hautement disponible et au moins 2 serveurs WEB feront partie du cluster.
Le serveur WEB doit être accessible à partir du réseau local et d’Internet. Internet sera simulé par le réseau bac à sable de l’EPSI. Il est impératif que ce serveur soit protégé et qu’il soit situé dans un réseau privé différent du LAN de la clinique.

---------------------------------------------------------------------------------------------------------------------------------------

Mission M3 : Synchronisation des fichiers au sein du cluster

Il est impératif que le contenu du service WEB soit identique sur chaque serveur du cluster.

Vous devez donc soit mettre en place un stockage partagé sur un serveur indépendant sur lequel sera stocké le contenu de l’application, chacun des serveurs pouvant y accéder simultanément, soit mettre en place un mécanisme de synchronisation de fichiers entre tous les serveurs du cluster.

Le stockage partagé peut être mis en place sur Linux ou Windows server, il pourra être accessible via un montage de fichiers selon le protocole de votre choix. Il est également possible d’utiliser une distribution qui émulerait un NAS (Type FreeNas par exemple).

---------------------------------------------------------------------------------------------------------------------------------------

Mission M4 : Mise en place d’un service Active Directory / DNS / DHCP

Afin de centraliser l’identification des utilisateurs sur le réseau et les postes de travail, la Clinique souhaite mettre en place un annuaire Active Directory (annuaire qui sera d’ailleurs utilisé par l’équipe de développement du portail d’authentification).

Cet Active Directory fera d’ailleurs office de serveur DNS pour la zone chatelet.local et fournira un adressage dynamique aux postes du réseau LAN.
Vous devrez utiliser un serveur Windows 2016/2019 server pour mettre en place ces services. Il est impératif d’en tester le fonctionnement.

La création d’un poste Windows 10 dans l’infrastructure vous permettra de faire vos tests en plaçant cette VM dans le LAN virtuel de la clinique que vous aurez précédemment créé.

---------------------------------------------------------------------------------------------------------------------------------------

Mission M5 : Sécurisation du réseau via FireWall

Afin de sécuriser les échanges entre le réseau LAN, le réseau du cluster WEB et Internet, il est impératif de mettre en place un Firewall (virtuel) qui fera le routage entre ces réseaux et qui gèrera les types de trafic autorisés ou interdits de transit entre les réseaux LAN et entre ces réseaux et Internet.

Il faudra cependant veiller à ce que le cluster WEB soit atteignable à partir du WAN.
Vous pouvez utiliser la solution de votre choix pour le firewall : Serveur Linux, Solution PFSence/OPENSence ou autres…

---------------------------------------------------------------------------------------------------------------------------------------

Mission M6 : Sécurisation du Cluster Web

Il est impératif de protéger votre serveur WEB des potentielles attaques, sachant que le portail des soignants doit être accessible à partir de l’Internet.
Pour cela, vous devrez mettre en place un système permettant de se protéger des attaques DDos ainsi que des tentatives de brute-force d’authentification sur le formulaire d’identification du portail.

Ces protections sont à placer directement sur les serveurs du cluster ou, selon votre infrastructure de cluster, sur le ou les serveurs frontaux accueillant les connexions (les répartiteurs de charges).

---------------------------------------------------------------------------------------------------------------------------------------

Mission M7 : Mise en place d’une solution de supervision

La DSI de la Clinique souhaite à tout moment connaitre l’état de la plate-forme des soignants, c’est-à-dire du cluster WEB. En cas de problème, la DSI doit être alertée par mail.

Elle veut également être capable d’évaluer la bande passante nécessaire au niveau de la connexion Internet afin d’assurer un service rapide aux utilisateurs distants.
Pour ce dernier point, il est nécessaire de mettre en place un service de métrologie permettant d’observer les débits réseaux dans le sens Internet > Cluster WEB et inversement.

Vous devez donc mettre en place une ou plusieurs solutions de supervision qui répondra aux besoins ci-dessus.

---------------------------------------------------------------------------------------------------------------------------------------

Mission M8 : Rédaction des livrables attendus et préparation de la soutenance

Voici la liste des livrables attendus :

• Une démonstration des services déployés fonctionnels aura lieu lors de la soutenance orale dont la date vous sera communiquée dans les meilleurs délais.
Vous devez démontrer que vous remplissez l’ensemble des fonctions et des contraintes décrites précédemment dans le document lors de cette démonstration, elle demande donc de la préparation et un fil conducteur.

• Un plan d’adressage IP de votre infrastructure
• Un schéma de votre infrastructure (qui peut comprendre le plan d’adressage)

---------------------------------------------------------------------------------------------------------------------------------------

V – CONTRAINTES ET MOYENS

5.1 Matériel

Une machine sera mise à votre disposition afin d’y déployer l’infrastructure. Elle disposera d’au moins 20Go de RAM et sera équipée obligatoirement de disques SSD afin d’y stocker les VMs en fonctionnement.

Vous serez libre d’y installer l’hyperviseur de votre choix.

La machine devra être restituée le jour de la soutenance.

Elle devra rester connectée au réseau bac à sable de l’EPSI, il n’y aura donc pas possibilité de la déplacer ailleurs.


5.2 Travail en groupe

Les groupes doivent être formés de 4 apprenants maximum et constitués dès le début de la première séance. Ils seront par la suite immuables.

• Établir en début de projet un planning prévisionnel précisant les tâches à accomplir, leur durée estimée et leur affectation.
• Certaines tâches sont dépendantes des autres, n’hésitez pas à créer des services temporaires pour tester certains services temporairement : par exemple vous pouvez commencer à travailler sur les moyens de protection d’un serveur WEB sans que le cluster soit monté.

• Les outils de virtualisation permettent d’exécuter des VMS sur n’importe quel hyperviseur, la copie des VMS est facile (il suffit de copier le répertoire), il est possible de faire des clones.

Comme vous travaillez à plusieurs, rien n’empêche d’utiliser chacun sa propre VM pour l’insérer ensuite dans l’infrastructure.

Par exemple, vous pouvez construire votre VM sous VMWare Workstation puis l’importer sur un ESXi à condition au départ d’avoir veillé aux compatibilités de versions lors du choix de création de la VM.

---------------------------------------------------------------------------------------------------------------------------------------
