# Ville de Longueuil

- Site : <https://longueuil.quebec>
- Vérifié le : 2026-10-24 (extraits de l'API, à la main) ; 2026-10-23 (Chrome headless, page d'accueil)
- Verdict : Drupal
- Méthodes : 5
- Notes : Page servie par Nuxt ; contenu tiré de l'API de cms.longueuil.quebec (Drupal)

## 5. Chemins et marqueurs de CMS

La page est affichée par Nuxt, mais son contenu vient de cms.longueuil.quebec :
l'API JSON:API de Drupal (`/fr/api/…`) et les styles d'image de Drupal
(`/sites/default/files/styles/…?itok=…`). Ce sous-domaine est retenu, même si
les autres ne le sont pas, parce que la page en dépend. Extraits ajoutés à la
main, 2026-10-24.

```js
href:"https:\u002F\u002Fcms.longueuil.quebec\u002Ffr\u002Fapi\u002Fhomepages\u002Fb8a42551-569b-4706-818b-a3284edbc814?resourceVersion=id%3A6833"
```

```js
front_large_21_9:"https:\u002F\u002Fcms.longueuil.quebec\u002Fsites\u002Fdefault\u002Ffiles\u002Fstyles\u002Ffront_large_21_9\u002Fpublic\u002Fmedias\u002F2026-10\u002Fbiblioclubtricotheque1.png?itok=IXAt-MyN"
```

```html
<video autoplay="autoplay" loop="loop" preload="none" src="https://cms.longueuil.quebec/sites/default/files/medias/videos/2026-09/2026-09/Vid%C3%A9o%20Automne%202025.mp4" poster="/sites/default/files/2021-09/Centre-ville%20Longueuil-6%20actuel.jpg" playsinline="" muted="muted" data-v-33f532c5="">
```

## Autres indices

```html
gueuil </p></div></div></div></div></div></footer></div></div></div><script>window.__NUXT__=(function(a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p,q,r,s,t,u,v,w,x,y,z,A,B,C,D,E,F,G,H,I,J,K,L,M,N,O,P,Q,R,S,T,U,V,W,X,Y,Z,_,$,aa,ab,ac,ad,ae,a
```
