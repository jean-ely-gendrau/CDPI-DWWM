# 📘 Support – PHP : Les boucles

![header](https://capsule-render.vercel.app/api?type=waving\&color=gradient\&height=200\&section=header\&text=Les%20Boucles-PHP\&fontSize=40\&fontAlignY=35\&desc=while%20do...while%20for\&descAlignY=55\&descAlign=50)

## 1. 🎓 Introduction

### 🎯 Objectif

Aujourd’hui, tu vas apprendre à utiliser les **boucles en PHP** (`while`, `do...while`, `for`) pour automatiser des actions répétitives dans tes scripts.

### 🛠️ Compétences visées (Référentiel DWWM)

* Écrire du **code PHP clair et structuré**.
* Utiliser des **boucles de contrôle** pour répéter des actions.
* Déboguer un script pour éviter les **boucles infinies**.

### 🌍 Contexte métier

* Compter des données (ex. nombre d’utilisateurs connectés).
* Afficher des listes (messages, produits, résultats).
* Traiter une chaîne caractère par caractère.

👉 Les boucles te permettent d’automatiser ce qui serait trop long à écrire ligne par ligne.

---

## 2. 🔹 Qu’est-ce qu’une boucle ?

Une **boucle** répète un bloc d’instructions tant qu’une **condition est vraie** (`while`, `do...while`) ou pendant un **nombre défini de fois** (`for`).

Exemple concret :

* Tu veux afficher les nombres de 1 à 10 → inutile d’écrire 10 fois `echo`. Tu utilises une boucle.

En PHP :

```php
for ($i = 1; $i <= 10; $i++) {
    echo $i . "<br>";
}
```

---

### 🔹 Les types de boucles

**1. while** : teste la condition **avant** d’exécuter.

```php
$i = 1;
while ($i <= 5) {
    echo $i . "<br>";
    $i++;
}
```

**2. do...while** : exécute **au moins une fois**.

```php
$i = 1;
do {
    echo $i . "<br>";
    $i++;
} while ($i <= 5);
```

**3. for** : défini avec compteur.

```php
for ($i = 1; $i <= 5; $i++) {
    echo $i . "<br>";
}
```

---

### 🔹 Bonnes pratiques DWWM

* Indente toujours ton code.
* Mets des **commentaires courts**.
* Choisis des noms clairs : `$i`, `$compteur`.
* Prévoy toujours une **condition de sortie**.

---

## 3. 💻 Démonstration pratique

👉 Exemple : Affiche les **10 premiers nombres pairs**.

```php
<?php
for ($i = 1; $i <= 10; $i++) {
    $pair = $i * 2;
    echo "Nombre pair : $pair <br>";
}
?>
```

---

## 4. 🛠️ TP PHP (les boucles)

### TP 1 – Le compteur de séances

**Consigne** :
Crée un fichier `entrainement.php`. Écris un script qui affiche :

```html
Séance n°1 terminée  
Séance n°2 terminée  
... jusqu’à Séance n°12 terminée
```

**Étapes** :

1. Crée ton fichier PHP.
2. Mets en place une boucle `for` de 1 à 12.
3. Affiche la phrase avec le compteur.

**Vérification** : tu dois avoir exactement 12 lignes, la dernière étant `Séance n°12 terminée`.

---

### TP 2 – Décoder un message

**Consigne** :
Crée un fichier `decoder.php`. Ton script doit parcourir la chaîne :

```html
"Coder tous les jours, un petit pas à la fois"
```

… et afficher **un caractère sur deux**.

**Étapes** :

1. Crée ton fichier.
2. Stocke la chaîne dans `$str`.
3. Utilise une boucle `for` avec un pas de 2.
4. Concatène et affiche le résultat.

**Vérification** : la sortie doit contenir environ la moitié des caractères.

---

### TP 3 – Filtrer les voyelles

**Consigne** :
Crée un fichier `voyelles.php`. Écris un script qui affiche uniquement les voyelles de :

```html
"Apprendre PHP demande de la pratique"
```

**Étapes** :

1. Crée ton fichier.
2. Parcours chaque caractère avec une boucle.
3. Vérifie si le caractère est une voyelle (`aeiouyAEIOUY`).
4. Affiche uniquement les voyelles.

**Vérification** : le texte affiché doit être composé uniquement de voyelles.

---

### TP 4 – Compter les caractères

**Consigne** :
Crée un fichier `compteur.php`. Ton script doit compter le nombre de caractères dans :

```html
"La répétition fait le maître"
```

**Étapes** :

1. Crée ton fichier.
2. Parcours la chaîne avec une boucle.
3. Incrémente un compteur à chaque tour.
4. Affiche le total.

**Vérification** : compare le résultat avec `strlen($str)`.

---

## 5. 🚀 TP PHP

### Le parcours d’apprentissage

**Consigne** :
Crée un fichier `progression.php` qui simule un plan de progression sur **14 jours**.

* Jours impairs : affiche `Jour X : exercice de boucles`.
* Jours pairs : affiche `Jour X : révision et quiz`.

**Étapes** :

1. Crée ton fichier.
2. Mets une boucle `for` de 1 à 14.
3. Ajoute une condition pour différencier pair/impair.
4. Affiche la ligne correspondante.

**Vérification** : tu dois avoir 14 lignes, et afficher aussi :

```html
Total d’itérations : 14
```

---

## 6. 🔧 Exercices pratiques courts

> 👉 Consigne : crée un fichier par exercice. Tu peux tester directement dans ton navigateur.

1. **Comptage contrôlé** : affiche de 0 à 20 par pas de 5.
2. **Compte à rebours** : affiche de 10 à 0, puis `Départ !`.
3. **Sélecteur d’indices** : affiche les indices pairs d’une chaîne donnée.
4. **Filtre de type** : parcours une chaîne et affiche uniquement les lettres (ignore espaces et ponctuation).
5. **Multiples ciblés** : affiche les multiples de 3 entre 3 et 30.

---

## 7. 📚 Ressources complémentaires

* [PHP – Boucles](https://www.php.net/manual/fr/control-structures.for.php)
* [Documentation PHP officielle](https://www.php.net/manual/fr/)

---

![footer](https://capsule-render.vercel.app/api?type=waving\&color=gradient\&height=120\&section=footer\&text=%F0%9F%8C%9F%20Continue%20ta%20progression%20en%20PHP%20!%20%F0%9F%9A%80\&fontSize=22)
