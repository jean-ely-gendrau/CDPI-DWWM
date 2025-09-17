# 📘 Support – PHP : Les tableaux (array)

![header](https://capsule-render.vercel.app/api?type=waving\&color=gradient\&height=200\&section=header\&text=PHP%20Arrays\&fontSize=40\&fontAlignY=35\&desc=Tableaux%2C%20Boucles%2C%20Parcours%2C%20Manipulation%20de%20donn%C3%A9es\&descAlignY=55\&descAlign=50)

## 1. 🎓 Introduction

### 🎯 Objectif

Tu vas apprendre à **créer, lire et parcourir des tableaux en PHP**, puis à effectuer des opérations simples (ajouter, modifier, supprimer, compter) sans utiliser de fonctions système avancées.

### 🛠️ Compétences visées (Référentiel DWWM)

* Manipuler des **tableaux indexés, associatifs et multidimensionnels**.
* Utiliser **boucles** et **conditions** pour traiter des collections.
* Écrire un code **lisible** (noms clairs, indentation, commentaires).

### 🌍 Contexte métier

* **E‑commerce** : stocker une liste de produits et calculer un total.
* **Gestion** : tenir une liste d’étudiants et parcourir leurs notes.
* **Projet réel** : préparer des données à afficher dans une page PHP.

---

## 2. 🔹 Théorie

### 📌 Qu’est‑ce qu’un tableau ?

Un **tableau** est une variable qui contient plusieurs valeurs. Chaque valeur est repérée par une **clé** (numérique ou texte).

### 🧩 Types de tableaux

* **Indexés** : clés 0,1,2…
* **Associatifs** : clés nommées (`"nom"`, `"prix"` …).
* **Multidimensionnels** : tableaux contenant d’autres tableaux.

### ✍️ Créer / Lire / Modifier

```php
<?php
// Tableau indexé
$fruits = ["Pomme", "Banane", "Orange"];
echo $fruits[0]; // Pomme

// Tableau associatif
$produit = [
    "nom" => "Clavier",
    "prix" => 29
];
echo $produit["nom"]; // Clavier

// Ajouter / modifier
$fruits[] = "Fraise";        // ajoute en fin
$produit["prix"] = 35;       // met à jour la clé "prix"
```

### 🔁 Parcourir un tableau

```php
<?php
$notes = [12, 15, 9];

// foreach sur les valeurs
foreach ($notes as $note) {
    echo $note . "\n"; // 12 15 9
}

// foreach sur clé + valeur
$etudiant = ["nom" => "Léa", "age" => 21];
foreach ($etudiant as $cle => $valeur) {
    echo $cle . " : " . $valeur . "\n"; // nom : Léa / age : 21
}
```

### ✅ Bonnes pratiques

* Donne des **noms explicites** : `$panier`, `$total`, `$etudiants`.
* **Indente** ton code et commente les étapes importantes.
* Préfère `foreach` quand tu n’as pas besoin de l’index.
* Utilise `isset($tableau["cle"])` pour vérifier l’existence d’une clé avant d’y accéder.

---

## 3. 💻 Démonstration pratique

*(fichier : `demo_moyenne_notes.php`)*

```php
<?php
// Objectif : calculer la moyenne d'un tableau de notes sans fonctions système
$notes = [12, 15, 9, 18, 14];

// 1) Calcul de la somme "à la main"
$somme = 0;               // on démarre à 0
$nbElements = 0;          // on comptera nous-même

foreach ($notes as $note) {
    $somme = $somme + $note; // on ajoute chaque note
    $nbElements = $nbElements + 1; // on incrémente le compteur
}

// 2) Calcul de la moyenne (vérifie qu'il y a au moins 1 élément)
$moyenne = 0;
if ($nbElements > 0) {
    $moyenne = $somme / $nbElements;
}

// 3) Affichage
echo "Somme : " . $somme . "\n";            // 68
echo "Nombre d'éléments : " . $nbElements . "\n"; // 5
echo "Moyenne : " . $moyenne . "\n";        // 13.6
```

> Ici pas de `array_sum` ni `count`, tout est fait **avec une boucle** et des **variables**.

---

## 4. 🛠️ TP PHP (guidés)

### TP 1 – Liste de prénoms numérotée

**Fichier** : `prenoms_liste_numero.php`
**Consigne** : Déclare un tableau de 5 prénoms et affiche‑les numérotés de 1 à N.
**Étapes** :

1. Crée `prenoms_liste_numero.php`.
2. Déclare `$prenoms = ["Jean","Nicolas","Néo","Maya","Zoé"];`.
3. Utilise `foreach` et **un compteur manuel** (`$i = 1;`) pour afficher `1 - Lina`, etc.
4. Si le tableau est vide, affiche `"Aucun prénom"`.
   **Vérification** : 5 lignes de `1 - ...` à `5 - ...`.

---

### TP 2 – Panier simple (total HT)

**Fichier** : `panier_total_ht.php`
**Consigne** : Stocke des produits (nom, prixHT, qte) et calcule le **total HT** sans `array_sum`.
**Étapes** :

1. Crée `panier_total_ht.php`.
2. `$panier = [["nom"=>"Clavier","prix"=>29,"qte"=>2],["nom"=>"Souris","prix"=>15,"qte"=>1]];`
3. Parcours le panier, calcule `ligne = prix * qte`, ajoute à `$total`.
4. Affiche chaque ligne et le total final.
   **Vérification** : total conforme au calcul manuel.

---

### TP 3 – Gestion d’étudiants - ajout de moyenne

**Fichier** : `etudiants_moyennes.php`
**Consigne** : Pour chaque étudiant (nom, notes\[]), calcule la moyenne **sans** `array_sum`/`count`.
**Étapes** :

1. Crée `etudiants_moyenne_sans_fonctions.php`.
2. Déclare un tableau multidimensionnel : `[["nom"=>"Lina","notes"=>[14,16,12]], ...]`.
3. Pour chaque étudiant : somme et compteur manuels, puis moyenne.
4. Ajoute la moyenne à la structure : `$eleve["moyenne"] = ...;`.
5. Affiche `Nom : X - Moyenne : Y`.
   **Vérification** : les moyennes affichées correspondent au calcul à la main.

---

### TP 4 – Recherche d’un élément

**Fichier** : `recherche_prenom_boucle.php`
**Consigne** : Dans un tableau de prénoms, indique si un prénom cible est présent **en utilisant uniquement une boucle**.
**Étapes** :

1. Crée `recherche_prenom_boucle.php`.
2. Déclare `$prenoms = [...]` et une variable `$cible = "Maya";`.
3. Parcours le tableau ; si trouvé, mets `$trouve = true;` et **stoppe la recherche** avec `break;`.
4. Affiche `"Trouvé"` ou `"Non trouvé"`.
5. Sécurise : si `$cible` est vide, affiche un message clair.
   **Vérification** : le script retourne le bon résultat pour des cibles présentes/absentes.

---

## 5. 🚀 TP PHP - les tableaux

**Projet** : *Mini annuaire en mémoire (affichage console/texte)*

* **Fichier** : `annuaire_minimal.php`
* **Objectif** : gérer un tableau de contacts (nom, email, telephone) : affichage de tous les contacts + ajout d’un nouveau contact **en dur dans le code** (pas d’entrée utilisateur), puis ré‑affichage.
* **Contraintes** : pas de fonctions système (hors `isset`), pas de `$_GET`.
* **Critères de réussite** :

  * Noms de variables clairs (`$contacts`, `$nouveauContact`).
  * Ajout correct du nouveau contact (`$contacts[] = ...`).
  * Affichage lisible : `Nom - Email - Téléphone`.

---

## 6. 🔧 Exercices pratiques courts

👉 **Consigne** : crée un fichier `.php` par exercice.

1. Déclarer un tableau de nombres et afficher uniquement les pairs **(ex01\_nombres\_pairs.php)**.
2. Compter manuellement le nombre d’éléments d’un tableau (avec un compteur) **(ex02\_compter\_elements\_manuel.php)**.
3. Trouver la **valeur maximale** d’un tableau sans fonction système **(ex03\_valeur\_max.php)**.
4. Inverser l’ordre d’un tableau **sans** `array_reverse` (construis un nouveau tableau) **(ex04\_inverser\_tableau\_manuel.php)**.
5. Fusionner **manuellement** deux tableaux indexés en un seul **(ex05\_fusion\_manuel\_tableaux.php)**.
6. Vérifier l’existence d’une **clé** dans un tableau associatif avec `isset()` **(ex06\_verifier\_cle\_avec\_isset.php)**.
7. Remplacer toutes les occurrences d’un prénom précis dans un tableau (par boucle) **(ex07\_remplacer\_prenom.php)**.
8. Supprimer un élément à une position donnée (reconstruis le tableau sans cet index) **(ex08\_supprimer\_position\_manuel.php)**.
9. Compter le nombre d’occurrences d’une valeur dans un tableau (boucle + compteur) **(ex09\_compter\_occurrences.php)**.
10. Créer un tableau associatif `produit => prix` et afficher une facture simple (ligne = nom + prix) **(ex10\_facture\_associative\_simple.php)**.

---

## 7. 📚 Ressources complémentaires

* Documentation officielle PHP – **Types array** : [https://www.php.net/manual/fr/language.types.array.php](https://www.php.net/manual/fr/language.types.array.php)
* Documentation officielle PHP – **Variables & bases** : [https://www.php.net/manual/fr/language.variables.php](https://www.php.net/manual/fr/language.variables.php)
* Guide style **PSR‑12** (PHP‑FIG) : [https://www.php-fig.org/psr/psr-12/](https://www.php-fig.org/psr/psr-12/)

---

### 🔭 Pour aller plus loin (optionnel)

Ces exemples utilisent des fonctions système **pour la culture** :

```php
<?php
$nums = [1,2,3,4];
$carres = array_map(fn($n) => $n*$n, $nums); // map
$pairs  = array_filter($nums, fn($n) => $n % 2 === 0); // filter
$total  = array_sum($nums); // reduce/somme
sort($nums); // tri croissant (réindexe)
```

> À garder pour plus tard : ici c’est juste pour te montrer ce que tu pourras utiliser ensuite.

---

![footer](https://capsule-render.vercel.app/api?type=waving\&color=gradient\&height=120\&section=footer\&text=⭐%20Continue%20ta%20progression%20en%20PHP%20!%20🚀\&fontSize=22)
