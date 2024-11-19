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
 
-- Table Users
CREATE TABLE Users (
    id_user SERIAL PRIMARY KEY,
    first_name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(100) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table Beers
CREATE TABLE Beers (
    id_beer SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    abv DECIMAL(3,1) CHECK (abv BETWEEN 0 AND 20),
    type VARCHAR(50),
    color VARCHAR(50),
    release_date DATE,
    id_brewery INT REFERENCES Breweries(id_brewery) ON DELETE CASCADE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table Breweries
CREATE TABLE Breweries (
    id_brewery SERIAL PRIMARY KEY,
    name VARCHAR(100) UNIQUE NOT NULL,
    country VARCHAR(100),
    region VARCHAR(100),
    address VARCHAR(255),
    facebook_link VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table Reviews
CREATE TABLE Reviews (
    id_review SERIAL PRIMARY KEY,
    id_user INT REFERENCES Users(id_user) ON DELETE CASCADE,
    id_beer INT REFERENCES Beers(id_beer) ON DELETE CASCADE,
    rating INT CHECK (rating BETWEEN 1 AND 5),
    comment TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table Favorites
CREATE TABLE Favorites (
    id_favorite SERIAL PRIMARY KEY,
    id_user INT REFERENCES Users(id_user) ON DELETE CASCADE,
    id_beer INT REFERENCES Beers(id_beer) ON DELETE CASCADE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table Photos
CREATE TABLE Photos (
    id_photo SERIAL PRIMARY KEY,
    id_beer INT REFERENCES Beers(id_beer) ON DELETE CASCADE,
    url VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table Ingredients
CREATE TABLE Ingredients (
    id_ingredient SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    type VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table BeerIngredients (Relation N:M entre Beers et Ingredients)
CREATE TABLE BeerIngredients (
    id_beer INT REFERENCES Beers(id_beer) ON DELETE CASCADE,
    id_ingredient INT REFERENCES Ingredients(id_ingredient) ON DELETE CASCADE,
    PRIMARY KEY (id_beer, id_ingredient)
);

-- Table Categories
CREATE TABLE Categories (
    id_category SERIAL PRIMARY KEY,
    name VARCHAR(100) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table BeerCategories (Relation 1:N entre Beers et Categories)
CREATE TABLE BeerCategories (
    id_beer INT REFERENCES Beers(id_beer) ON DELETE CASCADE,
    id_category INT REFERENCES Categories(id_category) ON DELETE CASCADE,
    PRIMARY KEY (id_beer, id_category)
);





  __  __   _____   _____  
 |  \/  | |  __ \ |  __ \ 
 | \  / | | |__) || |  | |
 | |\/| | |  ___/ | |  | |
 | |  | | | |     | |__| |
 |_|  |_| |_|     |_____/ 
 
 
-- Table Users
CREATE TABLE Users (
    id_user SERIAL PRIMARY KEY,
    first_name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(100) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table Breweries
CREATE TABLE Breweries (
    id_brewery SERIAL PRIMARY KEY,
    name VARCHAR(100) UNIQUE NOT NULL,
    country VARCHAR(100),
    region VARCHAR(100),
    address VARCHAR(255),
    facebook_link VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table Beers
CREATE TABLE Beers (
    id_beer SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    abv DECIMAL(3,1) CHECK (abv BETWEEN 0 AND 20),
    type VARCHAR(50),
    color VARCHAR(50),
    release_date DATE,
    id_brewery INT REFERENCES Breweries(id_brewery) ON DELETE CASCADE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table Ingredients
CREATE TABLE Ingredients (
    id_ingredient SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    type VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table BeerIngredients (Relation N:M entre Beers et Ingredients)
CREATE TABLE BeerIngredients (
    id_beer INT REFERENCES Beers(id_beer) ON DELETE CASCADE,
    id_ingredient INT REFERENCES Ingredients(id_ingredient) ON DELETE CASCADE,
    PRIMARY KEY (id_beer, id_ingredient)
);

-- Table Categories
CREATE TABLE Categories (
    id_category SERIAL PRIMARY KEY,
    name VARCHAR(100) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table BeerCategories (Relation 1:N entre Beers et Categories)
CREATE TABLE BeerCategories (
    id_beer INT REFERENCES Beers(id_beer) ON DELETE CASCADE,
    id_category INT REFERENCES Categories(id_category) ON DELETE CASCADE,
    PRIMARY KEY (id_beer, id_category)
);

-- Table Reviews
CREATE TABLE Reviews (
    id_review SERIAL PRIMARY KEY,
    id_user INT REFERENCES Users(id_user) ON DELETE CASCADE,
    id_beer INT REFERENCES Beers(id_beer) ON DELETE CASCADE,
    rating INT CHECK (rating BETWEEN 1 AND 5),
    comment TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table Favorites
CREATE TABLE Favorites (
    id_favorite SERIAL PRIMARY KEY,
    id_user INT REFERENCES Users(id_user) ON DELETE CASCADE,
    id_beer INT REFERENCES Beers(id_beer) ON DELETE CASCADE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table Photos
CREATE TABLE Photos (
    id_photo SERIAL PRIMARY KEY,
    id_beer INT REFERENCES Beers(id_beer) ON DELETE CASCADE,
    url VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);