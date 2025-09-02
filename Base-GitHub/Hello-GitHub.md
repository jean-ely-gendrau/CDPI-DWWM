# 🛠️ Base GitHub : Découverte, création de compte et dépôt

![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=200&section=header&text=Hello%20GitHub&fontSize=40&fontAlignY=35&desc=Les%20bases&descAlignY=55&descAlign=50)

## 🎯 Objectifs

* Crée ton compte GitHub et configure-le rapidement.
* Crée ton premier dépôt avec `README.md`.
* Mets en ligne un mini‑projet **HTML** dans un dépôt dédié (TP2).

---

## 1) 🚀 TP 1

### Étape A — Crée ton compte GitHub

1. Va sur [https://github.com](https://github.com).
2. Clique sur **Sign up**.
3. Renseigne ton **email**, un **mot de passe fort**, et choisis un **nom d’utilisateur** pro (ex. `prenom-nom`).
4. Choisis le plan **Free**.
5. Confirme l’email reçu.

> Résultat : ton compte GitHub est actif.

---

### Étape B — Crée ton premier dépôt

1. Clique sur **+ New repository**.
2. Nom du dépôt : `premier-test`.
3. **Public**, coche **Add a README file**.
4. Clique **Create repository**.

> Résultat attendu : la page du dépôt affiche `README.md` avec le titre `# premier-test`.

---

### Étape C — Édite le README

1. Ouvre `README.md` → **Edit**.
2. Remplace le contenu par :

   ```markdown
   # premier-test
   Dépôt d'essai pour découvrir GitHub.
   Auteur : Prénom NOM
   ```

3. Clique **Commit changes** (message de commit : `MAJ du README`).

> Résultat : tu vois ton commit dans l’onglet **Commits**.

---

### (Option) Étape D — Découvrir l’envoi de fichiers

> **Méthode Web (sans outil)**

1. Dans le dépôt, clique **Add file → Upload files**.
2. Dépose un fichier `notes.txt` avec du texte.
3. Message de commit : `Ajout notes.txt` → **Commit changes**.

> **Méthode Git (ligne de commande)**

```bash
# Initialiser un dépôt local
mkdir demo-git && cd demo-git        # Crée et entre dans le dossier du projet
git init                             # Initialise Git dans ce dossier

echo "Hello Git" > notes.txt        # Crée un fichier de test

git add notes.txt                    # Étape 1 : prépare le fichier pour le commit 

git commit -m "feat: ajout notes.txt"
# Étape 2 : enregistre un point de version avec un message clair et normé

# Associer le dépôt local au dépôt GitHub (remplace {TON-USER})
git remote add origin https://github.com/{TON-USER}/premier-test.git

# Envoyer l'historique local vers GitHub (branche principale)
git branch -M main                   # S'assure que la branche s'appelle main
git push -u origin main              # Pousse la branche main et définit le suivi
```

---

## 2) 🎨 TP 2 (Mini‑projet HTML)

> Utilise **un de tes mini‑projets HTML créés précédemment** (ex. ta **page profil** ou ton exercice **HTML++**). Tu vas l’héberger dans un dépôt dédié et l’exposer avec **GitHub Pages** **Plesk**.

### Étape A — Prépare ton projet

* Place les fichiers de ton mini‑projet dans un dossier local (ex. `profil-html`).
* Fichiers minimum recommandés : `index.html`, dossier `assets/` (images, CSS), éventuellement `style.css`.

**Exemple `index.html` minimal**

```html
<!doctype html>
<html lang="fr">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Mon profil</title>
    <!-- Bonne pratique: titre clair + meta viewport pour mobile -->
    <link rel="stylesheet" href="style.css" /> <!-- Séparer la présentation du contenu -->
  </head>
  <body>
    <header>
      <h1>Profil – Prénom Nom</h1> <!-- Titre principal sémantique -->
      <nav>
        <a href="#apropos">À propos</a>
        <a href="#contact">Contact</a>
      </nav>
    </header>

    <main>
      <section id="apropos">
        <h2>À propos</h2>
        <p>Développeur(se) web en formation DWWM.</p>
      </section>
      <section id="projets">
        <h2>Projets</h2>
        <ul>
          <li>Mini‑projet HTML++</li>
          <li>Page profil</li>
        </ul>
      </section>
    </main>

    <footer>
      <small>© 2025 – Mon Portfolio</small> <!-- Mentions légales simples -->
    </footer>
  </body>
</html>
```

**Exemple `style.css` minimal — commenté**

```css
/* Reset simple pour une base propre */
* { box-sizing: border-box; margin: 0; padding: 0; }

/* Lisibilité globale */
body { font-family: system-ui, sans-serif; line-height: 1.5; padding: 16px; }

header, main, footer { max-width: 900px; margin: 0 auto; }

header h1 { margin-bottom: 8px; }
nav a { margin-right: 12px; text-decoration: none; }

h2 { margin: 16px 0 8px; }

ul { list-style: disc; margin-left: 24px; }
```

---

### Étape B — Crée le dépôt GitHub

1. Sur GitHub → **+ New repository**.
2. Nom : `mini-projet-html` (ou un nom lié à ton sujet).
3. **Public**, coche **Add a README file** → **Create repository**.

---

### Étape C — Envoie tes fichiers

> **Méthode Web**

* **Add file → Upload files** → glisse `index.html`, `style.css`, `assets/…`.
* Message de commit : `feat: ajout mini‑projet HTML` → **Commit changes**.

> **Méthode Git (CLI)**

```bash
# Depuis le dossier de ton mini‑projet
cd chemin/vers/profil-html          # 1) se placer dans le bon dossier

git init                            # 2) initialiser Git si nécessaire

git add .                           # 3) mettre en suivi tous les fichiers

git commit -m "feat: première version du mini‑projet"
# 4) créer un point de version clair avec un message normé

# 5) lier au dépôt distant (remplace {TON-USER} et {TON-DEPOT})
git remote add origin https://github.com/{TON-USER}/{TON-DEPOT}.git

git branch -M main                  # 6) standardiser le nom de branche

git push -u origin main             # 7) publier sur GitHub
```

---

### (GitHub io) Étape D — Publie avec GitHub Pages

1. Dans ton dépôt → **Settings → Pages**.
2. **Source** : choisis **Deploy from a branch**.
3. **Branch** : `main` / dossier `/root` → **Save**.
4. Après le déploiement, une **URL publique** s’affiche (ex. `https://ton-user.github.io/ton-depot/`).

> Vérification : ouvre l’URL → ta page `index.html` doit s’afficher correctement.

---

## 3) ✅ Vérification

### Check‑list TP1

* [ ] Compte GitHub créé et email confirmé.
* [ ] Dépôt `premier-test` avec `README.md` mis à jour.
* [ ] Au moins un fichier ajouté (web ou Git).

### Check‑list TP2

* [ ] Dépôt `mini-projet-html` créé.
* [ ] Fichiers du mini‑projet envoyés (web ou Git).
* [ ] Page accessible en local ET/OU via **GitHub Pages** (si bonus fait).
* [ ] README avec : titre, description, auteur.

### Critères d’évaluation simples

* **Organisation** (noms de dépôts clairs, README présent).
* **Qualité** (fichiers HTML/CSS propres, commentaires présents).
* **Process** (commits avec messages explicites).
* **Autonomie** (capacité à publier via Pages en bonus).

---

## 4) 🧭 Aides & rappels

* *Repository* = dossier de projet versionné.
* *Commit* = sauvegarde avec message clair (ex. `feat: ajout section A propos`).
* *Push* = envoi vers GitHub. *Pull* = récupérer depuis GitHub.
* Messages de commit recommandés : `feat`, `fix`, `docs`, `style`, `refactor`, `chore`.

---

## 5) 📚 Ressources utiles

* Docs GitHub : [https://docs.github.com](https://docs.github.com)
* OpenClassrooms – Git & GitHub : [https://openclassrooms.com/fr/courses/5641726-gerez-votre-code-avec-git-et-github](https://openclassrooms.com/fr/courses/5641726-gerez-votre-code-avec-git-et-github)
* W3Schools – Git Tutorial : [https://www.w3schools.com/git/](https://www.w3schools.com/git/)
* MDN – Outils & GitHub : [https://developer.mozilla.org/fr/docs/Learn/Tools\_and\_testing/GitHub](https://developer.mozilla.org/fr/docs/Learn/Tools_and_testing/GitHub)

---

✍️ **À retenir** : Héberge ton **mini‑projet HTML** sur GitHub pour apprendre le vrai flux de travail : *créer → versionner → publier*.

![footer](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=120&section=footer&text=%F0%9F%8C%9F%20Mettez%20une%20%2A%20si%20vous%20avez%20aim%C3%A9%20ce%20TP%20!%20%F0%9F%9A%80&fontSize=22)