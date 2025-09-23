# 📘 Support : **INCLUDE / REQUIRE / \_ONCE en PHP**

![header](https://capsule-render.vercel.app/api?type=waving\&color=gradient\&height=200\&section=header\&text=Include%20Require%20PHP\&fontSize=40\&fontAlignY=35\&desc=include%20require%20include_once%20require_once\&descAlignY=55\&descAlign=50)

## 1. 🎓 Introduction

### 🎯 Objectif global

Découvre et apprends à utiliser les instructions **`include`**, **`require`**, **`include_once`** et **`require_once`** en PHP pour réutiliser du code sans duplication, organiser un projet de manière claire et professionnelle.

### 🛠️ Compétences visées (référentiel DWWM)

* Développer des pages web dynamiques en PHP
* Organiser et structurer ton code (réutilisabilité, modularité)
* Respecter les bonnes pratiques de développement

### 💼 Contexte métier

Dans un vrai projet web, un site contient souvent **des parties communes** :

* en-tête (logo, menu)
* pied de page
* fichier de configuration (connexion BDD, constantes, etc.)

Plutôt que de copier-coller ce code sur chaque page, tu utilises **`include`** ou **`require`** (et leurs variantes `_once`).
👉 Cela **te fait gagner du temps**, **évite les erreurs**, et rend le projet **plus facile à maintenir**.

---

## 2. 📖 Cours

### 📌 Définition

* **`include`** : insère le contenu d’un fichier dans un autre fichier PHP.
* **`require`** : fonctionne pareil, mais plus strict : si le fichier n’existe pas, PHP arrête l’exécution (erreur fatale).
* **`include_once`** : comme `include`, mais ne charge le fichier qu’une seule fois.
* **`require_once`** : comme `require`, mais ne charge le fichier qu’une seule fois.

### 🆚 Différences principales

| Instruction    | Si le fichier manque…         | Si déjà inclus…       | Usage conseillé                 |
| -------------- | ----------------------------- | --------------------- | ------------------------------- |
| `include`      | Warning (le script continue)  | Inclus à nouveau      | Pour du code optionnel          |
| `require`      | Erreur fatale (script stoppé) | Inclus à nouveau      | Pour du code vital              |
| `include_once` | Warning (le script continue)  | Ignoré si déjà inclus | Pour éviter doublons optionnels |
| `require_once` | Erreur fatale (script stoppé) | Ignoré si déjà inclus | Pour éviter doublons vitaux     |

### 🖼️ Analogie

Imagine un livre :

* `include` = tu peux lire le chapitre, s’il manque, tu continues le reste.
* `require` = si le chapitre obligatoire est manquant, tu ne peux plus continuer à lire.
* `include_once/require_once` = tu ne relis jamais deux fois le même chapitre.

### 📂 Exemple d’organisation d’un site

```bash
/mon-site
   ├── header.php
   ├── footer.php
   ├── config.php
   ├── index.php
   ├── contact.php
   ├── sidebar.php
```

---

## 3. 💻 Exemple

### Exemple concret

**Structure des fichiers :**

```bash
header.php
footer.php
config.php
index.php
sidebar.php
```

* **header.php**

```php
<header>
  <h1><?php echo $siteName; ?></h1>
  <nav>
    <a href="index.php">Accueil</a> |
    <a href="contact.php">Contact</a>
  </nav>
</header>
```

* **footer.php**

```php
<footer>
  <p>&copy; 2025 - Mon site web</p>
</footer>
</body>
</html>
```

* **config.php**

```php
<?php
$siteName = "Mon Site DWWM";
?>
```

* **sidebar.php** (exemple de contenu optionnel)

```php
<aside>
  <h3>Liens utiles</h3>
  <ul>
    <li><a href="#">Article PHP</a></li>
    <li><a href="#">Documentation</a></li>
    <li><a href="#">Tutoriel vidéo</a></li>
  </ul>
</aside>
```

* **index.php**

```php
<?php
// Charger la configuration (obligatoire, une seule fois)
require_once 'config.php';

// Définir un titre de page simple
$pageTitle = "Accueil";
?>
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title><?php echo $siteName . " — " . $pageTitle; ?></title>
  <link rel="stylesheet" href="assets/styles.css" />
</head>
<body>
  <?php
  // Inclure le header (indispensable)
  require_once 'header.php';

  // Inclure une sidebar (optionnelle)
  include 'sidebar.php';
  ?>

  <main class="container">
    <h2>Bienvenue sur la page d'accueil</h2>
    <p>Ceci est le contenu principal.</p>
  </main>

  <?php
  // Inclure le footer (indispensable)
  require_once 'footer.php';
  ?>
```

👉 Résultat attendu : une page avec un **header**, une **sidebar optionnelle**, du **contenu HTML structuré**, et un **footer**.

---

## 4. 🛠️ TP php (mini-portfolio)

### Thème : **Mini-portfolio** (avec tableau multidimensionnel + boucle)

Construis un mini-portfolio de 2 pages qui partagent le même en-tête et pied de page. Les **2 projets** affichés seront générés **automatiquement** depuis un **tableau multidimensionnel** (ex. *Fan site*, *Voyage*).

### Pages à créer

* `index.php` → Présentation + génération dynamique de 2 projets
* `contact.php` → Formulaire de contact (sans traitement serveur pour l’instant)

### Fichiers communs

* `config.php` → variables simples : `$siteName`, `$author`, `$year`, et **`$projects`** (tableau multidimensionnel)
* `header.php` → `<head>` + `<header>` + menu
* `footer.php` → `<footer>` + fermeture HTML

### Étapes guidées

1. Crée le dossier `portfolio/` et un sous-dossier `assets/` avec `styles.css` vide.

2. Dans `config.php`, déclare :

   ```php
   <?php
   $siteName = 'Portfolio DWWM';
   $author   = 'Prénom Nom';
   $year     = '2025';

   // Tableau multidimensionnel des projets (2 items minimum)
   $projects = [
     [
       'title' => 'Fan site',
       'desc'  => 'Création d\'un mini site pour un artiste / série.',
       'link'  => '#'
     ],
     [
       'title' => 'Voyage',
       'desc'  => 'Page de présentation d\'un voyage avec images et texte.',
       'link'  => '#'
     ]
   ];
   ?>
   ```

3. Dans `header.php`, écris le squelette HTML jusqu’à `<header>` avec :

   ```php
   <!DOCTYPE html>
   <html lang="fr">
   <head>
     <meta charset="utf-8" />
     <meta name="viewport" content="width=device-width, initial-scale=1" />
     <title><?php echo $siteName . ' — ' . ($pageTitle ?? ''); ?></title>
     <link rel="stylesheet" href="assets/styles.css" />
   </head>
   <body>
   <header>
     <h1><?php echo $siteName; ?></h1>
     <nav>
       <a href="index.php">Accueil</a> |
       <a href="contact.php">Contact</a>
     </nav>
   </header>
   ```

4. Dans `footer.php`, écris le `<footer>` avec `© <?php echo $year . ' - ' . $author; ?>` puis ferme le `<body>` et `</html>`.

5. Dans `index.php` :

   ```php
   <?php 
    require_once 'config.php'; 
    $pageTitle = 'Accueil'; 
    require_once 'header.php'; 
    ?>

   <main class="container">
     <h2>Bienvenue sur mon portfolio</h2>
     <p>Voici deux projets réalisés lors des dernières séances :</p>
     <section class="grid">
       <?php
       // Afficher uniquement les 2 premiers projets du tableau
       $count = 0;
       foreach ($projects as $project) {
         if ($count >= 2) { break; }
       ?>

         <article class="card">
           <h3><?php echo $project['title']; ?></h3>
           <p><?php echo $project['desc']; ?></p>
           <a href="<?php echo $project['link']; ?>">Voir</a>
         </article>

       <?php
         $count = $count + 1; // incrément simple
       }
       ?>
     </section>
   </main>

   <?php 
   require_once 'footer.php'; 
   ?>
   ```

6. Dans `contact.php` :

   ```php
   <?php 
    require_once 'config.php'; 
    $pageTitle = 'Contact'; 
    require_once 'header.php'; 
    ?>

   <main class="container">
     <h2>Contact</h2>
     <form action="#" method="post">
       <label>Nom <input type="text" name="nom" required></label>
       <label>Email <input type="email" name="email" required></label>
       <label>Message <textarea name="message" rows="5" required></textarea></label>
       <button type="submit">Envoyer</button>
     </form>
   </main>

   <?php 
    require_once 'footer.php'; 
    ?>
   ```

### Aides / Rappels

* `require_once` pour `config.php`, `header.php` et `footer.php` (vitaux, indispensables).
* `include` ou `include_once` pour les fichiers **optionnels** (ex. `sidebar.php`).
* Le **tableau multidimensionnel** permet de stocker plusieurs projets avec plusieurs informations (titre, description, lien).
* La **boucle** `foreach` parcourt chaque projet ; on limite l’affichage à **2 projets** avec un **compteur** et un `break`.

### Vérification

* Si **les 2 articles** (Fan site, Voyage) s’affichent automatiquement depuis `$projects` **c’est réussi** ✅

---

## 5. 🚀 TP (mini site bonus)

### Thème : **Portfolio multi-pages dynamique**

Objectif : consolider tes acquis en structurant un petit site de portfolio plus complet.

### Consigne

Crée un portfolio **3 à 4 pages** :

* `index.php` (Accueil avec présentation personnelle)
* `projets.php` (liste complète des projets)
* `contact.php` (formulaire simple)
* *(facultatif)* `about.php` (présentation détaillée)

### Données

* Dans `config.php`, ajoute au moins **3 projets** dans `$projects` (Fan site, Voyage, +1 autre de ton choix).
* Chaque projet contient : `title`, `desc`, et `link`.

### Instructions

* `index.php` : affiche uniquement une **sélection de 2 projets** (comme dans le TP guidé).
* `projets.php` : affiche **tous les projets** automatiquement avec une boucle `foreach`.
* `contact.php` : formulaire avec Nom, Email, Message (pas de traitement PHP encore).
* `header.php` et `footer.php` : identiques pour toutes les pages.

### Attendus

* Organisation claire des fichiers.
* Utilisation correcte de `require_once` et `include` pour les fichiers optionnels.
* Boucle `foreach` utilisée pour parcourir `$projects`.
* Navigation cohérente entre les pages.
* **Aucune fonction** utilisée (seulement variables, tableaux, boucles).

### Critères de réussite

* Si tu ajoutes un projet dans `$projects`, il apparaît automatiquement dans `projets.php`.
* Modifier le menu dans `header.php` doit se refléter sur toutes les pages.
* Pas de doublons d’inclusions.

---

## 6. 🔧 Exercices pratiques courts

1. Inclure deux fois `config.php` avec `require` → constate l’erreur.
2. Remplacer par `require_once` → constate que l’erreur disparaît.
3. Créer un fichier `boucle-foreach.php` qui déclare un tableau avec 3 valeurs : `"un", "deux", "trois"`. Parcours ce tableau avec une boucle foreach et affiche chaque valeur.
4. Inclure ce fichier avec `include_once` plusieurs fois → vérifie qu’il n’y a pas d’erreur et que les valeurs ne sont affichées qu’une seule fois.

**Comportement attendu :**

* Avec `require`/`include` → doublons possibles.
* Avec `require_once`/`include_once` → aucune redéclaration.

---

### Critères de réussite du TP

* Utilisation correcte des 4 commandes.
* Code organisé et factorisé.
* Site fonctionnel avec navigation cohérente.

### Réflexion

👉 Dans un vrai projet, `include/require` et leurs variantes `_once` sont essentiels pour :

* factoriser ton code
* centraliser les modifications
* éviter les erreurs de maintenance

---

## 7. 📚 Ressources complémentaires

* [Documentation PHP – include](https://www.php.net/manual/fr/function.include.php)
* [Documentation PHP – require](https://www.php.net/manual/fr/function.require.php)
* [Documentation PHP – include\_once](https://www.php.net/manual/fr/function.include-once.php)
* [Documentation PHP – require\_once](https://www.php.net/manual/fr/function.require-once.php)
* Tutoriel visuel : [OpenClassrooms – PHP](https://openclassrooms.com/fr/courses/1665806-programmez-avec-php)
* Astuce : utiliser `__DIR__` pour vérifier les chemins. [DOCUMENTATION PHP - magic constants](https://www.php.net/manual/en/language.constants.magic.php)

---

![footer](https://capsule-render.vercel.app/api?type=waving\&color=gradient\&height=120\&section=footer\&text=%F0%9F%8C%9F%20Continue%20ta%20progression%20en%20PHP%20!%20%F0%9F%9A%80\&fontSize=22)
