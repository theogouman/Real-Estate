# Landing — 3 rue Fenouillet, Hyères

Landing page privée pour un appartement de 87,61 m² Loi Carrez avec jardin de
130 m², au centre de Hyères. Document envoyé par lien direct à un couple de
prospects après contre-visite.

## Stack

HTML statique pur (CSS + JS inline dans `index.html`). Aucune dépendance npm,
aucune requête réseau externe. La page doit s'ouvrir offline une fois les
assets téléchargés.

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

À télécharger depuis Google Fonts (Cormorant Garamond) et Adobe / Google
Fonts (Source Sans 3), convertir en `.woff2` puis déposer avec ces noms :

- `cormorant-garamond-regular.woff2`
- `cormorant-garamond-italic.woff2`
- `cormorant-garamond-medium.woff2`
- `source-sans-3-regular.woff2`
- `source-sans-3-medium.woff2`
- `source-sans-3-semibold.woff2`

> En attendant, le fallback Georgia / system fonctionne déjà — la page reste
> lisible et conserve son rythme typographique.

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

**Pièces (drawer du plan interactif — section 5 / plan-pieces)**
- `sejour-01.webp` à `sejour-03.webp`
- `cuisine-01.webp` à `cuisine-02.webp`
- `chambre-1-01.webp`
- `chambre-2-01.webp`
- `chambre-3-01.webp`
- `salle-eau-1-01.webp`
- `salle-eau-2-01.webp`
- `terrasse-01.webp`
- `entree-01.webp`
- `cellier-01.webp`
- `wc-01.webp`

Une fois les photos déposées, mettre à jour le tableau `ROOMS` dans le JS
en bas de `index.html` (chaque entrée a un champ `photos: []` à remplir).

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

### Plan interactif — illustrations du jardin `/assets/plan/`

Le SVG du plan est déjà intégré inline dans `index.html` (section
`#plan-pieces`). Il référence 5 illustrations PNG à déposer en local :

- `plant-01.png` — palmier en bas du jardin (~75×75 px)
- `plant-02.png` — petit feuillage au centre (~62×62 px)
- `plant-03.png` — bande de végétation en haut (~186×80 px)
- `plant-04.png` — agave utilisée 2× (75×75 px côté gauche, 41×85 px côté droit)

Tant qu'elles ne sont pas déposées, le plan reste lisible mais affiche des
cadres vides à l'emplacement des plantes.

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

Pour ajouter des photos à une pièce, ouvrir `index.html`, trouver l'objet
`ROOMS` dans le `<script>` final, et remplir le tableau `photos: []` avec
les chemins des images :

```js
'chambre-parentale': {
  name: 'Chambre parentale',
  surface: '8,32 m²',
  description: '...',
  photos: [
    '/assets/photos/chambre-parentale-01.webp',
    '/assets/photos/chambre-parentale-02.webp'
  ]
}
```

Un carousel apparaît automatiquement à partir de 2 photos (flèches +
puces + navigation clavier ←/→).

## Performance

- Toutes les images sont lazy-loaded (sauf le Hero).
- Le CSS et le JS sont inline pour éviter les requêtes supplémentaires.
- Cibles Lighthouse : Performance > 95, Accessibilité > 95, SEO > 90.

## SEO & confidentialité

- `<meta name="robots" content="noindex, nofollow">` est en place.
- `vercel.json` ajoute aussi le header `X-Robots-Tag: noindex, nofollow` sur
  toutes les routes.
- Aucun tracking, aucun cookie, aucune dépendance externe.
