# Ministère de la Cybersécurité et du Numérique : Centre gouvernemental de cyberdéfense

- Site : <https://www.cyber.gouv.qc.ca>
- Vérifié le : 2026-10-25 (Chrome headless, page d'accueil)
- Verdict : AUCUN
- Méthodes : aucune
- Notes : Statistiques Matomo

Aucune signature PHP dans la page.

## Autres indices

Balise `generator` sans nom de produit :

```html
<meta name="generator" content="me">
```

Statistiques Matomo hébergées sur un autre domaine :

```html
var u = "https://analytique.itq.gouv.qc.ca/itq/"
```

```html
<script type="text/javascript"> function getCookie(name) { const match = document.cookie.match(new RegExp("(^| )" + name + "=([^;]+)")); return match ? match[2] : null; } var cookiesAccepted = getCookie("cookiesAccepted"); var analyticsCookies = getCookie("analyticsCookies"); if ( (cookiesAccepted =…
```
