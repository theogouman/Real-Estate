# Landing — 3 rue Fenouillet, Hyères

Landing page privée pour un appartement de 87,61 m² Loi Carrez avec jardin de
130 m², au centre de Hyères. Document envoyé par lien direct à un couple de
prospects après contre-visite.

## Stack

HTML statique pur (CSS + JS inline dans `index.html`). Aucune dépendance npm.

> **Note :** les photos du plan interactif et les 5 illustrations de plantes
> sont actuellement hébergées sur Cloudinary (`res.cloudinary.com/dceobxyts/`)
> pour bénéficier des transformations à la volée (`w_1280` / `w_400` / `w_200`).
> Cela introduit une dépendance réseau pour l'affichage du plan, contrairement
> à la contrainte initiale "100 % offline". Choix assumé : workflow d'édition
> plus rapide, optimisation automatique des images.

## Structure

```
/
├── index.html              # Mono-fichier (HTML + CSS + JS inline)
├── README.md
├── vercel.json             # Cache headers + noindex
├── .gitignore
└── assets/
    ├── fonts/              # .woff2 locaux (Cormorant Garamond + Source Sans 3)
    ├── photos/             # .webp + fallback .jpg
    ├── pdfs/               # diagnostics + accord vis-à-vis
    └── plan.svg            # plan interactif (intégré inline dans index.html)
```

## Déploiement sur Vercel

1. **Pousser le repo sur GitHub.**
   ```bash
   git push -u origin main
   ```
2. **Importer dans Vercel.** Aller sur https://vercel.com → *Add New* →
   *Project* → *Import Git Repository* → sélectionner le repo. Vercel détecte
   le projet statique automatiquement (Framework Preset = *Other*, Build
   Command = vide, Output Directory = vide). *Deploy*.
3. **URL publique.** Vercel attribue une URL `*.vercel.app`. C'est le lien à
   envoyer au prospect.
4. **Domaine personnalisé** (optionnel). *Settings → Domains* → ajouter le
   domaine. Suivre les instructions DNS.

## Édition

Toutes les valeurs textuelles et les chiffres sont en clair dans
`index.html`. Les sections sont commentées avec leur numéro (`01 — HERO`,
`02 — SOMMAIRE`, etc.) pour s'y retrouver rapidement.

## Placeholders à remplir

Le code contient des marqueurs `<!-- PLACEHOLDER: ... -->` dans `index.html`
pour chaque ressource manquante. Liste exhaustive :

### Polices `/assets/fonts/`

**Police principale : SF Pro Display** (Apple). Récupérable depuis
[developer.apple.com/fonts](https://developer.apple.com/fonts/). Convertir en
`.woff2` et déposer avec ces noms :

- `sf-pro-display-regular.woff2` (400)
- `sf-pro-display-medium.woff2` (500)
- `sf-pro-display-semibold.woff2` (600)
- `sf-pro-display-bold.woff2` (700)

**Police d'accent : Playfair Display** (Google Fonts, libre). Italique pour
les chiffres romains, les légendes et les accents manuscrits :

- `playfair-display-italic.woff2`
- `playfair-display-regular.woff2`

> Sans les `.woff2`, la stack système charge la **vraie SF Pro** sur tous les
> appareils Apple (Mac, iPhone, iPad), avec fallback Helvetica Neue puis
> system-ui ailleurs. Playfair Display retombe sur Georgia italic. La page
> reste lisible et conserve son rythme typographique.

### Photos `/assets/photos/`

Format recommandé : `.webp` à 80 % + fallback `.jpg` à 85 %, max 1600 px de
large pour les principales, 800 px pour la galerie.

**Hero (chargement immédiat, prendre la plus forte)**
- `hero-jardin.webp` + `hero-jardin.jpg` — jardin de nuit recommandé
- `og-image.jpg` — version 1200×630 px pour partage WhatsApp / email

**Jardin (galerie section 5)**
- `jardin-jour-01.webp` à `jardin-jour-03.webp`
- `jardin-nuit-01.webp` à `jardin-nuit-02.webp`
- `jardin-detail-01.webp`

**Pièces (modal du plan interactif — section 5 / plan-pieces)**
Les 11 pièces utilisent désormais des URLs Cloudinary (déclarées dans l'objet
`PLACEHOLDER_PHOTOS` du `<script>` final de `index.html`). Format des URLs :
`https://res.cloudinary.com/dceobxyts/image/upload/f_auto,q_auto,w_1280/<version>/<id>.jpg`.

Le code génère automatiquement les variantes basse-rés (`w_400` pour
placeholder pendant chargement) et thumbnails (`w_200` pour la bande sous le
carousel). Pour remplacer une photo : ouvrir `index.html`, retrouver le
tableau `PLACEHOLDER_PHOTOS[<room-id>]` et éditer les URLs.

**Parking (section 9)**
- `parking-cage-01.webp` + `parking-cage-02.webp`

### PDF `/assets/pdfs/`

- `dpe.pdf`
- `note_synthese.pdf`
- `amiante.pdf`
- `plomb.pdf`
- `termites.pdf`
- `electricite.pdf`
- `superficie_carrez.pdf`
- `accord_vis_a_vis.pdf` — celui-ci est embedé dans la section Jardin

> Une fois `accord_vis_a_vis.pdf` déposé, décommenter le bloc `<object>` dans
> la section Jardin de `index.html` et supprimer le `.pdf-placeholder`.

### Plan interactif — illustrations du jardin

Les 5 illustrations PNG des plantes sont également hébergées sur Cloudinary
(URLs directes dans les balises `<image href="...">` du SVG `#plan-svg`). Pour
les modifier, éditer directement le SVG inline dans `index.html`.

### Wording du plan interactif (drawer) vs tableau Carrez

Les noms affichés dans la modal du plan diffèrent volontairement du tableau
Carrez (section `#surfaces`) :

| data-room          | Nom dans la modal       | Nom au tableau Carrez |
|--------------------|-------------------------|------------------------|
| `chambre-parentale`| Chambre parentale       | Chambre n°1 (8,32 m²) |
| `chambre-amis`     | Chambre d'amis          | Chambre n°2 (13,50 m²)|
| `bureau-chambre`   | Bureau / Chambre        | Chambre n°3 (14,96 m²)|
| `sdb-privee`       | Salle de bain privée    | Salle d'eau / WC (4,02 m²)|
| `sdb-wc`           | Salle de bain & WC      | Salle d'eau (3,15 m²) |
| `cellier`          | Buanderie               | Cellier (2,60 m²)     |
| `sejour`           | Séjour & Entrée (30,05 m²)| Séjour 25,90 + Entrée 4,15 |

C'est une décision UX : le tableau Carrez reflète le certificat officiel
(à imprimer pour la promesse de vente) ; la modal utilise un wording plus
chaleureux pour aider à la projection. Pour modifier l'un sans l'autre,
éditer respectivement le tableau HTML ou l'objet `ROOMS` dans le `<script>`
en bas de `index.html`.

### Photos par pièce (modal du plan)

Les photos sont déclarées dans l'objet `PLACEHOLDER_PHOTOS` du `<script>`
final de `index.html`. Une pièce sans photo affiche un placeholder
"Photos à venir". Avec 2+ photos, le carousel apparaît automatiquement :
flèches liquid-glass, thumbnails sous le carousel, navigation clavier ←/→.

Optimisations actives :
- **Preload basse-rés** (`w_400`) de la 1ʳᵉ photo de chaque pièce au
  `DOMContentLoaded`, pour éviter l'écran noir à la première ouverture.
- **Preload haute-rés** (`w_1280`) des photos 0 et 1 d'une pièce au hover
  de sa zone (après 80 ms pour ignorer les hovers de passage).
- **Lazy/eager** : seules la slide courante et ses 2 voisines sont en
  `loading="eager"` ; les autres restent `lazy`.
- **Thumbnails** servies en `w_200`.

### Animation séquentielle au scroll

Quand la section `#plan-pieces` entre dans le viewport (à 30 % de visibilité),
un `IntersectionObserver` déclenche une **illumination séquentielle haut→bas**
des 11 pièces (1 pulse de 1200 ms par pièce, décalage de 600 ms). L'animation
ne se joue qu'une seule fois. Désactivée si `prefers-reduced-motion`.

## Performance

- Toutes les images sont lazy-loaded (sauf le Hero).
- Le CSS et le JS sont inline pour éviter les requêtes supplémentaires.
- Cibles Lighthouse : Performance > 95, Accessibilité > 95, SEO > 90.

## SEO & confidentialité

- `<meta name="robots" content="noindex, nofollow">` est en place.
- `vercel.json` ajoute aussi le header `X-Robots-Tag: noindex, nofollow` sur
  toutes les routes.
- Aucun tracking, aucun cookie, aucun analytics.
- Seule dépendance réseau : les photos hébergées sur Cloudinary (cf. note
  en début de README). Tout le reste (CSS, JS, polices) est inline ou local.
