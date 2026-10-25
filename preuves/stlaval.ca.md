# Société de transport de Laval (STL)

- Site : <https://www.stlaval.ca>
- Vérifié le : 2026-10-24 (Chrome headless, page d'accueil)
- Verdict : Craft CMS
- Méthodes : 5, 6, 7
- Notes : le témoin `CRAFT_CSRF_TOKEN` (Craft CMS) figure dans la liste des témoins affichée par le site

## 5. Chemins et marqueurs de CMS

```html
<td data-column="Nom">CRAFT_CSRF_TOKEN</td>
```

## 6. URL en `.php`

```html
<form id="subscribe-newsletter-form" method="post" action="https://stlaval.ca/index.php?p=actions/newsletter/api/register" novalidate="">
```

## 7. En-têtes HTTP

Requête simple (curl, User-Agent de Chrome), 2026-10-24. SEOmatic est une extension de Craft CMS.

```http
X-Powered-By: SEOmatic
```
