ANGULAR est pour le front ce que 
===
SPRING est pour le Back
===


![](/mib.jpg)

<h2>Lundi</h2>

**retour alternance**

**Projet** : vous devez réaliser une application web simple de gestion de produits(articles) classés par catégories permettant à terme aux utilisateurs de remplir leur panier !
L'appli complète aura une partie back avec Spring comprenant les web services à développer et la partie front avec Angular qui exploitera ces services.
Pour ce faire, vous utiliserez IntelliJ et un SGBD virtuel afin de vous concentrer essentiellement sur les nouvelles notions abordées ici, à savoir, la prise en main d'Angular !
Commencez par réaliser le schéma UML répondant aux besoins fonctionnels trés basique dans notre première version, à savoir :
"un produit n'appartient qu'à une seule catégorie et une catégorie peut posseder plusieurs produits"
      -> un produit a un id, une designation, un prix et un attribut quantité
nb : Dans ce premier Sprint, concentrez-vous particulièrement sur la gestion des produits afin de vous familiariser avec l'ensemble des frameworks et outils avant d'ajouter la gestion des catégories de produits.

**50.1 Install IntelliJ**
- si ce n'est pas fait, ajouter le jdk8 à votre Ide (projet structure + jdk8 )
      -> astuce pour trouver un chemin readlink -f $(which java) 
- ajouter le plug in de spring (assistant)

**50.2 Création d'un projet à l'aide de l'assistant spring**
- java 8 ; Group : co.simplon + Artifact ; CatService ; maven ; jar
- dependances : sql : jpa + h2 pour bdd virtuel) ; web : web(rest controller) + rest repo(web service) ; core : lombok (genère les getters...) ; tous les aspects securité seront gérés plutard avec spring security.

**50.3 Création des entités Product & Category + mécanisme d'annotation JPA**
      -> Nouveauté ici consiste à trouver un moyen de générer automatiquement getters, setters, constructeurs sans paramètres grâce à Lombok, constructeurs avec tous les paramètres, méthode toString... pour ce faire il faut ajouter le plug in Lombok à IntelliJ

**50.4 Ajout des interfaces JPA Repository**

**50.5 Ajouter maintenant des produits dans votre base virtuelle puis afficher les pour vérif**

**50.6 Nous avons déjà vu comment réaliser nous même des web services Rest aussi pour changer, vous allez demander à Spring de le faire pour vous : @RepositoryRestResource !**
      -> votre micro service crée, il faut maintenant le tester
      -> utiliser l'outil ARC de chrome pour envoyer une requête qui permet d'ajouter un produit, vérification
      -> puisqu'on y est, un peu de révision, réaliser une mise à jour d'un produit, vérification
      -> un dernier pour la route, merci de supprimer un produit, vérification
      
MERCI SPRING ...

<h2>Mardi</h2>

**veille**

**51.1 Ajouter maintenant un moyen de rechercher des produits par mots clés**
      -> par ex en renvoyant tous les produits commençant par PC
      -> ajouter ensuite un moyen de faire de même avec un mécanisme de pagination

**51.2 A l'aide du mécanisme de projection**
      -> mettez en oeuvre des filtres permettant de faire apparaitre uniquement les prix des produits
      -> puis ajouter aussi les désignations
      -> ajouter aussi un moyen d'afficher l'id des produits
      
**51.3 laissons Spring Data Rest de coté** 
Réaliser un Rest Controller qui sert en général à gérer les cas particuliers, difficile à mettre en oeuvre avec Spring data. Il s'agit donc ici de créer votre api Rest personnalisé avec l'avantage d'accéder à votre couche métier... un peu donc de révisions, ajouter des méthodes pour :
      -> renvoyer la liste des produits
      -> renvoyer un produit à partir de son id
      -> mettre à jour un produit
      -> ajouter un produit
      -> supprimer un produit
  Tester chaque méthode, quelle conclusion ?

<h2>Mercredi</h2>

**veille**

**52.1 ANGULAR ENFIN NOUS Y VOILA**
      -> Install nodeJS si c'est pas déjà fait
      -> Install angular/cli
      -> Créer un projet à partir de intelliJ (surtout changer de directory)
      -> Démarrer le serveur de test et ouvrer votre appli dans un navigateur (localhost:4200)
      -> Ouvrer votre projet dans votre Ide et observer la structure

**52.2 Recette pour "Réaliser" une page template rapidement**
      -> Nous aurons besoin d'installer Bootstrap3
      -> Puis de l'ajouter au projet via le fichier Angular.json
      -> redémarrer le serveur pour prendre en compte les modifs
      -> nous aurons besoin aussi de Jquery à installer aussi...
      -> Copier le code d'une barre de menu déroulant existante (menu bar boostrap3)
      -> Coller dans votre composant principale (app.component.html)
      -> démarrer votre serveur
      -> modifier votre menu déroulant pour obtenir le résultat suivant :
      ![](/first.png)

**52.3 Réalisation de votre premier composant**
      -> Générer votre premier composant "Products"
      -> Réaliser l'association entre le menu/chercher et l'affichage du composant (Routage)
      -> Vérifier que ça fonctionne
      -> Ajouter un autre composant pour menu/ajouter
      
**52.4 Il est temps de faire travailler notre composant**
      -> ajouter y un bouton qui provoque la récupèration de l'ensemble des produits via notre api puis les afficher comme ci dessous :
      ![](/second.png)
      
**52.5 Service**
      -> Vous allez refaire quasiment la même chose avec la notion de service d'Angular cette fois, votre composant doit utiliser un service pour récupérer les données
          
**52.6 Pipe**
      -> Utiliser maintenant un outil de formatage (Pipe) pour afficher les nombres décimaux comme ici :
      ![](/third.png)

<h2>Jeudi</h2>

**veille**

**53.1 Pagination** 
      -> Nous allons maintenant exploiter la pagination prévue en back aussi apporter les modifications pour obtenir 5 produits par page comme ici :
      ![](/fourth.png)

**53.2 Formulaire**
      -> Réaliser un formulaire de recherche de produits toujours en exploitant vos micro service côté back :
      ![](/fifth.png)

**53.3 Supprimer un produit**
      -> Ajouter un bouton pour supprimer un produit qui aura pour effet de le supprimer au niveau du back, n'oubliez pas de demander confirmation !
      ![](/sixth.png)

**53.4 Ajouter un produit**
      -> Faire de même pour le composant permettant d'ajouter un nouveau produit, il aura pour effet de l'ajouter en base coté back
      ![](/new-product.png)
      
  -> Option facultative ici : Offrez la possibilité d'afficher le produit nouvellement ajouté + bouton pour continuer à saisir d'autre produit

**53.5 Editer un produit**
      -> Réaliser un nouveau composant d'édition afin d'éditer un produit et de le mettre à jour en back forçément :
      ![](/edit.png)
      ![](/update.png)
      -> trouver un moyen de crypter les données sensibles en utilisant base64 comme ici
  
<h2>Vendredi</h2>

**veille**

**54.1 Gestion base de donné**
      -> jusqu'à maintenant, nous travaillons sur une bdd virtuelle aussi il faur basculer sur le SGBD de votre choix en apportant toutes les modifications necessaire.
      
**54.2 Deploiement de votre appli**
      généralement, on installe les micro services sur un serveur à l'aide d'un script et l'appli front sur un autre mais faites le test ici en local et pour ce faire il faut :
      -> Demander gentillement à angular de générer tous les fichiers de l'appli (index.html...)
      -> Faire de même avec maven qui va générer un .Jar
      -> lancer les 2 et tester

**55.1 Prochaine étape/sprint : Gestion des Catégories**
      -> Il s'agira enfin d'ajouter des catégories de produits (computers, smartphones...) et autre fonctionnalités (sécurité, Panier, commande, payement, Mobile...)

- Synthèse semaine Angular

- Terminer tous vos travaux + envoi sur github

- Organisation préparation du titre

NB : Il est fortement conseiller d'utiliser les outils de dev F12

**Ressources**

[IntelliJ IDEA: The Java IDE for Professional Developers by JetBrains](https://www.jetbrains.com/idea/)
[Tutoriel Vidéo TypeScript](https://www.grafikart.fr/tutoriels/typescript-781)
[Angular](https://angular.io/tutorial)
[Développez des applications Web avec Angular - OpenClassrooms](https://openclassrooms.com/en/courses/4668271-developpez-des-applications-web-avec-angular)
[YouTube](https://youtu.be/O7D6hFg1P3I)
