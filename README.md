# Suppression de lignes dupliquées dans des fichiers CSV avec Azure Data Factory

## Description du Projet
L'objectif de ce projet est de montrer comment j'ai utilisé Azure Data Factory (ADF) pour consolider plusieurs fichiers CSV stockés dans Azure Blob Storage, éliminer les doublons en fonction de la colonne ID, puis sauvegarder les données nettoyées. Ce processus automatisé est particulièrement utile pour centraliser et dédupliquer des données provenant de différentes sources ou partitions.

##Structure du Projet
Étapes du Flux de Travail
### Création du Linked Service :
J'ai commencé par configurer un Linked Service pointant vers Azure Blob Storage, où se trouvent mes fichiers CSV d’origine. Cette connexion permet à ADF d’accéder aux fichiers source et de les manipuler.

##Création des Datasets :
Pour ce projet, j'ai créé un Dataset pour chaque fichier CSV dans Azure Blob Storage. Cependant, dans une utilisation plus générale, il est possible de créer un seul Dataset en passant les noms des fichiers en tant que paramètres, ce qui rend le processus plus dynamique et flexible.

## Conception du Data Flow :
J'ai mis en place un Data Flow pour automatiser le traitement des fichiers CSV, avec les étapes suivantes :
- Ajout des Sources : 
Chaque fichier CSV est ajouté comme source distincte dans le Data Flow.
- Concaténation des Fichiers : 
J'ai ensuite concaténé tous les fichiers source pour obtenir un seul ensemble de données consolidé.
- Élimination des Duplicatas : 
L’opération de concaténation crée potentiellement des lignes dupliquées. Pour les supprimer, j'ai appliqué une agrégation en réalisant un Group By basé sur la colonne ID.
- Tri des Données : 
Après l'agrégation, j'ai trié les données pour faciliter l’analyse et la lisibilité (facultatif).

### Stockage des Données Nettoyées :
Enfin, j'ai sauvegardé les données dédupliquées et triées dans Azure Blob Storage, prêtes à être utilisées pour d’autres traitements ou analyses.

## Fonctionnalités et Avantages
- Automatisation et Orchestration : 
En utilisant Data Factory, j'ai pu automatiser le processus de déduplication, ce qui réduit les efforts manuels et les risques d’erreurs.
- Scalabilité :
Azure Data Factory est conçu pour manipuler des volumes importants de données, ce qui rend cette solution idéale pour des charges de travail en production.
- Paramétrisation Flexible :
En passant par des paramètres, il est possible d'adapter ce pipeline à divers ensembles de données ou à différents noms de fichiers, rendant le projet réutilisable et adaptable.
Cas d'Utilisation et Extensions

**Ce projet peut être étendu pour :**
Traiter des fichiers provenant de différentes sources.
Appliquer d’autres règles de nettoyage et de transformation de données.
Intégrer d’autres types de stockage dans Azure, comme SQL Database ou Data Lake Storage, en ajoutant les Linked Services appropriés.
