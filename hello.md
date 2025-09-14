# 🎓 Introduction pédagogique

## Objectif global du cours

Découvrir PHP avec Laragon 6 et apprendre à utiliser la commande **`echo`** pour afficher du texte dynamique. Tu vas créer tes premiers fichiers PHP et les exécuter dans ton navigateur.

## Compétences visées (référentiel DWWM)

* Installer et configurer un environnement de développement (Laragon).
* Créer et exécuter un fichier PHP.
* Utiliser `echo` pour générer du contenu dynamique.
* Respecter les bonnes pratiques d’écriture et de lisibilité du code.

## Contexte métier

Dans un site web, **afficher du contenu** est essentiel : titres, messages de bienvenue, résultats de calculs ou données issues d’une base. PHP permet de produire ce contenu en fonction de l’utilisateur. Tu vas découvrir la toute première pierre de cette logique.

---

# 📖 Cours théorique

### Qu’est-ce que PHP ?

* PHP est un **langage de programmation côté serveur**.
* Il permet de créer des pages **dynamiques** qui s’adaptent selon les besoins.
* Avec **Laragon**, tu disposes d’un serveur local simple et rapide pour exécuter ton code.

### La commande `echo`

* `echo` sert à **envoyer du texte ou du code HTML** vers ton navigateur.
* Exemple minimal :

```php
<?php
echo "Bonjour";
?>
```

➡️ Ici, PHP renvoie simplement le texte *Bonjour* dans ton navigateur.

### Bonnes pratiques

* **Toujours commenter ton code** : explique ce que tu fais.
* **Indente** correctement : le code doit être lisible.
* Utilise les **guillemets doubles** pour tes chaînes de texte.

### Les types primitifs en PHP

Pour manipuler des données, PHP utilise différents **types primitifs** :

* **String (chaîne de caractères)** : texte, ex. `"DWWM - Toulon"`
* **Integer (entier)** : nombre sans décimales, ex. `42`
* **Float (nombre à virgule)** : ex. `3.14`
* **Boolean (booléen)** : vrai ou faux (`true` / `false`)

Exemples :

```php
<?php
// Texte
$formation = "DWWM - Toulon";

// Nombre entier
$nbApprenants = 25;

// Nombre décimal
$tauxReussite = 95.5;

// Booléen
$inscriptionOuverte = true;

echo $formation;
echo "<br>Apprenants : $nbApprenants";
echo "<br>Taux de réussite : $tauxReussite%";
echo "<br>Inscription ouverte ? $inscriptionOuverte";
?>
```

➡️ Les variables permettent de stocker et afficher différents types de données.

---

# 💻 Démonstration pratique (live coding)

1. Ouvre **Laragon 6** et démarre Apache.
2. Va dans le dossier `www` de Laragon.
3. Crée un fichier nommé `hello.php`.
4. Écris ce code :

```php
<?php
// Premier affichage avec echo
echo "Bienvenue dans la formation DWWM - Toulon";
?>
```

👉 Dans ton navigateur, saisis :

```
http://localhost/hello.php
```

✅ Résultat attendu :

```
Bienvenue dans la formation DWWM - Toulon
```

---

# 🛠️ TP guidé (atelier pratique encadré)

## Objectif

Pratiquer l’instruction `echo` en affichant plusieurs lignes de texte.

## Étapes

1. Crée un fichier `dwwm.php` dans le dossier `www`.
2. Ajoute ce code :

```php
<?php
// Première page PHP autour de la formation
echo "DWWM - TOULON";
echo "<br>Première séance de PHP";
echo "<br>Tu apprends à utiliser echo";
?>
```

3. Ouvre `http://localhost/dwwm.php` dans ton navigateur.

✅ Résultat attendu :

```
DWWM - TOULON
Première séance de PHP
Tu apprends à utiliser echo
```

---

# 🛠️ TP guidé (atelier pratique encadré) – Variables et types

## Objectif

Découvrir les **types primitifs** de PHP en créant des variables et en les affichant avec `echo`.

## Étapes

1. Crée un fichier `types.php` dans le dossier `www`.
2. Ajoute ce code :

```php
<?php
// Chaîne de caractères
$formation = "Formation DWWM Toulon";

// Entier
$nbApprenants = 20;

// Décimal
$tauxPresence = 98.5;

// Booléen
$pauseCafe = false;

echo $formation;
echo "<br>Nombre d'apprenants : $nbApprenants";
echo "<br>Taux de présence : $tauxPresence%";
echo "<br>Pause café en cours ? $pauseCafe";
?>
```

3. Ouvre `http://localhost/types.php` dans ton navigateur.

✅ Résultat attendu :

```
Formation DWWM Toulon
Nombre d'apprenants : 20
Taux de présence : 98.5%
Pause café en cours ?
```

💡 Tu remarques que le booléen s’affiche comme `1` pour `true` ou rien pour `false`.

---

# 🎯 Exercices pratiques (autour de echo et des types primitifs)

Voici une série d’exercices centrés uniquement sur **l’instruction echo** et les **types primitifs** de PHP. Crée un fichier par exercice ou regroupe-les dans un seul fichier en commentant/décommentant.

1. **Texte simple**
   Affiche avec `echo` : `DWWM – TOULON`

2. **Deux lignes**
   Affiche :
   `Formation DWWM`
   `Ville : Toulon`

3. **String + Integer**
   Crée une variable `$apprenants = 20;` et affiche :
   `Apprenants inscrits : 20`

4. **Float**
   Crée une variable `$taux = 95.5;` et affiche :
   `Taux de réussite : 95.5%`

5. **Boolean**
   Crée `$ouvert = true;` et affiche :
   `Inscriptions ouvertes : oui` si vrai, sinon `non`.

6. **Concaténation**
   Crée deux variables `$prenom` et `$nom`, affiche :
   `Bonjour {prenom} {nom}`

7. **Somme simple**
   Crée `$a = 7; $b = 5;` et affiche :
   `La somme de 7 et 5 est : 12`

8. **Soustraction**
   Crée `$x = 12; $y = 4;` et affiche :
   `Résultat : 8`

9. **Division entière**
   Crée `$n = 25; $d = 4;` et affiche le quotient avec `intdiv()` et le reste avec `%`.

10. **Moyenne de notes**
    Crée trois variables de type **int** pour les notes, calcule la moyenne et affiche :
    `Moyenne : 16`

11. **Texte avec guillemets**
    Affiche avec `echo` : `Aujourd"hui, tu codes en "PHP" à DWWM – TOULON.`

12. **Variable float formatée**
    Crée `$prix = 19.99;` et affiche :
    `Prix : 19.99 €`

13. **Page d’accueil**
    Avec `echo`, affiche en HTML un `<h1>` : `Bienvenue` et un `<p>` : `Formation DWWM – TOULON`.

14. **Année courante**
    Affiche avec `echo` : `© 2025 Formation DWWM – TOULON` (utilise `date("Y")`).

15. **Fiche apprenant**
    Crée plusieurs variables (string, int, float, bool) et affiche une petite fiche : prénom, âge, moyenne, inscription.

---

# 🚀 TP autonome (mise en pratique libre)

(mise en pratique libre)

## Consigne

Crée une page PHP appelée `presentation.php` qui affiche :

* Ton prénom.
* La phrase : *Je suis en formation DWWM à Toulon*.
* Une phrase libre que tu inventes.

## Attendus

* Chaque phrase apparaît sur une ligne distincte (utilise `<br>` si besoin).
* Le code est bien indenté et commenté.

---

# ✅ Évaluation et auto-évaluation

### Vérifie :

* As-tu lancé Laragon et créé un fichier PHP ?
* Le fichier affiche-t-il bien toutes les lignes demandées ?
* Ton code est-il clair, indenté et commenté ?

### Réflexion

Comment utiliser `echo` dans un vrai projet ? Par exemple :

* Afficher le prénom de l’utilisateur après connexion.
* Montrer le contenu d’un panier d’achat.
* Présenter un message adapté selon l’heure de la journée.

---

# 📚 Ressources complémentaires

* [Documentation officielle PHP](https://www.php.net/manual/fr/)
* [Site officiel Laragon](https://laragon.org/)
* [W3Schools – PHP Echo](https://www.w3schools.com/php/php_echo_print.asp)
* [OpenClassrooms – Découvre PHP](https://openclassrooms.com/fr/courses/6173501-decouvrez-le-langage-php)
