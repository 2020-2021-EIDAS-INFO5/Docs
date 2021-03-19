#### UNIVERSITÉ DE GRENOBLE ALPES- GRENOBLE INP

**École polytechnique de l'université Grenoble-Alpes**

![Alt text](./Media/PolySignlogo.png "Title")


```
Rapport de projet eIDAS
```
## Projet de Signature électronique eIDAS*

```
Projet de fin d’étude de cycle d’ingénieur en informatique
```
```
Étudiants:
ASSI Dima
BILOUNGA Aleck
EL AJI Houda
ZERAMDINI Otba
```
```
Porteur de projet:
Prof. PALIX Nicolas
```

- Projet de Signature électronique eIDAS*
- Remerciement
- Objectif du projet
- Technologies Utilisées
- Architecture
- Maquettes
- Gestion de projet :
- Outils
   - 6.1 Outils de collaboration :
   - 6.2 Outils de développement :
- 7. Métriques Logicielles
   - Coût du Projet
- 8. Réalisations techniques
   - Front-end:
   - Back-end:
- 9. Difficultés et contraintes
- 10. Améliorations
- 11. Conclusion
- Bibliographie


## Remerciement

Nous tenons à remercier chaleureusement Monsieur NicolasPalix notre porteur de projet
qui nous a donné l’opportunité de pouvoir réaliserce projet. Sans sa disponibilité et son aide
très précieuse, ce projet n’aurait pas vu le jour. Nous tenons à exprimer, également notre
profonde reconnaissance pour toutes l’équipe pédagogiquede Polytech Grenoble, qui nous
a fourni les outils pour réussir ce projet.

## Objectif du projet

L’objectif de notre projet est de créer un serviceauto-hébergeable PolySign qui va
permettre de signer des documents administratifs ausein de l’université,
principalement les conventions de stage entre administration,étudiants et
entreprises.

Le but principal est de faire la conception et l'implémentationd’un service eIDAS
auto-hébergeable et open-source du workflow de documentspar des acteurs
identifiés au moyen de plusieurs systèmes d’authentification(Oauth2). En d’autres
termes, ce service de signature électronique doitrespecter les réglementation
Françaises et Européennes de la signature électronique.

Le fait d’avoir ce genre d’outils à l’école permettrade signer ces documents en toute
sécurité et sans avoir recours à d’autres logicielscomme Yousign, docusign...

PolySign permet alors à ses utilisateurs de créerdes processus de signature,
attribuer des signataires, visualiser des documentset les signer en toute sécurité en
se reposant sur un système de chiffrement à clé publiqueet clé privée pour signer et
vérifier la signature.

## Technologies Utilisées

Tout d’abord nous avons décidé d’utiliser un générateurde code : JHipster. En effet,
n’ayant que 2 semaines pour développer l'application,il était impossible de tout
développer de zéro.JHipster est un générateur d'applicationlibre et open source
utilisé pour développer rapidement des applicationsWeb modernes en utilisant
Angular et le framework Spring. jHipster propose unoutil en ligne nomméJDL
Studioparticulièrement utile et simple d’utilisation.Cet outil permet grâce à un
diagramme UML de générer du code Java et Angular.D’autre part pour le Mapping
Objet Relationnel nous utilisons la technologie JPAau niveau de la couche DAO.


D’autre part, notre choix s’est porté sur le framework JavaScript angular puisqu’il
permet d’écrire son code de manière très structuréavec TypeScript qui est un
langage orienté objet. De plus, ce framework fournitla possibilité de créer des SPA
(single page application). D’autre part, son richeécosystème facilite la
documentation et l’obtention d’aide. Il est égalementà noter que son architecture
modulaire permet aux développeurs de développer enparallèle et de manière
indépendante. Autrement dit, il permet de rendre ledéveloppement front-end plus
rapide et plus simple.
D’autre part, nous utilisons BootStrap quiest unecollection d'outils utiles à la
création du design de sites et d'applications web.Cette collection d’outils permet de
charger rapidement des templates dans un projet etoffre là encore un gain de temps
considérable.

En Backend notre choix s’est porté sur le frameworkJava Spring. D’une part parce
que le langage Java est un langage maîtrisé par l’ensembledes membres du groupe
et d’autre part parce que le framework Spring estun des framework les plus utilisé,
ce qui permet encore une fois de trouver plus facilementde la documentation.
Nous avons ainsi choisi pour la partie DAO le frameworkSpring Data. Ce framework
est très utile car il permet de déduire les requêtesà partir des signatures des
méthodes. Il représente un gain de temps important.

De plus, nous avons utilisé la couche service SpringBoot qui est un conteneur léger.
Spring Boot permet de faciliter le code de la coucheservice notamment avec
l’instanciation automatique via constructeur ou vial’annotation@Autowired.
Pour la couche web service on utilise le frameworkSpring Rest Api. Qui permet
d’exposer une API REST et de communiquer avec le Front-Endou avec d’autres
systèmes.

Pour la partie authentification nous avons décidéd’utiliser le framework Keycloak.
Keycloak est un outil permettant de centraliser l’infrastructurede sécurité des
applications. Il permet à la fois la gestion des identitésdes authentifications et des
autorisations. Cet outil se base sur des standardsdes protocoles de sécurité tels
que OpenID Connect, OAuth2. Ainsi il permet de mettreen place la double
authentification comme OTP.


## Architecture

```
Dans notre application nous avons 4 acteurs qui interagissentavec l’application :
```

![Alt text](./Conception/Architecture/System_Context_Diagram.png "Title")

#### Diagramme de contexte


● Le User est l’utilisateur d’une organisation.
● L’ Admin est l’administrateur de l’application
● L’ OrganisationAdmin est l’administration d’une organisation
● Le Signer est le signataire
● Keycloack est le service d’authentification exte
Chaque acteur à une liste de fonctionnalités qui sontrésumées dans le diagramme
des cas d’utilisations suivant :

![Alt text](./Conception/Architecture/Use_Case_diagram.png "Title")


#### Diagramme des cas d’utilisation

D’autre part, nous avons choisi une architecture Front-Endet Back-End de
l’application. Avec une architecture MVVM (modèle-vue-vuemodèle) en front-end et
une architecture à trois couches en back-end (WebService, Service en métier et
DAO (Data Access Object).


![Alt text](./Conception/Architecture/Data_abstraction_diagram.png "Title")

Nous avons également réalisé un diagramme de classeUML de l’application qui se
présente comme suit :

![Alt text](./Conception/Architecture/Class_diagram.png "Title")

Ce diagramme de classe nous a permis de créer le JDLet de générer le code grâce
à JHipster, et ainsi d’obtenir une architecture globalede l’application. Ce diagramme
est constitué de 6 entités.
* L‘entité organisation correspond à l’organisation,par exemple polytech ou
l’UGA ou Grenoble INP.
* L’entité UserEntity correspond à un utilisateur quelconque.
* L’entité Authorit est une association qui réalisele lien entre un utilisateur et
une organisation. Elle permet de donner à chaque utilisateurun rôle dans
chacune de sa ou ses organisations.
* L’entité signatureProcess correspond au processusde signature. Ainsi, si une
signature doit être créée cette entité doit être instanciée.
* L’entité SignOrder est très importante, elle est uneclasse d’association qui
fait le lien entre un utilisateur et un processusde signature. Elle permet ainsi
à la fois de mettre un ordre de signature. Et d’associerun fichier à chaque
signataire.
* L’entité SignaturePlacement permet quant à elle derelever depuis le front-end
l’ensemble des localisations dans le pdf où une personnedoit signer (numéro
de page, localisation de la signature en 2 dimensions).


## Maquettes
![Alt text](./Media/m1.png "Title")


La maquette ci-dessus présente la première étape dela création d’un processus de
signature qui consiste à donner un nom au processuset charger le fichier à signer.
Cette étape fait partie de 4 étapes du processus:choisir les signataires, positionner
les signatures sur le pdf et finalement envoyer l’invitation.

![Alt text](./Media/m2.png "Title")

Cette deuxième maquette présente la liste des processusen détail. Elle comporte la
date de la création de chaque processus, son nom,les signataires qui lui ont été
attribués, son statut(complet, en progrès ou annulé),le document à signer et
l’attestation de signature.
Elle comporte aussi le bouton qui permet de faire l’export csv de toute la liste.

## Gestion de projet :

Nous avons appliqué la méthode agile SCRUM pour lagestion de notre projet. Nous avons donc un chef de projet - Otba Zeramdini - et un SCRUM master - Aleck


BILOUNGA. Nous avons donc partager les rôles au sein de notre équipe comme le
suivant :

```
● Otba ZERAMDINI : Chef de projet & Développeur Back-end
● Houda ELAJI : Développeuse Front-end & DevOps
● Dima ASSI : Développeuse Back-end & gestionnairede base de données
● Aleck BILOUNGA : Développeur Front-end & SCRUM Master
```
Afin d’ếtre en contact et en relation tout au longdu projet nous avons effectué des
daily meetings chaque jour. Ces daily meeting permettentd’être renseigné des
avancements de chacun et de discuter des choix techniques. Pour cela, nous avons
utilisé Trello pour partager nos tâches sous formede ticket. D’autre part, Github
nous a permis de collaborer sur l’implémentation ducode. En effet, pour chaque
tâche déjà définie, nous avons créé un **_issue associée._** Nous avons associé à
chaque issue une branche. De plus, un pull requestassignée à un autre membre
pour revoir le code et le fusionner dans la branche **_dev_**.
Finalement, nous avons effectué un dernier **_merge_** dela branche **dev** vers la
branche **_master._**

Afin de progresser sur les tâches complexes, nousavons opté pour **_Live share
code_** pour programmer collectivement.

Pour une première étape du projet nous avons réaliséun planning prévisionnel :

![Alt text](./Media/planning_prévisionnel.png "Title")

Tout au long de notre projet, le planning prévisionnel a été changé est amélioré au
fur et à mesure de notre progression sur les différentestâches prévues :

![Alt text](./Media/planning_effectif.png "Title")


**Gith**

**6. Outils**

### 6.1 Outils de collaboration :

```
● Github : pour bien séparer le travail produit pourchaque fonctionnalité,
avoir un emplacement approprié pour héberger notreprojet avec Git et
pouvoir intégrer le plus grand nombre possible deservices externes.
En plus Github nous a permis d’organiser le travailen créant des issues pour
suivre les tâches, les partager et les discuter avecles membres de l’équipe.
Nous avons deux répertoires :
```
1. App : contenant l’implémentation de notre applicationweb.
2. Docs : Contenant toute la documentation techniquede notre projet.


```
● Trello : Pour garder un journal d’activité présentant nos accomplissements
sur l’ensemble du projet et organiser la répartitiondes tâches en le mettant à
jour par tous les membres de l’équipe.
● GitKraken : interface graphique intuitive de Gitqui simplifie et rationalise
les processus Git.
● Discord : Pour assurer la communication au sein del’équipe et avec notre
responsable, faire des points, discuter les tâches,partager des ressources et
travailler collectivement ou en binôme pour résoudredes problèmes ou
achever des tâches compliquées. Nous avons alors crééun serveur
comportant plusieurs salons textuels et vocaux.
● BBB ( BigBlueButton ) : Un deuxième outil de communicationplus simple
utilisé pour communiquer essentiellement avec notreresponsable de projet
pour discuter l’avancement du projet.
```
### 6.2 Outils de développement :

```
● Visual Studio Code : Éditeur pour le développementFront-end et
Back-end
● IntelliJ IDEA : Éditeur pour le développement Front-endet Back-end
● Docker : Outil d'empaquetage d'une application etde ces
dépendances
● JHipster : outils de génération de code.
```
## 7. Métriques Logicielles

Nous avons réalisé des métriques sur le nombre delignes de code ainsi que sur le
nombre de commits. Cependant elles ne sont pas forcémentreprésentatives du
travail puisque la taille des commits varie par rapportà d'autres. De plus, pour le
nombre de lignes de code on peut voir qu’ Otba a plusde 300000 lignes de code qui
est dû au fait qu’il a souvent travaillé sur la régénérationdu JDL de l’application. En
résumé

![Alt text](./Media/Code.png "Title")


```
● Nombre de commits : 115 commits au total
● Aleck Bilounga : 29%
● Dima Assi : 12%
● Houda El Aji : 18%
● Otba Zeramdini : 41%
● Lignes de code ajouté par nous: 368052
(6316 en réalité) lignes au total
● Aleck Bilounga : 23%
● Dima Assi : 23%
● Houda El Aji : 18%
● Otba Zeramdini : 36%
```

### Coût du Projet

Dans le but d’estimer le coût du projet, nous avonsutilisé la formule du COCOMO.

Pour l'appliquer, nous devons déterminer la complexitéde notre application. Notre
application est assez simple, mais elle requiert unemise en place de signature à
l’aide chaîne de certificats ssl qui est assez complexeà mettre en œuvre pour suivre
la réglementation eIDAS. Ainsi nous avons donc considérénotre application comme
organique.
Le projet compte 6316 lignes de codes .Si nous appliquonsle COCOMO ,on obtient
:
Effort = 2.4 * (6316/1000)^1.05 = 16.6 mois-homme

En sachant que le salaire d’un développeur junioren France est de 3000€brut/mois
on obtient donc pour notre projet un coût de 16.6*(3000€*1.45)= 72210€ en incluant
les charges patronales.

**Temps Ingénieur** : 8h * 5 * 5 =200h Total (en théorie) environ 8h/Jour 5 fois par
semaine

## 8. Réalisations techniques

### Front-end:

```
● Création d’un utilisateur: Nous avons développé lapossibilité de créer un
utilisateur en lui attribuant un nom, un prénom, uneadresse mail et un
numéro de téléphone.
● Assignation d’un rôle lors de la création: Quand unutilisateur est créé il peut
avoir le rôle d’un admin, user ou signer.
● Création d’un processus de signature et chargementde fichier: L’utilisateur de
PolySign peut créer un processus de signature en plusieursétapes. D’abord il
choisit l’organisation à laquelle est attribué leprocessus, il choisit le fichier à
signer et il ajoute des signataires à ce processusen donnant leurs noms,
prénoms, adresse mail et numéro de téléphone.
● Affichage d’un pdf page par page: Après avoir chargéle pdf, l’utilisateur aura
la possibilité de le visualiser et de naviguer dansla fenêtre page par page.
● Drag and drop: Le but de cette étape était d’avoirla possibilité d’avoir chacun
des signataires dans un rectangle défini par son nom.Puis avoir la possibilité
de glisser et déposer chaque rectangle sur le pdfpour définir la position où la
```

```
signature sera visualisée. Nous avons pu implémenter le fait de bouger les
rectangles dans la fenêtre mais pas les déposer surle pdf à cause de
problèmes de récupération des coordonnées.
● Export CSV: Dans le front nous avons ajouté un boutonpour faire l’export csv
de la liste des utilisateurs et la liste de processusde signatures.
```
### Back-end:

❏ Authentification:
* Configuration Keycloack dans Jhipster :
Tout d’abord il s’agit de lier les la configurationde jhipster avec Keycloack afin que jhipster
nous redirige vers Keycloack pour l’authentification.
D’autre part pour pouvoir communiquer avec Keycloackil faut partager un secret avec
Keycloack. En effet, la gestion des utilisateurs (création,suppression, changement de rôle
...) se fait grâce à l’échange de ce secret. Pour pouvoirpar exemple créer un utilisateur
Keycloack il faut d’abord créer une classe java **UserKeycloak.java** qui permet de récupérer
les utilisateurs et leurs différents champs au niveaudu back-end. Pour accéder à keycloack
nous créons une classe **KeycloakConfig.java** qui permetde récupérer un Objet Keycloack qui
va nous permettre de communiquer avec Keycloack. Dansla classe
**KeycloakAdminClientService.java nous** créons l’ensembledes services ou méthodes pour
créer un utilisateur modifier supprimer un utilisateur.Ces services sont directement accessibles
par le front-end via la couche web service et doncune API Rest.
❏ API et couche métier:
* Création d’un processus de signature :
Pour la création d’un processus de signature nouscréons des services de création d’un
processus de signature qui permettent de créer automatiquementles sign order associé aux
utilisateurs et ainsi leurs fichiers associés. Desroutes API ont été créées pour par exemple
récupérer l’ensemble des organisations de la personneconnectée, pour déterminer le rôle
de la personne connectée ...
* Création d’utilisateurs et création d’autorités associées:
La création d’utilisateur s’est faite également viaun service de création d’utilisateur. Cette
création est assez délicate puisqu’elle implique lacréation de l’entité Authorit. De plus cette
création d’utilisateur implique l’envoi d’email versl’utilisateur créer et la génération
automatique d’un password. De plus, il est à ajouterque cette création d’utilisateur sur
jhipster créer un utilisateur sur keycloak. C’estlors de cette phase que l’authentification
avec OTP est configurée.


* Création de certificat : Nous avons dans cette partie,avec java, généré pour
les signatures des pairs de clés privé et publiques.Cette partie est
essentiellement faite pour que les signatures soientbien vérifiées. La taille de
la clé publique est bien de 3072 bits.


* Signature d’un pdf : La signature des pdfs en back-endse fait en choisissant
l’id du fichier à signer et l’id du user qui va signer.Àce moment là les clés seront créés, et un nouveau fichier remplace l’anciendans la base de données avec les coordonnées du signataires et les information du certificat
ajoutés sur le pdf à l’aide de la librairie Spire.pdf.
## 9. Difficultés et contraintes

Étant donné que nous travaillons sur un nouveau projet,le cadre du travail n’était
pas défini auparavant. En effet, nous avons passéun temps considérable sur la
partie de conception UML et la mise en œuvre de l'architectureglobale du projet.

L’objectif de notre projet est la réalisation de signaturesélectroniques avec les
normes eIDAS. Cela implique l’utilisation des certificatset des chaînes de certificats.
De ce fait, nous avons, au début, eu des difficultésà comprendre toutes ces notions.
Ainsi, dans le cadre des réglementations eIDAS etANSSI, nous avons été amenés
aussi à bien faire attention à toutes les exigencestechniques, comme par exemple
l’algorithme d'encryption (SHA-256) et la tailledes clés ( 3072 bytes ).

Par ailleurs, la recherche des librairies pour lasignature d’un PDF était assez
délicate. Nous avons perdu beaucoup du temps et d'effortsà essayer des différentes
libraires en Angularjs/Javascript pour réaliser cettetâche. Cela englobe la signature
manuelle et le positionnement des emplacements dessignatures sur le document,
sans oublier la visualisation du fichier nativementdans l’application. Cela peut
s’expliquer d’une part, du manque de maîtrise de cesdifférents frameworks. D’une
autre part par le manque d' exemples facilitant leurprise en main rapidement. En
addition, au cours de nos recherches nous avons constatéque même les plus
fameuses plateformes de signatures électroniques(ex. DocuSign), s'appuient sur
des fournisseurs des technologies de traitement dedocuments ( PDFTron ). Ces
systèmes de signatures sont souvent payants.

Nos ambitions au départ étaient de réussir à livrerune première version utilisable de
l’application. Mais le manque de temps a été un freinà la réalisation de cet objectif.
Finalement, ce projet a été très intéressant, nousaurions bien aimé pouvoir avoir
plus de temps pour le terminer, ou du moins livrerune première version de
l’application.

## 10. Améliorations


Vu les difficultés rencontrés au cours de notre travail sur ce projet nous estimons
que des éventuelles amélioration peuvent ếtre apporterà notre réalisation :

```
● Créer des signataires à partir des fichier CSV (ex. élèves de Polytech)
● Prise en compte des rôles pour la gestion des autorités.
● Affichage de la liste des utilisateurs lors de laphase de création de la
signature.
● Modification du PDF en Front-End (librairie drag anddrop).
● Liaison du Front-end et Back-end pour l’emplacementdes différentes
signatures.
● Créer une interface de signataire (signer).
● Ajouter une barre de recherche pour récupérer lesutilisateurs
● Amélioration de l’ UI/UX design.
```
## 11. Conclusion

Finalement, ce projet était très enrichissant. Nousavons aimé travailler sur l’aspect
sécurité. En effet, nous avons découvert différentsaspects liés à ce domaine dans le
cadre du développement de l’application tel que Oauth2,OpenID connect et JWT...
De plus, ce projet étant d’actualité, en raison dela situation sanitaire, il permettra à
l’université d’avoir le privilège de posséder sonpropre service de signature
électronique. Ainsi ce service va fournir à l’universitéla possibilité de signer à
distance des conventions de stage pour ses étudiants.Ce projet nous a permis de
réaliser la conception complète d’un projet. De ladocumentation à la conception
puis à l’implémentation, ce projet nous a permis d’abordertous les points de la
conception logicielle. Ce projet a donc été très instructifpour l’ensemble des
membres de l’équipe. Nous sommes déçus de ne pas avoirpu aller tout au bout du
projet et de livrer une première version de l’application.Mais les connaissances que
nous avons pu en tirer sont sans égales.


## Bibliographie

* EIDAS documentation
https://www.ssi.gouv.fr/entreprise/reglementation/confiance-numerique/le-reglement-
eidas/documents-publies-par-lanssi/
https://www.certeurope.fr/blog/lhorodatage-des-documents-electroniques/
https://www.keylength.com/fr/5/
https://blog.signaturit.com/en/what-is-the-eidas-regulation-and-how-does-it-benefit-c
ompanies

* JHipster
https://www.jhipster.tech/
[http://www.jhipster-book.com/#!/](http://www.jhipster-book.com/#!/)
Full Stack Development with JHipster: Build modernweb applications and microservices
with Spring and Angular (English Edition)
* Keycloak
https://www.keycloak.org/docs/6.0/server_admin/

* OAuth
https://oauth.net/2/

* OpenID Connect
https://openid.net/connect/
https://www.infoq.com/fr/articles/introduction-openid-connect/

* JWT (JSON Web Token)
https://blog.ippon.fr/2017/10/12/preuve-dauthentification-avec-jwt/


