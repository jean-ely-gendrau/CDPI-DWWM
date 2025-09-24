# 📘 Support – PHP `$_SESSION` & `$_COOKIE`

---

## 1. 🎓 Introduction

### 🎯 Objectif global

À la fin de ce document, tu sauras **mémoriser des informations entre plusieurs pages** grâce aux **sessions** et aux **cookies** en PHP.

### 🧩 Compétences visées (référentiel DWWM)

* Utiliser des **superglobales** PHP (`$_SESSION`, `$_COOKIE`).
* Persister des **préférences simples** (langue, thème) et des **données utilisateur** (prénom, compteur).
* Appliquer des **bonnes pratiques** (sécurité, destruction, durée de vie).

### 🏢 Contexte métier

* Connexion utilisateur (qui est connecté ?).
* Panier / préférences de navigation (langue, thème).
* Petits jeux / interactions (score, tour du joueur).

---

## 2. 📖 Cours

### 2.1. HTTP est **sans mémoire**

Quand tu passes d’une page à l’autre, le serveur **oublie** qui tu es. On a donc besoin d’outils pour « se souvenir ».

**Analogie** : Tu entres dans une boulangerie → tu ressors → tu reviens… Le boulanger ne te reconnaît pas automatiquement.

### 2.2. Deux outils pour retenir : **cookies** & **sessions**

### **Cookies (🍪)**

* **Où ?**
    Dans le **navigateur**.
* **Quand ?**
    Peuvent durer **après** fermeture du navigateur (si date d’expiration).
* **Pour quoi ?**
    Préférences (langue, thème), reconnaitre un visiteur.

### **Sessions (🗝️)**

* **Où ?**

    Sur le **serveur** (via un identifiant de session, souvent stocké dans un cookie `PHPSESSID`).

* **Quand ?**

    En général **jusqu’à la fermeture** du navigateur ou un délai d’inactivité.

* **Pour quoi ?**

    Données plus sensibles (qui est connecté, panier sécurisé, droits).

### 2.3. Schéma (texte) pour visualiser

```bash
[Navigateur] --(cookie PHPSESSID)--> [Serveur]
[Navigateur] <--(html)------------ [Serveur]
         \-- cookies (thème, langue) --/
```

* Le **cookie** peut contenir de petites infos non sensibles (ou juste l’ID de la session).
* La **session** garde tes données côté serveur (plus sûr pour les infos importantes).

### 2.4. Règles d’or à retenir

1. **Toujours** démarrer la session **tout en haut** du script : `session_start();`
2. Lire/écrire comme dans un tableau : `$_SESSION['cle']`, `$_COOKIE['cle']`.
3. Pour **supprimer** : `session_destroy()` (et éventuellement `$_SESSION = [];`) ; pour un cookie, le recréer **expiré** : `setcookie('nom', '', time() - 3600);`
4. **Jamais** de mot de passe en clair dans un cookie.

### 2.5. Différences clés (mémo)

| Critère        | Cookies (🍪)        | Sessions (🗝️)          |
| -------------- | ------------------- | ----------------------- |
| Stockage       | Navigateur (client) | Serveur                 |
| Sécurité       | Moins sécurisé      | Plus sécurisé           |
| Taille approx. | \~4 Ko              | + grand (selon serveur) |
| Durée          | Paramétrable        | Session de navigation   |

---

## 3. 💻 Démonstration pratique

> Objectif : tu reproduis **à l’identique** pour te faire la main. Code **commenté**.

### 3.1. Compteur simple en **session**

```php
<?php
// 1) Toujours démarrer la session AVANT tout HTML
session_start();

// 2) Initialiser si première visite
if (!isset($_SESSION['compteur'])) {
    $_SESSION['compteur'] = 1; // première visite
} else {
    $_SESSION['compteur']++; // visites suivantes
}

// 3) Afficher la valeur
echo "Nombre de visites (session) : " . $_SESSION['compteur'];

// 4) Bouton pour remettre à zéro
?>
<form method="post">
    <button type="submit" name="reset">Remettre à zéro</button>
</form>
<?php
// 5) Traitement du reset
if (isset($_POST['reset'])) {
    $_SESSION['compteur'] = 0; // on remet à zéro
    // optionnel : header('Location: index.php'); exit; // pour recharger proprement
}
?>
```

### 3.2. Préférence de **thème** via **cookie**

```php
<?php
// Créer/mettre à jour un cookie 'theme' pour 1 heure
if (isset($_POST['theme'])) {
    setcookie('theme', $_POST['theme'], time() + 3600); // 3600 secondes = 1h
    // Après setcookie, un refresh peut être utile pour voir la valeur dans $_COOKIE
    header('Location: ' . $_SERVER['PHP_SELF']);
    exit;
}

$theme = $_COOKIE['theme'] ?? 'non défini';
echo "Thème actuel : " . htmlspecialchars($theme);
?>
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Choix du thème</title>

    <?php 
    // --- Application du CSS en fonction du thème ---
    // --- Crée deux fichiers CSS (clair.css et sombre.css) et utilise des classes sur des balises HTML
    //     pour observer visuellement le changement de style ---
    // On inclut le fichier clair.css ou sombre.css dynamiquement
    if ($theme === 'sombre'): ?>
        <link rel="stylesheet" href="sombre.css">
    <?php else: ?>
        <link rel="stylesheet" href="clair.css">
    <?php endif; ?>
</head>
<body>
    <!-- Affichage du thème actuel -->
    <h2>Thème actuel : <?= htmlspecialchars($theme) ?></h2>
    <form method="post">
        <label>Choisis un thème :</label>
        <select name="theme">
            <option value="clair">Clair</option>
            <option value="sombre">Sombre</option>
        </select>
        <button type="submit">Enregistrer</button>
    </form>

    <form method="post" action="?clear=1">
        <button type="submit">Supprimer le cookie</button>
    </form>
</body>
</html>

<?php
// Suppression : recréer le cookie expiré
if (isset($_GET['clear'])) {
    setcookie('theme', '', time() - 3600);
    header('Location: ' . strtok($_SERVER['REQUEST_URI'], '?'));
    exit;
}
?>
```

* **Fichier css clair.css**

```css
/* --- Thème clair : fond clair et texte foncé --- */
body {
    background-color: #ffffff;
    color: #222222;
    font-family: Arial, sans-serif;
}

.container {
    padding: 20px;
    border: 2px solid #ddd;
    border-radius: 8px;
    background-color: #f9f9f9;
}

.button {
    background-color: #eeeeee;
    color: #000;
    border: 1px solid #ccc;
    padding: 10px 15px;
    cursor: pointer;
}

.button:hover {
    background-color: #ddd;
}
```

* **Fichier css sombre.css**

```css
/* --- Thème sombre : fond sombre et texte clair --- */
body {
    background-color: #1c1c1c;
    color: #f5f5f5;
    font-family: Arial, sans-serif;
}

.container {
    padding: 20px;
    border: 2px solid #444;
    border-radius: 8px;
    background-color: #2c2c2c;
}

.button {
    background-color: #333333;
    color: #fff;
    border: 1px solid #555;
    padding: 10px 15px;
    cursor: pointer;
}

.button:hover {
    background-color: #555;
}
```

**Points clés** :

* `setcookie()` **envoie un en-tête** → fais-le **avant** tout affichage ou redirige juste après.
* Après un `setcookie()`, un **refresh** (redirection) permet de voir tout de suite la nouvelle valeur dans `$_COOKIE`.

---

## 4. 🛠️ TP php (Session/Cookie)

> But : enchaîner 3 mini-fonctionnalités très simples. Tu peux les faire dans des fichiers séparés.

### TP-G1 : Compteur de clics (session)

* Un bouton « +1 » incrémente `$_SESSION['clics']`.
* Un bouton « Reset » remet à 0.
* Affiche : « Clics : X ».

**Indices** : `session_start();`, `isset()`, opérateur `++`.

### TP-G2 : Bonjour avec prénom (session)

* Un formulaire `prenom` (input text). À l’envoi, tu stockes `$_SESSION['prenom']`.
* Tu affiches « Bonjour, \[prenom] ! ».
* Un bouton « Effacer le prénom » supprime la donnée.

**Indices** : `$_POST`, `htmlspecialchars()`, `unset($_SESSION['prenom']);`.

### TP-G3 : Préférence « langue » (cookie)

* Un select « fr / en / es ». À l’envoi, tu crées un cookie `langue` valable 24h.
* Tu affiches : « Langue actuelle : fr|en|es ».
* Un bouton « Supprimer » efface le cookie.

**Indices** : `setcookie('langue', $val, time()+86400);` ; redirection après setcookie.

* **Checklist réussite**

* [ ] La session démarre en haut de page.
* [ ] Le compteur s’incrémente correctement.
* [ ] Le prénom s’affiche et peut être effacé.
* [ ] La langue reste mémorisée après rechargement.

---

## 5. 🚀 TP autonome (facile, créatif)

### TP-A1 : Mini-site en 2 pages (session)

* **Page 1** : formulaire `prenom`.
* **Page 2** : affiche « Bonjour, \[prenom] ! » grâce à la session.
* Ajoute un bouton « Déconnexion » (détruit la session et revient à la page 1).

* **Attendus**

* Le prénom reste après refresh.
* Après déconnexion, la page 2 n’affiche plus le prénom.

### TP-A2 (option) : Préférence de **couleur** (cookie)

* Sur chaque page, le fond prend la couleur du cookie `couleur` (par défaut blanc).
* Une page « paramètres » permet de choisir et enregistrer la couleur.

---

## 6. 🔧 Exercices pratiques courts

> Fais-les rapidement pour manipuler les bases. Les corrections sont à me demander.

1. **Cookie jour** : crée un cookie `jour` avec la date du jour `Y-m-d` (valable 2h). Affiche « Dernière visite : \[jour] ».
2. **Secret en session** : stocke `$_SESSION['secret'] = 'abracadabra'` puis affiche-le seulement si un bouton « Voir le secret » a été cliqué.
3. **Compteur global + reset** : combine un compteur session et un bouton reset (sur la même page).
4. **Bonjour conditionnel** : si `$_COOKIE['prenom']` existe, affiche « Re-bonjour \[prenom] » sinon montre un petit formulaire pour le créer (cookie valable 30 min).
5. **Parité mémorisée** : formulaire nombre ; stocke la **dernière parité** (pair/impair) en session et affiche un message.

---

## 7. 🎮 Exercices « jeux » (préparatoires, plus simples que le morpion)

> Objectif : te préparer au Job « morpion » sans coder tout d’un coup. On reste **plus simple**.

### 7.1. Jeu 1 – **Puissance 3 (ligne unique)** *– proche du morpion mais en 1D*

* **But** : aligner 3 symboles identiques sur **une seule ligne de 3 cases**.
* **Interface** : 3 boutons « - » qui se remplissent tour à tour par `X` puis `O`.
* **Étapes** :

  1. Stocke la **grille** en session : `$_SESSION['g'] = ['-','-','-'];`
  2. Stocke le **tour** : `$_SESSION['tour'] = 'X'` au début.
  3. Quand tu cliques une case (index 0..2), si `'-'`, alors mets la lettre du joueur courant, puis **inverse** le tour.
  4. Vérifie la **victoire** : si `g[0]==g[1]==g[2]` et différent de `'-'`, afficher « X/O a gagné » et propose **Reset**.
  5. Si toutes les cases sont remplies sans gagnant → « Match nul » + Reset.

**Indice** : envoie l’index cliqué via `name="case" value="0|1|2"` dans un formulaire POST.

### 7.2. Jeu 2 – **Devine le nombre** (1 à 100)

* **But** : l’ordi choisit un nombre secret (session). Tu proposes un nombre ; il répond **plus / moins / trouvé**.
* **Étapes** :

  1. Si `$_SESSION['secret']` n’existe pas, fais `rand(1,100)` et stocke-le.
  2. Formulaire avec un input number (1..100).
  3. Compare et affiche le message ; compte le **nombre d’essais** dans `$_SESSION['tries']`.
  4. Bouton « Rejouer » → réinitialise `secret` et `tries`.

**Bonus** : garde **le meilleur score** (le score avec le moins d’essais) en **cookie** `meilleur_score`.

### 7.3. (Option) **Pile ou Face**

* Un bouton « Lancer » → `rand(0,1)` ; affiche « Pile » ou « Face ».
* Compte les victoires de l’utilisateur (devine avant ?), stocke le score en session.

* **Conseils communs (jeux)**

* Toujours `session_start()` en haut.
* Pense aux **redirections** après POST (pattern **PRG**: Post → Redirect → Get) pour éviter les doubles clics.
* Sépare l’**état** (session/cookies) de l’**affichage** (HTML) pour t’y retrouver.

---

## 8. ✅ Bonnes pratiques

* `session_start()` **tout en haut** ; pas d’echo avant.
* Après `setcookie()` → souvent **redirection** immédiate.
* Évite de stocker des infos sensibles dans un cookie ; si tu dois le faire, **chiffre** côté serveur puis vérifie.
* Utilise `htmlspecialchars()` pour afficher des données saisies par l’utilisateur.
* Pense à **nettoyer**/réinitialiser les sessions lors de la déconnexion.

---

## 9. 📚 Ressources fiables pour aller plus loin

* PHP manuel – Sessions : [https://www.php.net/manual/fr/book.session.php](https://www.php.net/manual/fr/book.session.php)
* PHP manuel – Cookies : [https://www.php.net/manual/fr/function.setcookie.php](https://www.php.net/manual/fr/function.setcookie.php)
* Pierre Giraud – Sessions : [https://www.pierre-giraud.com/php-mysql-apprendre-coder-cours/session-definition-utilisation/](https://www.pierre-giraud.com/php-mysql-apprendre-coder-cours/session-definition-utilisation/)
* Pierre Giraud – Cookies : [https://www.pierre-giraud.com/php-mysql-apprendre-coder-cours/cookie-creation-gestion/](https://www.pierre-giraud.com/php-mysql-apprendre-coder-cours/cookie-creation-gestion/)
* Pattern PRG (Post/Redirect/Get) : mots-clés pour chercher et améliorer tes formulaires.

---
![footer](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=120&section=footer&text=%F0%9F%8C%9F%20Mettez%20une%20%2A%20si%20vous%20avez%20aim%C3%A9%20ce%20TP%20!%20%F0%9F%9A%80&fontSize=22)
