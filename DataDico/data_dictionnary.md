# Dictionnaire de Données pour Zythologue


 __  __     ____     ____  
|  \/  |   / ___|   |  _ \ 
| \  / |  | |      | | | |
| |\/| |  | |___   | |_| |
|_|  |_|   \____|  |____/ 

## Users

| Nom de l'attribut       | Type     | Longueur max | Contraintes          | Description                      |
|-------------------------|----------|--------------|-----------------------|----------------------------------|
| id_user                | SERIAL   |              | PRIMARY KEY          | Identifiant unique de l'utilisateur |
| first_name             | VARCHAR  | 100          |                       | Prénom de l'utilisateur         |
| email                  | VARCHAR  | 100          | UNIQUE               | Adresse email de l'utilisateur  |
| password               | VARCHAR  | 100          |                       | Mot de passe de l'utilisateur    |
| created_at             | TIMESTAMP|              | DEFAULT CURRENT_TIMESTAMP | Date de création de l'utilisateur |
| updated_at             | TIMESTAMP|              | DEFAULT CURRENT_TIMESTAMP | Date de mise à jour de l'utilisateur |

## Beers

| Nom de l'attribut       | Type     | Longueur max | Contraintes          | Description                      |
|-------------------------|----------|--------------|-----------------------|----------------------------------|
| id_beer                 | SERIAL   |              | PRIMARY KEY          | Identifiant unique de la bière  |
| name                    | VARCHAR  | 100          |                       | Nom de la bière                 |
| description             | TEXT     |              |                       | Description de la bière         |
| abv                     | DECIMAL  | 3,1          | CHECK (abv BETWEEN 0 AND 20) | Taux d'alcool de la bière      |
| type                    | VARCHAR  | 50           |                       | Type de bière                   |
| color                   | VARCHAR  | 50           |                       | Couleur de la bière             |
| release_date            | DATE     |              |                       | Date de parution de la bière    |
| id_brewery              | INT      |              | FOREIGN KEY          | Identifiant de la brasserie     |
| created_at              | TIMESTAMP|              | DEFAULT CURRENT_TIMESTAMP | Date de création de la bière    |
| updated_at              | TIMESTAMP|              | DEFAULT CURRENT_TIMESTAMP | Date de mise à jour de la bière |

## Categories

| Nom de l'attribut       | Type     | Longueur max | Contraintes          | Description                      |
|-------------------------|----------|--------------|-----------------------|----------------------------------|
| id_category             | SERIAL   |              | PRIMARY KEY          | Identifiant unique de la catégorie |
| name                    | VARCHAR  | 100          | UNIQUE               | Nom de la catégorie             |
| created_at              | TIMESTAMP|              | DEFAULT CURRENT_TIMESTAMP | Date de création de la catégorie |
| updated_at              | TIMESTAMP|              | DEFAULT CURRENT_TIMESTAMP | Date de mise à jour de la catégorie |

## Breweries

| Nom de l'attribut       | Type     | Longueur max | Contraintes          | Description                      |
|-------------------------|----------|--------------|-----------------------|----------------------------------|
| id_brewery              | SERIAL   |              | PRIMARY KEY          | Identifiant unique de la brasserie |
| name                    | VARCHAR  | 100          | UNIQUE               | Nom de la brasserie             |
| country                 | VARCHAR  | 100          |                       | Pays de la brasserie            |
| region                  | VARCHAR  | 100          |                       | Région de la brasserie          |
| address                 | VARCHAR  | 255          |                       | Adresse de la brasserie         |
| facebook_link           | VARCHAR  | 255          |                       | Lien Facebook de la brasserie   |
| created_at              | TIMESTAMP|              | DEFAULT CURRENT_TIMESTAMP | Date de création de la brasserie |
| updated_at              | TIMESTAMP|              | DEFAULT CURRENT_TIMESTAMP | Date de mise à jour de la brasserie |

## Reviews

| Nom de l'attribut       | Type     | Longueur max | Contraintes          | Description                      |
|-------------------------|----------|--------------|-----------------------|----------------------------------|
| id_review               | SERIAL   |              | PRIMARY KEY          | Identifiant unique de la revue  |
| id_user                 | INT      |              | FOREIGN KEY          | Identifiant de l'utilisateur    |
| id_beer                 | INT      |              | FOREIGN KEY          | Identifiant de la bière         |
| rating                  | INT      |              | CHECK (rating BETWEEN 1 AND 5) | Note de la bière               |
| comment                 | TEXT     |              |                       | Commentaire de la bière         |
| created_at              | TIMESTAMP|              | DEFAULT CURRENT_TIMESTAMP | Date de création de la revue    |
| updated_at              | TIMESTAMP|              | DEFAULT CURRENT_TIMESTAMP | Date de mise à jour de la revue |

## Favorites

| Nom de l'attribut       | Type     | Longueur max | Contraintes          | Description                      |
|-------------------------|----------|--------------|-----------------------|----------------------------------|
| id_favorite             | SERIAL   |              | PRIMARY KEY          | Identifiant unique du favori    |
| id_user                 | INT      |              | FOREIGN KEY          | Identifiant de l'utilisateur    |
| id_beer                 | INT      |              | FOREIGN KEY          | Identifiant de la bière         |
| created_at              | TIMESTAMP|              | DEFAULT CURRENT_TIMESTAMP | Date de création du favori      |
| updated_at              | TIMESTAMP|              | DEFAULT CURRENT_TIMESTAMP | Date de mise à jour du favori    |

## Photos

| Nom de l'attribut       | Type     | Longueur max | Contraintes          | Description                      |
|-------------------------|----------|--------------|-----------------------|----------------------------------|
| id_photo                | SERIAL   |              | PRIMARY KEY          | Identifiant unique de la photo  |
| id_beer                 | INT      |              | FOREIGN KEY          | Identifiant de la bière         |
| url                     | VARCHAR  | 255          |                       | URL de la photo                 |
| created_at              | TIMESTAMP|              | DEFAULT CURRENT_TIMESTAMP | Date de création de la photo    |
| updated_at              | TIMESTAMP|              | DEFAULT CURRENT_TIMESTAMP | Date de mise à jour de la photo |

## Ingredients

| Nom de l'attribut       | Type     | Longueur max | Contraintes          | Description                      |
|-------------------------|----------|--------------|-----------------------|----------------------------------|
| id_ingredient           | SERIAL   |              | PRIMARY KEY          | Identifiant unique de l'ingrédient |
| name                    | VARCHAR  | 100          |                       | Nom de l'ingrédient             |
| type                    | VARCHAR  | 100          |                       | Type de l'ingrédient            |
| created_at              | TIMESTAMP|              | DEFAULT CURRENT_TIMESTAMP | Date de création de l'ingrédient |
| updated_at              | TIMESTAMP|              | DEFAULT CURRENT_TIMESTAMP | Date de mise à jour de l'ingrédient |








  __  __   _       _____  
 |  \/  | | |     |  __ \ 
 | \  / | | |     | |  | |
 | |\/| | | |     | |  | |
 | |  | | | |____ | |__| |
 |_|  |_| |______||_____/ 

-- Users Table
CREATE TABLE Users (
    id_user SERIAL PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100) UNIQUE,
    password VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Beers Table
CREATE TABLE Beers (
    id_beer SERIAL PRIMARY KEY,
    name VARCHAR(100),
    description TEXT,
    abv DECIMAL(3,1) CHECK (abv BETWEEN 0 AND 20),
    type VARCHAR(50),
    color VARCHAR(50),
    release_date DATE,
    id_brewery INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (id_brewery) REFERENCES Breweries(id_brewery)
);

-- Breweries Table
CREATE TABLE Breweries (
    id_brewery SERIAL PRIMARY KEY,
    name VARCHAR(100) UNIQUE,
    country VARCHAR(100),
    region VARCHAR(100),
    address VARCHAR(255),
    site_link VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Reviews Table
CREATE TABLE Reviews (
    id_review SERIAL PRIMARY KEY,
    id_user INT,
    id_beer INT,
    rating INT CHECK (rating BETWEEN 1 AND 5),
    comment TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (id_user) REFERENCES Users(id_user),
    FOREIGN KEY (id_beer) REFERENCES Beers(id_beer)
);

-- Favorites Table
CREATE TABLE Favorites (
    id_favorite SERIAL PRIMARY KEY,
    id_user INT,
    id_beer INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (id_user) REFERENCES Users(id_user),
    FOREIGN KEY (id_beer) REFERENCES Beers(id_beer)
);

-- Pictures Table
CREATE TABLE Pictures (
    id_pic SERIAL PRIMARY KEY,
    id_beer INT,
    url VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (id_beer) REFERENCES Beers(id_beer)
);

-- Ingredients Table
CREATE TABLE Ingredients (
    id_ingredient SERIAL PRIMARY KEY,
    name VARCHAR(100),
    type VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- BeerIngredients Table (Association Table for N:M Relationship)
CREATE TABLE BeerIngredients (
    id_beer INT,
    id_ingredient INT,
    PRIMARY KEY (id_beer, id_ingredient),
    FOREIGN KEY (id_beer) REFERENCES Beers(id_beer),
    FOREIGN KEY (id_ingredient) REFERENCES Ingredients(id_ingredient)
);

-- Categories Table
CREATE TABLE Categories (
    id_category SERIAL PRIMARY KEY,
    name VARCHAR(100) UNIQUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- BeerCategories Table (Association Table for 1:N Relationship)
CREATE TABLE BeerCategories (
    id_beer INT,
    id_category INT,
    PRIMARY KEY (id_beer, id_category),
    FOREIGN KEY (id_beer) REFERENCES Beers(id_beer),
    FOREIGN KEY (id_category) REFERENCES Categories(id_category)
);





  __  __   _____   _____  
 |  \/  | |  __ \ |  __ \ 
 | \  / | | |__) || |  | |
 | |\/| | |  ___/ | |  | |
 | |  | | | |     | |__| |
 |_|  |_| |_|     |_____/ 
 
 
 
-- Users Table
CREATE TABLE Users (
    id_user SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(100) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Beers Table
CREATE TABLE Beers (
    id_beer SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    abv DECIMAL(3,1) CHECK (abv BETWEEN 0 AND 20),
    type VARCHAR(50),
    color VARCHAR(50),
    release_date DATE,
    id_brewery INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (id_brewery) REFERENCES Breweries(id_brewery)
);

-- Breweries Table
CREATE TABLE Breweries (
    id_brewery SERIAL PRIMARY KEY,
    name VARCHAR(100) UNIQUE NOT NULL,
    country VARCHAR(100),
    region VARCHAR(100),
    address VARCHAR(255),
    site_link VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Reviews Table
CREATE TABLE Reviews (
    id_review SERIAL PRIMARY KEY,
    id_user INT,
    id_beer INT,
    rating INT CHECK (rating BETWEEN 1 AND 5),
    comment TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (id_user) REFERENCES Users(id_user),
    FOREIGN KEY (id_beer) REFERENCES Beers(id_beer)
);

-- Favorites Table
CREATE TABLE Favorites (
    id_favorite SERIAL PRIMARY KEY,
    id_user INT,
    id_beer INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (id_user) REFERENCES Users(id_user),
    FOREIGN KEY (id_beer) REFERENCES Beers(id_beer)
);

-- Pictures Table
CREATE TABLE Pictures (
    id_pic SERIAL PRIMARY KEY,
    id_beer INT,
    url VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (id_beer) REFERENCES Beers(id_beer)
);

-- Ingredients Table
CREATE TABLE Ingredients (
    id_ingredient SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    type VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- BeerIngredients Table (Association Table for N:M Relationship)
CREATE TABLE BeerIngredients (
    id_beer INT,
    id_ingredient INT,
    PRIMARY KEY (id_beer, id_ingredient),
    FOREIGN KEY (id_beer) REFERENCES Beers(id_beer),
    FOREIGN KEY (id_ingredient) REFERENCES Ingredients(id_ingredient)
);

-- Categories Table
CREATE TABLE Categories (
    id_category SERIAL PRIMARY KEY,
    name VARCHAR(100) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- BeerCategories Table (Association Table for 1:N Relationship)
CREATE TABLE BeerCategories (
    id_beer INT,
    id_category INT,
    PRIMARY KEY (id_beer, id_category),
    FOREIGN KEY (id_beer) REFERENCES Beers(id_beer),
    FOREIGN KEY (id_category) REFERENCES Categories(id_category)
);
