Conventions d'intégration CSS/HTML
==================================

Ce document doit permettre d'uniformiser le code HTML/CSS du pôle intégration à l'aide de différentes conventions.  
Le but recherché est de disposer d'un code maintenable facilement sur l'ensembles des projet gérés par le pôle
et que n'importe quel projet soit accessible à n'importe quel intervenant connaissant nos conventions.

## Table des matières

1. [Principes généraux](#general-principles)
2. [Indentation](#whitespace)
3. [Commentaires](#comments)
4. [Format](#format)
5. [Nommage](#naming)
6. [Exemple pratique](#example)
7. [Organisation](#organization)
8. [microformats](#microformats)
9. [Compilation et déploiement](#build-and-deployment)
10. [Sources et inspiration](#sources)

<a name="general-principles"></a>
## 1. Principes généraux

### Principes
* Tout code présent dans n'importe quelle base de code doit avoir l'air d'avoir été écrit par une seule personne, peu importe le nombre de gens qui y ont contribué ;
* Appliquez les conventions de style de manière stricte ;
* En cas de doute tournez vous vers vos collègue ou vers l'intégrateur référent.

### Règles de base
* Éviter au maximum d'utiliser les IDs pour styler les éléments ;
* Ne pas préciser d'unité pour la valeur 0 ;
* Utiliser les formes raccourcies, exemple : `padding: 10px 5px;` ;
* Ne pas préciser le 0 pour les valeurs comprises entre -1 et 1 : `font-size: .8em;` ;
* Noter le code héxadécimal toujours en minuscule avec 3 lettres si possible ;
* Utilisez toujours le même type de guillemets, à savoir les doubles guillemets, exemple : `content: "";` ;
* Utilisez toujours des guillemets pour les valeurs dans les sélecteurs, exemple : 'input[type="checkbox"]' ;
* Pas de hacks.

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
* Placez les commentaires sur une nouvelle ligne au-dessus de leur sujet ;
* Evitez les commentaires en fin de ligne ;
* Gardez une longueur de ligne de taille raisonnable, **80 caractères** ;
* Pas de z-index délirants, valeur maximum 99 ;
* Rédigez vos commentaires avec des majuscules et des minuscules et gardez une indentation constante pour le texte.

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
* Ajoutez toujours un point-virgule à la fin de la dernière déclaration d’un bloc ;
* Fermez l'accolade d'une règle au même niveau que le premier caractère de la règle ;
* Sautez une ligne entre chaque règle.

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
    /* Position/z-indx */
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

#### Préprocesseurs: considérations additionnelles pour le formatage

Les conventions suivantes font référence à Sass.

* Limiter l'imbrication à **un niveau de profondeur**.
* Evitez d'imbriquer un trop grand nombre de règles, séparez-les lorsque cela nuit à la lisibilité.
* Placez toujours les déclarations "@extend" en début de bloc.
* Si possible, regroupez toutes les déclarations "@include" en début de bloc juste après les déclarations "@extend".
* Pensez à préfixer vos propres fonctions avec x- ou un autre espace de nom. Cela permet d'éviter potentiellement de confondre votre fonction avec une fonction native CSS, ou les conflits avec des fonctions provenant de bibliothèques.

```scss
.selecteur-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    /* Autres */
}
```

<a name="sources"></a>
## 10. Sources et inspiration

Cette documentation est largement inspirée :
* Du projet [idiomatic-css](https://github.com/necolas/idiomatic-css) ;
* De github [CSS Styleguide](https://github.com/styleguide/css) ;
* De [Google HTML/CSS Style Guide](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml) ;
* Du livre [CSS maintenables](http://www.editions-eyrolles.com/Livre/9782212134179/css-maintenables) ;
* De mon expérience personnelle.