# Support — HTML - CSS

![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=200&section=header&text=HTML/CSS%20DWWM&fontSize=40&fontAlignY=35&desc=Apprendre%20les%20bases%20du%20HTML/CSS&descAlignY=55&descAlign=50)

## 1. 🎓 Introduction

### Objectif global 

L'objectif de ce module est d'apprendre à utiliser CSS pour mettre en
forme des pages HTML. Vous allez découvrir comment appliquer des
couleurs, des polices et des bordures, organiser les éléments d'une
page, et séparer le contenu (HTML) de la présentation (CSS).

### Compétences visées (Référentiel DWWM)

- Créer une interface utilisateur statique et ergonomique.
- Respecter les standards du web (W3C).
- Mettre en œuvre de bonnes pratiques de structuration et de lisibilité
du code.

### Contexte métier

Dans un vrai projet (site vitrine, blog, e-commerce, intranet
d'entreprise) :

- Le CSS est utilisé pour appliquer la charte graphique définie par un
client ou un designer.
- Il permet de travailler l'ergonomie et l'accessibilité.
- En formation DWWM, vous allez d'abord coder manuellement vos CSS, puis
apprendre à intégrer des frameworks (Bootstrap, Tailwind).

## 2. 📖 Cours théorique

### Qu'est-ce que le CSS ?

CSS signifie Cascading Style Sheets (Feuilles de style en cascade). Il
décrit l'apparence d'une page HTML.

Analogie :

- HTML = la maison (murs, fenêtres).
- CSS = la peinture, la déco, l'ameublement.

### Syntaxe d'une règle CSS

sélecteur { propriété: valeur; }

Exemple :
p { color: blue; font-size: 16px; }

### Sélecteurs principaux

- p → tous les paragraphes.
- .maClasse → tous les éléments ayant cette classe.
- #monId → un élément unique.

### ⚠️ ID vs Classe

Beaucoup de tutoriels débutants utilisent encore les IDs.

Exemple avec ID :

```html
<button id="btn-demo">Clique-moi</button>
```

```css
#btn-demo { background-color: darkblue; color: white; }
```

Exemple avec Classe :

```html
<button class="btn-demo">Clique-moi</button>
<button class="btn-demo">Moi aussi</button>
```

```css
.btn-demo { background-color: darkblue; color: white; }
```

## 3. 💻 Démonstration

Exemple d'une page HTML avec son CSS.

> HTML (index.html)

```html

<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>Demo CSS - La Plateforme_</title>
<link rel="stylesheet" href="style.css">
</head>
<body>
<h1>Bienvenue en formation DWWM</h1>
<p class="intro">Ceci est un exemple de paragraphe stylisé.</p>
<button class="btn-demo">Clique-moi</button>
<button class="btn-demo">Moi aussi</button>
</body>
</html>

```

> CSS (style.css)

```css

body {
font-family: Arial, sans-serif;
background-color: #f0f0f0;
margin: 20px;
}
h1 {
color: darkred;
text-align: center;
}
.intro {
color: #333;
background-color: white;
padding: 10px;
border: 1px solid #ccc;
border-radius: 5px;
}
.btn-demo {
background-color: darkblue;
color: white;
padding: 10px 20px;
border: none;
border-radius: 5px;
cursor: pointer;
}
.btn-demo:hover {
background-color: #004080;
}

```

## 4. 🛠️ TP HTML/CSS

Créer une page avec :

- Un titre centré en bleu,
- Deux paragraphes encadrés,
- Une image de 300px avec bordure noire,
- Deux boutons stylisés (utiliser une classe).

### Wireframe (schéma attendu TP 4.)

[ Titre centré en bleu ]

[ Paragraphe encadré ]
[ Paragraphe encadré ]

[ Image 300px ]

[ Bouton 1 ] [ Bouton 2 ]

## 5. 🚀 TP HTML/CSS

Créer une mini page personnelle :

- Ton prénom en h1,
- Une photo ou image,
- Un paragraphe 'À propos',
- Trois boutons (Me contacter, Mon CV, Mon GitHub).

### Wireframe (schéma attendu TP 5.)

[ Prénom (h1) ]

[ Photo/Image ]

[ Paragraphe À propos ]

[ Bouton 1 ] [ Bouton 2 ] [ Bouton 3 ]

## 7. 📚 Ressources complémentaires

- [MDN CSS](https://developer.mozilla.org/fr/docs/Web/CSS)
- [W3Schools CSS](https://www.w3schools.com/css/)
- [OpenClassrooms -- HTML/CSS](https://openclassrooms.com/fr/courses/1604541)
- [CSS Tricks](https://css-tricks.com/)

![footer](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=120&section=footer&text=%F0%9F%8C%9F%20Mettez%20une%20%2A%20si%20vous%20avez%20aim%C3%A9%20ce%20TP%20!%20%F0%9F%9A%80&fontSize=22)