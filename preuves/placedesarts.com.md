# Société de la Place des Arts de Montréal

- Site : <https://www.placedesarts.com>
- Vérifié le : 2026-10-24 (Chrome headless, page d'accueil)
- Verdict : Craft CMS
- Méthodes : 5, 6, 7

## 5. Chemins et marqueurs de CMS

```html
<script src="https://www.placedesarts.com/cpresources/351c00d8/js/scripts/front-end/plugin/freeform.js?v=1790856448">
```

```html
<input type="hidden" name="CRAFT_CSRF_TOKEN" value="…">
```

## 6. URL en `.php`

```html
<form name="waitinglistform" class="sb-waiting-list__form" method="post" action="https://www.placedesarts.com/index.php?p=actions/event-alert/subscribe" data-submit-bound="true">
```

## 7. En-têtes HTTP

Requête simple (curl, User-Agent de Chrome), 2026-10-24. SEOmatic est une extension de Craft CMS.

```http
X-Powered-By: SEOmatic
```
