Conventions d'intégration CSS/HTML
==================================

Ce document doit permettre d'uniformiser le code HTML/CSS du pôle intégration à l'aide de différentes conventions.  
Le but recherché est de disposer d'un code maintenable facilement sur l'ensembles des projet gérés par le pôle
et que n'importe quel projet soit accessible à n'importe quel intervenant connaissant nos conventions.

**/!\ Il est impératif d'appliquer les conventions suivantes de manière stricte.**  
_Tout code ne respectant pas ces conventions sera refusé à la revue de code._

## Table des matières

1. [Principes généraux](#general-principles)
2. [Indentation](#whitespace)
3. [Commentaires](#comments)
4. [Format](#format)
5. [Nommage](#naming)
6. [Internationalisation/traductions](#i18n)
7. [Organisation](#organization)
8. [microformats](#microformats)
9. [javascript](#javascript)
10. [Outils utiles](#tools)
11. [Sources et inspiration](#sources)

<a name="general-principles"></a>
## 1. Principes généraux

### Principes
* Tout code présent dans n'importe quelle base de code doit avoir l'air d'avoir été écrit par une seule personne, peu importe le nombre de gens qui y a contribué ;
* Appliquez les conventions de style de manière stricte ;
* En cas de doute tournez-vous vers vos collègues ou vers l'intégrateur référent.

### Règles de base
* Encodage UTF-8 (no BOM) ;
* Aucun style en dur dans le HTML ;
* L'unité de font à utiliser est le pixel, l'em est réservé à la zone de contenu principal (contenu d'un article sur une page article par exemple) ;
* Éviter au maximum d'utiliser les IDs pour styler les éléments ;
* Éviter de cacher du texte avec par exemple : `font-size: 0;` ou `text-indent: -150%;` ;
* Encoder les icons en base64 avec par exemple `inline-image()` en SCSS avec compass ;
* Ne pas préciser d'unité pour la valeur 0 ;
* Utiliser les formes raccourcies, exemple : `padding: 10px 5px;` ;
* Ne pas préciser le 0 pour les valeurs comprises entre -1 et 1 : `font-size: .8em;`, `color: rgba(#fff, .4);` ;
* Noter le code héxadécimal toujours en minuscule avec 3 lettres si possible ;
* Utiliser toujours le même type de guillemets, à savoir les doubles guillemets, exemple : `content: "";` ;
* Utiliser toujours des guillemets pour les valeurs dans les sélecteurs, exemple : `input[type="checkbox"]` ;
* Pas de hacks.

### Règles de base HTML
* Encodage UTF-8 (no BOM) ;
* Aucun style en dur dans le HTML ;
* Des documents HTML en HTML5 ;
* Les balises autofermantes sans le slash de fermeture, ex : `<br>`, `<img alt="" width="" height="" src="">`, `<meta>` ;
* Plus d'attribut 'type', ex : `<javascript src="//javascript.fr/script.js"></script>` ;
* Utilisez des images en base64 pour les icons ;
* Aucun élément HTML ne doit être fermé dans un fichier différent de celui où il a été ouvert ;

```html
<!-- header.html -->
<head>
   <title>A ne pas faire</title>
</head>
<body>
```

```html
<!-- footer.html -->
<p>Copyright 2018</p>
</body>
</html>
```

* Utiliser `<thead>`, `<tfoot>`, `<tbody>`, et `<th>` de manière appropriée (n'oubliez pas l'attribut Scope).  
**/!\** `<tfoot>` ce place avant `<tbody>`.

```html
<table summary="Tableau des factures 2011.">
  <thead>
    <tr>
      <th scope="col">Entête 1</th>
      <th scope="col">Entête 2</th>
    </tr>
  </thead>
  <tfoot>
    <tr>
      <td>Pied 1</td>
      <td>Pied 2</td>
    </tr>
  </tfoot>
  <tbody>
    <tr>
      <td>Donnée 1</td>
      <td>Donnée 2</td>
    </tr>
  </tbody>
</table>
```

**/!\** Un soin tout particulier doit-être apporté à la sémantique de votre code à l'aide des balises HTML5.

<a name="whitespace"></a>
## 2. Indentation

Pour les différents projets du pôle, nous utilisons les **tabulations** pour gérer l'indentation.  
Une seule manière d‘indenter doit être utilisée sur l'ensemble du code source des projets.  
Soyez toujours constant dans votre façon d‘indenter.  

**/!\** Ne mélangez jamais les espaces et les tabulations pour l'indentation.  
_**Astuce :** Configurez votre éditeur afin qu'il affiche les "caractères invisibles". Cela vous permettra de supprimer les espaces en fin de ligne, les espaces dans les lignes vides et évitera de polluer vos commits._

<a name="comments"></a>
## 3. Commentaires

Prenez le temps de décrire les composants, comment ils fonctionnent et la manière dont ils sont conçus.  
Ne laissez pas les autres membres de l'équipe deviner le but d'un code, documentez-le si il est peu explicite.

* Délimitez le code en grandes parties identifiables ;
* Placer les commentaires sur une nouvelle ligne au-dessus de leur sujet ;
* Eviter les commentaires en fin de ligne ;
* Garder une longueur de ligne de taille raisonnable, **80 caractères** ;
* Pas de z-index délirants, valeur maximum 99 ;
* Rédiger vos commentaires avec des majuscules et des minuscules et garder une indentation constante pour le texte.

### Exemple en CSS
```css
/* ==========================================================================
   Bloc de commentaire de section
   ========================================================================== */

/* Bloc de commentaire de sous-section
   ========================================================================== */

/*
 * Groupe de bloc de commentaires.
 * Parfait pour les explications sur plusieurs lignes et la documentation.
 */

/* Commentaire simple */
```

### Exemple en SCSS
```scss
// ==========================================================================
// Bloc de commentaire de section
// ==========================================================================

// Bloc de commentaire de sous-section
// ==========================================================================

//
// Groupe de bloc de commentaires.
// Parfait pour les explications sur plusieurs lignes
// et la documentation

// Commentaire simple
```

_**Astuce :** Paramètrez votre éditeur pour qu'il vous fournisse des raccourcis claviers qui produisent des commentaires conventionnels._

### Exemple concret
```css
/* ==========================================================================
   Header
   ========================================================================== */

/* Header - menu
   ========================================================================== */
   
/* Header - sous-menu
   ========================================================================== */

/*
 * Différentes tailles disponibles pour les boutons.
 * s,m,l = small(12px), medium(18px), large(22px)
 */
.btn-s { line-height: 12px; }
.btn-m { line-height: 18px; }
.btn-l { line-height: 22px; }

.btn {
  border: 1px solid black;
  background: rgba(0, 0, 0, 0.2);
  /* RGBA pour IE */
  filter:progid:DXImageTransform.Microsoft.gradient(startColorstr=#FF000000,endColorstr=#FF000000);
}
```

<a name="format"></a>
## 4. Format

Le format de code choisi permet d'assurer : une bonne lisibilité, des commentaires clairs, une réduction des probabilités d'insertion accidentelle d'erreurs, et la production de fichiers diff et de résolution des problèmes pratiques.

* Un seul sélecteur par ligne dans les régles à plusieurs sélecteurs ;
* Un espace avant l'accolade ouvrante d'une règle ;
* Une déclaration par ligne dans un bloc de déclarations ;
* Un espace après les deux points d'une déclaration ;
* Ajouter toujours un point-virgule à la fin de la dernière déclaration d’un bloc ;
* Fermer l'accolade d'une règle au même niveau que le premier caractère de la règle ;
* Sauter une ligne entre chaque règle.

```css
.selecteur-1,
.selecteur-2,
.selecteur-3 {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: block;
    color: #333;
    background: #fff;
}
```

### Ordre des déclarations

L'ordre des déclarations doit toujours obéir à la même règle.  
Les règles doivent respecter cet ordre, règles connexes ensemble et déclarer les propriétés importantes relatives à la structure (c-à-d le positionnement et le modèle de boîte) avant les règles typographiques, l'arrière-plan et les couleurs.

```css
.selecteur {
    /* @include/@extend */

    /* Position/z-index */
    position: relative;
    top: -10px;
    left: -10px;
    z-index: 5;

    /* Boîte */
    width: 100%;
    height: 100%;
    margin: 2em;
    padding: 1em;
    
    /* Bordure */
    border: 1px solid red;
    border-radius: 4px;
    
    /* Fond */
    background: #000;
    
    /* Texte */
    color: #777;
    font: normal 1em/1.4 sans-serif;
    
    /* Autres */
    -moz-box-shadow: 3px 4px 5px #000;
    -webkit-box-shadow: 3px 4px 5px #000;
    box-shadow: 3px 4px 5px #000;
}
```

### Exceptions et légèrs écarts

De gros blocs de déclarations uniques peuvent utiliser un format légèrement différent, regroupées sur une seule ligne. Dans ce cas, il faut insérer un espace après l'accolade ouvrante et avant l'accolade fermante.

```css
.selecteur-1 { width: 10%; }
.selecteur-2 { width: 20%; }
.selecteur-3 { width: 30%; }
```

Les longues valeurs de propriétés, séparées par des virgules - comme des ensembles de dégradés et d'ombres - peuvent être agencées sur plusieurs lignes de manière à améliorer la lisibilité et produire des fichiers diff plus utiles.

```css
.selecteur {
    box-shadow:
        1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
    background-image:
        linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
}
```

### Préprocesseurs: considérations additionnelles pour le formatage

Les conventions suivantes font référence à Sass.

* Limiter l'imbrication à **un niveau de profondeur**.
* Eviter d'imbriquer un trop grand nombre de règles, séparez-les lorsque cela nuit à la lisibilité.
* Placer toujours les déclarations `@extend` en début de bloc.
* Si possible, regrouper toutes les déclarations `@include` en début de bloc juste après les déclarations `@extend`.
* Penser à préfixer vos propres fonctions avec x- ou un autre espace de nom. Cela permet d'éviter potentiellement de confondre votre fonction avec une fonction native CSS, ou les conflits avec des fonctions provenant de bibliothèques.

```scss
.selecteur-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    /* Autres */
}
```

<a name="naming"></a>
## 5. Nommage

Utiliser des noms clairs et réfléchis pour les classes HTML.
Choisissez un modèle de nommage cohérent et compréhensif qui a du sens à la fois dans les fichiers HTML et dans les fichiers CSS.

* Le nom des classes doit être en **anglais** ;
* Plusieurs mots dans une classe doivent être séparés par un trait d'union ;
* Utiliser des classes et non des IDs dans la mesure du possible.

_Astuce : aidez-vous des différents framework CSS pour trouver des idées de nom de classe._

```css
/* Exemple de code mal nommé */
.s-scr {
    overflow: auto;
}

.cb {
    background: #000;
}

/* Exemple de code bien nommé */
.is-scrollable {
    overflow: auto;
}

.column-body {
    background: #000;
}
```

<a name="i18n"></a>
## 6. Internationalisation / traductions

Dans l'ensemble de vos dévelopements, chaque terme ou phrase, (_/!\ même pour vos tests_) doivent réspécter la syntaxe suivante :  
`//I_terme//` et `//I_Votre phrase//`
Une seule personne doit être en charge du wording, le chef de projet ou le client, cette synataxe permet d'identifier plus
rapidement les termes et phrases qu'il reste à traduire.
Lorsque c'est possible, vous pouvez remplacer ces termes par les variables de traduction, ex : `{{word|trans}}`
ou par les variables php/twig appropriées. Mais sans toute fois modifier les fichiers de langue .po, .mo et .yml associés,
qui sont reservés à la personne en charge du wording.

<a name="organization"></a>
## 7. Organisation

L'organisation du code est une partie importante.

* Séparer de manière logique les différentes parties de code (à l'aide des commentaires) ;
* Utiliser des fichiers distincts (concaténés au cours de l'étape de compilation) pour aider à découper le code en différents composants ;
* Si un préprocesseur est disponible sur votre projet, stockez le code récurrent dans des variables pour la couleur, la typographie, etc ;
* Organiser les classes en suivant la méthode OOCSS.

```
// Exemple d'organisation des fichiers
styles
├── components
│   ├── comments.scss
│   └── listings.scss
├── globals
│   ├── browser_helpers.scss
│   └── variables.scss
├── plugins
│   ├── jquery.fancybox-1.3.4.css
│   └── reset.scss
├── sections
│   ├── issues.scss
│   ├── profile.scss
└── shared
    └── forms.scss
```

```css
/* Exemple de boutons gérés avec la méthode OOCSS */
.btn {
   display: inline-block;
   padding: 0 10px;
   border: 1px solid black;
   border-radius: 4px;
   text-align: center;
}

/* Différentes couleurs disponibles pour les boutons. */
.btn-primary { background-color: red; }
.btn-secondary { background-color: grey; }

/*
 * Différentes tailles disponibles pour les boutons.
 * s,m,l = small(12px), medium(18px), large(22px)
 */
.btn-s { line-height: 12px; }
.btn-m { line-height: 18px; }
.btn-l { line-height: 22px; }
```

<a name="microformats"></a>
## 8. Microformats

Le microformat utilisé au pôle intégration est celui-ci : [http://schema.org/](http://schema.org/)
Chaque contenu qui peut l'être doit être taggé.
Naturellement, seules les interfaces front-office sont concernée, les interfaces backoffice par définition
non accessibles aux moteurs de recherche sont à exclures.

<a name="javascript"></a>
## 9. Javascript

### Librairie/framework

La librairie javascript à utiliser est [jQuery](http://jquery.com/).

Dans la mesure du possible vous devez utiliser les plugins internes à l'agence, si ceux-ci ne répondent pas à vos besoins  
référez-vous à l'intégrateur référent pour savoir si vous pouvez le développer ou en utiliser un public.
Chaque plugin dévelopé à l'agence doit être le plus générique possible et être àjouté au DOJO du pôle intégration.  
La règle à suivre pour les plugin est de pouvoir configurer celui-ci uniquement en html via les attributs HTML5 data-*  
Idéalement aucune configuration ne doit se faire en javascript. Pour ce qui est de l'intérnationalisation,
les termes doivent également êtres passés via les attributs data-*.

* Toutes vos actions doivent êtres associées à un élément `<button type="button">` et non à un lien (`<a href="#"`)
sauf si celui-ci est un lien qui fonctionne sans javascript activé, par exemple un lien vers une photo sans javascript
qui s'ouvre dans une pop-up avec javascript ;
* Autant que possible votre contenu doit s'afficher correctement avec javascript désactivé.

### Canvas

Les librairies canvas à uliser sont :
* [KineticJS](http://www.kineticjs.com/)
* [Google Chart](https://developers.google.com/chart/)

Autant que possible, ajoutez vos dévelopements canvas au DOJO du pôle intégration.

<a name="tools"></a>
## 10. Outils utiles

* [Encoder les images en base64](http://xaviesteve.com/pro/base64.php)
* [Compresser les png](http://tinypng.org/)
* [Afficher des images de remplacement](http://placehold.it/)
* [Convertir des caracètres html](http://matthieu.com/htmlchars/)
* [Générateur d'image de chargement](http://www.ajaxload.info/)

<a name="sources"></a>
## 11. Sources et inspiration

Cette documentation est largement inspirée :
* Du projet [idiomatic-css](https://github.com/necolas/idiomatic-css) ;
* De github [CSS Styleguide](https://github.com/styleguide/css) ;
* De [Google HTML/CSS Style Guide](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml) ;
* Du livre [CSS maintenables](http://www.editions-eyrolles.com/Livre/9782212134179/css-maintenables) ;
* De mon expérience personnelle.