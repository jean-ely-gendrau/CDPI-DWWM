# 📘 Support – Le Pattern MVC en PHP

---

![header](https://capsule-render.vercel.app/api?type=waving\&color=gradient\&height=200\&section=header\&text=Le%20Pattern%20MVC%20\&fontSize=40\&fontAlignY=35\&desc=PHP\&descAlignY=55\&descAlign=50)

## 1. 🎓 Introduction

### 🎯 Objectif global

Aujourd’hui, tu vas découvrir et comprendre le **pattern MVC (Modèle – Vue – Contrôleur)** en PHP. L’objectif est de savoir structurer ton code pour qu’il soit **plus clair, réutilisable et facile à maintenir**.

### 🛠️ Compétences visées (référentiel DWWM)

* Organiser ton projet avec une architecture adaptée
* Séparer la logique métier, l’affichage et le contrôle des données
* Développer une application web en suivant les bonnes pratiques
* Comprendre la logique des frameworks modernes (Symfony, Laravel, etc.)

### 🌍 Contexte métier

Dans un vrai projet :

* Le MVC permet de **travailler en équipe** : chacun gère sa partie (modèle, vue, contrôleur).
* Il rend la **maintenance plus facile** : tu corriges une partie sans tout casser.
* Il prépare l’avenir, car les **frameworks PHP utilisent MVC**.

---

## 🌱 Petit rappel avant de commencer : les classes en PHP

On n’as pas encore vu les **classes** ? Pas de panique !
Une **classe** est comme un plan de construction (une sorte de modèle) pour créer des objets.

### Exemple simple

```php
<?php
class Voiture {
    public $marque;
    public $couleur;

    public function rouler() {
        echo "La voiture roule 🚗";
    }
}

$maVoiture = new Voiture();
$maVoiture->marque = "Peugeot";
$maVoiture->couleur = "Rouge";
$maVoiture->rouler(); // Affiche : La voiture roule 🚗
```

➡️ Ici, `Voiture` est une **classe**. Elle peut créer des **objets** (ici `$maVoiture`) qui ont des **propriétés** (marque, couleur) et des **méthodes** (rouler).

👉 Retient : une **classe = plan**, un **objet = instance du plan**.

Ces notions sont utilisées dans le MVC, notamment pour les **Modèles** et les **Contrôleurs**.

---

## 2. 📖 Cours

### 💡 Qu’est-ce qu’un design pattern ?

Un **design pattern** est une solution réutilisable à un problème courant en programmation.
Le **pattern MVC** est l’un des plus utilisés dans le développement web.

### 🏗️ Définition du MVC

* **Modèle (Model)** : Gère les **données** (connexion à la base, règles métiers, requêtes SQL).
* **Vue (View)** : Gère l’**affichage** (HTML, CSS, présentation à l’utilisateur).
* **Contrôleur (Controller)** : Gère la **logique** (traite les requêtes, appelle le modèle, choisit la vue à afficher).

➡️ **Analogie simple** :
Imagine un **restaurant** :

* Le **client** = l’utilisateur final
* Le **serveur (Contrôleur)** prend ta commande et la transmet en cuisine
* Le **cuisinier (Modèle)** prépare le plat (les données)
* Le **serveur** t’apporte le plat dans une belle assiette (Vue).

### 🖼️ Schéma du MVC

```bash
[Utilisateur] → [Contrôleur] → [Modèle] → [Base de données]
        ↓
       [Vue]
```

### ✅ Bonnes pratiques

* Ne mets jamais de **SQL** directement dans la vue
* Ne mélange pas **HTML et PHP métier**
* Sépare toujours les responsabilités
* Organise tes fichiers dans des dossiers clairs :

  ```bash
  /app
    /controllers
    /models
    /views
  ```

---

## 4. 💻 Démonstration pratique

Créons une petite application MVC en PHP qui affiche une liste d’articles.

### 📂 Structure des dossiers

```bash
/app
   /controllers
      ArticleController.php
   /models
      Article.php
   /views
      articles.php
index.php
```

### 🔹 Étape 1 : Le modèle (Article.php)

```php
<?php
// app/models/Article.php
class Article {
    public static function getAll() {
        // Normalement : requête SQL vers une base de données
        // Ici : on simule avec un tableau
        return [
            ["id" => 1, "titre" => "Introduction au MVC"],
            ["id" => 2, "titre" => "PHP pour les débutants"],
            ["id" => 3, "titre" => "Structurer son code proprement"]
        ];
    }
}
```

### 🔹 Étape 2 : Le contrôleur (ArticleController.php)

```php
<?php
// app/controllers/ArticleController.php
require_once __DIR__ . "/../models/Article.php";

class ArticleController {
    public function index() {
        $articles = Article::getAll();
        require __DIR__ . "/../views/articles.php";
    }
}
```

### 🔹 Étape 3 : La vue (articles.php)

```php
<!-- app/views/articles.php -->
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Liste des articles</title>
</head>
<body>
    <h1>Liste des articles</h1>
    <ul>
        <?php foreach($articles as $article): ?>
            <li><?= htmlspecialchars($article["titre"]) ?></li>
        <?php endforeach; ?>
    </ul>
</body>
</html>
```

### 🔹 Étape 4 : Point d’entrée (index.php)

```php
<?php
// index.php
require_once __DIR__ . "/app/controllers/ArticleController.php";

$controller = new ArticleController();
$controller->index();
```

✅ Résultat attendu : une page affichant une **liste de 3 articles**.

---

## 5. 🛠️ TP guidé

### 🎯 Objectif

Créer une mini-application MVC en PHP qui affiche une liste de **produits**.

### 🔹 Consignes

1. Crée la structure MVC : `models/`, `views/`, `controllers/`.
2. Le **modèle** doit contenir une liste de produits (id, nom, prix).
3. Le **contrôleur** doit récupérer les produits.
4. La **vue** doit afficher la liste avec nom + prix.
5. Vérifie le bon fonctionnement avec `index.php`.

### 🔹 Indices

* Inspire-toi de l’exemple “Articles”
* Utilise `htmlspecialchars()` pour sécuriser l’affichage
* Vérifie l’ordre des `require` (le contrôleur doit inclure le modèle)

### 🔹 Vérification

👉 Si tu vois une liste de produits affichée correctement dans ton navigateur, c’est gagné !

---

## 6. 🚀 TP autonome (mini app MVC)

### 🎯 Objectif (mini-app)

Créer une mini-application MVC qui affiche des **utilisateurs** avec :

* Nom
* Email
* Âge

### 🔹 Attendus

* Une structure claire (MVC)
* Pas de mélange HTML / SQL
* Une page web lisible affichant les utilisateurs

---

## 7. 🔧 Exercices pratiques courts

1. Crée un **modèle** `Categorie.php` qui retourne une liste de catégories.
2. Crée un **contrôleur** `CategorieController.php` qui appelle le modèle.
3. Crée une **vue** `categories.php` qui affiche ces catégories en liste.

### ✅ Correction attendue (extrait)

```php
// models/Categorie.php
class Categorie {
    public static function getAll() {
        return ["PHP", "JavaScript", "HTML/CSS"];
    }
}
```

```php
// controllers/CategorieController.php
require_once __DIR__ . "/../models/Categorie.php";
class CategorieController {
    public function index() {
        $categories = Categorie::getAll();
        require __DIR__ . "/../views/categories.php";
    }
}
```

```php
<!-- views/categories.php -->
<ul>
    <?php foreach($categories as $categorie): ?>
        <li><?= htmlspecialchars($categorie) ?></li>
    <?php endforeach; ?>
</ul>
```

---

## 9. 📚 Ressources complémentaires

* 📖 Documentation officielle PHP : [https://www.php.net/manual/fr/](https://www.php.net/manual/fr/)
* 🌐 Tutoriel MVC PHP OpenClassrooms : [https://openclassrooms.com/fr/courses/](https://openclassrooms.com/fr/courses/)
* 📘 Livre : *PHP et MySQL – Développer un site web dynamique et interactif* (Eyrolles)
* 🔧 Pour aller plus loin : découvrir **Symfony** ou **Laravel**, frameworks MVC en PHP

![footer](https://capsule-render.vercel.app/api?type=waving\&color=gradient\&height=120\&section=footer\&text=%F0%9F%8C%9F%20Continue%20ta%20progression%20en%20PHP%20!%20%F0%9F%9A%80\&fontSize=22)
