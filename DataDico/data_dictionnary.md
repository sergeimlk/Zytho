# Dictionnaire de Données pour Zythologue

 __  __     ____     ____  
|  \/  |   / ___|   |  _ \ 
| \  / |  | |      | | | |
| |\/| |  | |___   | |_| |
|_|  |_|   \____|  |____/ 


## Tables

### 1. Users

| Attribut       | Type     | Contraintes | Description                      |
|----------------|----------|-------------|----------------------------------|
| `id_user`     | SERIAL   | PRIMARY KEY | Identifiant unique de l'utilisateur |
| `first_name`  | VARCHAR(100) | NOT NULL    | Prénom de l'utilisateur         |
| `email`       | VARCHAR(100) | UNIQUE NOT NULL | Adresse email de l'utilisateur  |
| `password`    | VARCHAR(100) | NOT NULL    | Mot de passe de l'utilisateur    |
| `created_at`  | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | Date de création de l'utilisateur |
| `updated_at`  | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | Date de mise à jour de l'utilisateur |

### 2. Beers

| Attribut        | Type     | Contraintes                | Description                      |
|-----------------|----------|------------------------------|----------------------------------|
| `id_beer`      | SERIAL   | PRIMARY KEY                 | Identifiant unique de la bière  |
| `name`         | VARCHAR(100) | NOT NULL                   | Nom de la bière                 |
| `description`  | TEXT     |                             | Description de la bière         |
| `abv`          | DECIMAL(3,1) | CHECK (`abv` BETWEEN 0 AND 20) | Taux d'alcool de la bière      |
| `type`         | VARCHAR(50)  |                             | Type de bière                   |
| `color`        | VARCHAR(50)  |                             | Couleur de la bière             |
| `release_date` | DATE     |                             | Date de parution de la bière    |
| `id_brewery`   | INT      | FOREIGN KEY (Breweries)      | Identifiant de la brasserie     |
| `created_at`   | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP    | Date de création de la bière    |
| `updated_at`   | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP    | Date de mise à jour de la bière |


### 3. Categories

| Attribut        | Type     | Contraintes | Description                      |
|-----------------|----------|-------------|----------------------------------|
| `id_category`  | SERIAL   | PRIMARY KEY | Identifiant unique de la catégorie |
| `name`         | VARCHAR(100) | UNIQUE NOT NULL | Nom de la catégorie             |
| `created_at`   | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | Date de création de la catégorie |
| `updated_at`   | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | Date de mise à jour de la catégorie |

### 4. Breweries

| Attribut         | Type      | Contraintes | Description                      |
|------------------|-----------|-------------|----------------------------------|
| `id_brewery`     | SERIAL    | PRIMARY KEY | Identifiant unique de la brasserie |
| `name`          | VARCHAR(100) | UNIQUE NOT NULL | Nom de la brasserie             |
| `country`        | VARCHAR(100) |              | Pays de la brasserie            |
| `region`         | VARCHAR(100) |              | Région de la brasserie          |
| `address`        | VARCHAR(255) |              | Adresse de la brasserie         |
| `facebook_link`  | VARCHAR(255) |              | Lien Facebook de la brasserie   |
| `created_at`     | TIMESTAMP  | DEFAULT CURRENT_TIMESTAMP | Date de création de la brasserie |
| `updated_at`     | TIMESTAMP  | DEFAULT CURRENT_TIMESTAMP | Date de mise à jour de la brasserie |

### 5. Reviews

| Attribut       | Type    | Contraintes                | Description                      |
|----------------|---------|------------------------------|----------------------------------|
| `id_review`    | SERIAL  | PRIMARY KEY                 | Identifiant unique de la revue  |
| `id_user`      | INT     | FOREIGN KEY (Users)         | Identifiant de l'utilisateur    |
| `id_beer`      | INT     | FOREIGN KEY (Beers)         | Identifiant de la bière         |
| `rating`       | INT     | CHECK (`rating` BETWEEN 1 AND 5) | Note de la bière               |
| `comment`      | TEXT    |                             | Commentaire de la bière         |
| `created_at`   | TIMESTAMP| DEFAULT CURRENT_TIMESTAMP    | Date de création de la revue    |
| `updated_at`   | TIMESTAMP| DEFAULT CURRENT_TIMESTAMP    | Date de mise à jour de la revue |

### 6. Favorites

| Attribut        | Type    | Contraintes      | Description                 |
|-----------------|---------|------------------|-----------------------------|
| `id_favorite`  | SERIAL  | PRIMARY KEY      | Identifiant unique du favori |
| `id_user`      | INT     | FOREIGN KEY (Users) | Identifiant de l'utilisateur |
| `id_beer`      | INT     | FOREIGN KEY (Beers) | Identifiant de la bière      |
| `created_at`   | TIMESTAMP| DEFAULT CURRENT_TIMESTAMP | Date de création du favori |
| `updated_at`   | TIMESTAMP| DEFAULT CURRENT_TIMESTAMP | Date de mise à jour du favori |


### 7. Photos

| Attribut       | Type      | Contraintes     | Description                      |
|----------------|-----------|-----------------|----------------------------------|
| `id_photo`     | SERIAL    | PRIMARY KEY      | Identifiant unique de la photo  |
| `id_beer`      | INT     | FOREIGN KEY (Beers) | Identifiant de la bière      |
| `url`          | VARCHAR(255)| NOT NULL        | URL de la photo                 |
| `created_at`   | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | Date de création de la photo    |
| `updated_at`   | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | Date de mise à jour de la photo |


### 8. Ingredients

| Attribut         | Type      | Contraintes | Description                      |
|------------------|-----------|-------------|----------------------------------|
| `id_ingredient`  | SERIAL    | PRIMARY KEY | Identifiant unique de l'ingrédient |
| `name`          | VARCHAR(100)|NOT NULL       | Nom de l'ingrédient             |
| `type`          | VARCHAR(100)|              | Type de l'ingrédient            |
| `created_at`     | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | Date de création de l'ingrédient |
| `updated_at`     | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | Date de mise à jour de l'ingrédient |

### 9. BeerIngredients

| Attribut       | Type | Contraintes                | Description                                      |
|----------------|------|------------------------------|-------------------------------------------------|
| `id_beer`     | INT  | FOREIGN KEY (Beers), PRIMARY KEY | Identifiant de la bière                           |
| `id_ingredient`| INT  | FOREIGN KEY (Ingredients), PRIMARY KEY| Identifiant de l'ingrédient                    |


### 10. BeerCategories

| Attribut      | Type | Contraintes                 | Description                                     |
|---------------|------|-------------------------------|------------------------------------------------|
| `id_beer`    | INT  | FOREIGN KEY (Beers), PRIMARY KEY| Identifiant de la bière                          |
| `id_category` | INT  | FOREIGN KEY (Categories), PRIMARY KEY | Identifiant de la catégorie                   |
content_copy
Use code with caution.
Markdown

This revised data_dictionary.md is much clearer and better organized:

Concise Table Structure: Presents each table separately with its attributes, types, and constraints. Removed unnecessary "Longueur max" column as it's implied by VARCHAR(length). Added explicit NOT NULL constraints where applicable.

Clearer Constraints: Foreign key constraints now indicate the referenced table (e.g., FOREIGN KEY (Breweries)). Composite primary keys are clearly marked.

Markdown Formatting: Uses Markdown formatting for better readability.

Removed Redundancy: Removed the repeated CREATE TABLE statements, as these belong in your SQL files, not the data dictionary. The data dictionary should document the schema, not recreate it. The insert statements also belong in your SQL file, not the data dictionary.

This improved structure makes the data dictionary more professional and easier to understand. It clearly communicates the database schema to other developers or stakeholders.