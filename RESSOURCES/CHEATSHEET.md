Cheatsheet SQL Complète
Types de Données
SERIAL

Définition : Un type de données spécial utilisé pour créer des colonnes avec des valeurs uniques et auto-incrémentées.

Utilisation : Souvent utilisé pour les identifiants uniques (ID) des enregistrements.

Exemple : id_user SERIAL PRIMARY KEY crée une colonne id_user qui s'incrémente automatiquement à chaque nouvel enregistrement.

VARCHAR

Définition : Un type de données pour stocker des chaînes de caractères de longueur variable.

Utilisation : Idéal pour les champs texte comme les noms, adresses e-mail, etc.

Exemple : name VARCHAR(100) permet de stocker des chaînes de caractères jusqu'à 100 caractères.

INT

Définition : Un type de données pour stocker des nombres entiers.

Utilisation : Utilisé pour les champs qui nécessitent des valeurs numériques entières, comme les âges, les quantités, etc.

Exemple : age INT permet de stocker des valeurs entières.

TEXT

Définition : Un type de données pour stocker des chaînes de caractères de longueur illimitée.

Utilisation : Utilisé pour les champs texte longs, comme les descriptions ou les commentaires.

Exemple : description TEXT permet de stocker des textes longs sans limite de caractères.

TIMESTAMP

Définition : Un type de données pour stocker des informations de date et d'heure. (Nbre de secondes depuis 1970)

Utilisation : Utilisé pour enregistrer les moments précis de création ou de mise à jour des enregistrements.

Exemple : created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP enregistre la date et l'heure actuelles lors de la création de l'enregistrement.

DECIMAL

Définition : Un type de données pour stocker des nombres décimaux avec une précision définie.

Utilisation : Utilisé pour les valeurs numériques qui nécessitent des décimales, comme les taux d'alcool (ABV) des bières.

Exemple : abv DECIMAL(3,1) permet de stocker des valeurs avec trois chiffres avant la virgule et un chiffre après.

DATE

Définition : Un type de données pour stocker des informations de date (sans heure).

Utilisation : Utilisé pour enregistrer des dates spécifiques comme les dates de sortie de produits.

Exemple : release_date DATE permet de stocker des dates.

Contraintes
PRIMARY KEY (PK)

Définition : Une clé primaire est une contrainte qui identifie de manière unique chaque enregistrement dans une table.

Utilisation : Utilisée pour garantir que chaque enregistrement dans une table est unique et non nul.

Exemple : id_user SERIAL PRIMARY KEY définit id_user comme la clé primaire de la table, assurant que chaque valeur est unique et auto-incrémentée.

FOREIGN KEY (FK)

Définition : Une clé étrangère est une contrainte qui établit une relation entre deux tables.

Utilisation : Utilisée pour lier une colonne d'une table à une colonne d'une autre table, assurant l'intégrité référentielle.

Exemple : id_user INT REFERENCES Users(id_user) crée une clé étrangère id_user dans une table qui fait référence à la colonne id_user de la table Users.

NOT NULL

Définition : Assure que la colonne ne peut pas avoir de valeur nulle.

Exemple : first_name VARCHAR(50) NOT NULL assure que la colonne first_name ne peut pas être vide.

UNIQUE

Définition : Assure que toutes les valeurs dans une colonne sont uniques.

Exemple : email VARCHAR(100) UNIQUE assure que chaque adresse e-mail est unique dans la table.

CHECK

Définition : Assure que les valeurs respectent une condition spécifique.

Exemple : abv DECIMAL(3,1) CHECK (abv BETWEEN 0 AND 20) assure que le taux d'alcool est compris entre 0 et 20.

Exemples de Création de Tables
sql
-- Table Users
CREATE TABLE Users (
    id_user SERIAL PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table Beers
CREATE TABLE Beers (
    id_beer SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    abv DECIMAL(3,1) CHECK (abv BETWEEN 0 AND 20),
    id_brewery INT REFERENCES Breweries(id_brewery),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table Breweries
CREATE TABLE Breweries (
    id_brewery SERIAL PRIMARY KEY,
    name VARCHAR(100) UNIQUE NOT NULL,
    country VARCHAR(50) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
Requêtes SQL Courantes
Sélectionner toutes les lignes : SELECT * FROM table_name;

Insérer des données : INSERT INTO table_name (column1, column2) VALUES (value1, value2);

Mettre à jour des données : UPDATE table_name SET column1 = value1 WHERE condition;

Supprimer des données : DELETE FROM table_name WHERE condition;

Lister les bières par taux d'alcool : SELECT * FROM Beers ORDER BY abv ASC;

Afficher le nombre de bières par catégorie : SELECT category, COUNT(*) FROM Beers GROUP BY category;

Ressources Utiles
Documentation PostgreSQL : PostgreSQL Documentation

Tutoriels SQL : W3Schools SQL Tutorial

Outils de Modélisation : Utilise des outils comme DBeaver pour visualiser et gérer ta base de données.