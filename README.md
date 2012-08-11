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

* Tout code présent dans n'importe quelle base de code doit avoir l'air d'avoir été écrit par une seule personne, peu importe le nombre de gens qui y ont contribué ;
* Appliquez les conventions de style de manière stricte ;
* En cas de doute tournez vous vers vos collègue ou vers l'intégrateur référent.

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

<a name="sources"></a>
## 4. Sources et inspiration

Cette documentation est largement inspirée :
* Du projet [idiomatic-css](https://github.com/necolas/idiomatic-css) ;
* De github [CSS Styleguide](https://github.com/styleguide/css) ;
* De [Google HTML/CSS Style Guide](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml) ;
* Du livre [CSS maintenables](http://www.editions-eyrolles.com/Livre/9782212134179/css-maintenables) ;
* De mon expérience personnelle.