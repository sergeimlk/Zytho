# 🗂️ **Règles Métier (Business Rules) - Zythologue**

Bienvenue dans la documentation des règles métier de **Zythologue**, une application dédiée aux amateurs de bières artisanales. Ce document établit les contraintes, relations et comportements pour garantir le bon fonctionnement de l'application.

---

## 📚 **Table des matières**

1. [👤 Utilisateurs](#-utilisateurs)  
2. [🍺 Bières](#-bières)  
3. [🏭 Brasseries](#-brasseries)  
4. [🏷️ Catégories](#-catégories)  
5. [⭐ Avis et Notations](#-avis-et-notations)  
6. [❤️ Favoris](#-favoris)  
7. [📷 Photos](#-photos)  
8. [🌾 Ingrédients](#-ingrédients)  
9. [🔗 Relations et Contraintes Globales](#-relations-et-contraintes-globales)  

---

## 👤 **Utilisateurs**

1. **🔑 Email unique**  
   - Chaque utilisateur doit avoir une adresse email unique.  
   - **Raison** : Éviter la duplication de comptes.  
   - **Implémentation** : Contrainte en base de données (`UNIQUE`).  

2. **🔒 Authentification sécurisée**  
   - Les mots de passe doivent être **hashés** et jamais stockés en clair.  
   - La connexion s'effectue via un couple **email/mot de passe**.  

3. **📝 Relation avec les avis et favoris**  
   - Un utilisateur peut laisser **un seul avis par bière**.  
   - Un utilisateur peut avoir plusieurs favoris, mais **pas de doublons**.  

4. **🗑️ Suppression**  
   - Si un utilisateur est supprimé, ses avis et favoris associés doivent l'être également.  

---

## 🍺 **Bières**

1. **🔢 ABV (Taux d'alcool)**  
   - La valeur de l'alcool (ABV) doit être comprise entre **0 % et 20 %**.  
   - **Raison** : Contraintes réalistes pour les bières artisanales.  
   - **Implémentation** : Contrainte en base de données (`CHECK`).  

2. **📖 Description facultative**  
   - Les bières peuvent inclure une description, mais ce n'est pas obligatoire.  

3. **📂 Catégorisation**  
   - Une bière doit appartenir à **au moins une catégorie**.  
   - Une bière peut être associée à plusieurs catégories.  

4. **🌾 Ingrédients**  
   - Une bière peut contenir plusieurs ingrédients (relation N:M).  

5. **🏭 Lien avec la brasserie**  
   - Chaque bière doit être associée à une brasserie.  
   - Si la brasserie est supprimée, ses bières le sont aussi (**ON DELETE CASCADE**).  

---

## 🏭 **Brasseries**

1. **🆔 Unicité du nom**  
   - Chaque brasserie doit avoir un nom unique.  
   - **Raison** : Éviter les doublons pour les utilisateurs.  

2. **📍 Informations géographiques**  
   - Une brasserie doit indiquer un **pays** et une **région**.  

3. **🍺 Relation avec les bières**  
   - Une brasserie peut produire plusieurs bières.  
   - **Suppression en cascade** : Si une brasserie est supprimée, toutes ses bières le sont également.  

---

## 🏷️ **Catégories**

1. **🆔 Unicité du nom**  
   - Chaque catégorie doit avoir un nom unique.  
   - **Exemple** : "IPA", "Stout", "Saison".  

2. **🔗 Relation avec les bières**  
   - Une catégorie peut inclure plusieurs bières.  
   - Une bière peut appartenir à plusieurs catégories (**relation N:M**).  

---

## ⭐ **Avis et Notations**

1. **🔢 Notation (Rating)**  
   - La note d'une bière doit être un entier entre **1 et 5**.  
   - **Raison** : Standardiser les évaluations des utilisateurs.  

2. **👤 Un avis par utilisateur et par bière**  
   - Un utilisateur peut laisser **un seul avis par bière**.  

3. **🗑️ Suppression d'avis**  
   - Si un utilisateur ou une bière est supprimé(e), ses avis doivent également être supprimés (**ON DELETE CASCADE**).  

---

## ❤️ **Favoris**

1. **🔗 Relation unique**  
   - Un utilisateur ne peut ajouter une bière qu'une seule fois à ses favoris.  

2. **🗑️ Suppression liée**  
   - Si un utilisateur ou une bière est supprimé(e), les favoris associés doivent être supprimés automatiquement (**ON DELETE CASCADE**).  

---

## 📷 **Photos**

1. **📸 Lien avec les bières**  
   - Chaque photo doit être associée à une bière.  
   - Une bière peut avoir plusieurs photos.  

2. **📂 URL obligatoire**  
   - Une photo doit avoir un lien URL valide.  

3. **🗑️ Suppression liée**  
   - Si une bière est supprimée, les photos associées doivent également être supprimées (**ON DELETE CASCADE**).  

---

## 🌾 **Ingrédients**

1. **🆔 Unicité du nom**  
   - Chaque ingrédient doit avoir un nom unique (par type).  

2. **🔗 Relation avec les bières**  
   - Une bière peut inclure plusieurs ingrédients.  
   - Un ingrédient peut être partagé par plusieurs bières (relation N:M).  

---

## 🔗 **Relations et Contraintes Globales**

1. **🌐 Intégrité référentielle**  
   - Toutes les relations sont gérées via des **clés étrangères**.  
   - Suppression en cascade pour garantir la cohérence des données.  

2. **🕒 Timestamps automatiques**  
   - Les champs `created_at` et `updated_at` doivent être automatiquement mis à jour lors de toute création ou modification.  

3. **📌 Contrainte de création**  
   - Une entité dépendante (ex. `Avis`, `Favoris`, `BeerIngredients`) ne peut exister que si l'entité principale associée (ex. `Users`, `Beers`) existe.  
