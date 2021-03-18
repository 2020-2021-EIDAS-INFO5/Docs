# Le projet

[eIDAS](https://fr.wikipedia.org/wiki/Electronic_identification_and_trust_services)Electronic IDentification Authentication and trust Services est un règlement de l'UE sur l'identification électronique et les services de confiance pour les transactions électroniques au sein de l'Union Européenne. 

Plusieurs services commerciaux proposent un service eIDAS.

Les applications à Polytech sont par exemple le circuit de signature des conventions de stage.

L'objectif du projet est la conception et l’implémentation d'un service eIDAS auto-hebergeable et open-source du workflow de documents par des acteurs identifiés au moyen de plusieurs systèmes d'authentification (OAuth2).

Exemples de services commerciaux
* [DocuSign](https://fr.wikipedia.org/wiki/DocuSign)
* [Yousign](https://yousign.com/fr-fr)
* [Universign](https://www.universign.com/fr/)
* etc

# L'équipe
* Dima ASSI
* Aleck BILOUNGA
* Houda EL AJI
* Otba ZERAMDINI

Supervisé par : M. Nicolas PALIX

# Journal
## Sprint 0
### Semaine du 25/01
* 28/02: Attribution du projet
* 29/02: Rendez-vous avec Nicolas PALIX
   1. Présentation du projet et de son contexte
   2. Discussion sur les outils de collaboration et conseils sur des librairies pour l'affichage de PDF

### Semaine du 01/02

* Mise en place des outils de collaboration
    1. Serveur Discord 
    2. Groupe Facebook
    3. Tableau Trello 
    4. Définition de tâches et répartition du travail
    5. Répartition des rôles
* Début Documentation sur EIDAS:
    1. Réglementation EIDAS
    2. Signature électronique
    3. Documentation sur l'ANSSI
    4. Recherche sur les librairies (pour visualiser des PDF : Jquery, ng2-pdf-viewer, ngx-extended-pdf-viewer,etc, écrire dans des PDF : Apache FOP, PDFBox)  

### Semaine du 08/02

* Création projet Github
* 12/02: Discussion sur l'avancée et des problème rencontrée lors de documentation sur le projet avec Nicolas PALIX 
* Documentation sur EIDAS :
    1. Certificats ssl
    2. Chaîne de certificats 
    3. Contraintes de l'ANSSI à respecter pour la réalisation de la signature électronique

## Sprint 1
### Semaine du 15/02

Interruption Pédagogique

* Recherche sur les différents services commerciaux existant réalisant la signature électronique (Yousign, Universign, DocuSign)
* Conception architecturale 
    1. Diagramme UML
    2. Diagramme de classe
    3. Diagramme des cas d'utilisation
    4. Due globale 
    5. Réalisation de maquettes
    6. etc

### Semaine du 22/02

* 22/02: Rendez-vous Nicolas PALIX : Discussion sur l'avancement du projet, présentation du travail sur la conception de l'architecture de l'application
* Conception : 
    1. Modifications apportées au diagramme de classe
    2. Modifications apportées au diagramme d'objet
* Documentation sur l'Horodatage électronique
* Documentation sur l'ANSSI: Contraintes à respecter pour la réalisation et la validité de la signature électronique
* 25/02: Rendez-vous avec Nicolas PALIX : Discussion sur la chaîne de certificats pour réaliser la signature et présentation des modifications apportées à l'architecture précédemment réalisée.
* 26/02: Soutenance de mi-parcours

## Sprint 2 

### Semaine du 01/03

* Travail sur le JDL de l'application
* Génération avec JHispter de l'application du projet
* Documentation Keycloak
    1. Documentation sur [Json Web Token(JWT)](https://jwt.io/introduction) 
    2. Protocoles [Oauth2](https://oauth.net/2/) et [OpenID connect](https://openid.net/connect/)
    3. Documentation sur Spring Security
    4. Envoi de mail
* Configuration de Keycloak
    1. Travail sur la liaison d'un utilisateur de Keycloak à un utilisateur de l'application jhipster.
    2. Vérification d'email, réinitialisation de mots de passe lors de la creation d'un compte utilisateur
    3. Configuration d'[https://fr.wikipedia.org/wiki/Mot_de_passe_%C3%A0_usage_unique OTP] avec Keycloak lors la création et la connexion d'un compte à l'application
* Visualisation d'un PDF en mode scrollable dans une page de l'application avec la librairie [https://www.npmjs.com/package/ngx-extended-pdf-viewer ngx-extended-pdf-viewer]
* Test sur les librairies de signature à la main  : [retenu](https://www.npmjs.com/package/signature_pad signature_pad) et [pas retenu](https://www.npmjs.com/package/angular2-signaturepad angular2-signaturepad)
* Réalisation de la page d’accueil d'un compte connecté à l'application
* 05/03: Rendez-vous avec Nicolas PALIX : Présentation de l'application généré et point d'avancement

### Semaine du 08/03
* Page de création d'un utilisateur d'une organisation dans l'application
* Merge de branches

* Positionnement d'un place holder pour poser la signature : ''cdkDrag Module'' d'Angular.
* Visualisation d'un PDF en tant que canvas d'un PDF et une page à la fois avec ''pdfjslib-dist'' la librairie [https://www.npmjs.com/package/pdfjs-dist pdfjs-dist]
* export en CSV de la liste des utlisateurs et des organisations de l'application 
* 12/03: rendez-vous avec Nicolas PALIX : Point d'avancement et conseils sur l'implémentation du circuit de signature
* Utilisation d'autres librairies:
    1. [https://www.e-iceblue.com/Introduce/free-pdf-for-java.html#.YFJQRu1KhNg Spire.PDF](version gratuite) pour lire et écrire dans les PDF et les sauvegarder 
* [https://fr.wikipedia.org/wiki/X.509 x509] pour la génération des certificats
* [https://www.bouncycastle.org/fr/ bouncyCastle] pour la génération des pairs de clés


### Semaine du 15/03
* Ajout de bouton pour le PDF avec afin de pouvoir changer de page. 
* Test sur la librairie [https://pdfbox.apache.org/ PDFBox] car non payante contrairement à Spire.pdf pour lire et écrire dans les PDF et les sauvegarder
* Test sur la librairie [https://interactjs.io/ Interactjs] pour le PDF car elle semble plus complète pour placer un canvas dans un PDF et aussi détecter la position du canvas par rapport à la page actuelle du PDF : pas retenu car nous n'avons pas réussi à récupérer les coordonnées du canvas dans le PDF par manque de temps.
* Travail sur la page de création d'un circuit de signature
** Page de Chargement du document PDF pour la signature
** Page d'Ajout des signataires au document 
** Page de Placement des cases dans le PDF où les signataires doivent signer (pas encore fait)
** Page de récapitulatif et envoi de mail aux signataires pour finaliser la création d'un circuit de signature (pas encore fait)
* Merge de branches

### 19/03: Soutenance finale

# Liens 

*[https://github.com/2020-2021-EIDAS-INFO5 Projet GitHub]
*[https://docs.spring.io/spring-framework/docs/5.3.5-SNAPSHOT/reference/html/ Documentation Spring]
*[https://www.keycloak.org/docs/latest/getting_started/index.html Keycloak]
*[https://angular.io/docs Documentation Angular]
*[https://ng-bootstrap.github.io/#/home Bootstrap 4 for Angular]
*[https://medium.com/angular-in-depth/how-to-get-started-with-canvas-animations-in-angular-2f797257e5b4 Canvas Angular]
