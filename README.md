# Le secteur public québécois et PHP

Portrait de l'usage de PHP par le secteur public québécois, à partir des sites
web publics de ses organisations, avec la technologie trouvée et la façon de la
vérifier. Le relevé couvre les organisations financées ou détenues par le
gouvernement du Québec ou par les municipalités : ministères, organismes,
sociétés d'État, tribunaux, réseaux de la santé et de l'éducation, municipalités
et organismes municipaux. Les entreprises privées sont exclues.

Chaque verdict repose surtout sur la page d'accueil du site telle qu'elle était
à la date indiquée. Pour le vérifier, il suffit de refaire l'une des méthodes
notées ou de consulter la preuve, liée depuis la date de vérification. Les
modifications du relevé sont listées dans [l'historique](HISTORIQUE.md).

## Sommaire

- [Méthode](#méthode)
- [Sites sur PHP](#sites-sur-php)
  - [Gouvernement](#gouvernement)
  - [Ministères](#ministères)
  - [Organismes](#organismes)
  - [Sociétés d'État](#sociétés-détat)
  - [Tribunaux](#tribunaux)
  - [Santé](#santé)
  - [Éducation](#éducation)
  - [Municipalités](#municipalités)
- [Sites sans signature de PHP](#sites-sans-signature-de-php)
  - [Gouvernement](#gouvernement-1)
  - [Ministères](#ministères-1)
  - [Organismes](#organismes-1)
  - [Sociétés d'État](#sociétés-détat-1)
  - [Santé](#santé-1)
  - [Éducation](#éducation-1)
  - [Municipalités](#municipalités-1)
- [Sites à visiter](#sites-à-visiter)
- [Historique](HISTORIQUE.md)

## Méthode

La plupart des pages ont été enregistrées avec Chrome headless, puis analysées
par un script. Pour vérifier à la main : ouvrir le site dans Chrome,
afficher le code source (Ctrl+U) et chercher (Ctrl+F) les signatures
ci-dessous. Un indice ajouté par JavaScript n'apparaît pas dans Ctrl+U : il se
voit dans les outils de développement (F12), onglet **Elements**. Les en-têtes
et les cookies se voient dans les onglets **Network** et **Application**.

TYPO3, Drupal, WordPress, Joomla, Magento et Craft CMS sont écrits en PHP :
reconnaître l'un d'eux suffit pour conclure que le site utilise PHP. Le verdict
« PHP » veut dire que PHP est visible (URL en `.php`, en-tête, cookie) sans que
le CMS soit identifié.

Un site n'a pas de raison d'afficher une signature de PHP qu'il n'utilise pas :
même les méthodes par déduction sont fiables. La colonne « Méthodes » des
tableaux renvoie aux numéros suivants, classés de la signature la plus directe à
la moins directe.

| # | Méthode | Exemples | Nature |
|---|---|---|---|
| 1 | Balise `generator` | `<meta name="generator" content="TYPO3 CMS">`, `Drupal`, `WordPress`, `Joomla!` | Déclaration |
| 2 | Commentaire dans le HTML | « This website is powered by TYPO3 », code `<?php … ?>` oublié | Déclaration ou fuite |
| 3 | Page d'erreur du CMS | « Oops, an error occurred! » de TYPO3 | Déclaration |
| 4 | Extension de CMS déclarée | `generator` d'Elementor, WPML, WP Rocket ou Site Kit, commentaire de Yoast SEO (WordPress) | Déclaration indirecte |
| 5 | Chemins et marqueurs de CMS | TYPO3 : `/fileadmin/`, `/typo3conf/`, `/_assets/` ; Drupal : `/sites/default/files/`, `/core/misc/`, `data-drupal-selector` ; WordPress : `/wp-content/`, `/wp-includes/`, `/wp-json/` ; Magento : `/static/version…/frontend/` ; Craft CMS : `/cpresources/`, `CRAFT_CSRF_TOKEN` | Déduction |
| 6 | URL en `.php` | `nous_joindre.php`, `/php/resultat.php` | Déduction |
| 7 | En-têtes HTTP | `X-Powered-By: PHP/…`, `X-Powered-By: SEOmatic` (Craft CMS) | Déduction |
| 8 | Cookies | `PHPSESSID`, `fe_typo_user` (TYPO3), `SSESS…` (Drupal) | Déduction |
| 9 | Source publique | étude de cas, portfolio ou blogue d'un fournisseur | Déclaration d'un tiers |

Les statistiques Matomo (`matomo.php`, cookies `_pk_…`) tournent sur PHP, mais
peuvent être hébergées ailleurs que le site : elles sont signalées en note
seulement.

## Sites sur PHP

235 des 320 sites visités utilisent PHP.

### Gouvernement

| Organisation | Site | Verdict | Méthodes | Notes | Vérifié le |
|---|---|---|---|---|---|
| Données Québec | [donneesquebec.ca](https://www.donneesquebec.ca/) | WordPress | 2, 4, 5, 6 | Le catalogue (`/recherche/`) est sur CKAN (Python) | [2026-10-23](preuves/donneesquebec.ca.md) |
| Québec.ca | [quebec.ca](https://www.quebec.ca/) | TYPO3 | 1, 2, 5, 9 | [blogue Québec.ca, bilan 2024](https://www.quebec.ca/blogue/details/bilan-grands-jalons-2024) ; [étude de cas TYPO3](https://typo3.com/case-studies/quebec) ; les pages des ministères (`quebec.ca/gouvernement/ministeres-organismes/…`) font partie de ce site | [2026-10-24](preuves/quebec.ca.md) |

### Ministères

| Organisation | Site | Verdict | Méthodes | Notes | Vérifié le |
|---|---|---|---|---|---|
| Secrétariat du Conseil du trésor | [tresor.gouv.qc.ca](https://www.tresor.gouv.qc.ca/) | TYPO3 | 1, 2, 5 | Statistiques Matomo | [2026-10-23](preuves/tresor.gouv.qc.ca.md) |
| Service d'authentification gouvernementale | [authentification.quebec.ca](https://authentification.quebec.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/authentification.quebec.ca.md) |

### Organismes

| Organisation | Site | Verdict | Méthodes | Notes | Vérifié le |
|---|---|---|---|---|---|
| Autorité des marchés financiers | [lautorite.qc.ca](https://lautorite.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/lautorite.qc.ca.md) |
| Autorité des marchés publics | [amp.quebec](https://www.amp.quebec/) | Drupal | 1, 5 | Statistiques Matomo | [2026-10-24](preuves/amp.quebec.md) |
| Autorité régionale de transport métropolitain (ARTM) | [artm.quebec](https://artm.quebec/) | WordPress | 4, 5 |  | [2026-10-23](preuves/artm.quebec.md) |
| Bureau des enquêtes indépendantes | [bei.gouv.qc.ca](https://bei.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/bei.gouv.qc.ca.md) |
| Bureau du coroner | [coroner.gouv.qc.ca](https://coroner.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/coroner.gouv.qc.ca.md) |
| Bureau du forestier en chef | [forestierenchef.gouv.qc.ca](https://forestierenchef.gouv.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/forestierenchef.gouv.qc.ca.md) |
| Centre de la francophonie des Amériques | [francophoniedesameriques.com](https://francophoniedesameriques.com/) | Drupal | 1, 5 |  | [2026-10-23](preuves/francophoniedesameriques.com.md) |
| Commissaire à la lutte contre la corruption | [upac.gouv.qc.ca](https://upac.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/upac.gouv.qc.ca.md) |
| Commissaire à la santé et au bien-être | [csbe.gouv.qc.ca](https://csbe.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/csbe.gouv.qc.ca.md) |
| Commissaire au lobbyisme du Québec | [commissairelobby.qc.ca](https://www.commissairelobby.qc.ca/) | WordPress | 4, 5, 6 | Redirige vers lobbyisme.quebec | [2026-10-24](preuves/commissairelobby.qc.ca.md) |
| Commission d'enquête sur la modernisation des systèmes informatiques de la SAAQ | [cesis.gouv.qc.ca](https://cesis.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/cesis.gouv.qc.ca.md) |
| Commission de l'éthique en science et en technologie | [ethique.gouv.qc.ca](https://ethique.gouv.qc.ca/) | WordPress | 4, 5 |  | [2026-10-23](preuves/ethique.gouv.qc.ca.md) |
| Commission de la capitale nationale du Québec | [capitale.gouv.qc.ca](https://capitale.gouv.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/capitale.gouv.qc.ca.md) |
| Commission de protection du territoire agricole du Québec | [cptaq.gouv.qc.ca](https://www.cptaq.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/cptaq.gouv.qc.ca.md) |
| Commission des normes, de l'équité, de la santé et de la sécurité du travail (CNESST) | [cnesst.gouv.qc.ca](https://www.cnesst.gouv.qc.ca/) | Drupal | 1, 5 |  | [2026-10-24](preuves/cnesst.gouv.qc.ca.md) |
| Commission des partenaires du marché du travail | [cpmt.gouv.qc.ca](https://cpmt.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/cpmt.gouv.qc.ca.md) |
| Commission des transports du Québec | [ctq.gouv.qc.ca](https://ctq.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/ctq.gouv.qc.ca.md) |
| Commission municipale du Québec | [cmq.gouv.qc.ca](https://cmq.gouv.qc.ca/) | PHP | 6, 8 | Cookie `PHPSESSID` relevé à la main (F12) | [2026-10-24](preuves/cmq.gouv.qc.ca.md) |
| Commission québécoise des libérations conditionnelles | [cqlc.gouv.qc.ca](https://cqlc.gouv.qc.ca/) | TYPO3 | 1, 2 |  | [2026-10-23](preuves/cqlc.gouv.qc.ca.md) |
| Conseil des arts et des lettres du Québec | [calq.gouv.qc.ca](https://calq.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/calq.gouv.qc.ca.md) |
| Conseil du patrimoine culturel du Québec | [cpcq.gouv.qc.ca](https://cpcq.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cpcq.gouv.qc.ca.md) |
| Conseil du statut de la femme | [csf.gouv.qc.ca](https://csf.gouv.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/csf.gouv.qc.ca.md) |
| Conseil supérieur de l'éducation | [cse.gouv.qc.ca](https://cse.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cse.gouv.qc.ca.md) |
| École nationale de police du Québec | [enpq.qc.ca](https://enpq.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/enpq.qc.ca.md) |
| École nationale des pompiers du Québec | [ecoledespompiers.gouv.qc.ca](https://ecoledespompiers.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/ecoledespompiers.gouv.qc.ca.md) |
| Élections Québec | [electionsquebec.qc.ca](https://electionsquebec.qc.ca/) | WordPress | 5 |  | [2026-10-23](preuves/electionsquebec.qc.ca.md) |
| Fondation de la faune du Québec | [fondationdelafaune.qc.ca](https://fondationdelafaune.qc.ca/) | WordPress | 4, 5 | Redirige vers fbfq.ca | [2026-10-23](preuves/fondationdelafaune.qc.ca.md) |
| Fonds d'aide aux actions collectives | [faac.justice.gouv.qc.ca](https://faac.justice.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/faac.justice.gouv.qc.ca.md) |
| Fonds de recherche du Québec | [frq.gouv.qc.ca](https://frq.gouv.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/frq.gouv.qc.ca.md) |
| Héma-Québec | [hema-quebec.qc.ca](https://hema-quebec.qc.ca/) | Drupal | 1, 5 | Redirige vers hemaquebec.ca | [2026-10-23](preuves/hema-quebec.qc.ca.md) |
| INSPQ | [inspq.qc.ca](https://www.inspq.qc.ca/) | Drupal | 1, 5, 9 | Site Drupal réalisé par Evolving Web : [fiche de projet](https://evolvingweb.com/projects/institut-national-de-sante-publique-du-quebec-inspq) | [2026-10-24](preuves/inspq.qc.ca.md) |
| Institut de technologie agroalimentaire du Québec | [itaq.ca](https://itaq.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/itaq.ca.md) |
| Institut national d'excellence en santé et en services sociaux | [inesss.qc.ca](https://inesss.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/inesss.qc.ca.md) |
| La Financière agricole du Québec | [fadq.qc.ca](https://fadq.qc.ca/) | TYPO3 | 1, 2, 5, 6 | Statistiques Matomo | [2026-10-23](preuves/fadq.qc.ca.md) |
| Musée d'art contemporain de Montréal | [macm.org](https://macm.org/) | WordPress | 4, 5 |  | [2026-10-23](preuves/macm.org.md) |
| Musée de la civilisation | [mcq.org](https://mcq.org/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/mcq.org.md) |
| Office de la protection du consommateur | [opc.gouv.qc.ca](https://opc.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/opc.gouv.qc.ca.md) |
| Parc olympique | [parcolympique.qc.ca](https://parcolympique.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/parcolympique.qc.ca.md) |
| Protecteur du citoyen | [protecteurducitoyen.qc.ca](https://protecteurducitoyen.qc.ca/) | Drupal | 1, 5 |  | [2026-10-23](preuves/protecteurducitoyen.qc.ca.md) |
| RAMQ | [ramq.gouv.qc.ca](https://www.ramq.gouv.qc.ca/) | Drupal | 5 |  | [2026-10-24](preuves/ramq.gouv.qc.ca.md) |
| RECYC-QUÉBEC | [recyc-quebec.gouv.qc.ca](https://recyc-quebec.gouv.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/recyc-quebec.gouv.qc.ca.md) |
| Régie des alcools, des courses et des jeux | [racj.gouv.qc.ca](https://racj.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/racj.gouv.qc.ca.md) |
| Régie du bâtiment du Québec | [rbq.gouv.qc.ca](https://rbq.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/rbq.gouv.qc.ca.md) |
| Retraite Québec | [retraitequebec.gouv.qc.ca](https://www.retraitequebec.gouv.qc.ca/) | Drupal | 5 |  | [2026-10-24](preuves/retraitequebec.gouv.qc.ca.md) |
| Revenu Québec | [revenuquebec.ca](https://www.revenuquebec.ca/) | TYPO3 | 2, 5 | Statistiques Matomo | [2026-10-24](preuves/revenuquebec.ca.md) |
| Revenu Québec : CGTM | [revenuquebec.ca/cgtm/](https://revenuquebec.ca/cgtm//) | TYPO3 | 2, 5 | Statistiques Matomo | [2026-10-23](preuves/revenuquebec.ca-cgtm.md) |
| Revenu Québec : emplois | [revenuquebec.ca/emplois/](https://revenuquebec.ca/emplois//) | TYPO3 | 2, 5 | Statistiques Matomo | [2026-10-23](preuves/revenuquebec.ca-emplois.md) |
| Sûreté du Québec | [sq.gouv.qc.ca](https://sq.gouv.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/sq.gouv.qc.ca.md) |
| Urgences-santé | [urgences-sante.qc.ca](https://www.urgences-sante.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/urgences-sante.qc.ca.md) |

### Sociétés d'État

| Organisation | Site | Verdict | Méthodes | Notes | Vérifié le |
|---|---|---|---|---|---|
| BAnQ | [banq.qc.ca](https://www.banq.qc.ca/) | Drupal | 5, 9 | Site Drupal réalisé par Evolving Web : [étude de cas Acquia](https://www.acquia.com/resources/customer-stories/bibliotheque-et-archives-nationales-du-quebec-banq), [blogue d'Evolving Web](https://evolvingweb.com/blog/acquia-engage-awards-finalist-banq) | [2026-10-24](preuves/banq.qc.ca.md) |
| Caisse de dépôt et placement du Québec | [cdpq.com](https://www.cdpq.com/) | Drupal | 5 | Redirige vers lacaisse.com | [2026-10-24](preuves/cdpq.com.md) |
| Investissement Québec | [investquebec.com](https://www.investquebec.com/) | Drupal | 5 | Thème `miza_wingsuit`, le même que Retraite Québec | [2026-10-24](preuves/investquebec.com.md) |
| ITHQ | [ithq.qc.ca](https://www.ithq.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-24](preuves/ithq.qc.ca.md) |
| SAAQ | [saaq.gouv.qc.ca](https://saaq.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-24](preuves/saaq.gouv.qc.ca.md) |
| SAQ | [saq.com](https://www.saq.com/) | Magento | 5, 6, 8 | `/index.php` et cookie `PHPSESSID` vérifiés à la main | [2026-10-24](preuves/saq.com.md) |
| Société de développement de la Baie James | [sdbj.gouv.qc.ca](https://sdbj.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/sdbj.gouv.qc.ca.md) |
| Société de développement des entreprises culturelles | [sodec.gouv.qc.ca](https://sodec.gouv.qc.ca/) | WordPress | 2, 4, 5 |  | [2026-10-23](preuves/sodec.gouv.qc.ca.md) |
| Société de la Place des Arts de Montréal | [placedesarts.com](https://www.placedesarts.com/) | Craft CMS | 5, 6, 7 |  | [2026-10-24](preuves/placedesarts.com.md) |
| Société des traversiers du Québec | [traversiers.com](https://traversiers.com/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/traversiers.com.md) |
| Société du Centre des congrès de Québec | [convention.qc.ca](https://convention.qc.ca/) | WordPress | 4, 5 |  | [2026-10-23](preuves/convention.qc.ca.md) |
| Société québécoise d'information juridique : blogue | [blogue.soquij.qc.ca](https://blogue.soquij.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-24](preuves/blogue.soquij.qc.ca.md) |
| Société québécoise d'information juridique : recherche citoyens | [citoyens.soquij.qc.ca](https://citoyens.soquij.qc.ca/) | PHP | 6, 8 | Cookie `PHPSESSID` relevé à la main (F12) | [2026-10-24](preuves/citoyens.soquij.qc.ca.md) |
| Société québécoise des infrastructures | [sqi.gouv.qc.ca](https://sqi.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/sqi.gouv.qc.ca.md) |

### Tribunaux

| Organisation | Site | Verdict | Méthodes | Notes | Vérifié le |
|---|---|---|---|---|---|
| Conseil de la magistrature | [conseildelamagistrature.qc.ca](https://conseildelamagistrature.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/conseildelamagistrature.qc.ca.md) |
| Cour d'appel du Québec | [courdappelduquebec.ca](https://courdappelduquebec.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-24](preuves/courdappelduquebec.ca.md) |
| Cour du Québec | [courduquebec.ca](https://courduquebec.ca/) | TYPO3 | 1, 2, 5 | Extensions Bootstrap Package, ke_search et news | [2026-10-24](preuves/courduquebec.ca.md) |
| Cour supérieure du Québec | [coursuperieureduquebec.ca](https://coursuperieureduquebec.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-24](preuves/coursuperieureduquebec.ca.md) |
| Cours municipales du Québec | [coursmunicipales.ca](https://coursmunicipales.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/coursmunicipales.ca.md) |
| Tribunal administratif de déontologie policière | [tadp.gouv.qc.ca](https://tadp.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/tadp.gouv.qc.ca.md) |
| Tribunal administratif des marchés financiers | [tmf.gouv.qc.ca](https://tmf.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/tmf.gouv.qc.ca.md) |
| Tribunal administratif du logement | [tal.gouv.qc.ca](https://www.tal.gouv.qc.ca/) | Drupal | 5 |  | [2026-10-23](preuves/tal.gouv.qc.ca.md) |
| Tribunal administratif du Québec | [taq.gouv.qc.ca](https://www.taq.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/taq.gouv.qc.ca.md) |
| Tribunal administratif du travail | [tat.gouv.qc.ca](https://tat.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/tat.gouv.qc.ca.md) |
| Tribunal des droits de la personne | [tribunaldesdroitsdelapersonne.ca](https://tribunaldesdroitsdelapersonne.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/tribunaldesdroitsdelapersonne.ca.md) |
| Tribunal des professions | [tribunaldesprofessions.ca](https://tribunaldesprofessions.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/tribunaldesprofessions.ca.md) |

### Santé

| Organisation | Site | Verdict | Méthodes | Notes | Vérifié le |
|---|---|---|---|---|---|
| Centre de santé Inuulitsivik | [inuulitsivik.ca](https://inuulitsivik.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/inuulitsivik.ca.md) |
| CHUM (Centre hospitalier de l'Université de Montréal) | [chumontreal.qc.ca](https://chumontreal.qc.ca/) | Drupal | 1, 5 |  | [2026-10-23](preuves/chumontreal.qc.ca.md) |
| Conseil cri de la santé et des services sociaux de la Baie James | [creehealth.org](https://creehealth.org/) | Drupal | 1, 5 |  | [2026-10-23](preuves/creehealth.org.md) |
| CUSM (Centre universitaire de santé McGill) | [cusm.ca](https://cusm.ca/) | Drupal | 1, 5 |  | [2026-10-23](preuves/cusm.ca.md) |
| Santé Québec Abitibi-Témiscamingue | [cisss-at.gouv.qc.ca](https://www.cisss-at.gouv.qc.ca/) | WordPress | 4, 5 |  | [2026-10-23](preuves/cisss-at.gouv.qc.ca.md) |
| Santé Québec Bas-Saint-Laurent | [cisss-bsl.gouv.qc.ca](https://cisss-bsl.gouv.qc.ca/) | Drupal | 1, 5 |  | [2026-10-23](preuves/cisss-bsl.gouv.qc.ca.md) |
| Santé Québec Capitale-Nationale | [ciusss-capitalenationale.gouv.qc.ca](https://ciusss-capitalenationale.gouv.qc.ca/) | Drupal | 1, 5 | Statistiques Matomo | [2026-10-23](preuves/ciusss-capitalenationale.gouv.qc.ca.md) |
| Santé Québec Centre-Ouest-de-l'Île-de-Montréal | [ciussscentreouest.ca](https://www.ciussscentreouest.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-24](preuves/ciussscentreouest.ca.md) |
| Santé Québec Centre-Sud-de-l'Île-de-Montréal | [ciusss-centresudmtl.gouv.qc.ca](https://ciusss-centresudmtl.gouv.qc.ca/) | Drupal | 1, 5 |  | [2026-10-23](preuves/ciusss-centresudmtl.gouv.qc.ca.md) |
| Santé Québec Chaudière-Appalaches | [cisssca.com](https://cisssca.com/) | TYPO3 | 1, 2, 5, 6 |  | [2026-10-23](preuves/cisssca.com.md) |
| Santé Québec Côte-Nord | [cisss-cotenord.gouv.qc.ca](https://www.cisss-cotenord.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/cisss-cotenord.gouv.qc.ca.md) |
| Santé Québec des Îles | [cisssdesiles.com](https://cisssdesiles.com/) | WordPress | 1, 5, 6 |  | [2026-10-23](preuves/cisssdesiles.com.md) |
| Santé Québec Est-de-l'Île-de-Montréal | [ciusss-estmtl.gouv.qc.ca](https://ciusss-estmtl.gouv.qc.ca/) | Drupal | 1, 5 |  | [2026-10-23](preuves/ciusss-estmtl.gouv.qc.ca.md) |
| Santé Québec Estrie – CHUS | [santeestrie.qc.ca](https://santeestrie.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/santeestrie.qc.ca.md) |
| Santé Québec Gaspésie | [cisss-gaspesie.gouv.qc.ca](https://www.cisss-gaspesie.gouv.qc.ca/) | WordPress | 1, 4, 5, 6, 7 | En-tête `X-Powered-By: PHP` vérifié par requête simple | [2026-10-24](preuves/cisss-gaspesie.gouv.qc.ca.md) |
| Santé Québec Lanaudière | [cisss-lanaudiere.gouv.qc.ca](https://www.cisss-lanaudiere.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/cisss-lanaudiere.gouv.qc.ca.md) |
| Santé Québec Laurentides | [santelaurentides.gouv.qc.ca](https://santelaurentides.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-24](preuves/santelaurentides.gouv.qc.ca.md) |
| Santé Québec Laval | [lavalensante.com](https://www.lavalensante.com/) | TYPO3 | 1, 2, 5 |  | [2026-10-24](preuves/lavalensante.com.md) |
| Santé Québec Montérégie-Centre | [santemonteregie.qc.ca/centre](https://santemonteregie.qc.ca/centre/) | Drupal | 5 |  | [2026-10-23](preuves/santemonteregie.qc.ca-centre.md) |
| Santé Québec Montérégie-Est | [santemonteregie.qc.ca/est](https://santemonteregie.qc.ca/est/) | Drupal | 5 |  | [2026-10-23](preuves/santemonteregie.qc.ca-est.md) |
| Santé Québec Montérégie-Ouest | [santemo.quebec](https://santemo.quebec/) | Drupal | 5 | Redirige vers santemonteregie.qc.ca | [2026-10-23](preuves/santemo.quebec.md) |
| Santé Québec Nord-de-l'Île-de-Montréal | [ciusssnordmtl.ca](https://ciusssnordmtl.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/ciusssnordmtl.ca.md) |
| Santé Québec Ouest-de-l'Île-de-Montréal | [ciusss-ouestmtl.gouv.qc.ca](https://ciusss-ouestmtl.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/ciusss-ouestmtl.gouv.qc.ca.md) |
| Santé Québec Outaouais | [cisss-outaouais.gouv.qc.ca](https://cisss-outaouais.gouv.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/cisss-outaouais.gouv.qc.ca.md) |
| Santé Québec Saguenay–Lac-Saint-Jean | [santesaglac.gouv.qc.ca](https://santesaglac.gouv.qc.ca/) | PHP | 6 |  | [2026-10-23](preuves/santesaglac.gouv.qc.ca.md) |

### Éducation

| Organisation | Site | Verdict | Méthodes | Notes | Vérifié le |
|---|---|---|---|---|---|
| Cégep à distance | [cegepadistance.ca](https://cegepadistance.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cegepadistance.ca.md) |
| Cégep André-Laurendeau | [claurendeau.qc.ca](https://claurendeau.qc.ca/) | WordPress | 4, 5 | Lien vers Moodle (formation.claurendeau.qc.ca) | [2026-10-23](preuves/claurendeau.qc.ca.md) |
| Cégep Beauce-Appalaches | [cegepba.qc.ca](https://cegepba.qc.ca/) | WordPress | 4, 5 |  | [2026-10-23](preuves/cegepba.qc.ca.md) |
| Cégep Champlain – Campus Saint-Lawrence | [slc.qc.ca](https://slc.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/slc.qc.ca.md) |
| Cégep Champlain – Lennoxville | [crc-lennox.qc.ca](https://crc-lennox.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/crc-lennox.qc.ca.md) |
| Cégep Champlain – Saint-Lambert | [champlainonline.com/champlainweb](https://champlainonline.com/champlainweb/) | WordPress | 1, 4, 5, 6 | Redirige vers champlainsaintlambert.ca | [2026-10-23](preuves/champlainonline.com-champlainweb.md) |
| Cégep de Baie-Comeau | [cegepbc.ca](https://cegepbc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cegepbc.ca.md) |
| Cégep de Bois-de-Boulogne | [bdeb.qc.ca](https://bdeb.qc.ca/) | WordPress | 4, 5 | Statistiques Matomo | [2026-10-23](preuves/bdeb.qc.ca.md) |
| Cégep de Chicoutimi | [cchic.ca](https://cchic.ca/) | WordPress | 5, 6 |  | [2026-10-23](preuves/cchic.ca.md) |
| Cégep de Drummondville | [cegepdrummond.ca](https://cegepdrummond.ca/) | WordPress | 1, 5, 6 |  | [2026-10-23](preuves/cegepdrummond.ca.md) |
| Cégep de Granby | [cegepgranby.ca](https://cegepgranby.ca/) | WordPress | 4, 5 |  | [2026-10-23](preuves/cegepgranby.ca.md) |
| Cégep de Jonquière | [cegepjonquiere.ca](https://cegepjonquiere.ca/) | PHP | 6 |  | [2026-10-23](preuves/cegepjonquiere.ca.md) |
| Cégep de l'Abitibi-Témiscamingue | [cegepat.qc.ca](https://www.cegepat.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-24](preuves/cegepat.qc.ca.md) |
| Cégep de l'Outaouais | [cegepoutaouais.qc.ca](https://cegepoutaouais.qc.ca/) | WordPress | 1, 5, 6 |  | [2026-10-23](preuves/cegepoutaouais.qc.ca.md) |
| Cégep de la Gaspésie et des Îles | [cegepgim.ca](https://cegepgim.ca/) | WordPress | 4, 5, 6 |  | [2026-10-25](preuves/cegepgim.ca.md) |
| Cégep de La Pocatière | [cegeplapocatiere.qc.ca](https://cegeplapocatiere.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cegeplapocatiere.qc.ca.md) |
| Cégep de Lévis | [cegeplevis.ca](https://cegeplevis.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cegeplevis.ca.md) |
| Cégep de Maisonneuve | [cmaisonneuve.qc.ca](https://cmaisonneuve.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/cmaisonneuve.qc.ca.md) |
| Cégep de Matane | [cegep-matane.qc.ca](https://cegep-matane.qc.ca/) | WordPress | 4, 5 |  | [2026-10-23](preuves/cegep-matane.qc.ca.md) |
| Cégep de Rosemont | [crosemont.qc.ca](https://crosemont.qc.ca/) | WordPress | 4, 5 |  | [2026-10-23](preuves/crosemont.qc.ca.md) |
| Cégep de Saint-Félicien | [cegepstfe.ca](https://cegepstfe.ca/) | WordPress | 5 |  | [2026-10-23](preuves/cegepstfe.ca.md) |
| Cégep de Saint-Hyacinthe | [cegepsth.qc.ca](https://cegepsth.qc.ca/) | WordPress | 5 |  | [2026-10-23](preuves/cegepsth.qc.ca.md) |
| Cégep de Saint-Jérôme | [cstj.qc.ca](https://cstj.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/cstj.qc.ca.md) |
| Cégep de Saint-Laurent | [cegepsl.qc.ca](https://cegepsl.qc.ca/) | WordPress | 1, 5, 6 |  | [2026-10-23](preuves/cegepsl.qc.ca.md) |
| Cégep de Sainte-Foy | [csfoy.ca](https://www.csfoy.ca/accueil) | TYPO3 | 1, 2, 5, 6 |  | [2026-10-24](preuves/csfoy.ca-accueil.md) |
| Cégep de Sept-Îles | [cegepsi.ca](https://cegepsi.ca/) | WordPress | 4, 5 |  | [2026-10-23](preuves/cegepsi.ca.md) |
| Cégep de Shawinigan | [cegepshawinigan.ca](https://cegepshawinigan.ca/) | WordPress | 1, 5, 6 |  | [2026-10-23](preuves/cegepshawinigan.ca.md) |
| Cégep de Sherbrooke | [cegepsherbrooke.qc.ca](https://cegepsherbrooke.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cegepsherbrooke.qc.ca.md) |
| Cégep de Sorel-Tracy | [cegepst.qc.ca](https://cegepst.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cegepst.qc.ca.md) |
| Cégep de Thetford | [cegepthetford.ca](https://cegepthetford.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cegepthetford.ca.md) |
| Cégep de Trois-Rivières | [cegeptr.qc.ca](https://cegeptr.qc.ca/) | WordPress | 4, 5 |  | [2026-10-23](preuves/cegeptr.qc.ca.md) |
| Cégep de Valleyfield | [cegepvalleyfield.ca](https://cegepvalleyfield.ca/) | WordPress | 4, 5 |  | [2026-10-23](preuves/cegepvalleyfield.ca.md) |
| Cégep de Victoriaville | [cegepvicto.ca](https://cegepvicto.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cegepvicto.ca.md) |
| Cégep du Vieux Montréal | [cvm.qc.ca](https://cvm.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/cvm.qc.ca.md) |
| Cégep Garneau | [cegepgarneau.ca](https://cegepgarneau.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cegepgarneau.ca.md) |
| Cégep Gérald-Godin | [cgodin.qc.ca](https://cgodin.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cgodin.qc.ca.md) |
| Cégep John Abbott | [johnabbott.qc.ca](https://johnabbott.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/johnabbott.qc.ca.md) |
| Cégep Limoilou | [cegeplimoilou.ca](https://cegeplimoilou.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cegeplimoilou.ca.md) |
| Cégep Lionel-Groulx | [clg.qc.ca](https://clg.qc.ca/) | WordPress | 1, 5, 6 |  | [2026-10-23](preuves/clg.qc.ca.md) |
| Cégep Montmorency | [cmontmorency.qc.ca](https://www.cmontmorency.qc.ca/) | WordPress | 5 | « Site web temporaire » ; COL.NET en `.asp` | [2026-10-24](preuves/cmontmorency.qc.ca.md) |
| Cégep régional de Lanaudière à Joliette | [cegep-lanaudiere.qc.ca/joliette](https://cegep-lanaudiere.qc.ca/joliette/) | WordPress | 4, 5 |  | [2026-10-23](preuves/cegep-lanaudiere.qc.ca-joliette.md) |
| Cégep régional de Lanaudière à L'Assomption | [cegep-lanaudiere.qc.ca/lassomption](https://cegep-lanaudiere.qc.ca/lassomption/) | WordPress | 4, 5 |  | [2026-10-23](preuves/cegep-lanaudiere.qc.ca-lassomption.md) |
| Cégep régional de Lanaudière à Terrebonne | [cegep-lanaudiere.qc.ca/terrebonne](https://cegep-lanaudiere.qc.ca/terrebonne/) | WordPress | 4, 5 |  | [2026-10-23](preuves/cegep-lanaudiere.qc.ca-terrebonne.md) |
| Cégep Saint-Jean-sur-Richelieu | [cstjean.qc.ca](https://www.cstjean.qc.ca/) | Drupal | 1, 5 |  | [2026-10-24](preuves/cstjean.qc.ca.md) |
| Centre de services scolaire de Charlevoix | [csscharlevoix.gouv.qc.ca](https://www.csscharlevoix.gouv.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/csscharlevoix.gouv.qc.ca.md) |
| Centre de services scolaire de Kamouraska–Rivière-du-Loup | [csskamloup.gouv.qc.ca](https://csskamloup.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/csskamloup.gouv.qc.ca.md) |
| Centre de services scolaire de l'Énergie | [cssenergie.gouv.qc.ca](https://cssenergie.gouv.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/cssenergie.gouv.qc.ca.md) |
| Centre de services scolaire de l'Estuaire | [cssestuaire.gouv.qc.ca](https://cssestuaire.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cssestuaire.gouv.qc.ca.md) |
| Centre de services scolaire de la Baie-James | [cssbj.gouv.qc.ca](https://cssbj.gouv.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/cssbj.gouv.qc.ca.md) |
| Centre de services scolaire de la Beauce-Etchemin | [cssbe.gouv.qc.ca](https://cssbe.gouv.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/cssbe.gouv.qc.ca.md) |
| Centre de services scolaire de la Capitale | [cssc.gouv.qc.ca](https://cssc.gouv.qc.ca/) | WordPress | 4, 5 |  | [2026-10-23](preuves/cssc.gouv.qc.ca.md) |
| Centre de services scolaire de la Côte-du-Sud | [csscotesud.gouv.qc.ca](https://csscotesud.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/csscotesud.gouv.qc.ca.md) |
| Centre de services scolaire De La Jonquière | [cssdlj.gouv.qc.ca](https://cssdlj.gouv.qc.ca/) | WordPress | 4, 5 |  | [2026-10-23](preuves/cssdlj.gouv.qc.ca.md) |
| Centre de services scolaire de la Moyenne-Côte-Nord | [csmcn.qc.ca](https://www.csmcn.qc.ca/) | PHP | 6 |  | [2026-10-23](preuves/csmcn.qc.ca.md) |
| Centre de services scolaire de la Pointe-de-l'Île | [csspi.gouv.qc.ca](https://csspi.gouv.qc.ca/) | Joomla | 1, 6 |  | [2026-10-23](preuves/csspi.gouv.qc.ca.md) |
| Centre de services scolaire de la Région-de-Sherbrooke | [cssrs.gouv.qc.ca](https://cssrs.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/cssrs.gouv.qc.ca.md) |
| Centre de services scolaire de la Riveraine | [cssdlr.gouv.qc.ca](https://cssdlr.gouv.qc.ca/) | WordPress | 1, 5, 6 |  | [2026-10-23](preuves/cssdlr.gouv.qc.ca.md) |
| Centre de services scolaire de la Seigneurie-des-Mille-Îles | [cssmi.qc.ca](https://cssmi.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cssmi.qc.ca.md) |
| Centre de services scolaire de la Vallée-des-Tisserands | [cssvt.gouv.qc.ca](https://cssvt.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cssvt.gouv.qc.ca.md) |
| Centre de services scolaire de Laval | [csslaval.gouv.qc.ca](https://csslaval.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/csslaval.gouv.qc.ca.md) |
| Centre de services scolaire de Montréal | [cssdm.gouv.qc.ca](https://cssdm.gouv.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/cssdm.gouv.qc.ca.md) |
| Centre de services scolaire de Rouyn-Noranda | [cssrn.gouv.qc.ca](https://cssrn.gouv.qc.ca/) | WordPress | 5, 6 |  | [2026-10-23](preuves/cssrn.gouv.qc.ca.md) |
| Centre de services scolaire de Saint-Hyacinthe | [csssh.gouv.qc.ca](https://csssh.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/csssh.gouv.qc.ca.md) |
| Centre de services scolaire de Sorel-Tracy | [cssst.gouv.qc.ca](https://cssst.gouv.qc.ca/) | WordPress | 4, 5, 6 | Statistiques Matomo | [2026-10-23](preuves/cssst.gouv.qc.ca.md) |
| Centre de services scolaire des Affluents | [cssda.gouv.qc.ca](https://cssda.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cssda.gouv.qc.ca.md) |
| Centre de services scolaire des Chic-Chocs | [csscc.gouv.qc.ca](https://csscc.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/csscc.gouv.qc.ca.md) |
| Centre de services scolaire des Découvreurs | [cssdd.gouv.qc.ca](https://cssdd.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cssdd.gouv.qc.ca.md) |
| Centre de services scolaire des Grandes-Seigneuries | [cssdgs.gouv.qc.ca](https://cssdgs.gouv.qc.ca/) | WordPress | 4, 5 |  | [2026-10-23](preuves/cssdgs.gouv.qc.ca.md) |
| Centre de services scolaire des Hautes-Laurentides | [csshl.gouv.qc.ca](https://csshl.gouv.qc.ca/) | WordPress | 4, 5 |  | [2026-10-23](preuves/csshl.gouv.qc.ca.md) |
| Centre de services scolaire des Hautes-Rivières | [cssdhr.gouv.qc.ca](https://cssdhr.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cssdhr.gouv.qc.ca.md) |
| Centre de services scolaire des Hauts-Cantons | [csshc.gouv.qc.ca](https://csshc.gouv.qc.ca/) | WordPress | 4, 5 |  | [2026-10-23](preuves/csshc.gouv.qc.ca.md) |
| Centre de services scolaire des Îles | [cssdesiles.gouv.qc.ca](https://cssdesiles.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cssdesiles.gouv.qc.ca.md) |
| Centre de services scolaire des Laurentides | [csslaurentides.gouv.qc.ca](https://csslaurentides.gouv.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/csslaurentides.gouv.qc.ca.md) |
| Centre de services scolaire des Monts-et-Marées | [cssmm.gouv.qc.ca](https://cssmm.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cssmm.gouv.qc.ca.md) |
| Centre de services scolaire des Navigateurs | [cssdn.gouv.qc.ca](https://cssdn.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cssdn.gouv.qc.ca.md) |
| Centre de services scolaire des Patriotes | [cssp.gouv.qc.ca](https://cssp.gouv.qc.ca/) | WordPress | 4, 5 |  | [2026-10-23](preuves/cssp.gouv.qc.ca.md) |
| Centre de services scolaire des Phares | [cssphares.gouv.qc.ca](https://www.cssphares.gouv.qc.ca/) | WordPress | 4, 5 |  | [2026-10-24](preuves/cssphares.gouv.qc.ca.md) |
| Centre de services scolaire des Portages-de-l'Outaouais | [csspo.gouv.qc.ca](https://csspo.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/csspo.gouv.qc.ca.md) |
| Centre de services scolaire des Premières-Seigneuries | [cssps.gouv.qc.ca](https://cssps.gouv.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/cssps.gouv.qc.ca.md) |
| Centre de services scolaire des Rives-du-Saguenay | [csrsaguenay.qc.ca](https://csrsaguenay.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/csrsaguenay.qc.ca.md) |
| Centre de services scolaire des Samares | [csssamares.gouv.qc.ca](https://csssamares.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 | Statistiques Matomo | [2026-10-23](preuves/csssamares.gouv.qc.ca.md) |
| Centre de services scolaire des Sommets | [cssds.gouv.qc.ca](https://cssds.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cssds.gouv.qc.ca.md) |
| Centre de services scolaire des Trois-Lacs | [csstl.gouv.qc.ca](https://csstl.gouv.qc.ca/) | WordPress | 5, 6 |  | [2026-10-23](preuves/csstl.gouv.qc.ca.md) |
| Centre de services scolaire du Chemin-du-Roy | [csscdr.gouv.qc.ca](https://csscdr.gouv.qc.ca/) | WordPress | 4, 5 |  | [2026-10-23](preuves/csscdr.gouv.qc.ca.md) |
| Centre de services scolaire du Fer | [csdufer.qc.ca](https://www.csdufer.qc.ca/) | PHP | 6 | Feuille de style générée par `css_dynamic_controleur.css.php` | [2026-10-23](preuves/csdufer.qc.ca.md) |
| Centre de services scolaire du Fleuve-et-des-Lacs | [cssfl.gouv.qc.ca](https://cssfl.gouv.qc.ca/) | PHP | 6 |  | [2026-10-23](preuves/cssfl.gouv.qc.ca.md) |
| Centre de services scolaire du Lac-Abitibi | [cssla.gouv.qc.ca](https://cssla.gouv.qc.ca/) | WordPress | 1, 5, 6 |  | [2026-10-23](preuves/cssla.gouv.qc.ca.md) |
| Centre de services scolaire du Lac-Témiscamingue | [csslt.gouv.qc.ca](https://csslt.gouv.qc.ca/) | WordPress | 1, 5, 6 |  | [2026-10-24](preuves/csslt.gouv.qc.ca.md) |
| Centre de services scolaire du Littoral | [cssdulittoral.gouv.qc.ca](https://cssdulittoral.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/cssdulittoral.gouv.qc.ca.md) |
| Centre de services scolaire du Pays-des-Bleuets | [csspb.gouv.qc.ca](https://csspb.gouv.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/csspb.gouv.qc.ca.md) |
| Centre de services scolaire du Val-des-Cerfs | [cssvdc.gouv.qc.ca](https://cssvdc.gouv.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/cssvdc.gouv.qc.ca.md) |
| Centre de services scolaire Harricana | [csharricana.qc.ca](https://www.csharricana.qc.ca/) | WordPress | 1, 5, 6 | Redirige vers cssh.gouv.qc.ca | [2026-10-23](preuves/csharricana.qc.ca.md) |
| Centre de services scolaire Marguerite-Bourgeoys | [cssmb.gouv.qc.ca](https://cssmb.gouv.qc.ca/) | WordPress | 4, 5 | Statistiques Matomo | [2026-10-23](preuves/cssmb.gouv.qc.ca.md) |
| Centre de services scolaire René-Lévesque | [cssrl.gouv.qc.ca](https://cssrl.gouv.qc.ca/) | WordPress | 1, 5, 6 |  | [2026-10-23](preuves/cssrl.gouv.qc.ca.md) |
| Collège d'Alma | [collegealma.ca](https://collegealma.ca/) | WordPress | 5, 6 |  | [2026-10-23](preuves/collegealma.ca.md) |
| Collège Dawson | [dawsoncollege.qc.ca](https://dawsoncollege.qc.ca/) | WordPress | 5 |  | [2026-10-23](preuves/dawsoncollege.qc.ca.md) |
| Collège Héritage | [cegep-heritage.qc.ca](https://cegep-heritage.qc.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-23](preuves/cegep-heritage.qc.ca.md) |
| Commission scolaire crie | [eeyoueducation.ca](https://eeyoueducation.ca/) | PHP | 6 |  | [2026-10-23](preuves/eeyoueducation.ca.md) |
| Commission scolaire Eastern Shores | [essb.qc.ca](https://essb.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/essb.qc.ca.md) |
| Commission scolaire Eastern Townships | [etsb.qc.ca](https://etsb.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/etsb.qc.ca.md) |
| Commission scolaire Kativik | [kativik.qc.ca](https://kativik.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/kativik.qc.ca.md) |
| Commission scolaire Lester-B.-Pearson | [lbpsb.qc.ca](https://lbpsb.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/lbpsb.qc.ca.md) |
| Commission scolaire New Frontiers | [nfsb.qc.ca](https://nfsb.qc.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/nfsb.qc.ca.md) |
| Commission scolaire Riverside | [rsb.qc.ca](https://rsb.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/rsb.qc.ca.md) |
| Commission scolaire Sir-Wilfrid-Laurier | [swlauriersb.qc.ca](https://www.swlauriersb.qc.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/swlauriersb.qc.ca.md) |
| Commission scolaire Western Québec | [westernquebec.ca](https://westernquebec.ca/) | WordPress | 1, 5, 6 |  | [2026-10-23](preuves/westernquebec.ca.md) |
| École nationale d'administration publique | [enap.ca](https://enap.ca/) | Drupal | 1, 5 |  | [2026-10-23](preuves/enap.ca.md) |
| HEC Montréal | [hec.ca](https://hec.ca/) | Drupal | 1, 5 |  | [2026-10-23](preuves/hec.ca.md) |
| Institut national de la recherche scientifique | [inrs.ca](https://inrs.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/inrs.ca.md) |
| Université Bishop's | [ubishops.ca](https://www.ubishops.ca/) | WordPress | 4, 5, 6 | Chrome headless sans réponse, vérifié par requête simple | [2026-10-24](preuves/ubishops.ca.md) |
| Université de Montréal | [umontreal.ca](https://www.umontreal.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-24](preuves/umontreal.ca.md) |
| Université de Sherbrooke | [usherbrooke.ca](https://www.usherbrooke.ca/) | TYPO3 | 1, 2, 5 |  | [2026-10-24](preuves/usherbrooke.ca.md) |
| Université du Québec à Chicoutimi | [uqac.ca](https://uqac.ca/) | WordPress | 1, 5, 6 |  | [2026-10-23](preuves/uqac.ca.md) |
| Université du Québec à Montréal | [uqam.ca](https://uqam.ca/) | WordPress | 4, 5 |  | [2026-10-23](preuves/uqam.ca.md) |
| Université du Québec à Rimouski | [uqar.ca](https://uqar.ca/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/uqar.ca.md) |
| Université du Québec en Outaouais | [uqo.ca](https://uqo.ca/) | Drupal | 1, 5 |  | [2026-10-23](preuves/uqo.ca.md) |
| Université Laval | [ulaval.ca](https://www.ulaval.ca/) | Drupal | 1, 5 | Thème maison `majuscule` | [2026-10-24](preuves/ulaval.ca.md) |
| Université Laval : bibliothèque | [bibl.ulaval.ca](https://bibl.ulaval.ca/) | Drupal | 1, 5 |  | [2026-10-23](preuves/bibl.ulaval.ca.md) |
| Université Laval : formation à distance | [distance.ulaval.ca](https://distance.ulaval.ca/) | Drupal | 1, 5 |  | [2026-10-23](preuves/distance.ulaval.ca.md) |
| Université Laval : PEPS | [peps.ulaval.ca](https://peps.ulaval.ca/) | Drupal | 1, 5 |  | [2026-10-23](preuves/peps.ulaval.ca.md) |
| Université Laval : philanthropie | [dprd.ulaval.ca](https://dprd.ulaval.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/dprd.ulaval.ca.md) |
| Université Laval : résidences | [residences.ulaval.ca](https://residences.ulaval.ca/) | Drupal | 1, 5 |  | [2026-10-23](preuves/residences.ulaval.ca.md) |
| Université Laval : Rouge et Or | [rougeetor.ulaval.ca](https://rougeetor.ulaval.ca/) | WordPress | 1, 5 |  | [2026-10-23](preuves/rougeetor.ulaval.ca.md) |
| Université McGill | [mcgill.ca](https://mcgill.ca/) | Drupal | 1 |  | [2026-10-23](preuves/mcgill.ca.md) |

### Municipalités

| Organisation | Site | Verdict | Méthodes | Notes | Vérifié le |
|---|---|---|---|---|---|
| Communauté métropolitaine de Montréal | [cmm.qc.ca](https://cmm.qc.ca/) | WordPress | 4, 5 |  | [2026-10-24](preuves/cmm.qc.ca.md) |
| Communauté métropolitaine de Québec | [cmquebec.qc.ca](https://cmquebec.qc.ca/) | WordPress | 5 |  | [2026-10-23](preuves/cmquebec.qc.ca.md) |
| Réseau de transport de la Capitale | [rtcquebec.ca](https://rtcquebec.ca/) | Drupal | 1, 5 |  | [2026-10-23](preuves/rtcquebec.ca.md) |
| Société de transport de Laval (STL) | [stlaval.ca](https://www.stlaval.ca/) | Craft CMS | 5, 6, 7 |  | [2026-10-24](preuves/stlaval.ca.md) |
| Ville de Laval | [laval.ca](https://laval.ca/) | WordPress | 1, 4, 5, 6 |  | [2026-10-23](preuves/laval.ca.md) |
| Ville de Longueuil | [longueuil.quebec](https://longueuil.quebec/) | Drupal | 5 | Page servie par Nuxt ; contenu tiré de l'API de cms.longueuil.quebec (Drupal) | [2026-10-24](preuves/longueuil.quebec.md) |
| Ville de Terrebonne | [ville.terrebonne.qc.ca](https://ville.terrebonne.qc.ca/) | WordPress | 1, 4, 5, 6 | Redirige vers terrebonne.ca | [2026-10-23](preuves/ville.terrebonne.qc.ca.md) |
| Ville de Trois-Rivières | [v3r.net](https://v3r.net/) | WordPress | 4, 5, 6 |  | [2026-10-23](preuves/v3r.net.md) |

## Sites sans signature de PHP

Aucune des méthodes n'a trouvé de signature de PHP sur ces sites. Quand une
autre technologie est visible (ASP.NET, Nuxt, Next.js, Magnolia…), elle est
indiquée en note ; sinon, la technologie n'est pas déterminée.

### Gouvernement

| Organisation | Site | Notes | Vérifié le |
|---|---|---|---|
| Assemblée nationale du Québec | [assnat.qc.ca](https://www.assnat.qc.ca/) | ASP.NET (`.aspx`) | [2026-10-24](preuves/assnat.qc.ca.md) |
| Consultation Québec | [consultation.quebec.ca](https://consultation.quebec.ca/) | Decidim, sur Ruby on Rails (`/decidim-packs/`, `/rails/active_storage/`) | [2026-10-25](preuves/consultation.quebec.ca.md) |
| Légis Québec | [legisquebec.gouv.qc.ca](https://www.legisquebec.gouv.qc.ca/) | URL sans extension ; dossiers `/CSS/` et `/css/` mêlés ; feuilles de style `cyberlex` | [2026-10-23](preuves/legisquebec.gouv.qc.ca.md) |
| Système électronique d'appel d'offres (SEAO) | [seao.gouv.qc.ca](https://www.seao.gouv.qc.ca/) |  | [2026-10-24](preuves/seao.gouv.qc.ca.md) |

### Ministères

| Organisation | Site | Notes | Vérifié le |
|---|---|---|---|
| Ministère de la Cybersécurité et du Numérique : Centre gouvernemental de cyberdéfense | [cyber.gouv.qc.ca](https://www.cyber.gouv.qc.ca/) | Statistiques Matomo | [2026-10-25](preuves/cyber.gouv.qc.ca.md) |

### Organismes

| Organisation | Site | Notes | Vérifié le |
|---|---|---|---|
| Bureau d'audiences publiques sur l'environnement | [bape.gouv.qc.ca](https://bape.gouv.qc.ca/) |  | [2026-10-23](preuves/bape.gouv.qc.ca.md) |
| Commission d'accès à l'information | [cai.gouv.qc.ca](https://cai.gouv.qc.ca/) |  | [2026-10-23](preuves/cai.gouv.qc.ca.md) |
| Commission d'évaluation de l'enseignement collégial | [ceec.gouv.qc.ca](https://ceec.gouv.qc.ca/) |  | [2026-10-23](preuves/ceec.gouv.qc.ca.md) |
| Commission de toponymie | [toponymie.gouv.qc.ca](https://toponymie.gouv.qc.ca/) | ASP.NET (`.aspx`), par exemple [actualités](https://toponymie.gouv.qc.ca/ct/salle-de-presse/actualites/index.aspx) | [2026-10-23](preuves/toponymie.gouv.qc.ca.md) |
| Commission des droits de la personne et des droits de la jeunesse | [cdpdj.qc.ca](https://cdpdj.qc.ca/) |  | [2026-10-23](preuves/cdpdj.qc.ca.md) |
| Commission des services juridiques | [csj.qc.ca](https://csj.qc.ca/) |  | [2026-10-23](preuves/csj.qc.ca.md) |
| Conservatoire de musique et d'art dramatique du Québec | [conservatoire.gouv.qc.ca](https://conservatoire.gouv.qc.ca/) |  | [2026-10-23](preuves/conservatoire.gouv.qc.ca.md) |
| Institut de la statistique du Québec | [stat.gouv.qc.ca](https://stat.gouv.qc.ca/) | Next.js | [2026-10-23](preuves/stat.gouv.qc.ca.md) |
| Musée national des beaux-arts du Québec | [mnbaq.org](https://mnbaq.org/) |  | [2026-10-23](preuves/mnbaq.org.md) |
| Office de la sécurité du revenu des chasseurs et piégeurs cris | [osrcpc.ca](https://osrcpc.ca/) | Redirige vers chasseurcri.ca | [2026-10-23](preuves/osrcpc.ca.md) |
| Office Québec-Monde pour la jeunesse | [lojiq.org](https://lojiq.org/) |  | [2026-10-23](preuves/lojiq.org.md) |
| Office québécois de la langue française | [oqlf.gouv.qc.ca](https://www.oqlf.gouv.qc.ca/) | ASP.NET (`.aspx`) | [2026-10-23](preuves/oqlf.gouv.qc.ca.md) |
| Régie de l'énergie | [regie-energie.qc.ca](https://www.regie-energie.qc.ca/) |  | [2026-10-23](preuves/regie-energie.qc.ca.md) |
| Revenu Québec : Juste pour tous | [justepourtous.revenuquebec.ca](https://justepourtous.revenuquebec.ca/) |  | [2026-10-23](preuves/justepourtous.revenuquebec.ca.md) |
| Santé Québec | [sante.quebec](https://sante.quebec/) | Nuxt | [2026-10-23](preuves/sante.quebec.md) |
| Secrétariat aux emplois supérieurs | [emplois-superieurs.gouv.qc.ca](https://emplois-superieurs.gouv.qc.ca/) |  | [2026-10-23](preuves/emplois-superieurs.gouv.qc.ca.md) |
| Société de protection des forêts contre le feu | [sopfeu.qc.ca](https://sopfeu.qc.ca/) | Nuxt | [2026-10-23](preuves/sopfeu.qc.ca.md) |
| Vérificateur général du Québec | [vgq.qc.ca](https://vgq.qc.ca/) |  | [2026-10-23](preuves/vgq.qc.ca.md) |

### Sociétés d'État

| Organisation | Site | Notes | Vérifié le |
|---|---|---|---|
| Hydro-Québec | [hydroquebec.com](https://www.hydroquebec.com/) | Pages `.html` statiques ; cookies : seulement Google Analytics, OneTrust et Qualtrics | [2026-10-24](preuves/hydroquebec.com.md) |
| Hydro-Québec : emplois | [emploi.hydroquebec.com](https://emploi.hydroquebec.com/) |  | [2026-10-23](preuves/emploi.hydroquebec.com.md) |
| Hydro-Québec : Info-pannes | [pannes.hydroquebec.com](https://pannes.hydroquebec.com/) | Redirige vers infopannes.solutions.hydroquebec.com | [2026-10-23](preuves/pannes.hydroquebec.com.md) |
| Hydro-Québec : nouvelles | [nouvelles.hydroquebec.com](https://nouvelles.hydroquebec.com/) |  | [2026-10-23](preuves/nouvelles.hydroquebec.com.md) |
| Loto-Québec | [lotoquebec.com](https://www.lotoquebec.com/) | Redirige vers espacejeux.com ; application Nuxt (`window.__NUXT__`) ; chemins `/.resources/` et `/dam/jcr/` de Magnolia (Java) | [2026-10-24](preuves/lotoquebec.com.md) |
| Loto-Québec : 2e chance | [2echance.espacejeux.com](https://2echance.espacejeux.com/) | Magnolia | [2026-10-23](preuves/2echance.espacejeux.com.md) |
| Loto-Québec : Bien jouer | [bienjouer.lotoquebec.com](https://bienjouer.lotoquebec.com/) | Nuxt ; Magnolia | [2026-10-23](preuves/bienjouer.lotoquebec.com.md) |
| Loto-Québec : carrières | [carrieres.lotoquebec.com](https://carrieres.lotoquebec.com/) | Nuxt ; Magnolia | [2026-10-23](preuves/carrieres.lotoquebec.com.md) |
| Loto-Québec : site corporatif | [societe.lotoquebec.com](https://societe.lotoquebec.com/) | Magnolia | [2026-10-23](preuves/societe.lotoquebec.com.md) |
| Sépaq | [sepaq.com](https://sepaq.com/) |  | [2026-10-23](preuves/sepaq.com.md) |
| Société de financement des infrastructures locales du Québec | [sofil.gouv.qc.ca](https://www.sofil.gouv.qc.ca/) | ASP.NET (`.aspx`) | [2026-10-24](preuves/sofil.gouv.qc.ca.md) |
| Société du Grand Théâtre de Québec | [grandtheatre.qc.ca](https://grandtheatre.qc.ca/) |  | [2026-10-23](preuves/grandtheatre.qc.ca.md) |
| Société du parc industriel et portuaire de Bécancour | [spipb.com](https://spipb.com/) |  | [2026-10-23](preuves/spipb.com.md) |
| Société québécoise d'information juridique | [soquij.qc.ca](https://soquij.qc.ca/) | Images servies par blogue.soquij.qc.ca (WordPress) | [2026-10-23](preuves/soquij.qc.ca.md) |
| Télé-Québec | [telequebec.tv](https://www.telequebec.tv/) |  | [2026-10-24](preuves/telequebec.tv.md) |

### Santé

| Organisation | Site | Notes | Vérifié le |
|---|---|---|---|
| Centre de santé Tulattavik de l'Ungava | [tulattavik.com](https://tulattavik.com/) |  | [2026-10-23](preuves/tulattavik.com.md) |
| CHU de Québec-Université Laval | [chudequebec.ca](https://chudequebec.ca/) | ASP.NET (`.aspx`) | [2026-10-23](preuves/chudequebec.ca.md) |
| CHU Sainte-Justine | [chusj.org](https://chusj.org/) | ASP.NET (`.aspx`) | [2026-10-23](preuves/chusj.org.md) |
| Rendez-vous santé Québec | [rvsq.gouv.qc.ca](https://rvsq.gouv.qc.ca/) | ASP.NET (`.aspx`) | [2026-10-23](preuves/rvsq.gouv.qc.ca.md) |
| Santé Québec Baie-James | [crsssbaiejames.gouv.qc.ca](https://crsssbaiejames.gouv.qc.ca/) | ASP.NET (`.aspx`) | [2026-10-23](preuves/crsssbaiejames.gouv.qc.ca.md) |
| Santé Québec Mauricie-et-du-Centre-du-Québec | [ciusssmcq.ca](https://ciusssmcq.ca/) |  | [2026-10-23](preuves/ciusssmcq.ca.md) |

### Éducation

| Organisation | Site | Notes | Vérifié le |
|---|---|---|---|
| Cégep d'Ahuntsic | [collegeahuntsic.qc.ca](https://collegeahuntsic.qc.ca/) |  | [2026-10-23](preuves/collegeahuntsic.qc.ca.md) |
| Cégep de Rimouski | [cegep-rimouski.qc.ca](https://cegep-rimouski.qc.ca/) |  | [2026-10-23](preuves/cegep-rimouski.qc.ca.md) |
| Cégep de Rivière-du-Loup | [cegeprdl.ca](https://cegeprdl.ca/) |  | [2026-10-23](preuves/cegeprdl.ca.md) |
| Cégep Édouard-Montpetit | [cegepmontpetit.ca](https://cegepmontpetit.ca/) |  | [2026-10-23](preuves/cegepmontpetit.ca.md) |
| Cégep Marie-Victorin | [collegemv.qc.ca](https://collegemv.qc.ca/) |  | [2026-10-23](preuves/collegemv.qc.ca.md) |
| Cégep Vanier | [vaniercollege.qc.ca](https://vaniercollege.qc.ca/) | Next.js | [2026-10-23](preuves/vaniercollege.qc.ca.md) |
| Centre de services scolaire au Cœur-des-Vallées | [csscv.gouv.qc.ca](https://csscv.gouv.qc.ca/) |  | [2026-10-23](preuves/csscv.gouv.qc.ca.md) |
| Centre de services scolaire de la Rivière-du-Nord | [cssrdn.gouv.qc.ca](https://cssrdn.gouv.qc.ca/) |  | [2026-10-23](preuves/cssrdn.gouv.qc.ca.md) |
| Centre de services scolaire de Portneuf | [cssportneuf.gouv.qc.ca](https://cssportneuf.gouv.qc.ca/) |  | [2026-10-23](preuves/cssportneuf.gouv.qc.ca.md) |
| Centre de services scolaire des Appalaches | [cssa.gouv.qc.ca](https://cssa.gouv.qc.ca/) |  | [2026-10-23](preuves/cssa.gouv.qc.ca.md) |
| Centre de services scolaire des Bois-Francs | [cssbf.gouv.qc.ca](https://cssbf.gouv.qc.ca/) |  | [2026-10-23](preuves/cssbf.gouv.qc.ca.md) |
| Centre de services scolaire des Chênes | [cssdeschenes.gouv.qc.ca](https://cssdeschenes.gouv.qc.ca/) | ASP.NET (`.aspx`) | [2026-10-23](preuves/cssdeschenes.gouv.qc.ca.md) |
| Centre de services scolaire des Draveurs | [cssd.gouv.qc.ca](https://cssd.gouv.qc.ca/) |  | [2026-10-23](preuves/cssd.gouv.qc.ca.md) |
| Centre de services scolaire des Hauts-Bois-de-l'Outaouais | [csshbo.gouv.qc.ca](https://csshbo.gouv.qc.ca/) |  | [2026-10-23](preuves/csshbo.gouv.qc.ca.md) |
| Centre de services scolaire du Lac-Saint-Jean | [csslsj.gouv.qc.ca](https://csslsj.gouv.qc.ca/) |  | [2026-10-23](preuves/csslsj.gouv.qc.ca.md) |
| Centre de services scolaire Marie-Victorin | [cssmv.gouv.qc.ca](https://cssmv.gouv.qc.ca/) | Nuxt | [2026-10-23](preuves/cssmv.gouv.qc.ca.md) |
| Commission scolaire Central Québec | [cqsb.qc.ca](https://cqsb.qc.ca/) |  | [2026-10-23](preuves/cqsb.qc.ca.md) |
| Commission scolaire English-Montréal | [emsb.qc.ca](https://emsb.qc.ca/) |  | [2026-10-23](preuves/emsb.qc.ca.md) |
| École de technologie supérieure | [etsmtl.ca](https://etsmtl.ca/) |  | [2026-10-23](preuves/etsmtl.ca.md) |
| Polytechnique Montréal | [polymtl.ca](https://polymtl.ca/) |  | [2026-10-23](preuves/polymtl.ca.md) |
| Université Concordia | [concordia.ca](https://concordia.ca/) |  | [2026-10-23](preuves/concordia.ca.md) |
| Université du Québec à Trois-Rivières | [uqtr.ca](https://uqtr.ca/) |  | [2026-10-23](preuves/uqtr.ca.md) |
| Université du Québec en Abitibi-Témiscamingue | [uqat.ca](https://uqat.ca/) |  | [2026-10-23](preuves/uqat.ca.md) |
| Université Laval : nouvelles | [nouvelles.ulaval.ca](https://nouvelles.ulaval.ca/) |  | [2026-10-23](preuves/nouvelles.ulaval.ca.md) |
| Université TÉLUQ | [teluq.ca](https://teluq.ca/) |  | [2026-10-23](preuves/teluq.ca.md) |

### Municipalités

| Organisation | Site | Notes | Vérifié le |
|---|---|---|---|
| Bibliothèque de Québec | [bibliothequedequebec.qc.ca](https://bibliothequedequebec.qc.ca/) | ASP.NET (`.aspx`) | [2026-10-23](preuves/bibliothequedequebec.qc.ca.md) |
| Bibliothèques de Laval | [biblio.laval.ca](https://biblio.laval.ca/) |  | [2026-10-23](preuves/biblio.laval.ca.md) |
| exo | [exo.quebec](https://exo.quebec/) | Next.js | [2026-10-24](preuves/exo.quebec.md) |
| Réseau de transport de Longueuil (RTL) | [rtl-longueuil.qc.ca](https://www.rtl-longueuil.qc.ca/) |  | [2026-10-24](preuves/rtl-longueuil.qc.ca.md) |
| Service de police de la Ville de Montréal (SPVM) | [spvm.qc.ca](https://spvm.qc.ca/) |  | [2026-10-23](preuves/spvm.qc.ca.md) |
| Service de police de Saguenay | [police.saguenay.ca](https://police.saguenay.ca/) |  | [2026-10-24](preuves/police.saguenay.ca.md) |
| Société d'habitation et de développement de Montréal | [shdm.org](https://shdm.org/) | Nuxt | [2026-10-23](preuves/shdm.org.md) |
| Société de transport de Montréal (STM) | [stm.info](https://www.stm.info/) |  | [2026-10-24](preuves/stm.info.md) |
| Société du parc Jean-Drapeau | [parcjeandrapeau.com](https://www.parcjeandrapeau.com/) |  | [2026-10-24](preuves/parcjeandrapeau.com.md) |
| Ville de Gatineau | [gatineau.ca](https://gatineau.ca/) | ASP.NET (`.aspx`) | [2026-10-23](preuves/gatineau.ca.md) |
| Ville de Lévis | [ville.levis.qc.ca](https://ville.levis.qc.ca/) | Redirige vers levis.ca ; Nuxt | [2026-10-23](preuves/ville.levis.qc.ca.md) |
| Ville de Montréal | [montreal.ca](https://montreal.ca/) |  | [2026-10-23](preuves/montreal.ca.md) |
| Ville de Montréal : données ouvertes | [donnees.montreal.ca](https://donnees.montreal.ca/) |  | [2026-10-23](preuves/donnees.montreal.ca.md) |
| Ville de Québec | [ville.quebec.qc.ca](https://www.ville.quebec.qc.ca/) | ASP.NET (`.aspx`) | [2026-10-24](preuves/ville.quebec.qc.ca.md) |
| Ville de Québec : blogue | [blogue.ville.quebec.qc.ca](https://blogue.ville.quebec.qc.ca/) | ASP.NET (`.aspx`) | [2026-10-23](preuves/blogue.ville.quebec.qc.ca.md) |
| Ville de Québec : Québec animée | [animee.ville.quebec.qc.ca](https://animee.ville.quebec.qc.ca/) | ASP.NET (`.aspx`) | [2026-10-23](preuves/animee.ville.quebec.qc.ca.md) |
| Ville de Saguenay | [ville.saguenay.ca](https://ville.saguenay.ca/) |  | [2026-10-23](preuves/ville.saguenay.ca.md) |
| Ville de Sherbrooke | [sherbrooke.ca](https://sherbrooke.ca/) |  | [2026-10-23](preuves/sherbrooke.ca.md) |

## Sites à visiter

Organisations à vérifier, avec la raison pour laquelle elles ne le sont pas
encore.

### Organismes

| Organisation | Site | Statut |
|---|---|---|
| Institut national des mines | inmq.gouv.qc.ca | En maintenance (2026-10-25) |

### Éducation

| Organisation | Site | Statut |
|---|---|---|
| Centre de services scolaire de l'Or-et-des-Bois | cssob.gouv.qc.ca | Bloqué : 403 Forbidden, à faire à la main (2026-10-25) |

### Municipalités

| Organisation | Site | Statut |
|---|---|---|
| Société de transport de l'Outaouais (STO) | sto.ca | En maintenance (2026-10-25) |
