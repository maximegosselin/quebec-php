# SAQ

- Site : <https://www.saq.com/>
- Vérifié le : 2026-10-24 (Chrome headless, page d'accueil)
- Verdict : Magento
- Méthodes : 5, 6, 8

## 5. Chemins et marqueurs de CMS

```html
<script type="text/javascript" src="https://www.saq.com/static/version1792586433/frontend/Saq/saq/fr_CA/requirejs/require.min.js">
```

## 6. URL en `.php`

Vérifié à la main dans Chrome, 2026-10-24 : <https://www.saq.com/index.php> répond, alors que <https://www.saq.com/index2.php> donne une erreur 404. Le fichier `index.php` existe donc bien ; c'est le point d'entrée de Magento.

## 8. Cookies

Cookie `PHPSESSID` relevé à la main dans les outils de développement (F12, onglet **Application**). Une requête simple (curl) ne le renvoie pas.

## Fournisseur

Modules `Absolunet_…` dans le thème Magento (Absolunet, Montréal), par déduction.

```html
<img src="https://www.saq.com/static/version1792586433/frontend/Saq/saq/fr_CA/Absolunet_Footer/images/saq_logo_moderation_fr.svg" alt="La modération a bien meilleur goût." loading="lazy">
```

```html
<script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="Absolunet_StoreLocator/js/action/getStoreOpenedLabel" src="https://www.saq.com/static/version1792586433/frontend/Saq/saq/fr_CA/Absolunet_StoreLocator/js/action/getStoreOpenedLabel.min.js">
```
