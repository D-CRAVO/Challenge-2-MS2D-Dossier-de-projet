# Challenge-2-MS2D-Dossier-de-projet
  
## 1 Cahier des charges

### 1.1 Résumé du projet

Le projet a pour but de permettre de constituer des groupes de travail lorsque les apprenants doivent travailler à plusieurs sur un thème particulier.

### 1.2 Contexte du projet

L’ESN a un client qui édite des applications web à l’intention des écoles et des centres de formation. Dans ce contexte il faut concevoir une nouvelle fonctionnalité permettant au formateur d’organiser le travail des apprenants.

### 1.3 Spécifications fonctionnelles

Un formateur doit pouvoir entrer les noms et prénoms de chaque apprenant, indiquer le nombre de groupes qu’il souhaite puis appuyer sur un bouton « Former les groupes » afin que la liste des apprenants s’affiche par groupe.

### 1.4 Spécifications techniques

Le développement du Backend se fera sous Java et Spring Boot par l'intermédiaire de l'IDE Visual Studio Code. Le développement du Frontend se fera sous Angular et utilisera Material par l'intermédiaire de l'IDE Visual Studio Code. La persistance des données sera gérée par PostGreSQL. Le versioning sera assuré par Git.

## 2 Analyse "Système fermé"

### 2.1 Analyse des acteurs et des Use Case

#### Définir les acteurs

Formateur : personne en charge de rentrer les noms des apprenants dans le système.

#### Définir les Use Case

Ajouter un apprenant : le formateur saisi les noms et prénom de l’apprenant.

Supprimer un apprenant : le formateur supprime un apprenant de la liste des apprenants.

Déterminer le nombre de groupes : le formateur renseigne le nombre de groupes.

#### Diagramme des Use Case

![Diagramme_Use_Case](/Enterprise-Architect/Primary%20Use%20Cases.bmp)

### 2.2 Sélection des Use Case

#### 2.2.1 Use Case : ajouter un apprenant

Acteur : formateur

Précondition : le système affiche la page « Enregistrer un apprenant - vierge »

Postcondition : l’apprenant est enregistré

Scénario nominal :

1.	Le formateur saisi le nom de l’apprenant
2.	Le formateur saisi le prénom de l’apprenant
3.	Le formateur clique sur le bouton « Ok »
4.	Le système enregistre l’apprenant et affiche un pop-up de indiquant que l’opération s’est bien déroulée

Scénario exceptionnel :

3E1 Le formateur clique sur le bouton « Annuler »
1.	L’application annule l’opération et revient à l’affichage de la page « Enregistrer un apprenant - vierge »

Diagramme d’activité :

![Activite_ajouter_apprenant](/Enterprise-Architect/AD%20Ajouter%20un%20apprenant.bmp)

Diagramme de séquence :

![Sequence_ajouter_apprenant](/Enterprise-Architect/SD%20Ajouter%20un%20apprenant.bmp)

#### 2.2.2 Use Case : supprimer un apprenant

Acteur : formateur

Précondition : le système affiche la page « Liste des apprenants »

Postcondition : l’apprenant est supprimé

Scénario nominal :

1.	Le formateur clique sur l’icône de suppression
2.	Le système affiche un pop-up de confirmation avec les nom et prénom de l’apprenant
3.	Le formateur clique sur le bouton « Ok »
4.	Le système supprime l’apprenant et affiche un pop-up indiquant que l’opération s’est bien déroulée

Scénario exceptionnel : 

3E1 Le formateur clique sur le bouton « Annuler »
1.	Le système annule la suppression et revient à l’affichage de la page « Liste des apprenants »

Diagramme d’activité :

![Activite_supprimer_apprenant](/Enterprise-Architect/AD%20Supprimer%20un%20apprenant.bmp)

Diagramme de séquence :

![Sequence_supprimer_apprenant](/Enterprise-Architect/SD%20Supprimer%20un%20apprenant.bmp)

#### 2.2.3 Use Case : déterminer le nombre de groupes

Acteur : formateur

Précondition : le système affiche la page « Gestion des groupes – vierge »

Postcondition : le système affiche la page « Liste des groupes »

Scénario nominal :

1.	Le formateur saisi le nombre de groupes souhaité
2.	Le formateur clique sur le bouton « Valider »
3.	Le système génère la liste des groupes
4.	Le système affiche la page « Liste des groupes »

Diagramme d’activité : 

![Activite_nombre_groupes](/Enterprise-Architect/AD%20Déterminer%20le%20nombre%20de%20groupes.bmp)

Diagramme de séquence :

![Sequence_nombre_groupes](/Enterprise-Architect/SD%20Déterminer%20le%20nombre%20de%20groupes.bmp)

### 2.3 Maquettage

#### Enregistrer un apprenant - vierge

![Enregistrer_un_apprenant-vierge](/Figma/Enregistrer%20un%20apprenant%20-%20vierge.png)

#### Enregistrer un apprenant - rempli

![Enregistrer_un_apprenant-rempli](/Figma/Enregistrer%20un%20apprenant%20-%20rempli.png)

#### Enregistrer un apprenant - pop-up d'information

![Enregistrer_un_apprenant-pop-up_information](/Figma/Enregistrer%20un%20apprenant%20-%20pop-up.png)

#### Gestion des groupes - vierge

![Gestion_des_groupes-vierge](/Figma/Gestion%20des%20groupes%20-%20vierge.png)

#### Gestion des groupes - rempli

![Gestion_des_groupes-rempli](/Figma/Gestion%20des%20groupes%20-%20rempli.png)

#### Liste des groupes

![Liste_des_groupes](/Figma/Liste%20des%20groupes.png)

#### Liste des apprenants

![Liste_des_apprenants](/Figma/Liste%20des%20apprenants.png)

#### Liste des apprenants - pop-up de confirmation

![Liste_des_apprenants-pop-up_confirmation](/Figma/Liste%20des%20apprenants%20-%20pop-up%20de%20confirmation.png)

#### Liste des apprenants - pop-up d'information

![Liste_des_apprenants-pop-up_information](/Figma/Liste%20des%20apprenants%20-%20pop-up%20d'information.png)

#### Menu

![Menu](/Figma/Menu.png)

## 3 Conception

### 3.1 Diagramme de classe

![Diagramme_classe_model](/Enterprise-Architect/Diagramme%20de%20classe%20model.png)

### 3.2 Détermination des couches

•	Controller, qui va être la porte d’entrée du Frontend pour communiquer avec l’API.

•	Service, qui va regrouper toute la logique métier, et qui va assurer la communication entre le Controller et le Repository.

•	Repository, qui va avoir la charge de récupérer les données, dans notre cas, depuis la base de données.

•	Models, qui va regrouper toutes les objets métiers nécessaires au fonctionnement de l’API.

•	Mapper, qui va assurer la conversion des objets DTO en objets Models et inversement.

•	DTO (Data Transfer Object), qui va permettre le transport des données à travers les couches, sans exposer les Models.

### 3.3 Diagramme de package

![Diagramme_package](/Enterprise-Architect/Diagramme%20de%20Package.bmp)

### 3.4 Classes et interfaces en détail

![Diagramme_classe](/Enterprise-Architect/Diagramme%20de%20classe.bmp)

## 4 Dase de données

Méthode Merise

### 4.1 Dictionnaire des données

Entités|Mnémonique|Signification|Type(longueur)|Contraintes|
|---|---|---|---|---|
|learner|id_learner|identifiant de l'apprenant|Bigint|Identifiant, auto-incrémenté|
|learner|firstname|Prénom de l'apprenant|Text|Facultatif|
|learner|lastname|Nom de l'apprenant|Text|Obligatoire|
|group_learners|id_group|Identifiant du groupe|Bigint|Identifiant, auto-incrémenté|
group_learners|name|Nom du groupe|Text|Obligatoire|

### 4.2 Règles de gestion

1 learner est contenu dans 0 ou 1 groupe

1 groupe contient 1 ou plusieurs learner

### 4.3 Modèle conceptuel des données (MCD)

![MCD](/Looping/Modele_conceptuel_des_donnees.png)

### 4.4 Modèle logique des données (MLD)

![MLD](/Looping/Modele_logique_des_donnees.png)