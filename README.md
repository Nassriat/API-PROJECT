# API-PROJECT
 Créer une BDD et la remplir des données venant d'une API
 
# Table of Contents
 * [SUPERHEROS](#SUPERHEROS)
    - [Info API SUPERHEROS](#Info-API-SUPERHEROS)
    - [Dictionnaire des données SUPERHEROS](#Dictionnaire-des-données-SUPERHEROS)
 * [MARVEL](#MARVEL)
    - [Info API MARVEL](#Info-API-MARVEL)
    - [Dictionnaire des données MARVEL](#Dictionnaire-des-données-MARVEL)
 * [PAYS](#PAYS)
    - [Info API PAYS](#Info-API-PAYS)
    - [Dictionnaire des données PAYS](#Dictionnaire-des-données-PAYS)
 
 
 ## SUPERHEROS
 ![Capture](https://user-images.githubusercontent.com/75089728/103438089-7c72bc00-4c2f-11eb-9e75-8ab1dadc387e.PNG)
 
 ### Info API SUPERHEROS
 Endpoint utilisé : **`https://superheroapi.com/api/_access-token_/search/name`**
 
 **Étape 1** : récuperer l' _access.token_ en se connectant avec un compte FACEBOOK.
 
 Pour cette API, il y a 2 manieres d'obtenir les données :
 + A partir de l'**ID** 
 + A partir du **nom** 

 Dans notre cas, pour recuperer un maximu de données, nous avons cherché à partir du nom : **`https://superheroapi.com/api/_acces-token_/search/a`**  
 
 Nous avons fait **`search/a`** car logiquement, plusieurs Superheros ont la lettre **'a'** dans le prenom.
 
 ## Dictionnaire des données SUPERHEROS
 
 **Étape 2** : récuperer les données sous forme JSON Object et création des differents dictionnaires
 
 En transformant le code en _Python JSON Object_ nous obtenons des données structurées (un extrait):
 
 ![JSON SUPERHEROS](https://user-images.githubusercontent.com/75089728/103440037-abdef400-4c42-11eb-8bcc-2aa68723ddf6.PNG)
 
 A partir de cela, nous avons donc fait la liste des tables que nous allons creer sur SQL : 


 
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
 ![JSON MARVEL](https://user-images.githubusercontent.com/75089728/103440036-ab465d80-4c42-11eb-8f7c-9a2c630ccd32.PNG)
 
  ## Dictionnaire des données MARVEL
 
 **Étape 2** : récuperer les données sous forme JSON Object et création des differents dictionnaires
 
 En transformant le code en _Python JSON Object_ nous obtenons des données structurées (un extrait):
 
![JSON MARVEL](https://user-images.githubusercontent.com/75089728/103440036-ab465d80-4c42-11eb-8f7c-9a2c630ccd32.PNG)

 
 A partir de cela, nous avons donc fait la liste des tables que nous allons creer sur SQL : 


 ---
 
## PAYS
![PAGE DE GARDE](https://user-images.githubusercontent.com/75089728/103438105-96ac9a00-4c2f-11eb-812f-5a3d3525d062.PNG)

## Info API_PAYS

 Endpoint utilisé : **`http(s)://restcountries.eu/rest/v2/all`**
 
 **Etape 1** : pas besoin de créer un compte ou avoir une _public key_.
 
 Pour récuperer tous les données, nous avons utilisé le Endpoint ci dessus.
 
 ![JSON_PAYS](https://user-images.githubusercontent.com/75089728/103440038-ad102100-4c42-11eb-9bfb-404461698203.PNG)

 ## Dictionnaire des données SUPERHEROS
 
 **Étape 2** : récuperer les données sous forme JSON Object et création des differents dictionnaires
 
 En transformant le code en _Python JSON Object_ nous obtenons des données structurées (un extrait):
 
![JSON_PAYS](https://user-images.githubusercontent.com/75089728/103440038-ad102100-4c42-11eb-9bfb-404461698203.PNG)
 
 A partir de cela, nous avons donc fait la liste des tables que nous allons creer sur SQL : 


---
 
 
