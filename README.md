# API-PROJECT
 Créer une BDD et la remplir des données venant d'une API
 
# Table of Contents
 * [SUPERHEROS](#SUPERHEROS)
    - [Info API SUPERHEROS](#Info-API-SUPERHEROS)
    - [Dictionnaire des données SUPERHEROS](#Dictionnaire-des-données-SUPERHEROS)
    - [Création des tables SUPERHEROS](#Création-des-tables-SUPERHEROS) 
    - [Schéma de base de données SUPERHEROS](#Schéma-de-base-de-données-SUPERHEROS)
 * [MARVEL](#MARVEL)
    - [Info API MARVEL](#Info-API-MARVEL)
    - [Dictionnaire des données MARVEL](#Dictionnaire-des-données-MARVEL)
    - [Création des tables MARVEL](#Création-des-tables-MARVEL)
    - [Schéma de base de données MARVEL](#Schéma-de-base-de-données-MARVEL)
 * [PAYS](#PAYS)
    - [Info API PAYS](#Info-API-PAYS)
    - [Dictionnaire des données PAYS](#Dictionnaire-des-données-PAYS)
    - [Création des tables PAYS](#Création-des-tables-PAYS)
    - [Schéma de base de données PAYS](#Schéma-de-base-de-données-PAYS)
 
 
 ## SUPERHEROS
 ![Capture](https://user-images.githubusercontent.com/75089728/103438089-7c72bc00-4c2f-11eb-9e75-8ab1dadc387e.PNG)
 
 ### Info API SUPERHEROS
 Endpoint utilisé : **`https://superheroapi.com/api/_access-token_/search/name`**
 
 **Étape 1** : récuperer l' _access.token_ en se connectant avec un compte FACEBOOK.
 
 Pour cette API, il y a 2 manieres d'obtenir les données :
 + A partir de l'**ID** 
 + A partir du **nom** 

 Dans notre cas, pour recuperer un maximum de données, nous avons cherché à partir du nom : **`https://superheroapi.com/api/_acces-token_/search/a`**  
 
 Nous avons fait **`search/a`** car logiquement, plusieurs Superheros ont la lettre **'a'** dans le prenom.
 
 ## Dictionnaire des données SUPERHEROS
 
 **Étape 2** : récuperer les données sous forme JSON Object et création des differents dictionnaires
 
 En transformant le code en _Python JSON Object_ nous obtenons des données structurées (un extrait):
 
 ![JSON SUPERHEROS](https://user-images.githubusercontent.com/75089728/103440037-abdef400-4c42-11eb-8bcc-2aa68723ddf6.PNG)
 
 A partir de cela, nous avons donc fait la liste des tables que nous allons creer sur SQL : 
 
![DIFFERENTES TABLES SUPERHEROS](https://user-images.githubusercontent.com/75089728/103440295-8ce16180-4c44-11eb-81a6-787880ef5d36.PNG)

## Création des tables SUPERHEROS 

**ÉTAPE 3** : Créer les differentes tables à partir du python dans SQL

Comme vu precedemment, nous avons au total sept tables daans la database **SUPERHEROS** (la database a été créé dans SQL avant de pouvoir l'utiliser).
Nous allons nous baser sur une seule table **APPEARENCE** pour expliquer plus en detail.

Tous d'abord, il faut connecter *Python* à *SQL SERVER* en utilisante la librairie **`pyodbc`**.
``` python
import pyodbc
conn = pyodbc.connect('Driver={SQL Server};'
                      'Server=ServerName;'
                      'Database=SUPERHEROS;'
                      'Trusted_Connection=yes;')
```

Ensuite, il faut faire la requête permettant de créer la table **APPEARENCE** dans *SQL SERVER*

![CODE appearance](https://user-images.githubusercontent.com/75089728/103443264-a8a53180-4c5d-11eb-8fd4-0c24766395e2.PNG)

Nous avons créé cette méthode pour toutes les tables.
 
##Schéma de base de données SUPERHEROS

Aprés avoir créer toutes les tables, nous pouvons aller sur SQL SERVER afin de visualiser le schéma de données.

![SCHEMA BDD](https://user-images.githubusercontent.com/75089728/103443914-e0af7300-4c63-11eb-9c1a-14cf9f76f0f8.PNG)


 ---
 
 ## MARVEL
 ![PAGE DE GARDE](https://user-images.githubusercontent.com/75089728/103438093-84caf700-4c2f-11eb-902c-80720f80507e.PNG)
 
 ### Info API_MARVEL 
 Endpoint utilisé : **`http(s)://gateway.marvel.com/`**
 
 **Étape 1** : récuperer l' _access.token_ en se connectant avec un compte MARVEL.
 
 Apres avoir creer le compte, il faut utiliser les deux clés ( public key et private key ) pour obtenir deux autres parametres obligatoires :
 + **ts** : correspond au premier chiffre de la public key
 + **hash** : coorespond au codage md5(_ts_ +  _public key_ + _private key_ )
 
 Cela va nous donner pour les parametres : **```params={"apikey":"_public key_","_ts"_: "_ts_","hash": "_hash_"}```**
 
 Pour cette API, il y a plusieurs manieres d'obtenir les données des Superheros :
 + A partir de **characters** 
 + A partir du **comics**
 + A partir de **creators** 
 + A partir du **events**
 + A partir de **stories** 
 
 Pour recuperer les données, nous avons utiliser : **`http://gateway.marvel.com/v1/public/characters`**
 
 Il faut savoir que le nombre de données est limité à 100.
 
  ## Dictionnaire des données MARVEL
 
 **Étape 2** : récuperer les données sous forme JSON Object et création des differents dictionnaires
 
 En transformant le code en _Python JSON Object_ nous obtenons des données structurées (un extrait):
 
![JSON MARVEL](https://user-images.githubusercontent.com/75089728/103440036-ab465d80-4c42-11eb-8f7c-9a2c630ccd32.PNG)
 
 A partir de cela, nous avons donc fait la liste des tables que nous allons creer sur SQL : 

![LES DIFFRERENTES TABLES MARVEL](https://user-images.githubusercontent.com/75089728/103440297-936fd900-4c44-11eb-8bf6-b8bda045faff.PNG)

## Création des tables MARVEL 

**ÉTAPE 3** : Créer les differentes tables à partir du python dans SQL

Comme vu precedemment, nous avons au total douze tables daans la database **MARVEL** (la database a été créé dans SQL avant de pouvoir l'utiliser).
Nous allons nous baser sur une seule table **CHARACTERS** pour expliquer plus en detail.

Tous d'abord, il faut connecter *Python* à *SQL SERVER* en utilisante la librairie **`pyodbc`**.
``` python
import pyodbc
conn = pyodbc.connect('Driver={SQL Server};'
                      'Server=ServerName;'
                      'Database=MARVEL;'
                      'Trusted_Connection=yes;')
```

Ensuite, il faut faire la requête permettant de créer la table **CHARACTERS** dans *SQL SERVER*

![CODE characters](https://user-images.githubusercontent.com/75089728/103443506-384bdf80-4c60-11eb-9944-4d0b3821d1fb.PNG)

Nous avons créé cette méthode pour toutes les tables.

##Schéma de base de données MARVEL

Aprés avoir créer toutes les tables, nous pouvons aller sur SQL SERVER afin de visualiser le schéma de données.

![SCHEMA BDD](https://user-images.githubusercontent.com/75089728/103443917-e73dea80-4c63-11eb-848c-0580e3cb7fb6.PNG)


 ---
 
## PAYS
![PAGE DE GARDE](https://user-images.githubusercontent.com/75089728/103438105-96ac9a00-4c2f-11eb-812f-5a3d3525d062.PNG)

## Info API_PAYS

 Endpoint utilisé : **`http(s)://restcountries.eu/rest/v2/all`**
 
 **Etape 1** : pas besoin de créer un compte ou avoir une _public key_.
 
 Pour récuperer tous les données, nous avons utilisé le Endpoint ci dessus.
 
 ## Dictionnaire des données PAYS
 
 **Étape 2** : récuperer les données sous forme JSON Object et création des differents dictionnaires
 
 En transformant le code en _Python JSON Object_ nous obtenons des données structurées (un extrait):
 
![JSON_PAYS](https://user-images.githubusercontent.com/75089728/103440038-ad102100-4c42-11eb-9bfb-404461698203.PNG)
 
 A partir de cela, nous avons donc fait la liste des tables que nous allons creer sur SQL : 

![CODE_DIFFERENTES_TABLES PAYS](https://user-images.githubusercontent.com/75089728/103440301-a08cc800-4c44-11eb-968a-5aa8db618e56.PNG)

## Création des tables PAYS

**ÉTAPE 3** : Créer les differentes tables à partir du python dans SQL

Comme vu precedemment, nous avons au total dix tables daans la database **PAYS** (la database a été crée dans SQL avant de pouvoir l'utiliser).
Nous allons nous baser sur une seule table **GEOGRAPHY** pour expliquer plus en detail.

Tous d'abord, il faut connecter *Python* à *SQL SERVER* en utilisante la librairie **`pyodbc`**.
``` python
import pyodbc
conn = pyodbc.connect('Driver={SQL Server};'
                      'Server=ServerName;'
                      'Database=PAYS;'
                      'Trusted_Connection=yes;')
```

Ensuite, il faut faire la requête permettant de créer la table **GEOGRAPHY** dans *SQL SERVER*

![CODE geography](https://user-images.githubusercontent.com/75089728/103443508-3da92a00-4c60-11eb-8a47-6c835f5d49c6.PNG)

Nous avons créé cette méthode pour toutes les tables.

##Schéma de base de données PAYS

Aprés avoir créer toutes les tables, nous pouvons aller sur SQL SERVER afin de visualiser le schéma de données.

![SCHEMA_BDD](https://user-images.githubusercontent.com/75089728/103443920-eefd8f00-4c63-11eb-9b20-0496e2fda441.PNG)

---
 
 
