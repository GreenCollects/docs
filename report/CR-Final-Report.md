# Rappel du sujet / besoin et cachier des charges

  Le projet **Green Collects** est l’initiative des 4 étudiants de _Polytech Grenoble_ cherchant à améliorer le recyclage des déchets, en le rendant plus accessible et en récompensant les personnes effectuant des actions de tri. De plus, nous sommes soucieux de la consommation de produits dangereux pour l’environnement, et nous voulons orienter les consommateurs vers des produits plus vertueux. Ce projet déclenché par notre intérêt pour le recyclage et l’envie de faire des efforts dans les transitions écologiques, nous a également permis de nous intéresser à un milieu que nous connaissions peu, l’entreprenariat. 

  Le projet est né du fait que de plus en plus de déchets se recyclent facilement (plastiques, verres, alimentaires, verts, ménagers) en ayant des poubelles dédiés souvent au pied des habitations. Cependant, encore beaucoup de déchets restent compliqués à recycler comme les batteries, les piles, les huiles ou encore les pneus. L’objectif du projet est donc de faciliter l’identification des lieux de dépôt de ces déchets, et également de permettre aux utilisateurs ayant prévus de s’y rendre d'amener les déchets d’autres personnes ne pouvant pas s 'y rendre en temps normal.

  Ceci a pour finalité d'aider et pousser les filières de recyclage à se développer afin de mieux réutiliser les matières premières et ainsi diminuer l'extraction de ces dernières.

  Nous avons donc décidé de faire une application mobile comportant un système d’identification et d’ajout de points de collectes et de création de collectes entre particuliers, le tout de façon communautaire. 

  L’identification de points de collectes se fait par l’affichage de ces points sur une carte centrée sur la position de l’utilisateur. Il est possible d’ajouter un point de collecte n’importe où sur la carte et ainsi référencer un maximum de points sur la carte. Et afin de vérifier la validité des points de collectes, une note pourrait leur être attribuée par la communauté. Si un point atteint un seuil de notation trop bas il ne sera alors plus affiché sur la carte. 

  La création de collectes à deux objectifs principaux, le premier est de limiter le nombre de déplacement dans les différents lieux de collectes en permettant de confier les déchets à une unique personne qui ira jusqu'à un point de récolte. Le second est de permettre aux personnes n’ayant aucun moyen de transport de participer au recyclage. A termes, lors de la création d’une collecte proche de la position d’un utilisateur, une notification lui sera envoyée afin d’éviter aux utilisateurs de devoir vérifier l'existence d’une collecte régulièrement.

# Technologies employées

  Pour ce projet dont nous sommes à l’origine, nous avons voulu utiliser au moins une technologie que nous n’avons pas pu voir durant notre cursus. Cette décision aurait pu nous poser problème durant la période de travail que nous avions. Cependant, nous sommes curieux et motivés, nous aimons apprendre et nous voulons aussi nous mettre dans le cadre de travail en entreprise où les technologies utilisées ne sont pas forcément celles que nous connaissons.

  Notre projet est une application mobile que nous souhaitons, à termes, déployer sur les deux plateformes mobiles : Android et IOS. Qui dit application mobile dit aussi Frontend et Backend. Concernant le Frontend, deux choix s’offraient à nous : utiliser les technologies natives ou utiliser les technologies hybrides. Les technologies natives sont les plus stables et sont aussi celles qui permettent d’utiliser l’ensemble des services que nous proposent ces systèmes d’exploitations. Cependant il existe une restriction qui nous a plutôt orienté vers la deuxième solution. En effet, pour utiliser les technologies natives Android il faut utiliser des langages comme Java ou Kotlin et peut être développé à partir de n’importe quel ordinateur ayant les caractéristiques requises pour travailler sur ce genre d’application. Mais il faut un appareil Android pour pouvoir tester précisément l’application bien qu’il existe des émulateurs. De plus, les technologies IOS sont plus restrictives car nécessitent un espace de travail Apple pour utiliser l’éditeur XCode. Ces restrictions imposent la présence d’une équipe spécialisée IOS et une équipe spécialisée Android. Malheureusement, dans notre équipe de 4 seule 1 personne peut utiliser l’espace de travail Apple. La charge de travail serait donc trop déséquilibrée et le temps imparti ne nous le permettait pas.

  Nous nous sommes donc orienté vers les technologies hybrides permettant d’utiliser un langage commun et produire une application compatible sur les deux systèmes d’exploitations. Aujourd’hui il existe 2 frameworks implantés Flutter par Google et React Native par Facebook. Nous avons décidé d’utiliser React Native car il s’agit de la technologie React que nous avons tous utilisé en projet personnel ou dans notre cursus. Le principe est d'utiliser le paradigme de la programmation orienté composant en Javascript qui sera ensuite traduit en langage natif.

  La stylisation est un axe d’amélioration pour l’ensemble des membres de l’équipe c’est pourquoi nous avons décidé d’utiliser une bibliothèque de composants graphiques : UI Kitten. De plus, la stylisation en React Native fonctionne grâce à la technologie CSS. Pour nous faciliter les modifications graphiques nous avons utilisé un Framework CSS semblable à Bootstrap nommé Tailwind CSS.

  Une fois les technologies Frontend définies nous voulions utiliser une technologie Backend telle qu’aucune personne du groupe n’a eu l’occasion d’utiliser. Comme énoncé précédemment : c’est un risque mais nous l’avons décemment pris. Nous avons donc regardé ce qui se faisait le mieux en tant que framework Backend et nous sommes arrivé à la décision d’utiliser Django REST Framework basé sur Python3 que nous connaissons tous. Ce framework est considéré aujourd’hui comme l’un des meilleurs et le plus utilisé aux côtés de Laravel un framework PHP. Finalement l’utilisation de cette technologie à été instructive et nous avons pu ajouter cela à notre portefeuille de connaissances. Pour la base de données nous avons choisis d’utiliser PostgreSQL une technologie que nous maîtrisons tous : c’est un gain de temps. Vous trouverez en annexe de ce rapport une comparaison plus détaillée.

  Enfin, nous avons utilisé Docker pour conteneurisé la partie Backend et base de données ce qui nous permet de déployer cette partie sur tout type d’architecture.

# Architecture technique

  ![Architecture technique] (https://github.com/GreenCollects/docs/new/main/report/pictures/architecture.png)

  Par soucis de mobilité, l’application pour les utilisateurs est une application mobile. Ce qui n’est pas le cas de l’application dédiée à l’administration. En effet les administrateurs n’ont pas de problématique de mobilité. Ainsi il est plus simple pour eux d’y accéder par une interface web traditionnelle par ordinateur.

  Ces applications sont des clients légers, c'est-à-dire qu’elles ne possèdent pas la logique applicative et dépendent d’un serveur central.

  Ce dernier contient une API Rest ou interface de programmation d'application en python Django, présentée précédemment. Dans notre cas, l’utilité de l’API vient du fait que nous utilisons notre service sur plusieurs types de plateforme. Ainsi il est facile de développer la logique applicative (manipulation des données, gestion des autorités, …) sans avoir besoin de se soucier de ce qui est fait côté client.

  Nous avons vu qu’il est possible de mettre NGinx sur le serveur web afin de gérer le trafic web en direction de notre service ainsi que le protocoles à utiliser (SSL/TLS). Il a l’avantage d’avoir une charge et une consommation de mémoire très inférieures à celles des serveurs HTTP classiques.

  Le dernier élément est la base de données. Cette dernière est directement reliée au serveur web et permet de stocker toutes les informations nécessaires au fonctionnement de notre application. En développement nous utilisons une base de données sqlite3 et postgreSQL en production.

# Réalisations techniques

  Tout au long de notre période de projet, nous avons pu développer 6 principales fonctionnalités qui nous permet d’avoir une première version d’application viable : l’affichage des points de collecte, le filtrage des points de collecte, la création d’un nouveau point de collecte et d’une collecte, la possibilité de noter un point de collecte ainsi que la gestion des comptes utilisateurs.

## Afficher des points de collecte

  Lorsque l’on arrive sur l’application, on accède directement à une carte où l’on peut voir les différents points de collectes recensés autour de la position de l’utilisateur. L’utilisateur peut alors cliquer sur un des points de collecte et voir quels déchets peuvent être déposés à celui-ci.

  ![Affichage des marqueurs] (https://github.com/GreenCollects/docs/new/main/report/pictures/marker.png)
  ![Détails d'un point] (https://github.com/GreenCollects/docs/new/main/report/pictures/carte.png)
  
## Filtrer des points de collecte

  L’utilisateur a la possibilité de filtrer les points de collecte en fonction du type de déchet. Ainsi, seuls les points de collectes acceptant les déchets sélectionnés par l’utilisateur seront affichés sur la map.

  De plus, il est également possible de filtrer les points de collecte en fonction d’un rayon afin de n’afficher seulement ceux présent dans ce rayon.

  ![Filtrage des points par déchet] (https://github.com/GreenCollects/docs/new/main/report/pictures/dechet.png)
  ![Filtrage des déchets par kilomètre] (https://github.com/GreenCollects/docs/new/main/report/pictures/filtres.png)

## Proposer un nouveau point de collecte

  L’ajout de points de collecte est entièrement communautaire. Il est donc possible de proposer un nouveau point de collecte en précisant son emplacement ainsi que les déchets acceptés.  

  ![Sélection d'une position sur la carte] (https://github.com/GreenCollects/docs/new/main/report/pictures/point.png)
 
## Noter un point de collecte

  Afin de rendre notre système plus fiable, chaque utilisateur peut noter un point de collecte afin de confirmer sa présence et les informations liées à celui-ci, ou au contraire signaler qu’il ne serait pas conforme. 
  
  ![Évaluation d'un point] (https://github.com/GreenCollects/docs/new/main/report/pictures/carte.png)
  
## Créer une collecte

  Une autre fonctionnalité de notre application est de pouvoir créer des collectes entre particuliers afin qu'un seul véhicule n'ait à se déplacer vers le point assigné à la collecte. La personne organisatrice de la collecte n’a alors qu’à renseigner la date, les déchets à récolter ainsi que le lieu de la collecte.
  
  ![Organiser une collecte] (https://github.com/GreenCollects/docs/new/main/report/pictures/collecte.png)
  
## Créer un compte et modifier les informations utilisateurs

  Afin d’accéder à certaines fonctionnalités (comme la création d’une collecte par exemple), l’utilisateur doit posséder un compte et être connecté. Nous avons donc implémenté les fonctionnalités de création et de gestion d’un compte. Un utilisateur peut donc s’inscrire, se connecter, se déconnecter, mais aussi modifier ses informations tels que son nom d’utilisateur, son email, son prénom ou encore son nom.
  
  ![Formulaire de connexion] (https://github.com/GreenCollects/docs/new/main/report/pictures/connexion.png)
  ![Formulaire d'inscription] (https://github.com/GreenCollects/docs/new/main/report/pictures/inscription.png)
  ![Détails d'un compte] (https://github.com/GreenCollects/docs/new/main/report/pictures/compte.png)
 
# Gestion de projet (méthode, planning prévisionnel et effectif, gestion des risques, rôles des membres ...)

  Notre équipe était composée de quatre développeurs dont un chef de projet (Quentin Cambus) et un Scrum Master (Guillaume Mallen).

## Méthode de gestion de projet

  Concernant la gestion de projet, nous avons utilisé différents outils. Tout d’abord, nous avons utilisé Github et plus précisément l’outil Kanban qui nous a permis d’organiser notre projet en tâches et sous tâches. Chaque personne du groupe peut ensuite s’assigner une tâche, et les classer suivant leur avancée : A faire - En cours - Fini. Cet outil nous a aidé à suivre l'avancée de chaque personne du groupe ainsi que l’avancée globale du projet, mais aussi à savoir sur quoi travaillait chaque personne du groupe.
  
  ![Tableau Kanban] (https://github.com/GreenCollects/docs/new/main/report/pictures/kanban.png)
  
  Nous avons également utilisé Discord comme deuxième outil de gestion de projet. Cet outil nous a permis de communiquer entre nous via des salons vocaux et textuels. Nous pouvions également facilement nous retrouver en partageant nos écrans si nous avions des difficultés. Cet outil a grandement facilité le travail collectif. 

  ![Image de Discord] (https://github.com/GreenCollects/docs/new/main/report/pictures/discord.png)
  
  Nous avons pu relier ces deux outils pour recevoir certaines notifications de Github sur Discord lorsque des tâches étaient finies et en attente de revue par d’autres personnes du groupe.

  ![Lien entre Discord et Github] (https://github.com/GreenCollects/docs/new/main/report/pictures/github.png)

  Enfin, nous avons utilisé Google Drive pour collaborer et stocker facilement des documents. 

  En plus de ces différents outils, nous avions au sein du groupe un Chef de projet ainsi qu’un Scrum Master afin de faciliter notre gestion de projet. Des réunions hebdomadaires  étaient organisées avec notre tuteur, Mr Bernard Tourancheau, afin de faire un point sur notre avancée. Nous avons donc appliqué une méthode agile pour ce projet, se rapprochant de la méthode SCRUM. 

  Ces méthodes de gestion de projet se retrouvent communes et de plus en plus répandues notamment concernant discord pour le télétravail. Elles s’incluent dans la mise en place de projet agile qui existe depuis maintenant plusieurs années. Ce ne sont donc pas des méthodes de gestion de projet très innovantes. Elles restent néanmoins des méthodes fonctionnelles et très adaptées à notre projet.

## Gestion des risques

### Contraintes

  Le projet comporte plusieurs contraintes qui sont :
    * **Une contrainte économique** : le projet ne possède aucun financement
    * **Une contrainte temporelle** : des soutenances intermédiaires sont attendus en cours de projet et le projet devra être terminé le 18 mars 2022
    * **Une contrainte organisationnelle** : l’équipe projet doit être composée de quatre étudiants de Polytech de Grenoble du département informatique. Cette équipe ne peut être modifiable.
    * **Une contrainte technique** : l’équipe devra développer une application mobile 
    * **Une contrainte juridique** : l’équipe ne devra pas plagier le code source ou tout autre document venant de l’extérieur du projet.
    
### Risques

  A partir des contraintes exprimées précédemment, certains risques ont été définis. Nous avons ainsi pu établir une matrice de criticité qui permet de hiérarchiser les risques suivants: leur probabilité d’apparition et la criticité de leurs conséquences. 

  En annexe, vous pourrez retrouver pour chaque risque, les mesures préventives et correctives mises en place.
  
  | Probabilité / Gravité | Faible | Moyenne | Grave | Très grave |
  | --- | --- | --- | --- | --- |
  | Très improbable | | - Méconnaissance des outils utilisés, erreur de manipulation | - Mésentente au sein de l'équipe | |
  | | | - Maladie d'un / des membres de l'équipe | - Visions différentes du produit à réaliser au sein de l'équipe projet | |
  | | | | - Perte de données | |
  | Improbable | - Membre de l’équipe peu efficace | - Utilisation / création d’une solution protégée par un brevet | - Utilisation de technologies peu maitrisées par l’équipe projet et manque d’expérience | - Plagiat |
  | | | - Absentéisme | - Mauvaise traduction de nos besoins en fonctionnalité | |
  | | | | - Manque de prise en compte du cahier des charges dans la réalisation du produit | |
  | Probable | | - Attribution d’une tâche inadaptée au profil d’un membre de l’équipe | - Dépassement des délais de rendu | |
  | | | | - Erreur dans la planification du travail | - Complexité imprévue due au manque d’expérience de l’équipe projet |
  | Très probable | | | | |
  
# Outils (collaboration, CD/CI, ...)

## Github

  Nous avons utilisé Github pour : le versionning de code source, la gestion projet, et le DevOps. En effet Github propose de nombreux outils comme un outil de gestion de projet permettant de gérer un Kanban comme expliqué plus tôt. Il permet aussi de mettre en place des pipeline DevOps. Dans notre cas, nous avons mis en place une pipeline d’intégration continue. Une pipeline de déploiement a aussi été commencé. Cependant cette dernière n’est liée à aucun service de web ou cloud car nous n’avons pas eu les financements.

## Discord

  Nous avons aussi utilisé un autre outil, Discord, qui nous permettait de travailler à distance et de faciliter les échanges textuels et vocaux.

  Nous en avons profité pour mettre en place un lien (Webhooks) entre Github et Discord afin de recevoir les notifications de pull request, review, commentaire directement dans Discord.

## VSCode

  Concernant le développement nous avons utilisé l’outil Visual Studio Code qui intègre un grand nombre de plugins (comme Thunder Client*) permettant de s’adapter à toutes nos technologies. Ce dernier outil nous permettait aussi de faire du Pair programming.

  \* Thunder Client est un client Rest intégré sous forme de plugin à VSCode. Il nous a permis de tester notre API ainsi que les autorisations. De plus, il ne nécessite pas télécharger une énième application pour le développement.

## Docker

  Docker est un outil de conteneurisation. Il nous a permis d’utiliser des logiciels tels que postgreSQL, PgAdmin sans avoir à tout paramétrer sur l’ensemble des machines des groupes.

  Nous avons aussi développé la possibilité de construire une image Docker afin de faire marcher notre serveur dans un conteneur.

## Expo

  Expo est plus un framework qu’un outil à part entière. En revanche, il nous a été extrêmement utile pour le développement mobile. En effet, il suffit que le mobile soit sur le même réseau que la machine de développement et expo construit et déploie automatiquement l’application vers le mobile cible.

# Métriques logiciels

## Calcul des lignes de codes et commits

  Voici le tableau récapitulatif des commits du projet avec les lignes de codes de chaque membre de l’équipe :
  
  | | Dorian | Quentin | Malone | Guillaume |
  | --- | --- | --- | --- | --- |
  | Nombre de commits | 72 - 40% | 41 - 23% | 31 - 19% | 30 - 18% |
  | Lignes ajoutées | 6747 | 13159 | 21740 - 12000\* | 4701 |
  | Lignes supprimées | 1946 | 6369 | 1471 | 453 |
  | Lignes total | 4801 - 20% | 6790 - 28% | 8269 - 34% | 4248 - 18% |
  \* ligne de code de l'initialisation du projet
  
  En observant ce tableau on remarque que notre manière de travailler est différente, notamment sur les commits. En effet, on voit que certains membres du groupe préfèrent finir une fonctionnalité avant de commit tandis que d’autres réalisent plusieurs commits par fonctionnalité. On remarque aussi une certaine inégalité quant aux lignes de code totales. En réalité, nous pensons avoir tous fourni un travail équivalent. Ces inégalités proviennent en grande partie de la méthode de pair programming. De plus, nous avons utilisé  du JavaScript, du TypeScript pour le côté frontend et du Python pour le backend. L’ensemble du groupe à travailler sur ces 2 parties du projet, mais les langages cités précédemment n’ont pas les mêmes syntaxe et le Python par exemple est beaucoup moins verbeux que le Typescript, ce qui peut expliquer la différence de ligne de code.
  
## Performance et temps ingénieur

La performance du développement d’un projet est très impacté par le facteur humain. Le fait que le projet se soit bien déroulé et que les objectifs aient été atteint vient de l’équipe et de son fonctionnement. La taille de l’équipe est idéale pour un projet de cette envergure et la communication a été un point crucial du projet. Nous avons tout au long du projet échangé beaucoup que ce soit oralement ou textuellement, et même mis en place du pair programming ce qui a permis de ne jamais laisser un camarade seul sans aides tout en étant tout le temps à jour avec l’avancée globale du projet.

Voici le tableau des jours travaillé et du coup du développement du projet :

 | Noms | Jours / Semaine | Jours total | Coût Total (en €) |
 | --- | --- | --- | --- |
 | Dorian | 6 | 42 | 6026 |
 | Guillaume | 6 | 42 | 6026 |
 | Malone | 6 | 42 | 6026 |
 | Quentin | 6 | 42 |6026 |
 
# Conclusion (Retour d'expérience)

Initialement, nous ne savions pas où aller nous porter ce projet et cette expérience. Nous avons imaginé un sujet et nous avons eu la chance qu’il soit accepté. Ainsi, nous avons travaillé dans un domaine qui nous plait à tous, sur un sujet qui nous à tous motivé. Grâce à cela nous avons pu construire une application from scratch en suivant le principe de MVP (Produit minimum viable). Concernant l’aboutissement de ce projet, nous considérons avoir atteint et dépassé les objectifs que nous nous étions initialement fixés. En effet, l’ensemble des fonctionnalités clés ont été développées. Nous avons pu travailler et mettre en pratique la plupart des méthodes que nous avons pu voir durant notre cursus ou nos expériences professionnelles. Pour certains membres du groupe, ce projet à pu confirmer leur volonté de continuer dans ce domaine de développement (Web & Mobile). On pense objectivement avoir correctement utilisé les différentes méthodes de gestion de projet et ainsi nous avons produit une application rapidement et efficacement. Bien sûr, nous sommes conscients que Green Collects pourrait être grandement amélioré et que certaines fonctionnalités que nous avons imaginés n’ont pas pu être implémentées. Cependant, nous sommes fiers de l'avancée finale. En somme, ce projet était une très bonne expérience et nous avons hâte de travailler à nouveau sur un projet aussi motivant que celui-ci et avec un groupe aussi agréable.

