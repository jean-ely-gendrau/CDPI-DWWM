# 📘 Support – Les fonctions en PHP

---
![header](https://capsule-render.vercel.app/api?type=waving\&color=gradient\&height=200\&section=header\&text=Les%20Fonctions\&fontSize=40\&fontAlignY=35\&desc=PHP\&descAlignY=55\&descAlign=50)

## 1. 🎓 Introduction

### 🎯 Objectif global

Découvrir, comprendre et utiliser les **fonctions en PHP** pour rendre ton code plus clair, plus réutilisable et plus professionnel.

### 🛠️ Compétences visées (référentiel DWWM)

* Développer la partie back-end d’une application web.
* Produire du code structuré, lisible et réutilisable.
* Appliquer les bonnes pratiques de programmation.

### 🌍 Contexte métier

Dans un vrai projet web (site e-commerce, réseau social, blog, application mobile…), il est **impossible de tout écrire en un seul bloc**.
Les **fonctions** te permettent de :

* éviter les répétitions,
* structurer ton code,
* simplifier la maintenance,
* partager des blocs réutilisables avec ton équipe.

**Analogie :** une fonction, c’est comme une **recette de cuisine**.
➡️ Tu l’écris une fois, tu l’exécutes autant de fois que tu veux, en changeant les ingrédients (paramètres).

---

## 2. 📖 Cours

### 🔹 Qu’est-ce qu’une fonction ?

Une fonction est un **bloc de code** qui a un **nom**, qui peut recevoir des **paramètres** et qui peut **renvoyer un résultat**.

**Schéma simplifié :**

```bash
Entrée (paramètres) ---> [ Fonction ] ---> Sortie (résultat)
```

### 🔹 Syntaxe de base

```php
function nom_de_ma_fonction($parametre1, $parametre2) {
    // Bloc de code à exécuter
    return $resultat; // optionnel
}
```

* **function** → mot-clé pour définir une fonction
* **nom\_de\_ma\_fonction** → doit être explicite (snake_case | camelCase)
* **paramètres** → valeurs d’entrée (optionnels)
* **return** → permet de renvoyer une valeur (optionnel)

### 🔹 Exemple simple

```php
function direBonjour($prenom) {
    return "Bonjour " . $prenom . " !";
}

echo direBonjour("Jean"); // Affiche : Bonjour Jean !
```

### 🔹 Types de fonctions

* **Sans paramètre et sans retour**

```php
function afficherMessage() {
    echo "Bienvenue sur le site !";
}
```

* **Avec paramètre(s)**

```php
function carre($nombre) {
    return $nombre * $nombre;
}
```

* **Avec valeur de retour**

```php
$resultat = carre(5); // 25
```

### ✅ Bonnes pratiques

* Donne un **nom clair** à ta fonction (ex: `calculTTC` plutôt que `ctt`)
* Ta fonction doit faire **une seule tâche**
* Indente correctement ton code pour la **lisibilité**
* Ajoute des **commentaires** si nécessaire

---

## 3. 💻 Démonstration pratique 

### Exemple : Calcul de prix TTC

```php
<?php
// Définition de la fonction
function calculTTC($prixHT, $tauxTVA) {
    // Calcule le prix TTC
    $prixTTC = $prixHT + ($prixHT * $tauxTVA / 100);
    return $prixTTC;
}

// Utilisation de la fonction
echo "Prix TTC : " . calculTTC(100, 20) . " €"; // Résultat : 120 €
?>
```

* **Explication pas à pas :**

1. Tu crées une fonction `calculTTC` avec 2 paramètres : `$prixHT`, `$tauxTVA`
2. Tu calcules le TTC dans une variable intermédiaire
3. Tu retournes le résultat avec `return`
4. Tu appelles la fonction et tu affiches le résultat

---

## 4. 🛠️ TP PHP (moyenne de 3 notes)

### Consigne

Crée une fonction qui calcule la **moyenne de 3 notes**.

### Étapes

1. Crée une fonction `moyenne` avec 3 paramètres
2. Fais la somme des notes
3. Divise par 3
4. Retourne le résultat
5. Teste avec des exemples

### Indices

* Addition : `$somme = $n1 + $n2 + $n3;`
* Division : `$somme / 3`

### Vérification

👉 Si `moyenne(10, 15, 20)` retourne `15`, c’est réussi ✅

---

## 5. 🚀 TP PHP  (générer un mot de pass)

### Consigne TP

Crée une fonction `genererMotDePasse($longueur)` qui génère un mot de passe aléatoire de longueur donnée.

### Indications attendues

* Utilise une chaîne de caractères comme base (`abcXYZ123mnu!@#`)
* Parcours la chaîne en boucle pour générer le mot de passe
* Retourne la chaîne finale

### Critères de réussite

* La fonction doit **accepter une longueur** en paramètre
* Le mot de passe doit être **aléatoire et de la bonne taille**

---

## 6. 🔧 Exercices pratiques courts

1. Crée une fonction `saluer($prenom)` qui affiche "Salut \[prenom]".
2. Crée une fonction `carre($n)` qui retourne le carré du nombre.
3. Crée une fonction `estPair($n)` qui retourne `true` si le nombre est pair, `false` sinon.
4. Crée une fonction `convertirEuroDollar($montant, $taux)` qui convertit des euros en dollars.
5. Crée une fonction `maximum($a, $b)` qui retourne le plus grand des deux nombres.
6. Crée une fonction `numeroChance($prenom)` avec un formulaire **POST** qui demande ton prénom et retourne un numéro chance compris entre 1 et 100, stable pour la journée.

---

## 7. 📚 Ressources complémentaires

* [Documentation officielle PHP – Fonctions](https://www.php.net/manual/fr/functions.php)
* [W3Schools – PHP Functions](https://www.w3schools.com/php/php_functions.asp)
* [OpenClassrooms – Fonctions en PHP](https://openclassrooms.com/fr/courses/1732036-programmez-avec-php/1735483-utilisez-les-fonctions)

---

![footer](https://capsule-render.vercel.app/api?type=waving\&color=gradient\&height=120\&section=footer\&text=%F0%9F%8C%9F%20Continue%20ta%20progression%20en%20PHP%20!%20%F0%9F%9A%80\&fontSize=22)
