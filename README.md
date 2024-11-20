# 🍺 Zythologue - Base De Données pour Amateurs de Bière

## 📜 Contexte du Projet
Découvrir et partager le monde de la Zythologie au-delà de la dégustation : explorer l'histoire derrière chaque brasserie, les ingrédients spécifiques, et les techniques de brassage.

Pour ce projet, j'ai créé une base de données relationnelle pour cataloguer et gérer des informations sur les bières, les brasseries, les utilisateurs, et bien plus encore. En utilisant PostgreSQL comme SGBD, j'ai structuré les données selon la méthode MERISE et les ai manipulées avec des requêtes SQL.

Pour faciliter le déploiement et la gestion de la base de données, j'ai utilisé Docker et docker-compose pour créer un environnement isolé et reproductible. DBeaver a été utilisé comme interface graphique pour interagir avec la base de données, permettant une gestion plus intuitive et visuelle des données.

J'ai effectué ce brief sur 3 jours : lundi, mardi et mercredi. L'objectif était de fournir une solution complète et fonctionnelle qui permet aux amateurs de bière de découvrir, classer, et partager leurs découvertes de manière structurée et efficace.

## 🚀 Procédure de Mise en Place

### Prérequis
- Docker et docker-compose installés
- PostgreSQL installé
- DBeaver ou un autre client SQL

### Étapes

1. **Cloner le dépôt GitHub**
  ```bash
  git clone <URL_DU_DEPOT>
  cd <NOM_DU_DEPOT>
  ```

2. **Configurer l'environnement Docker**
  - Assurez-vous que Docker et docker-compose sont installés.
  - Lancer les conteneurs Docker :
    ```bash
    docker-compose up -d
    ```

3. **Initialiser la base de données**
  - Importer le script SQL pour initialiser la base de données avec des données de test :
    ```bash
    docker exec -i <zythologue-db> psql -U <zythologue_user> -d <zythologue> < init.sql
    ```

4. **Accéder à la base de données avec DBeaver**
  - Configurer une nouvelle connexion PostgreSQL en utilisant les informations de connexion fournies dans le fichier `docker-compose.yml`.

5. **Vérifier les relations et les données**
  - Utiliser DBeaver pour explorer les tables et vérifier les relations entre elles.

## 🎓 Modalités Pédagogiques

### I. Méthode MERISE
Organise tes données à l'aide de :
- Un dictionnaire de données définissant les attributs de chaque entité.
- Des règles de gestion décrivant les contraintes et processus métiers.
- Un MCD (Modèle Conceptuel de Données) pour formaliser les entités et leurs relations.
- Un MLD (Modèle Logique de Données) pour préparer le passage au SGBD relationnel.
- Un MPD (Modèle Physique de Données) pour traduire le modèle en tables SQL.

### II. Structure de la Base de Données
- **Users** : Stocke les informations des utilisateurs, essentiel pour personnaliser l'expérience et gérer les accès.
  - Propriétés : `first_name`, `email`, `password`
- **Beers** : Contient les détails de chaque bière.
  - Propriétés : `id_beer`, `name`, `description`, `abv`
- **Categories** : Classifie les bières en différentes catégories pour simplifier la navigation et la découverte.
  - Propriétés : `name`
- **Breweries** : Répertorie les informations sur les brasseries pour enrichir la connaissance des utilisateurs sur l'origine des bières.
  - Propriétés : `name`, `country`
- **Reviews** : Les utilisateurs peuvent laisser des notes et commentaires sur les bières.
- **Favorites** : Permet aux utilisateurs de sauvegarder leurs bières préférées.
- **Photos** : Les utilisateurs peuvent voir des photos des bières.
  - Propriétés : `url`
- **Ingredients** : Détaille les ingrédients des bières.
  - Propriétés : `name`, `type`

### Diagramme MLD et MPD

![Diagramme MCD](./RESSOURCES/Diagramme%20MCD.png)
![Diagramme MLD MPD](./RESSOURCES/Diagramme%20MLD%20MPD.png)

### III. Requêtes SQL
- Lister les bières par taux d'alcool, de la plus légère à la plus forte.
- Afficher le nombre de bières par catégorie.
- Trouver toutes les bières d'une brasserie donnée.
- Lister les utilisateurs et le nombre de bières qu'ils ont ajoutées à leurs favoris.
- Ajouter une nouvelle bière à la base de données.
- Afficher les bières et leurs brasseries, ordonnées par pays de la brasserie.
- Lister les bières avec leurs ingrédients.
- Afficher les brasseries et le nombre de bières qu'elles produisent, pour celles ayant plus de 5 bières.
- Lister les bières qui n'ont pas encore été ajoutées aux favoris par aucun utilisateur.
- Trouver les bières favorites communes entre deux utilisateurs.
- Afficher les brasseries dont les bières ont une moyenne de notes supérieure à une certaine valeur.
- Mettre à jour les informations d'une brasserie.
- Supprimer les photos d'une bière en particulier.

### IV. Manipulations Avancées
- Écrire une procédure stockée permettant à un utilisateur de noter une bière. Si l'utilisateur a déjà noté cette bière, la note est mise à jour ; sinon, une nouvelle note est ajoutée.
- Écrire un déclencheur (trigger) pour vérifier que l'ABV (taux d'alcool) est compris entre 0 et 20 avant l'ajout de chaque bière.

## 📋 Contraintes
- Utiliser un SGBD relationnel en particulier : PostgreSQL (MongoDB et autres NoSQL non autorisés).
- Créer un environnement Docker avec docker-compose pour lancer PostgreSQL.
- Utiliser un compte SQL dédié pour gérer la base de données (root interdit).
- Chaque entrée de la base de données doit inclure une date de création et de modification pour le suivi.

## ⏳ Deadline
3 jours.

## 📝 Modalités d'Évaluation
Correction entre pairs. Les requêtes seront testées en local après importation de l’environnement Docker.

## 📦 Livrables
Un dépôt GitHub contenant :
- L'environnement Docker configuré avec docker-compose pour la base de données.
- Le dictionnaire des données.
- Les règles de gestion.
- MCD, MPD, et MLD détaillés.
- Un script SQL pour initialiser la base de données avec des données de test.
- Une documentation des requêtes dans le README.md.

## 🏆 Critères de Performance
- Facilité de mise en place de l’environnement.
- Exactitude des relations entre les tables.
- Fonctionnalité du trigger.
- Clarté et pertinence des requêtes documentées dans le README.md.
- Exécution sans erreur des requêtes.

## 📚 Ressources
- DBeaver pour une interface de gestion de base de données.
- Comprendre les bases de données
- Modèle Conceptuel des Données
- Langage SQL

## 👥 Groupes de Travail

Voici la répartition des groupes pour la reprise du projet :

- **Morgan POUSSON** ⇔ **Elena ZIANI**
- **Mounir GAOUI** ⇔ **Clavequin YAËL**
- **Maëva CORNIC** ⇔ **Lucio DELLA FELICE**
- **Emmanuel LINO KUBEMBA** ⇔ **Sergeï MILYUKOV**
- **Boris DUKO** ⇔ **Agnès CAPPELLO**
- **Jimmy NI** ⇔ **Quentin DEGLI ESPOSTI**
- **Juliette SUC** ⇔ **Adrien LEYVAL**
- **Gwendoline GARLET** ⇔ **Mathieu LECANU**
- **Nathan VIANEY** ⇔ **Ariane BERTAUD**
- **Erwan DIDILLON** ⇒ **Camille JANIN** ⇒ **Arnaud MAINDRE** ⇒ **Erwan DIDILLON**
