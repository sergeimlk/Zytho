# 🍺 Zythologue - Base De Données pour Amateurs de Bière

## 📜 Contexte du Projet
Tu as une passion dévorante pour la bière artisanale et souhaites découvrir et partager ce monde au-delà de la dégustation : explorer l'histoire derrière chaque brasserie, les ingrédients spécifiques, et les techniques de brassage.

En tant que développeur, tu envisages de créer une application web/mobile pour organiser et partager cette passion. Avant de te lancer dans le développement, une base de données bien structurée est cruciale.

À toi de jouer ! 😊

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