# Analyse de données avec RStudio

Ce dossier contient le troisième projet du TP de bases de données avancées. Il porte sur l'analyse descriptive et l'analyse factorielle d'un jeu de données de 120 clients.

## Contenu du dossier

| Fichier | Description |
| --- | --- |
| `Projet D'analyse des donnees.Rproj` | Projet RStudio à ouvrir |
| `data.csv` | Jeu de données utilisé pour les analyses |
| `Guide_commandes.docx` | Guide pratique des commandes R et de leur interprétation |
| `Rapport_ACP_partie_A.docx` | Rapport de la partie A : ACP normalisée |
| `Rapport_AFC_partie_B.docx` | Rapport de la partie B : AFC |
| `Rapport_clustering_PARTIE_C_et_D.docx` | Rapports des parties C et D : K-means |

## Jeu de données

Le fichier `data.csv` contient 120 observations et 12 variables :

- 7 variables quantitatives : âge, ancienneté, heures de connexion, volume de données, dépenses, nombre de services et nombre de réclamations ;
- 5 variables associées à l'identification ou à des caractéristiques qualitatives : identifiant client, ville, catégorie socioprofessionnelle, type d'abonnement et satisfaction.

## Analyses réalisées

### Partie A - ACP normalisée

L'analyse en composantes principales utilise les sept variables quantitatives. Elle est réalisée après suppression des cinq lignes contenant des valeurs manquantes.

Les variables sont centrées et réduites afin que les différences d'échelle entre les FCFA, les mois, les heures et les autres unités n'affectent pas artificiellement les résultats.

### Partie B - AFC

L'analyse factorielle des correspondances étudie la relation entre :

- la catégorie socioprofessionnelle ;
- le niveau de satisfaction.

Le chi-deux et les profils lignes/colonnes permettent de vérifier si les écarts observés dans le tableau de contingence peuvent être interprétés avec prudence.

### Parties C et D - ACP/AFC avec K-means

- La partie C segmente les clients à partir des coordonnées obtenues par ACP ;
- la partie D regroupe les catégories socioprofessionnelles à partir des coordonnées obtenues par AFC ;
- la méthode de la silhouette permet d'évaluer les différents nombres de groupes.

L'identifiant client n'est jamais fourni à l'ACP ou à K-means : il s'agit d'une étiquette, pas d'une variable numérique pertinente.

## Prérequis

Ouvrez RStudio, puis ouvrez `Projet D'analyse des donnees.Rproj`. Installez les packages une seule fois :

```r
install.packages(c("FactoMineR", "factoextra", "cluster"))
```

Chargez-les à chaque nouvelle session :

```r
library(FactoMineR)
library(factoextra)
library(cluster)
```

## Exécution

Placez-vous dans le dossier du projet si nécessaire :

```r
setwd("chemin/vers/Rstudio-Projet3")
```

Puis chargez les données :

```r
donnees <- read.csv("data.csv",
                    na.strings = c("", "NA"),
                    encoding = "UTF-8")

dim(donnees)
```

Le résultat attendu est `120 12`, correspondant à 120 clients et 12 colonnes.

Pour comprendre chaque étape, les commandes, les valeurs attendues et les interprétations, consultez `Guide_commandes.docx`.
