# 📘 Support – PHP : $\_GET / $\_POST

![header](https://capsule-render.vercel.app/api?type=waving\&color=gradient\&height=200\&section=header\&text=PHP%20Formulaires\&fontSize=40\&fontAlignY=35\&desc=\$_GET%20-%20\$_POST%20-%20Formulaires\&descAlignY=55\&descAlign=50)

---

## 1. 🎓 Introduction

### 🎯 Objectif

Aujourd’hui, tu vas apprendre à utiliser les superglobales **`$_GET`** et **`$_POST`** en PHP pour transmettre et traiter des données de formulaires.

### 🛠️ Compétences visées (Référentiel DWWM)

* Développer la partie back-end d’une application web.
* Manipuler des données issues de formulaires.
* Assurer la sécurité et la validation des entrées utilisateur.

### 🌍 Contexte métier

* **Métier** : Un développeur web doit savoir récupérer et traiter des données envoyées depuis un formulaire (connexion, recherche, contact).
* **Vie quotidienne** : Tu remplis un formulaire d’inscription → tes informations passent en **POST**.
* **Projet réel** : Un moteur de recherche interne utilise **GET** pour afficher les résultats selon tes mots-clés.

---

## 2. 🔹 Théorie

### ✅ Définition

* **`$_GET`** : récupère les données envoyées via l’URL (visible dans la barre d’adresse).
* **`$_POST`** : récupère les données envoyées de manière invisible, via le corps de la requête HTTP.

### ✅ Exemple avec `$_GET`

```php
<?php
// URL : http://www.exemple.com/page.php?nom=Marie&age=25

echo "Bonjour " . $_GET['nom']; // Affiche : Bonjour Marie
echo "<br>";
echo "Tu as " . $_GET['age'] . " ans."; // Affiche : Tu as 25 ans
?>
```

![Schéma URL avec paramètres GET](./img/php-url-schema-get.png)
*Illustration : structure d’une URL avec protocole, domaine, chemin et paramètres GET.*

### ✅ Exemple avec `$_POST`

```php
<!-- fichier form.php -->
<form action="traitement.php" method="post">
  <input type="text" name="prenom" placeholder="Ton prénom">
  <input type="submit" value="Envoyer">
</form>
```

```php
<?php
// fichier traitement.php
echo "Ton prénom est " . $_POST['prenom'];
?>
```

### ✅ Bonnes pratiques

* Toujours vérifier si la variable existe avant de l’utiliser :

  ```php
  if (isset($_POST['prenom'])) { ... }
  ```
* Nommer les variables de manière claire (`$prenom`, `$email`).
* Bien indenter et commenter le code.

---

## 3. 💻 Démonstration pratique

![Schéma Cycle HTTP](./img/php-entete-request.png)
*Illustration : cycle complet Client → Requête HTTP → Serveur PHP → Réponse HTML.*

Créons un petit formulaire de connexion :

```php
<!-- login.php -->
<form action="login_traitement.php" method="post">
  <label>Utilisateur :</label>
  <input type="text" name="username"><br>
  
  <label>Mot de passe :</label>
  <input type="password" name="password"><br>
  
  <input type="submit" value="Se connecter">
</form>
```

```php
<?php
// login_traitement.php
if (isset($_POST['username']) && isset($_POST['password'])) {
    $user = $_POST['username'];
    $pass = $_POST['password'];

    if ($user === "admin" && $pass === "1234") {
        echo "✅ Connexion réussie, bienvenue $user !";
    } else {
        echo "❌ Identifiants incorrects.";
    }
} else {
    echo "Merci de remplir le formulaire.";
}
?>
```

---

## 4. 🛠️ TP PHP (guidés)

![Schéma GET vs POST](./img/get-vs-post.png)
*Comparaison visuelle entre les méthodes GET et POST.*

### TP 1 – Formulaire GET

**Consigne** : Crée un formulaire demandant un prénom et l’âge. Affiche-les dans une page résultat via `$_GET`.

**Étapes** :

1. Crée un fichier `form1.php`.
2. Ajoute un formulaire avec méthode `GET`.
3. Dans `result1.php`, récupère et affiche les données.

**Vérification** : URL doit ressembler à `result1.php?prenom=Paul&age=22`.

---

### TP 2 – Formulaire POST

**Consigne** : Crée un formulaire de contact (nom, email, message). Affiche les données avec `$_POST`.

**Étapes** :

1. Fichier `form2.php`.
2. Formulaire avec `method="POST"`.
3. Page `result2.php` affiche les données.

**Vérification** : Les infos ne doivent **pas** apparaître dans l’URL.

---

### TP 3 – Formulaire + Condition

**Consigne** : Crée un formulaire demandant un mot de passe. Vérifie si c’est `dwwm2025`.

**Étapes** :

1. Crée `form3.php`.
2. Utilise `method="POST"`.
3. Dans `result3.php`, affiche ✅ ou ❌.

**Vérification** : Entrer `dwwm2025` → succès.

---

### TP 4 – Formulaire de calcul

**Consigne** : Crée un formulaire demandant deux nombres. Calcule la somme.

**Étapes** :

1. `form4.php` → deux champs numériques.
2. `result4.php` → affiche la somme.

**Vérification** : 5 + 7 doit donner 12.

---

## 5. 🚀 TP PHP (les donées avec $_GET)

**Consigne** : Crée un petit formulaire de recherche de film.

* L’utilisateur saisit un titre → la page affiche “Résultats pour : TITRE”.
* Critères de réussite :

  * Le champ de recherche utilise `GET`.
  * Si aucun titre n’est saisi, affiche un message “Merci d’entrer un titre”.

---

## 6. 🔧 Exercices pratiques courts

👉 Consigne : crée un fichier `.php` par exercice.

### Exercice 1 – Afficher `$_GET`

* **Fichier** : `exo1_get.php`
* **Consigne** : Crée une page qui affiche le contenu complet de `$_GET` avec `print_r()`.
* **Résultat attendu** : En accédant à `exo1_get.php?nom=Paul&age=30`, la page doit afficher un tableau avec les valeurs.

### Exercice 2 – Formulaire prénom

* **Fichier** : `exo2_prenom.php`
* **Consigne** : Formulaire demandant un prénom (POST). Affiche : “Bonjour PRENOM”.
* **Résultat attendu** : Si on tape “Marie” → affiche `Bonjour Marie`.

### Exercice 3 – Carré d’un nombre

* **Fichier** : `exo3_carre.php`
* **Consigne** : Formulaire avec champ numérique. Affiche le carré du nombre.
* **Résultat attendu** : Entrée `5` → affiche `Le carré de 5 est 25`.

### Exercice 4 – Plus grand nombre

* **Fichier** : `exo4_max.php`
* **Consigne** : Formulaire demandant deux nombres. Affiche le plus grand.
* **Résultat attendu** : 8 et 3 → affiche `Le plus grand est 8`.

### Exercice 5 – Case à cocher

* **Fichier** : `exo5_checkbox.php`
* **Consigne** : Formulaire avec case “J’accepte les conditions”. Affiche message selon choix.
* **Résultat attendu** : ✅ Conditions acceptées ou ❌ Tu dois accepter.

### Exercice 6 – Choisir une couleur

* **Fichier** : `exo6_couleur.php`
* **Consigne** : Formulaire demandant une couleur (input type="color"). Affiche un texte avec cette couleur.
* **Résultat attendu** : Choisir rouge → texte en rouge.

### Exercice 7 – Année bissextile

* **Fichier** : `exo7_bissextile.php`
* **Consigne** : Formulaire demandant une année. Vérifie si elle est bissextile.
* **Résultat attendu** : 2024 → bissextile ; 2023 → pas bissextile.

### Exercice 8 – Email en minuscules

* **Fichier** : `exo8_email.php`
* **Consigne** : Formulaire demandant un email. Affiche-le en minuscules.
* **Résultat attendu** : `Paul.Dupond@EXEMPLE.Com` → `paul.dupond@exemple.com`.

### Exercice 9 – Majeur ou mineur

* **Fichier** : `exo9_age.php`
* **Consigne** : Formulaire demandant un âge. Affiche majeur ou mineur.
* **Résultat attendu** : 16 → mineur ; 21 → majeur.

### Exercice 10 – Longueur d’un mot

* **Fichier** : `exo10_longueur.php`
* **Consigne** : Formulaire demandant un mot. Affiche son nombre de lettres.
* **Résultat attendu** : `bonjour` → contient 7 lettres.

---

## 7. 📚 Ressources complémentaires

* [Documentation PHP – $\_GET](https://www.php.net/manual/fr/reserved.variables.get.php)
* [Documentation PHP – $\_POST](https://www.php.net/manual/fr/reserved.variables.post.php)
* [W3Schools – PHP Forms](https://www.w3schools.com/php/php_forms.asp)

---

![footer](https://capsule-render.vercel.app/api?type=waving\&color=gradient\&height=120\&section=footer\&text=⭐%20Continue%20ta%20progression%20en%20PHP%20!%20🚀\&fontSize=22)
