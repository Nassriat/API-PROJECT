# API-PROJECT
 Créer une BDD et la remplir des données venant d'une API
 
# Table of Contents
 * [SUPERHEROS](#SUPERHEROS)
    - [Info API SUPERHEROS](#Info-API-SUPERHEROS)
    - [Dictionnaire des données SUPERHEROS](#Dictionnaire-des-données-SUPERHEROS)
    - [Création des tables SUPERHEROS](#Création-des-tables-SUPERHEROS) 
    - [Schéma de base de données SUPERHEROS](#Schéma-de-base-de-données-SUPERHEROS)
    - [Remplissage des tables SUPEREHEROS](#Remplissage-des-tables-SUPERHEROS)
    - [Exemples de requêtes SQL SUPERHEROS](#Exemple-de-requetes-SQL-SUPERHEROS)
 * [MARVEL](#MARVEL)
    - [Info API MARVEL](#Info-API-MARVEL)
    - [Dictionnaire des données MARVEL](#Dictionnaire-des-données-MARVEL)
    - [Création des tables MARVEL](#Création-des-tables-MARVEL)
    - [Schéma de base de données MARVEL](#Schéma-de-base-de-données-MARVEL)
    - [Remplissage des tables MARVEL](#Remplissage-des-tables-MARVEL)
    - [Exemples de requêtes SQL MARVEL](#Exemple-de-requetes-SQL-MARVEL)
 * [PAYS](#PAYS)
    - [Info API PAYS](#Info-API-PAYS)
    - [Dictionnaire des données PAYS](#Dictionnaire-des-données-PAYS)
    - [Création des tables PAYS](#Création-des-tables-PAYS)
    - [Schéma de base de données PAYS](#Schéma-de-base-de-données-PAYS)
    - [Remplissage des tables PAYS](#Remplissage-des-tables-PAYS)
    - [Exemples de requêtes SQL PAYS](#Exemple-de-requetes-SQL-PAYS)
 
 
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
 
## Schéma de base de données SUPERHEROS

Aprés avoir créer toutes les tables, nous pouvons aller sur SQL SERVER afin de visualiser le schéma de données.

![SCHEMA BDD](https://user-images.githubusercontent.com/75089728/103443914-e0af7300-4c63-11eb-9c1a-14cf9f76f0f8.PNG)

## Remplissage des tables SUPERHEROS
**Étape 4** : remplir les tables à partir de Python et les visualiser sur SQL SERVER 

Apres avoir rempli les tables à partir de Python, nous pouvons desormais les visualiser sur SQL

1) **PERSONNAGE**

![SQL PERSONNAGE](https://user-images.githubusercontent.com/75089728/103444141-00479b00-4c66-11eb-90e0-bf5f191e7ae4.PNG)

2) **APPARENCE**

![SQL APPEARANCE](https://user-images.githubusercontent.com/75089728/103444138-f7ef6000-4c65-11eb-92d7-cc4d8ca56436.PNG)

3) **POWERSTATS**

![SQL POWERSTATS](https://user-images.githubusercontent.com/75089728/103444154-210ff080-4c66-11eb-99cb-07a2c4027c67.PNG)

4) **BIOGRAPHY**

![SQL BIOGRAPHY](https://user-images.githubusercontent.com/75089728/103444155-240ae100-4c66-11eb-882e-4ae17b6ab6b9.PNG)

5) **CONNECTION**

![SQL CONNECTION](https://user-images.githubusercontent.com/75089728/103444158-29682b80-4c66-11eb-9246-1bfcd43045ba.PNG)

6) **WORK**

![SQL WORK](https://user-images.githubusercontent.com/75089728/103444163-2f5e0c80-4c66-11eb-92c3-646fa7204b45.PNG)

7) **IMAGE**

![SQL IMAGE](https://user-images.githubusercontent.com/75089728/103444164-37b64780-4c66-11eb-958d-69a9600b32ae.PNG)

## Exemples de requêtes SQL SUPERHEROS

Pour tester notre base de données, on a effectué des requetes SQL à partir de la database.

1) **Tous les Superheros et leur nom complet qui sont de race humaine**

![REQUETE tous les SH FN ID - de race humaine](https://user-images.githubusercontent.com/75089728/103447130-537e1580-4c87-11eb-9a9b-20ca1d9e1256.PNG)

2) **Tous les Superheros qui ont une intelligence comprise entre 60 et 70**

![REQUETE tous les SH qui ont une intelligence comprise entre 60 et 70](https://user-images.githubusercontent.com/75089728/103447132-54af4280-4c87-11eb-8acb-12cbf7a76d4b.PNG)

3) **Top 100 des Superheros par ordre alphabétique ayant le maximum de combat**

![Top 100 des superheros par ordre alphabetique et le maximu de combat effectué](https://user-images.githubusercontent.com/75089728/103447139-655fb880-4c87-11eb-893f-b6f3ddb7debe.PNG)

4) **Noms des Superheros qui n'ont pas de cheveux "Hair_color = No Hair"**

![Nom des SH qui n'ont pas de cheveux No_Hair](https://user-images.githubusercontent.com/75089728/103447146-77415b80-4c87-11eb-9f73-074b5b1733f6.PNG)

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

## Schéma de base de données MARVEL

Aprés avoir créer toutes les tables, nous pouvons aller sur SQL SERVER afin de visualiser le schéma de données.

![SCHEMA BDD](https://user-images.githubusercontent.com/75089728/103443917-e73dea80-4c63-11eb-848c-0580e3cb7fb6.PNG)

## Remplissage des tables MARVEL
**Étape 4** : remplir les tables à partir de Python et les visualiser sur SQL SERVER 

Apres avoir rempli les tables à partir de Python, nous pouvons desormais les visualiser sur SQL

1) **CHARACTERS**

![SQL CHARACTERS](https://user-images.githubusercontent.com/75089728/103444329-c5466700-4c67-11eb-8fda-e1eeaf86ee0b.PNG)

2) **COMICS**

![SQL COMICS](https://user-images.githubusercontent.com/75089728/103444330-c7102a80-4c67-11eb-90fa-152d19b179d6.PNG)

3) **SERIES**

![SQL SERIES](https://user-images.githubusercontent.com/75089728/103444343-da22fa80-4c67-11eb-98e4-3c9796dcdde1.PNG)

4) **STORIES**

![SQL STORIES](https://user-images.githubusercontent.com/75089728/103444344-dd1deb00-4c67-11eb-8631-eef9fc80f4c7.PNG)

5) **EVENTS**

![SQL EVENTS](https://user-images.githubusercontent.com/75089728/103444366-063e7b80-4c68-11eb-9baf-ce03e6905456.PNG)

6) **DESCRIPTIONS**

![SQL DESCRIPTION](https://user-images.githubusercontent.com/75089728/103444373-1191a700-4c68-11eb-9c04-96e0e8ffdbe6.PNG)

7) **URL**

![SQL URL](https://user-images.githubusercontent.com/75089728/103444379-1d7d6900-4c68-11eb-9f73-b8c403424d44.PNG)

8) **THUMBNAIL**

![SQL THUMBNAIL](https://user-images.githubusercontent.com/75089728/103444349-e6a75300-4c67-11eb-9e21-4abcc47d7f90.PNG)

9) **ITEMS COMICS**

![SQL ITEMS COMICS](https://user-images.githubusercontent.com/75089728/103444389-2cfcb200-4c68-11eb-9153-bb531176ce9d.PNG)

10) **ITEMS EVENTS**

![SQL ITEMS EVENTS](https://user-images.githubusercontent.com/75089728/103444459-ac8a8100-4c68-11eb-8eb1-15542f28bdf1.PNG)

11) **ITEM SERIES**

![SQL ITEMS SERIES](https://user-images.githubusercontent.com/75089728/103444393-3128cf80-4c68-11eb-9a1a-f1da94859bbd.PNG)

12) **ITEM STORIES**

![SQL ITEMS STORIES](https://user-images.githubusercontent.com/75089728/103444395-338b2980-4c68-11eb-8e65-ddc956053304.PNG)

## Exemples de requêtes SQL MARVEL

Pour tester notre base de données, on a effectué des requetes SQL à partir de la database.

1)
2)
3)


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

Comme vu precedemment, nous avons au total huit tables daans la database **PAYS** (la database a été crée dans SQL avant de pouvoir l'utiliser).
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

## Schéma de base de données PAYS

Aprés avoir créer toutes les tables, nous pouvons aller sur SQL SERVER afin de visualiser le schéma de données.

![SCHEMA_BDD](https://user-images.githubusercontent.com/75089728/103443920-eefd8f00-4c63-11eb-9b20-0496e2fda441.PNG)

## Remplissage des tables PAYS
**Étape 4** : remplir les tables à partir de Python et les visualiser sur SQL SERVER 

Apres avoir rempli les tables à partir de Python, nous pouvons desormais les visualiser sur SQL

1) **PAYS**

![SQL_PAYS](https://user-images.githubusercontent.com/75089728/103444559-831e2500-4c69-11eb-8fd5-9ce2cad079be.PNG)

2) **GEOGRAPHY**

![SQL_GEOGRAPHY](https://user-images.githubusercontent.com/75089728/103444564-86191580-4c69-11eb-816b-401f689beabb.PNG)

3) **REGIONAL BLOCS**

![SQL_REGIONAL_BLOCS](https://user-images.githubusercontent.com/75089728/103444560-844f5200-4c69-11eb-906f-668a89a042e1.PNG)

4) **ORIGIN**

![SQL_ORIGIN](https://user-images.githubusercontent.com/75089728/103444566-874a4280-4c69-11eb-8c7e-0d45c1f8a0a9.PNG)

5) **SPECIAL CODES**

![SQL_SPECIAL_CODES](https://user-images.githubusercontent.com/75089728/103444561-844f5200-4c69-11eb-90a7-b8e71d7ad43e.PNG)

6) **LANGUAGES**

![SQL_LANGUAGES](https://user-images.githubusercontent.com/75089728/103444565-86b1ac00-4c69-11eb-82bb-1fd58bd514dd.PNG)

7) **CURRENCIES**

![SQL_CURRENCIES](https://user-images.githubusercontent.com/75089728/103444563-85807f00-4c69-11eb-8a96-b95244525a91.PNG)

8) **TRANSLATION**

![SQL_TRANSLATION](https://user-images.githubusercontent.com/75089728/103444562-84e7e880-4c69-11eb-85c9-caf84ffe60b4.PNG)

## Exemples de requêtes SQL PAYS

Pour tester notre base de données, on a effectué des requetes SQL à partir de la database.

1)
2)
3)


---
 
 
