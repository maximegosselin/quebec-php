# Cégep de Sainte-Foy

- Site : <https://www.csfoy.ca/accueil>
- Vérifié le : 2026-10-24 (Chrome headless, page d'accueil)
- Verdict : TYPO3
- Méthodes : 1, 2, 5, 6

## 1. Balise `generator`

```html
<meta name="generator" content="TYPO3 CMS">
```

## 2. Commentaire dans le HTML

```html
<!-- build by sitepackagebuilder.com This website is powered by TYPO3 - inspiring people to share! TYPO3 is a free open source Content Management Framework initially created by Kasper Skaarhoj and licensed under GNU/GPL. TYPO3 is copyright 1998-2026 of Kasper Skaarhoj. Extensions are copyright of th…
```

## 5. Chemins et marqueurs de CMS

```html
<link rel="icon" href="/typo3conf/ext/skin_site_principal/Resources/Public/Icons/favicon.ico" type="image/vnd.microsoft.icon">
```

## 6. URL en `.php`

```html
<!-- <div class="sticky-footer isBig" id="sticky-footer"> <div class="sub-sticky-footer"> <div class="small-footer"> <button id="openStickyFooter">Guide étudiant</button> </div> <div class="big-footer"> <button id="closeStickyFooter">X</button> <p><a href="https://www.csfoy.ca/index.php?id=6460">Con…
```

```html
<a href="https://www.csfoy.ca/index.php?id=37">
```
