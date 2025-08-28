# Support — HTML

![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=200&section=header&text=HTML%20DWWM&fontSize=40&fontAlignY=35&desc=Apprendre%20les%20bases%20du%20HTML&descAlignY=55&descAlign=50)

## 1. Introduction

### Objectif global

Comprendre ce qu’est **HTML**, savoir structurer une page web avec des **balises sémantiques**, et produire un code **clair, accessible et maintenable**.

### Compétences visées

- Poser la structure HTML d’une page (head + body).
- Utiliser les balises de contenu (titres, paragraphes, listes, médias, liens, tableaux, formulaires simples).
- Employer les balises sémantiques HTML5 (header, nav, main, section, article, aside, footer).
- Respecter les bonnes pratiques professionnelles : indentation, attributs obligatoires, textes alternatifs, hiérarchie de titres, validation W3C.

### Contexte métier / À quoi ça sert

Dans un projet réel, HTML est la **colonne vertébrale**. Sans structure claire, **CSS** et **JavaScript** deviennent fragiles.  
Un HTML propre :  

- Améliore le référencement (**SEO**) et l’accessibilité (**a11y**).  
- Réduit le coût de maintenance.  
- Facilite le travail d’équipe (développeurs, SEO, PO, designers).  

Dans les premières années du web, certaines balises visuelles comme `<blink>` et `<marquee>` étaient utilisées pour attirer l’œil. Elles rendaient la lecture fatigante et ont été abandonnées au profit d’une structure sémantique claire.

---

## 2. Cours théorique

### 2.1. Qu’est-ce que HTML ?

**HyperText Markup Language** est un **langage de balisage** : il décrit la **structure** et le **sens du contenu**, mais ce n’est pas un langage de programmation.

*Analogie maison* :  

- **HTML** = murs et pièces (structure)  
- **CSS** = décoration (style)  
- **JavaScript** = électricité et automatisation (interaction)

### 2.2. Structure minimale d’une page HTML

```html
<!DOCTYPE html> <!-- Déclare le standard HTML5 et évite le quirks mode -->
<html lang="fr"> <!-- Définit la langue du document : utile pour l’accessibilité et le SEO -->
  <head> <!-- Métadonnées : non affichées directement -->
    <meta charset="UTF-8"> <!-- Encodage universel -->
    <meta name="viewport" content="width=device-width, initial-scale=1"> <!-- Responsive -->
    <meta name="description" content="Cours HTML DWWM : structure, sémantique et bonnes pratiques"> <!-- Résumé SEO -->
    <title>Introduction à HTML — DWWM</title>
  </head>
  <body>
    <h1>Bienvenue dans le HTML</h1>
    <p>Ceci est mon premier paragraphe en HTML.</p>
  </body>
</html>
```

Le doctype moderne est court. Les anciens doctypes, plus verbeux, pouvaient provoquer des comportements imprévus s’ils étaient mal saisis.

### 2.3. Balises indispensables

- **Titres** : `<h1>` à `<h6>` pour une hiérarchie logique.  
- **Texte** : `<p>`, `<strong>` (importance), `<em>` (emphase).  
- **Liens** : `<a href="..." target="_blank" rel="noopener">` (sécurité en nouvel onglet).  
- **Images** : `<img src="..." alt="...">` avec `alt` descriptif (ou vide si décorative).  
- **Listes** : `<ul>`, `<ol>`, `<li>`.  
- **Citations** : `<blockquote>`, `<q>`, `<cite>`.  
- **Médias** : `<figure>` + `<figcaption>`.  
- **Données temporelles** : `<time datetime="YYYY-MM-DD">...</time>`.  
- **Formulaires** : `<form>`, `<label for>`, `<input>`, `<textarea>`, `<button>` (associer label et champ).  

Attention : `<b>` met en gras visuellement, `<strong>` indique une importance sémantique.

### 2.4. Structure sémantique type (moderne)

```html
<header>
  <div class="brand">
    <a href="/" title="Retour à l’accueil">MonSite</a>
  </div>
  <nav aria-label="Navigation principale">
    <ul>
      <li><a href="#actus">Actualités</a></li>
      <li><a href="#services">Services</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>
</header>

<main id="contenu">
  <section id="actus" aria-labelledby="titre-actus">
    <h2 id="titre-actus">Dernières actualités</h2>
    <article>
      <header>
        <h3>Nouveau service de support</h3>
        <p><time datetime="2025-08-25">25 août 2025</time></p>
      </header>
      <p>Nous lançons un support étendu pour nos clients.</p>
      <footer>
        <a href="#">Lire plus</a>
      </footer>
    </article>
  </section>

  <aside aria-label="Informations complémentaires">
    <h2>À ne pas manquer</h2>
    <p>Inscris-toi à la newsletter.</p>
  </aside>
</main>

<footer>
  <p>&copy; 2025 — MonSite. <a href="/mentions-legales">Mentions légales</a></p>
</footer>
```

### 2.5. Avant vs maintenant et erreurs à éviter

Ancienne approche à éviter :

```html
<center>Bienvenue</center>
<font color="red" size="7">Titre</font>
<table width="100%" border="0">
  <tr>
    <td>Menu</td>
    <td>Contenu</td>
  </tr>
</table>
<br><br><br>
```

Approche moderne :

```html
<header>
  <h1>Bienvenue</h1>
</header>
<main>
  <nav>
    <ul>
      <li><a href="#">Accueil</a></li>
      <li><a href="#">Services</a></li>
    </ul>
  </nav>
  <section>
    <h2>Contenu</h2>
    <p>Texte de présentation…</p>
  </section>
</main>
```

---

## 3. Démonstration pratique

Objectif : reproduire une mini page vitrine simple en HTML.

```html
<!DOCTYPE html>
<html lang="fr">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Mini vitrine — Pâtisserie Douceur</title>
    <meta name="description" content="Pâtisserie Douceur : gâteaux artisanaux, horaires et contact.">
  </head>
  <body>
    <header>
      <h1>Pâtisserie Douceur</h1>
      <nav aria-label="Navigation principale">
        <ul>
          <li><a href="#produits">Produits</a></li>
          <li><a href="#horaires">Horaires</a></li>
          <li><a href="#contact">Contact</a></li>
        </ul>
      </nav>
    </header>

    <main id="contenu">
      <section id="produits" aria-labelledby="titre-produits">
        <h2 id="titre-produits">Nos spécialités</h2>
        <figure>
          <img src="https://via.placeholder.com/600x300" alt="Assortiment de pâtisseries maison">
          <figcaption>Assortiment de gâteaux du jour.</figcaption>
        </figure>
      </section>
    </main>

    <footer>
      <p>&copy; 2025 Pâtisserie Douceur • <a href="#">Mentions légales</a></p>
    </footer>
  </body>
</html>
```

---

## 4. TP HTML

### Consignes

1. Crée un fichier `index.html`.  
2. Ajoute le squelette HTML5.  
3. Organise le `body` avec `header`, `main`, `footer`.  
4. Utilise au moins une image avec `alt`, une liste et un lien externe.

### Gabarit à compléter

```html
<!DOCTYPE html>
<html lang="fr">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Mon profil — Prénom Nom</title>
  </head>
  <body>
    <header>
      <h1>Prénom Nom</h1>
      <nav>
        <ul>
          <li><a href="#presentation">Présentation</a></li>
          <li><a href="#projets">Projets</a></li>
          <li><a href="#contact">Contact</a></li>
        </ul>
      </nav>
    </header>
  </body>
</html>
```

---

## 5. TP HTML LIBRE

Sujet : créer une fiche produit 100 % HTML.  
Attendus : structure sémantique, figure + figcaption, tableau simple, deux liens internes.

---

### Critères de réussite

- Checklist du TP guidé validée.  
- TP autonome respecté.  
- Code validé W3C.  

---

## 7. Ressources complémentaires

- [MDN](https://developer.mozilla.org/fr/docs/Web/HTML)  
- [Validateur W3C](https://validator.w3.org/)  
- [OpenClassrooms](https://openclassrooms.com/fr/courses/1946386)  
- [W3Schools](https://www.w3schools.com/html/)  

---

## Mémo rapide

- `<!DOCTYPE html>` • `<html lang="fr">` • `<meta charset="UTF-8">` • `<meta name="viewport"...>`  
- Un seul `<h1>` conseillé.  
- `alt` descriptif sur toutes les images (ou vide si décoratives).  
- Préférer `header`, `nav`, `main`, `section`, `article`, `aside`, `footer` aux `<div>`.  
- Ne pas utiliser `<font>`, `<center>`, `<marquee>`, `<blink>` ; éviter les `<br>` répétés.  

![footer](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=120&section=footer&text=%F0%9F%8C%9F%20Mettez%20une%20%2A%20si%20vous%20avez%20aim%C3%A9%20ce%20TP%20!%20%F0%9F%9A%80&fontSize=22)
