# 📘 Support – PHP Connecteur MySQL (MySQLi & PDO)

## 1. 🎓 Introduction

### Objectif global

Aujourd’hui, tu vas apprendre à connecter ton code PHP à une base de données MySQL. Tu verras deux méthodes : **MySQLi** et **PDO**. Tu vas aussi comprendre comment exécuter des requêtes et afficher les résultats.

### Compétences visées (DWWM)

* Te connecter à une base de données depuis un script PHP.
* Exécuter des requêtes SQL avec PHP.
* Afficher des résultats dans une page web.

### Contexte métier

Dans un vrai projet (site e-commerce, réseau social, application métier…), les données sont stockées dans une base de données. Sans connexion PHP–MySQL, impossible d’afficher des produits, de gérer des comptes utilisateurs ou de stocker des messages.

---

## 2. 📖 Cours

### 2.1 Les connecteurs MySQL

* **MySQLi** : simple, rapide, mais uniquement pour MySQL.
* **PDO** : plus moderne, orienté objet, compatible avec plusieurs bases (MySQL, PostgreSQL, SQLite…).

👉 Imagine un **adaptateur électrique** : ton code PHP est la prise, la base MySQL est la centrale, et le connecteur (MySQLi ou PDO) est l’adaptateur qui permet le branchement.

### 2.2 Connexion MySQLi ([programmation procédural](https://fr.wikipedia.org/wiki/Programmation_proc%C3%A9durale))

```php
<?php
$conn = mysqli_connect("localhost", "root", "", "jour09");

if (!$conn) {
    die("Erreur de connexion : " . mysqli_connect_error());
}
echo "Connexion réussie !";
?>
```

### 2.3 Connexion PDO ([programmation orientée object](https://fr.wikipedia.org/wiki/Programmation_orient%C3%A9e_objet))

```php
<?php
try {
    $pdo = new PDO("mysql:host=localhost;dbname=jour09", "root", "");
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    echo "Connexion réussie !";
} catch (PDOException $e) {
    echo "Erreur : " . $e->getMessage();
}
?>
```

### 2.4 Bonnes pratiques

* Toujours tester la connexion.
* Utiliser `try/catch` avec PDO.
* Utiliser des **requêtes préparées** pour éviter l’injection SQL.
* Fermer la connexion en fin de script.

---

## 3. 💻 Démonstration pratique

Affichons tous les étudiants de la table `etudiants` avec PDO :

```php
<?php
try {
    $pdo = new PDO("mysql:host=localhost;dbname=jour09", "root", "");
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    $sql = "SELECT prenom, nom, naissance FROM etudiants";
    $stmt = $pdo->query($sql);

    echo "<table border='1'>";
    echo "<tr><th>Prénom</th><th>Nom</th><th>Date de naissance</th></tr>";

    while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
        echo "<tr>";
        echo "<td>" . $row['prenom'] . "</td>";
        echo "<td>" . $row['nom'] . "</td>";
        echo "<td>" . $row['naissance'] . "</td>";
        echo "</tr>";
    }

    echo "</table>";

} catch (PDOException $e) {
    echo "Erreur : " . $e->getMessage();
}
?>
```

---

## 4. 🛠️ TP jour09 avec php

### Objectif

Afficher les données de ta base existante (`etudiants`, `salles`, `etage`) avec MySQLi puis avec PDO.

### Étapes

1. Connecte-toi à ta base avec **MySQLi**.
2. Exécute une requête simple (par ex. `SELECT * FROM etudiants`).
3. Affiche les résultats dans un tableau HTML.

👉 Si tu vois apparaître la liste des prénoms et noms dans ton navigateur, c’est gagné !

---

## 5. 🚀 TP php-sql

### Objectif (tp php-sql)

Crée une nouvelle base `bibliotheque` avec une table `livres` :

* id (int, AI, PK)
* titre (varchar 255)
* auteur (varchar 255)
* annee (int)

Ensuite :

1. Insère quelques livres.
2. Affiche-les dans un tableau HTML avec PDO.
3. (Bonus) Ajoute un formulaire qui permet d’insérer un nouveau livre.

👉 Critères de réussite : connexion fonctionnelle, affichage correct, ajout possible.

---

## 6. 🔧 Exercices pratiques courts

1. Affiche uniquement les prénoms des étudiants.
2. Affiche les salles triées par capacité décroissante.
3. Compte le nombre total d’étudiants.
4. Calcule la capacité moyenne des salles.
5. Affiche uniquement les étudiantes.

💡 Astuce : utilise les requêtes vues dans le cours, mais exécute-les cette fois avec PHP.

---

### Critères de réussite

* Tu arrives à afficher des données depuis ta base.
* Tu peux modifier la requête pour obtenir un autre résultat.

---

## 7. 📚 Ressources complémentaires

* [Doc officielle PDO](https://www.php.net/manual/fr/book.pdo.php)
* [Doc officielle MySQLi](https://www.php.net/manual/fr/book.mysqli.php)
* [Cours SQL (sql.sh)](https://sql.sh/)
