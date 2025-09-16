# 📘 Support – PHP : Les conditions 

![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=200&section=header&text=Les%20Conditions-PHP&fontSize=40&fontAlignY=35&desc=If-elseif-else%20switch%20match&descAlignY=55&descAlign=50)

## 1. 🎓 Introduction  

### 🎯 Objectif

Aujourd’hui, tu vas apprendre à utiliser les **conditions en PHP** (`if`, `else`, `elseif`, `switch`, `match`) ainsi que l’instruction **echo** pour afficher des résultats dans une page web.  

### 🛠️ Compétences visées (Référentiel DWWM)

- Écrire du **code PHP clair et structuré**.  
- Mettre en place des **conditions logiques** pour gérer des choix.  
- Utiliser **echo** pour afficher du texte ou des résultats dynamiques.  
- Comprendre et choisir entre `if/else`, `switch` et `match`.  

### 🌍 Contexte métier

Imagine que tu développes un site pour des services de **Toulon** :

- Vérifier si un supporter est **inscrit au club de rugby du RCT**.  
- Afficher un message différent selon le jour pour un commerce de **Mayol**.  
- Gérer les horaires des bus ou bateaux du réseau **Mistral**.  

👉 Les conditions te permettent d’adapter ton site à chaque utilisateur.  

---

## 2.🔹 Qu’est-ce qu’une condition ?  

Une **condition** permet à ton programme de **prendre une décision** :

Exemple concret à Toulon :  

- **Si** le bus du réseau Mistral est en retard → **alors** tu attends.  
- **Sinon** → tu prends un bateau-bus.  

En PHP :  

```php
if (condition) {
    // instructions si la condition est vraie
} else {
    // instructions si la condition est fausse
}
```

---

### 🔹 L’instruction `echo`  

- `echo` te permet d’**afficher du texte ou des résultats**.  

Exemple :

```php
echo "Bonjour Toulon !";
echo 2 + 3; // Affiche 5
```

---

### 🔹 Exemple combiné

```php
$age = 20;

if ($age >= 18) {
    echo "Tu es majeur, bienvenue à Toulon.";
} else {
    echo "Tu es mineur, certaines activités sont limitées.";
}
```

---

### 🔹 Bonnes pratiques DWWM

- **Indente** ton code correctement.  
- Ajoute des **commentaires pertinents**.  
- Utilise des **noms de variables clairs** : `$age`, `$prenom`, `$ville`.  

---

## 🔹 Les conditions avancées : `switch` et `match`  

### `switch`

La structure **switch** est utile quand tu veux comparer **une seule variable à plusieurs valeurs possibles**.  

👉 Exemple avec le centre commercial **Mayol** :

```php
$jour = "Samedi";

switch ($jour) {
    case "Lundi":
        echo "Ouvert de 10h à 19h";
        break;

    case "Samedi":
        echo "Ouvert jusqu’à 20h pour ton shopping à Mayol !";
        break;

    case "Dimanche":
        echo "Fermé, profite d’un match du RCT au Stade Mayol !";
        break;

    default:
        echo "Jour non reconnu.";
}
```

---

### `match` (PHP 8 et +)

La structure **match** est une version plus moderne et compacte du `switch`.  

👉 Exemple avec les **bateaux-bus du réseau Mistral** :

```php
$destination = "La Seyne";

$message = match ($destination) {
    "Les Sablettes" => "Départ toutes les 30 minutes.",
    "La Seyne" => "Départ toutes les 20 minutes depuis Toulon.",
    "St Mandrier" => "Dernier départ à 22h.",
    default => "Destination inconnue.",
};

echo $message;
```

---

✅ **Quand utiliser quoi ?**

- `if / else` → conditions simples ou calculs logiques.  
- `switch` → plusieurs valeurs possibles pour une même variable.  
- `match` → syntaxe moderne, plus lisible et expressive (PHP 8+).  

---

## 3. 💻 Démonstration pratique  

👉 Exemple : Vérifie le **score d’un match du RCT**.  

```php
<?php
$scoreRCT = 25;
$scoreAdversaire = 18;

if ($scoreRCT > $scoreAdversaire) {
    echo "Victoire du RCT à Toulon !";
} else {
    echo "Défaite... entraînement intensif demain.";
}
?>
```

👉 Exemple : Affiche les **horaires du centre Mayol** avec switch.

```php
$jour = "Dimanche";

switch ($jour) {
    case "Samedi":
        echo "Mayol est ouvert jusqu’à 20h.";
        break;
    case "Dimanche":
        echo "Mayol est fermé, mais il y a peut-être un match au Stade Mayol.";
        break;
    default:
        echo "Horaires classiques : 10h - 19h.";
}
```

---

## 4. 🛠️ TP PHP (les conditions)  

### Consigne  

Écris un script PHP qui affiche un message en fonction du **mode de transport choisi à Toulon** (bus ou bateau du réseau Mistral).  

### Étapes  

1. Crée une variable `$transport` avec la valeur `"Bus"` ou `"Bateau"`.  
2. Utilise un `switch` pour tester la valeur.  
3. Affiche :  
   - “Tu prends le bus, pense à ton ticket !”  
   - “Tu prends le bateau, profite de la vue sur la rade de Toulon !”  

### Vérification  

👉 Si ton code affiche un message différent selon `$transport`, tu as réussi.  

---

## 5. 🚀 TP PHP (match)  

### Consigne  TP PHP (match)

Crée un script qui affiche un message personnalisé selon le **résultat d’un match du RCT** avec `match`.  

- Si RCT gagne → “Victoire à Mayol !”  
- Si égalité → “Match nul, à travailler…”  
- Si défaite → “Défaite, mais Toulon reste fort !”  

👉 Objectif : pratiquer `match` avec des conditions simples.  

---

## 6. 🔧 Exercices pratiques courts  

> 👉 **Consigne** : réalise les exercices ci-dessous dans des fichiers séparés (un fichier par exercice). **Pas de correction ici** : tu pourras te corriger via la branche dédiée du dépôt GitHub Classroom.

1. **Température Toulon**  
   Déclare `$temperature = 30;`. Affiche "Il fait chaud à Toulon" si la température est ≥ 28, sinon "Température agréable".

2. **Quai bateau-bus Mistral (switch)**  
   Avec `$destination` parmi `"Les Sablettes"`, `"La Seyne"`, `"St Mandrier"`, affiche le **quai** correspondant (1, 2, 3). Utilise `switch`.

3. **Commentaire de note (match)**  
   Avec `$note` (0–20), affiche :  
   - ≥ 16 → "Excellent travail à Toulon !"  
   - ≥ 10 → "Assez bien, continue !"  
   - sinon → "À améliorer !"  
   Utilise `match`.

4. **Jours d’ouverture Mayol (switch)**  
   Lundi–Vendredi → "Ouvert 10h - 19h" ; Samedi → "Ouvert 10h - 20h" ; Dimanche → "Fermé".

5. **Mode de transport (switch)**  
   `$transport` ∈ {`"Bus"`, `"Bateau"`} → message différent pour bus/bateau du réseau Mistral. Cas par défaut si autre valeur.

6. **Résultat RCT (match)**  
   `$resultat` ∈ {`"Victoire"`, `"Défaite"`, `"Nul"`} → message adapté.

7. **Quai + heure (switch + echo)**  
   Selon `$destination` (3 cases), affiche aussi un horaire indicatif (ex. "Départ toutes les 20 min").

8. **Réduction à Mayol (match)**  
   `$carte` ∈ {`"Étudiant"`, `"Senior"`} → 10% / 15% ; défaut 0%.

9. **Météo Toulon (switch)**  
   `$meteo` ∈ {`"Soleil"`, `"Pluie"`, `"Vent"`} → message adapté (plage du Mourillon, coder au centre, attention au Mistral).

10. **Billet RCT (match)**  
    `$categorie` ∈ {`"Enfant"`, `"Adulte"`, `"VIP"`} → prix 10 / 20 / 50 ; affiche "Prix du billet : X €".

11. **Jours de formation DWWM (switch)**  
    Lundi–Vendredi → "Cours DWWM" ; Samedi/Dimanche → "Repos".

12. **Itinéraire rapide (switch)**  
    `$ligne` ∈ {`"Bus 23"`, `"Bus 40"`, `"Bateau"`} → affiche la **destination** (Cap Brun, Mourillon, La Seyne).

---

## 7. 📚 Ressources complémentaires  

- [PHP – Structures conditionnelles](https://www.php.net/manual/fr/control-structures.if.php)  
- [Documentation PHP officielle](https://www.php.net/manual/fr/)  

---
![footer](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=120&section=footer&text=%F0%9F%8C%9F%20Mettez%20une%20%2A%20si%20vous%20avez%20aim%C3%A9%20ce%20TP%20!%20%F0%9F%9A%80&fontSize=22)