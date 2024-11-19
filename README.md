# Projet de Machine Learning - Recommandation de Playlist Spotify

## Description du projet

Dans le cadre du module **Techniques d’Apprentissage Artificiel** en Master 1 Informatique, nous avons réalisé un projet d'apprentissage automatique consistant à créer un système de recommandation basé sur les préférences musicales des utilisateurs. Le but est de prédire si un utilisateur appréciera une chanson dans une playlist donnée, en fonction des caractéristiques audio des morceaux.

### Objectifs

1. **Collecte et préparation des données :** Extraire des informations sur des morceaux de musique à partir de playlists Spotify, puis les transformer en un format exploitable pour un modèle de machine learning.
2. **Analyse des caractéristiques importantes :** Utiliser un modèle de Random Forest pour identifier les caractéristiques audio les plus pertinentes pour la prédiction.
3. **Construction du modèle de prédiction :** Créer un modèle de classification basé sur l'algorithme K-Nearest Neighbors (KNN) pour prédire si un utilisateur aimera une chanson ou non.
4. **Évaluation du modèle :** Tester et évaluer le modèle sur des playlists de test.

## Structure du projet

Le projet se compose de plusieurs scripts Python répartis en deux fichiers principaux : 

### 1. `model.py`

Ce fichier contient le code principal pour la création et l'entraînement du modèle de machine learning, ainsi que la prédiction des chansons aimées par un utilisateur dans une playlist donnée.

**Fonctionnalités principales :**
- Chargement des données d'entraînement et de test à partir de fichiers CSV.
- Normalisation des caractéristiques audio des morceaux avec `MinMaxScaler`.
- Séparation des données en ensembles d'entraînement et de test.
- Utilisation de `RandomForestClassifier` pour déterminer les caractéristiques importantes.
- Entraînement du modèle K-Nearest Neighbors (KNN) pour prédire les morceaux aimés.
- Prédiction des chansons aimées dans une playlist de test et affichage des résultats.

### 2. `create_data.py`

Ce fichier permet de collecter les données de playlists Spotify et de les préparer pour l'entraînement du modèle. Il utilise la fonction `playlist_to_dataframe` pour extraire les informations des playlists.

**Fonctionnalités principales :**
- Extraction des playlists "aimées" et "non aimées" à partir de Spotify.
- Création d'un DataFrame avec les caractéristiques des morceaux et l'étiquette associée (1 = aimé, 0 = non aimé).
- Sauvegarde des données sous forme de fichiers CSV pour être utilisés par le modèle.

### 3. Dossiers et fichiers :

- **`data/train_data.csv`** : Jeu de données d'entraînement contenant les caractéristiques audio des morceaux et l'étiquette de "like" ou "dislike".
- **`data/test_data.csv`** : Jeu de données de test contenant les caractéristiques audio des morceaux à évaluer par le modèle.

## Installation

1. Clonez le repository :

```bash
git clone https://github.com/your-username/spotify-recommendation-project.git
cd spotify-recommendation-project
```

2. Installez les dépendances nécessaires :

```bash
pip install -r requirements.txt
```

## Utilisation

### Entraînement et Évaluation du modèle

1. **Préparation des données :**
   - Exécutez `create_data.py` pour récupérer et préparer les playlists de test et d'entraînement depuis Spotify.
   - Le script sauvegardera les fichiers CSV nécessaires dans le dossier `data/`.

2. **Entraînement du modèle :**
   - Exécutez `model.py` pour entraîner le modèle de machine learning et obtenir les résultats sur les playlists de test.

```bash
python model.py
```

3. **Affichage des résultats :**
   - Le modèle affichera la précision de la prédiction et une estimation du nombre de morceaux que l'utilisateur pourrait aimer dans la playlist de test.

### Détails du Code

#### Partie 1 : Préparation des données

Le fichier `model.py` commence par charger les données à partir de fichiers CSV, puis il effectue une normalisation des caractéristiques audio des morceaux à l'aide de `MinMaxScaler`. Les caractéristiques sont extraites des colonnes comme `danceability`, `energy`, `loudness`, etc.

#### Partie 2 : Sélection des caractéristiques importantes

Un modèle de Random Forest est utilisé pour identifier les caractéristiques les plus importantes pour la prédiction. Les caractéristiques comme `mode`, `key`, et `time_signature` ont été jugées peu importantes et ne sont donc pas retenues pour la suite de l'entraînement du modèle.

#### Partie 3 : Entraînement du modèle KNN

Un modèle K-Nearest Neighbors (KNN) est utilisé pour prédire si un utilisateur aimera un morceau de musique ou non. Le nombre de voisins (k) est fixé à 4.

#### Partie 4 : Prédiction et estimation

Le modèle prédit les morceaux que l'utilisateur pourrait aimer dans une playlist donnée, et affiche un pourcentage d'objets aimés, ainsi que des détails sur chaque morceau.

## Exemples d'Exécution

Voici un exemple d'exécution du script `model.py` avec une sortie typique :

```bash
Score du modèle : 0.85 .
Vous allez aimer 30/50 chansons.
Pourcentage de chances que vous aimiez cette playlist est de 60.0 %.
Details des chansons aimées et ou pas ci-dessous :
             name               artist  liked
0    Song Name 1      Artist Name 1       1
1    Song Name 2      Artist Name 2       0
...
```

## Contributions

Si vous souhaitez contribuer à ce projet, n'hésitez pas à soumettre une pull request ou à ouvrir une issue.

## Auteurs

- [Aaron Amani]
- [Wilhem Liban]

## Licence

Ce projet est sous licence MIT - voir le fichier [LICENSE](LICENSE) pour plus de détails.