# Support — PHP Hello Worl

![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=200&section=header&text=Hello%20Worl-PHP&fontSize=40&fontAlignY=35&desc=Les%20bases&descAlignY=55&descAlign=50)

## 🎓 Introduction

## Objectif global

Découvrir PHP avec Laragon 6 et apprendre à utiliser la commande **`echo`** pour afficher du texte dynamique. Tu vas créer tes premiers fichiers PHP et les exécuter dans ton navigateur.

## Compétences visées (référentiel DWWM)

* Installer et configurer un environnement de développement (Laragon).
* Créer et exécuter un fichier PHP.
* Utiliser `echo` pour générer du contenu dynamique.
* Respecter les bonnes pratiques d’écriture et de lisibilité du code.

## Contexte métier

Dans un site web, **afficher du contenu** est essentiel : titres, messages de bienvenue, résultats de calculs ou données issues d’une base. PHP permet de produire ce contenu en fonction de l’utilisateur. Tu vas découvrir la toute première pierre de cette logique.

---

## Qu’est-ce que PHP ?

* PHP(Hypertext Preprocessor) est un **langage de programmation côté serveur**.
* Il est exécuté sur le serveur et envoie du HTML au navigateur.
* Créé en 1994 par Rasmus Lerdorf, il est encore largement utilisé (WordPress, Laravel, Drupal, Prestashop…).
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
* Nommer ses fichiers clairement (ex : hello.php).

---

## 💻 Démonstration pratique

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

    ```html
    http://localhost/hello.php
    ```

    ✅ Résultat attendu :

    ```html
    Bienvenue dans la formation DWWM - Toulon
    ```

---

## 🛠️ TP PHP **echo**

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

```php
DWWM - TOULON
Première séance de PHP
Tu apprends à utiliser echo
```

---

## 🚀 TP PHP *autonome*

## Consigne

Crée une page PHP appelée `presentation.php` qui affiche :

* Ton prénom.
* La phrase : *Je suis en formation DWWM à Toulon*.
* Une phrase libre que tu inventes.

## Attendus

* Chaque phrase apparaît sur une ligne distincte (utilise `<br>` si besoin).
* Le code est bien indenté et commenté.

---

## ✅ Évaluation et auto-évaluation

### Vérifie

* As-tu lancé Laragon et créé un fichier PHP ?
* Le fichier affiche-t-il bien toutes les lignes demandées ?
* Ton code est-il clair, indenté et commenté ?

### Réflexion

Comment utiliser `echo` dans un vrai projet ? Par exemple :

* Afficher le prénom de l’utilisateur après connexion.
* Montrer le contenu d’un panier d’achat.
* Présenter un message adapté selon l’heure de la journée.

---

## 📚 Ressources complémentaires

* [Documentation officielle PHP](https://www.php.net/manual/fr/)
* [Site officiel Laragon](https://laragon.org/)
* [W3Schools – PHP Echo](https://www.w3schools.com/php/php_echo_print.asp)
* [OpenClassrooms – Découvre PHP](https://openclassrooms.com/fr/courses/6173501-decouvrez-le-langage-php)

![footer](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=120&section=footer&text=%F0%9F%8C%9F%20Mettez%20une%20%2A%20si%20vous%20avez%20aim%C3%A9%20ce%20TP%20!%20%F0%9F%9A%80&fontSize=22)